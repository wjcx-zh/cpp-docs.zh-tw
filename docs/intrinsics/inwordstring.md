---
title: "__inwordstring | Microsoft Docs"
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
  - "__inwordstring"
  - "__inwordstring_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__inwordstring 內建"
  - "rep insw 指令"
ms.assetid: 6de37939-017a-4740-9e3d-7de78a30daba
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __inwordstring
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 從指定的連接埠使用中讀取資料`rep insw`指令。  
  
## 語法  
  
```  
void __inwordstring(  
   unsigned short Port,  
   unsigned short* Buffer,  
   unsigned long Count  
);  
```  
  
#### 參數  
 \[in\] `Port`  
 若要從讀取連接埠。  
  
 \[out\] `Buffer`  
 從連接埠所讀取的資料會寫入下面。  
  
 \[in\] `Count`  
 要讀取資料的單字個數。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__inwordstring`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 只有使用與內建這個常式。  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)