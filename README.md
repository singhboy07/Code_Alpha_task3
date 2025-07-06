// App.jsx

import React, { useEffect, useState } from 'react';

function App() {

 const [tasks, setTasks] = useState([]);

 useEffect(() => {

 fetch('/api/tasks').then(res => res.json()).then(setTasks);

 }, []);

 return <div>{tasks.map(t => <div key={t.id}>{t.title}</div>)}</div>;

}

export default App;

// server.js

const express = require('express');

const app = express();

const tasks = [

 { id: 1, title: 'Design UI' },

 { id: 2, title: 'Setup Backend' }

];

app.get('/api/tasks', (req, res) => {

 res.json(tasks);

});

app.listen(3002, () => console.log('PMT server on port 3002'));
