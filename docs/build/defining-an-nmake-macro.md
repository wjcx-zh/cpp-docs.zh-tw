---
title: "定義 NMAKE 巨集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "定義 NMAKE 巨集"
  - "巨集, NMAKE"
  - "NMAKE 巨集, 定義"
ms.assetid: 45aae451-9d33-4a3d-8799-2e0cae17070d
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 定義 NMAKE 巨集
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
macroname=string  
```  
  
## 備註  
 *macroname* 是字母、數字，以及底線 \(\_\) 的組合，最多為 1,024 字元，並且區分大小寫。  *macroname* 名稱可含有叫用的巨集。  如果 *macroname* 完全由叫用的巨集組成，所叫用的巨集不能為 Null 或未定義。  
  
 `string` 可以是任何零或多個字元的序列。  Null 字串包含零個字元，或只包含空格和定位字元。  `string` 可包含巨集引動過程。  
  
## 您還想知道關於哪些方面的詳細資訊？  
 [巨集中的特殊字元](../build/special-characters-in-macros.md)  
  
 [Null 和未定義的巨集](../build/null-and-undefined-macros.md)  
  
 [定義巨集的位置](../build/where-to-define-macros.md)  
  
 [巨集定義的優先順序](../build/precedence-in-macro-definitions.md)  
  
## 請參閱  
 [巨集和 NMAKE](../build/macros-and-nmake.md)