📝 Prisma Cheat Sheet: Simplify Database Operations with Prisma ORM 🛠️🐙

**Installation**:
Install Prisma CLI globally: `npm install -g prisma`

**1. Setting up Prisma**:
- Create a `prisma` folder with a `schema.prisma` file.
- Define data models using Prisma's schema syntax.

```prisma
model User {
id Int @id @default(autoincrement())
name String
email String @unique
posts Post[]
}

model Post {
id Int @id @default(autoincrement())
title String
content String?
author User @relation(fields: [authorId], references: [id])
authorId Int
}
```

**2. Generate Prisma Client**:
Generate Prisma Client to interact with the database:

```bash
prisma generate
```

**3. CRUD Operations**:
Perform basic Create, Read, Update, Delete operations with Prisma Client:

```typescript
import { PrismaClient } from '@prisma/client';

const prisma = new PrismaClient();

// Create
const newUser = await prisma.user.create({
data: {
name: 'John Doe',
email: 'john@example.com',
},
});

// Read
const user = await prisma.user.findUnique({
where: { id: 1 },
});

// Update
const updatedUser = await prisma.user.update({
where: { id: 1 },
data: { name: 'Updated Name' },
});

// Delete
const deletedUser = await prisma.user.delete({
where: { id: 1 },
});
```

**4. Advanced Queries**:
Utilize Prisma's powerful query capabilities:

```typescript
const usersWithPosts = await prisma.user.findMany({
include: { posts: true },
});

const specificPost = await prisma.post.findUnique({
where: { id: 1 },
include: { author: true },
});
```

**5. Relationships & Joins**:
Easily handle relationships and perform joins:

```typescript
const userWithPosts = await prisma.user.findUnique({
where: { id: 1 },
include: { posts: true },
});
```

Prisma makes database operations a breeze with its intuitive syntax and powerful features. Level up your backend development with the elegance of Prisma ORM! 🚀🔍💼 #PrismaORM #DatabaseMagic #ORMInAction #BackendDevelopment #WebDev #DatabaseManagement #CRUDOperations #QueryLikeAPro
