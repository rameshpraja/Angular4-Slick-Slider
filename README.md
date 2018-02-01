# ngx-slick


## Installation

To install this library, run:

```bash
$ npm install ngx-slick --save
```


after installation, go to your Root module : `App Module`

```typescript
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';

import { AppComponent } from './app.component';

// Import your library
import { SlickModule } from 'ngx-slick';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule,

    // Specify your library as an import
    SlickModule.forRoot()
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

- Include Jquery and Slick css/js in your application - go to index.html and paste below libraries :
```
<script src="//code.jquery.com/jquery-3.2.1.min.js"></script>
<link rel="stylesheet" type="text/css" href="//cdn.jsdelivr.net/jquery.slick/1.6.0/slick.css"/>
<link rel="stylesheet" type="text/css" href="//cdn.jsdelivr.net/jquery.slick/1.6.0/slick-theme.css"/>
<script src="https://unpkg.com/slick-carousel@1.6.0/slick/slick.js"></script>
```

Once your library is imported, you can use its components, directives and pipes in your Angular application:
```html
  1. goto  app.component.html
 <!-- You can now use your library component in app.component.html -->
  <ngx-slick class="carousel" #slickModal="slick-modal" [config]="slideConfig" (afterChange)="afterChange($event)">
    <div ngxSlickItem *ngFor="let slide of slides" class="slide">
          <img src="{{ slide.img }}" alt="" width="100%">
    </div>
</ngx-slick>

<button (click)="addSlide()">Add</button>
<button (click)="removeSlide()">Remove</button>
<button (click)="slickModal.slickGoTo(2)">slickGoto 2</button>
<button (click)="slickModal.unslick()">unslick</button>
```

```javascript
  2. goto app.component.ts file

import { Component } from '@angular/core';

//import slick module
import {SlickModule} from 'ngx-slick';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'app';

//Start - slides array and functions
  slides = [
    {img: "http://placehold.it/350x150/000000"},
    {img: "http://placehold.it/350x150/111111"},
    {img: "http://placehold.it/350x150/333333"},
    {img: "http://placehold.it/350x150/666666"}
  ];
  slideConfig = {"slidesToShow": 4, "slidesToScroll": 4};

  addSlide() {
    this.slides.push({img: "http://placehold.it/350x150/777777"})
  }

  removeSlide() {
    this.slides.length = this.slides.length - 1;
  }

  afterChange(e) {
    console.log('afterChange');
  }
  //End - slides array and functions
}
```


## Run Project
Now to run the project in your local machine, you just need to run :

    ng serve

so you will start a web server on http://localhost:4200

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md).