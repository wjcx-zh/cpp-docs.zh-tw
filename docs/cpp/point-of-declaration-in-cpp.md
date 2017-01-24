---
title: "C++ 中的宣告點 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "宣告點"
ms.assetid: 92ea8707-80cb-497c-b479-f907b8401859
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++ 中的宣告點
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

名稱會視為在緊接著它的宣告子之後、但是在它的 \(選擇性\) 初始設定式之前宣告   \(如需宣告子的詳細資訊，請參閱[宣告子](http://msdn.microsoft.com/zh-tw/8a7b9b51-92bd-4ac0-b3fe-0c4abe771838)\)。  
  
 請考量以下範例：  
  
```  
// point_of_declaration1.cpp  
// compile with: /W1   
double dVar = 7.0;  
int main()  
{  
   double dVar = dVar;   // C4700  
}  
```  
  
 如果宣告的點是在初始化「之後」，則區域 `dVar` 會初始化為 7.0，也就是全域變數 `dVar` 的值。  不過，由於並不是這種情況，因此 `dVar` 會初始化為未定義的值。  
  
## 請參閱  
 [範圍](../cpp/scope-visual-cpp.md)