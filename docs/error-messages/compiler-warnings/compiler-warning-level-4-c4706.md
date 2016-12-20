---
title: "編譯器警告 (層級 4) C4706 | Microsoft Docs"
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
  - "C4706"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4706"
ms.assetid: 89cd3f4f-812c-4a4b-9426-65a5a6d1b99c
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4706
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在條件運算式中使用指派運算子  
  
 條件運算式中的測試值是指派的結果。  
  
 指派中有一值 \(在指派左側的值\) 可以合法使用在其他運算式中，包括測試運算式。  
  
 下列範例會產生 C4706：  
  
```  
// C4706a.cpp  
// compile with: /W4  
int main()  
{  
   int a = 0, b = 0;  
   if ( a  = b ) // C4706  
   {  
   }  
}  
```  
  
 即使您為測試條件加上兩層括弧，還是會發生此警告：  
  
```  
// C4706b.cpp  
// compile with: /W4  
int main()  
{  
   int a = 0, b = 0;  
   if ( ( a  =  b ) ) // C4706  
   {  
   }  
}  
```  
  
 如果您是要測試關聯，而不是要指派，請使用 `==` 運算子。  例如，下列程式行會測試 a 和 b 是否相等：  
  
```  
// C4706c.cpp  
// compile with: /W4  
int main()  
{  
   int a = 0, b = 0;  
   if ( a == b )  
   {  
   }  
}  
```  
  
 如果您想要將測試值設為指派的結果，請進行測試以確保指派是非零或不是 Null。  例如，下列程式碼就不會產生此警告：  
  
```  
// C4706d.cpp  
// compile with: /W4  
int main()  
{  
   int a = 0, b = 0;  
   if ( ( a = b ) != 0 )  
   {  
   }  
}  
```