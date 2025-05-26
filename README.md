# -Dynamic-Form-Build

A small Vue 3 app which dynamically assemble forms by selecting field types and previewing a live JSON schema

Installation:

1. Make sure Node.js (v14+) and npm are installed
   -> in the terminal:
   node -v
   npm -v
   -> If node and npm aren't installed, install them

2. After that, create a new Vite + Vue 3 project
   -> in the terminal:
   npm init vite@latest (name-of-project-folder) -- --template vue
   -> then follow the instuctions given from the code:
   cd (name-of-project-folder)
   npm install
   npm run dev

About the project:

The architecture of my project is simple. I have a main file, App.vue, from where I display my main three components:

- FieldPallet, FormBuilder, and JSONSchemaPreview

My main file works as a communication channel for the three components. The functions for adding, updating, and removing input fields are located in App.vue.

The three components are just rendering the ref, which stores all the inputs. From the FieldPallet, I create the buttons, which then emit an adding function in App.vue. From there, the adding function adds an input of the button type and displays it through the fields ref. When a field is updated or removed, a remove or add function is emitted from FormBuilder. From there, again, the fields ref is updated and displayed again, updated. The JSONSchemaPreview only displays the fields as a JSON string. Each time the ref is updated, the component re-render as well.
