---
title: 編譯器警告 C4956
ms.date: 11/04/2016
f1_keywords:
- C4956
helpviewer_keywords:
- C4956
ms.assetid: 9154f2d1-d49f-4e07-90d2-0e9bc028011a
ms.openlocfilehash: c15de8b22f56a2555cc763a45153139b1df01a31
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449097"
---
# <a name="compiler-warning-c4956"></a>編譯器警告 C4956

> '*型別*': 此類型不是可驗證

## <a name="remarks"></a>備註

指定 [/clr:safe](../../build/reference/clr-common-language-runtime-compilation.md) 且您的程式碼包含無法驗證的類型時，就會產生這個警告。 **/Clr: safe**編譯器選項是在 Visual Studio 2015 中已被取代，不支援的 Visual Studio 2017 中。

如需詳細資訊，請參閱 <<c0> [ 純粹的和可驗證程式碼 (C + + /cli CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。

發出這個警告即表示發生錯誤，而且可以使用 [warning](../../preprocessor/warning.md) pragma 或 [/wd](../../build/reference/compiler-option-warning-level.md) 編譯器選項予以停用。

## <a name="example"></a>範例

下列範例會產生 C4956：

```cpp
// C4956.cpp
// compile with: /clr:safe
int* p;   // C4956
```