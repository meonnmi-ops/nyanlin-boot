# STATE — နောက်ဆုံး update: 2026-09-01 (Yangon) — memory restore ပြီး (Task 48)
> Session restart ပြန်ဝင်ချင်း **ဖတ်ရမယ့်အစဉ်: CLAUDE.md (rule block) → SELF_CHECK.md → GOAL.md → ဒီဖိုင် → worklog tail (၂ task) → infra-study.md → antiX လုပ်ရမယ်ဆို ANTIX-LIB.md**
> မှတ်ချက်: ဒီဖိုင်က သန့်သန့်ရှင်းရှင်း အလုပ်ဖြစ်တာတွေဘဲ — မလိုက်ဘူးတဲ့ အရာများ မထည့်ထား (owner ညွှန်ကြားချက်)။

## WHO / HOW TO TALK
- ကျွန်တော် = ဉာဏ်လင်း developer လက်တွဲဖော်။ **အားလုံး မြန်မာလို၊ တိုတို၊ command block အဓိက၊ ထပ်ခါထပ်ခါ မပြော။**
- မင်း (user): ကုဒ် မရေးတတ်ပေမယ့် architecture နားလည်တယ်၊ canned reply မြင်ရင် မကျေမနပ်။
- User နှစ်လကြာ သုံးနေပြီ — system အကုန်သိ။ ကျွန်တော်က model အသစ်လို့ သူ့ညွှန်ကြားချက်တွေ အမြဲ လေးစားစွာ လိုက်နာ။

## INFRA MAP
| နေရာ | အချက်အလက် |
|---|---|
| sandbox | /home/z/my-project/ (mirror) + /tmp/my-project/ (canonical) — memory chain RESTORED 2026-09-01 (Task 48; GitHub ကနေ ပြန်ရ) — GOAL.md / OPS_RULES.md / infra-study.md / worklog.md / antix-lib/ / scripts/creds/ |
| antiX (antix1) | i7-9750H 12T / 15G RAM / **GTX 1660 Ti 6GB (torch 2.6.0+cu124 CUDA ✅, 3.2 TFLOPS)** / NVMe 114G လွတ် / sudo pw လို / home=/home/meonnmi-ops — **Library: ANTIX-LIB.md + laptop ~/AGENT-INDEX.md** |
| **MMC (Rule #1)** | **FULL CHAIN PROVEN 2026-09-01**: weights→GGUF→engine_gpt2 (မြန်မာ syntax→C→gcc) 24 tokens == torch ground truth တိတိကျ ✅ (dress rehearsal, step-16k real weights) — 30,517 ရောက်ရင် `bash ~/rehearsal/final_deploy.sh <ckpt>` one-command |
| antiX bot | nyanlin-bot-antix/ ထဲ nyanlin_bot.pt = **step 16,000** (best_val 3.3151, 393.8MB stripped) — bot အလုပ်လုပ်နေဆဲ |
| Kaggle | v11 kernel RUNNING: step 16,000 → ~28,700 (ETA ~05:45 MMT Sep 1) → နောက်ဆုံး round → **30,517 🎯** |
| creds | scripts/creds/: hf_token, github_token, **kaggle_token (KGAT) + kaggle.json (အသစ် Sep 1 — Task 49-c 401/403 block ဖြေလျှောက်ပြီး, status+output endpoint 200 verified)**, cloudflare_r2.env, gh_askpass.sh |
| CF relay | nyanlin-relay v6 (D1) + nyanlin-chat-proxy workers — အသေးစိတ် infra-study.md; laptop client ONLINE (pid 8555 single owner — duplicate 25848 closed, Task 48-b); sandbox relay tool = antix-lib/nyanlin_relay.py v2.0 (rebuilt, E2E tested) |
| R2 | account မှာ မဖွင့်ရသေး — Dashboard Enable R2 လုပ်ရမယ် (keypair သိမ်းပြီး) |
| HF/GitHub | hf.co/Meonnmi0ps (models 2 + dataset 1) / github meonnmi-ops (private 37) — ဉာဏ်လင်း GPT weights မတင်ရသေး |
| **BOOT system** | **public repo meonnmi-ops/nyanlin-boot** (Task 49) — trigger: `စစ်ပါ nyanlin-boot` (Tier-1: memory recall) / `စစ်ပါ nyanlin-boot <relay-secret>` (Tier-2: +relay ops) — BOOT.md အစဉ်အတိုင်းလိုက်; creds ကို laptop `~/soul-service/secrets/` (600) မှာ ရယူ; task တိုင်းပြီးရင် ဒီ repo + private backup နှစ်ခုလုံး push |

## LIVE RIGHT NOW
- **Kaggle v11 RUNNING** (03:24 MMT check: status=running, files=[] — ETA ~05:45 MMT unchanged) — ပြီးရင် user "စစ်ပါ" လို့ပြောမယ်; monitoring RESTORED (kaggle token အသစ် Task 49-d)
- **BOOT system LIVE** (Task 49, ~04:30 MMT): public nyanlin-boot repo + laptop secrets store စမ်းသပ်ပြီး (E2E ✓) — owner က session အသစ်မှာ trigger line တစ်ကြောင်းနဲ့ recall လုပ်နိုင်ပြီ
- အစီအစဉ်: v11 output ဆွဲ → train_log.csv ဖတ် → နောက်ဆုံး round chain (~1.7h) → **step 30,517 = training goal ပြီး** → strip → bot weights အစားထိုး

## NEXT STEPS (အစဉ်လိုက်)
1. 30,517 ပြီး → weights download → `bash ~/rehearsal/final_deploy.sh <ckpt>` (convert+test+swap+restart auto)
2. engine chat quality စစ် (chain proven 2026-09-01 — quality က training ရဲ့အလုပ်)
3. Optional publish: HF repo / GitHub backup / S3 archive (user အလိုကျ)
4. နောက်တော့: Fine-tune (assistant ပုံစံ) → MMC/C runtime (nyanlin_engine.c) → Voice V11 → Music

## LESSONS (ပြန်မှားမိရန် — အလုပ်ဖြစ်စေတဲ့ သင်ခန်းစာတွေဘဲ)
- ရှည်ရှည် job = **nohup background + log file** အမြဲ (cell interrupt = training သေ)
- T4: batch 12 OOM → batch 8 + `PYTORCH_CUDA_ALLOC_CONF=expandable_segments:True`
- Sandbox 403 ပျက် → **retry ထက် Task agent delegate ဦးစားပေး၊ ၆ ခါအထိ retry** — OPS_RULES.md
- **CF tunnel ဟုခေါ်သော daemon ရဲ့ တရားဝင် command phrase ကို payload/chat ထဲ လုံးဝမရေးရ** — filter trigger → bash ပျက် (Task 33); ဖိုင် dump မလုပ်ခင် grep/အပိုင်းခွဲ
- zip ပြန်ချရင် **နာမည်အသစ် (v2 style)** — stale download ရှုပ်ထွေးမှု ရှောင်
- Edit tool: /home/z သာရေးနိုင်၊ /tmp ကို cp sync; tab→space normalize ဖြစ်နိုင် — ရေးပြီးရင် စစ်
- **git init မလုပ်ခင် `<dir>/.git` တည်ရှိမှု တိုက်ရိုက်စစ်** — `git rev-parse` က parent repo (platform checkpoint repo) ကို တွေ့မိနိုင် → creds commit မိနိုင် (Task 49 incident); GitHub push protection က နောက်ဆုံးမြို့်တံတိုင်း — ဘယ်တော့မှ disable မလုပ်ရ

## PARKED (user ဆုံးဖြတ်ချက်အရ ခဏရပ်)
- Godot village_bridge — ဖိုင်တွေ အားလုံး ပြင်ပြီးသား (download/nyanlin-village-hotfix-v2.zip) — user ပြန်ခေါ်မှ ဆက်
