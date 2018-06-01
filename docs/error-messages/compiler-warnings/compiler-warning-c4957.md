---
title: 編譯器警告 C4957 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4957
dev_langs:
- C++
helpviewer_keywords:
- C4957
ms.assetid: a18c52d4-23e2-44f1-b4b5-f7fa5a7f3987
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 60cf1c03ace94c866b77c5340e2a04a9d8190e4d
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34705214"
---
# <a name="compiler-warning-c4957"></a>編譯器警告 C4957

> '*轉換*': 明確的轉換，從'*cast_from*'to'*cast_to*' 不是可驗證

## <a name="remarks"></a>備註

轉換會產生無法驗證的影像。

部分轉換是安全的 (例如，觸發使用者定義轉換的 `static_cast` 以及 `const_cast`)。 [safe_cast](../../windows/safe-cast-cpp-component-extensions.md) 保證會產生可驗證的程式碼。

如需詳細資訊，請參閱[純粹的和可驗證程式碼 (C + + /CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。

**/Clr: safe**編譯器選項已被取代 Visual Studio 2015 中，在 Visual Studio 2017 中支援。

發出這個警告即表示發生錯誤，而且可以使用 [warning](../../preprocessor/warning.md) pragma 或 [/wd](../../build/reference/compiler-option-warning-level.md) 編譯器選項予以停用。

## <a name="example"></a>範例

下列範例會產生 C4957：

```cpp
// C4957.cpp
// compile with: /clr:safe
// #pragma warning( disable : 4957 )
using namespace System;
int main() {
   Object ^ o = "Hello, World!";
   String ^ s = static_cast<String^>(o);   // C4957
   String ^ s2 = safe_cast<String^>(o);   // OK
}
```