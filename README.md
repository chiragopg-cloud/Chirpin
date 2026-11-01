
# 🐦 Chirpin

A modern social media platform where people can connect, share posts, upload media, follow users, and interact with their community.

## ✨ Features

- 👤 User profiles
- ➕ Follow and unfollow users
- 📝 Create and delete posts
- 🖼️ Image and video posts
- 💬 Comments and threaded replies
- ❤️ Like posts
- ☑️ Verified badges
- 👑 VIP badges
- 🛡️ Admin panel
- 🚫 Ban and unban accounts
- 🗑️ Post moderation
- 🔤 Blocked-word filtering
- 🎨 Light theme with purple accents

## 🛠️ Tech Stack

- React
- TypeScript
- TanStack Start
- TanStack Router
- Tailwind CSS
- Better Auth
- SQL Database

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone YOUR_REPOSITORY_URL
cd chirpin
```

### 2. Install dependencies

```bash
npm install
```

### 3. Configure environment variables

Create a `.env` file in the project root.

```env
DATABASE_URL=your_database_url
BETTER_AUTH_SECRET=your_secret_key
BETTER_AUTH_URL=http://localhost:3000
ADMIN_EMAILS=your_registered_email@example.com
```

Keep your secrets private. Never commit your `.env` file.

### 4. Run database migrations

Run the database migration process configured by your project.

### 5. Start the development server

```bash
npm run dev
```

Open:

```text
http://localhost:3000
```

## 🛡️ Admin Panel

Visit:

```text
/admin
```

Admin access is controlled through the server-side `ADMIN_EMAILS` environment variable.

Admins can:

- Assign or remove verified badges
- Assign or remove VIP badges
- Ban or unban accounts
- Moderate and delete posts
- Manage blocked words

Never rely on a password check performed only in the browser for admin security.

## 🌐 Deployment

You can deploy Chirpin using platforms such as:

- Vercel
- Netlify (if configured for the app's server runtime)

For Vercel:

1. Import your GitHub repository.
2. Configure the required environment variables.
3. Connect your production database.
4. Deploy the project.
5. Visit `/admin` after signing in with your configured admin account.

## 🔐 Security

- Keep API secrets private.
- Use server-side authorization for admin actions.
- Validate user input on the server.
- Do not expose admin credentials in frontend code.
- Back up your database regularly.

## 📄 License

Choose a license before distributing or accepting contributions to this project.

---

Made with 💜 for the Chirpin community.
