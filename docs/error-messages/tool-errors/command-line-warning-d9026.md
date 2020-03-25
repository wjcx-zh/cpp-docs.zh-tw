---
title: 命令列警告 D9026
ms.date: 11/04/2016
f1_keywords:
- D9026
helpviewer_keywords:
- D9026
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
ms.openlocfilehash: 59dfcdc97fb9caf60a018cb20583ee6fca3dcb27
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196699"
---
# <a name="command-line-warning-d9026"></a>命令列警告 D9026

選項適用于整個命令列

指定 filename 之後，在命令上指定了選項。 此選項已套用至其前面的檔案。

例如，在命令中

```
CL verdi.c /G5 puccini.c
```

將使用/G5 選項（而非/G4 預設值）來編譯 VERDI 檔案。

這種行為不同于先前的某些版本，只會套用 filename 前面指定的選項，因此會使用/G4 來編譯 VERDI，並使用/G5. 編譯 PUCCINI。 c
