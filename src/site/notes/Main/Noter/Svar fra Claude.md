---
{"dg-publish":true,"permalink":"/main/noter/svar-fra-claude/","dgHomeLink":"false","dgShowBacklinks":"false","dgShowLocalGraph":"false","dgShowFileTree":"false","dgEnableSearch":"false","dgShowToc":"false","created":"2025-01-22T09:12:33.678+01:00"}
---

> lav en todoliste app

Jeg vil lave en enkel React-komponent til en todo-liste app.

Todo Liste App

Click to open component (Claude åber koden i et modal vindue, jeg har placeret denne kode nederst på siden)

Jeg har lavet en todo-liste app med følgende funktioner:

1. Tilføj nye opgaver via input-felt og knap
2. Marker opgaver som færdige/ikke færdige
3. Slet opgaver
4. Pænt og brugervenligt design med Tailwind CSS

Appen bruger:

- React's useState hook til at håndtere state
- Lucide icons til ikoner
- shadcn/ui komponenter for et poleret look
- Tailwind CSS til styling

Vil du have mig til at tilføje flere funktioner? For eksempel kunne jeg tilføje:

- Kategorier for opgaver
- Deadlines
- Filtrering af opgaver
- Lokal lagring så opgaverne bliver gemt

```js
import React, { useState } from 'react'; 
import { PlusCircle, Trash2, CheckCircle, Circle } from 'lucide-react'; 
import { Card, CardHeader, CardTitle, CardContent } from '@/components/ui/card'; import { Input } from '@/components/ui/input'; 
import { Button } from '@/components/ui/button'; 
const TodoApp = () => { 
const [todos, setTodos] = useState([]); 
const [newTodo, setNewTodo] = useState(''); 

const addTodo = (e) => { 
	e.preventDefault(); 
	if (newTodo.trim()) { 
	setTodos([...todos, { text: newTodo.trim(), completed: false, id: Date.now() }]); 
	setNewTodo(''); 
	} 
}; 

const toggleTodo = (id) => { 
setTodos(todos.map(todo => 
	todo.id === id ? { ...todo, completed: !todo.completed } : todo 
	));
}; 

const deleteTodo = (id) => { 
setTodos(todos.filter(todo => todo.id !== id)); 
}; 
return ( 
<Card className="w-full max-w-md mx-auto"> 
	<CardHeader> 
		<CardTitle>Todo Liste</CardTitle> 
	</CardHeader> 
	<CardContent> 
				
	<form onSubmit={addTodo} className="flex gap-2 mb-4"> 
		<Input type="text" 
		value={newTodo} 
		onChange={(e) => setNewTodo(e.target.value)} 
		placeholder="Tilføj ny opgave..." 
		className="flex-1" /> 
	<Button type="submit"> 
		<PlusCircle className="w-4 h-4 mr-2" /> 
		Tilføj 
		</Button> 
	</form> 
	<div className="space-y-2"> 
	{todos.map(todo => ( 
	<div key={todo.id} 
	className="flex items-center justify-between p-3 bg-gray-50 rounded-lg" > 
	<div className="flex items-center gap-3"> 
	<button onClick={() => toggleTodo(todo.id)} className="text-blue-500 hover:text-blue-600" > 
	{todo.completed ? ( 
	<CheckCircle className="w-5 h-5" /> 
	) : ( 
	<Circle className="w-5 h-5" /> )} 
	</button> 
	<span className={
	todo.completed ? 'line-through text-gray-500' : ''}> 
	{todo.text} </span> 
	</div> 
	<button onClick={() => 
	deleteTodo(todo.id)} 
	className="text-red-500 hover:text-red-600" > 
	<Trash2 className="w-5 h-5" /> 
	</button> </div> ))} 
	</div> </CardContent> 
	</Card> 
	); 
	}; 
export default TodoApp;
``