---
title: 編譯器警告 (層級 1) C4929
ms.date: 11/04/2016
f1_keywords:
- C4929
helpviewer_keywords:
- C4929
ms.assetid: 95f8ab4f-4468-4caa-acd5-8f4592f03b3c
ms.openlocfilehash: 7627acbd359058566a5d14d880f4efb2980a8a93
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90683854"
---
# <a name="compiler-warning-level-1-c4929"></a>編譯器警告 (層級 1) C4929

' file '：類型程式庫包含 union;忽略 ' embedded_idl ' 限定詞

[#Import](../../preprocessor/hash-import-directive-cpp.md)的 embedded_idl 屬性無法套用至類型程式庫，因為類型程式庫中有聯集。 若要解決此警告，請不要使用 embedded_idl。

## <a name="examples"></a>範例

下列範例會定義一個元件。

```cpp
// C4929a.cpp
// compile with: /LD /link /TLBOUT:C4929a.tlb
#include <objbase.h>
[module(name="Test")];
[public, switch_type(short)] typedef union _TD_UNION_TYPE   {
   [case(24)]
      float fM;
   [case(25)]
      double dMN;
   [default]
      int x;
} TD_UNION_TYPE;

[export, public] typedef struct _TDW_TYPE {
   [switch_is(sU)] TD_UNION_TYPE w;
      short sU;
} TD_TYPE;

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface I {
   HRESULT f(TD_TYPE*);
};

[coclass, uuid("00000000-0000-0000-0000-000000000002")]
struct C : I {
   HRESULT f(TD_TYPE*) { return 0; }
};
```

下列範例會產生 C4929。

```cpp
// C4929b.cpp
// compile with: /c /W1
#import "C4929a.tlb" embedded_idl   // C4929
```
