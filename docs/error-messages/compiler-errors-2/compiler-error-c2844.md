---
title: "編譯器錯誤 C2844 | Microsoft Docs"
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
  - "C2844"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2844"
ms.assetid: dcaf4cd2-21b0-4280-ae42-0a706c524d83
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2844
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'member' : 不可為介面 'interface' 的成員  
  
 [interface class](../../windows/interface-class-cpp-component-extensions.md) 不可以包含資料成員，除非它也是屬性。  
  
 介面中不允許任何屬性或成員 \(Member\) 函式以外的項目存在。  而且還不允許包含建構函式 \(Constructor\)、解構函式 \(Destructor\) 和運算子。  
  
 下列範例會產生 C2844：  
  
```  
// C2844a.cpp  
// compile with: /clr /c  
public interface class IFace {  
   int i;   // C2844  
   // try the following line instead  
   // property int Size;  
};  
```  
  
 下列範例會產生 C2844：  
  
```  
// C2844b.cpp  
// compile with: /clr:oldSyntax /c  
#using <mscorlib.dll>  
__gc __interface IFace {  
   int i;   // C2844  
   // try the following line instead  
   // __property int Size { get; set; };  
};  
```