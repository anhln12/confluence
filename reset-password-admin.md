Bật Recovery Mode

Tạo ra 1 tài khoản Admin tạm thời dạng Rescue Mode mà không cần sửa DB.

Bước 1: Stop conluence service
```
systemctl stop confluence
# Hoặc: /opt/atlassian/confluence/bin/stop-confluence.sh
```
Bước 2: Thêm tham số Recovery Mode vào JVM
```
/opt/atlassian/confluence/bin/setenv.sh

CATALINA_OPTS="-Datlassian.recovery.password=PasswordRescue123 $CATALINA_OPTS"
```

Bước 3: Start lại Confluence và đăng nhập
```
systemctl start confluence
```

Bước 4: Truy cập Web UI đăng nhập
```
Username: recovery_admin
Password: PasswordRescue123
```

Bước 5: Reset password cho admin chính
```
Truy cập General Configuration > Users (hoặc User Management).
Tìm user admin cần reset, chọn Edit / Set Password.
Lưu lại mật khẩu mới.
```

Bước 6: Tắt Recovery Mode
```
Xóa dòng -Datlassian.recovery.password=... trong setenv.sh, sau đó restart lại Confluence để đảm bảo an toàn bảo mật.
```

