---
title: 編譯器錯誤 C2457
ms.date: 11/04/2016
f1_keywords:
- C2457
helpviewer_keywords:
- C2457
ms.assetid: 347e169d-23ad-434f-8836-5b09b53980ff
ms.openlocfilehash: 40e666b1f2b566ca6309ee7759452647f8101a38
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205240"
---
# <a name="compiler-error-c2457"></a>編譯器錯誤 C2457

> '*宏*'：預先定義的宏不能出現在函式主體之外

您嘗試在全域空間中使用預先定義的宏，例如[ &#95; &#95;FUNCTION&#95;](../../preprocessor/predefined-macros.md)。

## <a name="example"></a>範例

下列範例會產生 C2457，而且也會顯示正確的使用方式：

```cpp
// C2457.cpp
#include <stdio.h>

__FUNCTION__;   // C2457, cannot be global

int main()
{
    printf_s("\n%s", __FUNCTION__);   // OK
}
```
