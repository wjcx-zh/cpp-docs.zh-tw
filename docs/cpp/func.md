---
title: "__func__ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__func__"
  - "__func___cpp"
dev_langs: 
  - "C++"
ms.assetid: a5299b8d-f0ee-4af2-91dd-8fb165e68798
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __func__
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**\(C\+\+11\)** 預先定義的識別項 \_\_func\_\_ 以隱含方式定義為字串，其中包含封入函式的不合格及未修飾名稱。  \_\_func\_\_ 由 C\+\+ 標準所託管，而且不是 Microsoft 擴充功能。  
  
## 語法  
  
```vb  
__func__  
```  
  
## 傳回值  
 傳回以 null 結束的字元 const char 陣列，其中包含函式名稱。  
  
## 範例  
  
```  
  
#include <string>  
#include <iostream>  
  
namespace Test  
{  
    struct Foo  
    {  
        static void DoSomething(int i, std::string s)  
        {  
           std::cout << __func__ << std::endl; // Output: DoSomething  
        }  
    };  
}  
int main()  
{  
    Test::Foo::DoSomething(42, "Hello");  
  
    return 0;  
}  
  
```  
  
## 需求  
 C\+\+11