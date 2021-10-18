Spring Authorization
Spring Boot and OAuth2
Single Sign On With GitHub

To create application uses GitHub for authentication.

Create project Spring initializr.
Create index.html in the src/main/resources/static folder
Securing the Application with GitHub and Spring Security
Add Spring Security OAuth 2.0 Client dependency.
Add a New GitHub App.
Then, to make the link to GitHub, add the following to your application.yml:
spring:
  security:
    oauth2:
      client:
        registration:
          github:
            clientId: github-client-id
            clientSecret: github-client-secret
# ...


This app, in OAuth 2.0 terms, is a Client Application, and it uses the authorization code grant to obtain an access token from GitHub (the Authorization Server).

It then uses the access token to ask GitHub for some personal details (only what you permitted it to do), including your login ID and your name. In this phase, GitHub is acting as a Resource Server, decoding the token that you send and checking if it gives the app permission to access the user’s details. If that process is successful, the app inserts the user details into the Spring Security context so that you are authenticated.

This is what we can add to index.html:

<div class="container unauthenticated">
    With GitHub: <a href="/oauth2/authorization/github">click here</a>
</div>
<div class="container authenticated" style="display:none">
    Logged in as: <span id="user"></span>
</div>

example for adding server-side endpoint:
@GetMapping("/user")
    public Map<String, Object> user(@AuthenticationPrincipal OAuth2User principal) {
        return Collections.singletonMap("name", principal.getAttribute("name"));
    }

in the configure for making the home page public:
 @Override
    protected void configure(HttpSecurity http) throws Exception {
    	// @formatter:off
        http
            .authorizeRequests(a -> a
                .antMatchers("/", "/error", "/webjars/**").permitAll()
                .anyRequest().authenticated()
            )
            .exceptionHandling(e -> e
                .authenticationEntryPoint(new HttpStatusEntryPoint(HttpStatus.UNAUTHORIZED))
            )
            .oauth2Login();
        // @formatter:on
    }

Login with GitHub
To use Google’s OAuth 2.0 authentication system for login, you must set up a project in the Google API Console to obtain OAuth 2.0 credentials.
Setting the redirect URI

http://localhost:8080/login/oauth2/code/google

Adding the Client Registration
Add this to application.yml:
spring:
  security:
    oauth2:
      client:
        registration:
          github:
            clientId: github-client-id
            clientSecret: github-client-secret
          google:
            client-id: google-client-id
            client-secret: google-client-secret

Add links in html.
Adding an Error Message, whenever authentication fails:
protected void configure(HttpSecurity http) throws Exception {
	// @formatter:off
	http
	    // ... existing configuration
	    .oauth2Login(o -> o
            .failureHandler((request, response, exception) -> {
			    request.getSession().setAttribute("error.message", exception.getMessage());
			    handler.onAuthenticationFailure(request, response, exception);
            })
        );
}