---
title: "資源編譯器錯誤 RC2001 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- RC2001
dev_langs:
- C++
helpviewer_keywords:
- RC2001
ms.assetid: 92bfb4c0-1879-4606-bb9f-ef7368707b4a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7c04110898780495f918c1e37c0068daead340a4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-error-rc2001"></a>資源編譯器錯誤 RC2001
常數中的新行  
  
 字串常數繼續第二行，而不是反斜線 (**\\**) 或左右雙引號內 (**"**)。  
  
 若要中斷分成兩行原始程式檔中的字串常數，執行下列其中一項：  
  
-   結尾的第一行以反斜線，行接續字元。  
  
-   關閉第一個列中利用雙引號字串並在下一行的字串以開啟另一個引號。  
  
 不足結束 \n、 內嵌字串常數中的新行字元的逸出序列的第一行。