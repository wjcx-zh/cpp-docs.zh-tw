---
title: 連結器工具錯誤 LNK1201
ms.date: 11/04/2016
f1_keywords:
- LNK1201
helpviewer_keywords:
- LNK1201
ms.assetid: 64c3f496-a428-4b54-981e-faa82ef9c8a1
ms.openlocfilehash: c5cbb9a7159a976ad0f96f46462669cff7b19f26
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62213260"
---
# <a name="linker-tools-error-lnk1201"></a>連結器工具錯誤 LNK1201

寫入程式資料庫 'filename'; 時發生錯誤檢查有足夠的磁碟空間、 無效的路徑或沒有足夠的權限

連結無法寫入輸出檔的程式資料庫 (PDB)。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正

1. Soubor je poškozen。 刪除 PDB 檔案並重新連結。

1. 磁碟空間不足，無法寫入檔案。

1. 無法使用時，可能是因為網路問題的磁碟機。

1. 偵錯工具仍在您嘗試連結的程式。

1. 堆積空間不足。  請參閱[C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md)如需詳細資訊。