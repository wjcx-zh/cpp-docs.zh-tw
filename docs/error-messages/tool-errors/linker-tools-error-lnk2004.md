---
title: "連結器工具錯誤 LNK2004 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2004
dev_langs: C++
helpviewer_keywords: LNK2004
ms.assetid: 07645371-e67b-4a2c-b0e0-dde24c94ef7e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0bd4ddd4e7caf042ac16c5947a6b48aa21ab5739
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk2004"></a>連結器工具錯誤 LNK2004
'target;' 的 gp 相對修復溢位short 區段 'section' 是太大，或超出範圍。  
  
 區段是太大。  
  
 若要解決這個錯誤，減少短的區段，藉由明確地將資料放在長的區段，透過 #pragma > 一節 （「.sectionname"，讀取、 寫入、 長時間） 和使用的大小`__declspec(allocate(".sectionname"))`上資料定義和宣告。  例如：  
  
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
  
 您也可以成為自己結構，將會大於 8 個位元組，編譯器會配置 long 資料區段中的資料集合中移動以邏輯方式分組的資料。  例如：  
  
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
  
 此錯誤後面是嚴重錯誤`LNK1165`。