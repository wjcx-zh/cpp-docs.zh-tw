---
title: 編譯器錯誤 C2472
ms.date: 11/04/2016
f1_keywords:
- C2472
helpviewer_keywords:
- C2472
ms.assetid: 3b36bcdc-2ba5-4357-ab88-7545ba0551cd
ms.openlocfilehash: d2f104bb61915f8d19d5fff22eea17929c0e8d74
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350906"
---
# <a name="compiler-error-c2472"></a>編譯器錯誤 C2472

> '*函式*' 不能在 managed 程式碼產生: '*訊息*'; 以 /clr 編譯以便產生混合的影像

## <a name="remarks"></a>備註

在純粹 Common Language Runtime (CLR) 環境內使用 Managed 程式碼不支援的類型時，會發生這個錯誤。 請使用 **/clr** 進行編譯，來解決這個錯誤。

**/Clr: pure**並 **/clr: safe**編譯器選項是在 Visual Studio 2015 中已被取代，而且不支援的 Visual Studio 2017 中。

## <a name="example"></a>範例

下列範例會產生 C2472。

```cpp
// C2472.cpp
// compile with: /clr:pure
// C2472 expected

#include <cstdlib>

int main()
{
   int * __ptr32 p32;
   int * __ptr64 p64;

   p32 = (int * __ptr32)malloc(4);
   p64 = p32;
}
```

## <a name="see-also"></a>另請參閱

- [/clr (通用語言執行平台編譯)](../../build/reference/clr-common-language-runtime-compilation.md)
