---
title: "__indwordstring | Microsoft Docs"
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
  - "__indwordstring"
  - "__indwordstring_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__indwordstring 內建"
  - "rep insd 指令"
ms.assetid: 96a1cf33-f691-4916-99e4-fa849b61e3a9
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __indwordstring
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 從指定的連接埠使用中讀取資料`rep insd`指令。  
  
## 語法  
  
```  
void __indwordstring(  
   unsigned short Port,  
   unsigned long* Buffer,  
   unsigned long Count  
);  
```  
  
#### 參數  
 \[in\] `Port`  
 若要從讀取連接埠。  
  
 \[out\] `Buffer`  
 從連接埠所讀取的資料會寫入下面。  
  
 \[in\] `Count`  
 要讀取的資料位元組數目。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__indwordstring`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 只有使用與內建這個常式。  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)