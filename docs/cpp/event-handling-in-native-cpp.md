---
title: "原生 C++ 中的事件處理 | Microsoft Docs"
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
  - "事件處理, Visual C++"
ms.assetid: e4b9219a-15d8-42fb-83c8-6d2e4e087c8d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 原生 C++ 中的事件處理
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在原生 C\+\+ 事件處理中，您需使用 [event\_source](../windows/event-source.md) 和 [event\_receiver](../windows/event-receiver.md) 屬性並指定 `type`\=`native`，分別設定事件來源和事件接收器。  這些屬性可讓套用它們的類別引發事件，以及在原生的非 COM 內容中處理事件。  
  
## 宣告事件  
 在事件來源類別中，請在方法宣告中使用 [\_\_event](../cpp/event.md) 關鍵字將方法宣告為事件。  請務必宣告方法，但不要定義方法；這樣會產生編譯器錯誤，因為編譯器會在將方法變成事件時隱含定義該方法。  原生事件可以是包含零個或多個參數的方法。  傳回類型可為 void 或任何整數類型。  
  
## 定義事件處理常式  
 在事件接收器類別中，您會定義事件處理常式，其為具有簽章 \(傳回類型、呼叫慣例和引數\)，符合將處理之事件的方法。  
  
## 攔截事件的事件處理常式  
 同時，在事件接收器類別中，您可以使用內建函式 [\_\_hook](../cpp/hook.md) 將事件與事件處理常式產生關聯，以及使用 [\_\_unhook](../cpp/unhook.md) 來取消事件與事件處理常式的關聯。  您可以在事件處理常式中攔截多個事件，或在事件中攔截多個事件處理常式。  
  
## 引發事件  
 若要引發事件，只要呼叫在事件來源類別中宣告為事件的方法即可。  如果在事件中攔截到處理常式，則會呼叫處理常式。  
  
### 原生 C\+\+ 事件代碼  
 下列範例示範如何在原生 C\+\+ 中引發事件。  若要編譯和執行這個範例，請參閱程式碼中的註解。  
  
## 範例  
  
### 程式碼  
  
```  
// evh_native.cpp  
#include <stdio.h>  
  
[event_source(native)]  
class CSource {  
public:  
   __event void MyEvent(int nValue);  
};  
  
[event_receiver(native)]  
class CReceiver {  
public:  
   void MyHandler1(int nValue) {  
      printf_s("MyHandler1 was called with value %d.\n", nValue);  
   }  
  
   void MyHandler2(int nValue) {  
      printf_s("MyHandler2 was called with value %d.\n", nValue);  
   }  
  
   void hookEvent(CSource* pSource) {  
      __hook(&CSource::MyEvent, pSource, &CReceiver::MyHandler1);  
      __hook(&CSource::MyEvent, pSource, &CReceiver::MyHandler2);  
   }  
  
   void unhookEvent(CSource* pSource) {  
      __unhook(&CSource::MyEvent, pSource, &CReceiver::MyHandler1);  
      __unhook(&CSource::MyEvent, pSource, &CReceiver::MyHandler2);  
   }  
};  
  
int main() {  
   CSource source;  
   CReceiver receiver;  
  
   receiver.hookEvent(&source);  
   __raise source.MyEvent(123);  
   receiver.unhookEvent(&source);  
}  
```  
  
### Output  
  
```  
MyHandler2 was called with value 123.  
MyHandler1 was called with value 123.  
```  
  
## 請參閱  
 [事件處理](../cpp/event-handling.md)