---
title: "__inbyte | Microsoft Docs"
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
  - "__inbyte"
  - "__inbyte_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "in 指令"
  - "內建 __inbyte"
ms.assetid: 03b61799-2a08-474d-adc4-2cbf7c81a4d5
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __inbyte
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 會產生`in`指令時，傳回一個位元組從所指定的連接埠讀取`Port`。  
  
## 語法  
  
```  
unsigned char __inbyte(  
   unsigned short Port  
);  
```  
  
#### 參數  
 \[in\] `Port`  
 若要從讀取連接埠。  
  
## 傳回值  
 從指定的連接埠讀取的位元組。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__inbyte`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 結束 Microsoft 特定  
  
## 備註  
 只有使用與內建這個常式。  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)