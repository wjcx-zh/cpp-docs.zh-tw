---
title: "連結器工具錯誤 LNK1201 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1201
dev_langs: C++
helpviewer_keywords: LNK1201
ms.assetid: 64c3f496-a428-4b54-981e-faa82ef9c8a1
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 44e2ad811645889cd655bf297f6f8b9492574def
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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