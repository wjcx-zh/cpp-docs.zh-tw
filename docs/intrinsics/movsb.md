---
title: "__movsb | Microsoft Docs"
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
  - "__movsb"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "movsb 指令"
  - "rep movsb 指令"
  - "內建 __movsb"
ms.assetid: ba5469f6-f797-4cd2-bee8-74c7666c26d4
caps.latest.revision: 15
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __movsb
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 產生移動的字串 \(`rep movsb`\) 的指令。  
  
## 語法  
  
```  
void __movsb(   
   unsigned char* Destination,   
   unsigned const char* Source,   
   size_t Count   
);  
```  
  
#### 參數  
 \[out\] `Destination`  
 若要複製的目的端變數的指標。  
  
 \[in\] `Source`  
 若要複製的來源變數的指標。  
  
 \[in\] `Count`  
 要複製的位元組數目。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__movsb`|x86，[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 備註  
 結果會是第一個`Count`個位元組所指`Source`會被複製到`Destination`字串。  
  
 只有使用與內建這個常式。  
  
## 範例  
  
```  
// movsb.cpp  
// processor: x86, x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__movsb)  
  
int main()  
{  
    unsigned char s1[100];  
    unsigned char s2[100] = "A big black dog.";  
    __movsb(s1, s2, 100);  
  
    printf_s("%s %s", s1, s2);  
}  
```  
  
  **大型的黑色小狗。**  
 **大型的黑色小狗。**   
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)