---
title: 連結器工具錯誤 LNK1140 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1140
dev_langs:
- C++
helpviewer_keywords:
- LNK1140
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f850360bc749a41e548cebae9f58f9fc7d3d420
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044700"
---
# <a name="linker-tools-error-lnk1140"></a>連結器工具錯誤 LNK1140

程式資料庫的模組太多連結，以 /PDB: NONE

此專案包含超過 4096 個模組。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 使用重新連結[/PDB: NONE](../../build/reference/pdb-use-program-database.md)。

1. 某些模組編譯但不偵錯資訊。

1. 降低模組的數目。