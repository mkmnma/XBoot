# 🔧 XBoot: A Prototype-Oriented DSL for Secure and Modular Spring Boot Application Generation

**XBoot** is a low-code DSL based tool that generates secure, layered Spring Boot applications from XML specifications. It’s ideal for rapid prototyping and for students and educators learning backend development patterns using Spring Boot.

## 📁 Project Structure

```
xboot/
├── input/           # Place your XML application specification here
├── output/          # Generated Spring Boot projects appear here
├── schema/
│   └── XBootSchema.xsd  # XML schema to validate input specifications
└── xboot.jar        # The generator executable
```

## ✅ Prerequisites

To run XBoot, you need:

- **Java 17 or higher**
- (Optional) **Maven** (for building generated Spring Boot projects)
- An IDE like **Eclipse** or **IntelliJ** (optional but recommended)

## 🚀 How to Use

1. **Write Your XML Spec**

   Create an XML file describing your Spring Boot app and save it to the `input/` directory.

   Example: `input/StudentCourses.xml`

2. **Validate Your XML (Optional)**

   You can validate your file against `schema/XBootSchema.xsd` using any XML validator to ensure correctness.

3. **Run the Generator**

   In terminal or command prompt, navigate to the `xboot/` folder and run:

   ```bash
   java -jar xboot.jar
   ```

   This will:
   - Read your XML from `input/`
   - Generate a fully structured Spring Boot application into `output/YourAppName/`

4. **Open or Build the App**

   - Open the project from `output/YourAppName/` in your IDE
   - Or run from terminal:
     ```bash
     cd output/YourAppName
     mvn spring-boot:run
     ```

## 📌 Features

- Generates:
  - REST controllers
  - View controllers with Thymeleaf
  - Entity classes, services, repositories
  - `pom.xml` with required dependencies (JPA, Thymeleaf, Security, Swagger, Validation)
  - Swagger UI, CSRF, and role-based security
- Supports:
  - One-to-many and many-to-one relationships
  - Route and role mapping
  - Bootstrap-styled HTML templates
  - Login/logout with Spring Security (default login page)

## 📂 Example XML DSL (StudentCourses)
you might also use the helper XBoot GPT to generate XML DSL from natural language text description, can be accessed  at : https://chatgpt.com/g/g-68761e073534819184c9f4b78c688544-xboot-dsl-generator

XBoot XML DSL Example:
```xml
<Application name="StudentCourses">
  <Entity name="Student">
    <Field name="name" type="String" required="true"/>
    <Field name="email" type="String"/>
  </Entity>
  <Entity name="Course">
    <Field name="title" type="String"/>
  </Entity>
  <Entity name="Enrollment">
    <Field name="grade" type="String"/>
    <Relation field="student" type="Student" kind="ManyToOne"/>
    <Relation field="course" type="Course" kind="ManyToOne"/>
  </Entity>
</Application>
```

## 🧪 Output Preview

- `pom.xml`: Complete Maven config with dependencies like `spring-boot-starter-thymeleaf`, `spring-boot-starter-security`, `thymeleaf-extras-springsecurity6`
- `SecurityConfig.java`: Enables CSRF, login/logout support, role-based protection
- Thymeleaf templates: Bootstrap-styled with form validation and logout support
- Controllers, Services, Repositories: Fully generated per entity
