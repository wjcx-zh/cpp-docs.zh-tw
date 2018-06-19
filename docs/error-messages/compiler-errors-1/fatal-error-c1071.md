---
title: 嚴重錯誤 C1071 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1071
dev_langs:
- C++
helpviewer_keywords:
- C1071
ms.assetid: 489f1786-370e-4ecd-af67-538fe6e5bd4e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9cef64c327c0fd3b668947de52f2776cca2833c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33227190"
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