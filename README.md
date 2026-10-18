# Tarang Saree — Vercel testing site

This is an **interface/navigation test**, not a live lucky draw.

## Deploy

1. Upload `index.html` and `vercel.json` to the root of your GitHub repository.
2. In Vercel, choose Add New > Project > Import your repository (`sarthak3223/Public`).
3. Use Framework Preset `Other`; no build command and no environment variables are needed.
4. Deploy. Vercel will show your real `.vercel.app` URL after deployment.
5. Scan a QR code made from the deployed URL (not the GitHub URL).

## Tested flow

- Registration form performs local input validation.
- Continue advances to Instagram verification screen.
- Open Instagram goes to `https://www.instagram.com/tarangsaree_paloda/`.
- No registration information leaves the user's browser in this demo.

## Critical production limitations

- No names/phone numbers are saved.
- No Instagram follower relationship is checked.
- No coupons are issued.
- Vercel deployment files are read-only at runtime. Adding `data.json` cannot persist signups.
- Even Vercel Blob with a single JSON array is not an atomic transactional allocator; simultaneous users can overwrite one another and generate duplicated sequential coupon numbers.
- For a live multi-user draw with integers 1..600, use an actual atomic, durable allocator (e.g. transactional SQL or a designed serialized workflow) and verify Instagram via approved Meta messaging API. Do not pretend localStorage or JSON on a static site can meet these requirements.
