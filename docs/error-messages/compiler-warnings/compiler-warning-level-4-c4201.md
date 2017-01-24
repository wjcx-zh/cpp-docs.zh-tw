---
title: "編譯器警告 (層級 4) C4201 | Microsoft Docs"
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
  - "C4201"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4201"
ms.assetid: 6156f508-9393-4d77-9e73-1ec3e1c32d0d
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4201
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用非標準的擴充：沒有名稱的結構\/等位  
  
 在 Microsoft 擴充功能 \(\/Ze\) 之下，您可以指定結構，不需以宣告子 \(Declarator\) 做為其他結構或等位的成員。  這些結構在 ANSI 相容性 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 下會產生錯誤。  
  
## 範例  
  
```  
// C4201.cpp  
// compile with: /W4  
struct S  
{  
   float y;  
   struct  
   {  
      int a, b, c;  // C4201  
   };  
} *p_s;  
  
int main()  
{  
}  
```