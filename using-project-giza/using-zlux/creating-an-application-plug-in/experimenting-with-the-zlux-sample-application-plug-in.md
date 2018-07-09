# Experimenting with the zLUX sample application plug-in

Your zLUX installation provides a sample application plug-in with which you can experiment.

To build the sample app, node and npm must be included in the PATH. You can use the `npm run build` or `npm start` command to build the sample application plug-in. These commands are configured in `package.json`.

**Note:**

* Be aware that whenever you change the source code for the sample application, you must subsequently rebuild the sample application.
* If you want to modify sample-app, you must run `_npm install_` in the virtual-desktop and the `sample-app/webClient`. Then, you can run `_npm run build_` in `sample-app/webClient`.
* Try adding an item to sample-app. The following figure shows the unmodified contents of `app.component.ts`:

  ```text
  import { Component } from '@angular/core';

  @Component({
   selector: 'app-root',
   templateUrl: './app.component.html',
   styleUrls: ['./app.component.css']
  })
  export class AppComponent {
   items = ['a', 'b', 'c', 'd']
   title = 'app';
  }
  ```

* Save your changes to `app.component.ts`.
* Issue one of these commands: 
  * `npm run build` to rebuild the application plug-in.
  * `npm start` to rebuild the application plug-in and wait for additional changes to `app.component.ts`.
* Reload the web page. 
* Whenever you make changes to the sample application source code, you must subsequently rebuild the application: 
  1. Navigate to the sample-app subdirectory where you made the source code changes. 
  2. Issue this command: `npm run build` 
  3. Reload the web page. 

**Parent topic:** [Creating an application plug-in](./)

