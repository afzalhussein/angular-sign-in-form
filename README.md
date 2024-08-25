# angular-sign-in-form

Creating a sign-in form in Angular involves several steps, including setting up a new Angular application, creating components, configuring routes, and handling user input. Below, I'll provide a step-by-step example of how to create a basic sign-in form in Angular, including the necessary changes to Angular modules.

Assuming you have Angular CLI installed, follow these steps:

### Step 1: Create a New Angular Application

Open your terminal and run the following command to create a new Angular application:

```bash
ng new angular-signin-form
```

Follow the prompts to configure your application (you can choose the default settings for most questions).

### Step 2: Create Components

Next, create two components: one for the sign-in form and another for a welcome page. Run these commands to generate the components:

```bash
ng generate component signin
ng generate component welcome
```

This will generate the necessary component files in the project.

### Step 3: Create a Sign-in Form

Open the `src/app/signin/signin.component.html` file and create your sign-in form. Here's a basic example:

```html
<div class="signin-form">
  <h2>Sign In</h2>
  <form (ngSubmit)="onSubmit()">
    <div class="form-group">
      <label for="username">Username:</label>
      <input type="text" id="username" name="username" [(ngModel)]="username" required>
    </div>
    <div class="form-group">
      <label for="password">Password:</label>
      <input type="password" id="password" name="password" [(ngModel)]="password" required>
    </div>
    <button type="submit">Sign In</button>
  </form>
</div>
```

### Step 4: Create Component Logic

Open the `src/app/signin/signin.component.ts` file and add the component logic. Import the necessary modules for forms and reactive forms, and implement a basic form submission.

```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'app-signin',
  templateUrl: './signin.component.html',
  styleUrls: ['./signin.component.css'],
})
export class SigninComponent {
  username: string = '';
  password: string = '';

  onSubmit() {
    // Handle form submission logic here (e.g., authentication).
    console.log('Username:', this.username);
    console.log('Password:', this.password);
  }
}
```

### Step 5: Configure Routes

Open the `src/app/app-routing.module.ts` file and configure routes for the sign-in form and welcome page.

```typescript
import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
import { SigninComponent } from './signin/signin.component';
import { WelcomeComponent } from './welcome/welcome.component';

const routes: Routes = [
  { path: '', component: WelcomeComponent },
  { path: 'signin', component: SigninComponent },
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule],
})
export class AppRoutingModule {}
```

### Step 6: Update App Module

Open the `src/app/app.module.ts` file and import FormsModule and ReactiveFormsModule from `@angular/forms`. Also, add these modules to the `imports` array of the `@NgModule` decorator.

```typescript
import { FormsModule, ReactiveFormsModule } from '@angular/forms';

@NgModule({
  declarations: [
    // ...
  ],
  imports: [
    BrowserModule,
    FormsModule, // Add this
    ReactiveFormsModule, // Add this
    AppRoutingModule,
  ],
  bootstrap: [AppComponent],
})
export class AppModule {}
```

### Step 7: Add Routing Links

Open the `src/app/app.component.html` file and add navigation links for your sign-in form and welcome page.

```html
<nav>
  <a routerLink="/">Welcome</a>
  <a routerLink="/signin">Sign In</a>
</nav>
<router-outlet></router-outlet>
```

### Step 8: Styling (Optional)

You can apply CSS styles to your components for a better appearance.

### Step 9: Run Your Application

Run the following command to start your Angular development server:

```bash
ng serve
```

Open your browser and navigate to `http://localhost:4200`. You should see your welcome page with navigation links to the sign-in form.

This is a basic example of creating a sign-in form in Angular. You can further enhance it by adding authentication, validation, and error handling as needed for your project.
