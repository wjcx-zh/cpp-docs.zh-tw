---
title: "嚴重錯誤 C1071 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1071"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1071"
ms.assetid: 489f1786-370e-4ecd-af67-538fe6e5bd4e
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 嚴重錯誤 C1071
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在註解中找到未預期的檔案結尾  
  
 編譯器在掃描一個註解時遇到檔案的結尾。  
  
### 若要修正，請檢查下列可能原因  
  
1.  遺漏了註解結束字元 \(\*\/\)。  
  
2.  在原始程式檔最後一行的註解後面遺漏了換行字元。  
  
 下列範例會產生 C1071：  
  
```  
// C1071.cpp  
int main() {  
}  
  
/* this comment is fine */  
/* forgot the closing tag        // C1071  
```