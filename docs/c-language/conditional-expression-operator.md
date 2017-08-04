---
title: "條件運算式運算子 | Microsoft Docs"
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
- conditional operators
- operators [C++], conditional
- expressions [C++], conditional
ms.assetid: c4f1a5ca-0844-44a7-a384-eca584d4e3dd
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
ms.openlocfilehash: 1b7f7bae193af30a5ea9a4d8c9d176ce6763d8ec
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="conditional-expression-operator"></a>條件運算式運算子
C 有一個三元運算子：條件運算式運算子 (**? :**)。  
  
## <a name="syntax"></a>語法  
 *conditional-expression*：  
 *logical-OR-expression*  
  
 *logical-OR expression*  **?**  *expression*  **:**  *conditional-expression*  
  
 *logical-OR-expression* 必須要有整數、浮點或指標類型。 其評估條件為全等於 0。 *logical-OR-expression* 後方會有一個序列點。 評估運算元的方式如下：  
  
-   如果 *logical-OR-expression* 不等於 0，則會評估 *expression*。 運算式的評估結果由非終端 *expression* 決定。 (這表示唯有當 *logical-OR-expression* 為 true 時，才會評估 *expression*)。  
  
-   如果 *logical-OR-expression* 等於 0，則會評估 *conditional-expression*。 運算式的結果是 *conditional-expression* 的值。 (這表示唯有當 *logical-OR-expression* 為 false 時，才會評估 *conditional-expression*)。  
  
 請注意，系統只會評估 *expression* 或 *conditional-expression*，不會同時評估二者。  
  
 條件運算式結果的類型取決於 *expression* 或 *conditional-expression* 運算元的類型，如下所示：  
  
-   如果 *expression* 或 *conditional-expression* 有整數或浮點類型 (其類型可以不同)，運算子會執行一般算術轉換。 結果的類型是轉換後的運算元類型。  
  
-   如果 *expression* 和 *conditional-expression* 有相同結構、等位或指標類型，結果的類型會是相同的結構、等位或指標類型。  
  
-   如果兩個運算元的類型都是 `void`，結果的類型就會是 `void`。  
  
-   如果任一運算元是任何類型的指標，且另一個運算元是 `void` 的指標，會將物件的指標轉換為 `void` 的指標，而結果則是 `void` 的指標。  
  
-   如果 *expression* 或 *conditional-expression* 是指標，且另一個運算元是值為 0 的常數運算式，結果的類型會是指標類型。  
  
 在指標的類型比較中，指標指向之類型的任何類型限定詞 (**const`volatile` 或** ) 都不具意義，但結果類型會繼承條件式之兩個元件的限定詞。  
  
## <a name="examples"></a>範例  
 下列範例顯示條件式運算子的用法：  
  
```  
j = ( i < 0 ) ? ( -i ) : ( i );  
```  
  
 這個範例會將 `i` 的絕對值指派為 `j`。 如果 `i` 小於 0，會將 `-i` 指派至 `j`。 如果 `i` 大於或等於 0，則會將 `i` 指派至 `j`。  
  
```  
void f1( void );  
void f2( void );  
int x;  
int y;  
    .  
    .  
    .  
( x == y ) ? ( f1() ) : ( f2() );  
```  
  
 在此範例中會宣告兩個函式 (`f1` 和 `f2`) 及兩個變數 (`x` 和 `y`)。 稍後在程式中，如果兩個變數具有相同的值，便會呼叫 `f1` 函式。 否則會呼叫 `f2`。  
  
## <a name="see-also"></a>另請參閱  
 [條件運算子：? :](../cpp/conditional-operator-q.md)
