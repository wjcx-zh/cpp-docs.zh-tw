---
title: "__segmentlimit | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__segmentlimit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__segmentlimit 內建"
  - "lsl 指令"
ms.assetid: d0bc3630-90cb-4185-8667-686fd41e23d4
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# __segmentlimit
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 會產生`lsl` \(載入區段限制\) 的指令。  
  
## 語法  
  
```  
unsigned long __segmentlimit(   
   unsigned long a   
);  
```  
  
#### 參數  
 \[in\] `a`  
 指定的區段選取器的常數。  
  
## 傳回值  
 區段的限制所指定的區段選取器`a,` 此處的選擇器 」 是有效且可以看到目前的權限層級。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__segmentlimit`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 如果無法擷取此區段限制，則此指令會失敗。  在失敗時，這個指令清除 ZF 旗標，則傳回值是未定義。  
  
 只有使用與內建這個常式。  
  
## 範例  
  
```  
#include <stdio.h>  
  
#ifdef _M_IX86  
typedef unsigned int READETYPE;  
#else  
typedef unsigned __int64 READETYPE;  
#endif  
  
#define EFLAGS_ZF      0x00000040  
#define KGDT_R3_DATA    0x0020  
#define RPL_MASK        0x3  
  
extern "C"  
{  
unsigned long __segmentlimit (unsigned long);  
READETYPE __readeflags();  
}  
  
#pragma intrinsic(__readeflags)  
#pragma intrinsic(__segmentlimit)  
  
int main(void)  
{  
   const unsigned long initsl = 0xbaadbabe;  
   READETYPE eflags = 0;  
   unsigned long sl = initsl;  
  
   printf("Before: segment limit =0x%x eflags =0x%x\n", sl, eflags);  
   sl = __segmentlimit(KGDT_R3_DATA + RPL_MASK);  
  
   eflags = __readeflags();  
  
   printf("After: segment limit =0x%x eflags =0x%x eflags.zf = %s\n", sl, eflags, (eflags & EFLAGS_ZF) ? "set" : "clear");  
  
   // If ZF is set, the call to lsl succeeded; if ZF is clear, the call failed.  
   printf("%s\n", eflags & EFLAGS_ZF ? "Success!": "Fail!");  
  
   // You can verify the value of sl to make sure that the instruction wrote to it  
   printf("sl was %s\n", (sl == initsl) ? "unchanged" : "changed");  
  
   return 0;  
}  
```  
  
  **之前： 區段的限制 \= 0xbaadbabe eflags \= 0x0 之後： 區段限制 \= 0xffffffff eflags \= 0x256 eflags.zf \= 設定成功\!**  
 **sl 已變更**   
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)