---
title: "BSCMAKE 警告 BK4502 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- BK4502
- BK1513
dev_langs: C++
helpviewer_keywords:
- BK1513
- BK4502
ms.assetid: ee412ec8-df03-4cdb-91ee-5d609ded8691
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 64b8fc9434f066599e6e33f6a8c9db7b3b1647aa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="bscmake-warning-bk4502"></a>BSCMAKE 警告 BK4502
截斷。SBR 檔案 'filename' 不在檔案名稱  
  
 更新期間指定了零長度.sbr 檔案原本不.bsc 檔的一部分。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正  
  
1.  指定的檔案名稱錯誤。  
  
2.  刪除的檔案。 (錯誤[BK1513](../../error-messages/tool-errors/bscmake-error-bk1513.md)結果。)  
  
3.  檔案已損毀，需要執行完整建置 BSCMAKE。