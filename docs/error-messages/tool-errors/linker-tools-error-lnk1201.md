---
title: 連結器工具錯誤 LNK1201
ms.date: 11/04/2016
f1_keywords:
- LNK1201
helpviewer_keywords:
- LNK1201
ms.assetid: 64c3f496-a428-4b54-981e-faa82ef9c8a1
ms.openlocfilehash: 8d02743333c02c7cdff3b75e4a16bfecda442fa9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195106"
---
# <a name="linker-tools-error-lnk1201"></a>連結器工具錯誤 LNK1201

寫入程式資料庫 ' filename ' 時發生錯誤;檢查磁碟空間不足、路徑無效或許可權不足

連結無法寫入輸出檔的程式資料庫（PDB）。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. 檔案已損毀。 刪除 PDB 檔案並重新連結。

1. 磁碟空間不足，無法寫入檔案。

1. 磁片磁碟機無法使用，可能是因為網路問題所致。

1. 偵錯工具在您嘗試連結的程式上為作用中狀態。

1. 堆積空間不足。  如需詳細資訊，請參閱[C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) 。
