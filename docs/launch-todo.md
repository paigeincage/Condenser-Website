# Launch To-Do — The Condenser / BuildCore

**Launch target:** 2026-04-29
**Current state:** both repos on `launch-prep` branch, all 7 waves committed, nothing pushed.

Every item below is either something **only you** can do (🧍 Paige) or something you can **hand to Claude Code** by pasting the quoted prompt (🤖 Claude).

---

## Phase 1 — This week (before launch day)

### 🧍 1. Set JWT_SECRET
- Run: `openssl rand -hex 32`
- Paste output into `C:\Users\Admin\the-condenser-experimental\server\.env` as a new line: `JWT_SECRET=<value>`
- **Time:** 2 min
- **Why only you:** the secret should stay on your machine / Railway env, not in chat

### 🤖 2. Apply schema to Railway DB + run local dev
Paste to Claude Code:
> Resume condenser. I set JWT_SECRET. Run `cd server && npx prisma db push` against the current DATABASE_URL (Railway), then spin the server and frontend dev servers. Keep them running and give me the localhost URL to test.
- **Time:** 3 min

### 🤖 3. Run the 5 QA flows with you in the loop
Paste to Claude Code:
> Walk me through the 5 launch-prep QA flows one at a time. I'll test in the browser and tell you what I see. Start with Flow 1 (signup + greeting).
- **The 5 flows:** signup → create project → SendModal manual recipient → logout/login → Founding User CTA
- **Time:** 30 min
- If anything breaks, Claude writes the patch inline and you retest.

### 🧍 4. Sign up for Beehiiv
- Go to beehiiv.com → create publication → free plan is fine
- Settings → Integrations → API → generate key
- Copy **Publication ID** (starts with `pub_`) and **API Key**
- **Time:** 10 min

### 🧍 5. Sign up for Plausible
- Go to plausible.io → add site → use your final domain (`buildcoreoperations.com`)
- Copy the **domain name** you entered (that's all you need)
- **Time:** 5 min

### 🧍 6. Buy + point the domain
- Cloudflare Registrar → `buildcoreoperations.com` (locked per memory)
- Point CNAME at Railway landing service
- Add `app.buildcoreoperations.com` CNAME at Railway app service (optional — or keep railway URL for app)
- **Time:** 20 min
- **Why only you:** DNS changes need your account

### 🧍 7. Record hero video
- 20–40 seconds, portrait or landscape, muted-autoplay friendly
- Content: you walking a lot, dictating into the app, send screen firing
- Save as `.mp4`, under 10MB if possible
- **Time:** depends on your schedule
- **Why only you:** it's your face, your jobsite

### 🧍 8. Take 4 app screenshots
- Walkthrough view (items populating)
- Send modal (trade pills + contact picked)
- Contacts page (populated list)
- Dashboard (live metrics)
- PNG or JPG, save to `C:\Users\Admin\the-condenser-landing\public\screenshots\`
- **Time:** 10 min once the app has real data in it

### 🤖 9. Wire hero video + screenshots + env vars
Once you have the assets + keys, paste to Claude Code:
> Wire these in on both launch-prep branches:
> - Hero video at `public/<filename>.mp4` — update `HERO_VIDEO_SRC` in landing App.tsx
> - Screenshots in `public/screenshots/` — mount the screenshots section between Integrations and Support
> - Add these env vars to both Railway services (landing + app):
>   - `VITE_PLAUSIBLE_DOMAIN=buildcoreoperations.com`
>   - `VITE_BEEHIIV_PUB_ID=pub_xxxxxxxx` (landing only)
>   - `VITE_BEEHIIV_API_KEY=xxxxxxxx` (landing only)
> Commit to launch-prep. Don't push yet.
- **Time:** 10 min

---

## Phase 2 — Launch day (Tuesday April 29)

### 🤖 10. Final pre-flight check
Paste to Claude Code at 6am:
> Launch day. Pull latest on both launch-prep branches, run builds, run TypeScript checks, verify no uncommitted drift. Report clean-or-not in one line each.
- **Time:** 5 min

### 🤖 11. Merge + deploy
If clean, paste:
> Merge launch-prep into master on both repos and push. Railway will auto-deploy. Monitor deploy status and tell me when both services are live. If anything fails, stop and tell me before rolling forward.
- **Time:** 10–15 min (Railway deploy ~60s each, plus your sanity check)

### 🧍 12. Live-site smoke test
- Open `buildcoreoperations.com` → does it load, does Founding User CTA work?
- Open app URL → sign up with a fresh email → does "Hey, [name]" appear?
- Open pricing section on landing → toggle monthly/annual → tiers update
- **Time:** 5 min
- **Why only you:** real browser, real eyeballs

### 🤖 13. Verify analytics + email capture are firing
Paste:
> Confirm Plausible events are firing on landing (open devtools, trigger a CTA click, confirm `plausible` call in network). Confirm a test email through Founding User form actually lands in Beehiiv. Report both.
- **Time:** 10 min

### 🧍 14. Post launch content
**Order matters** — don't dump everything at once:
- **12:01am PT (overnight before):** Submit to Product Hunt (use copy from `launch-content/product-hunt-copy.md`)
- **7am CT:** LinkedIn post (`linkedin-post.md`)
- **10am CT:** X thread (`x-thread.md`)
- **11am CT:** Reddit post #1 — r/Construction (`reddit-posts.md`)
- **Next day 10am:** Reddit post #2 — r/Contractor
- **Day after that:** Reddit post #3 — r/HomeBuilding
- **Time:** 15 min per post, plus ~2 hours monitoring replies
- **Why only you:** your accounts, your voice, your tone

### 🤖 15. (Optional) Claim old Contact rows
If you had real contacts from before Wave 5:
> Run `cd server && npx tsx src/scripts/claim-orphan-contacts.ts <my-email>` and report the count reassigned.
- **Time:** 1 min

---

## Phase 3 — Post-launch (first week)

### 🧍 16. Reply to every comment in the first 6 hours
- PH, LinkedIn, Reddit, X — all of them
- Don't ignore anyone. Don't pitch in replies. Answer the actual question.
- **Time:** scattered over day 1

### 🤖 17. Start sending cold outreach
Use templates in `launch-content/cold-outreach.md`. Paste to Claude:
> Take the Template 1 from cold-outreach.md. I want to send to [name] who I worked with at [project]. They said [specific thing]. Rewrite the template for them, keep it under 120 words, no generic phrasing.
- **Time:** 3 min per send. Send 10–30 total over launch week.

### 🤖 18. Daily founding-user check-in
For the first 7 days, paste each morning:
> Show me new signups since yesterday. For anyone who hasn't created their first project within 48 hours of signup, draft a personal check-in email I can send from my inbox.

(Note: this requires a dashboard query — if the app doesn't have that admin view yet, Claude will surface it as a blocker and we'll decide whether to build it.)

### 🤖 19. Day 7 — pull the numbers
> Query the DB: how many signups, how many completed first walkthrough, how many sent at least one punch list, median items-per-project. Report as a one-screen summary.
- Those numbers go into email #3 of the founding sequence (already drafted, Beehiiv will send automatically).

---

## When things go sideways

### Auth is broken → 🤖
> Login is returning 500. Check server logs, confirm JWT_SECRET is set in Railway env on the app service (not just local .env). If it's there, paste me the first error line from the logs.

### Deploy broken → 🤖
> Deploy failed. Show me the failing build step. Do not attempt to hotfix on master — roll back, diagnose, fix on launch-prep, re-merge.

### DB push caused a problem → 🤖
> Revert the Wave 5 schema push — drop the `user_id` columns on contacts and templates. Come up with a smaller-step migration plan before trying again.

### I hate something about the UI → 🤖
> The [specific thing] on [landing or app] feels wrong. Here's why: [your reason]. Fix it on launch-prep and show me the diff before committing.

---

## What NOT to say to Claude

- "Just push it" — I always want to see what's changing first
- "Make it look better" — give me a specific complaint, not a vibe
- "Deploy to production" — it's auto-deploy on push; always verify build passed locally first
- "Skip the QA flows" — those 5 flows are the only thing between you and a broken launch

---

**Last updated:** 2026-04-20
**Next expected update:** launch day debrief
