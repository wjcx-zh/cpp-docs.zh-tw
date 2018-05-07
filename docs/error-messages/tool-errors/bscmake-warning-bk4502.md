---
title: BSCMAKE 警告 BK4502 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK4502
- BK1513
dev_langs:
- C++
helpviewer_keywords:
- BK1513
- BK4502
ms.assetid: ee412ec8-df03-4cdb-91ee-5d609ded8691
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ed7145c28b10885dc6edf0c399478aea4503ca0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="bscmake-warning-bk4502"></a>BSCMAKE 警告 BK4502
截斷。SBR 檔案 'filename' 不在檔案名稱  
  
 更新期間指定了零長度.sbr 檔案原本不.bsc 檔的一部分。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正  
  
1.  指定的檔案名稱錯誤。  
  
2.  刪除的檔案。 (錯誤[BK1513](../../error-messages/tool-errors/bscmake-error-bk1513.md)結果。)  
  
3.  檔案已損毀，需要執行完整建置 BSCMAKE。