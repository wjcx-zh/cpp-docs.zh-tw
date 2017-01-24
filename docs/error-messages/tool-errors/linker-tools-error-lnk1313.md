---
title: "連結器工具錯誤 LNK1313 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1313"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1313"
ms.assetid: 5df0b72e-bb3f-428c-8d84-6084238f9827
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具錯誤 LNK1313
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

偵測到 ijw\/native 模組；無法與純模組連結  
  
 目前的 Visual C\+\+ 版本不支援將原生或混合的受管理\/原生 .obj 檔與使用 **\/clr:pure** 所編譯的 .obj 檔案連結。  
  
## 範例  
  
```  
// LNK1313.cpp  
// compile with: /c /clr:pure  
// a pure module  
int main() {}  
```  
  
## 範例  
  
```  
// LNK1313_b.cpp  
// compile with: /c /clr  
// an IJW module  
void test(){}  
```  
  
## 範例  
 下列範例會產生 LNK1313。  
  
```  
// LNK1313_c.cpp  
// compile with: /link LNK1313.obj LNK1313_b.obj  
// LNK1313 warning expected  
```