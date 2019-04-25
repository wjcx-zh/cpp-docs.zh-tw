---
title: 編譯器錯誤 C2434
ms.date: 11/04/2016
f1_keywords:
- C2434
helpviewer_keywords:
- C2434
ms.assetid: 01329e26-7c74-4219-b74f-69e3a40c9738
ms.openlocfilehash: c73a8d4fcde945ddf2495cc2d0d7dc47216f2db3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166330"
---
# <a name="compiler-error-c2434"></a>編譯器錯誤 C2434

> '*符號*': 以 __declspec （process） 宣告的符號無法以動態方式初始化在 /clr: pure 模式

## <a name="remarks"></a>備註

**/Clr: pure**並 **/clr: safe**編譯器選項是在 Visual Studio 2015 中已被取代，而且不支援的 Visual Studio 2017 中。

不可能以動態方式初始化處理序專屬變數下的 **/clr: pure**。 如需詳細資訊，請參閱 < [/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)並[程序](../../cpp/process.md)。

## <a name="example"></a>範例

下列範例會產生 C2434。 若要修正此問題，請使用常數來初始化`process`變數。

```cpp
// C2434.cpp
// compile with: /clr:pure /c
int f() { return 0; }
__declspec(process) int i = f();   // C2434
__declspec(process) int i2 = 0;   // OK
```