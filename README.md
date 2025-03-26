## Basic-angular-project

Output:

![Alt Text]

1. Ensure Node.js is installed:
```
node -v
npm -v
```
2. Install Angular CLI globally:
```
npm install -g @angular/cli
ng version
```
3.Create an Angular Project
```
ng new todo-app
cd todo-app
code .
```
If prompted:
Choose Yes for Angular routing.
Select CSS for styling.

4. Run the Angular Project
```
ng serve
```

5. Create Components for To-Do List :
Inside the project folder (todo-app), run:
```
ng generate component todo
```
OR
```
ng g c todo
```
This creates:
src/app/todo/todo.component.ts
src/app/todo/todo.component.html
src/app/todo/todo.component.css
src/app/todo/todo.component.spec.ts

6. Edit src/app/todo/todo.component.ts :
```
import { Component } from '@angular/core';

@Component({
  selector: 'app-todo',
  templateUrl: './todo.component.html',
  styleUrls: ['./todo.component.css']
})
export class TodoComponent {
  tasks: string[] = [];
  newTask: string = '';

  addTask() {
    if (this.newTask.trim()) {
      this.tasks.push(this.newTask);
      this.newTask = '';
    }
  }

  removeTask(index: number) {
    this.tasks.splice(index, 1);
  }
}
```
7.  Edit src/app/todo/todo.component.html :
```
<div class="container">
  <h2>To-Do List</h2>
  <input [(ngModel)]="newTask" placeholder="Enter task" />
  <button (click)="addTask()">Add Task</button>

  <ul>
    <li *ngFor="let task of tasks; let i = index">
      {{ task }}
      <button (click)="removeTask(i)">❌</button>
    </li>
  </ul>
</div>
```
8. Edit src/app/todo/todo.component.css :
```
.container {
  text-align: center;
  margin-top: 50px;
}
input {
  padding: 5px;
  margin-right: 10px;
}
button {
  padding: 5px 10px;
  cursor: pointer;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  margin: 10px 0;
}
```
9.  Edit src/app/app.module.ts (Enable FormsModule) :
```
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { FormsModule } from '@angular/forms'; // Import FormsModule

import { AppComponent } from './app.component';
import { TodoComponent } from './todo/todo.component';

@NgModule({
  declarations: [AppComponent, TodoComponent],
  imports: [BrowserModule, FormsModule], // Add FormsModule here
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule {}
```
10. Edit src/app/app.component.html to Include To-Do Component
```
<app-todo></app-todo>
```
11. Run the App
```
ng serve
```


