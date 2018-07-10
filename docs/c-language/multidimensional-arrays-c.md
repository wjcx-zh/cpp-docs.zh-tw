---
title: 多維陣列 (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- arrays [C], multidimensional
- multidimensional arrays
- subscript expressions
ms.assetid: 4ba5c360-1f17-4575-b370-45f62e1f2bc2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 25ca58d9818782b51e6c07bb6bb758948adab3ae
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32387950"
---
# <a name="multidimensional-arrays-c"></a>多維陣列 (C)
註標運算式也可以擁有多個註標，如下所示：  
  
```  
  
expression1  
[  
expression2  
] [  
expression3  
]...  
```  
  
 註標運算式的關聯是由左至右。 最左邊的下標運算式 *expression1 ***[*** expression2***]** 會最先評估。 *expression1* 和 *expression2* 相加所產生的位址會形成指標運算式，然後 *expression3* 會加入這個指標運算式形成新的指標運算式，依此類推，直到加入最後一個註標運算式為止。 除非最後一個指標值會定址陣列類型 (請參閱以下範例)，否則間接取值運算子 (**\***) 會在評估最後一個註標運算式之後套用。  
  
 具有多個註標的運算式會參考「多維陣列」的元素。 所謂的多維陣列是指其中所包含的元素也是一種陣列。 例如，三維陣列的第一個元素是具有兩個維度的陣列。  
  
## <a name="examples"></a>範例  
 在下列範例中，名為 `prop` 的陣列中宣告了三個元素，每個元素都是 4x6 的 `int` 值陣列。  
  
```  
int prop[3][4][6];  
int i, *ip, (*ipp)[6];  
```  
  
 `prop` 陣列參考的外觀如下：  
  
```  
i = prop[0][0][1];  
```  
  
 上述範例示範如何參考 `int` 的第二個個別 `prop` 元素。 陣列會依資料列儲存，因此最後一個註標變化的速度更快，而 `prop[0][0][2]` 運算式會參考陣列的下一個 (第三個) 元素，依此類推。  
  
```  
i = prop[2][1][3];  
```  
  
 這個陳述式對於 `prop` 的個別元素來說是更為複雜的參考。 運算式評估如下：  
  
1.  第一個註標 `2` 會乘以 4x6 `int` 陣列的大小，並且增加至指標值 `prop`。 結果會指向 `prop` 的第三個 4x6 陣列。  
  
2.  第二個註標 `1` 會乘以 6 個元素 `int` 陣列的大小，並且增加至 `prop[2]` 所代表的位址。  
  
3.  6 個元素陣列的每個元素都是 `int` 值，因此最後一個註標 `3` 會先乘以 `int` 的大小，再增加至 `prop[2][1]`。 產生的指標會定址 6 個元素陣列的第四個元素。  
  
4.  間接運算子會套用至指標值。 結果會是位於該位址的 `int` 元素。  
  
 接下來的兩個範例將示範未套用間接運算子的案例。  
  
```  
ip = prop[2][1];  
  
ipp = prop[2];  
```  
  
 在第一個陳述式中，運算式 `prop[2][1]` 為三維陣列 `prop` 的有效參考，它會參考 6 個元素的陣列 (上面所宣告)。 由於指標值會定址陣列，因此不會套用間接運算子。  
  
 同樣地，第二個陳述式 `prop[2]` 中 `ipp = prop[2];` 運算式的結果是定址二維陣列的指標值。  
  
## <a name="see-also"></a>請參閱  
 [註標運算子：](../cpp/subscript-operator.md)