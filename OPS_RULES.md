# OPS RULEBOOK V1.0 — Tunnel/Relay Command Discipline
> ပြင်ပ agent က tunnel/relay သုံးပြီး server ပေါ် command run တဲ့အခါ စည်းမျဉ်း — ဘယ် task မှ မကျွတစေရ

## THE RULE — IF / ELSE
- **IF tool ရတယ်** → direct run (အကောင်းဆုံး path)
- **ELSE tool ပျက်တယ်** → ချက်ချင်း Task agent / sub-agent ဆီ delegate — **retry ထက် delegate ဦးစားပေး၊ task မရပ်စေရ**

## COMMAND DISCIPLINE ၅ ခု
1. **Non-interactive သာ** — prompt မေးနိုင်တာ တား (`-y`, `--no-input`, `-o BatchMode` စသဖြင့်)
2. **Timeout တပ်ပြီး run** — tool ထာဝရ မစောင့်ရ
3. **ကြာရှည် task = background** — `nohup <cmd> > run.log 2>&1 &` ချက်ချင်း ပြန်လာမယ်
4. **Output ချုံ့ပြီး ပြန်ယူ** — giant dump မပို့ရ (`| tail -30`)
5. **Log ဖိုင် ချန်ထား** — ရလဒ်အားလုံး ဖိုင်ထဲ — server ပေါ်မှာ ကျန်ရစ် (အထောက်အထား)

## PROVEN PATTERNS (ကျွန်တော်တို့ စမ်းသပ်ပြီး)
- Relay script: **Write tool** နဲ့ ကြီးကြီးရေး → **bash တိုတို** နဲ့ run: `bash x.sh > x.out 2>&1; tail -N x.out`
- paramiko တစ်ကြိမ် connect → exec_command → output ဖတ်
- 403 intermittent → တစ်ကြိမ် retry မဟုတ်၊ **၆ ခါအထိ retry သို့ fresh agent**
- Giant heredoc ကို bash tool payload ထဲ မထည့် — ဖိုင်အရင်ရေး

## 403 CASE CHECKLIST
1. Test အရင် — ရောဂါရှာ (တိုတို run)
2. Command ခွဲစစ် — `curl -I https://github.com`
3. Log ဖတ် — `cf_access.log`
4. Fix — network allow / `curl -k` / script ပြင် / timeout မြှင့် / allowedCommands
5. အနှစ်ချုပ် — script မှားတာ မဟုတ်၊ policy + ကန့်သတ်ချက် — **download နဲ့ sudo ရှောင်၊ တိုတိုခွဲ run**

## MONITORING & RECOVERY
- alive: `ps aux | grep <task>` · progress: `tail -30 run.log` · session: `tmux ls`
- Tool ပြန်ရလာ → log ကနေ ဆက်ယူ၊ delegate ရလဒ် အတည်ပြု၊ ဘာကြောင့်ပျက်လဲ မှတ်စုချန် (worklog.md)
- **အားလုံး server မှာ ကျန်နေရမယ် — log file = အမြဲတမ်း အထောက်အထား**
