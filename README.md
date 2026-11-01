# Chirpin

Chirpin is a light, purple-accented community app built with React, TanStack Start, and PostgreSQL/PGlite.

## Social features

- Follow and unfollow profiles, with follower/following counts.
- A **Following** feed containing your own posts and posts from people you follow, alongside **For you** (the public community feed).
- Threaded replies on posts.
- Image and video attachments on posts (JPEG, PNG, GIF, WebP, MP4, WebM, QuickTime; 5 MB maximum per attachment).

## Database migration

`migrations/0003_chirpin_social.sql` adds the follow graph, comment parent references, and post media columns. It is applied automatically by the existing migration runner on startup/build.

## Media storage note

For portability, media attachments are currently stored as base64 data URLs in the post database row. This is suitable for small early-stage uploads and demos, but is not an ideal long-term media architecture. Before public scale, move uploads to object storage (for example, S3-compatible storage or Cloudinary) and persist only the returned media URL.

## Run

```bash
npm install
npm run dev
```

The app uses the existing auth configuration and database setup. A deployed instance needs its configured authentication provider and `DATABASE_URL` as described by the original project setup.


## Admin panel and member badges

Set the server-only `ADMIN_EMAILS` environment variable to a comma-separated list of administrator email addresses (for example, `owner@example.com`). These addresses must belong to existing signed-in accounts. The Admin link then appears for those accounts, where admins can grant/revoke Verified and VIP badges. Never expose `ADMIN_EMAILS` as a `VITE_` variable. The database migration `0004_chirpin_roles_badges.sql` adds the badge fields.


## Admin and moderation

Set `ADMIN_EMAILS` in the server environment to a comma-separated list of the email addresses of registered Chirpin accounts that should administer the site. Keep this variable server-side (never prefix it with `VITE_`). Admins sign in normally, then open `/admin`. Admin endpoints re-check the allowlist on the server.

Migration `0005_chirpin_moderation.sql` adds account suspension and the blocked-word list. The admin panel can assign verified/VIP badges, suspend or restore accounts, remove posts (including attached image/video data), and manage blocked words. Suspended accounts are rejected by the server auth middleware. Blocked words are checked against new posts and replies.
