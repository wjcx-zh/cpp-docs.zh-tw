---
title: "編譯器警告 (層級 3) C4240 | Microsoft Docs"
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
  - "C4240"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4240"
ms.assetid: a2657cdb-18e1-493f-882b-4e10c0bca71d
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 3) C4240
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用非標準的擴充 : 存取 'classname' 現在已經定義為 'access specifier'，之前它定義為 'access specifier'  
  
 使用 ANSI 相容性 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\)，您無法變更巢狀類別 \(Nested Class\) 的存取。  在預設的 Microsoft 擴充功能 \(\/Ze\) 之下，您可以進行變更，但會出現此警告。  
  
## 範例  
  
```  
// C4240.cpp  
// compile with: /W3  
class X  
{  
private:  
   class N;  
public:  
   class N  
   {   // C4240  
   };  
};  
  
int main()  
{  
}  
```