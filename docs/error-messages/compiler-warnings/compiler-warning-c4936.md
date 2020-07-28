---
title: 編譯器警告 C4936
ms.date: 11/04/2016
f1_keywords:
- C4936
helpviewer_keywords:
- C4936
ms.assetid: 6676de35-bf1b-4d0b-a70f-b5734130336c
ms.openlocfilehash: 9b1c3d1de662451432fe4fa0f058c503dc1f7b39
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220115"
---
# <a name="compiler-warning-c4936"></a>編譯器警告 C4936

> 以 /clr 或 /clr:pure 編譯時才支援這個 __declspec

## <a name="remarks"></a>備註

**/Clr： pure**編譯器選項在 Visual Studio 2015 中已被取代，在 Visual Studio 2017 中不支援。

使用了修飾詞， **`__declspec`** 但該 **`__declspec`** 修飾詞只有在使用其中一個[/clr](../../build/reference/clr-common-language-runtime-compilation.md)選項進行編譯時才有效。

如需詳細資訊，請參閱 [appdomain](../../cpp/appdomain.md) 和 [處理序](../../cpp/process.md)。

C4936 總是發出錯誤。  您可以使用 [warning](../../preprocessor/warning.md) pragma 來停用 C4936。

## <a name="example"></a>範例

下列範例會產生 C4936：

```cpp
// C4936.cpp
// compile with: /c
// #pragma warning (disable : 4936)
__declspec(process) int i;   // C4936
__declspec(appdomain) int j;   // C4936
```
