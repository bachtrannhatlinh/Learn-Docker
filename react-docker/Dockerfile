# Sử dụng Node.js phiên bản Alpine để tạo image nhẹ
FROM node:20-alpine

# Tạo user app không có quyền root để bảo mật hơn
RUN addgroup app && adduser -S -G app app

# Thiết lập thư mục làm việc
WORKDIR /app

# Sao chép package.json và package-lock.json vào container trước khi chạy npm install
COPY package*.json ./

# Cài đặt dependencies trước khi đổi user
RUN npm install

# Đổi quyền sở hữu để user app có thể truy cập
RUN chown -R app:app /app

# Đổi user thành app
USER app

# Sao chép toàn bộ project vào container
COPY --chown=app:app . .

# Mở cổng cho Vite chạy
EXPOSE 5173

# Lệnh mặc định để chạy project
CMD ["npm", "run", "dev"]
