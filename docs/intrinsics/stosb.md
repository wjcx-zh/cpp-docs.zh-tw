---
title: "__stosb | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__stosb"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rep stosb 指令"
  - "__stosb 內建"
  - "stosb 指令"
ms.assetid: 634589ed-2da3-439b-a381-a214d89bf10c
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# __stosb
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 會產生存放字串指示 \(`rep stosb`\)。  
  
## 語法  
  
```  
void __stosb(   
   unsigned char* Dest,   
   unsigned char Data,   
   size_t Count   
);  
```  
  
#### 參數  
 \[out\] `Dest`  
 作業的目的地。  
  
 \[in\] `Data`  
 要儲存的資料。  
  
 \[in\] `Count`  
 要寫入的位元組區塊的長度。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__stosb`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 結果是，字元`Data`會寫入一段內`Count`位元組的`Dest`字串。  
  
 只有使用與內建這個常式。  
  
## 範例  
  
```  
// stosb.c  
// processor: x86, x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__stosb)  
  
int main()  
{  
    unsigned char c = 0x40; /* '@' character */  
    unsigned char s[] = "*********************************";  
  
    printf_s("%s\n", s);  
    __stosb((unsigned char*)s+1, c, 6);  
    printf_s("%s\n", s);  
  
}  
```  
  
  **\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\* \*@@@@@@\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\***   
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)