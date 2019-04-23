---
title: 編譯器警告 C4972
ms.date: 11/04/2016
f1_keywords:
- C4972
helpviewer_keywords:
- C4972
ms.assetid: d18e8e65-b2ef-4d75-a207-fbd0c17c9060
ms.openlocfilehash: 7c58258298fb91d04014e719732135a1f33f13b6
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59777896"
---
# <a name="compiler-warning-c4972"></a>編譯器警告 C4972

直接修改或將 Unbox 作業的結果視為左值，將無法驗證

對實值類型的控制代碼取值 (也稱為 Unboxing)，然後指派給它，這個作業無法驗證。

如需詳細資訊，請參閱 [Boxing](../../extensions/boxing-cpp-component-extensions.md)中定義的介面的私用 C++ 專屬實作。

## <a name="example"></a>範例

下列範例會產生 C4972。

```
// C4972.cpp
// compile with: /clr:safe
using namespace System;
ref struct R {
   int ^ p;   // a value type
};

int main() {
   R ^ r = gcnew R;
   *(r->p) = 10;   // C4972

   // OK
   r->p = 10;
   Console::WriteLine( r->p );
   Console::WriteLine( *(r->p) );
}
```