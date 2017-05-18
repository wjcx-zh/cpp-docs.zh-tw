---
title: "一元算術運算子 | Microsoft Docs"
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
- operators [C], unary
- tilde (~) one's complement operator
- bitwise-complement operator
- arithmetic operators [C++], unary
- + operator, unary operators
- unary operators
- exclamation points
- ~ operator, one's complement operator
- logical negation
- '! operator, unary arithmetic operators'
ms.assetid: 78c91415-d469-499e-9dfe-4435350fd333
caps.latest.revision: 6
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 875fd5c87583f93a647cf51907d897603f923e7e
ms.contentlocale: zh-tw
ms.lasthandoff: 04/01/2017

---
# <a name="unary-arithmetic-operators"></a>一元算術運算子
下列清單中討論 C 的一元加法、算術負數、補數和邏輯負運算子：  
  
|運算子|描述|  
|--------------|-----------------|  
|**+**|在運算式前方括號內的一元加法運算子會強制執行以括號括住之作業的群組。 它可用於搭配包含多個聯結或交替二元運算子的運算式。 運算元必須具有算術類型。 結果會是運算元的值。 整數運算元會經歷整數提升的過程。 運算結果的類型會是提升後運算元的類型。|  
|**-**|算術負數運算子會產生其運算元的負數 (二的補數)。 運算元必須是整數或浮動值。 這個運算子會執行一般算術轉換。|  
|`~`|位元補數 (或位元 NOT) 運算子會產生其運算元的位元補數。 運算元必須是整數類型。 此運算子會執行一般算術轉換；結果會是運算元在轉換之後的類型。|  
|**!**|如果其運算元為 true (非零)，邏輯負 (邏輯 NOT) 運算子會得到值 0，如果其運算元為 false (0)，則得到值 1。 結果為 `int` 類型。 運算元必須是整數、浮動或指標值。|  
  
 在指標上進行一元算術運算是不合法的。  
  
## <a name="examples"></a>範例  
 下列範例說明一元算術運算子：  
  
```  
short x = 987;  
    x = -x;  
```  
  
 在上述範例中，`x` 的新值為負 987 (或 -987)。  
  
```  
unsigned short y = 0xAAAA;  
    y = ~y;  
```  
  
 在這個範例中，指派給 `y` 的新值是不帶正負號的值 0xAAAA 或 0x5555 的 1 補數。  
  
```  
if( !(x < y) )  
```  
  
 如果 `x` 的值大於或等於 `y` 的值，則運算式的結果為 1 (true)。 如果 `x` 小於 `y`，則結果為 0 (false)。  
  
## <a name="see-also"></a>另請參閱  
 [具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)
