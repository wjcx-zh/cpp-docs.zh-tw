---
title: 連結器工具錯誤 LNK1140
ms.date: 11/04/2016
f1_keywords:
- LNK1140
helpviewer_keywords:
- LNK1140
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
ms.openlocfilehash: 845c796ee9611e921e2fd1707b9bb956ab62a5ac
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195262"
---
# <a name="linker-tools-error-lnk1140"></a>連結器工具錯誤 LNK1140

程式資料庫的模組太多;使用/PDB 連結：無

專案包含4096個以上的模組。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 使用[/pdb： NONE](../../build/reference/pdb-use-program-database.md)重新連結。

1. 編譯某些模組，而不進行調試資訊。

1. 減少模組的數目。
