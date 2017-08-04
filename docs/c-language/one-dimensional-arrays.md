---
title: "一維陣列 | Microsoft Docs"
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
- brackets [ ]
- brackets [ ], arrays
- one-dimensional arrays
- arrays [C++], one-dimensional
- square brackets [ ]
- square brackets [ ], arrays
- subscript expressions
ms.assetid: e28536e5-3b77-46b5-97fd-9b938c771816
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
ms.openlocfilehash: 0edd36d539fe597bec8fc34a8c7e4e0e3b8e526a
ms.contentlocale: zh-tw
ms.lasthandoff: 05/18/2017

---
# <a name="one-dimensional-arrays"></a>一維陣列
後置運算式 (postfix expression) 後面跟著以方括號 (**[ ]**) 括住的運算式，是以註標方式來表示的陣列物件元素。 當註標運算式如下表示時，代表 *expression* 於 *postfix-expression* 之外的所在位置位址值：  
  
```  
  
postfix-expression  
[  
expression  
]  
  
```  
  
 通常，*postfix-expression* 所代表的值是指標值，例如陣列識別項，而 *expression* 則是整數值。 不過，在語法上需要的是其中一個指標類型的運算式，另一個則是整數類型。 因此，整數值可以在 *postfix-expression* 位置，而指標值則可以在 *expression* 的括號中，或是在註標位置。 例如，以下這個程式碼是合法的：  
  
```  
// one_dimensional_arrays.c  
int sum, *ptr, a[10];  
int main() {  
   ptr = a;  
   sum = 4[ptr];  
}  
```  
  
 註標運算式通常用來參考陣列元素，但是您可以將註標套用到任何指標。 無論值的順序為何，*expression* 都必須以方括號 (**[ ]**) 括住。  
  
 評估註標運算式的方式是在指標值中加入整數值，然後將間接運算子 (**\***) 套用到結果。 (如需間接運算子的相關討論，請參閱[間接和傳址運算子](../c-language/indirection-and-address-of-operators.md))。實際上，假設 `a` 是指標而 `b` 是整數，下列四個運算式對一維陣列而言是相等的：  
  
```  
a[b]  
*(a + b)  
*(b + a)  
b[a]  
```  
  
 根據加法運算子的轉換規則 (請參閱[加法類運算子](../c-language/c-additive-operators.md))，會藉由將整數值乘以指標定址之類型的長度，將整數值轉換為位址位移。  
  
 例如，假設識別項 `line` 參考 `int` 值的陣列。 下列程序用於評估註標運算式 `line[ i ]`：  
  
1.  整數值 `i` 乘以定義為 `int` 項目長度的位元組數目。 `i` 的轉換值代表 `i` `int` 位置。  
  
2.  轉換後的值會和原始指標值 (`line`) 相加，產生從 `line` 位移 `i` `int` 個位置的位址。  
  
3.  將間接運算子套用至新的位址。 結果是在該位置之陣列元素 (憑直覺是 `line [ i ]`) 的值。  
  
 註標運算式 `line[0]` 代表該行第一個元素的值，因為從 `line` 代表的位址位移是 0。 同樣地，運算式 (如 `line[5]`) 會參考從程式行位移五個位置的元素，或是陣列的第六個元素。  
  
## <a name="see-also"></a>另請參閱  
 [註標運算子：](../cpp/subscript-operator.md)
