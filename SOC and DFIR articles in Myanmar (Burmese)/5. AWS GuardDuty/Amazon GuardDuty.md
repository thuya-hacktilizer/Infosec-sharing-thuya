![[Pasted image 20250809200744.png]]

ဒီနေ့တော့ AWS နဲ့ security feature တစ်ခုဖြစ်တဲ့ GuardDuty ဆိုတဲ့ service လေးနဲ့ မိတ်ဆက်ပေးချင်ပါတယ်။ ဒီ Service လေးကို ကျွန်တော်လုပ်ဖူးတဲ့ Cloud Log source တွေရှိတဲ့ SOC တော်တော်များများမှာတွေ့ဖူးပါတယ်။ မှတ်မှတ်ရရ လုပ်ပေးဖူးတဲ့ SOC တစ်ခုဆို အဲ့ Customer ကသူ့ Infra တစ်ခုလုံးကို AWS မှာ Run တာပါ။ ကုမ္ပဏီက တက်ဆီဆားဗစ် App ကုမ္ပဏီပါ။ အရှေ့တောင် အာရှ အခြေဆိုဒ် ကုမ္ပဏီတစ်ခုပါ။ ဒီကုမ္ပဏီက AWS Log source တော်တော်များများက Log တွေကို SIEM ပေါ်ကိုပို့ထားပါတယ်။ SIEM ကလဲ AWS Cloud ပေါ်မှာပါပဲ။ အဓိကသူတို့ AWS service တွေသုံးတဲ့ထဲ မှာ GuardDuty ဆိုတဲ့ security service လေးကိုသုံးတာလည်းတွေ့ခဲ့ရပါတယ်။

GuardDuty ဆိုတာ AWS ရဲ့ security service တစ်ခုဖြစ်ပြီး မိမိ AWS account ထဲက malicious event တွေကို Detect လုပ်ပေးနိုင်တဲ့ service တစ်ခုပါ။ SOC မရှိတဲ့ customer တွေလဲ အသုံးပြုလို့ရပါတယ်။ Mini SIEM လေးလို သဘောထားပြီးလဲသုံးလို့ရပါတယ်။ AWS မှာ GuardDuty ကိုဖွင့်လိုက်ပြီဆို သူက Foundational Data Source (Log Source) တွေဖြစ်တဲ့ VPC flow logs, CloudTrail, DNS Logs စတဲ့ Log Source တွေကဒေတာကိုယူပြီး သူ့ဆီမှာရှိတဲ့ Threat Intelligence Data, threat detection ML Model တွေနဲ့ ပေါင်းစပ်ပြီး Malicious event တွေကို detect လုပ်တာပါ။ အဲ့ LogSource တွေကိုသွားပြီး သီးသန့် ဖွင့်တာ၊ configuration ချတာတွေလုပ်နေစရာမလိုပါဘူး။ GuardDuty က သူ့ဘာသာသူ အဲ့ဒီ Log source တွေက ဒေတာယူပြီး Monitoring လုပ်ပေးနေတာပါ။ တစ်ခုခု Malicious event တွေ့ပြီဆိုရင် ကိုယ့်ကို Alert ပေးပါတယ်။

ရလာတဲ့ Alert ပေါ်မူတည်ပြီး တစ်ခုခုကိုပိတ်ချင်တာ၊ IP တစ်ခုခုကို Ban ချင်တာ၊ စသဖြင့် auto response လုပ်ချင်ရင် Lamda function လိုဟာမျိုးနဲ့ ပေါင်းပြီး auto response လုပ်သွားအောင် configuration ချထားလို့ရပါသေးတယ်။ Detection အဓိကဆိုပေမဲ့ detect ဖြစ်ပြီး လူက manual threat ကို တုံ့ပြန်စရာ မလို့ဘဲ Lamda Function  လို service မျိုးနဲ့ ပေါင်းစပ်ပြီး အလိုအလျှောက်တုံ့ပြန်လို့ရအောင် ပြုလုပ်ထားလို့ရတာပါ။

နောက်အဓိက GuardDuty ရဲ့ feature တစ်ခုကတော့ ကိုယ့် AWS account ထဲက EC2 Instance e တစ်ခုခုဆီက malicious traffic တွေ့တယ်ဆို အဲ့ Instance ရဲ့  EBS (တစ်နည်း Harddisk) တစ်ခုလုံးကို Malware Scan စစ်နိုင်တာပါပဲ။ အဲ့ဒီလိုစစ်တဲ့အချိန်မှာ အဲ့ဒီ Instance ထဲမှာ Antivirus Agent လိုမျိုး Agent တစ်ခုခု ထည့်သွင်းပေးဖို့မလိုခြင်းပဲဖြစ်ပါတယ်။ ဒါကသူ့ရဲ့ထူးခြားချက်ပါ။ သူလုပ်ဆောင်ပုံက အဲ့ဒီ့ Instance ရဲ့ EBS volume ကို snapshot လုပ်ပြီးသူ့ဘာသာသူ အဲ့ snapshot ထဲမှာ malware ကိုရှာတာပါ။ ပြီးရင်တော့ အဲ့ Snapshot ကို သူဘာသာသူ အလိုအလျှောက် ဖျက်ပစ်မှာပါ။

Malware တွေ့သွားလို့ ကိုယ်က  အဲ့ Snapshot ကို နောက်ပိုင်း Forensics လုပ်ဖို့သိမ်းထားမယ်ဆို သူ့ကို သိမ်းခိုင်းထားလို့လည်း ရပါတယ်။ EC2 Instances တွေထဲ Antivirus Agent မထည့်ချင်တဲ့ Dev Team နဲ့ Security Team ချနေစရာမလိုတော့ဘူးပေါ့ဗျာ😊 ။

GuardDuty က Alert တွေကို SIEM ထဲကို ပို့ထားပြီး SIEM ကနေပဲ GuardDuty ကို Log source တစ်ခု သဘောမျိုးထားပြီး စီမံလို့လဲရပါတယ်။ GuardDuty Alert တွေကိုကြည့်ပြီး SOC က response လုပ်လို့လဲရပါတယ်။ SIEMကိုလာတဲ့ နမူနာ GuardDuty Alert တွေကိုကြည့်ချင်ရင်တော့ Splunk နဲ့ BOTSv3 Data set ထဲမှာ အောက်ပါ filter ကိုသုံးပြီးရှာကြည့်လို့ရပါတယ်။


![[Pasted image 20250809200704.png]]

![[Pasted image 20250809200707.png]]

GuardDuty ကိုစပြီးဖွင့်လိုက်မယ်ဆိုရင်တော့ တစ်လ Trial free ရပါလိမ့်မယ်။ သူက Pay-as-you-go service ဖြစ်တာကြောင့် ကိုယ့် environment ကသူ process လုပ်ရမယ့် Log Volume ပေါ်မူတည်ပြီး ကုန်ကျစရိတ်ရှိမှာပါ။ ပထမတစ်လ Trial မှာ ကိုယ့် environment မှာ ဘယ်လောက်လောက် ကျသင့်မလဲ မှန်းလို့ရသွားပါလိမ့်မယ်။ Pricing အသေးစိတ်တွက်ချက်မှုကိုတော့ အောက်ကသူ့ရဲ့ pricing page မှာ ဝင်ရောက်ကြည့်ရှုနိုင်ပါတယ်။ [https://aws.amazon.com/guardduty/pricing/](https://aws.amazon.com/guardduty/pricing/)

AWS environment မှာအဖြစ်များလေ့ရှိတဲ့ ကိုယ့်ရဲ့ EC2 instance မှာ Bitcoin mining လာလုပ်ခံရတာတို့၊ ကိုယ့် environment ကနေ known malicious IP ကိုဆက်သွယ်နေတာတို့၊ ကိုယ့် remote service တစ်ခုခုကို brute force လာလုပ်နေတာတို့ကို GuardDuty က detect လုပ်နိုင်ပါတယ်။

ဒါကြောင့် Security အကြောင်းကို အရမ်းမကျွမ်းကျင်တဲ့ Developer များကိုယ်တိုင် မိမိ environment မှာ SIEM တွေဘာတွေ လိုတစ်‌ခြား Security Service တွေမရှိသည့်တိုင် ဒါလေးကိုဖွင့်ပြီး တတ်နိုင်သလောက် AWS account မှာ Security Detection and Response လုပ်နိုင်အောင် မျှဝေပေးလိုက်ပါတယ်။

စေတနာဖြင့်
သူရ (9.8.2025)
