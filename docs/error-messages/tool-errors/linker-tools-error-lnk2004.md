---
title: "連結器工具錯誤 LNK2004 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2004"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2004"
ms.assetid: 07645371-e67b-4a2c-b0e0-dde24c94ef7e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 連結器工具錯誤 LNK2004
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'target' 的 gp 相對修復溢位；short 區段 'section' 太長或超出範圍  
  
 區段過大。  
  
 若要解除這項錯誤，請縮減 short 區段的大小，可以經由 \#pragma section\(".sectionname", read, write, long\)，並使用資料定義和宣告上的 `__declspec(allocate(".sectionname"))`，明確地將資料放入 long 區段之中。例如：  
  
```  
#pragma section(".data$mylong", read, write, long)  
__declspec(allocate(".data$mylong"))  
char    rg0[1] = { 1 };  
char    rg1[2] = { 1 };  
char    rg2[4] = { 1 };  
char    rg3[8] = { 1 };  
char    rg4[16] = { 1 };  
char    rg5[32] = { 1 };  
```  
  
 您也可以將以邏輯方式群組的資料移入其本身結構中，該結構將是大於 8 位元組的資料集合，而編譯器會將它配置在 long 資料區段之中。例如：  
  
```  
// from this...  
int     w1  = 23;  
int     w2 = 46;  
int     w3 = 23*3;  
int     w4 = 23*4;  
  
// to this...  
struct X {  
    int     w1;  
    int     w2;  
    int     w3;  
    int     w4;  
} x  = { 23, 23*2, 23*3, 23*4 };  
  
```  
  
 這個錯誤之後會出現嚴重錯誤 `LNK1165`。