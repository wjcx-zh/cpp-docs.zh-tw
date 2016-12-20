---
title: "編譯器錯誤 C2705 | Microsoft Docs"
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
  - "C2705"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2705"
ms.assetid: 29249ea3-4ea7-4105-944b-bdb83e8d6852
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2705
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'label' : 不合法的跳躍進入 'exception handler block' 範圍  
  
 執行跳至 `try`\/`catch`、`__try`\/`__except`、`__try`\/`__finally` 區塊內的標記。  如需詳細資訊，請參閱[例外狀況處理](../../cpp/exception-handling-in-visual-cpp.md)。  
  
 下列範例會產生 C2705：  
  
```  
// C2705.cpp  
int main() {  
goto trouble;  
   __try {  
      trouble: ;   // C2705  
   }  
   __finally {}  
  
   // try the following line instead  
   // trouble: ;  
}  
```