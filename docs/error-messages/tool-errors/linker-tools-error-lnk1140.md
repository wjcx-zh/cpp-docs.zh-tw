---
title: 連結器工具錯誤 LNK1140
ms.date: 11/04/2016
f1_keywords:
- LNK1140
helpviewer_keywords:
- LNK1140
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
ms.openlocfilehash: 48c735f29918c4d1caeb15123f7376276d116fb4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482458"
---
# <a name="linker-tools-error-lnk1140"></a>連結器工具錯誤 LNK1140

程式資料庫的模組太多連結，以 /PDB: NONE

此專案包含超過 4096 個模組。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 使用重新連結[/PDB: NONE](../../build/reference/pdb-use-program-database.md)。

1. 某些模組編譯但不偵錯資訊。

1. 降低模組的數目。