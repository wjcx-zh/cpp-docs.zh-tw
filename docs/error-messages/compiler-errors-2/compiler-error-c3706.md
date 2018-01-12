---
title: "編譯器錯誤 C3706 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3706
dev_langs: C++
helpviewer_keywords: C3706
ms.assetid: d20a33eb-d625-46c5-ac87-32075a590d07
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2b33ea3c7de9afc605622cc55f4a45f73350d7db
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3706"></a>編譯器錯誤 C3706
'function': 必須是 COM 介面來引發 COM 事件  
  
 您用來引發 COM 事件的事件介面必須是 COM 介面。 在此情況下，介面應該使用 Visual c + + 屬性會定義或匯入使用[#import](../../preprocessor/hash-import-directive-cpp.md)從 #import 的 embedded_idl 屬性的型別程式庫。  
  
 請注意，`#include`行下面範例所示的 ATL 標頭檔所需使用 COM 事件。 若要修正這個錯誤，請`IEvents`（事件介面） 的 COM 介面，藉由套用下列屬性至介面定義：[物件](../../windows/object-cpp.md)，[雙重](../../windows/dual.md)，或[dispinterface](../../windows/dispinterface.md)。  
  
 如果介面是由 MIDL 產生的標頭檔來自，編譯器會將其辨識為 COM 介面。  
  
 下列範例會產生 C3706:  
  
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