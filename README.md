# Product Category REST API and AJAX

Spring Boot 3 exercise: Category REST API, Swagger 3 documentation, and Product/Category AJAX CRUD.

## Requirements

- Java 21 target, Maven, SQL Server 2019+.
- Create database: `CREATE DATABASE webst2;`
- Set credentials outside Git:

```powershell
$env:DB_USERNAME = "sa"
$env:DB_PASSWORD = "your-password"
```

The application uses `http://localhost:8082`, database `webst2`, and filesystem uploads in `uploads/`.

## Item 3 - Category REST API

- [x] Category CRUD with multipart icon upload.
- [x] Safe UUID image filenames, type/extension/size validation and traversal protection.
- [x] Duplicate-name protection, validation, centralized JSON errors and HTTP status codes.
- [x] Category search and paging: `GET /api/category/search?q=&page=0&size=10`.
- [x] Deletion is rejected if Products belong to the Category.

Category endpoints:

- `GET /api/category?q=`
- `POST /api/category/getCategory?id=`
- `POST /api/category/addCategory` (`categoryName`, optional `icon` multipart)
- `PUT /api/category/updateCategory` (`categoryId`, `categoryName`, optional `icon` multipart)
- `DELETE /api/category/deleteCategory?categoryId=`

All APIs return `{ "status", "message", "body" }`.

## Build and test

```powershell
mvn clean test
mvn clean package
mvn spring-boot:run
```

The automated test profile uses H2 only. Runtime uses SQL Server and requires `DB_PASSWORD` to be set. No password, uploads, PDFs, IDE settings or build output are committed.

## Planned items

- [ ] Item 4: Springdoc OpenAPI / Swagger 3 only (no Springfox or Swagger 2).
- [ ] Item 5: Product API and Thymeleaf + jQuery/AJAX pages.
