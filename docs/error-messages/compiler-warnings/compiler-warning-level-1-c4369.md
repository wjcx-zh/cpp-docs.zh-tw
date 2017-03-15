---
title: "編譯器警告 (層級 1) C4369 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4369"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4369"
ms.assetid: ade87e84-36be-4e00-be99-2930af848feb
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器警告 (層級 1) C4369
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'enumerator' : 列舉值 'value' 不可表示為 'type'，值為 'new\_value'  
  
 列舉值計算出來是大於指定基礎型別的最大值。因而造成溢位，而編譯器將列舉值包裝為該型別的最低值。  
  
## 範例  
 下列範例會產生 C4369。  
  
```  
// C4369.cpp  
// compile with: /W1  
int main() {  
   enum Color: char { red = 0x7e, green, blue };   // C4369  
   enum Color2: char { red2 = 0x7d, green2, blue2};   // OK  
}  
```