# TypeScript - ការណែនាំលម្អិត

## 📚 តារាងមាតិកា
- [សេចក្តីណែនាំ](#សេចក្តីណែនាំ)
- [ការដំឡើង](#ការដំឡើង)
- [ការចាប់ផ្តើម](#ការចាប់ផ្តើម)
- [ប្រព័ន្ធប្រភេទ](#ប្រព័ន្ធប្រភេទ)
- [អនុគមន៍](#អនុគមន៍)
- [ឧបករណ៍ (Interfaces)](#ឧបករណ៍)
- [ថ្នាក់ (Classes)](#ថ្នាក់)
- [បច្ចេកទេសល្អបំផុត](#បច្ចេកទេសល្អបំផុត)

---

## 🎯 សេចក្តីណែនាំ

**TypeScript** ជាភាសាសរសេរកម្មវិធីដែលបង្កើតលើ **JavaScript** ដោយបានបន្ថែមលក្ខណៈពិសេស **ប្រព័ន្ធប្រភេទ** (Type System)។ វាផ្តល់នូវ:

- ✅ ស្វែងរកកំហុសមុនពេលដំណើរការកម្មវិធី
- ✅ ធានាលក្ខណៈសម្បត្តិនៃកូដកាន់តែល្អ
- ✅ ធានាលក្ខណៈសម្បត្តិក្នងពេលវេលាលូត
- ✅ អនុលោមលម្អិតលម្អិតលម្អិតអំពីកូដ

### ឧទាហរណ៍សាមញ្ញ
```typescript
// ប្រកាស់ប្រភេទអថេរ
const greeting: string = "សូស្វាគមន៍ TypeScript";
const age: number = 25;
const isActive: boolean = true;

console.log(greeting); // លទ្ធផល: សូស្វាគមន៍ TypeScript
```

---

## 💻 ការដំឡើង

### តម្រូវការ
- **Node.js** v14 ឬលើសពីនេះ
- **npm** ឬ **yarn**

### ជំហាន ១: ដំឡើង TypeScript ក្នងលម្អិតលម្អិត
```bash
npm install -g typescript
```

### ជំហាន ២: ពិនិត្យមើលកំណែ
```bash
tsc --version
```

### ជំហាន ៣: បង្កើតគម្រោង TypeScript ថ្មី
```bash
mkdir my-typescript-project
cd my-typescript-project
npm init -y
npm install --save-dev typescript
```

### ជំហាន ៤: បង្កើតឯកសារកំណត់រចនាសម្ព័ន្ធ
```bash
npx tsc --init
```

នេះនឹងបង្កើតឯកសារ `tsconfig.json` សម្រាប់កំណត់រចនាសម្ព័ន្ធគម្រោង។

---

## 🚀 ការចាប់ផ្តើម

### ឯកសារមូលដ្ឋាន
បង្កើតឯកសារ `index.ts`:

```typescript
function greetUser(name: string): void {
  console.log(`សូស្វាគមន៍, ${name}!`);
}

greetUser("សុខ");  // ✅ ត្រូវ
// greetUser(123);  // ❌ កំហុស - ត្រូវប្រភេទ string
```

### ដំណើរការកម្មវិធី
```bash
# បកប្រែ TypeScript ទៅ JavaScript
npx tsc

# រើស ឯកសារ JavaScript ដែលបានបង្កើត
node index.js
```

---

## 🔧 ប្រព័ន្ធប្រភេទ

TypeScript ប្រើប្រភេទដើម្បីស្វែងរក និងខ្វើលកំហុស មុនពេលដំណើរការកម្មវិធី។

### ប្រភេទមូលដ្ឋាន

#### ១. String (អក្សរ)
```typescript
const name: string = "សុខ";
const message: string = `សូស្វាគមន៍, ${name}`;
```

#### ២. Number (លេខ)
```typescript
const age: number = 25;
const price: number = 99.99;
const negative: number = -10;
```

#### ៣. Boolean (ពិត/មិនពិត)
```typescript
const isStudent: boolean = true;
const isGraduated: boolean = false;
```

#### ៤. Array (ម៉ាទ្រីស)
```typescript
// វិធីទី 1
const numbers: number[] = [1, 2, 3, 4, 5];

// វិធីទី 2
const strings: Array<string> = ["A", "B", "C"];

// ម៉ាទ្រីសលាយ
const mixed: (string | number)[] = [1, "ពីរ", 3, "បួន"];
```

#### ៥. Any (ទទួលយករៀងល្អ)
```typescript
let value: any = "អក្សរ";
value = 42;          // ✅ ត្រូវ
value = true;        // ✅ ត្រូវ
```

#### ៦. Union Type (ប្រភេទឆ្លាស់)
```typescript
const id: string | number = 123;  // ✅ ត្រូវ
let status: "active" | "inactive" = "active";  // ✅ ត្រូវ
```

#### ៧. Tuple (ម៉ាទ្រីសនៃប្រភេទកំណត់)
```typescript
const tuple: [string, number] = ["សុខ", 25];
const tuple2: [string, number, boolean] = ["ឈ្មោះ", 30, true];
```

---

## 📋 អនុគមន៍

### អនុគមន៍មូលដ្ឋាន
```typescript
function add(a: number, b: number): number {
  return a + b;
}

const result = add(5, 3);  // លទ្ធផល: 8
```

### ប្រាក់ឥណទាននៃប៉ារ៉ាម៉ែត្រ (Optional Parameters)
```typescript
function greet(firstName: string, lastName?: string): void {
  if (lastName) {
    console.log(`សូស្វាគមន៍ ${firstName} ${lastName}`);
  } else {
    console.log(`សូស្វាគមន៍ ${firstName}`);
  }
}

greet("សុខ");           // ✅ ត្រូវ
greet("សុខ", "វង្ស");  // ✅ ត្រូវ
```

### តម្លៃលម្អិតលម្អិត (Default Parameters)
```typescript
function multiply(a: number, b: number = 2): number {
  return a * b;
}

console.log(multiply(5));      // លទ្ធផល: 10 (5 × 2)
console.log(multiply(5, 3));   // លទ្ធផល: 15 (5 × 3)
```

### ប៉ារ៉ាម៉ែត្របន្សំ (Rest Parameters)
```typescript
function sumNumbers(...numbers: number[]): number {
  return numbers.reduce((sum, num) => sum + num, 0);
}

console.log(sumNumbers(1, 2, 3, 4, 5));  // លទ្ធផល: 15
```

### អនុគមន៍ព្រួញ (Arrow Functions)
```typescript
const multiply = (x: number, y: number): number => x * y;

const greetUser = (name: string): string => `សូស្វាគមន៍, ${name}`;

console.log(multiply(4, 5));  // លទ្ធផល: 20
```

---

## 🏗️ ឧបករណ៍ (Interfaces)

Interfaces ប្រើប្រាស់ដើម្បីកំណត់រចនាសម្ព័ន្ធ និងលក្ខណៈសម្បត្តិនៃវត្ថុ។

### ឧទាហរណ៍មូលដ្ឋាន
```typescript
interface User {
  id: number;
  name: string;
  email: string;
}

const user: User = {
  id: 1,
  name: "សុខ",
  email: "sokh@example.com"
};
```

### ប៉ារ៉ាម៉ែត្របន្ថែម (Optional Properties)
```typescript
interface Product {
  id: number;
  name: string;
  description?: string;  // ឯកសារលម្អិតលម្អិត (ប្រើបានឬទេ)
  price: number;
}

const product: Product = {
  id: 1,
  name: "ឧបករណ៍",
  price: 99.99
  // description មិនចាំបាច់បង់ប្រាក់
};
```

### ប៉ារ៉ាម៉ែត្រមិនផ្លាស់ប្តូរ (Readonly Properties)
```typescript
interface AppConfig {
  readonly apiKey: string;
  readonly maxRetries: number;
}

const config: AppConfig = {
  apiKey: "secret123",
  maxRetries: 3
};

// config.apiKey = "newkey";  // ❌ កំហុស - ឯកសារលម្អិតលម្អិត
```

### វិធីសាស្ត្របង្វង (Methods in Interfaces)
```typescript
interface Animal {
  name: string;
  makeSound(): void;
}

const dog: Animal = {
  name: "ឡើង",
  makeSound() {
    console.log("ឆ្នោតឆ្នោត");
  }
};

dog.makeSound();  // លទ្ធផល: ឆ្នោតឆ្នោត
```

---

## 🎓 ថ្នាក់ (Classes)

ថ្នាក់គឺជាប្ល៉ាននៃសម្ព័ន្ធដែលពិពណ៌នាលក្ខណៈសម្បត្តិ និងវិធីសាស្ត្រ។

### ឧទាហរណ៍សាមញ្ញ
```typescript
class Person {
  name: string;
  age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }

  introduce(): void {
    console.log(`ឈ្មោះខ្ញុំគឺ ${this.name}, អាយុ ${this.age} ឆ្នាំ`);
  }
}

const person = new Person("សុខ", 25);
person.introduce();  // លទ្ធផល: ឈ្មោះខ្ញុំគឺ សុខ, អាយុ 25 ឆ្នាំ
```

### សិទ្ធិចូលទៅ (Access Modifiers)
```typescript
class BankAccount {
  public accountNumber: string;    // ដាច់ដោយឡែក - គ្រប់គ្នាអាចដំណើរការ
  private balance: number;         // ឯកជន - មិនដាច់ដោយឡែក
  protected status: string;        // ការពារ - បានបង្ហាញក្នងថ្នាក់រង

  constructor(accountNumber: string, balance: number) {
    this.accountNumber = accountNumber;
    this.balance = balance;
    this.status = "ដំណើរការ";
  }

  public withdraw(amount: number): void {
    if (amount <= this.balance) {
      this.balance -= amount;
      console.log(`ដកយក: ${amount}`);
    }
  }

  private updateBalance(): void {
    // កូដឯកជន
  }
}
```

### ការបង្កើតឡើងវិញ (Inheritance)
```typescript
class Animal {
  name: string;

  constructor(name: string) {
    this.name = name;
  }

  makeSound(): void {
    console.log("សម្លេង");
  }
}

class Dog extends Animal {
  makeSound(): void {
    console.log("ឆ្នោតឆ្នោត!");
  }
}

class Cat extends Animal {
  makeSound(): void {
    console.log("ម៉ែវ!");
  }
}

const myDog = new Dog("ប៉ូលី");
myDog.makeSound();  // លទ្ធផល: ឆ្នោតឆ្នោត!
```

### ថ្នាក់ឡើង (Abstract Classes)
```typescript
abstract class Shape {
  abstract calculateArea(): number;

  describe(): void {
    console.log(`ផ្ទៃដែនកំណត់: ${this.calculateArea()}`);
  }
}

class Circle extends Shape {
  radius: number;

  constructor(radius: number) {
    super();
    this.radius = radius;
  }

  calculateArea(): number {
    return Math.PI * this.radius * this.radius;
  }
}

const circle = new Circle(5);
circle.describe();  // លទ្ធផល: ផ្ទៃដែនកំណត់: 78.53981...
```

---

## ⚙️ បច្ចេកទេសល្អបំផុត

### ១. ប្រើប្រភេទច្បាស់លាស់ដូចដែលអាចធ្វើទៅបាន
```typescript
// ❌ មិនល្អ
function process(data: any) {
  return data.value;
}

// ✅ ល្អ - ប្រេ្ជាភេទច្បាស់លាស់
function process(data: { value: string }): string {
  return data.value;
}
```

### ២. ពិនិត្យមើល null និង undefined
```typescript
function getUserName(user: User | null): string {
  if (!user) {
    return "មិនស្គាល់";
  }
  return user.name;
}
```

### ៣. ប្រើ const ដល់ដូចដែលអាចធ្វើទៅបាន
```typescript
// ❌ មិនល្អ
let value = 10;
value = 20;

// ✅ ល្អ - ប្រើ const
const value = 10;
```

### ៤. ប្រើ Interface សម្រាប់រចនាសម្ព័ន្ធ
```typescript
interface UserProfile {
  id: number;
  name: string;
  email: string;
}

// ✅ ល្អ - ឯកសារលម្អិតលម្អិត
const user: UserProfile = {
  id: 1,
  name: "សុខ",
  email: "sokh@example.com"
};
```

### ៥. ដាក់ឯកសារលម្អិតលម្អិត
```typescript
/**
 * គណនាផលបូកនៃលេខពីរ
 * @param a លេខដំបូង
 * @param b លេខទីពីរ
 * @returns ផលបូក
 */
function add(a: number, b: number): number {
  return a + b;
}
```

### ៦. ប្រើ Enums សម្រាប់តម្លៃលម្អិត
```typescript
enum Status {
  Active = "active",
  Inactive = "inactive",
  Pending = "pending"
}

const userStatus: Status = Status.Active;
```

---

## 📚 ធនធាននៅលើគេហទំព័រ

- 📖 [ឯកសារផ្លូវការ TypeScript](https://www.typescriptlang.org/)
- 📚 [ការណែនាំលម្អិត TypeScript](https://www.typescriptlang.org/docs/)
- 🎮 [Playground TypeScript](https://www.typescriptlang.org/play)
- 💡 [ឧទាហរណ៍ និងលម្អិត](https://www.typescriptlang.org/docs/handbook/)

---

## ✨ សេចក្តីសន្និដ្ឋាន

TypeScript គឺជាឧបករណ៍ដ៏មានឤទ្ធិសក្តិដែលធានាលក្ខណៈសម្បត្តិនៃកូដ JavaScript។ វាផ្តល់នូវ:

- ✨ ប្រព័ន្ធប្រភេទដែលធានាលក្ខណៈសម្បត្តិ
- ✨ ឧបករណ៍អភិវឌ្ឍនកម្ម (IDE) ដ៏ល្អ
- ✨ កូដដែលងាយស្រួលក្នងការរក្សាទុក និងបង្កើន
- ✨ ការស្វែងរកកំហុសម៉ាសមបឋម

### គន្លឹះសំខាន់
- ✅ ប្រភេទផ្តល់នូវសុវត្ថិភាព
- ✅ Interfaces ធានាលក្ខណៈសម្បត្តិថ្នាក់
- ✅ ថ្នាក់ផ្តល់នូវរចនាសម្ព័ន្ធល័ក

---

## 🤝 ការចូលរួម

សូមផ្នែកចូលក្នងគម្រោង! បង្កើត Pull Request ដើម្បីបង្កើន ឬកែលម្អ។

---

**ទំនាក់ទំនង:** info@example.com  
**កំណែ:** 1.0.0  
**ថ្ងៃលើក:** 2024

---

*ឯកសារលម្អិតលម្អិតនេះត្រូវបានរៀបចំដើម្បីផ្តល់នូវការណែនាំលម្អិត និងឧទាហរណ៍ TypeScript។*
