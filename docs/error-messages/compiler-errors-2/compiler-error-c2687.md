---
title: "編譯器錯誤 C2687 | Microsoft Docs"
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
  - "C2687"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2687"
ms.assetid: 1d24b24a-cd0f-41cc-975c-b08dcfb7f402
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2687
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type' : 例外狀況宣告不能是 'void' 或代表不完整的型別或是對不完整型別的指標或參考  
  
 若要使型別成為例外狀況宣告的一部分，則您必須定義它，且它不可以是 void。  
  
 下列範例會產生 C2687：  
  
```  
// C2687.cpp  
class C;  
  
int main() {  
   try {}  
   catch (C) {}   // C2687 error  
}  
```  
  
 可能的解決方案：  
  
```  
// C2687b.cpp  
// compile with: /EHsc  
class C {};  
  
int main() {  
   try {}  
   catch (C) {}  
}  
```