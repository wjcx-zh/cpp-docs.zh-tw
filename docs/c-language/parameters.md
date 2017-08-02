---
title: "參數 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- arguments [C++], function
- function parameters
- parameters [C++]
- function arguments, vs. parameters
- parameters [C++], function
- functions [C], parameters
- function parameters, syntax
- ellipses (...), parameters
- '... ellipsis'
ms.assetid: 8f2b8026-78b5-4e21-86a3-bf0f91f05689
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 7f596595f8d21df6a0027a3a5ebfdc5beda5e374
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="parameters"></a>參數
引數是值的名稱，會由函式呼叫傳遞至函式。 參數是函式預期收到的值。 在函式原型中，函式名稱後面接著的括號會包含函式參數與及類型的完整清單。 參數宣告會指定參數中所儲存值的類型、大小和識別項。  
  
## <a name="syntax"></a>語法  
 *function-definition*:  
 *declaration-specifiers* opt*attribute-seq* opt*declarator declaration-list* opt*compound-statement*  
  
 /\* *attribute-seq* 是 Microsoft 專有 */  
  
 *declarator* :  
 *pointer* opt*direct-declarator*  
  
 *direct-declarator*:/\* 函式宣告子 \*/  
 *direct-declarator*  **(**  *parameter-type-list*  **)** /* 新樣式的宣告子 \*/  
  
 *parameter-type-list*: /\* 參數清單 \*/  
 *parameter-list*  
  
 *parameter-list*  **,...**  
  
 *parameter-list*：  
 *parameter-declaration*  
  
 *parameter-list*  **,**  *parameter-declaration*  
  
 *parameter-declaration*：  
 *declaration-specifiers declarator*  
  
 *declaration-specifiers abstract-declarator* opt  
  
 *parameter-type-list* 是參數宣告的序列，各參數會以逗號分隔。 參數清單中每個參數的形式如下所示：  
  
```  
[register]  type-specifier [declarator]   
```  
  
 使用 **auto** 屬性宣告的函式參數會產生錯誤。 參數的識別項會在函式主體中用來參考傳遞至函式的值。 您可以在原型中為參數命名，不過名稱會在宣告結尾超出範圍。 因此，參數名稱可以在函式定義中以相同或不同的方式指派。 這些識別項無法在函式主體的最外層區塊中重新定義，但是可以在內部的巢狀區塊中重新定義，如同將參數清單當做封閉區塊一般。  
  
 *parameter-type-list* 中的每個識別項前面都必須加上適當的類型指定名稱，如這個範例中所示：  
  
```  
void new( double x, double y, double z )  
{  
    /* Function body here */  
}  
```  
  
 如果參數清單中至少會有一個參數，則清單可用逗號且後面接著三個英文句號的形式結束 (**, ...**)。 這種建構稱為「省略符號標記法」，表示函式的可變引數數目。 (如需詳細資訊，請參閱[使用可變數目的引數呼叫](../c-language/calls-with-a-variable-number-of-arguments.md))。不過，函式的呼叫中擁有的引數數目，必須至少為最後一個逗號前面的參數數目。  
  
 如果沒有要傳遞至函式的引數，則參數清單會以關鍵字 `void` 取代。 這種 `void` 用法與其做為類型指定名稱的用法不同。  
  
 參數的順序和類型 (包括使用的省略符號標記法) 在所有函式宣告 (如果有的話) 和函式定義中必須相同。 一般算術轉換之後的引數類型必須與對應參數類型的指派相容。 (如需有關算術轉換的詳細資訊，請參閱[一般算術轉換](../c-language/usual-arithmetic-conversions.md))。省略符號後面的引數不會加以檢查。 參數可以具有任何基本、結構、等位、指標或陣列類型。  
  
 編譯器會在每個參數和每個引數上分別執行一般算術轉換 (如有需要)。 在轉換之後，參數的長度不會比 `int` 短，而且除非參數類型在原型中明確指定為 **float**，否則參數不會具有 **float** 類型。 這表示，例如將一個參數宣告為 `char` 的效果與將它宣告為 `int` 的效果相同。  
  
## <a name="see-also"></a>另請參閱  
 [C 函式定義](../c-language/c-function-definitions.md)
