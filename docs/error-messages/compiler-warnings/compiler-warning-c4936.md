---
title: 編譯器警告 C4936
ms.date: 11/04/2016
f1_keywords:
- C4936
helpviewer_keywords:
- C4936
ms.assetid: 6676de35-bf1b-4d0b-a70f-b5734130336c
ms.openlocfilehash: bbb69cccbf93be6e97d13db5008780f57e63f9da
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280850"
---
# <a name="compiler-warning-c4936"></a>編譯器警告 C4936

> 以 /clr 或 /clr:pure 編譯時才支援這個 __declspec

## <a name="remarks"></a>備註

**/Clr: pure**編譯器選項是在 Visual Studio 2015 中已被取代，不支援的 Visual Studio 2017 中。

已使用 `__declspec` 修飾詞，但該 `__declspec` 修飾詞僅有在以 [/clr](../../build/reference/clr-common-language-runtime-compilation.md) 選項之一來編譯時才有效。

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