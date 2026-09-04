## Product Requirements
- CRUD app that allows users to store collections of notes for various books they are reading
- Also allows users to search up words in the dictionary as they are using the app (small mini-tool)
- Social features are out of scope

## Architecture

Frontend
- React

Backend
- Typescript
- NextJS
- ExpressJS

Database/ORM
- Prisma
- Postgres

## Schema

``` prisma
model User {
  id        Int      @id @default(autoincrement())
  email     String   @unique
  username  String?
  name      String?
  books     Book[]
}

model Book {
  id        Int      @id @default(autoincrement())
  title     String
  titleKey  String
  user      User     @relation(fields: [userId], references: [id])
  userId    Int
  notes     Note[]
}

model Note {
  id        Int      @id @default(autoincrement())
  title     String
  content   String
  book      Book     @relation(fields: [bookId], references: [id])
  bookId    Int
}
```

## API Endpoints
Reference: https://stackoverflow.blog/2020/03/02/best-practices-for-rest-api-design/

`/user`

`/book`

`/note`