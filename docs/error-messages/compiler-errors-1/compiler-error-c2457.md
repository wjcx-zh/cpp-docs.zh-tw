---
title: 編譯器錯誤 C2457
ms.date: 11/04/2016
f1_keywords:
- C2457
helpviewer_keywords:
- C2457
ms.assetid: 347e169d-23ad-434f-8836-5b09b53980ff
ms.openlocfilehash: a08ac9f9cfbc332b90ad16c663349ee227427278
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50446629"
---
# <a name="compiler-error-c2457"></a>編譯器錯誤 C2457

> '*巨集*': 預先定義的巨集不能出現在函式主體之外

您嘗試使用預先定義的巨集，例如[ &#95;&#95;函式&#95;&#95;](../../preprocessor/predefined-macros.md)，在全域空間中。

## <a name="example"></a>範例

下列範例會產生 C2457，並也會示範正確使用方式：

```cpp
// C2457.cpp
#include <stdio.h>

__FUNCTION__;   // C2457, cannot be global

int main()
{
    printf_s("\n%s", __FUNCTION__);   // OK
}
```