
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
# functional programming
<a name="functionalprogram"></a>
```
function calculationBMI(bmi
  if(bmi < 0) {
    return '資料錯誤'
  } else if(bmi < 18.5) {
    return '過輕'
  } else if(bmi >= 18.5 && bmi < 24) {
    return '正常'
  } else if(bmi >= 24 && bmi < 27) {
    return '過重'
  } else if(bmi >= 27 && bmi < 30) {
    return '輕度肥胖'
  } else if(bmi >= 30 && bmi < 35) {
    return '中度肥胖'
  } else{
    return '重度肥胖'
  }
}

calculationBMI(20); // '正常'
```
```
// match 函式先省略
const lessThan = x => bmi => bmi< x ;

const calculationBMI = BMI => 
match(BMI)
.on(lessThan(0), () => '資料錯誤')
.on(lessThan(18.5), () => '體重過輕')
.on(lessThan(24), () => '正常')
.on(lessThan(27), () => '過重')
.on(lessThan(30), () => '輕度肥胖')
.on(lessThan(35), () => '中度肥胖')
.otherwise(() => "重度肥胖")


calculationBMI(20); // '正常'
```