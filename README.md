# full
// App.js
import React from 'react';
import './App.css';

class ResumeSection extends React.Component {
  render() {
    return (
      <div className="resume-section">
        <h2>{this.props.title}</h2>
        {this.props.items.map((item, index) => (
          <div key={index} className="resume-item">
            <h3>{item.title}</h3>
            <p>{item.description}</p>
          </div>
        ))}
      </div>
    );
  }
}

function App() {
  const education = [
    { title: 'Bachelor of Science in Computer Science', description: 'University XYZ, 2020-2024' },
  ];

  const experience = [
    { title: 'Software Developer Intern', description: 'Company ABC, Summer 2023' },
  ];

  return (
    <div className="App">
      <h1>My Resume</h1>
      <ResumeSection title="Education" items={education} />
      <ResumeSection title="Experience" items={experience} />
    </div>
  );
}

export default App;


//App.css



.App {
  text-align: center;
  margin: 20px;
}

.resume-section {
  margin-bottom: 20px;
}

.resume-item {
  border: 1px solid #a90f0f;
  padding: 10px;
  margin-bottom: 10px;
}
body{
  background-color: #61dafb;
}









2  Build Student Registration Portal using entities like component, State and Props

 src/StudentForm.js

import React, { useState } from 'react';

const StudentForm = ({ addStudent }) => {
  const [name, setName] = useState('');
  const [grade, setGrade] = useState('');

  const handleSubmit = (e) => {
    e.preventDefault();
    addStudent({ name, grade });
    setName('');
    setGrade('');
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Name:
        <input type="text" value={name} onChange={(e) => setName(e.target.value)} />
      </label>
      <label>
        Grade:
        <input type="text" value={grade} onChange={(e) => setGrade(e.target.value)} />
      </label>
      <button type="submit">Add Student</button>
    </form>
  );
};

export default StudentForm;

// src/StudentList.js

import React from 'react';

const StudentList = ({ students }) => (
  <div>
    <h2>Student List</h2>
    <ul>
      {students.map((student, index) => (
        <li key={index}>
          {student.name} - Grade: {student.grade}
        </li>
      ))}
    </ul>
  </div>
);

export default StudentList;

// src/App.js
import React, { useState } from 'react';
import StudentForm from './StudentForm';
import StudentList from './StudentList';

const App = () => {
  const [students, setStudents] = useState([]);

  const addStudent = (student) => {
    setStudents([...students, student]);
  };

  return (
    <div>
      <h1>Student Registration Portal</h1>
      <StudentForm addStudent={addStudent} />
      <StudentList students={students} />
    </div>
  );
};

export default App;

