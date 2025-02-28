## BSON 
- Binary JSON
- [Difference Between JSON and BSON - GeeksforGeeks](https://www.geeksforgeeks.org/difference-between-json-and-bson/)
- [Explaining BSON With Examples | MongoDB](https://www.mongodb.com/basics/bson)
- MongoDB stores data in BSON format.
- Use more space but faster than JSON.
- Has encoding and decoding technique.
- A single MongoDB document cannot exceed 16MB in size.

## Change Stream
- **MongoDB Change Stream yêu cầu dữ liệu phải bền vững**, nên nó chỉ hoạt động với `readConcern: "majority"` (đọc dữ liệu đã được nhiều node xác nhận).
- `readConcern: "available"` dùng cho đọc dữ liệu nhanh nhưng có thể chưa chính xác trên replica set.
## Read Concern
