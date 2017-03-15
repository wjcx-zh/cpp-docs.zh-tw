---
title: "編譯器錯誤 C3706 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3706"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3706"
ms.assetid: d20a33eb-d625-46c5-ac87-32075a590d07
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3706
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 必須是 COM 介面來引發 COM 事件  
  
 您用來引發 COM 事件的事件介面必須是 COM 介面。  在此情況下，介面應該使用 Visual C\+\+ 屬性定義，或是使用 [\#import](../../preprocessor/hash-import-directive-cpp.md) 從型別程式庫以 \#import 的 embedded\_idl 屬性匯入。  
  
 請注意，若要使用 COM 事件，如下列範例中 ATL 標頭檔之 `#include` 行是必要的。  若要修正此錯誤，請將下列屬性的其中一個套用至介面定義：[object](../../windows/object-cpp.md)、[dual](../../windows/dual.md) 或 [dispinterface](../../windows/dispinterface.md)，讓 `IEvents` \(事件介面\) 成為 COM 介面：  
  
 如果介面是來自 MIDL 所產生的標頭檔，編譯器會無法將它識別為 COM 介面。  
  
 下列範例會產生 C3706：  
  
```  
// C3706.cpp  
// compile with: /c  
// C3706 expected  
#define _ATL_ATTRIBUTES 1  
#include <atlbase.h>  
#include <atlcom.h>  
#include <atlctl.h>  
  
[module(dll, name="idid", uuid="12341234-1234-1234-1234-123412341234")];  
  
// Uncomment the following line to resolve.  
// [object, uuid="12341234-1234-1234-1234-123412341237"]  
__interface IEvents : IUnknown {  
   HRESULT event1(/*[in]*/ int i);   // uncomment [in]  
};  
  
[dual, uuid="12341234-1234-1234-1234-123412341235"]  
__interface IBase {  
   HRESULT fireEvents();  
};  
  
[coclass, event_source(com), uuid="12341234-1234-1234-1234-123412341236"]  
class CEventSrc : public IBase {  
   public:  
   __event __interface IEvents;  
  
   HRESULT fireEvents() {  
      HRESULT hr = IEvents_event1(123);  
      return hr;  
   }  
};  
```