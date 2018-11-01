---
title: 連結器工具錯誤 LNK1200
ms.date: 11/04/2016
f1_keywords:
- LNK1200
helpviewer_keywords:
- LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
ms.openlocfilehash: c99b25a83836f1ee0bc6ba622e42ea382c377172
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466829"
---
# <a name="linker-tools-error-lnk1200"></a>連結器工具錯誤 LNK1200

讀取程式資料庫 'filename' 時發生錯誤

無法讀取程式資料庫 (PDB)。

此錯誤的原因可能是檔案損毀。

如果`filename`是 PDB 物件檔案，重新編譯物件檔案使用[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)。

如果`filename`PDB 的主要輸出檔，且累加連結期間發生此錯誤，刪除 PDB 並重新連結。