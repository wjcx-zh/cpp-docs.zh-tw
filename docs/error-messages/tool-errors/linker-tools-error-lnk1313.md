---
title: 連結器工具錯誤 LNK1313 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1313
dev_langs:
- C++
helpviewer_keywords:
- LNK1313
ms.assetid: 5df0b72e-bb3f-428c-8d84-6084238f9827
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6a896c8ba012c69755c5292475b2d155ad92066
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34705084"
---
# <a name="linker-tools-error-lnk1313"></a>連結器工具錯誤 LNK1313

> 偵測到 ijw/native 模組；無法與純模組連結

## <a name="remarks"></a>備註

目前版本的 Visual c + + 不支援連結原生或混合的 managed/原生.obj 檔與所編譯的.obj 檔 **/clr: pure**。

**/Clr: pure**編譯器選項已被取代 Visual Studio 2015 中，在 Visual Studio 2017 中支援。

## <a name="example"></a>範例

```cpp
// LNK1313.cpp
// compile with: /c /clr:pure
// a pure module
int main() {}
```

## <a name="example"></a>範例

```cpp
// LNK1313_b.cpp
// compile with: /c /clr
// an IJW module
void test(){}
```

## <a name="example"></a>範例

下列範例會產生 LNK1313。

```cpp
// LNK1313_c.cpp
// compile with: /link LNK1313.obj LNK1313_b.obj
// LNK1313 warning expected
```