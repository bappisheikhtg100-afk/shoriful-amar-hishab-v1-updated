# আমার হিসাব (Amar Hisab) — Offline Android APK (Capacitor + GitHub Actions)

একটি সম্পূর্ণ অফলাইন, প্রিমিয়াম ও মিনিমালিস্ট ব্যক্তিগত আয়-ব্যয়, দেনা-পাওনা (খাতা), বাজেট, শিডিউল টাস্ক রিমাইন্ডার, সঞ্চয় লক্ষ্যমাত্রা, মাসিক বিল, কন্টাক্ট বুক ও ক্যালকুলেটর ভল্ট অ্যাপ।

## কীভাবে GitHub থেকে অটোমেটিক `.apk` ফাইল তৈরি করবেন:

1. প্রজেক্টের সব কোড আপনার GitHub Repository-তে Push করুন।
2. **(গুরুত্বপূর্ণ ধাপ — APK অটো-বিল্ড চালু করতে):** GitHub-এর সিকিউরিটি নিয়মের কারণে থার্ড-পার্টি অ্যাপ সরাসরি `.github/workflows/` ফোল্ডারে ফাইল Push করতে পারে না। তাই ওয়ার্কফ্লো ফাইলটি `apk-workflow/build-apk.yml` নামে রাখা হয়েছে।
   - GitHub Repository-তে গিয়ে `apk-workflow/build-apk.yml` ফাইলটি ওপেন করুন।
   - ডানপাশের **Edit (✏️)** আইকনে ক্লিক করুন।
   - ফাইলের নামের বক্সে `apk-workflow/build-apk.yml` পরিবর্তন করে `.github/workflows/build-apk.yml` লিখে **Commit changes** বাটনে ক্লিক করুন।
3. সাথে সাথে Repository-এর **Actions** ট্যাবে **Build Offline Android APK (Amar Hisab)** অটোমেটিক চালু হয়ে যাবে। ২–৩ মিনিট পর বিল্ড শেষ হলে **Artifacts** বা **Releases** থেকে সাইন্ড `amar-hisab.apk` ডাউনলোড করে ফোনে ইনস্টল করুন!

## অফলাইন পারমিশনসমূহ (অটোমেটিক যুক্ত করা আছে):
- `POST_NOTIFICATIONS`, `SCHEDULE_EXACT_ALARM`, `USE_EXACT_ALARM`, `RECEIVE_BOOT_COMPLETED` — ইন্টারনেট ছাড়াই নির্দিষ্ট সময়ে রিমাইন্ডার ও অ্যালার্ম নোটিফিকেশন পাঠানোর জন্য।
- `READ_MEDIA_IMAGES`, `READ_MEDIA_VIDEO` — কন্টাক্টের ছবি এবং ক্যালকুলেটর Secret Vault-এ ছবি/ভিডিও/ডকুমেন্ট সংরক্ষণের জন্য।
- `@capacitor/filesystem` ও `@capacitor/share` — অফলাইনে A4 PDF রিপোর্ট এবং JSON ব্যাকআপ সংরক্ষণ ও শেয়ারের জন্য।
