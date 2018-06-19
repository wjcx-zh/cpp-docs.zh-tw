---
title: NMAKE 嚴重錯誤 U1033 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1033
dev_langs:
- C++
helpviewer_keywords:
- U1033
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1d39d4c35ec66d405d51d601b7c5d2b2ab37b02
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33319266"
---
# <a name="nmake-fatal-error-u1033"></a>NMAKE 嚴重錯誤 U1033
語法錯誤: 'string' 預期  
  
 字串不是 makefile 的有效語法的一部分。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正  
  
1.  如果關閉設定的角括號 (**<<**) 的內嵌檔不是在一行的開頭，就會發生下列錯誤：  
  
    ```  
    syntax error : 'EOF' unexpected  
    ```  
  
2.  Makefile 中的巨集定義如果包含等號 (**=**) 沒有前面名稱，或如果所定義的名稱是展開為無巨集，就會發生下列錯誤：  
  
    ```  
    syntax error : '=' unexpected  
    ```  
  
3.  如果分號 (**;**) 工具中的註解資料行中。INI 不在一行的開頭就會發生下列錯誤：  
  
    ```  
    syntax error : ';' unexpected  
    ```  
  
4.  如果已格式化 makefile 的文書處理器，發生下列錯誤：  
  
    ```  
    syntax error : ':' unexpected  
    ```