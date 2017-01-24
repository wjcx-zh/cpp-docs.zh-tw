---
title: "編譯器錯誤 C2718 | Microsoft Docs"
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
  - "C2718"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2718"
ms.assetid: 78cc71f8-c142-46fc-9aed-970635d74f0c
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2718
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'parameter': 具有 \_\_declspec\(align\('\#'\)\) 的實質參數不會被對齊  
  
 不允許函式參數上出現 [align](../../cpp/align-cpp.md) `__declspec` 修飾詞 \(Modifier\)。  
  
 下列範例會產生 C2718：  
  
```  
// C2718.cpp  
typedef struct __declspec(align(32)) AlignedStruct  {   
   int i;   
} AlignedStruct;  
  
void f2(int i, ...);  
  
void f4() {  
   AlignedStruct as;  
  
   f2(0, as);   // C2718, actual parameter is aligned  
}  
```