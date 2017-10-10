---
title: "嚴重錯誤 C1071 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1071
dev_langs:
- C++
helpviewer_keywords:
- C1071
ms.assetid: 489f1786-370e-4ecd-af67-538fe6e5bd4e
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: acd48401d3abc17d994e861bf6fb046450d88ca6
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="fatal-error-c1071"></a>嚴重錯誤 C1071
在註解中找到未預期的檔案結尾  
  
 編譯器會掃描註解時遇到檔案結尾。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正  
  
1.  遺漏註解結束字元 (* /)。  
  
2.  遺漏註解的原始程式檔的最後一行後面的新行字元。  
  
 下列範例會產生 C1071:  
  
```  
// C1071.cpp  
int main() {  
}  
  
/* this comment is fine */  
/* forgot the closing tag        // C1071  
```
