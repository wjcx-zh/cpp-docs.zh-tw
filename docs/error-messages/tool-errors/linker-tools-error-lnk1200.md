---
title: 連結器工具錯誤 LNK1200
ms.date: 11/04/2016
f1_keywords:
- LNK1200
helpviewer_keywords:
- LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
ms.openlocfilehash: 9dcc37bd74a25e29726529346b1578bb8b18ac3e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195132"
---
# <a name="linker-tools-error-lnk1200"></a>連結器工具錯誤 LNK1200

讀取程式資料庫 ' filename ' 時發生錯誤

無法讀取程式資料庫（PDB）。

此錯誤可能是檔案損毀所造成。

如果 `filename` 是物件檔案的 PDB，請使用[/zi](../../build/reference/z7-zi-zi-debug-information-format.md)重新編譯物件檔案。

如果 `filename` 是主要輸出檔的 PDB，而且在累加連結期間發生此錯誤，請刪除 PDB 並重新連結。
