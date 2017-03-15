---
title: "內嵌組譯碼中的資料指示詞和運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__asm 關鍵字 [C++], 參考限制"
  - "資料指示詞 [C++]"
  - "指示詞 [C++], MASM"
  - "內嵌組譯碼, 資料指示詞"
  - "內嵌組譯碼, 運算子"
  - "MASM (Microsoft Macro Assembler), 指示詞"
  - "MASM (Microsoft Macro Assembler), 運算子"
  - "MASM (Microsoft Macro Assembler), 結構"
  - "運算子 [MASM]"
  - "結構 [C++], MASM"
ms.assetid: fb7410c7-156a-4131-bcfc-211aa70533e3
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 內嵌組譯碼中的資料指示詞和運算子
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定的  
 `__asm` 區塊可以參考 C 或 C\+\+ 資料類型和物件，但無法定義含 MASM 指示詞或運算子的資料物件。  具體來說，您不能使用定義指示詞 **DB**、`DW`、**DD**、`DQ`、`DT` 和 `DF`，或是運算子 `DUP` 或 **THIS**。  也無法使用 MASM 結構和記錄。  內嵌組合語言不接受指示詞 `STRUC`、`RECORD`、**WIDTH** 或 **MASK**。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [在 \_\_asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)