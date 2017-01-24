---
title: "__indword | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__indword_cpp"
  - "__indword"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "in 指令"
  - "內建 __indword"
ms.assetid: 1068d686-586e-4e36-b962-d1d7c3315260
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __indword
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 從指定的連接埠使用讀取資料的一個雙字`in`指令。  
  
## 語法  
  
```  
unsigned long __indword(  
   unsigned short Port  
);  
```  
  
#### 參數  
 \[in\] `Port`  
 若要從讀取連接埠。  
  
## 傳回值  
 從連接埠，讀取這個字。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__indword`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 只有使用與內建這個常式。  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)