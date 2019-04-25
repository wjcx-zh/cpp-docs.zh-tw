---
title: 編譯器警告 C4959
ms.date: 11/04/2016
f1_keywords:
- C4959
helpviewer_keywords:
- C4959
ms.assetid: 3a128f3e-4d8a-4565-ba1a-5d32fdeb5982
ms.openlocfilehash: 646347dec7bc2bac7fa73c8f754d2f9549cb2ba6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388655"
---
# <a name="compiler-warning-c4959"></a>編譯器警告 C4959

> 無法定義 unmanaged 的結構 '*型別*' /clr: safe 中因為存取它的成員會產生無法驗證的程式碼

## <a name="remarks"></a>備註

存取 Unmanaged 類型的成員將會產生無法驗證的 (peverify.exe) 映像。

如需詳細資訊，請參閱 <<c0> [ 純粹的和可驗證程式碼 (C++/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。</c0>

**/Clr: safe**編譯器選項是在 Visual Studio 2015 中已被取代，不支援的 Visual Studio 2017 中。

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