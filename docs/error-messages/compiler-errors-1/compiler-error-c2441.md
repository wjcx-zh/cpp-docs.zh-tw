---
title: 編譯器錯誤 C2441
ms.date: 11/04/2016
f1_keywords:
- C2441
helpviewer_keywords:
- C2441
ms.assetid: ffbd6573-777a-48dd-892f-5cf4a758dcab
ms.openlocfilehash: 4e5d5335717ec77c61069ad08e209f9e1851dc2f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205305"
---
# <a name="compiler-error-c2441"></a>編譯器錯誤 C2441

> '*variable*'：使用 __declspec （process）宣告的符號，在/clr： pure 模式中必須是 const

## <a name="remarks"></a>備註

**/Clr： pure**和 **/clr： safe**編譯器選項在 Visual Studio 2015 中已被取代，在 Visual Studio 2017 中不支援。

根據預設，變數是在 **/clr： pure**底下的每個應用程式域。 在 **/clr： pure**下標記 `__declspec(process)` 的變數，如果在一個應用程式域中修改並讀取另一個，則容易發生錯誤。

因此，編譯器會將每個進程變數強制 `const` 在 **/clr： pure**之下，使其在所有應用程式域中都是唯讀的。

如需詳細資訊，請參閱[process](../../cpp/process.md)和[/Clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)。

## <a name="example"></a>範例

下列範例會產生 C2441。

```cpp
// C2441.cpp
// compile with: /clr:pure /c
__declspec(process) int i;   // C2441
__declspec(process) const int j = 0;   // OK
```
