---
title: 編譯器錯誤 C3706
ms.date: 11/04/2016
f1_keywords:
- C3706
helpviewer_keywords:
- C3706
ms.assetid: d20a33eb-d625-46c5-ac87-32075a590d07
ms.openlocfilehash: 461850b2c1686343f23c77274b8fb2ca6fd9071e
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508005"
---
# <a name="compiler-error-c3706"></a>編譯器錯誤 C3706

' function '：必須是用來引發 COM 事件的 COM 介面

您用來引發 COM 事件的事件介面必須是 COM 介面。 在這種情況下，應該使用 Visual C++ 屬性來定義介面，或使用 [#import](../../preprocessor/hash-import-directive-cpp.md) 從具有 #import 之 embedded_idl 屬性的類型程式庫匯入。

請注意， `#include` 下列範例中所示的 ATL 標頭檔行是使用 COM 事件的必要程式碼。 若要修正這個錯誤，請將 `IEvents` 下列其中一個屬性套用至介面定義，以將事件介面 () COM 介面： [object](../../windows/attributes/object-cpp.md)、 [雙重](../../windows/attributes/dual.md)或分派 [介面](../../windows/attributes/dispinterface.md)。

如果介面來自 MIDL 所產生的標頭檔，編譯器將不會將它辨識為 COM 介面。

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
