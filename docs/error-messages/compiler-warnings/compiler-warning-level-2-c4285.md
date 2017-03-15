---
title: "編譯器警告 (層級 2) C4285 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4285"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4285"
ms.assetid: fa14de1f-fc19-4eec-8bea-81003636e12f
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器警告 (層級 2) C4285
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果使用中置標記法來套用，'identifier::operator –\>' 的傳回型別是遞迴的型別  
  
 指定的 **operator–\>\(\)** 函式無法傳回它被定義的型別，或是傳回它被定義的型別之參考。  
  
 下列範例會產生 C4285：  
  
```  
// C4285.cpp  
// compile with: /W2  
class C  
{  
public:  
    C operator->();   // C4285  
   // C& operator->();  C4285, also  
};  
  
int main()  
{  
}  
```