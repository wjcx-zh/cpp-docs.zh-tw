---
title: "編譯器錯誤 C2706 | Microsoft Docs"
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
  - "C2706"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2706"
ms.assetid: e18da924-c42d-4b09-8e29-f4e0382d7dc6
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2706
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不合法的 \_\_except 沒有相符的 \_\_try \(在 \_\_try 區塊中遺漏 '}' ?\)  
  
 編譯器找不到 `__try` 區塊的右括號。  
  
 下列範例會產生 C2706：  
  
```  
// C2706.cpp  
int main() {  
   __try {  
      void f();  
   // C2706  } missing here  
   __except(GetExceptionCode() == 0x0) {  
   }  
}  
```