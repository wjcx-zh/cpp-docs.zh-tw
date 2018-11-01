---
title: 資源編譯器嚴重錯誤 RW1025
ms.date: 11/04/2016
f1_keywords:
- RW1025
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
ms.openlocfilehash: 8ecfc11f5cc991294d966a4b6c75d8da6669d5b1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575678"
---
# <a name="resource-compiler-fatal-error-rw1025"></a>資源編譯器嚴重錯誤 RW1025

堆積記憶體不足

檢查有可能佔用太多空間的常駐記憶體的軟體。 若要了解您有多少記憶體使用 CHKDSK 程式。

如果您要建立大型的資源檔，請將資源指令碼分成兩個檔案。 建立兩個.res 檔案之後, 使用 MS-DOS 命令列將它們聯結在一起：

```
copy first.res /b + second.res /b full.res
```