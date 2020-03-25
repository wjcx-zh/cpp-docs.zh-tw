---
title: 編譯器警告 C4959
ms.date: 11/04/2016
f1_keywords:
- C4959
helpviewer_keywords:
- C4959
ms.assetid: 3a128f3e-4d8a-4565-ba1a-5d32fdeb5982
ms.openlocfilehash: 13d2ed705bff7b42eb3c348692a5829bd54158b0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164868"
---
# <a name="compiler-warning-c4959"></a>編譯器警告 C4959

> 無法在/clr： safe 中定義非受控結構 '*type*'，因為存取它的成員會產生無法驗證的程式碼

## <a name="remarks"></a>備註

存取 Unmanaged 類型的成員將會產生無法驗證的 (peverify.exe) 映像。

如需詳細資訊，請參閱[單純和可C++驗證的程式碼（/cli）](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。

**/Clr： safe**編譯器選項在 Visual Studio 2015 中已被取代，在 Visual Studio 2017 中不支援。

發出這個警告即表示發生錯誤，而且可以使用 [warning](../../preprocessor/warning.md) pragma 或 [/wd](../../build/reference/compiler-option-warning-level.md) 編譯器選項予以停用。

## <a name="example"></a>範例

下列範例會產生 C4959：

```cpp
// C4959.cpp
// compile with: /clr:safe

// Uncomment the following line to resolve.
// #pragma warning( disable : 4959 )
struct X {
   int data;
};

int main() {
   X x;
   x.data = 10;   // C4959
}
```
