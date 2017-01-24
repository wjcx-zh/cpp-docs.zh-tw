---
title: "編譯器錯誤 C2589 | Microsoft Docs"
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
  - "C2589"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2589"
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2589
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : '::' 右邊的語彙基元不合法  
  
 如果範圍解析運算子 \(兩個冒號\) 的左側出現類別、結構或等位名稱，則其右側的語彙基元 \(Token\) 必須是類別、結構或等位成員。  要不然，任何全域識別項會出現在右側。  
  
 範圍解析 \(Scope Resolution\) 運算子不可多載。  
  
 下列範例會產生 C2589：  
  
```  
// C2589.cpp  
void Test(){}  
class A {};  
void operator :: ();   // C2589  
  
int main() {  
   ::Test();  
}  
```