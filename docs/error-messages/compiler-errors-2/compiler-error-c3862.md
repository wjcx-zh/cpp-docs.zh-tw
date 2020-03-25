---
title: 編譯器錯誤 C3862
ms.date: 11/04/2016
f1_keywords:
- C3862
helpviewer_keywords:
- C3862
ms.assetid: ba547366-4189-4077-8c00-ab45e08a9533
ms.openlocfilehash: 0b9c1e1213949d7d700094caa6687232df881ce6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165479"
---
# <a name="compiler-error-c3862"></a>編譯器錯誤 C3862

> '*function*'：無法使用/clr： pure 或/clr： safe 編譯非受控函式

## <a name="remarks"></a>備註

**/Clr： pure**和 **/clr： safe**編譯器選項在 Visual Studio 2015 中已被取代，在 Visual Studio 2017 中不支援。

使用 **/clr： pure**或 **/clr： safe**進行編譯時，將會產生僅限 MSIL 的映射，也就是沒有原生（非受控）程式碼的影像。  因此，您無法在 **/clr： pure**或 **/clr： safe**編譯中使用 `unmanaged` pragma。

如需詳細資訊，請參閱[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)和[managed、非受控](../../preprocessor/managed-unmanaged.md)。

## <a name="example"></a>範例

下列範例會產生 C3862：

```cpp
// C3862.cpp
// compile with: /clr:pure /c
#pragma unmanaged
void f() {}   // C3862
```
