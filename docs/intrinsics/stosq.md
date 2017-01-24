---
title: "__stosq | Microsoft Docs"
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
  - "__stosq"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rep stosq 指令"
  - "stosq 指令"
  - "__stosq 內建"
ms.assetid: 3ea28297-4369-4c2d-bf0c-91fa539ce209
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __stosq
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 會產生存放字串指示 \(`rep stosq`\)。  
  
## 語法  
  
```  
void __stosb(   
   unsigned __int64* Dest,   
   unsigned __int64 Data,   
   size_t Count   
);  
```  
  
#### 參數  
 \[out\] `Dest`  
 作業的目的地。  
  
 \[in\] `Data`  
 要儲存的資料。  
  
 \[in\] `Count`  
 要寫入的 quadwords 的區塊的長度。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__stosq`|AMD64|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 結果是 quadword `Data`會寫入一段內`Count`中的 quadwords `Dest`字串。  
  
 只有使用與內建這個常式。  
  
## 範例  
  
```  
// stosq.c  
// processor: x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__stosq)  
  
int main()  
{  
   unsigned __int64 val = 0xFFFFFFFFFFFFI64;  
   unsigned __int64 a[10];  
   memset(a, 0, sizeof(a));  
   __stosq(a+1, val, 2);  
   printf("%I64x %I64x %I64x %I64x", a[0], a[1], a[2], a[3]);   
}  
```  
  
## Output  
  
```  
0 ffffffffffff ffffffffffff 0  
```  
  
### 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)