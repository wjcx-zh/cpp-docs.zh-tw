---
title: "編譯器錯誤 C2867 | Microsoft Docs"
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
  - "C2867"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2867"
ms.assetid: 63be26b2-d9ab-4f3d-a8b7-981ce3e4d6b9
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2867
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 不是命名空間  
  
 `using`  指示詞套用至命名空間以外的項目。  
  
 下列範例會產生 C2867：  
  
```  
// C2867.cpp  
// compile with: /c  
namespace N {  
   class X {};  
}  
using namespace N::X;   // C2867  
```