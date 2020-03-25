---
title: BSCMAKE 警告 BK4502
ms.date: 11/04/2016
f1_keywords:
- BK4502
helpviewer_keywords:
- BK4502
ms.assetid: ee412ec8-df03-4cdb-91ee-5d609ded8691
ms.openlocfilehash: 1c5204239909e579fa93006e245e3841b7fb64eb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197453"
---
# <a name="bscmake-warning-bk4502"></a>BSCMAKE 警告 BK4502

去.不在檔案名中的 .SBR 檔案 ' filename '

在更新期間，未指定原本為 .bsc 檔案一部分的長度為零的 .sbr 檔案名。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 指定了錯誤的檔案名。

1. 檔案已刪除。 （ [BK1513](../../error-messages/tool-errors/bscmake-error-bk1513.md)結果時發生錯誤）。

1. 檔案損毀，需要 BSCMAKE 執行完整組建。
