---
title: 編譯器警告 (層級 1) C4627
ms.date: 09/09/2018
f1_keywords:
- C4627
helpviewer_keywords:
- C4627
ms.assetid: 8840f3e6-b496-423a-8635-eb55d5f854a2
ms.openlocfilehash: e833141020de1aef51a1ea3823dea86b024e077d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50542385"
---
# <a name="compiler-warning-level-1-c4627"></a>編譯器警告 (層級 1) C4627

> '*header_file*': 尋找先行編譯標頭檔使用時，略過

如果目前的原始程式檔已[/Yu\(使用先行編譯標頭檔)](../../build/reference/yu-use-precompiled-header-file.md)選項集，則編譯器會忽略檔案中的所有項目之前會包含先行編譯標頭。 警告**C4627**如果，在 Visual Studio 2015 和更早版本中就會產生*header_file*包含先行編譯標頭檔中，而且如果先行編譯標頭也未包含*header_file*。

## <a name="example"></a>範例

這個範例會示範如何可能會發生錯誤，並示範如何修正此問題：

```cpp
// c4627.cpp
#include <iostream>       // C4627 - iostream not included by pch.h
#include "pch.h"          // precompiled header file that does not include iostream
// #include <iostream>    // To fix, move the iostream header include here from above
int main()
{
    std::cout << "std::cout is defined!\n";
}
```

## <a name="see-also"></a>另請參閱

[建立先行編譯標頭檔](../../build/reference/creating-precompiled-header-files.md)
