---
title: 連結器工具錯誤 LNK1313
ms.date: 11/04/2016
f1_keywords:
- LNK1313
helpviewer_keywords:
- LNK1313
ms.assetid: 5df0b72e-bb3f-428c-8d84-6084238f9827
ms.openlocfilehash: 03ff61a1f3501b3ea106138e957a657ed064e645
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90683438"
---
# <a name="linker-tools-error-lnk1313"></a>連結器工具錯誤 LNK1313

> 偵測到 ijw/native 模組；無法與純模組連結

## <a name="remarks"></a>備註

目前版本的 Visual C++ 不支援將原生或混合的 managed/native .obj 檔案與以 **/clr： pure**編譯的 .obj 檔案連結。

**/Clr： pure**編譯器選項在 Visual Studio 2015 中已被取代，Visual Studio 2017 中不支援。

## <a name="examples"></a>範例

```cpp
// LNK1313.cpp
// compile with: /c /clr:pure
// a pure module
int main() {}
```

```cpp
// LNK1313_b.cpp
// compile with: /c /clr
// an IJW module
void test(){}
```

下列範例會產生 LNK1313。

```cpp
// LNK1313_c.cpp
// compile with: /link LNK1313.obj LNK1313_b.obj
// LNK1313 warning expected
```
