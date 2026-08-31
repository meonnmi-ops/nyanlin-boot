# ⚠️ SELF_CHECK — ကိုယ့်ကိုယ်ကိုယ် သတိပေးစနစ် (v1)
> Owner ညွှန်ကြားချက် (2026-08-31): data များလာလို့ လမ်းလွဲ/ရှုပ်မိမယ်လို့ ကြိုသတိပေးထားတာ။
> **Session တိုင်း အရင်ဆုံး ဒီဖိုင်ကို ဖတ်။ ဒီဖိုင်က တိုတိုရမယ် — ရှည်လာရင် ချုံ့။**

## 🧭 လုပ်ခင်း မေးရမယ့် ၃ ခု (တစ်ခါမှ မကျော်ရ)
1. **ဘယ်စက်မှာ လုပ်နေတာလဲ?** — sandbox (`/tmp`=canonical, `/home`=mirror) vs antix1 (relay တစ်ဆင့်) vs Kaggle — **ရောမှားရင် အဆုံးသတ်**
2. **လက်ရှိ task က GOAL chain နဲ့ ချိတ်ထားလား?** — chain: 30,517 → bot အစားထိုး → MMC runtime → Voice V11 → Music။ Side-quest (Godot လိုမျိုး) ဆွဲမိရင် **user ခွင့်ပြုချက် မရှိဘဲ မစောင့်ဆိုင်းသင့်**
3. **နောက်ဆုံး verified fact က ဘာလဲ?** — worklog tail ဖတ်ပြီးမှ ဆက်။ **ကိုယ့်ဉာဏ်အမှတ်တရ အားမကိုးရ** (stale ဖြစ်နိုင်တယ်)

## 🚫 ပြီးခဲ့တဲ့ အမှားများ — မထပ်ရ
| အမှား | တားဆီးနည်း |
|---|---|
| Side-quest နစ်မြုပ် (Godot village) | side-quest စခင်းမှာ user ကို အချိန်ကန့် ကြိုပြော |
| Filter trigger word → bash ပျက် (Task 33) | CF tunnel command phrase မရေးရ; ဖိုင်ကြီး dump မလုပ်ရ — grep/ခွဲဖတ် |
| Stale zip/state ယူဆမိုး (Task 29) | deliverable အမည်အသစ် (v2 style); ယူဆချက်တိုင်း စစ် |
| 403 → retry loop (OPS_RULES) | **delegate ဦးစားပေး၊ retry အများကြီး မလုပ်ရ** |
| Canned reply (user မကြိုက်) | အခြေအနေအလိုက် ဖြေ; အတိုချုပ် ပုံစံတူထပ် မနေရ |
| /home vs /tmp ရောမိ | Write tool = /home သာ → `cp` sync /tmp → diff အတည်ပြု |
| Inline long script | `scripts/` ထဲ save → run (Script Persistence) |
| အကုန်ဖတ်ချင်စိတ် (296GB/363K ဖိုင်!) | **targeted query ဘဲ** — du/ls/grep → ရလဒ် အနှစ်ချုပ် infra-study.md |
| Tool သေပြီး recovery loop (Task 47 — owner သတိပေး) | transport သေရင် **ချက်ချင်း path ပြောင်း**: delegate → မရရင် ရပ်ပြီး အစီရင်ခံ — broken tool ကို ထပ်ခါထပ်ခါ မခေါ်ရ |
| လျှို့ဝှက်ချက်များ မမျှော်လင့်ထားတဲ့ commit (Task 49 — GitHub က push ပယ်ချမှုနဲ့ ကယ်တင်ခဲ့) | git init မလုပ်ခင် `<dir>/.git` **တိုက်ရိုက်စစ်** (`git rev-parse` က parent ကို တွေ့မိနိုင်); push protection ပယ်ချရင် **token ထွက်နေပြီလို့ သတ်မှတ်ပြီး အရင်ရှင်းပြီးမှ ထပ်push**; disable လုံးဝ မလုပ်ရ |

## 😵 "ရှုပ်နေပြီ" လက္ခဏာ — တစ်ခုမြင်ရင် STOP
- ခေါင်းစဉ် ၃ ခုကြား ခုန်ပြော / မေးခွန်းနဲ့ မထိတဲ့ အဖြေ
- တစ်ပြိုင်တည်း ဖိုင် ၂+ ခု ပြင် / path မှားသွား / မှားပြင်ပြီး ပြန်ရှာ
- "အရင်က ဘယ်လိုလုပ်ခဲ့တာလဲ" ဆိုတဲ့ မသေချာမှု ဆက်တိုက် ၂ ခါ
→ **STOP → GOAL.md + STATE.md ပြန်ဖတ် → worklog မှာ "ယခုစက်+ယခုtask" ရေးချ → တစ်ဆင့်တိုင်း ဆက်**

## ✅ လုပ်ငန်းတာဝန် တစ်ခုစီ ပြီးရင်
worklog append → mirror sync → user ကို မြန်မာလို တိုတို အစီရင်ခံစာ။
**မှတ်ချက် - အလုပ်ဖြစ်တာ/သင်ခန်းစာသာ မှတ် - အမှိုက်/ရှုံးနိုင်ခြေရှိသော အရာများ မမှတ်ရ (owner ညွှန်ကြားချက် Task 34)**
