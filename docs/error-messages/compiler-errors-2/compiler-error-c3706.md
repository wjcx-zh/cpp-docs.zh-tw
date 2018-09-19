---
title: 編譯器錯誤 C3706 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3706
dev_langs:
- C++
helpviewer_keywords:
- C3706
ms.assetid: d20a33eb-d625-46c5-ac87-32075a590d07
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbebf5752a9ed42ea4af8d3a13e45c78fc1753ec
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110506"
---
# <a name="compiler-error-c3706"></a>編譯器錯誤 C3706

'function': 必須是 COM 介面來引發 COM 事件

您用來引發 COM 事件的事件介面必須是 COM 介面。 在此情況下，介面應該使用 Visual c + + 屬性會定義或使用 匯入[#import](../../preprocessor/hash-import-directive-cpp.md)從 #import 的 embedded_idl 屬性的型別程式庫。

請注意，`#include`行的下列範例所示的 ATL 標頭檔，才能使用 COM 事件。 若要修正這個錯誤，請`IEvents`（事件介面） 的 COM 介面，藉由套用下列其中一個屬性至介面定義：[物件](../../windows/object-cpp.md)，[雙重](../../windows/dual.md)，或[dispinterface](../../windows/dispinterface.md)。

如果介面是由 MIDL 所產生的標頭檔，則編譯器不會將它視為 COM 介面。

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