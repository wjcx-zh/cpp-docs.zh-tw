---
title: 資源編譯器嚴重錯誤 RW1025 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW1025
dev_langs:
- C++
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2bf7bdeed320c004ffb75fa1d25d9b89147b0c13
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117396"
---
# <a name="resource-compiler-fatal-error-rw1025"></a>資源編譯器嚴重錯誤 RW1025

堆積記憶體不足

檢查有可能佔用太多空間的常駐記憶體的軟體。 若要了解您有多少記憶體使用 CHKDSK 程式。

如果您要建立大型的資源檔，請將資源指令碼分成兩個檔案。 建立兩個.res 檔案之後, 使用 MS-DOS 命令列將它們聯結在一起：

```
copy first.res /b + second.res /b full.res
```