---
title: "__outbytestring | Microsoft Docs"
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
  - "__outbytestring"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rep outsb 指令"
  - "__outbytestring 內建"
  - "outsb 指令"
ms.assetid: c9150661-9c18-427f-bae8-710bba6ed78c
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __outbytestring
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 會產生`rep outsb`指令，會將傳送第一個`Count`個位元組的資料所指`Buffer`到所指定的連接埠`Port`。  
  
## 語法  
  
```  
void __outbytestring(   
   unsigned short Port,   
   unsigned char* Buffer,   
   unsigned long Count   
);  
```  
  
#### 參數  
 \[in\] `Port`  
 若要將資料傳送到連接埠。  
  
 \[in\] `Buffer`  
 要送出指定的連接埠的資料。  
  
 \[in\] `Count`  
 要傳送的資料位元組數目。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__outbytestring`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 只有使用與內建這個常式。  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)