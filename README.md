# DFPServer
Cung cấp các api cho việc xử lý file phân tán

## Các công nghệ sử dụng
###### - NodeJS
###### - Monogodb

## Set up server local trên máy của bạn
### Yêu câu máy có cài đặt NodeJS version 8 trở lên, cài đặt thêm nodemon dành cho phát triển api
### 1. Tải mã nguồn
###### `git clone  https://github.com/JackieNek/DFPServer.git`
### 2. Truy cập thư mục mã nguồn
######  `cd DFPServer`
### 3. Cài đặt các thư viện
######  `npm install`
### 4. Run server
######  Dành cho sử dụng api `node index.js
######  Dành cho phát triển api `npm start`
######  restart server bằng lệnh `rs`
### 5. Kiểm tra:
######  truy cập `http://localhost:8000/api/test` bằng trình duyệt kết quả thu được chuỗi json `{"test":"ok"}`

## Dành cho dev
### 1. Làm việc với cơ sở dữ liệu
##### Đăng ký collection trong cơ sở dữ liệu
######  Tạo một mô hình collection trong `lib/collection/`(tham khảo `lib/collection/test.js`) và đăng ký nó trong file `lib/collection/index.js`
##### CRUD với collection
######  Tạo một file trong `lib/` tại đây có thể xử lý các thao tác crud với collection (tham khảo `lib/test.js`) đăng ký trong file `lib/index.js`
### 2. Phát triển api
##### Đăng ký api
######  Tham khảo file `api/index.js`
##### Cấu trúc api
######  Tham khảo folder `api/test`
##### Sử đụng CRUD với api trong controller hoặc middleware
######  `lib.collectionName.function()`

## Document api link
######  https://docs.google.com/spreadsheets/d/1pmnSbpOP7B07nYl6Y43x564lbmREUWfmDVxX2A1_AT4/edit?fbclid=IwAR3EA9FIbZBxH40JKVo8507XFPiMfGNwd78hzkZTKB2tvFpuVKOMVktcjPk#gid=1736681266

### RECORD
#### Cấu trúc
###### `{`
###### `  fileId: String,`
###### `  speaker: String,`
###### `  time: Number,`
###### `  content: String`
###### `}`
##### 1. GET `/api/record`
##### Chức năng: liệt kê các bản ghi
##### Các tham số của query 
###### - `recordID`: id của bản ghi - kiểu dữ kiệu: ObjectID
###### - `fileId`: id của file      - kiểu dữ liệu: ObjectID
###### - `speaker`: người nói       - Kiểu dữ liệu: String
###### Đầu ra: Danh sách các bản ghi

##### 2. POST `/api/record/:fileID`
###### Chức năng: tạo mới một bản ghi
###### Đầu vào: data1, data2 chứa trong `body`
###### `data1: {`
###### `  speaker: String,`
###### `  time: Number,`
###### `}`
###### `data2: {`
###### `  time: Number,`
###### `  content: String`
###### `}`
###### Đầu ra: `record` chứa thêm trường `_id`

##### 3. PUT `/api/record/:id`
###### Chức năng: Sửa một bản ghi có sẵn
###### Tham số `id` là id của bản ghi - kiểu dữ liệu ObjecID
###### Đầu vào: `options` chứa các trường thay đổi ghi vào trong `body`
###### Đầu ra: Bản ghi đã được sửa

##### 4. DELETE `/api/record/:id`
###### Chức năng: Xóa một bản ghi có sẵn
###### Tham số `recordID` là id của bản ghi - kiểu dữ liệu ObjecID

### FILE
#### Cấu trúc
###### `{`
###### `  name: String,`
###### `  creator: String,`
###### `  owners: Array`
###### `  createAt: Number` 
###### `}`
##### 1. GET `/api/file`
##### Chức năng: liệt kê các file
##### Các tham số của query 
###### - `creator`: id của bản ghi - kiểu dữ kiệu: ObjectID
###### - `fileId`: id của file     - kiểu dữ liệu: ObjectID
###### - `owner`: người nói        - Kiểu dữ liệu: ObjectID
###### Đầu ra: Danh sách các file

##### 2. POST /api/file
###### Chức năng: tạo mới một file
###### Đầu vào: 
###### `name: "file 2",`
###### `createAt: 123456,`
###### `owners:[]`
###### Đầu ra: 
###### `{`
###### `    _id: "5bd7039bae427baf213d5c05"`
###### `	name: "file 2",`
###### `    creator: "5bd7039bae427baf213d5c05"
###### `	createAt: 123456,`
###### `	owners:[]`
###### `}`

##### 3. PUT `/api/file/:id`
###### Chức năng: Sửa một bản ghi có sẵn
###### Tham số `fileID` là id của bản ghi - kiểu dữ liệu ObjecID
###### Đầu vào: `options` chứa các trường thay đổi ghi vào trong `body`
###### Đầu ra: File đã được sửa thông tin

##### 4. DELETE `/api/file/:id`
###### Chức năng: Xóa một file có sẵn
###### Tham số `id` là id của file - kiểu dữ liệu ObjecID
