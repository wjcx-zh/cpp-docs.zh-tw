---
title: 編譯器警告 (層級 4) C4400
ms.date: 11/04/2016
f1_keywords:
- C4400
helpviewer_keywords:
- C4400
ms.assetid: f135fe98-4f92-4e07-9d71-2621b36ee755
ms.openlocfilehash: 3f04bd30c4d390cecfa7e4e636f1a3771f26cfff
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990856"
---
# <a name="compiler-warning-level-4-c4400"></a>編譯器警告 (層級 4) C4400

' type '：不支援此類型的 const/volatile 限定詞

[Const](../../cpp/const-cpp.md)和[volatile](../../cpp/volatile-cpp.md)限定詞不會與 common language runtime 類型的變數搭配使用。

## <a name="example"></a>範例

下列範例會產生 C4400。

```cpp
// C4400.cpp
// compile with: /clr /W4
// C4401 expected
using namespace System;
#pragma warning (disable : 4101)
int main() {
   const String^ str;   // C4400
   volatile String^ str2;   // C4400
}
```
