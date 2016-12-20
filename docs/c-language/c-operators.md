---
title: "C 運算子 | Microsoft Docs"
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
  - "運算子的順序關聯性"
  - "二進位資料, 二進位運算式"
  - "二元運算子"
  - "運算子 [C]"
  - "符號, 運算子"
  - "三元運算子"
ms.assetid: 13bc4c8e-2dc9-4b23-9f3a-25064e8777ed
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C 運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C 運算子是 [C\+\+ 運算子](../misc/cpp-operators.md)的子集。  
  
 運算子可分三種類型。  一元的運算式包含附加在運算元之前的一元運算子，或運算式之後的 `sizeof` 關鍵字。  運算式可以是變數名稱或轉型運算式。  如果運算式是轉型運算式，必須以括號括住。  二進位運算式是由兩個以二元運算子聯結的運算元組成。  三元運算式是由三個以條件運算式運算子聯結的運算元組成。  
  
 C 包括以下一元運算子：  
  
|符號|名稱|  
|--------|--------|  
|**– ~ \!**|負運算子和補數運算子|  
|**\* &**|間接和傳址運算子|  
|`sizeof`|Size 運算子|  
|**\+**|一元加號運算子|  
|**\+\+ ––**|一元遞增和遞減運算子|  
  
 二元運算子會由左至右關聯。  C 會提供下列二元運算子：  
  
|符號|名稱|  
|--------|--------|  
|**\* \/ %**|乘法類運算子|  
|**\+ –**|加法類運算子|  
|**\<\<**<br /> **\>\>**|移位運算子|  
|**\<   \>   \<\=   \>\=   \=\=   \!\=**|關係運算子|  
|**&   &#124; ^**|位元運算子|  
|**&&   &#124;&#124;**|邏輯運算子|  
|**,**|循序求值運算子|  
  
 舊版 Microsoft 16 位元 C 編譯器支援的基底運算子 \(**:\>**\)，將在 [C 語言語法摘要](../c-language/c-language-syntax-summary.md)中加以說明。  
  
 有別於二進位運算式，條件運算式運算子優先順序較低，並且是右向關聯的。  
  
 具有運算子的運算式也包括使用一元或二元指派運算子的指派運算式。  一元指派運算子是指遞增 \(`++`\) 和遞減 \(**––**\) 運算子；二元指派運算子則是簡單指派運算子 \(**\=**\) 和複合指派運算子。  每個複合指派運算子都是另一個二元運算子與簡單指派運算子的組合。  
  
## 請參閱  
 [運算式和指派](../c-language/expressions-and-assignments.md)