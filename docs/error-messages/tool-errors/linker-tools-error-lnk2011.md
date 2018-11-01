---
title: 連結器工具錯誤 LNK2011
ms.date: 11/04/2016
f1_keywords:
- LNK2011
helpviewer_keywords:
- LNK2011
ms.assetid: 04991ef5-49d5-46c7-8eee-a9d1d3fc541e
ms.openlocfilehash: c8c62da6c1b4ea856f7a0854b998946893f2be63
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518855"
---
# <a name="linker-tools-error-lnk2011"></a>連結器工具錯誤 LNK2011

先行編譯中，未連結的物件映像可能無法執行

如果您使用先行編譯標頭時，連結會需要的所有使用先行編譯標頭建立的物件檔案必須連結中。 如果您有您使用其他原始程式檔中產生先行編譯標頭使用的原始程式檔，您現在必須包含先行編譯標頭以及建立的物件檔案。

比方說，如果您編譯稱為 STUB.cpp 建立先行編譯標頭使用其他原始程式檔的檔案，您必須連結 stub.obj 或您會收到這個錯誤。 在下列的命令列中，行 1 用來建立先行編譯標頭，COMMON.pch PROG1.cpp 與 PROG2.cpp 用於兩個和第三行。 檔案只包含 STUB.cpp`#include`行 (相同`#include`PROG1.cpp 和 PROG2.cpp 行) 只能用來產生先行編譯標頭和。 在最後一行中，STUB.obj 必須連結中以避免 LNK2011。

```
cl /c /Yccommon.h stub.cpp
cl /c /Yucommon.h prog1.cpp
cl /c /Yucommon.h prog2.cpp
link /out:prog.exe stub.obj prog1.obj prog2.obj
```