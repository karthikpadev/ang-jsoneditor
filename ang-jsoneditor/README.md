# Angular Json Editor

[![Build Status](https://travis-ci.org/mariohmol/ang-jsoneditor.svg?branch=master)](https://travis-ci.org/mariohmol/ang-jsoneditor)

Angular Json Editor (wrapper for [jsoneditor](https://github.com/josdejong/jsoneditor)). View/Edit Json file with formatting.

[StackBlitz template](https://stackblitz.com/edit/angular-json-editor)

Working with latest Angular 6. 

![Demo Image](/src/assets/printDemo.png)

## Installation

To install this library with npm, run below command:

$ npm install --save jsoneditor ang-jsoneditor


Example:

```html
<json-editor [options]="editorOptions" [data]="data" (change)="getData($event)"></json-editor>
```

## Usage

### Configuration

First, Import Angular  JsonEditor module in root

```ts
import { NgJsonEditorModule } from 'ang-jsoneditor' 

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    ....,
    NgJsonEditorModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```
Then setup your component models as below :

```ts
import { Component, ViewChild } from '@angular/core';
import { JsonEditorComponent, JsonEditorOptions } from 'ang-jsoneditor';

@Component({
  selector: 'app-root',
  template: '<json-editor [options]="editorOptions" [data]="data"></json-editor>',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  public editorOptions: JsonEditorOptions;
  public data: any;
  @ViewChild(JsonEditorComponent) editor: JsonEditorComponent;

  constructor() { 
    this.editorOptions = new JsonEditorOptions()
    this.editorOptions.modes = ['code', 'text', 'tree', 'view']; // set all allowed modes
    //this.options.mode = 'code'; //set only one mode
      
      this.data = {"products":[{"name":"car","product":[{"name":"honda","model":[{"id":"civic","name":"civic"},{"id":"accord","name":"accord"},{"id":"crv","name":"crv"},{"id":"pilot","name":"pilot"},{"id":"odyssey","name":"odyssey"}]}]}]}
  }

}
```
Note : For better styling, add below line to your main style.css file

```js
@import "~jsoneditor/dist/jsoneditor.min.css";
```

### Extra Features

Besides all the 
[configuration options](https://github.com/josdejong/jsoneditor/blob/master/docs/api.md) 
from the original jsoneditor, Angular Json Editor supports one additional option:

_expandAll_ - to automatically expand all nodes upon json loaded with the _data_ input. 

# Troubleshoot

If you have issue with the height of the component, you can try one of those solutions:

When you import CSS:

```css
@import "~jsoneditor/dist/jsoneditor.min.css";
textarea.jsoneditor-text{min-height:350px;}
```

Or Customizing the CSS:

```css
:host ::ng-deep json-editor,
:host ::ng-deep json-editor .jsoneditor,
:host ::ng-deep json-editor > div,
:host ::ng-deep json-editor jsoneditor-outer {
  height: 500px;
}
```

Or  as a inner style in component:

```html
<json-editor class="col-md-12" #editorExample style="min-height: 300px;" [options]="editorOptionsData" [data]="dataStructure"></json-editor>
```


# Demo

Demo component files are included in Git Project.

Demo Project with a lot of different implementations (ngInit, change event and others):
[https://github.com/mariohmol/ang-jsoneditor/tree/master/src/app/demo)

When publishing it to npm, look over this docs: https://docs.npmjs.com/misc/developers

# License
MIT(./LICENSE)
