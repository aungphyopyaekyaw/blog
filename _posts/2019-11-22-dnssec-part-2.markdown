---
layout: post
title:  "DNSSEC အပိုင်း ၂"
date:   2019-11-22 23:54:00 +0630
categories: DNS
image:
    path: /assets/img/2019-nov/dnssec-part2.png
---

![dnssec part 2](/assets/img/2019-nov/dnssec-part2.png){:class="img-responsive"}

ကျွန်တော် DNSSEC အပိုင်း ၂ ကို ဆက်ပြီဗျာ။ ဒီအပိုင်းမှာတော့ technical အကြောင်းတွေပဲပါ ပါမယ်။ ဘယ်ကစမလဲဆိုတော့ encryption ကနေစတာပေါ့။​ 

![Symmetric-Encryption](/assets/img/2019-nov/Symmetric-Encryption.png){:class="img-responsive"}

Encrytp လုပ်တဲ့နေရာမှာ symmetri နဲ့ asymmetri ဆိုပြီးရှိတယ်ဗျ။ Symmetrical Encryption ကတော့ရှင်းပါတယ် key တစ်ခုတည်းနဲ့ encript လုပ်လိုက်တယ် ပြီးတော့ အဲ့ key နဲ့ပဲပြန် decrypt လုပ်တယ်ပေါ့။ ပြောရရင် point A နဲ့ B ရှိတယ်ဆိုပါဆို့.. A က B ကို encrypt လုပ်ပြီးပို့ချင်တဲ့အခါ key တစ်ခုသုံးပြီး A မှာ encrypt လိုက်တယ် နောက်ပြီး အဲ့ key နဲ့ပဲ B မှာ decrypt ရတယ်။ ဆိုတော့ တစ်နည်းနည်းနဲ့တော့ အဲ့ဒီ key က A ရော B မှာပါ ရှိရတာပေါ့။ ဒါဆို အဲ့ဒီ key က A ရော B မှာပါ မရှိနိုင်ရင် ဘယ်လိုလုပ်မလဲ.. အဲ့မှာ asymmetric စ ပါပြီ။ သူကျတော့ဗျာ point A ရော B မှာပါ key pair ရှိပါတယ်.. ကိုယ့် key နဲ့ ကိုယ်ပေါ့ ဒီမှာ key pair ဆိုတာ public key နဲ့ private key လို့ ဆိုလိုပါတယ် (အဲ့ဒီ private နဲ့ public key မှာ connection တစ်ခုတော့ရှိတယ်ဗျ သူတို့ကို RSA algorithm နဲ့ generate လုပ်လိုက်တယ်ဆိုပါတော့)။​ သူ့ကို စာနဲ့ရေးရင် နည်းနည်းတော့ရှုပ်တယ်ဗျ။​ စမ်းကြည့်တာပေါ့.. A ရဲ့ private က A ပဲသိ A မှာပဲ ရှိပြီး public key ကတော့ B တင်မက အားလုံးက ကြည့်နိုင်ပါတယ်။ အဲ့လိုပဲ B ရဲ့ private က B မှာပဲရှိ B ပဲ ကြည့်လို့ရပြီး public key ကိုတော့ ဘယ်ကဖြစ်ဖြစ် ကြည့်လို့ ရပါတယ်။ Key တွေက ဟုတ်ပါပြီ သူတို့ဘယ်လိုတွေ encrypt လုပ်လဲ?? Public key တွေကလည်း ပြန်အလှန်တွေ့နေကြတယ်ဆိုတော့ A က ပို့ချင်တဲ့ဟာကို သူ့ key နဲ့သူ မလုပ်ပဲ B ရဲ့ public key နဲ့ encript လုပ်လိုက်တယ်ဗျာ.. အဲ့ဒီဟာက B ကိုလည်းရောက်ရော B က သူ့ private key နဲ့ decrypt ပြန်လုပ်တယ်။​ ပြောရရင် B ရဲ့ public key နဲ့ encrypt လုပ်တဲ့ဟာကို B ရဲ့ private key နဲ့ပဲ ပြန် decrypt လုပ်လိုက်တာ။ အခုပြောတဲ့ encryption နည်းက DNSSEC မှာတင်မဟုတ်ပဲ​ https, ssh, bitcoin, တော်တော်များများမှာ သုံးပါတယ်။

![Asymmetric-Encryption](/assets/img/2019-nov/Asymmetric-Encryption.png){:class="img-responsive"}

အခု encryption အကြောင်းပြီးပြီဆိုတော့ DNSSEC ကိုဆက်တာပေါ့.. အခု DNS မှာတော့ အဲ့ဒီ keys တွေကို encrypt လုပ်ဖို့ မသုံးဘူးဗျ။ [အရင်ပိုစ့်][dns-ssl]တုန်းက ပြောခဲ့သလိုပဲ DNS ဆိုတာ plain text ပဲလေ.. ဒါဆို ဘာအတွက် အခုလို key pairs တွေသုံးနေပါသလဲ??​ အဖြေကတော့ DNS ဆိုတာ hierarchical ဆိုတော့ level တစ်ခုနဲ့ တစ်ခုကြားမျာ authentication ခံပြီး ဒီ domain က ဒီ root က လာတယ်ဆိုတာ သေချာပါတယ်ဆိုတာကို လုပ်ပေးတာဖြစ်ပါတယ်။​ DNS မှာ zone file ဆိုတာ ရှိတယ်ဗျာ အဲ့ကို အလွယ်ပြောရရင် domain ရဲ့ resource record တွေသိမ်းထားတဲ့ database ပေါ့ အဲ့ဒိကို ကျွန်တော်တို့ RSASAH1 တို့ RSASHA256 တို့နဲ့ sing လုပ်လိုက်တယ်ဗျာ.. sign လုပ်ပြီးရင် သူ့ရဲ့ parent ကို delication singing record ဆိုတဲ့ DS record ပေးရတယ်.. ဒါပေမဲ့ အဲ့လို sign မှာ သက်တမ်းရှိတယ်ဗျ.. ကိုယ့် record တွေကလည်း ခဏခဏပြောင်းနိုင်တယ်လေ အဲ့လိုပဲ sign က လည်းသိပ်ကြာလို့အဆင်မပြေဘူး အဲ့တော့ ကိုယ့် ​parent/root server ကို DS ခဏခဏပို့ရမလိုဖြစ်နေတယ် အဲ့ဒါဘယ်လိုလုပ်မလဲ.. အဲ့တော့ zone ကို sign ထားတဲ့ဟာကို ပိုကောင်းတဲ့ encryption နဲ့ထပ် sign လိုက်တယ်ဗျာ.. zone ကို sign ထားတော့ zone signing key ပေါ့ အဲ့ key ကိုထပ် sign တော့ key signing key ဖြစ်ရောပါ့.. အဲ့ကျမှ ထွက်လာတဲ့ DS ကို root ပို့လိုက်ရင် ခဏခဏလည်း ပို့နေစရာမလိုတော့ဘူးပေါ့ဗျာ.. အဲ့မှာတင် parent နဲ့ child server အတွဲမိသွားပြီး chain လေးဖြစ်လာတယ်ပေါ့။ chain ဆိုလို့ zone ကို sign တဲ့အခါမှာလည်း chain တစ်ခုဖြစ်လာတယ်ဗျ.. အဲ့ဒါကို NSEC (Next secure) လို့ခေါ်ပါတယ်။ ကဲပါလေ အခုပြောသွားတဲ့ DNSSEC ကို ဘယ်လိုလုပ်မလဲဆိုရင်တော့ DNS panel တော်တော်များများမှာ one click နဲ့ ရပါတယ်.. အဲ့က ထွက်လာတဲ့ DS record ကို parent server မှာ ထည့်ပေးလိုက်တာနဲ့ ရပြီပဲ။ လိုအပ်တာရှိရင်တော့ အောက်က comment မှာလာပြောလို့ရပါတယ်..

[dns-ssl]: https://blog.kernellab.site/dns/2019/09/13/doh-vs-dot.html