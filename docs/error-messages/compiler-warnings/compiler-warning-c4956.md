---
title: 編譯器警告 C4956
ms.date: 11/04/2016
f1_keywords:
- C4956
helpviewer_keywords:
- C4956
ms.assetid: 9154f2d1-d49f-4e07-90d2-0e9bc028011a
ms.openlocfilehash: 474bdfa6eb670f39a2876b0c1490e7254cf216e7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164896"
---
# <a name="compiler-warning-c4956"></a>編譯器警告 C4956

> '*type*'：這個類型無法驗證

## <a name="remarks"></a>備註

指定 [/clr:safe](../../build/reference/clr-common-language-runtime-compilation.md) 且您的程式碼包含無法驗證的類型時，就會產生這個警告。 **/Clr： safe**編譯器選項在 Visual Studio 2015 中已被取代，在 Visual Studio 2017 中不支援。

如需詳細資訊，請參閱[單純和可C++驗證的程式碼（/cli）](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。

發出這個警告即表示發生錯誤，而且可以使用 [warning](../../preprocessor/warning.md) pragma 或 [/wd](../../build/reference/compiler-option-warning-level.md) 編譯器選項予以停用。

## <a name="example"></a>範例

下列範例會產生 C4956：

```cpp
// C4956.cpp
// compile with: /clr:safe
int* p;   // C4956
```
