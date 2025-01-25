SOC မှာအလုပ်လုပ်မဲ့ Security Analyst တစ်ယောက်အတွက် မသိမဖြစ်သိထားရမှာက Windows Logs တွေပါပဲ။ Company တော်တော်များများ၊ အဖွဲ့အစည်းတော်တော်များများက Windows PC and Servers တွေကိုသုံးကြပါတယ်။ ဒါကြောင့် ဒီ Windows Devices တွေကို Monitor လုပ်ဖို့ threat detection လုပ်ဖို့ Windows ပေါ်က Log တွေအကြောင်း အထူးသိဖို့လိုပါတယ်။ ဒီဆောင်းပါးမှာတော့ Windows Event တွေအကြောင်းလုံးမသိသေးတဲ့သူတွေအတွက် အခြေခံပိုင်းလေးတွေပြောပြပေးပါမယ်။

Windows OS က default အားဖြင့် Log တစ်ချို့ကို generate လုပ်ပါတယ်။ Default အားဖြင့် Application, System, Security log တွေကို generate လုပ်ပါတယ်။ မိမိစက်က Log တွေကို ပြန်ကြည့်ချင် ရင် Windows မှာ Event Viewer ဆိုတဲ့ program လေးပါပါတယ်။ ဒီ program လေးကနေ လက်ရှိ မိမိ ကွန်ပျူတာ၊ ဆာဗာ မှာဖြစ်ပျက်နေတဲ့ အဖြစ်အပျက်တွေကိုကြည့်လို့ရပါတယ်။

> [!Attention]
> ဒါပေမဲ့ Windows Default log setting က ကန့်သတ်ချက်အများကြီးရှိပါတယ်။ Logs တွေကို C:\Windows\System32\winevt\Logs ဆိုတဲ့ directory အောက်မှာ .evtx ဆိုတဲ့ ဖိုင် format နဲ့ သိမ်း‌ပြီး ခုနပြောတဲ့ Application, System, Security စတဲ့ Log တွေရဲ့ Log ဖိုင်ဆိုဒ်ဟာ 20 MB ထိပဲ လက်ခံပါတယ်။ 20 MB ပြည့်ရင် အရင်က Log တွေပျက်သွားပြီး auto rotate ပုံစံနဲ့ saveတာပါ။ ဒီ 20MB ဆိုဒ် limit setting ကိုပြင်လို့ရပါတယ်။ ကိုယ့်စက်၊ဆာဗာမှာ storage space အပိုရှိမယ်ဆို အနည်းဆုံး 2GB လောက်ထိထားသင့်ပါတယ်။

ဒါကြောင့် Windows Logs တွေကို SIEM ဆီသို့ real time တောက်လျှောက်ပို့နေဖို့လိုပါတယ်။

Windows log တွေထဲမှာ ဘာတွေပါလဲ

Windows Logs တွေဟာ xml format နဲ့ရှိနေပြီး အရေးကြီးတဲ့ information တွေပါပါတယ်။

အဓိက အကျဆုံး field ဆိုရင်တော့ Event ID field ပါပဲ။ သူက Event တစ်ခု Log တစ်ကြောင်း က ဘယ်လို Logလဲ၊ ဘာအမျိုးအစားလဲဆိုတာဖော်ပြပေးပါတယ်။ Event ID နံပါတ်ပေါ်မူတည်ပြီး ဒါက ဘယ်လို Event လဲ ဘာကြောင့်ဖြစ်လဲ ဆိုတာပြောပြလို့ရပါတယ်။ ဥပမာ - Event ID 4720 နဲ့ လာတဲ့ Event ဆို တစ်ယောက်ယောက်က ကွန်ပျူတာမှာ user account အသစ်တည်ဆောက်တဲ့ အချိန်မှာလာတဲ့ Event ဖြစ်တယ်။ AD ထဲမှာ user တစ်ယောက်ကို delete လုပ်လိုက်မယ်ဆိုရင်တော့ event ID 4726 ပါတဲ့ log တစ်ကြောင်းကို တွေ့ရပါလိမ့်မယ်။

![image alt](https://github.com/thuya-hacktilizer/Infosec-sharing-thuya/blob/main/SOC%20and%20DFIR%20articles%20in%20Myanmar%20(Burmese)/4.%20Microsoft%20Windows%20Logs/Pasted%20image%2020250124091933.png?raw=true)

XML Format နဲ့ကြည့်ရင် အထက်ပါ Log ကို ဒီလိုတွေ့ရပါမယ်။

![image alt](https://github.com/thuya-hacktilizer/Infosec-sharing-thuya/blob/main/SOC%20and%20DFIR%20articles%20in%20Myanmar%20(Burmese)/4.%20Microsoft%20Windows%20Logs/Pasted%20image%2020250124092258.png?raw=true)

###### တစ်ခြား အရေးကြီးတဲ့ Field တွေကို အောက်ပါ List မှ ကြည့်နိုင်ပါတယ်။

**Log Name :** Name of the event log to which events from different logging components will be written. Events are commonly logged for system, security, and applications. (e.g., Application, System, Security, etc.).

**TimeCreated SystemTime:** the exact timestamp when an event was logged on the system, essentially recording the date and time the event occurred; it is a key element used to identify when a specific system activity happened. 

**Source :** The software that logged the event.

**Event ID :** A unique identifier for the event.

**Task Category :** This often contains a value or name that can help us understand the
purpose or use of the event.

**Level :** The severity of the event (Information, Warning, Error, Critical, and Verbose).

**Keywords :** Keywords are flags that allow us to categorize events in ways beyond the
other classification options. These are generally broad categories, such as "Audit
Success" or "Audit Failure" in the Security log.

**User :** The user account that was logged on when the event occurred.

**OpCode :** This field can identify the specific operation that the event reports.

**Logged :** The date and time when the event was logged.

**Computer :** The name of the computer where the event occurred.

XML Data : All the above information is also included in an XML format along with

additional event data.

Event ID တွေက windows OS version ပြောင်းသွားလည်းများသောအားဖြင့်ပြောင်းလေ့မရှိပါဘူး။ ဒါပေမဲ့ Event ID တွေပေါ်မူတည်ပြီး မိမိတို့ SOC ထဲမှာ Detection rules တွေကို ရေးတော့မယ်ဆိုရင်တော့ နောက်ဆုံးတစ်ခေါက်လောက် ရေးချင်တဲ့ Event ID အကြောင်းကို Microsoft online documentation မှာ ဖတ်လိုက်ပါ။ ပြောင်းသွားလားမပြောင်းသေးလား သေချာအောင်ရယ် တစ်ခြား update တွေရှိမလားစစ်ဖို့အတွက်ပါ။

Default အားဖြင့် ပေါ်လေ့ရှိတဲ့ Log တွေကအကန့်အသတ်ရှိလို့ Log visibility ပိုကောင်းအောင် Blue Teamer တော်တော်များများက widnows log အပြင် sysmon ပါသုံးဖို့ အကြံပြုပါတယ်။ Sysmon ဆိုတာ windows မှာရှိနေတဲ့ default log တွေအပြင် ပို detail ကျတဲ့ log တွေကို ထုတ်ပေးတဲ့ program တစ်ခုပါ။ Microsoft ကိုယ်တိုင်ထုတ်ပေးထားတဲ့ add on program တစ်ခုပါ။ သူ့အကြောင်းကို နောက် article သပ်သပ်ရေးပါမယ်။

Windows Log တွေနဲ့ ပက်သက်ပြီး SOC Architect တွေအနေနဲ့ သတိပြုစရာ လေးတွေဆက်ပြောပြပါမယ်။

> [!Attention]
> Windows Log တွေကို Default setting ဘဲထားမယ်ဆိုရင် Sigma rule repo ထဲက rules တွေရဲ့ 10~20% လောက်သာ အသုံးပြုလို့ရမှာပါ။ များသောအားဖြင့် windows sigma rules တွေက sysmon နှင့် တစ်ခြား Non-default enable logs တွေပေါ်မှာ အခြေခံ detection ကိုရေးထားလို့ပါ။ အောက်ပါ ပုံ ကို reference လုပ်နိုင်ပါတယ်။

![image alt](https://github.com/thuya-hacktilizer/Infosec-sharing-thuya/blob/main/SOC%20and%20DFIR%20articles%20in%20Myanmar%20(Burmese)/4.%20Microsoft%20Windows%20Logs/Pasted%20image%2020250124092632.png?raw=true)

###### Default Application, system, security Log တွေအပြင် အောက်ပါ Log တွေကိုလဲ SIEM ကိုပိုသင့်ပါတယ်။

Powershell Module logging and ScriptBlock logging ကိုဖွင့်ထားပါ။ Attacker တော်တော်များများက powershell ကို abuse လုပ်ပြီးသုံးကြလို့ပါ။

Microsoft-Windows-Windows Defender%4Operational.evtx အောက်မှာ သိမ်းလေ့ရှိတဲ့ Windows Defender logs တွေကို SIEM ဆီပို့သင့်ပါတယ်။ Windows defender Alert များနှင့် exclusion event များကို သိနိုင်ပါတယ်။ အထူးသဖြင့် EDR မသုံးနိုင်သေးတဲ့ environment မှာဆို ဒီ Log တွေက အထူးအရေးကြီးပါတယ်။

Microsoft-Windows-Windows Firewall With Advanced Security%4Firewall.evtx အောက်မှာ ရှိတဲ့ Firewall logs တွေကိုလဲ ပို့သင့်ပါတယ်။ ဒီ Log တွေကနေ firewall rule added/modified/deleted စတဲ့ ဟာတွေအားလုံး သိရှိနိုင်ပါတယ်။ ဟက်ကာတွေက C2 traffic တွေအတွက် Firewall တွေကိုပြင်ဆင်တာတွေပြုလုပ်လေ့ရှိပါတယ်။

တစ်ခြားသောအရေးကြီးတဲ့ Log တွေလဲကျန်ပါသေးတယ်။ ဒီ Article က Basic ဆိုတော့ အနည်းငယ်ပဲ ဖော်ပြပေးလိုက်ပါတယ်။ နောက် Article တွေမှာ Windows Log နဲ့ပက်သက်ပြီး ပိုမိုအသေးစိတ်ဆွေးနွေး ပါဦးမယ်။

> [!warning]
> ကိုယ့် အလုပ်က Cybersecurity policy, environment တွေနဲ့ ကိုက်ညီမယ့် Windows logs တွေ on တာက အနုပညာ တစ်ရပ်လိုတောင်ဖြစ်နေပါပြီ။ SOC Architect တစ်ယောက်အနေနဲ့ ဘယ်လို environment မျိုးမှာ ဘယ်လို Windows Logs တွေ On သင့်လဲဆိုတာကောင်းကောင်းသိဖို့လိုပါမယ်။ ရှုပ်ပါတယ် endpoint အားလုံးက ရှိသမျှ Log အကုန် On မယ်ဆိုရင် မိမိလုပ်နေတဲ့ organization က အရမ်းချမ်းသာပြီး အရမ်း Storage တွေပေါနေမှဖြစ်မယ်နော် 😉 ။ အလွယ်တကူပြီးအောင် ဘာမှ သေချာ tune မလုပ်ဘဲ Default အတိုင်းရတဲ့ log တွေလောက်ကိုဘဲ SIEM ဆီပို့မယ်ဆိုလဲ security detection မှာ အများကြီး လစ်ဟာသွားမှာပါ။ Tictical Windows Logs enabling အကြောင်းကို နောက်များမှာထပ်ဆွေးနွေးပါမယ်။

စေတနာဖြင့်

သူရ

January 2025


အရေးကြီးတဲ့ Windows Logs တွေထဲက event ID တစ်ချို့ကိုဖော်ပြပေးလိုက်ပါတယ်။

**Event ID 1102 (The audit log was cleared) :** Clearing the audit log is often a
sign of an attempt to remove evidence of an intrusion or malicious activity.

**Event ID 1116 (Antivirus malware detection) :** This event is particularly
important because it logs when Defender detects a malware. A surge in these
events could indicate a targeted attack or widespread malware infection.

**Event ID 1118 (Antivirus remediation activity has started) :** This event
signifies that Defender has begun the process of removing or quarantining
detected malware. It's important to monitor these events to ensure that
remediation activities are successful.

**Event ID 1119 (Antivirus remediation activity has succeeded) :** This event
signifies that the remediation process for detected malware has been successful.
Regular monitoring of these events will help ensure that identified threats are
effectively neutralized.

**Event ID 1120 (Antivirus remediation activity has failed) :** This event is
the counterpart to 1119 and indicates that the remediation process has failed.
These events should be closely monitored and addressed immediately to ensure
threats are effectively neutralized.

**Event ID 4624 (Successful Logon) :** This event records successful logon events.
This information is vital for establishing normal user behavior. Abnormal behavior,
such as logon attempts at odd hours or from different locations, could signify a
potential security threat.

**Event ID 4625 (Failed Logon) :** This event logs failed logon attempts. Multiple
failed logon attempts could signify a brute-force attack in progress.

**Event ID 4648 (A logon was attempted using explicit credentials) :** This
event is triggered when a user logs on with explicit credentials to run a program.
Anomalies in these logon events could indicate lateral movement within a network,
which is a common technique used by attackers.

**Event ID 4672 (Special Privileges Assigned to a New Logon) :** This event is
logged whenever an account logs on with super user privileges. Tracking these
events helps to ensure that super user privileges are not being abused or used
maliciously.

**Event ID 4698 (A scheduled task was created) :** This event is triggered when
a scheduled task is created. Monitoring this event can help you detect persistence
mechanisms, as attackers often use scheduled tasks to maintain access and run
malicious code.

**Event ID 4700 & Event ID 4701 (A scheduled task was enabled/disabled) :**
This records the enabling or disabling of a scheduled task. Scheduled tasks are
often manipulated by attackers for persistence or to run malicious code, thus these
logs can provide valuable insight into suspicious activities.

**Event ID 4702 (A scheduled task was updated) :** Similar to 4698, this event is
triggered when a scheduled task is updated. Monitoring these updates can help
detect changes that may signify malicious intent.

**Event ID 4738 (A user account was changed) :** This event records any changes
made to user accounts, including changes to privileges, group memberships, and
account settings. Unexpected account changes can be a sign of account takeover
or insider threats.

**Event ID 4771 (Kerberos pre-authentication failed) :** This event is similar to
4625 (failed logon) but specifically for Kerberos authentication. An unusual amount
of these logs could indicate an attacker attempting to brute force your Kerberos
service.

**Event ID 4776 (The domain controller attempted to validate the**
**credentials for an account) :** This event helps track both successful and
failed attempts at credential validation by the domain controller. Multiple failures
could suggest a brute-force attack.

