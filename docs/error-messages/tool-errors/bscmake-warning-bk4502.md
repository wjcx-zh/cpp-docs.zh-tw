---
title: BSCMAKE 警告 BK4502
ms.date: 11/04/2016
f1_keywords:
- BK4502
helpviewer_keywords:
- BK4502
ms.assetid: ee412ec8-df03-4cdb-91ee-5d609ded8691
ms.openlocfilehash: 47bb81827bb6ae1f580ff907be6c0acf7139a29a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57821452"
---
# <a name="bscmake-warning-bk4502"></a>BSCMAKE 警告 BK4502

截斷。SBR 檔案 'filename' 不是在檔案名稱

在更新期間指定原本並不是.bsc 檔的一部分的長度為零的.sbr 檔案。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 指定了錯誤的檔案名稱。

1. 刪除的檔案。 (錯誤[BK1513](../../error-messages/tool-errors/bscmake-error-bk1513.md)結果。)

1. 檔案已損毀，需要執行完整建置 BSCMAKE。