# CLAUDE.md — ဉာဏ်လင်း AI Project Rule Block (v1.0 · 2026-09-01)
> ဘယ် AI၊ ဘယ် session၊ ဘယ်အချိန်ကိုမဆို **အရင်ဆုံး ဖတ်ရမယ့် compact rule block**။
> Source: ai--goal.pptx mission deck (owner) + GOAL.md — အသေးစိတ် = memory chain ကို ဖတ်။
> ဒီဖိုင်ထဲ မရှိတဲ့အရာ = ကိုယ့်ဉာဏ်အမှတ်တရ အားမကိုးဘူး — chain ဖိုင်တွေကို မေး။

## ၁။ MISSION — တစ်ကြိမ်ဖတ်ပြီး မမေ့ရ
- ဉာဏ်လင်း = **MMC Myanmar Programming Language** နဲ့ ရေးထားတဲ့ လုံးဝ ကိုယ်ပိုင် AI LLM။
- **"ဉာဏ်လင်း AI Assistant မဖြစ်မခြင်း — ဒါက အမြဲတမ်း ငါ့ရဲ့ Goal"** (owner permanent declaration)။
- Tagline: From Scratch · No External Brain · Local First · Low-End First · **100% MMC Core · 0 External API**။
- လက်ရှိ chain: **step 30,517 🎯 → bot weights အစားထိုး (final_deploy.sh) → MMC runtime → Fine-tune → Voice V11 → Music**။

## ၂။ စည်းမျဉ်း ၅ ခု — ဘယ်တော့မှ မလျှော့ရ
| # | Rule | အဓိပ္ပာယ် |
|---|------|-----------|
| 1 | **Core code = MMC** | Core အားလုံး MMC နဲ့သာ — MMC → C → machine code။ |
| 2 | **No External Brain** | ပြင်ပ model / brain / pretrained weights / API အားလုံး တား။ |
| 3 | **C Compiler = Run** | C compiler ရှိတဲ့ စက်တိုင်း run ရမယ် — စက်အဟောင်းပါ။ |
| 4 | **Python = Training Only** | Product ထဲ Python dependency = **0** — MMC runtime က weights တိုက်ရိုက်ဖတ်။ |
| 5 | **Local First → Free Cloud** | Local အရင်၊ မလောက်မှ Kaggle/Colab free — **paid API/GPU = လုံးဝတား**။ |

## ၃။ SESSION BOOTSTRAP — session တိုင်း အစမှာ verify (မကျော်ရ)
1. **Memory ဖတ် (အစဉ်လိုက်):** SELF_CHECK.md → GOAL.md → STATE.md → worklog tail (၂ task) → infra-study.md → (antiX အလုပ်ဆို ANTIX-LIB.md)။
2. **မေးရမယ့် ၃ ခု:** ဘယ်စက်မှာလဲ? GOAL chain နဲ့ ချိတ်ထားလား? နောက်ဆုံး verified fact က ဘာလဲ?
3. **Verify မပြီးခင် ဘာအလုပ်မှ မစရ။** ရှုပ်နေရင် STOP → GOAL.md + STATE.md ပြန်ဖတ်။
4. **အလုပ်တိုင်း ပြီးရင်:** worklog append → /tmp mirror sync → (memory ပြောင်းရင် GitHub push) → owner ကို မြန်မာလို တိုတို အစီရင်ခံ။

## ၄။ OPS DISCIPLINE — command run တိုင်း
- Non-interactive + timeout တပ် · ကြာရှည် task = `nohup … > run.log 2>&1 &` · output ချုံ့ပြီး ပြန်ယူ · log ဖိုင် ချန်။
- Long script = `scripts/` ထဲ save ပြီးမှ run (inline heredoc ကြီးကြီး တား)။
- Tool ပျက် → retry loop မလုပ်ဘဲ **delegate ဦးစားပေး** (OPS_RULES.md)။
- Sandbox: Write = /home/z/my-project · canonical mirror = /tmp/my-project — `cp` sync + diff အတည်။
- ဖိုင်ကြီး dump မပို့ရ — grep/အပိုင်းခွဲ။ zip ပြန်ချရင် နာမည်အသစ် (v2 style)။

## ၅။ GOVERNANCE — ဆုံးဖြတ်ချက်အဆင့် (owner ညွှန်ကြားချက် 2026-08-31)
- **Agent က လက်ရှိ ဦးဆောင်ဆုံးဖြတ်သူ** — owner = final goal keeper (chain လမ်းမှားမိုးသူ)။
- Side-quest ဆွဲမယ်ဆို အချိန်ကန့် ကြိုပြော — **GOAL chain က အမြဲ ဦးစားပေး**။
- Owner ရဲ့ မူလ ၃ ညွှန်ကြားချက် အမြဲတက်: data သန့် · canned reply မဖြေ · အလုပ်ဖြစ်တာသာ မှတ်။
