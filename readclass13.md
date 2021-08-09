# Status Codes Based On REST Methods

**A status code is a number higher than 100 and smaller than 600 that is part of a HTTP response. The first digit defines the class of the status. A status code comes with a reason phrase. The code is for programmatic recognition the phrase is for humans to understand what happened.**

### 100’s : Informational status codes

 they usually tell the client that the header part of the request has been received and the server will try to comply with a transmission demand of the client. Like using a different protocol or telling the client that its request will fail before they start sending the body.

### 200’s : The success codes

 They tell the client that its request was accepted. In case of asynchronous processing of a request `(202)`, **this doesn’t mean the request was successfully processed only that it met all validation requirements at the time of sending.**

### 300’s : Redirection codes

They tell the client that **the resource they are requesting isn’t available at the expected location anymore**. This can have multiple reasons, be temporary or permanent, but `the client has to issue a request to the new location.`

### 400’s : The client error codes

They are all about **invalid requests a client sent to a server.** There are several causes to this, ***timeouts, wrong URI, missing authentication, etc.*** A client is sending incorrect input and should confirm the input parameters are correct before retrying the request.

### 500’s : The server error codes

Often they indicate **problems with overwhelmed servers or unreachable servers behind proxies**, but sometimes they can be directly related to client requests that trigger error exceptions on the server. These errors can be temporary or permanent. Usually it’s best for the client to retry the same request.

## What is a status code 202?

This code tells the client that the request was valid, but its processing will finish sometime in the future.The response body **should include an URL to the finished resource with some information about when it will be available**, or an URL to some monitoring endpoint that tells the client when the resource is available.

## What is a status code 308?

**Permanent Redirect**, This **tells the client to use another URL to access the resource and not use the current URL anymore**. It’s helpful when we have multiple endpoints for one resource, but don’t want to implement reading from all of them.

## What code would you use if an update didn’t return data to a client?

**204 No Content**

## What code would you use if a resource used to exist but no longer does?

**410 Gone**

## What is the ‘Forbidden’ status code?

- The client has authorized or doesn’t need to authorize itself, but still has no permissions to access the resource.
