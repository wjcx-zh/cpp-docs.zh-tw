---
title: 引數數目可變的呼叫 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- arguments [C++], function
- arguments [C++], variable number of
- VARARGS.H
- ellipses (...), variable number of arguments
- STDARGS.H
- function calls, arguments
- '... ellipsis'
- function calls, variable number of arguments
ms.assetid: 8808fb26-4822-42f5-aba3-ac64b54e151b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bee194177acc9f2e63719b4ecd16593db7fe048f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="calls-with-a-variable-number-of-arguments"></a>引數數目可變的呼叫
部分參數清單的末端可以用逗號後面接著三個句號 (**, ...**) 的省略符號標記法，來表示可能有更多傳遞至函式的引數，不過未提供這些引數的相關資訊。 類型檢查不會在這類引數上執行。 至少有一個參數前面必須加上省略符號標記法，而且省略符號標記法必須是參數清單中的最後一個語彙基元。 未使用省略符號標記法時，如果函式收到的參數不是參數清單中所宣告的參數，表示函式的行為尚未定義。  
  
 若要呼叫具有可變引數數目的函式，請在函式呼叫中指定任意數目的引數。 例如，C 執行階段程式庫中的 `printf` 函式。 函式呼叫必須針對參數清單或引數類型清單中宣告的每個類型名稱包含一個引數。  
  
 除非指定 `__fastcall` 呼叫慣例，否則函式呼叫中指定的所有引數都會放置在堆疊上。 針對函式宣告的參數數目，可判斷從堆疊取出並指派至參數的引數數目。 您必須負責從堆疊擷取任何額外的引數，以及判斷有多少引數存在。 STDARG.H 檔案中包含 ANSI 樣式的巨集，用於存取採用可變引數數目之函式的引數。 此外仍支援 VARARGS.H 中 XENIX 樣式的巨集。  
  
 這個範例宣告用於呼叫可變引數數目的函式：  
  
```  
int average( int first, ...);  
```  
  
## <a name="see-also"></a>請參閱  
 [函式呼叫](../c-language/function-calls.md)