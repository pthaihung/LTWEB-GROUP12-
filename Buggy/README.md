# Buggy PHP Lab

Project PHP mini cho sinh viên thực hành tìm lỗi và sửa lỗi.

## Mục tiêu bài tập

Sinh viên cần:

1. Chạy được project trong môi trường local.
2. Tìm tối thiểu 8 lỗi trong source code.
3. Phân loại mỗi lỗi vào 1 trong 2 nhóm:
   - `syntax`
   - `logic`
4. Sửa tất cả lỗi để các trang hoạt động đúng.

## Cách chạy

Yêu cầu:

- PHP 8.1 trở lên

Chạy built-in server:

```bash
php -S localhost:8000
```

Mở trình duyệt:

```text
http://localhost:8000
```

## Các trang cần kiểm tra

- `/` hoặc `/?page=dashboard`
- `/?page=orders`
- `/?page=checkout`
- `/?page=customers`
- `/?page=reports`
- `/?page=orders`

## Gợi ý

- Có cả lỗi khiến trang bị `parse error`.
- Có lỗi không làm crash trang, nhưng trả ra kết quả sai.
- Không cần database, dữ liệu mẫu nằm trong thư mục `data/`.
- Nên dùng `php -l <file>` để kiểm tra syntax từng file.

## Kết quả mong đợi

Sau khi sửa xong:

- Tất cả route đều mở được.
- Số liệu trên dashboard hợp lý.
- Danh sách đơn hàng hiển thị đúng.
- Tính toán checkout đúng logic.
- Báo cáo và cài đặt không còn lỗi syntax.

## Sửa lỗi: 
## syntax:
-   /?page=customers : thiếu ; ở line 3
-   /?page=orders : thiếu `)` ở line 15
-   /?page=orders : thiếu , ở line 
## logic:
- `/?page=checkout` 
   foreach ($cart as $item) {
    $subtotal += $products[$item['sku']]['price'] * $item['qty'];}

- `/?page=checkout`
   $discountPercent = 10;
   $discountValue   = $subtotal * ($discountPercent / 100); // discount 10% thì phải * 0.1
   $shippingFee     = $subtotal >= 50 ? 0 : 5;    //  Đơn hàng lớn hơn thì được free
   $vat             = ($subtotal - $discountValue) * 0.1; // VAT phải tính sau khi trừ đi Discount
   $grandTotal      = $subtotal - $discountValue + $shippingFee + $vat;
   


- `/?page=dashboard`
   foreach ($order['items'] as $item) {
        $price = $products[$item['sku']]['price'];
        $totalRevenue += $item['qty'] * $price;  // quality * price thì mới ra doanh thu
   }

- `/?page=orders`
   foreach ($products as $sku => $product) {
      if ($product['stock'] <= 5) { //hang stock <= 5 vì đó là SLowStock
        $lowStockItems[] = $sku . ' - ' . $product['name'];
      }
   }

   foreach ($orders as $order) {
      if ($order['status'] == 'pending') { //nếu có lớn hơn 2 trạng thái thì != complete sẽ wrong 
        $pendingOnly[] = $order;
      }
   }