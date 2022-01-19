# visualize-response-in-postman
visualize response in postman

```
// Bước 1: lưu data cần visualize vào 1 object
// Lấy json response từ API: var objectData = pm.response.json()
var objectData = pm.response.json()
// var objectData = {"singers":[{"id":1,"name":"Sơn Tùng M-TP","hot_songs":["Hãy trao cho anh","Lạc trôi","Không phải dạng vừa đâu","Cơn mưa ngang qua"]},{"id":2,"name":"Mr. Siro","hot_songs":["Lắng nghe nước mắt","Một bước yêu vạn dặm đau"]},{"id":3,"name":"Bích Phương","hot_songs":["Có khi nào rời xa","Đi đu đưa đi","Bao giờ lấy chồng"]}],"total":3,"total_song":9}

```

```
// Bước 2: Tạo template (dùng handlebars)
// var template = `{{statusCode}}`

//  <h2>Total {{ tbl_portrait_customer }}</h2>
// <h2>Total {{ data.tbl_portrait_customer }}</h2>

// <h2>Total {{ data.tbl_portrait_customer }}</h2>
var template = `
    <ul>
    {{#each data.tbl_portrait_customer}}
        <li>{{this.portrait_customer_name}}</li>
    {{/each}}
    </ul>
`
// var template = `<div>
//     <p>- Tổng số ca sĩ: {{total}}</p>
//     <p>- Tổng số bài hát: {{total_song}}</p>
// </div>
// <table>
//     <thead>
//     <tr>
//         <th>ID</th>
//         <th>Name</th>
//         <th>Hot songs</th>
//     </tr>
//     </thead>
//     <tbody>
//     {{#each singers}}
//     <tr>
//         <td>{{id}}</td>
//         <td>{{name}}</td>
//         <td>
//             {{#each this.hot_songs}}
//             <span>{{this}}, </span>
//             {{/each}}
//         </td>
//     </tr>
//     {{/each}}
//     </tbody>
// </table>`

```

```
// Bước 3: Set template
pm.visualizer.set(template, objectData)

```
