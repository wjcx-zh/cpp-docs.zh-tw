---
title: "編譯器錯誤 C2017 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2017"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2017"
ms.assetid: 1083eed9-9906-4a97-883c-54e52d7e82cd
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器錯誤 C2017
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不合法的逸出序列  
  
 逸出序列 \(Escape Sequence，例如 \\t\) 出現在字元或字串常數之外。  
  
 下列範例會產生 C2017：  
  
```  
// C2017.cpp  
int main() {  
   char test1='a'\n;   // C2017  
   char test2='a\n';   // ok  
}  
```  
  
 當字串化運算子搭配包含逸出序列的字串時，可能會發生 C2017。  
  
 下列範例會產生 C2017：  
  
```  
// C2017b.cpp  
#define TestDfn(x) AfxMessageBox(#x)  
TestDfn(CString("\\") + CString(".h\"\n\n"));   // C2017  
```