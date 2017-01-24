---
title: "引數數目可變的呼叫 | Microsoft Docs"
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
  - "... 省略符號"
  - "引數 [C++], 函式"
  - "引數 [C++], 可數數目"
  - "省略符號 (...), 引數數目可變的"
  - "函式呼叫, 引數"
  - "函式呼叫, 引數數目可變的"
  - "STDARGS.H"
  - "VARARGS.H"
ms.assetid: 8808fb26-4822-42f5-aba3-ac64b54e151b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 引數數目可變的呼叫
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

部分參數清單可以藉由逗號後面接著三個句號 \(**, ...**\) 的省略符號標記法結束，表示可能有更多引數傳遞至函式，不過未提供這些引數的相關資訊。  類型檢查不會在這類引數上執行。  至少有一個參數前面必須加上省略符號標記法，而且省略符號標記法必須是參數清單中的最後一個語彙基元。  未使用省略符號標記法時，如果函式收到的參數不是參數清單中所宣告的參數，表示函式的行為尚未定義。  
  
 若要呼叫具有可變引數數目的函式，請在函式呼叫中指定任意數目的引數。  例如，C 執行階段程式庫中的 `printf` 函式。  函式呼叫必須針對參數清單或引數類型清單中宣告的每個類型名稱包含一個引數。  
  
 除非指定 `__fastcall` 呼叫慣例，否則函式呼叫中指定的所有引數都會放置在堆疊上。  針對函式宣告的參數數目，可判斷從堆疊取出並指派至參數的引數數目。  您必須負責從堆疊擷取任何額外的引數，以及判斷有多少引數存在。  STDARG.H 檔案中包含 ANSI 樣式的巨集，用於存取採用可變引數數目之函式的引數。  此外仍支援 VARARGS.H 中 XENIX 樣式的巨集。  
  
 這個範例宣告用於呼叫可變引數數目的函式：  
  
```  
int average( int first, ...);  
```  
  
## 請參閱  
 [函式呼叫](../c-language/function-calls.md)