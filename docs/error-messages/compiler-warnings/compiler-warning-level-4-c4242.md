---
title: "編譯器警告 (層級 4) C4242 | Microsoft Docs"
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
  - "C4242"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4242"
ms.assetid: 8df742e1-fbf1-42f3-8e93-c0e1c222dc7e
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4242
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 將 'type1' 轉換為 'type2'，資料可能遺失  
  
 型別是不同的。  型別轉換可能會造成資料的遺失。  編譯器進行型別轉換。  
  
 此警告在預設情況下為關閉的。  如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 如需 C4242 的額外資訊，請參閱[常見編譯器錯誤](http://msdn.microsoft.com/library/windows/desktop/aa384160)。  
  
 下列範例會產生 C4242：  
  
```  
// C4242.cpp  
// compile with: /W4  
#pragma warning(4:4242)  
int func() {  
   return 0;  
}  
  
int main() {  
   char a;  
   a = func();   // C4242, return type and variable type do not match  
}  
```