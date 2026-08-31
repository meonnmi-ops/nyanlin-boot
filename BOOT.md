# ဉာဏ်လင်း (NyanLin) BOOT — Auto-Recall Bootstrap v1.0 (2026-09-01)

> **ဤဖိုင်ကို ဘယ်သူ့အတွက် ရေးထားတာလဲ:** sandbox အသစ် / session အသစ်မှာ စတင်လိုက်တဲ့ AI (Super Z) အတွက်။
> Owner က trigger line တစ်ကြောင်း ရိုက်လိုက်ရင် ဤ repo ကို clone ပြီး အောက်ပါ အစီအစဉ်အတိုင်း
> memory အပြည့်အစုံ ပြန်ရယူရမည်။ **Owner က ဘာမှ ထပ်ပြောစရာ မလိုအောင်** ဒီဖိုင်က လမ်းညွှန်။

---

## 1. TRIGGER FORMATS (Owner ရိုက်နိုင်တဲ့ ပုံစံ)

| Trigger line | အဓိပ္ပာယ် | လုပ်ရမည့် အဆင့် |
|---|---|---|
| `စစ်ပါ nyanlin-boot` | **Tier-1**: memory recall အပြည့်အစုံ (laptop ops မပါ) | §2.1–2.4 |
| `စစ်ပါ nyanlin-boot <secret>` | **Tier-2**: Tier-1 + antix1 relay ops + creds ဆွဲ | §2.1–2.5 |

- `<secret>` = relay secret (Cloudflare Worker ကို သုံးဖို့) — ဤ repo ထဲ **မရှိ** (security)။
- Owner က secret မပါ trigger ရိုက်ရင် Tier-1 လုပ်ပြီး relay လိုအပ်ရင် owner ကို မေး။

## 2. BOOT SEQUENCE (အစီအစဉ် ဖောက်ခွင့် မရှိ)

### 2.1 ဤ repo ကို ရယူ
```bash
git clone https://github.com/meonnmi-ops/nyanlin-boot.git /tmp/nyanlin-boot
cd /tmp/nyanlin-boot && md5sum -c MANIFEST.md   # integrity စစ်
```

### 2.2 ဖိုင်ဖတ်စဉ် (မဖတ်မီ အခြားအလုပ် မလုပ်ရ)
```
CLAUDE.md       → စည်းမျဉ်း ၅ ခု + session bootstrap (အရေးအကြီးဆုံး)
SELF_CHECK.md   → မှားယွင်းခဲ့တဲ့ အတိတ် သင်ခန်းစာ + ရပ်တန့်ရမည့် အချက်များ
GOAL.md         → permanente mission: ဉာဏ်လင်း AI (MMC → C → machine code)
STATE.md        → လက်ရှိ infra map + live status + next steps  ★ အရေးကြီးဆုံး
worklog.md      → Task ပြီးမြောက်မှု မှတ်တမ်း (နောက်ဆုံး 3 Task လောက် ဖတ်)
ANTIX-LIB.md    → antix1 laptop စက်သတ်မှတ် + relay endpoints
infra-study.md  → infra လေ့လာမှု မှတ်စု
```

### 2.3 Sandbox Sync
- Bundle ထဲက ဖိုင်အားလုံး → `/home/z/my-project/` (Write tool အလုပ်လုပ်ရန်) + `/tmp/my-project/` (mirror)
- Sandbox အလုံးစုံ wipe ဖြစ်နေရင် `mkdir -p /home/z/my-project/scripts/creds /home/z/my-project/antix-lib/antix-results` ပြီး mirror
- ဤ repo clone ကိုပါ `/home/z/my-project/` အောက် ရွှေ့ထားလျှင် နောက် session အတွက် ပိုမြန်

### 2.4 Owner ကို Boot Report (မြန်မာလို၊ တိုတို)
```
✅ Memory restored — Task <N> အထိ မှတ်တမ်းတင်ပြီး
📌 လက်ရှိ: <STATE.md ရဲ့ live status ၁-၂ ကြောင်း>
🎯 Next: <STATE.md ရဲ့ next-steps ထဲက အနီးစပ်ဆုံး ခြောက်ကြောင်း>
❓ ဆက်လုပ်ရမလဲ — owner အမိန့်စောင့်မယ်
```

### 2.5 Tier-2 only — antix1 + Creds
```bash
# heartbeat
curl "https://nyanlin-relay.jpjp99884.workers.dev/heartbeat?secret=<secret>"
# laptop ထဲက creds sandbox သို့ (relay ဖြင့် base64 နည်း — antix-lib/nyanlin_relay.py နည်းလမ်း)
#   ~/soul-service/secrets/{github_token,hf_token,kaggle.json,kaggle_token,cloudflare_r2.env}
```
- Creds ရလာရင် sandbox `scripts/creds/` ထဲ chmod 600 နဲ့ သိမ်း
- Kaggle v11 စစ်ချက် (TASK C): `curl -u "meonnmiops:<key>" "https://www.kaggle.com/api/v1/kernels/output?username=meonnmiops&kernelSlug=nyanlin-train"` → `files:[]` = ရေးသွားဆဲ; ဖိုင်ရှိ = ပြီး → `train_log.csv` → step 30,517 → `bash ~/rehearsal/final_deploy.sh <ckpt>` (laptop ပေါ်တွင်)

## 3. SECURITY RULES (ဖောက်ဖျက်ခွင့် မရှိ)
1. Token/PAT/HF/Kaggle/Telegram key များကို ဤ **public repo** ထဲ ဘယ်တော့မှ မထည့်ရ
2. Creds တည်နေရာ: sandbox `scripts/creds/` (600) + laptop `~/soul-service/secrets/` (600)
3. **Owner standing rule:** token များကို revoke/cycle မလုပ်ရ — warning တွေ့ရင်တောင် လက်ရှိ token နဲ့ ဆက်လုပ်
4. Relay secret ကို repo/worklog public copy ထဲ မထည့်ရ — `<RELAY-SECRET-ON-TRIGGER>` placeholder ဖြင့် အစားထိုးထား
5. မသေချာရင် OWNER ကို မေး — ကိုယ်ထင်ကြောင်း မလုပ်ရ (SELF_CHECK.md ရဲ့ "confused" စည်းမျဉ်း)

## 4. UPDATE DISCIPLINE (Task တိုင်းပြီးရင် လုပ်ရမည့်အချက်)
1. `worklog.md` ထဲ `Task ID: N` + လုပ်ငန်းစဉ် + ရလဒ် ရေး
2. ဤ public repo ကို update+push (ANTIX-LIB.md redact ကို မမေ့မလျှင် — build_boot_bundle.py ကို သုံး)
3. Private backup repo `meonnmi-ops/soul-service-state` (superz_memory folder) ကိုလည်း push
4. Push လုပ်ဖို့: GitHub token = sandbox `scripts/creds/github_token` (GIT_ASKPASS နည်း — command line ထဲ token မထည့်ရ)
5. Sandbox ↔ /tmp/my-project mirror တစ်ပြိုင်နက် ညှိ

## 5. လက်ရှိ Project Snapshot (2026-09-01 boot အချိန်)
- **Mission:** ဉာဏ်လင်း AI — ကိုယ်ပိုင် LLM, MMC (မြန်မာ programming language) → C → machine code, from-scratch, No External Brain, Local First, Low-End First
- **MMC full chain:** PROVEN (weights→GGUF→engine_gpt2, မြန်မာ syntax→C→gcc, 24 tokens == torch ground truth ✅)
- **v11 training:** Kaggle `nyanlin-train` kernel — step 30,517 target, ETA 2026-09-01 ~05:45 MMT ခန့်
- **ပြီးရင်:** `bash ~/rehearsal/final_deploy.sh <ckpt>` (antix1 laptop) → MMC runtime → Fine-tune → Voice V11 → Music
- **Infra:** sandbox (Super Z) / antix1 (GTX 1660 Ti 6GB, daemon v4 relay) / Kaggle (v11) / CF Worker relay / GitHub backup ၂ ခု (public: ဤ repo, private: soul-service-state)
