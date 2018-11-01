---
title: 命令列警告 D9026
ms.date: 11/04/2016
f1_keywords:
- D9026
helpviewer_keywords:
- D9026
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
ms.openlocfilehash: 3fd8d442dfabaf2f03d8b564c9fdfb1537f6ff28
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599429"
---
# <a name="command-line-warning-d9026"></a>命令列警告 D9026

選項會套用至整個命令列

指定檔案名稱之後命令上指定的選項。 選項已套用到它前面的檔案。

例如，在命令中

```
CL verdi.c /G5 puccini.c
```

將使用 /G5 選項，而不是 /g4 是預設會編譯 /g4 的檔案。

此行為是不同的一些先前的版本，才要編譯的檔名，導致 /g4 之前所指定的選項，使用/第 4 代 」 和 「 而 puccini.c 會以要編譯使用 /G5 套用。