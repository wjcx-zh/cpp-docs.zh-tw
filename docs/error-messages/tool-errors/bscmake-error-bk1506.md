---
title: BSCMAKE 錯誤 BK1506
ms.date: 11/04/2016
f1_keywords:
- BK1506
helpviewer_keywords:
- BK1506
ms.assetid: f51f8cea-f8fc-4323-bcf2-b7bd119792ee
ms.openlocfilehash: b272a12e1d729e33794b550c911fd2e56f1af006
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197791"
---
# <a name="bscmake-error-bk1506"></a>BSCMAKE 錯誤 BK1506

無法開啟檔案 ' filename ' [： reason]

BSCMAKE 無法開啟檔案。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 檔案已由另一個進程鎖定。 如果 `reason` 顯示 [**拒絕許可權**]，則表示瀏覽器可能使用檔案。 關閉 [流覽] 視窗，然後重試組建。

1. 完整磁片。

1. 硬體錯誤。

1. 指定的輸出檔與現有子目錄的名稱相同。
