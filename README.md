# Chet — Setup Guide

Firebase config udah ditanam di `index.html` (project: rhf-chet). Tinggal:

## 1. Aktifkan Google Sign-In
Firebase Console → Authentication → Sign-in method → aktifkan **Google**

## 2. Deploy Firestore Rules
Firebase Console → Firestore Database → Rules → paste isi `firestore.rules` → Publish

(Kalau Firestore belum dibuat: Firestore Database → Create database → mode production/test, lalu baru paste rules)

## 3. Push ke GitHub

```bash
git init
git add .
git commit -m "init chet"
git remote add origin https://github.com/USERNAME/REPO.git
git push -u origin main
```

## 4. Deploy ke Vercel
Buka vercel.com → Import Project → pilih repo GitHub-nya → Deploy (zero config, udah ada `vercel.json`)

## 5. Authorized Domain (WAJIB)
Firebase Console → Authentication → Settings → Authorized domains
→ tambahkan domain Vercel kamu (contoh: `chet.vercel.app`)

Tanpa ini, Google Sign-In bakal gagal di production.

---

**Catatan:** config punya `databaseURL` (Realtime Database) tapi app ini pakai **Firestore** untuk chat/room (lebih gampang query + scalable). Realtime Database-nya nganggur, aman diabaikan — gak ganggu apa pun.
