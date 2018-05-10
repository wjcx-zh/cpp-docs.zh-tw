---
title: C 邏輯運算子 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- logical operators, expression sequence points
- logical operators, C
- logical AND operator
- '|| operator'
- operators [C], logical
- short-circuit evaluation
- '&& operator'
- logical OR operator
ms.assetid: c0a4e766-ad56-4300-bf76-b28dc0e19b43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f92adbeab4175178be8f41a09c4455d8a581131
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="c-logical-operators"></a>C 邏輯運算子
邏輯運算子會執行邏輯 AND (**&&**) 與邏輯 OR ( `||` ) 運算。  
  
 **語法**  
  
 *logical-AND-expression*：  
 *inclusive-OR-expression*  
  
 *logical-AND-expression*  **&&**  *inclusive-OR-expression*  
  
 *logical-OR-expression*：  
 *logical-AND-expression*  
  
 *logical-OR-expression*  **&#124;&#124;**  *logical-AND-expression*  
  
 邏輯運算子不會執行一般算術轉換。 它們會以等價於 0 的方式評估每個運算元。 邏輯運算的結果是 0 或 1。 結果的類型是 `int`。  
  
 C 邏輯運算子描述如下：  
  
|運算子|描述|  
|--------------|-----------------|  
|**&&**|若兩個運算元都有非零值，則邏輯 AND 運算子會產生值 1。 若任一運算元等於 0，則結果是 0。 若邏輯 AND 運算的第一個運算元等於 0，則不會評估第二個運算元。|  
|`&#124;&#124;`|邏輯 OR 運算子會在其運算元上執行包含 OR 運算。 若兩個運算元都有 0 值，則結果是 0。 若任一運算元有非零值，則結果是 1。 若邏輯 OR 運算的第一個運算元有非零值，則不會評估第二個運算元。|  
  
 邏輯 AND 與邏輯 OR 運算式的運算元是從左到右評估。 若第一個運算元的值就足以決定運算結果，則不會評估第二個運算元。 這稱為「最少運算」(Short-circuit) 求值。 第一個運算元後方有一個序列點。 如需詳細資訊，請參閱[序列點](../c-language/c-sequence-points.md)。  
  
## <a name="examples"></a>範例  
 下列範例說明邏輯運算子：  
  
```  
int w, x, y, z;  
  
if ( x < y && y < z )  
    printf( "x is less than z\n" );  
```  
  
 在此範例中，若 `x` 小於 `y` 且 `y` 小於 `z`，則會呼叫 `printf` 函式以列印訊息。 若 `x` 大於 `y`，則不會評估第二個運算元 (`y < z`)，而且不會列印任何內容。 請注意，在第二個運算元有副作用 (有其他項目因為某些其他原因仰賴此運算元) 的情況中，這可能會造成問題。  
  
```  
printf( "%d" , (x == w || x == y || x == z) );  
```  
  
 在此範例中，如果 `x` 等於 `w`、`y` 或 `z`，則 `printf` 函式的第二個引數判斷值為 true，並且列印值 1。 否則，它的判斷值為 false，並且印出值 0。 只要其中一項條件的判斷值為 true，求值就會停止。  
  
## <a name="see-also"></a>請參閱  
 [邏輯 AND 運算子：&&](../cpp/logical-and-operator-amp-amp.md)   
 [邏輯 OR 運算子：&#124;&#124;](../cpp/logical-or-operator-pipe-pipe.md)