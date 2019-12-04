---
title: 編譯器錯誤 C3706
ms.date: 11/04/2016
f1_keywords:
- C3706
helpviewer_keywords:
- C3706
ms.assetid: d20a33eb-d625-46c5-ac87-32075a590d07
ms.openlocfilehash: 810ec59a814b04349913648fb49a03eb63912cd9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757978"
---
# <a name="compiler-error-c3706"></a>編譯器錯誤 C3706

' function '：必須是 COM 介面，才能引發 COM 事件

您用來引發 COM 事件的事件介面必須是 COM 介面。 在此情況下，應該使用視覺化C++屬性來定義介面，或使用 #import 的 embedded_idl 屬性從類型程式庫匯入[#import](../../preprocessor/hash-import-directive-cpp.md) 。

請注意，使用 COM 事件時，需要下列範例中所示的 ATL 標頭檔 `#include` 行。 若要修正這個錯誤，請將下列其中一個屬性套用至介面定義，使 `IEvents` （事件介面）成為 COM 介面： [object](../../windows/object-cpp.md)、[雙重](../../windows/dual.md)[或分配介面。](../../windows/dispinterface.md)

如果介面來自 MIDL 產生的標頭檔，則編譯器不會將它辨識為 COM 介面。

下列範例會產生 C3706：

```cpp
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
