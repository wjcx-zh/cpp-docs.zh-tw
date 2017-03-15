---
title: "__outdwordstring | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__outdwordstring"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "outsd 指令"
  - "內建 __outdwordstring"
  - "rep outsd 指令"
ms.assetid: 55b31a65-aab7-4b5c-b61d-d9e2fb0c497a
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# __outdwordstring
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 會產生`rep outsd`指令，會傳送`Count`為起始點的 doublewords `Buffer`出所指定的 I\/O 連接埠`Port`。  
  
## 語法  
  
```  
void __outdwordstring(   
   unsigned short Port,   
   unsigned long* Buffer,   
   unsigned long Count   
);  
```  
  
#### 參數  
 \[in\] `Port`  
 若要將資料傳送到連接埠。  
  
 \[in\] `Buffer`  
 寄出指定的連接埠的資料指標。  
  
 \[in\] `Count`  
 若要傳送的 doublewords 數目。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__outdwordstring`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 只有使用與內建這個常式。  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)