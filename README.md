# Token Proxy Service

Serverless proxy API để lấy Microsoft OAuth Access Token cho Power Automate.

## 🏗️ Cấu trúc Project

```
├── api/
│   └── get-token.js     # Serverless function
├── .env.example         # Template environment variables
├── .gitignore           # Bảo vệ secrets
├── package.json         # Dependencies
├── vercel.json          # Cấu hình Vercel
└── README.md            # Tài liệu này
```

## 🚀 Cách Deploy lên Vercel

### Bước 1: Push code lên GitHub

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
git push -u origin main
```

### Bước 2: Connect với Vercel

1. Truy cập [vercel.com](https://vercel.com)
2. Click **"Add New Project"**
3. Import repository từ GitHub
4. Click **"Deploy"**

### Bước 3: Cấu hình Environment Variables

1. Vào **Project Settings** → **Environment Variables**
2. Thêm các biến sau:

| Name | Value |
|------|-------|
| `TENANT_ID` | Azure AD Tenant ID của bạn |
| `CLIENT_ID` | App Registration Client ID |
| `CLIENT_SECRET` | App Registration Secret |

3. Click **"Save"**
4. **Redeploy** để áp dụng thay đổi

## 📡 Cách sử dụng API

### Endpoint

```
POST https://your-project.vercel.app/api/get-token
```

### Response

```json
{
  "token_type": "Bearer",
  "expires_in": 3599,
  "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOi..."
}
```

### Ví dụ gọi API

```javascript
const response = await fetch('https://your-project.vercel.app/api/get-token', {
  method: 'POST'
});
const data = await response.json();
console.log(data.access_token);
```

## 🔒 Bảo mật

- ✅ Secrets được lưu trong Vercel Environment Variables
- ✅ `.gitignore` chặn file `.env` khỏi Git
- ✅ Không hardcode bất kỳ secret nào trong code

## 📝 License

MIT
