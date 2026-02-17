{
  "name": "hisn-muslim-app",
  "version": "1.0.0",
  "private": true,
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-scripts": "5.0.1"
  },
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  }
}
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>حصن المسلم</title>
</head>
<body>
  <div id="root"></div>
    import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './App';
import './styles/App.css';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
import React from 'react';
import AzkarList from './components/AzkarList';
import Sebha from './components/Sebha';
import Tasks from './components/Tasks';

function App() {
  return (
    <div className="App">
      <header>
        <h1>تطبيق حصن المسلم</h1>
      </header>

      <section>
        <h2>الأذكار اليومية</h2>
        <AzkarList />
      </section>

      <section>
        <h2>السبحة</h2>
        <Sebha />
      </section>

      <section>
        <h2>مهامك اليومية</h2>
        <Tasks />
      </section>

      <section>
        <h2>المصحف (صور)</h2>
        <p>ضع صور صفحات المصحف داخل مجلد <strong>images/</strong></p>
      </section>
    </div>
  );
}

export default App;
import React from 'react';

const azkar = [
  { title: 'أذكار الصباح', text: 'سبحان الله، الحمد لله، الله أكبر ...' },
  { title: 'أذكار المساء', text: 'سبحان الله، الحمد لله، الله أكبر ...' },
  { title: 'أذكار بعد الصلاة', text: 'اللهم أنت السلام ...' }
];

function AzkarList() {
  return (
    <div className="azkar-list">
      {azkar.map((item, idx) => (
        <div key={idx} className="azkar-item">
          <h3>{item.title}</h3>
          <p>{item.text}</p>
        </div>
      ))}
    </div>
  );
}

export default AzkarList;
import React, { useState } from 'react';

function Sebha() {
  const [count, setCount] = useState(0);

  return (
    <div className="sebha">
      <h3>العدد: {count}</h3>
      <button onClick={() => setCount(count + 1)}>اضغط للتسبيح</button>
      <button onClick={() => setCount(0)}>إعادة التعيين</button>
    </div>
  );
}

export default Sebha;
import React, { useState } from 'react';

function Tasks() {
  const [tasks, setTasks] = useState([
    { text: 'صلاة الفجر', done: false },
    { text: 'صلاة الظهر', done: false },
    { text: 'صلاة العصر', done: false },
    { text: 'صلاة المغرب', done: false },
    { text: 'صلاة العشاء', done: false },
  ]);

  const toggleTask = (index) => {
    const newTasks = [...tasks];
    newTasks[index].done = !newTasks[index].done;
    setTasks(newTasks);
  };

  return (
    <div className="tasks">
      {tasks.map((task, idx) => (
        <div key={idx}>
          <input
            type="checkbox"
            checked={task.done}
            onChange={() => toggleTask(idx)}
          />
          <span className={task.done ? 'done' : ''}>{task.text}</span>
        </div>
      ))}
    </div>
  );
}

export default Tasks;
body {
  font-family: "Arial", sans-serif;
  background: #f8f8f8;
  color: #333;
  direction: rtl;
}

.App {
  max-width: 800px;
  margin: 20px auto;
  padding: 20px;
  background: #fff;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0,0,0,0.1);
}

h1, h2, h3 {
  text-align: center;
  color: #2c3e50;
}

.azkar-item, .sebha, .tasks {
  margin: 15px 0;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 8px;
  background: #fdfdfd;
}

button {
  margin: 5px;
  padding: 8px 12px;
  border: none;
  background: #3498db;
  color: #fff;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background: #2980b9;
}

.done {
  text-decoration: line-through;
  color: #888;
}

</body>
</html>
