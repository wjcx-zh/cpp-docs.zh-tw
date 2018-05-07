---
title: 連結器工具錯誤 LNK1201 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1201
dev_langs:
- C++
helpviewer_keywords:
- LNK1201
ms.assetid: 64c3f496-a428-4b54-981e-faa82ef9c8a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ad83fecfe4df211cb7c5f301626454b5d2c9e47
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1201"></a>連結器工具錯誤 LNK1201
寫入程式資料庫 'filename'; 時發生錯誤檢查有足夠的磁碟空間、 無效路徑或特殊權限不足  
  
 連結無法寫入輸出檔的程式資料庫 (PDB)。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正  
  
1.  檔案已損毀。 刪除 PDB 檔案並重新連結。  
  
2.  磁碟空間不足，無法寫入檔案。  
  
3.  無法使用，可能是因為網路問題的磁碟機。  
  
4.  您嘗試連結的程式作用中偵錯工具。  
  
5.  堆積空間不足。  請參閱[C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md)如需詳細資訊。