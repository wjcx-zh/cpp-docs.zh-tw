---
title: "位元移位運算子 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], bitwise
- shift operators, bitwise
- bitwise-shift operators
- operators [C++], shift
ms.assetid: d0485785-5c72-47e1-a7c0-0adde03ade23
caps.latest.revision: 10
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
translationtype: Human Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 54cd2dad24563082c820999ff53e17b4d04380f7
ms.lasthandoff: 04/01/2017

---
# <a name="bitwise-shift-operators"></a>位元移位運算子
移位運算子會按照第二個運算元所指定的位置數目將其第一個運算元左移 (`<<`) 或右移 (`>>`)。  
  
## <a name="syntax"></a>語法  
 *shift-expression*：  
 *additive-expression*  
  
 *shift-expression*  `<<`  *additive-expression shift-expression*  `>>`  *additive-expression*  
  
 兩個運算元都必須是整數值。 這些運算子會執行一般算術轉換；結果類型是左運算元在轉換之後的類型。  
  
 向左移位空出的右位元設為 0。 向右移位空出的左位元則會根據轉換後第一個運算元的類型填入。 如果類型是 `unsigned`，則會設為 0。 否則均會填入正負號位元的複本。 若是沒有溢位的左移運算子，陳述式  
  
```  
expr1 << expr2   
```  
  
 等於乘以 2<sup>expr2</sup>。 若為右移運算子，  
  
```  
expr1 >> expr2   
```  
  
 等於除以 2<sup>expr2</sup> (如果 `expr1` 不帶正負號或有非負值)。  
  
 如果第二個運算元是負數，或者右運算元大於或等於已提升之左運算元的位元寬度，則不會定義移位運算的結果。  
  
 由於移位運算子所執行的轉換不提供溢位或反向溢位條件，因此，如果移位運算的結果無法以第一個運算元轉換後的類型表示，則可能會遺失資訊。  
  
```  
unsigned int x, y, z;  
  
x = 0x00AA;  
y = 0x5500;  
  
z = ( x << 8 ) + ( y >> 8 );  
```  
  
 在此範例中，`x` 會左移八個位置，`y` 則會右移八個位置。 移位的值會相加，指定 0xAA55，然後指派給 `z`。  
  
 將負值右移會產生原始值的一半 (無條件捨去)。 例如，-253 (二進位 11111111 00000011) 向右移位一個位元會產生 -127 (二進位 11111111 10000001)。 正 253 向右移位會產生 +126。  
  
 向右移位會保留正負號位元。 當帶正負號的整數向右移位時，最高有效位元會保持原位。 當不帶正負號的整數向右移位時，會清除最高有效位元。  
  
## <a name="see-also"></a>另請參閱  
 [左移和右移運算子 (>> 和 <<)](../cpp/left-shift-and-right-shift-operators-input-and-output.md)
