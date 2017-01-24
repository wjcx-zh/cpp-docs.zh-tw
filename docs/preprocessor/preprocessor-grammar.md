---
title: "前置處理器文法 | Microsoft Docs"
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
  - "文法, 前置處理器"
  - "前置處理器"
  - "前置處理器, 文法"
ms.assetid: 6cd33fad-0b08-4592-9be8-7359c43e24e9
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 前置處理器文法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**\#define**  *identifier* *token\-string*opt  
  
 *\#* **define**  *identifier*\[**\(** *identifier*opt**,** *...* **,** *identifier*opt **\)**\] *token\-string*opt  
  
 **defined\(**  *identifier* **\)**  
  
 **defined**  *identifier*  
  
 `#include` **"***path\-spec***"**  
  
 `#include` **\<***path\-spec***\>**  
  
 **\#line**  *digit\-sequence*  **"** *filename* **"** opt  
  
 *\#* **undef**  *identifier*  
  
 **\#error**  *token\-string*  
  
 **\#pragma**  *token\-string*  
  
 *conditional* ：  
 *if\-part elif\-parts* opt *else\-part*opt *endif\-line*  
  
 *if\-part* ：  
 *if\-linetext*  
  
 *if\-line* ：  
 **\#if**  *constant\-expression*  
  
 **\#ifdef**  *identifier*  
  
 **\#ifndef**  *identifier*  
  
 *elif\-parts* ：  
 *elif\-line text*  
  
 *elif\-parts elif\-line text*  
  
 *elif\-line* ：  
 **\#elif**  *constant\-expression*  
  
 *else\-part* ：  
 *else\-linetext*  
  
 *else\-line* ：  
 `#else`  
  
 *endif\-line* ：  
 `#endif`  
  
 *digit\-sequence* ：  
 *digit*  
  
 *digit\-sequence digit*  
  
 *digit* ：下列其中一個  
 **0 1 2 3 4 5 6 7 8 9**  
  
 *token\-string* ：  
 語彙基元字串  
  
 *token* ：  
 *keyword*  
  
 *識別項*  
  
 *常數*  
  
 *運算子*  
  
 `punctuator`  
  
 *filename* ：  
 合法的作業系統檔名  
  
 *path\-spec* ：  
 合法的檔案路徑  
  
 *text* ：  
 文字的任意序列  
  
> [!NOTE]
>  下列非終止項會在《C\+\+ 語言參考》中的＜附錄 A，[文法摘要](../misc/grammar-summary-cpp.md)＞中進行擴充：`constant`、`constant`\-*expression*、*identifier*, *keyword*、`operator` 和 `punctuator`。  
  
## 請參閱  
 [文法摘要](../preprocessor/grammar-summary-c-cpp.md)