---
title: 連結器工具錯誤 LNK1106
ms.date: 11/04/2016
f1_keywords:
- LNK1106
helpviewer_keywords:
- LNK1106
ms.assetid: 528f7e65-04be-4966-b8af-9276837c7cda
ms.openlocfilehash: 091d4e173bfb2eff8ffee2b5c30647f4d5e3bc04
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195366"
---
# <a name="linker-tools-error-lnk1106"></a>連結器工具錯誤 LNK1106

不正確檔案或磁片已滿：無法搜尋位置

此工具無法讀取或寫入記憶體對應檔案中的 `location`。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 磁片已滿。

   請釋放一些空間，然後再連結一次。

1. 嘗試透過網路連結。

   某些網路並不完全支援連結器所使用的記憶體對應檔案。 請嘗試在您的本機磁片上連結。

1. 磁片上的區塊錯誤。

   雖然作業系統和磁片硬體應該偵測到這類錯誤，但您可能會想要執行磁片檢查程式。

1. 堆積空間不足。

   如需詳細資訊，請參閱[C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) 。
