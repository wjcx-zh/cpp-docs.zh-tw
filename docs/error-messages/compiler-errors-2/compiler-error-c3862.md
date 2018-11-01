---
title: 編譯器錯誤 C3862
ms.date: 11/04/2016
f1_keywords:
- C3862
helpviewer_keywords:
- C3862
ms.assetid: ba547366-4189-4077-8c00-ab45e08a9533
ms.openlocfilehash: 2ba130862b1debbe2991ca7cbcae50192f900cd8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50446237"
---
# <a name="compiler-error-c3862"></a>編譯器錯誤 C3862

> '*函式*': 無法編譯 unmanaged 函式使用 /clr: pure 或 /clr: safe

## <a name="remarks"></a>備註

**/Clr: pure**並 **/clr: safe**編譯器選項是在 Visual Studio 2015 中已被取代，而且不支援的 Visual Studio 2017 中。

編譯 **/clr: pure**或是 **/clr: safe**會產生 MSIL 僅映像，映像使用任何原生 (unmanaged) 程式碼。  因此，您無法使用`unmanaged`中的 pragma **/clr: pure**或 **/clr: safe**編譯。

如需詳細資訊，請參閱 < [/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)並[managed、 unmanaged](../../preprocessor/managed-unmanaged.md)。

## <a name="example"></a>範例

下列範例會產生 C3862:

```cpp
// C3862.cpp
// compile with: /clr:pure /c
#pragma unmanaged
void f() {}   // C3862
```