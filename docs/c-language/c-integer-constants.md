---
title: "C 整數常數 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "整數常數"
ms.assetid: fcf6b83c-2038-49ec-91ca-3d5ca1f83037
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C 整數常數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

「整數常數」為代表整數值的十進位 \(基底 10\)、八進位 \(基底 8\) 或十六進位 \(基底 16\) 數字。  使用整數常數來表示無法變更的整數值。  
  
## 語法  
 *integer\-constant*：  
 *decimal\-constant integer\-suffix*  opt  
  
 *octal\-constant integer\-suffix*  opt  
  
 *hexadecimal\-constant integer\-suffix*  opt  
  
 *decimal\-constant*:  
 *nonzero\-digit*  
  
 *decimal\-constant digit*  
  
 *octal\-constant*：  
 **0**  
  
 *octal\-constant octal\-digit*  
  
 *hexadecimal\-constant*：  
 **0x**  *hexadecimal\-digit*  
  
 **0X**  *hexadecimal\-digit*  
  
 *hexadecimal\-constant hexadecimal\-digit*  
  
 *nonzero\-digit*：下列其中一個  
 **1 2 3 4 5 6 7 8 9**  
  
 *octal\-digit*：下列其中一個  
 **0 1 2 3 4 5 6 7**  
  
 *hexadecimal\-digit*：下列其中一個  
 **0 1 2 3 4 5 6 7 8 9**  
  
 **a b c d e f**  
  
 **A B C D E F**  
  
 *integer\-suffix*：  
 *unsigned\-suffix long\-suffix*  opt  
  
 *long\-suffix unsigned\-suffix*  opt  
  
 *unsigned\-suffix*：下列其中一個  
 **u U**  
  
 *long\-suffix*：下列其中一個  
 **l L**  
  
 *64\-bit integer\-suffix*：  
 **i64**  
  
 除非前面加上負號 \(**–**\)，否則整數常數為正數。  負號會解譯為一元算術負運算子 \(如需這個運算子的詳細資訊，請參閱[一元算術運算子](../c-language/unary-arithmetic-operators.md)\)。  
  
 如果整數常數的開頭是 **0x** 或 **0X**開始，即為十六進位。  如果開頭是數字 **0**，即為八進位。  否則即假設為十進位。  
  
 下列各行是相等的：  
  
```  
0x1C   /* = Hexadecimal representation for decimal 28 */  
034    /* = Octal representation for decimal 28 */  
```  
  
 空白字元不能分隔整數常數的數字。  下列範例示範有效的十進位、八進位和十六進位常數。  
  
```  
/* Decimal Constants */  
10  
132  
32179  
  
/* Octal Constants */  
012  
0204  
076663  
  
/* Hexadecimal Constants */  
0xa or 0xA  
0x84  
0x7dB3 or 0X7DB3  
```  
  
## 請參閱  
 [C 常數](../c-language/c-constants.md)