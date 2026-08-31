# ⚑ ဉာဏ်လင်း AI — အမြဲတမ်း GOAL (Permanent Mission Record)

> ဘယ် AI၊ ဘယ် session၊ ဘယ်အချိန်ကိုမဆို ဖွင့်ကြည့်နိုင်ရမယ်။
> ဒီဖိုင်က **ကတိ** ဖြစ်ပါတယ်။ ပြင်လို့မရဘဲ လိုက်နာရမယ့် အခြေခံစည်းမျဉ်း။

## ၁။ အမြဲတမ်း ကတိစကား (Owner's Permanent Declaration)
> **"ဉာဏ်လင်း AI Assistant မဖြစ်မခြင်း — ဒါက အမြဲတမ်း ငါ့ရဲ့ Goal"**
- ဉာဏ်လင်းက project တစ်ခု မဟုတ်ဘူး — **အမြဲတမ်း ကတိတစ်ခု**။
- ကိုယ်ပိုင် AI assistant တကယ်ဖြစ်လာတဲ့အထိ ဆက်သွားမယ်။
- အချိန်ယူရင်ယူပါစေ၊ အဆင့်ဆင့် တည်ဆောက်သွားမယ်။
- အောင်မြင်မှုကို model ကြီးမားမှုနဲ့ မတိုင်းဘူး — မြန်မာလို သဘာဝကျပြီး
  စက်အရင်းအမြစ်နည်းနည်းနဲ့ လက်တွေ့သုံးနိုင်တာနဲ့ တိုင်းမယ်။

## ၂။ လိုက်နာရမယ့် စည်းမျဉ်း ၅ ခု (Core Rules — ဘယ်တော့မှ မလျှော့ရ)
| # | စည်းမျဉ်း | အနက်အဓိပ္ပာယ် |
|---|-----------|----------------|
| 1 | **Core code = MMC** | ဉာဏ်လင်းရဲ့ core code အားလုံးကို MMC Myanmar Programming Language နဲ့သာ ရေးရမယ်။ MMC → C compiler → machine code။ |
| 2 | **No External Brain** | ရှိပြီးသား model / brain / pretrained weights / API ကို **လုံးဝ အားမကိုးဘူး**။ လုံးဝမဖြစ်နိုင်တော့မှသာ ပြန်စဉ်းစားမယ် (အခုအချိန်ထက်တိုင်း — မဖြစ်နိုင်သေးဘူး ဆိုတာ သက်သေပြပြီးသား)။ |
| 3 | **C Compiler = Run** | C compiler ရှိတဲ့ မည်သည့် device မဆို run နိုင်ရမယ် — PC၊ Raspberry Pi၊ စက်အဟောင်းများပါ။ |
| 4 | **Python = Training Only** | Python က dataset စုဆောင်း၊ tokenizer ဖန်တီး၊ training အတွက်သာ။ Product ထဲမှာ Python dependency = **0** — MMC runtime က weights တိုက်ရိုက်ဖတ်မယ်။ |
| 5 | **Local Training First — မလောက်မှ Free Cloud** | antiX Linux server မှာ အရင်စပြီး ဘယ်လောက်ထိရောက်မလဲ ပြမယ်။ မလောက်တော့မှ **free cloud (Kaggle / Colab)** ကိုသာ သုံးမယ်။ Paid API / paid GPU လုံးဝ မသုံးဘူး။ |

Rule 5 လက်ရှိအခြေအနေ (2026-08-30 မှတ်တမ်း): Local 6GB GPU နဲ့ from-scratch training က
data + compute အရ မလောက်တော့တာ သက်သေပြပြီး (v1–v6 စမ်းသပ်မှုများ၊ val_loss 1.23-1.34 ကန့်သတ်ချက်) —
Rule 5 ရဲ့ "မလောက်တော့မှ free cloud" အဆင့် တရားဝင် ဖွင့်လိုက်ပြီ။ ဒါက စည်းမျဉ်းဖောက်တာ မဟုတ်ဘူး —
စည်းမျဉ်းအတိုင်း လိုက်နာတာပါ။

## ၃။ Roadmap — Phase သုံးခု
1. **◌ Text LLM** — မြန်မာလို နားလည်ပြီး ပြန်ပြောနိုင်တဲ့ ကိုယ်ပိုင် LLM
   - Tokenizer (မြန်မာစာအတွက် ကိုယ်ပိုင်နည်းနဲ့ ခွဲခြမ်း) → Architecture
     (low-end လျော်ညီ transformer) → Pretrain (မြန်မာ + English corpus) →
     Fine-tune (assistant ပုံစံချ) → **MMC Runtime** (C compiler ရှိရင် run)
2. **◖ Voice AI — NyanLin V11** — Local TTS/STT (cloud voice API လုံးဝ မလို)၊
   Text LLM နဲ့ တွဲဖက်ပြီး အသံနဲ့ စကားပြောနိုင်မယ်
3. **♪ Music Generation** — မြန်မာ melody ခံစားမှုနဲ့ Lyrics/Melody/Vocal local generation

## ၄။ Data အကြောင်း အခြေခံသဘောတူညီမှု (Raw Text ≠ Brain)
- စည်းမျဉ်း #2 က တားမြစ်ထားတာက **model brain (pretrained weights, API)** ပါ။
- **Raw စာသား (public open web corpus / Wikipedia dump / news စာမျက်နှာများ)**
  က ကုန်ကြမ်းပစ္စည်းသက်သက် — brain မဟုတ်ဘူး။ မည်သည့် model ရဲ့ အသိဉာဏ်မှ မပါဘူး။
- Tokenizer က **ကိုယ်ပိုင်** တည်ဆောက်မယ်၊ Data processing က **ကိုယ့်ပိုင် pipeline** နဲ့သာ။
- Owner သဘောမတူရင် ရပ်တန့်ပြီး ပြန်ဆွေးနွေးမယ်။

## ၅။ အောင်မြင်မှု သတ်မှတ်ချက် (Success Criteria)
1. ဉာဏ်လင်းက မြန်မာစာကို စာလုံးပေါင်းမှားဘဲ၊ အဓိပ္ပာယ်ရှိရှိ **ရေးတတ်မယ်**
2. ဉာဏ်လင်းက မြန်မာလို မေးခွန်း နားလည်ပြီး **သဘာဝကျကျ ပြန်ဖြေတတ်မယ်**
3. MMC runtime နဲ့ C compiler ရှိတဲ့ စက်အဟောင်းမှာပါ **run နိုင်မယ်**
4. ဒီလမ်းစဉ်တစ်ခုလုံးမှာ External Brain အားကိုးမှု **0** ရှိနေမယ်

## ၆။ မှတ်တမ်း — လမ်းကြောင်းဆုံးဖြတ်ချက်များ (Decision Log)
| Version | လမ်းကြောင်း | ရလဒ် |
|---------|------------|------|
| v1–v6 | Local GPU နဲ့ from-scratch | Train လုပ်နိုင်တာ သက်သေပြပြီး — ဒါပေမယ့် data/compute နည်းလွန်းလို့ မြန်မာစာ မရေးတတ်နိုင် (val_loss ~1.23–1.34 အနိမ့်ကန့်သတ်ချက်) |
| v7 | Pretrained base + QLoRA | **Owner က ငြင်းပယ်** — Rule #2 နဲ့ ဆန့်ကျင်။ မလုပ်တော့ဘူး။ |
| **v8 (လက်ရှိ)** | **From-scratch + Free Cloud (Kaggle/Colab) + ကိုယ်ပိုင် pipeline** | Rule #2 ✅ Rule #5 ✅ — အစကနေ ကိုယ်တိုင်၊ local မလောက်တော့ free cloud၊ checkpoint အမြဲ resume ရမယ့် design |

**GOAL status: ACTIVE — ဉာဏ်လင်း မြန်မာစာရေးတတ်တဲ့အထိ ရပ်တန့်ခွင့်မရှိ။**
