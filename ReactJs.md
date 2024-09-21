---

## 1. React คืออะไร?

React.js เป็นไลบรารีที่ใช้สำหรับสร้าง UI ของเว็บแอป โดยใช้แนวคิดของ **Component-based architecture** ซึ่ง UI จะแบ่งออกเป็นชิ้นส่วนย่อย ๆ ที่เรียกว่า **Component** แต่ละ Component สามารถทำงานแยกกันได้ แต่สามารถนำมารวมกันเพื่อสร้างหน้าเว็บที่สมบูรณ์

---

## 2. เริ่มต้นใช้งาน React

### การติดตั้ง React

คุณสามารถเริ่มต้นโปรเจ็กต์ React ได้ง่ายๆ โดยใช้ **Create React App** ซึ่งเป็น CLI tool ที่ช่วยในการตั้งค่าโปรเจ็กต์อย่างรวดเร็ว

1. ติดตั้ง Node.js (หากยังไม่ได้ติดตั้ง)
   - ดาวน์โหลด Node.js ได้จาก [Node.js](https://nodejs.org/)

2. ใช้คำสั่ง `npx` ในการสร้างโปรเจ็กต์ React:
   ```bash
   npx create-react-app my-app
   cd my-app
   npm start
   ```

คำสั่งนี้จะสร้างโครงสร้างของโปรเจ็กต์ React และเปิดเว็บเซิร์ฟเวอร์ขึ้นที่ `http://localhost:3000`

---

## 3. โครงสร้างของโปรเจ็กต์ React

หลังจากที่คุณสร้างโปรเจ็กต์ React แล้ว คุณจะเห็นโครงสร้างโฟลเดอร์ดังนี้:

```
my-app/
├── node_modules/
├── public/
├── src/
│   ├── App.css
│   ├── App.js
│   ├── index.css
│   ├── index.js
├── package.json
└── README.md
```

- `public/` : เก็บไฟล์ HTML และทรัพยากรที่ไม่ต้องเปลี่ยนแปลงบ่อย
- `src/` : เก็บไฟล์โค้ดของ React, Component, และไฟล์ CSS

ไฟล์หลักที่เริ่มการทำงานคือ `src/index.js` ซึ่งจะทำการ Render แอปของเราลงใน DOM (Document Object Model)

---

## 4. การสร้าง Component

React ใช้ **Component** ในการจัดการและสร้าง UI แต่ละหน้า Component ก็คือฟังก์ชัน JavaScript ที่คืนค่าเป็น HTML ผ่านการใช้ **JSX** (JavaScript XML)

### ตัวอย่างการสร้าง Component ง่าย ๆ:

```jsx
import React from 'react';

function HelloWorld() {
  return (
    <div>
      <h1>สวัสดีชาวโลก!</h1>
    </div>
  );
}

export default HelloWorld;
```

### การใช้ Component

เมื่อเราสร้าง Component `HelloWorld` แล้ว เราสามารถเรียกใช้มันใน Component อื่นได้ เช่นใน `App.js`:

```jsx
import React from 'react';
import HelloWorld from './HelloWorld';

function App() {
  return (
    <div>
      <HelloWorld />
    </div>
  );
}

export default App;
```

เมื่อคุณรันแอป (`npm start`), จะเห็นข้อความ "สวัสดีชาวโลก!" บนหน้าเว็บ

---

## 5. JSX (JavaScript XML)

JSX เป็นการเขียนโค้ดแบบ JavaScript ผสมกับ HTML ใน React ซึ่งจะถูกแปลงเป็น JavaScript ธรรมดาเมื่อทำการ compile

### ตัวอย่าง JSX:

```jsx
const element = <h1>สวัสดีชาวโลก!</h1>;
```

JSX สามารถแทรก JavaScript expression ได้ เช่น:

```jsx
const name = 'React';
const element = <h1>สวัสดี {name}!</h1>;
```

---

## 6. Props และ State

### Props (Properties)

**Props** เป็นวิธีการส่งข้อมูลจาก Component หนึ่งไปยัง Component อื่น เป็นค่าแบบ Read-only ที่ไม่สามารถเปลี่ยนแปลงได้ใน Component ปลายทาง

ตัวอย่างการใช้ Props:

```jsx
function Welcome(props) {
  return <h1>สวัสดี, {props.name}!</h1>;
}

function App() {
  return (
    <div>
      <Welcome name="React" />
    </div>
  );
}
```

ในตัวอย่างนี้, `Welcome` จะรับ `name` ผ่าน Props และแสดงผล "สวัสดี, React!"

### State

**State** ใช้สำหรับเก็บข้อมูลที่สามารถเปลี่ยนแปลงได้ภายใน Component ซึ่งจะทำให้ UI ถูกอัปเดตเมื่อ State เปลี่ยน

ตัวอย่างการใช้ State:

```jsx
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>คุณกดปุ่ม {count} ครั้ง</p>
      <button onClick={() => setCount(count + 1)}>
        กดที่นี่
      </button>
    </div>
  );
}

export default Counter;
```

ในตัวอย่างนี้, เมื่อกดปุ่ม ค่า `count` จะเพิ่มขึ้นและ UI จะอัปเดตแสดงจำนวนครั้งที่กด

---

## 7. การจัดการเหตุการณ์ (Event Handling)

ใน React, คุณสามารถจัดการเหตุการณ์ต่าง ๆ เช่น การคลิกปุ่ม โดยใช้ JavaScript ที่สอดคล้องกับ DOM events

ตัวอย่างการจัดการเหตุการณ์:

```jsx
function App() {
  function handleClick() {
    alert('ปุ่มนี้ถูกกด!');
  }

  return (
    <button onClick={handleClick}>
      กดปุ่มนี้
    </button>
  );
}

export default App;
```

เมื่อผู้ใช้กดปุ่ม, ฟังก์ชัน `handleClick` จะถูกเรียกและแสดงการแจ้งเตือน

---

## 8. การใช้ Effect (useEffect)

`useEffect` เป็น Hook ที่ใช้เพื่อจัดการ side-effects ใน Component เช่น การดึงข้อมูลจาก API

ตัวอย่างการใช้ `useEffect`:

```jsx
import React, { useState, useEffect } from 'react';

function DataFetcher() {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch('https://api.example.com/data')
      .then((response) => response.json())
      .then((data) => setData(data));
  }, []);

  return (
    <div>
      <h1>ข้อมูลจาก API:</h1>
      <pre>{JSON.stringify(data, null, 2)}</pre>
    </div>
  );
}

export default DataFetcher;
```

ในตัวอย่างนี้, เมื่อ Component ถูกแสดงครั้งแรก จะทำการดึงข้อมูลจาก API และเก็บข้อมูลนั้นไว้ใน State

---

## 9. การจัดการเส้นทาง (Routing) ด้วย React Router

หากคุณต้องการสร้างเว็บที่มีหลายหน้า คุณสามารถใช้ **React Router** เพื่อนำทางระหว่างหน้าได้

1. ติดตั้ง React Router:
   ```bash
   npm install react-router-dom
   ```

2. ตัวอย่างการใช้งาน React Router:

```jsx
import React from 'react';
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom';

function Home() {
  return <h2>หน้าแรก</h2>;
}

function About() {
  return <h2>เกี่ยวกับเรา</h2>;
}

function App() {
  return (
    <Router>
      <div>
        <Switch>
          <Route exact path="/" component={Home} />
          <Route path="/about" component={About} />
        </Switch>
      </div>
    </Router>
  );
}

export default App;
```

ในตัวอย่างนี้, เมื่อผู้ใช้เข้าชม `/` จะเห็นหน้า Home และเมื่อเข้าชม `/about` จะเห็นหน้า About

---

## 10. สรุป

React.js เป็นเครื่องมือที่ทรงพลังสำหรับการสร้าง UI ที่ตอบสนองต่อการเปลี่ยนแปลงของข้อมูลได้อย่างรวดเร็ว การเข้าใจการใช้งาน **Component**, **Props**, **State**, และ **Hooks** จะช่วยให้คุณสามารถพัฒนาเว็บแอปที่ซับซ้อนได้อย่างมีประสิทธิภาพ

หากคุณต้องการศึกษาเพิ่มเติม สามารถเข้าดูเอกสารของ React ได้ที่ [React Documentation](https://reactjs.org/).

--- 

