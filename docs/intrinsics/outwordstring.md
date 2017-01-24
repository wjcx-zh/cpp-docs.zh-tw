---
title: "__outwordstring | Microsoft Docs"
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
  - "__outwordstring"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rep outsw 指令"
  - "內建 __outwordstring"
  - "outsw 指令"
ms.assetid: b470c7a0-1de9-4370-886a-b2c3a1f842f4
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __outwordstring
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 會產生`rep outsw`指令，會傳送`Count`字為起始點`Buffer`出所指定的 I\/O 連接埠`Port`。  
  
## 語法  
  
```  
void __outwordstring(   
   unsigned short Port,   
   unsigned short* Buffer,   
   unsigned long Count   
);  
```  
  
#### 參數  
 \[in\] `Port`  
 若要將資料傳送到連接埠。  
  
 \[in\] `Buffer`  
 寄出指定的連接埠的資料指標。  
  
 \[in\] `Count`  
 要傳送的文字數。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__outwordstring`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 只有使用與內建這個常式。  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)