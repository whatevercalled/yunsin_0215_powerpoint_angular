
# Service
用注入service的方式，減少組件的代碼，並且可以復用
```
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root'
})
export class ExampleService {
  num = 0;

  constructor() { }

  add() {
    this.num++;
  }

}
```
```
export class A1Component implements OnInit {
  get num() {
    return this.exampleService.num;
  }

  constructor(private exampleService: ExampleService) { }

  ngOnInit(): void {
  }

  add() {
    this.exampleService.add();
  }

}
```