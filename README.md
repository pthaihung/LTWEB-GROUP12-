# Buggy PHP Lab

Project PHP mini cho sinh vien thuc hanh tim loi va sua loi.

## Muc tieu bai tap

Sinh vien can:

1. Chay duoc project trong local.
2. Tim toi thieu 8 loi trong source code.
3. Phan loai moi loi vao 1 trong 2 nhom:
   - `syntax`
   - `logic`
4. Sua tat ca loi de cac trang hoat dong dung.

## Cach chay

Yeu cau:

- PHP 8.1 tro len

Chay built-in server:

```bash
php -S localhost:8000
```

Mo trinh duyet:

```text
http://localhost:8000
```

## Cac trang can kiem tra

- `/` hoac `/?page=dashboard`
- `/?page=orders`
- `/?page=checkout`
- `/?page=customers`
- `/?page=reports`
- `/?page=settings`

## Goi y cho sinh vien

- Co ca loi khien trang bi `parse error`.
- Co loi khong lam crash trang, nhung tra ra ket qua sai.
- Khong can database, du lieu mau nam trong thu muc `data/`.
- Nen dung `php -l <file>` de kiem tra syntax tung file.

## Ket qua mong doi

Sau khi sua xong:

- Tat ca route deu mo duoc.
- So lieu tren dashboard hop ly.
- Danh sach don hang hien dung.
- Tinh toan checkout dung logic.
- Bao cao va cai dat khong con loi syntax.
