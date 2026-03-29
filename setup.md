# Firebase 设置指南

## 1. 创建 Firebase 项目
1. 打开 [Firebase Console](https://console.firebase.google.com/)
2. 创建新项目（名称随意，如 `cogito-pitch`）
3. 关闭 Google Analytics（不需要）

## 2. 启用 Realtime Database
1. 左侧菜单 → Build → Realtime Database
2. 创建数据库 → 选择区域（推荐 `asia-southeast1`）
3. 安全规则选 **测试模式**（30天免配置）

## 3. 获取配置
1. 项目设置（齿轮图标）→ 常规 → 你的应用
2. 点击 Web 图标 `</>` 添加应用
3. 复制 `firebaseConfig` 对象

## 4. 填入配置
在 `index.html` 和 `dm.html` 中找到 `FIREBASE_CONFIG`，替换为你的配置：

```javascript
const FIREBASE_CONFIG = {
  apiKey: "AIzaSy...",
  authDomain: "cogito-pitch.firebaseapp.com",
  databaseURL: "https://cogito-pitch-default-rtdb.asia-southeast1.firebasedatabase.app",
  projectId: "cogito-pitch",
  storageBucket: "cogito-pitch.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abc123"
};
```

## 5. 部署（可选）
最简单的方式：
```bash
npx serve ./web
```
然后访问 `http://localhost:3000`

或者部署到 Firebase Hosting：
```bash
npm install -g firebase-tools
firebase login
firebase init hosting  # 选择 web/ 作为公共目录
firebase deploy
```

## 6. DEMO 模式
如果不配置 Firebase，系统自动进入 DEMO 模式：
- 身份验证正常工作
- 投票仅在本地生效（不跨设备同步）
- DM控制台显示模拟数据
- 适合提前彩排和测试流程
