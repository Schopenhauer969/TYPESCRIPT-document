# 📘 TypeScript — មគ្គុទ្ទេសក៍ពេញលេញជាភាសាខ្មែរ

> ចាប់ពីកម្រិតដំបូង រហូតដល់កម្រិតខ្ពស់ · From Beginner to Advanced

[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-3178C6?style=flat-square&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg?style=flat-square)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](CONTRIBUTING.md)

---

## 📚 តារាងមាតិកា

- [🎯 សេចក្តីណែនាំ](#-សេចក្តីណែនាំ)
- [💻 ការដំឡើង](#-ការដំឡើង)
- [🟢 កម្រិតដំបូង (Beginner)](#-កម្រិតដំបូង-beginner)
  - [ប្រភេទមូលដ្ឋាន](#ប្រភេទមូលដ្ឋាន)
  - [អថេរ](#អថេរ)
  - [អនុគមន៍មូលដ្ឋាន](#អនុគមន៍មូលដ្ឋាន)
- [🟡 កម្រិតមធ្យម (Intermediate)](#-កម្រិតមធ្យម-intermediate)
  - [Interfaces](#interfaces)
  - [ថ្នាក់ Classes](#ថ្នាក់-classes)
  - [Generics](#generics)
- [🔴 កម្រិតខ្ពស់ (Advanced)](#-កម្រិតខ្ពស់-advanced)
  - [Advanced Types](#advanced-types)
  - [Decorators](#decorators)
  - [Utility Types](#utility-types)
  - [Declaration Merging](#declaration-merging)
  - [Module Augmentation](#module-augmentation)
- [⚙️ tsconfig.json](#️-tsconfigjson)
- [✅ បច្ចេកទេសល្អបំផុត](#-បច្ចេកទេសល្អបំផុត)
- [📚 ធនធានបន្ថែម](#-ធនធានបន្ថែម)

---

## 🎯 សេចក្តីណែនាំ

**TypeScript** គឺជា **superset** នៃ JavaScript ដែលបន្ថែម **ប្រព័ន្ធប្រភេទ** (static typing) ។ Microsoft បានបង្កើតវាក្នុងឆ្នាំ ២០១២ ដើម្បីផ្តល់ **សុវត្ថិភាពលើកូដ** និង **ជំនួយ IDE** កាន់តែប្រសើរ។

**ហេតុអ្វីត្រូវប្រើ TypeScript?**

| លក្ខណៈ | JavaScript | TypeScript |
|--------|-----------|-----------|
| ការរកកំហុស | Runtime | Compile-time ✅ |
| Autocomplete | មានកំណត់ | ពេញលេញ ✅ |
| Refactoring | ពិបាក | ងាយស្រួល ✅ |
| Documentation | ដោយដៃ | Auto-generated ✅ |

```typescript
// JavaScript — ដឹងកំហុសសុំតែ runtime
function add(a, b) { return a + b; }
add("hello", 5);  // ❌ bug ប៉ុន្តែ JS មិនប្រាប់

// TypeScript — ដឹងកំហុសភ្លាមៗ
function add(a: number, b: number): number { return a + b; }
add("hello", 5);  // ❌ Error: Argument of type 'string' is not assignable
```

---

## 💻 ការដំឡើង

### តម្រូវការ

- **Node.js** v18+ → [nodejs.org](https://nodejs.org)
- **npm** v9+ (មកជាមួយ Node.js)

### ជំហានដំឡើង

```bash
# ១. ដំឡើង TypeScript globally
npm install -g typescript

# ២. ពិនិត្យកំណែ
tsc --version
# Output: Version 5.x.x

# ៣. បង្កើតគម្រោងថ្មី
mkdir my-ts-project && cd my-ts-project
npm init -y
npm install --save-dev typescript @types/node

# ៤. បង្កើត tsconfig.json
npx tsc --init
```

### រចនាសម្ព័ន្ធគម្រោង

```
my-ts-project/
├── src/
│   ├── index.ts
│   └── utils/
│       └── helpers.ts
├── dist/          ← JavaScript output
├── tsconfig.json
└── package.json
```

### ដំណើរការ

```bash
# Compile ម្តង
npx tsc

# Watch mode (compile ស្វ័យប្រវត្តិ)
npx tsc --watch

# ដំណើរការ TypeScript ផ្ទាល់ (dev only)
npx ts-node src/index.ts
```

---

## 🟢 កម្រិតដំបូង (Beginner)

### ប្រភេទមូលដ្ឋាន

TypeScript មានប្រភេទ built-in ៨ ដូចខាងក្រោម៖

```typescript
// ── String (អក្សរ) ──────────────────────────────────
const name: string = "វណ្ណៈ";
const greeting: string = `ជំរាបសួរ, ${name}!`;  // template literal

// ── Number (លេខ) ───────────────────────────────────
const age: number = 25;
const price: number = 9.99;
const hex: number = 0xFF;    // hexadecimal
const big: number = 1_000_000;  // separator សម្រាប់ងាយអាន

// ── Boolean (ពិត/មិនពិត) ───────────────────────────
const isStudent: boolean = true;
const hasPassed: boolean = false;

// ── Array (អារ៉េ) ───────────────────────────────────
const scores: number[] = [85, 90, 78];
const names: Array<string> = [" សុខ", "ដារា", "វិចិត្រ"];

// ── Tuple (អារ៉េកំណត់ប្រភេទ) ────────────────────────
const coordinate: [number, number] = [11.55, 104.92];  // Phnom Penh
const person: [string, number, boolean] = ["ដារា", 22, true];

// ── Null & Undefined ────────────────────────────────
let empty: null = null;
let notDefined: undefined = undefined;

// ── Symbol ──────────────────────────────────────────
const id: symbol = Symbol("unique-id");
```

### Union & Literal Types

```typescript
// Union Type — ទទួលប្រភេទច្រើន
let value: string | number = "hello";
value = 42;  // ✅ ត្រូវ

// Literal Type — តម្លៃជាក់លាក់
type Direction = "north" | "south" | "east" | "west";
let move: Direction = "north";  // ✅
// move = "up";  // ❌ Error

// Nullable
function findUser(id: number): string | null {
  if (id === 1) return "ដារា";
  return null;
}
```

### Any, Unknown, Never, Void

```typescript
// any — បិទ type checking (ជៀសវាង!)
let anything: any = "hello";
anything = 42;
anything.methodThatDoesNotExist();  // ✅ no error (DANGEROUS!)

// unknown — ប្រសើរជាង any (safe)
let userInput: unknown = "hello";
if (typeof userInput === "string") {
  console.log(userInput.toUpperCase());  // ✅ safe
}

// void — អនុគមន៍មិនត្រឡប់ value
function log(message: string): void {
  console.log(message);
}

// never — មិនដែលត្រឡប់ (throw error ឬ infinite loop)
function throwError(message: string): never {
  throw new Error(message);
}
```

---

### អថេរ

```typescript
// const — មិនអាចប្តូរ reference (ប្រើដូច default)
const MAX_SIZE = 100;

// let — អាចប្តូរ
let count = 0;
count++;

// Type Inference — TypeScript ស្មានប្រភេទដោយខ្លួនឯង
const message = "hello";  // inferred: string
const num = 42;           // inferred: number
const arr = [1, 2, 3];    // inferred: number[]

// Type Assertion — ប្រាប់ compiler ឱ្យជឿ
const input = document.getElementById("input") as HTMLInputElement;
const value = (input).value;  // alternative syntax
```

---

### អនុគមន៍មូលដ្ឋាន

```typescript
// ── Function Declaration ────────────────────────────
function greet(name: string): string {
  return `ជំរាបសួរ, ${name}!`;
}

// ── Arrow Function ──────────────────────────────────
const add = (a: number, b: number): number => a + b;

// ── Optional Parameter (ប្រើ ?)  ────────────────────
function createUser(name: string, age?: number): string {
  return age ? `${name} (${age})` : name;
}
createUser("ដារា");       // ✅
createUser("ដារា", 25);  // ✅

// ── Default Parameter ───────────────────────────────
function multiply(a: number, b: number = 2): number {
  return a * b;
}
multiply(5);    // 10
multiply(5, 3); // 15

// ── Rest Parameter ──────────────────────────────────
function sum(...numbers: number[]): number {
  return numbers.reduce((total, n) => total + n, 0);
}
sum(1, 2, 3, 4, 5);  // 15

// ── Function Overloading ────────────────────────────
function format(value: string): string;
function format(value: number): string;
function format(value: string | number): string {
  return String(value).trim();
}
```

---

## 🟡 កម្រិតមធ្យម (Intermediate)

### Interfaces

Interface ជាការ**កំណត់ contract** នៃ object structure ។

```typescript
// ── Interface មូលដ្ឋាន ─────────────────────────────
interface User {
  id: number;
  name: string;
  email: string;
  age?: number;           // optional
  readonly createdAt: Date; // read-only
}

// ── Method ក្នង Interface ───────────────────────────
interface Repository<T> {
  findById(id: number): T | null;
  findAll(): T[];
  save(entity: T): void;
  delete(id: number): boolean;
}

// ── Interface Extending ─────────────────────────────
interface Animal {
  name: string;
  sound(): string;
}

interface Pet extends Animal {
  owner: string;
}

interface Dog extends Pet {
  breed: string;
}

const myDog: Dog = {
  name: "ប៉ូលី",
  owner: "ដារា",
  breed: "Golden Retriever",
  sound: () => "ហ្វូ ហ្វូ!"
};

// ── Index Signature ─────────────────────────────────
interface StringMap {
  [key: string]: string;
}

const translations: StringMap = {
  hello: "ជំរាបសួរ",
  goodbye: "លា​សិន​ហើយ",
  thanks: "អរគុណ"
};
```

---

### ថ្នាក់ Classes

```typescript
// ── Class មូលដ្ឋាន ────────────────────────────────
class Person {
  public name: string;       // accessible everywhere
  private age: number;       // class only
  protected email: string;   // class + subclasses
  readonly id: number;       // cannot reassign

  constructor(name: string, age: number, email: string) {
    this.name = name;
    this.age = age;
    this.email = email;
    this.id = Math.random();
  }

  // Getter
  get info(): string {
    return `${this.name} (${this.age})`;
  }

  // Setter
  set newAge(age: number) {
    if (age < 0) throw new Error("អាយុមិនអាចអវិជ្ជមាន");
    this.age = age;
  }

  introduce(): void {
    console.log(`ខ្ញុំឈ្មោះ ${this.name}, អាយុ ${this.age} ឆ្នាំ`);
  }
}

// ── Shorthand Constructor ────────────────────────────
class Point {
  constructor(
    public x: number,
    public y: number,
    private label: string = "point"
  ) {}

  toString(): string {
    return `${this.label}(${this.x}, ${this.y})`;
  }
}

// ── Inheritance ──────────────────────────────────────
class Student extends Person {
  constructor(
    name: string,
    age: number,
    email: string,
    public studentId: string
  ) {
    super(name, age, email);  // ហៅ parent constructor
  }

  study(subject: string): void {
    console.log(`${this.name} កំពុងរៀន ${subject}`);
  }
}

// ── Abstract Class ───────────────────────────────────
abstract class Shape {
  abstract area(): number;      // must be implemented
  abstract perimeter(): number; // must be implemented

  describe(): string {
    return `ផ្ទៃ: ${this.area().toFixed(2)}, ខ្សែរង្វង់: ${this.perimeter().toFixed(2)}`;
  }
}

class Circle extends Shape {
  constructor(private radius: number) { super(); }

  area(): number { return Math.PI * this.radius ** 2; }
  perimeter(): number { return 2 * Math.PI * this.radius; }
}

class Rectangle extends Shape {
  constructor(private width: number, private height: number) { super(); }

  area(): number { return this.width * this.height; }
  perimeter(): number { return 2 * (this.width + this.height); }
}

// ── Interface Implementation ─────────────────────────
interface Serializable {
  toJSON(): string;
  fromJSON(json: string): void;
}

class Config implements Serializable {
  constructor(public settings: Record<string, unknown> = {}) {}

  toJSON(): string { return JSON.stringify(this.settings); }
  fromJSON(json: string): void { this.settings = JSON.parse(json); }
}
```

---

### Generics

Generics ផ្តល់ **flexibility** ដោយមិនបាត់ type safety ។

```typescript
// ── Generic Function ─────────────────────────────────
function identity<T>(value: T): T {
  return value;
}
identity<string>("hello");  // explicit
identity(42);               // inferred: number

// ── Generic with Constraint ──────────────────────────
function getProperty<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}

const user = { name: "ដារា", age: 25 };
getProperty(user, "name");  // "ដារា"
// getProperty(user, "email");  // ❌ Error

// ── Generic Interface ────────────────────────────────
interface ApiResponse<T> {
  data: T;
  status: number;
  message: string;
  timestamp: Date;
}

interface UserData {
  id: number;
  name: string;
}

const response: ApiResponse<UserData> = {
  data: { id: 1, name: "ដារា" },
  status: 200,
  message: "Success",
  timestamp: new Date()
};

// ── Generic Class ────────────────────────────────────
class Stack<T> {
  private items: T[] = [];

  push(item: T): void {
    this.items.push(item);
  }

  pop(): T | undefined {
    return this.items.pop();
  }

  peek(): T | undefined {
    return this.items[this.items.length - 1];
  }

  get size(): number {
    return this.items.length;
  }

  isEmpty(): boolean {
    return this.items.length === 0;
  }
}

const numStack = new Stack<number>();
numStack.push(1);
numStack.push(2);
numStack.pop();  // 2

// ── Multiple Type Parameters ─────────────────────────
function pair<K, V>(key: K, value: V): [K, V] {
  return [key, value];
}

pair("name", "ដារា");    // [string, string]
pair(1, true);           // [number, boolean]
```

---

## 🔴 កម្រិតខ្ពស់ (Advanced)

### Advanced Types

```typescript
// ── Conditional Types ────────────────────────────────
type IsString<T> = T extends string ? true : false;
type A = IsString<string>;  // true
type B = IsString<number>;  // false

// Infer keyword
type ReturnType<T> = T extends (...args: unknown[]) => infer R ? R : never;
type Fn = () => string;
type R = ReturnType<Fn>;  // string

// ── Mapped Types ─────────────────────────────────────
type Optional<T> = {
  [K in keyof T]?: T[K];
};

type ReadOnly<T> = {
  readonly [K in keyof T]: T[K];
};

type Nullable<T> = {
  [K in keyof T]: T[K] | null;
};

interface Config {
  host: string;
  port: number;
  debug: boolean;
}

type OptionalConfig = Optional<Config>;
// { host?: string; port?: number; debug?: boolean; }

// ── Template Literal Types ───────────────────────────
type EventName = "click" | "focus" | "blur";
type Handler = `on${Capitalize<EventName>}`;
// "onClick" | "onFocus" | "onBlur"

type CSSProperty = "margin" | "padding";
type CSSDirection = "top" | "bottom" | "left" | "right";
type CSSValue = `${CSSProperty}-${CSSDirection}`;
// "margin-top" | "margin-bottom" | ... | "padding-right"

// ── Discriminated Unions ─────────────────────────────
type Shape =
  | { kind: "circle"; radius: number }
  | { kind: "rectangle"; width: number; height: number }
  | { kind: "triangle"; base: number; height: number };

function calculateArea(shape: Shape): number {
  switch (shape.kind) {
    case "circle":
      return Math.PI * shape.radius ** 2;
    case "rectangle":
      return shape.width * shape.height;
    case "triangle":
      return (shape.base * shape.height) / 2;
  }
}

// ── Intersection Types ───────────────────────────────
type Timestamped = {
  createdAt: Date;
  updatedAt: Date;
};

type Identifiable = {
  id: number;
};

type Entity<T> = T & Timestamped & Identifiable;

type UserEntity = Entity<{ name: string; email: string }>;
// { name: string; email: string; createdAt: Date; updatedAt: Date; id: number }
```

---

### Decorators

Decorators ផ្តល់ **metadata** និង **behavior modification** ។

> ⚠️ ត្រូវបើក `"experimentalDecorators": true` ក្នង `tsconfig.json`

```typescript
// ── Class Decorator ──────────────────────────────────
function Singleton<T extends new (...args: unknown[]) => unknown>(Base: T) {
  let instance: InstanceType<T>;
  return class extends Base {
    constructor(...args: unknown[]) {
      if (instance) return instance;
      super(...args);
      instance = this as InstanceType<T>;
    }
  };
}

@Singleton
class Database {
  constructor(public url: string) {
    console.log("Connecting to:", url);
  }
}

// ── Method Decorator ─────────────────────────────────
function Log(target: unknown, key: string, descriptor: PropertyDescriptor) {
  const original = descriptor.value;
  descriptor.value = function (...args: unknown[]) {
    console.log(`Calling ${key} with`, args);
    const result = original.apply(this, args);
    console.log(`${key} returned`, result);
    return result;
  };
  return descriptor;
}

// ── Property Decorator ───────────────────────────────
function Required(target: unknown, key: string) {
  let value: unknown;
  const getter = () => value;
  const setter = (newVal: unknown) => {
    if (newVal === null || newVal === undefined) {
      throw new Error(`${key} is required`);
    }
    value = newVal;
  };
  Object.defineProperty(target, key, { get: getter, set: setter });
}

class UserService {
  @Required
  username!: string;

  @Log
  getUser(id: number): string {
    return `User #${id}`;
  }
}
```

---

### Utility Types

TypeScript ភ្ជាប់មក **built-in utility types** ជាច្រើន។

```typescript
interface User {
  id: number;
  name: string;
  email: string;
  age: number;
  role: "admin" | "user" | "moderator";
}

// Partial<T> — fields ទាំងអស់ optional
type UpdateUser = Partial<User>;
// { id?: number; name?: string; email?: string; ... }

// Required<T> — fields ទាំងអស់ required
type StrictUser = Required<User>;

// Readonly<T> — fields ទាំងអស់ read-only
type ImmutableUser = Readonly<User>;

// Pick<T, K> — ជ្រើស fields ជាក់លាក់
type UserPreview = Pick<User, "id" | "name">;
// { id: number; name: string; }

// Omit<T, K> — ដក fields ជាក់លាក់ចេញ
type PublicUser = Omit<User, "email" | "age">;
// { id: number; name: string; role: ... }

// Record<K, V> — object type ជាមួយ key/value
type UserMap = Record<string, User>;
type RolePermissions = Record<User["role"], string[]>;

// Exclude<T, U> — ដកប្រភេទចេញពី union
type NonAdminRole = Exclude<User["role"], "admin">;
// "user" | "moderator"

// Extract<T, U> — ចំណាញប្រភេទពី union
type AdminOnly = Extract<User["role"], "admin" | "superadmin">;
// "admin"

// NonNullable<T> — ដក null/undefined
type SafeString = NonNullable<string | null | undefined>;
// string

// ReturnType<T> — ប្រភេទ return value របស់ function
function fetchUser(): Promise<User> {
  return Promise.resolve({ id: 1, name: "ដារា", email: "", age: 25, role: "user" });
}
type FetchReturn = ReturnType<typeof fetchUser>;
// Promise<User>

// Parameters<T> — ប្រភេទ parameters របស់ function
function createPost(title: string, content: string, tags: string[]): void {}
type PostParams = Parameters<typeof createPost>;
// [string, string, string[]]

// ConstructorParameters<T> — parameters នៃ constructor
class HttpClient {
  constructor(
    private baseUrl: string,
    private timeout: number = 5000
  ) {}
}
type ClientParams = ConstructorParameters<typeof HttpClient>;
// [string, number?]
```

---

### Declaration Merging

```typescript
// ── Interface Merging ────────────────────────────────
interface Window {
  myCustomProperty: string;
}

interface Window {
  anotherProperty: number;
}

// ឥឡូវ Window មាន: myCustomProperty, anotherProperty + originals

// ── Namespace Merging ────────────────────────────────
namespace Validation {
  export interface StringValidator {
    isAcceptable(s: string): boolean;
  }
}

namespace Validation {
  export class LettersOnlyValidator implements StringValidator {
    isAcceptable(s: string) {
      return /^[A-Za-z]+$/.test(s);
    }
  }
}

// ── Enum Merging (via const assertion) ──────────────
const HttpStatus = {
  OK: 200,
  NOT_FOUND: 404,
  INTERNAL_ERROR: 500
} as const;

type HttpStatus = typeof HttpStatus[keyof typeof HttpStatus];
// 200 | 404 | 500
```

---

### Module Augmentation

```typescript
// ── Augment existing module ──────────────────────────
// file: global.d.ts
declare global {
  interface Array<T> {
    last(): T | undefined;
    groupBy<K extends string>(fn: (item: T) => K): Record<K, T[]>;
  }
}

// implementation
Array.prototype.last = function () {
  return this[this.length - 1];
};

// ── Augment third-party types ────────────────────────
// file: express.d.ts
import "express";

declare module "express" {
  interface Request {
    user?: { id: string; role: string };
    requestId: string;
  }
}
```

---

## ⚙️ tsconfig.json

```jsonc
{
  "compilerOptions": {
    // ── Output ──────────────────────────────────────
    "target": "ES2022",          // JavaScript version output
    "module": "commonjs",        // module system
    "outDir": "./dist",          // output folder
    "rootDir": "./src",          // source folder
    "declaration": true,         // generate .d.ts files
    "declarationMap": true,      // source maps for declarations
    "sourceMap": true,           // source maps for debugging

    // ── Type Checking (ណែនាំឱ្យបើករាល់!) ───────────
    "strict": true,              // enable all strict checks
    "noImplicitAny": true,       // no implicit any
    "strictNullChecks": true,    // null/undefined checks
    "strictFunctionTypes": true, // function type checking
    "noUnusedLocals": true,      // error on unused variables
    "noUnusedParameters": true,  // error on unused params
    "noImplicitReturns": true,   // all paths must return
    "noFallthroughCasesInSwitch": true,

    // ── Module Resolution ────────────────────────────
    "moduleResolution": "node",
    "baseUrl": ".",
    "paths": {
      "@/*": ["src/*"],
      "@utils/*": ["src/utils/*"]
    },
    "esModuleInterop": true,
    "allowSyntheticDefaultImports": true,

    // ── Advanced ─────────────────────────────────────
    "experimentalDecorators": true,
    "emitDecoratorMetadata": true,
    "resolveJsonModule": true,
    "skipLibCheck": true
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules", "dist", "**/*.test.ts"]
}
```

---

## ✅ បច្ចេកទេសល្អបំផុត

### ១. ជៀសវាង `any` ប្រើ `unknown` ជំនួស

```typescript
// ❌ មិនល្អ — បិទ type checking
function process(data: any) {
  return data.user.name;  // crash ដោយមិនដឹង
}

// ✅ ល្អ — safe type narrowing
function process(data: unknown) {
  if (
    typeof data === "object" &&
    data !== null &&
    "user" in data
  ) {
    const d = data as { user: { name: string } };
    return d.user.name;
  }
  throw new Error("Invalid data structure");
}
```

### ២. ប្រើ `const assertions`

```typescript
// ❌ inferred as string[]
const ROLES = ["admin", "user", "moderator"];

// ✅ inferred as readonly ["admin", "user", "moderator"]
const ROLES = ["admin", "user", "moderator"] as const;
type Role = typeof ROLES[number];  // "admin" | "user" | "moderator"
```

### ៣. Type Guards

```typescript
// Custom type guard
function isUser(value: unknown): value is User {
  return (
    typeof value === "object" &&
    value !== null &&
    "id" in value &&
    "name" in value
  );
}

if (isUser(response.data)) {
  console.log(response.data.name);  // TypeScript ដឹងថា data ជា User
}
```

### ៤. Error Handling ត្រឹមត្រូវ

```typescript
// ✅ Typed errors
class AppError extends Error {
  constructor(
    message: string,
    public code: string,
    public statusCode: number = 500
  ) {
    super(message);
    this.name = "AppError";
  }
}

async function fetchData<T>(url: string): Promise<T> {
  try {
    const res = await fetch(url);
    if (!res.ok) {
      throw new AppError(`HTTP Error`, "FETCH_FAILED", res.status);
    }
    return res.json() as Promise<T>;
  } catch (error) {
    if (error instanceof AppError) throw error;
    throw new AppError("Unknown error", "UNKNOWN");
  }
}
```

### ៥. Immutability

```typescript
// ✅ ប្រើ readonly arrays/objects
function sortNumbers(numbers: readonly number[]): number[] {
  return [...numbers].sort((a, b) => a - b);  // copy ជំនួស mutate
}

// Object.freeze + const assertion
const CONFIG = Object.freeze({
  apiUrl: "https://api.example.com",
  timeout: 5000,
} as const);
```

---

## 📚 ធនធានបន្ថែម

| ធនធាន | តំណភ្ជាប់ | ការពិពណ៌នា |
|-------|---------|-----------|
| 📖 Official Docs | [typescriptlang.org](https://www.typescriptlang.org/docs/) | ឯកសារផ្លូវការ |
| 🎮 Playground | [typescriptlang.org/play](https://www.typescriptlang.org/play) | សាកល្បង online |
| 📘 TypeScript Deep Dive | [basarat.gitbook.io](https://basarat.gitbook.io/typescript/) | ណែនាំស៊ីជម្រៅ |
| 🧩 Type Challenges | [github.com/type-challenges](https://github.com/type-challenges/type-challenges) | លំហាត់ Advanced |
| 🎯 Total TypeScript | [totaltypescript.com](https://www.totaltypescript.com) | វគ្គសិក្សា |

---

## 🤝 ការចូលរួម

PR និង Issues ត្រូវបានស្វាគមន៍! សូមមើល [CONTRIBUTING.md](CONTRIBUTING.md) ។

---

<div align="center">

**ទំនាក់ទំនង:** info@example.com · **កំណែ:** 2.0.0 · **ថ្ងៃធ្វើបច្ចុប្បន្នភាព:** 2025

*ឯកសារនេះត្រូវបានរៀបចំដោយស្នើទ្នងសម្រាប់អ្នករៀន TypeScript ជាភាសាខ្មែរ*

</div>
