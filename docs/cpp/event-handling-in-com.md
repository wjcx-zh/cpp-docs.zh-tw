---
title: "COM 中的事件處理 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COM, 事件"
  - "宣告事件"
  - "宣告事件, COM 中的事件處理"
  - "宣告事件, 在 COM 中"
  - "事件處理常式"
  - "事件處理常式, COM"
  - "事件處理"
  - "事件處理, 關於事件處理"
  - "事件處理, COM"
  - "事件接收器, 在事件處理中"
  - "事件接收器, 名稱和簽章比對"
  - "事件來源, 在事件處理中"
  - "連結事件"
ms.assetid: 6b4617d4-a58e-440c-a8a6-1ad1c715b2bb
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COM 中的事件處理
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 COM 事件處理中，您需使用 [event\_source](../windows/event-source.md) 和 [event\_receiver](../windows/event-receiver.md) 屬性並指定 `type`\=**com**，分別設定事件來源和事件接收器。  這些屬性會從自訂、分派和雙重介面插入適當的程式碼，以允許它們所套用的類別透過 COM 連接點引發事件和處理事件。  
  
## 宣告事件  
 在事件來源類別中，請在介面宣告使用 [\_\_event](../cpp/event.md) 關鍵字將介面的方法宣告為事件。  當您以介面方法呼叫它們時，會引發該介面的事件。  事件介面的方法可以有零或多個參數 \(應該都是 **in** 參數\)。  傳回類型可為 void 或任何整數類型。  
  
## 定義事件處理常式  
 在事件接收器類別中，您會定義事件處理常式，其為具有簽章 \(傳回類型、呼叫慣例和引數\)，符合將處理之事件的方法。  COM 事件不需要符合呼叫慣例，如需詳細資訊，請參閱[配置相依的 COM 事件](#vcconeventhandlingincomanchorlayoutdependentcomevents)。  
  
## 攔截事件的事件處理常式  
 同時，在事件接收器類別中，您可以使用內建函式 [\_\_hook](../cpp/hook.md) 將事件與事件處理常式產生關聯，以及使用 [\_\_unhook](../cpp/unhook.md) 來取消事件與事件處理常式的關聯。  您可以在事件處理常式中攔截多個事件，或在事件中攔截多個事件處理常式。  
  
> [!NOTE]
>  通常，有兩種方法可以讓 COM 事件接收器存取事件來源介面定義。  第一種是共用常見的標頭檔，如下所示。  第二種是使用 [\#import](../preprocessor/hash-import-directive-cpp.md) 搭配 `embedded_idl` 匯入限定詞，以便將事件來源類型程式庫寫入 .tlh 檔案，其中已儲存屬性產生的程式碼。  
  
## 引發事件  
 若要引發事件，只要呼叫在事件來源類別中使用 `__event` 關鍵字宣告之介面的方法即可。  如果在事件中攔截到處理常式，則會呼叫處理常式。  
  
### COM 事件代碼  
 下列範例示範如何在 COM 中引發事件。  若要編譯和執行這個範例，請參閱程式碼中的註解。  
  
```  
// evh_server.h  
#pragma once  
  
[ dual, uuid("00000000-0000-0000-0000-000000000001") ]  
__interface IEvents {  
   [id(1)] HRESULT MyEvent([in] int value);  
};  
  
[ dual, uuid("00000000-0000-0000-0000-000000000002") ]  
__interface IEventSource {  
   [id(1)] HRESULT FireEvent();  
};  
  
class DECLSPEC_UUID("530DF3AD-6936-3214-A83B-27B63C7997C4") CSource;  
```  
  
 伺服器端的程式碼如下：  
  
```  
// evh_server.cpp  
// compile with: /LD  
// post-build command: Regsvr32.exe /s evh_server.dll  
#define _ATL_ATTRIBUTES 1  
#include <atlbase.h>  
#include <atlcom.h>  
#include "evh_server.h"  
  
[ module(dll, name="EventSource", uuid="6E46B59E-89C3-4c15-A6D8-B8A1CEC98830") ];  
  
[coclass, event_source(com), uuid("530DF3AD-6936-3214-A83B-27B63C7997C4")]  
class CSource : public IEventSource {  
public:  
   __event __interface IEvents;   
  
   HRESULT FireEvent() {  
      __raise MyEvent(123);  
      return S_OK;  
   }  
};  
```  
  
 用戶端的程式碼如下：  
  
```  
// evh_client.cpp  
// compile with: /link /OPT:NOREF  
#define _ATL_ATTRIBUTES 1  
#include <atlbase.h>  
#include <atlcom.h>  
#include <stdio.h>  
#include "evh_server.h"  
  
[ module(name="EventReceiver") ];  
  
[ event_receiver(com) ]  
class CReceiver {  
public:  
   HRESULT MyHandler1(int nValue) {  
      printf_s("MyHandler1 was called with value %d.\n", nValue);  
      return S_OK;  
   }  
  
   HRESULT MyHandler2(int nValue) {  
      printf_s("MyHandler2 was called with value %d.\n", nValue);  
      return S_OK;  
   }  
  
   void HookEvent(IEventSource* pSource) {  
      __hook(&IEvents::MyEvent, pSource, &CReceiver::MyHandler1);  
      __hook(&IEvents::MyEvent, pSource, &CReceiver::MyHandler2);  
   }  
  
   void UnhookEvent(IEventSource* pSource) {  
      __unhook(&IEvents::MyEvent, pSource, &CReceiver::MyHandler1);  
      __unhook(&IEvents::MyEvent, pSource, &CReceiver::MyHandler2);  
   }  
};  
  
int main() {  
   // Create COM object  
   CoInitialize(NULL);  
   {  
      IEventSource* pSource = 0;  
      HRESULT hr = CoCreateInstance(__uuidof(CSource), NULL,         CLSCTX_ALL, __uuidof(IEventSource), (void **) &pSource);  
      if (FAILED(hr)) {  
         return -1;  
      }  
  
      // Create receiver and fire event  
      CReceiver receiver;  
      receiver.HookEvent(pSource);  
      pSource->FireEvent();  
      receiver.UnhookEvent(pSource);  
   }  
   CoUninitialize();  
   return 0;  
}  
```  
  
### 輸出  
  
```  
MyHandler1 was called with value 123.  
MyHandler2 was called with value 123.  
```  
  
##  <a name="vcconeventhandlingincomanchorlayoutdependentcomevents"></a> 配置相依的 COM 事件  
 配置相依性是只有 COM 程式設計才有的問題。  在原生與 Managed 事件處理中，處理常式的簽章 \(傳回類型、呼叫慣例和引數\) 必須與其事件相符，不過，處理常式的名稱不必與其事件相符。  
  
 不過，在 COM 事件處理中，當您將 **event\_receiver** 的 *layout\_dependent* 參數設定為 **true** 時，便會強制執行名稱和簽章的比對。  這表示事件接收器中處理常式的名稱和簽章必須與所要攔截之事件的名稱和簽章完全相符。  
  
 當 *layout\_dependent* 設為 **false** 時，可以在引發事件方法和攔截方法 \(其委派\) 之間混合搭配及比對呼叫慣例和儲存類別 \(虛擬、靜態等等\)。  這會比 *layout\_dependent*\=**true** 稍微有效率一些。  
  
 例如，假設已定義的 `IEventSource` 中內含下列方法：  
  
```  
[id(1)] HRESULT MyEvent1([in] int value);  
[id(2)] HRESULT MyEvent2([in] int value);  
```  
  
 假設事件來源的格式如下：  
  
```  
[coclass, event_source(com)]  
class CSource : public IEventSource {  
public:  
   __event __interface IEvents;  
  
   HRESULT FireEvent() {  
      MyEvent1(123);  
      MyEvent2(123);  
      return S_OK;  
   }  
};  
```  
  
 然後，在事件接收器中，所有在 `IEventSource` 的方法中攔截到的處理常式必須符合其名稱和簽章，如下所示：  
  
```  
[coclass, event_receiver(com, true)]  
class CReceiver {  
public:  
   HRESULT MyEvent1(int nValue) {  // name and signature matches MyEvent1  
      ...  
   }  
   HRESULT MyEvent2(E c, char* pc) {  // signature doesn't match MyEvent2  
      ...  
   }  
   HRESULT MyHandler1(int nValue) {  // name doesn't match MyEvent1 (or 2)  
      ...  
   }  
   void HookEvent(IEventSource* pSource) {  
      __hook(IFace, pSource);  // Hooks up all name-matched events   
                               // under layout_dependent = true  
      __hook(&IFace::MyEvent1, pSource, &CReceive::MyEvent1);   // valid  
      __hook(&IFace::MyEvent2, pSource, &CSink::MyEvent2);   // not valid  
      __hook(&IFace::MyEvent1, pSource, &CSink:: MyHandler1); // not valid  
   }  
};  
```  
  
## 請參閱  
 [事件處理](../cpp/event-handling.md)