# Câu A1 — Viewport & Mobile-First
## 1. 
- Thẻ meta viewport chuẩn
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```
- Giải thích từng thuộc tính
name="viewport"

Cho trình duyệt biết đây là cấu hình viewport của trang web.

width=device-width

Chiều rộng trang web sẽ bằng chiều rộng thật của thiết bị.

Ví dụ:

iPhone nhỏ → web co lại vừa màn hình
iPad → web rộng hơn
Desktop → full chiều rộng desktop
initial-scale=1.0

Mức zoom ban đầu = 100%.

Trang web không bị zoom phóng to hoặc thu nhỏ khi mở lần đầu.

## 2. Nếu thiếu meta viewport thì chuyện gì xảy ra?

iPhone sẽ giả lập trang web như desktop khoảng 980px.

Kết quả: Làm cho:
+ Chữ cực nhỏ
+ Layout bị thu nhỏ toàn bộ
+ Người dùng phải zoom tay
+ Responsive không hoạt động đúng

## 3. So sánh Mobile-First và Desktop-First

| Mobile-First | Desktop-First |
|---|---|
| CSS mặc định cho mobile | CSS mặc định cho desktop |
| Dùng min-width | Dùng max-width |
| Mở rộng dần lên tablet, desktop | Thu nhỏ dần xuống mobile |
| Tối ưu hiệu năng mobile tốt hơn |	Dễ bị CSS chồng chéo |

- VD về Mobile-First:
/* Mobile */
.container {
    font-size: 14px;
}

/* Tablet trở lên */
@media (min-width: 768px) {
    .container {
        font-size: 18px;
    }
}

- VD về Desktop-First:
/* Desktop */
.container {
    font-size: 18px;
}

/* Tablet trở xuống */
@media (max-width: 768px) {
    .container {
        font-size: 14px;
    }
}

- Tại sao Mobile-First được khuyên dùng?
+ Mobile hiện chiếm đa số người dùng
+ CSS nhẹ hơn
+ Hiệu năng tốt hơn
+ Responsive dễ quản lý hơn
+ Google ưu tiên Mobile-First indexing
+ Dễ scale từ nhỏ → lớn hơn

# Câu A2 — Breakpoints

| Breakpoint | Pixel | Thiết bị đại diện | Ví dụ lưới sản phẩm |
|---|---|---|---|
| Extra Small | <576px | Mobile nhỏ | 1 cột |
| Small | ≥576px | Mobile lớn | 1-2 cột |
| Medium | ≥768px | Tablet | 2 cột |
| Large | ≥992px | Laptop | 3 cột |
| Extra Large | ≥1200px | Desktop | 4 cột |
| XXL | ≥1400px | Màn hình lớn | 5-6 cột |

# Câu A3 — Media Queries

| Chiều rộng màn hình | .container width |
|---|---|
| 375px (iPhone SE) | 100% |
| 600px | 540px |
| 800px | 720px |
| 1000px | 960px |
| 1400px | 1140px |

# A4 — SCSS Basics

| Tính năng | Giải thích | Ví dụ |
|---|---|---|
| Variables | Lưu giá trị để tái sử dụng | $primary-color: blue; |
| Nesting | Viết CSS lồng nhau | .card { .title {} } |
| Mixins | Tái sử dụng nhóm CSS | @mixin flex-center |
| @extend | Kế thừa CSS | .btn-primary @extend .btn |

## Tại sao trình duyệt không đọc được .scss?

- Vì trình duyệt chỉ hiểu CSS thuần.

- SCSS cần được compile sang CSS trước khi chạy trên trình duyệt.

## Compile SCSS → CSS

### Cài Sass

```bash
npm install -g sass
```

### Compile SCSS sang CSS

```bash
sass scss/style.scss style.css
```