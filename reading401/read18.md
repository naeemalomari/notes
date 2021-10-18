## Web App Security
Many to Many Relationship
To create a many-to-many relationship, we need to:

Database Setup: for each entity, you have to create a table in database to implement the relations between them.
CREATE TABLE employee(employee_idint(11) NOT NULL AUTO_INCREMENT,first_namevarchar(50) DEFAULT NULL,last_name varchar(50) DEFAULT NULL, PRIMARY KEY (employee_id) ) ENGINE=InnoDB AUTO_INCREMENT=17 DEFAULT CHARSET=utf8; CREATE TABLE project(project_idint(11) NOT NULL AUTO_INCREMENT,title varchar(50) DEFAULT NULL, PRIMARY KEY (project_id) ) ENGINE=InnoDB AUTO_INCREMENT=18 DEFAULT CHARSET=utf8; CREATE TABLE employee_project(employee_idint(11) NOT NULL,project_id int(11) NOT NULL, PRIMARY KEY (employee_id,project_id), KEY project_id (project_id), CONSTRAINT employee_project_ibfk_1 FOREIGN KEY (employee_id) REFERENCES employee (employee_id), CONSTRAINT employee_project_ibfk_2 FOREIGN KEY (project_id) REFERENCES project (project_id) ) ENGINE=InnoDB DEFAULT CHARSET=utf8;

Use Model Classes: you have to create models with JPA annotations:
@Entity @Table(name = "Project") public class Project { @ManyToMany(mappedBy = "projects") private Set<Employee> employees = new HashSet<>();}

@Entity @Table(name = "Employee") public class Employee { @ManyToMany(cascade = { CascadeType.ALL }) @JoinTable( name = "Employee_Project", joinColumns = { @JoinColumn(name = "employee_id") }, inverseJoinColumns = { @JoinColumn(name = "project_id") } ) Set<Project> projects = new HashSet<>();}

The association between Employee class and Project classes is bidirectional.
In order to map a many-to-many association, we use the @ManyToMany, @JoinTable and @JoinColumn annotations
The @ManyToMany annotation is used in both classes to create the many-to-many relationship between the entities.
This association has two sides i.e. the owning side which is Employee in our example and the inverse side which is Project in our example.
The @JoinColumn annotation is used to specify the join/linking column with the main table.
Execution: `public class HibernateManyToManyAnnotationMainIntegrationTest { private static SessionFactory sessionFactory; private Session session;
// ...
@Test public void givenData_whenInsert_thenCreatesMtoMrelationship() { String[] employeeData = { "Peter Oven", "Allan Norman" }; String[] projectData = { "IT Project", "Networking Project" }; Set projects = new HashSet<>();
 for (String proj : projectData) {
     projects.add(new Project(proj));
 }
 for (String emp : employeeData) {
     Employee employee = new Employee(emp.split(" ")[0], 
       emp.split(" ")[1]);
     assertEquals(0, employee.getProjects().size());
     employee.setProjects(projects);
     session.persist(employee);
     assertNotNull(employee);
 }
}

@Test public void givenSession_whenRead_thenReturnsMtoMdata() { @SuppressWarnings("unchecked") List employeeList = session.createQuery("FROM Employee") .list();

 assertNotNull(employeeList);

 for(Employee employee : employeeList) {
     assertNotNull(employee.getProjects());
 }
}
// ... }`

Also, you can create mappings using Hibernate's many-to-many annotations, which is a more convenient counterpart compared to creating XML mapping files.

## This World of Ours

The writer points were about security especially authentication. For example, you have to use a strong password for your e-mail and accounts, and never share it with others, because it can lead for bad results such as hacking, criminal issues and even political purposes.