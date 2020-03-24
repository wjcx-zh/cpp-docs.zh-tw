---
title: 編譯器錯誤 C2434
ms.date: 11/04/2016
f1_keywords:
- C2434
helpviewer_keywords:
- C2434
ms.assetid: 01329e26-7c74-4219-b74f-69e3a40c9738
ms.openlocfilehash: 869db3b49075fa477860e045e59306e22a381ca4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205459"
---
# <a name="compiler-error-c2434"></a>編譯器錯誤 C2434

> '*symbol*'：以 __declspec （process）宣告的符號無法在/clr： pure 模式中動態初始化

## <a name="remarks"></a>備註

**/Clr： pure**和 **/clr： safe**編譯器選項在 Visual Studio 2015 中已被取代，在 Visual Studio 2017 中不支援。

您無法在 **/clr： pure**下動態初始化個別進程變數。 如需詳細資訊，請參閱[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)和[process](../../cpp/process.md)。

## <a name="example"></a>範例

下列範例會產生 C2434。 若要修正此問題，請使用常數來初始化 `process` 變數。

```cpp
// C2434.cpp
// compile with: /clr:pure /c
int f() { return 0; }
__declspec(process) int i = f();   // C2434
__declspec(process) int i2 = 0;   // OK
```
