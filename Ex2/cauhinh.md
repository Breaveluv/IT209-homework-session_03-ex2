server {
    listen 80;
    listen [::]:80;

    server_name _;

    root /var/www/my-web/html;
    index index.html;

    # Khai báo trang lỗi 404 tùy chỉnh
    error_page 404 /404.html;

    # Cấu hình bảo mật trang lỗi 404 bằng chỉ thị internal
    location = /404.html {
        root /var/www/my-web/html;
        internal;
    }

    # Định tuyến mặc định
    location / {
        try_files $uri $uri/ =404;
    }
}