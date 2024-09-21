# พื้นฐานการเขียน JavaScript

ไฟล์นี้จะอธิบายพื้นฐานของ JavaScript เช่น การแสดงผล การประกาศตัวแปร ฟังก์ชัน และการใช้งานอ็อบเจ็กต์ เพื่อช่วยให้ผู้เริ่มต้นเข้าใจการเขียนโค้ดได้ง่ายขึ้น

---

## 1. การแสดงผล

เราสามารถแสดงผลข้อมูลไปยังหน้าจอคอนโซลได้โดยใช้ `console.log()` มันใช้สำหรับการดีบักและตรวจสอบค่าในโปรแกรม

```javascript
console.log("Jxxn03 (jean)");
```

---

## 2. บล็อกสโคป (Block Scope) และตัวแปร

ใน JavaScript เราสามารถประกาศตัวแปรได้ 3 แบบ คือ `var`, `let` และ `const`

### ตัวอย่าง:
```javascript
var x = 5;

if (x == 5) {
    let y = 10; // 'y' มีค่าเฉพาะภายในบล็อกนี้เท่านั้น
    console.log("y = " + y); // แสดงผล 10
}

console.log("Y = " + y); // จะเกิดข้อผิดพลาดเพราะ 'y' ไม่สามารถเข้าถึงได้จากภายนอกบล็อก
```

ในตัวอย่างนี้:
- `let` เป็นตัวแปรแบบบล็อกสโคป ซึ่งสามารถใช้งานได้ภายในบล็อกเท่านั้น
- `var` เป็นตัวแปรที่สามารถใช้งานได้ภายในฟังก์ชันหรือทั่วโปรแกรม ถ้าประกาศนอกฟังก์ชัน

---

## 3. ค่าคงที่ (Constant)

ตัวแปรที่ประกาศด้วย `const` ไม่สามารถเปลี่ยนแปลงค่าได้หลังจากที่ถูกกำหนดค่าแล้ว

```javascript
const z = 7;
z = 9; // จะเกิดข้อผิดพลาดเพราะ 'z' เป็นค่าคงที่
console.log(z);
```

---

## 4. ฟังก์ชันแบบลูกศร (Arrow Function)

ฟังก์ชันแบบลูกศรช่วยให้เขียนฟังก์ชันใน JavaScript ได้สั้นและกระชับขึ้น

### ตัวอย่าง:
```javascript
const fullname = (fname, lname) => {
    return fname + " " + lname;
};

console.log(fullname("Sigma", "Ohio")); // แสดงผล "Sigma Ohio"
```

---

## 5. อ็อบเจ็กต์ (Object)

ใน JavaScript เราใช้ **อ็อบเจ็กต์** เพื่อเก็บค่าหลายๆ ค่าไว้ในตัวแปรเดียว อ็อบเจ็กต์สามารถประกอบด้วยคุณสมบัติ (properties) และฟังก์ชัน (methods)

### ตัวอย่าง:
```javascript
const name = "Sigma Rizz Ohio";
const age = 99;
const adress = "Russian";

const customer = {
    ctmanme: name,
    age: age,
    address: adress,

    showdata() {
        console.log("Name: " + this.ctmanme); // แสดงผล "Name: Sigma Rizz Ohio"
    }
};

console.log(customer); // แสดงอ็อบเจ็กต์ customer
customer.showdata(); // เรียกใช้ฟังก์ชันในอ็อบเจ็กต์
```

---

## 6. สตริงและ Template Literals

**Template Literals** ช่วยให้เราสามารถสร้างสตริงที่มีตัวแปรหรือการแสดงผลแทรกเข้าไปได้ง่ายขึ้น โดยใช้เครื่องหมาย backticks (\` \`)

### ตัวอย่าง:
```javascript
let ctmname = "Alya";
const address = `Name: ${ctmname}
address: Japan
tel: 78987654345678765`;

console.log(address);
```

จะได้ผลลัพธ์ดังนี้:

```
Name: Alya
address: Japan
tel: 78987654345678765
```

Template literals ช่วยให้การเขียนสตริงที่มีตัวแปรรวมอยู่ทำได้สะดวกขึ้น

---

## 7. ตัวอย่างการรวมทุกอย่าง

นี่คือตัวอย่างที่รวมทุกหัวข้อที่เราได้เรียนรู้:

```javascript
console.log("Jxxn03 (jean)");

// Block scope
var x = 5;

if (x == 5) {
    let y = 10; // 'y' มีค่าเฉพาะในบล็อกนี้
    console.log("y =" + y);
}

// บรรทัดนี้จะเกิดข้อผิดพลาดเพราะ 'y' ไม่สามารถเข้าถึงจากนอกบล็อกได้
// console.log("Y = " + y);

// Arrow function
const fullname = (fname, lname) => {
    return fname + " " + lname;
};
console.log(fullname("YouNameSigma", "TwT"));

// Object ที่มีคุณสมบัติและฟังก์ชัน
const name = "EZ";
const age = 99;
const adress = "Lol";

const customer = {
    ctmanme: name,
    age: age,
    address: adress,

    showdata() {
        console.log("Name: " + this.ctmanme);
    }
};

console.log(customer);
customer.showdata();

// Template literals สำหรับการใช้งานสตริง
let ctmname = "Sigma";
const address = `Name: ${ctmname}
address: Ohio
tel: 1237129837128937128937128973129871289791287391287389127398127893127389127389127328917329187192731289739812738912789578685328746527834587325478324678236482736478263478632784`;

console.log(address);
```

---

## 8. เคล็ดลับสำหรับผู้เริ่มต้น

- ใช้ `let` และ `const` แทน `var` เพราะ `var` มีพฤติกรรมที่อาจทำให้สับสนเนื่องจากฟังก์ชันสโคป
- ใช้ `const` เมื่อค่าตัวแปรจะไม่เปลี่ยนแปลง
- ใช้ฟังก์ชันแบบลูกศร (`=>`) เพื่อทำให้โค้ดสั้นและอ่านง่ายขึ้น
- ใช้ Template Literals (`\``) เพื่อรวมตัวแปรลงในสตริงได้ง่ายขึ้น

---
