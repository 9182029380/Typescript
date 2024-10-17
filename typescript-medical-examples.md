# TypeScript Examples in Medical Context

## Table of Contents
1. [Basic Types](#basic-types)
2. [Object Types](#object-types)
3. [Type Inference](#type-inference)
4. [Variables and Constants](#variables-and-constants)
5. [Functions](#functions)
6. [Classes](#classes)
7. [Modules](#modules)
8. [Generics](#generics)

## Basic Types

### Example 1: Number
```typescript
let patientAge: number = 45;
let bodyTemperature: number = 98.6;
```
Here, we're declaring variables to store a patient's age and body temperature. The `: number` indicates that these variables can only hold numeric values.

### Example 2: String
```typescript
let patientName: string = "John Doe";
let diagnosis: string = "Common Cold";
```
These variables store text data. The `: string` ensures that only text can be assigned to these variables.

## Object Types

### Example 1: Arrays
```typescript
let vitals: number[] = [98.6, 72, 120, 80];
```
This array stores a patient's vital signs (temperature, heart rate, blood pressure systolic, blood pressure diastolic). The `number[]` type indicates an array of numbers.

### Example 2: Interfaces
```typescript
interface Patient {
  name: string;
  age: number;
  allergies: string[];
}

let newPatient: Patient = {
  name: "Jane Smith",
  age: 30,
  allergies: ["Penicillin", "Peanuts"]
};
```
An interface defines the structure of an object. Here, we're creating a `Patient` object with specified properties.

## Type Inference

### Example 1:
```typescript
let heartRate = 72; // TypeScript infers this as number
let patientStatus = "Stable"; // TypeScript infers this as string
```
TypeScript can automatically determine (infer) the type based on the assigned value.

### Example 2:
```typescript
function getMedicationDosage(weight: number) {
  return weight * 0.5; // TypeScript infers the return type as number
}
```
The return type is inferred based on the calculation.

## Variables and Constants

### Example 1: let
```typescript
let bloodPressure = 120;
bloodPressure = 118; // This is allowed
```
`let` allows reassignment of values.

### Example 2: const
```typescript
const patientId = "P12345";
// patientId = "P67890"; // This would cause an error
```
`const` creates a constant that cannot be reassigned.

## Functions

### Example 1: Function with parameters and return type
```typescript
function calculateBMI(weight: number, height: number): number {
  return weight / (height * height);
}

let patientBMI = calculateBMI(70, 1.75);
```
This function calculates Body Mass Index (BMI) given weight (in kg) and height (in meters).

### Example 2: Arrow function with optional parameter
```typescript
const getFullName = (firstName: string, lastName: string, middleName?: string): string => {
  if (middleName) {
    return `${firstName} ${middleName} ${lastName}`;
  }
  return `${firstName} ${lastName}`;
};

console.log(getFullName("John", "Doe")); // Output: John Doe
console.log(getFullName("Jane", "Smith", "Marie")); // Output: Jane Marie Smith
```
This arrow function constructs a full name, with an optional middle name.

## Classes

### Example 1: Basic class
```typescript
class MedicalRecord {
  patientName: string;
  diagnosis: string;

  constructor(name: string, diagnosis: string) {
    this.patientName = name;
    this.diagnosis = diagnosis;
  }

  updateDiagnosis(newDiagnosis: string) {
    this.diagnosis = newDiagnosis;
  }
}

let record = new MedicalRecord("Alice Johnson", "Influenza");
record.updateDiagnosis("Pneumonia");
```
This class represents a medical record with methods to update the diagnosis.

### Example 2: Inheritance
```typescript
class Person {
  name: string;
  age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}

class Doctor extends Person {
  specialty: string;

  constructor(name: string, age: number, specialty: string) {
    super(name, age);
    this.specialty = specialty;
  }

  introduceYourself() {
    console.log(`I'm Dr. ${this.name}, a ${this.specialty} specialist.`);
  }
}

let cardiologist = new Doctor("Smith", 45, "Cardiology");
cardiologist.introduceYourself();
```
This example shows a `Doctor` class inheriting from a `Person` class, demonstrating inheritance in TypeScript.

## Modules

### Example 1: Exporting a function
```typescript
// File: vitalsCheck.ts
export function isFeverish(temperature: number): boolean {
  return temperature > 38;
}

// File: patientAssessment.ts
import { isFeverish } from './vitalsCheck';

let patientTemp = 38.5;
if (isFeverish(patientTemp)) {
  console.log("Patient has a fever");
}
```
This example shows how to export a function from one file and import it in another.

### Example 2: Exporting a class
```typescript
// File: patient.ts
export class Patient {
  constructor(public name: string, public age: number) {}
}

// File: hospital.ts
import { Patient } from './patient';

let newPatient = new Patient("Bob Brown", 50);
```
Here, we're exporting a `Patient` class and importing it in another file.

## Generics

### Example 1: Generic function
```typescript
function getFirstElement<T>(arr: T[]): T {
  return arr[0];
}

let firstVital = getFirstElement([98.6, 72, 120, 80]); // Returns 98.6
let firstAllergy = getFirstElement(["Penicillin", "Peanuts"]); // Returns "Penicillin"
```
This generic function can work with arrays of any type.

### Example 2: Generic class
```typescript
class MedicalQueue<T> {
  private queue: T[] = [];

  enqueue(item: T) {
    this.queue.push(item);
  }

  dequeue(): T | undefined {
    return this.queue.shift();
  }
}

let patientQueue = new MedicalQueue<string>();
patientQueue.enqueue("John Doe");
patientQueue.enqueue("Jane Smith");
console.log(patientQueue.dequeue()); // Output: John Doe
```
This generic class implements a queue that can work with any type of data.

These examples cover the basic concepts of TypeScript in a medical context. They demonstrate how TypeScript can be used to create more robust and type-safe code, which is particularly important in fields like healthcare where accuracy is crucial. The strong typing system helps prevent errors and makes the code more self-documenting, which can be beneficial even for non-coders who might need to understand or review the logic.
