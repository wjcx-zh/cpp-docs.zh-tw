---
title: 編譯器錯誤 C2441
ms.date: 11/04/2016
f1_keywords:
- C2441
helpviewer_keywords:
- C2441
ms.assetid: ffbd6573-777a-48dd-892f-5cf4a758dcab
ms.openlocfilehash: 7fcf333f62253eb676c0f0ada1c927ab962ae1ca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551247"
---
# <a name="compiler-error-c2441"></a>編譯器錯誤 C2441

> '*變數*': 以 __declspec （process） 宣告的符號必須是在 /clr: pure 模式

## <a name="remarks"></a>備註

**/Clr: pure**並 **/clr: safe**編譯器選項是在 Visual Studio 2015 中已被取代，而且不支援的 Visual Studio 2017 中。

根據預設，變數是每個應用程式網域底下 **/clr: pure**。 變數標示`__declspec(process)`底下 **/clr: pure**很容易發生錯誤，如果一個應用程式定義域中進行修改，但在另一個讀取。

因此，編譯器會強制每個變數的程序`const`底下 **/clr: pure**，只在所有應用程式定義域中的進行這些讀取。

如需詳細資訊，請參閱 <<c0> [ 程序](../../cpp/process.md)並[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="example"></a>範例

下列範例會產生 C2441。

```cpp
// C2441.cpp
// compile with: /clr:pure /c
__declspec(process) int i;   // C2441
__declspec(process) const int j = 0;   // OK
```