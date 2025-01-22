---
{"dg-publish":true,"permalink":"/main/noter/svar-fra-gpt/","dgHomeLink":"false","dgShowBacklinks":"false","dgShowLocalGraph":"false","dgShowFileTree":"false","dgEnableSearch":"false","dgShowToc":"false","created":"2025-01-22T09:10:38.765+01:00"}
---


> lav en todoliste app

## Svaret fra GPT-4o
At lave en todoliste-app er en god øvelse! Her er en enkel plan for, hvordan du kan bygge en todoliste-app i React med en C# backend og en MSSQL-database, der passer til din erfaring og stack.

---

### **Funktionaliteter**

1. **Opret en opgave**
2. **Marker opgaver som fuldført**
3. **Rediger opgaver**
4. **Slet opgaver**
5. **Organiser opgaver i kategorier eller projekter**
6. **Gem opgaver i en database**

---

### **Teknologi Stack**

- **Frontend**: React (med TypeScript og Tailwind CSS)
- **Backend**: ASP.NET Core Web API (C#)
- **Database**: MSSQL (via Entity Framework)
- **Hosting**: Lokal udvikling eller cloud (f.eks. Azure)

---

### **Trin-for-trin Guide**

#### 1. **Opsæt backend i C#**

1. Opret en ASP.NET Core Web API:

    ```bash
    dotnet new webapi -n TodoListApi
    ```
2. Installer Entity Framework Core til MSSQL:

    ```bash
    dotnet add package Microsoft.EntityFrameworkCore.SqlServer dotnet add package Microsoft.EntityFrameworkCore.Tools
    ```
3. Definér en model for opgaver:

    ```Csharp
public class TodoItem 
{     
public int Id { get; set; }     
public string Title { get; set; } = string.Empty;     
public bool IsCompleted { get; set; } }
    ```
4. Opret en DbContext:

```csharp
    public class TodoContext : DbContext 
    {     
    public TodoContext(DbContextOptions<TodoContext> options) : base(options) 
    { 
    }     
    public DbSet<TodoItem> TodoItems { get; set; } }
    ```

1. Tilføj en controller for CRUD-operationer.

---

#### 2. **Opsæt MSSQL-database**

1. Tilføj en forbindelse til din database i `appsettings.json`:
    
```json
    "ConnectionStrings": 
    {     
    "DefaultConnection": "Server=localhost;Database=TodoDb;Trusted_Connection=True;" 
    }
        ```
1. Kør migrationer:
    
    ```bash
    dotnet ef migrations add InitialCreate dotnet ef database update
    ```
    

---

#### 3. **Byg frontend i React**

1. Opret en React-app med Vite:
    
 ```bash
    npm create vite@latest todo-list --template react-ts
    ```
2. Installer Axios for at lave API-kald:
    
```bash
    `npm install axios`
    ```
3. Lav en simpel todoliste-komponent:
    
```js
    import { useState, useEffect } from 'react'; 
    import axios from 'axios'; 

const TodoList = () => {     
const [todos, setTodos] = useState([]);     
const [newTodo, setNewTodo] = useState("");      

useEffect(() => {        
axios.get('/api/todos').then(response => setTodos(response.data));    
}, 
		  []);      
		  
		  const addTodo = async () => {         
		  const response = await axios.post('/api/todos', 
		  { title: newTodo });       
		  setTodos([...todos, response.data]);         
		  setNewTodo('');     };      
		  return (        
		   <div className="p-4">             
		   <h1 className="text-xl font-bold mb-4">Todo List</h1>  
			<input                 
			value={newTodo}                 
			onChange={(e) => setNewTodo(e.target.value)}                 
			className="border p-2 mr-2"                 
			placeholder="Add a new task"             
			/>             
			<button onClick={addTodo} 
			className="bg-blue-500 text-white px-4 py-2">                
			 Add             
			 </button>             
			 <ul>                
{todos.map((todo) => (                     
<li key={todo.id} className="flex justify-between mt-2">
{todo.title}                     
</li>                 
))}             
</ul>         
</div>    
); 
};  
    export default TodoList;
    
```
---

#### 4. **Kobl frontend og backend sammen**

- Opsæt en proxy i `vite.config.ts` for at videresende API-kald til din backend:
    
```js
    server: {     
    proxy: {         
    '/api': 'http://localhost:5000'     
    } 
    }
```

---

#### 5. **Tilføj styling med Tailwind CSS**

1. Installer Tailwind CSS:
    ```bash
    npm install -D tailwindcss postcss autoprefixer npx tailwindcss init
    ```
2. Konfigurer Tailwind og tilføj styles.

---

Vil du have en komplet kodebase, eller er der en bestemt del, du vil fokusere på først? 😊