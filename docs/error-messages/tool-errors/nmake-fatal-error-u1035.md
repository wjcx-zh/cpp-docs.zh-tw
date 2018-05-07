---
title: NMAKE 嚴重錯誤 U1035 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1035
dev_langs:
- C++
helpviewer_keywords:
- U1035
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6bb32f815345b933ad6a65a0c8c1ec8ad59cbe81
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-fatal-error-u1035"></a>NMAKE 嚴重錯誤 U1035
語法錯誤： 必須是 ':' 或 '=' 分隔符號  
  
 冒號 (**:**) 或等號 (**=**) 必須是。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正  
  
1.  冒號未遵循目標。  
  
2.  冒號且不得包含空格 （例如 a:） 後面接著單一字母目標。 NMAKE 當作它的磁碟機規格。  
  
3.  冒號未遵循推斷規則。  
  
4.  巨集定義後面沒有等號。  
  
5.  字元後面接著反斜線 (**\\**) 用來繼續到下一行的命令。  
  
6.  在出現未遵循任何 NMAKE 語法規則的字串。  
  
7.  文書處理器來格式化的 makefile。