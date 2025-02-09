

# @if, @for, @switch Directives in Angular 17  
  
## \*ngIf Directive  
  
```html  
<div *ngIf="isLoggedIn">Welcome, user!</div>  
```  
  
- Dễ sử dụng và hiểu  
- Performance Overhead: Khi điều kiện thay đổi, Angular sẽ destroy và re-create DOM element. Điều này có thể tốn nhiều hiệu suất, khi 1 điều kiện phức tạp và thay đổi nhiều lần.  
  
## @if Directive  
  
```html  
<div @if="isLoggedIn">Welcome, user!</div>  
```  
  
- Sử dụng `@if` directive. Không destroy và re-create DOM element.  
- Có thể 1 số thư viện và công cụ bên thứ 3 không hỗ trợ `@if` directive.  
- You don't need to import the directive or the CommonModule when build standalone components.  
- Droping thoses directives also drops a few kBs from the main bundle.  
  
## Example  
  
```html  
<div @if="userStatus$ | async === 'online'">User is online</div>  
```  
  
## @for Directive  
  
```html  
@for (car of cars; track car) {  
   <option [value]="car.value">{{car.viewValue}}</option>}  
```  
  
- In the case of the @for block, feature wise they serve the same purpose with a few advantages :  
  
No need to import the directive in standalone components  
Generate a bit less code in the final bundle  
enable better DX for track by passing a key directly.  
Make devs more concious about the track functionality by making it required.  
Nice DX for empty for-loops with the @empty block