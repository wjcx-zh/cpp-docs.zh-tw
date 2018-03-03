---
title: "原生 c + + 中的事件處理 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- event handling [C++], Visual C++
ms.assetid: e4b9219a-15d8-42fb-83c8-6d2e4e087c8d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 157b31f244ce5400aac5857f2473deb67938d8d0
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="event-handling-in-native-c"></a>原生 C++ 中的事件處理

在原生 c + + 事件處理中，您將使用的事件來源和事件接收器設定[event_source](../windows/event-source.md)和[event_receiver](../windows/event-receiver.md)分別屬性，指定`type` = `native`. 這些屬性可讓套用它們的類別引發事件，以及在原生的非 COM 內容中處理事件。

## <a name="declaring-events"></a>宣告事件

在 事件來源類別中，使用[__event](../cpp/event.md)關鍵字來宣告為事件的方法在方法宣告。 請務必宣告方法，但不要定義方法；這樣會產生編譯器錯誤，因為編譯器會在將方法變成事件時隱含定義該方法。 原生事件可以是包含零個或多個參數的方法。 傳回型別可為 void 或任何整數類型。  
  
## <a name="defining-event-handlers"></a>定義事件處理常式

在事件接收器類別中，您會定義事件處理常式，其為具有簽章 (傳回型別、呼叫慣例和引數)，符合將處理之事件的方法。  
  
## <a name="hooking-event-handlers-to-events"></a>攔截事件的事件處理常式  

也在事件接收器類別中，您要使用內建函式[__hook](../cpp/hook.md)使事件與事件處理常式和[__unhook](../cpp/unhook.md)來取消事件的事件處理常式。 您可以在事件處理常式中攔截多個事件，或在事件中攔截多個事件處理常式。  
  
## <a name="firing-events"></a>引發事件  

若要引發事件，只要呼叫在事件來源類別中宣告為事件的方法即可。 如果在事件中攔截到處理常式，則會呼叫處理常式。  
  
### <a name="native-c-event-code"></a>原生 C++ 事件代碼  

下列範例示範如何在原生 C++ 中引發事件。 若要編譯和執行這個範例，請參閱程式碼中的註解。  
  
## <a name="example"></a>範例  
  
### <a name="code"></a>程式碼  
  
```cpp  
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
  
### <a name="output"></a>輸出  
  
```Output
MyHandler2 was called with value 123.  
MyHandler1 was called with value 123.  
```  
  
## <a name="see-also"></a>請參閱

[事件處理](../cpp/event-handling.md)  

