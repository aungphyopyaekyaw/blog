---
layout: post
title:  "DNSSEC အပိုင်း ၁"
date:   2019-10-26 18:33:09 +0630
categories: WebTech
---

![dnssec part 1](/assets/img/2019-oct/fig3.png){:class="img-responsive"}

DNSSEC အကြောင်းရေးမယ်ဆိုဆိုတော့ ကျွန်တော်အပိုင်း ၁၊ ၂ ခွဲထားလိုက်တယ်။ အပိုင်း ၁ မှာတော့ ယေဘူယျအကြောင်းလောက်ပဲထည့်ပြီး ၂ မှာတော့ technical အပိုင်းလေးထည့်သွားမယ်ဗျာ။ အရင်ဆုံး DNSSEC ဆိုတာ မရေးခင် DNS ဆိုတာပြောရအောင်ဗျာ.. DNS ဆိုတာကတော့ domain name system လို့ခေါ်တဲ့ IP address တွေကို လူတွေမှတ်မိလွယ်အောင် နာမည်တွေပြောင်းပေးတဲ့ system ပေ့ါဗျာ။ ဥပမာ www.google.com ကိုခေါ်လိုက်ရင် သူနဲ့သက်ဆိုင်တဲ့ 172.217.194.100 ဆိုတဲ့ IP ကိုသွားတယ် ပြောရရင် google ရဲ့ web server က အဲ့ဒီ IP မှာရှိတာပေါ့.. အဲ့လိုတွေပြောင်းပေးတဲ့ system ကို domain name system (DNS) လို့ခေါ်ပါတယ်။

အခု DNS ပြီးတော့ DNSSEC ကို ဆက်သွားပါမယ်.. DNSSEC ဆိုတာ DNS ရဲ့ security extension ပဲဖြစ်ပါတယ်။ ပြေရမယ်ဆိုရင် DNS ဆိုတဲ့ အရာက hierarchical ပုံစံရှိတယ်ဗျ။ www.google.com. ကို fully qualify domain name (FQDN) လို့ခေါ်တယ်ဗျ.. ရှေ့က www ဆိုတာ hostname လို့ပြောလို့ရပြီး google.com. ဆိုတာကတော့ domain name ပေါ့။​ အဲ့ဒီမှာ နောက်ဆုံးကနေစကြည့်တယ် com ရဲ့ နောက်မှာ . ဆိုတဲ့ ဟာလေးကိုတွေ့ရမယ် အဲ့ဒါတော့ root dns server တွေကိုကိုယ်စားပြုပါတယ်။​ နောက်ပြီးအဲ့ဒီကနေ .com ကို ရောက်မယ် နောက်ပြီး .google ပြီးတော့ www အဲ့ဒီလိုတစ်ဆင့်ချင်း သွားပါတယ်။ ပိုရှင်းအောင် အောက်က ပုံလေးကိုကြည့်လိုက်ပါ။

![dnssec_hierachy](/assets/img/2019-oct/dnssec_hierachy.png){:class="img-responsive"}

အဲ့ဒီလို ဆာဗာတစ်ခုနဲ့တစ်ခုကြားမှာ ပုံမှန်ဆို ဘယ်လို authentication မှ ရှိမနေဘူးဗျ။ အဲ့ဒီတော့ ကြားကနေ attacker က၀င်ပြီး ကိုယ်သွားချင်တဲ့ website IP ကို၀င်ပြောင်းလို့ရတာပေါ့ဗျာ ပြောရရင် MIM တို့ cache poisoning တို့ ဘာတို့ညာတို့နဲ့ resolver ကိုဖြစ်ဖြစ် ဘယ်ကိုဖြစ်ဖြစ်၀င်လုပ်လို့ရတယ်ပေါ့ဗျာ။ အဲ့ဒီတော့ website အမှန်ကို မရောက်ဘဲ သူရဲ့ ပုံစံတူလုပ်ထားတဲ့ pushing site ကိုရောက်ပြီး ကိုယ့်ရဲ့အချက်အလက်တွေကိုယူနိုင်တာပေါ့။

![dnssec_bad_hierachy_en](/assets/img/2019-oct/dnssec_bad_hierachy_en.png){:class="img-responsive"}

အဲ့ဒီလိုတွေမဖြစ်အောင်လို့ DNSSEC နဲ့ တစ်ဆင့်ချင်းမှာ authenticate ခံပြီးမှန်မှဆက်သွားဆိုတာမျိုးလုပ်လိုက်တော့ အထိုက်အလျောက်တော့ အချို့ attack တွေကို ကာကွယ်ပြီးသားဖြစ်သွားတာပေါ့။​ ဥပမာ [dnssec-failed.org][dnssec-failed]{:target="_blank" rel="noopener"} ဆိုရင် browser မှာခေါ်လို့ရမှာ မဟုတ်ပါဘူး။ လောလောဆယ်တော့ အပိုင်း ၁ ကို ဒီမှာပဲ ခဏနားလိုက်ဦးမယ်ဗျာ နောက်မှ technical ပိုင်း ပါတဲ့ အပိုင်း ၂ ကိုဆက်သွားတာပေါ့။ ဒါနဲ့ ကျွန်တော် အဲ့ဒီ DNSSEC ရဲ့ status ပြပေးတဲ့ browser extension လေးဘာလေးရေးမလားစဥ်းစာနေတာ SSL ကိုပြတဲ့ သော့အစိမ်းလေးလိုမျိုးလေ.. အာရုံရရင်တော့ လုပ်တာပေါ့။

※ ဒီ post မှာပြထားတဲ့ပုံများကို [nic.ch][nic-ch] မှယူသုံးထားပါတယ်။

[nic-ch]: https://www.nic.ch/faqs/dnssec/details/
[dnssec-failed]: https://dnsviz.net/d/dnssec-failed.org/dnssec/