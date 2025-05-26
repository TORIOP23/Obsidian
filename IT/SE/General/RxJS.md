[RxJS](https://rxjs.dev/api)

[Learn RxJS](https://www.learnrxjs.io/)

[Integrated Learning Experience](https://app.pluralsight.com/ilx/video-courses/51676108-c3a6-4a95-91e9-c52ec8aa0791/adee1db0-b573-4154-ab14-8642d960c594/2a035715-efd3-41ce-a5ad-b2839ba4eb5e)
## Type
- **Observable:** luồng dữ liệu có thể bao gồm các giá trị, sự kiện hoặc các đối tượng khác.
- **Observer:** đối tượng được sử dụng để lắng nghe các giá trị được emit bởi một Observable.
- **Subscription:** đối tượng đại diện cho sự kết nối giữa một Observable và một Observer.
- **Operator:** hàm có thể được sử dụng để thay đổi cách một Observable hoạt động

**Các loại Observable cơ bản**
- **Simple Observable:** Đây là loại Observable đơn giản nhất. Nó chỉ emit các giá trị và không có bất kỳ hành vi nào khác.
- **Cold Observable:** Loại Observable này chỉ bắt đầu emit các giá trị khi có một Observer subscribe vào nó.
- **Hot Observable:** Loại Observable này emit các giá trị ngay cả khi không có Observer nào subscribe vào nó.

**Các loại Observable nâng cao**
- **BehaviorSubject:** Loại Observable này emit giá trị hiện tại của nó cho tất cả các Observer mới subscribe vào nó.
- **ReplaySubject:** Loại Observable này lưu trữ một số giá trị đã emit trước đó và emit các giá trị đó cho tất cả các Observer mới subscribe vào nó.
- **AsyncSubject:** Loại Observable này chỉ emit giá trị cuối cùng cho tất cả các Observer mới subscribe vào nó.

### Create an Observable
- `of` automatic complete
```jsx
const apple$ = of('Apple1', 'Apple2');
const apples$ = from(['Apple1', 'Apple2'])
const click$ = fromEvent(document, 'click')
const item$ = timer(initialDelay)
```

### Rxjs Operator
- Map, tap, take, filter
- `take` limit observable
- `tap` for debugging