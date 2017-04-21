---
title: "類型 float | Microsoft Docs"
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
- type float
- exponent length
- float keyword [C]
- mantissas, length
- floating-point numbers, float type
- ranges, floating-point types
- floating-point numbers, variables
- lengths, mantissa
- double data type, type float
- IEEE floating-point representation
- lengths, exponent
ms.assetid: 706e332b-17a0-4a30-b7d8-5d6cd372524b
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
translationtype: Human Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 0f18df0dba0895699213fbb69ec02559e3d7f35b
ms.lasthandoff: 04/01/2017

---
# <a name="type-float"></a>類型 float
浮點數使用的是 IEEE (電子電機工程師協會) 格式。 浮點類型的單精確度值有 4 個位元組，包括正負號位元、8 位元的超 127 二進位指數和 23 位元的尾數。 尾數表示介於 1.0 和 2.0 之間的數字。 因為尾數的高序位位元永遠為 1，因此不會儲存在數字中。 若是 float 類型，此表示的範圍大約從 3.4E-38 到 3.4E+38。  
  
 您可以根據應用程式的需求，將變數宣告為 float 或 double。 這兩個類型之間的主要差異是它們可以表示的精確度、所需的儲存空間，以及範圍。 下表顯示精確度和儲存需求之間的關聯性。  
  
### <a name="floating-point-types"></a>浮點類型  
  
|類型|有效數字|位元組數|  
|----------|------------------------|---------------------|  
|浮動|6 - 7|4|  
|double|15 - 16|8|  
  
 浮點變數由尾數 (包含數字的值) 和指數 (包含數字範圍的順序) 表示。  
  
 下表顯示針對每個浮點類型配置之尾數和指數的位元數目。 所有 float 或 double 的最高有效位元一定是正負號位元。 如果是 1，則數字會被視為是負數，否則，會將其視為正數。  
  
### <a name="lengths-of-exponents-and-mantissas"></a>指數和尾數的長度  
  
|類型|指數長度|尾數長度|  
|----------|---------------------|---------------------|  
|float|8 位元|23 位元|  
|double|11 位元|52 位元|  
  
 由於指數是以不帶正負號的形式儲存，因此指數被偏移了其最大值的一半。 若是 float 類型，其偏差是 127，若是 double 類型，則為 1023。 您可以從指數值減去偏差值，以計算實際的指數值。  
  
 儲存為二進位分數的尾數會大於或等於 1 且小於 2。 對於 float 和 double 類型，其在最高有效位元位置的尾數中隱含前置數字 1，因此，尾數的長度實際上分別為 24 和 53 個位元，即使最高有效位元未曾儲存在記憶體中。  
  
 除了上述儲存方法之外，浮點封裝可以將二進位浮點數儲存為未標準化的數字。 「未標準化的數字」是非零的浮點數，其具有保留的指數值，即尾數的最高有效位元為 0。 使用未標準化的格式，浮點數的範圍可以擴充，不過會使精確度降低。 您無法控制浮點數是以標準化還是未標準化的形式表示，這是由浮點封裝來判斷表示方式。 除非指數小於標準化形式可以表示的最小值，否則浮點封裝不會使用未標準化的形式。  
  
 下表顯示您可以在每個浮點類型變數中儲存的最小值和最大值。 在下表中列出的值僅適用於標準化的浮點數，未標準化的浮點數具有較小的最小值。 請注意，在 80*x*87 暫存器中保存的數字一律會以 80 位元的標準化形式表示，若是儲存在 32 位元或 64 位元的浮點變數 (float 類型和 long 類型的變數) 中，則該數字只能以未標準化形式表示。  
  
### <a name="range-of-floating-point-types"></a>浮點類型的範圍  
  
|類型|最小值|最大值|  
|----------|-------------------|-------------------|  
|浮動|1.175494351 E - 38|3.402823466 E + 38|  
|double|2.2250738585072014 E - 308|1.7976931348623158 E + 308|  
  
 如果儲存空間的重要性大於精確度，請考慮使用 float 類型的浮點變數。 相反地，如果精確度是最重要的準則，請使用 double 類型。  
  
 浮點變數可以提升為精確度較高的類型 (從 float 類型提升為 double 類型)。 當您在執行浮點變數的算術運算時，最常發生變數類型提升的情形。 這個算術運算會盡可能使用與精確度等級最高之變數相同的精確度等級進行。 例如，請考慮下列類型宣告：  
  
```  
float f_short;  
double f_long;  
long double f_longer;  
  
f_short = f_short * f_long;  
```  
  
 在上述範例中，`f_short` 變數會提升為 double 類型，並與 `f_long` 相乘，再將結果四捨五入為 float 類型後指派給 `f_short`。  
  
 下列範例中 (使用前述範例的宣告)，會以變數的 float (32 位元) 精確度來進行算術運算，然後再將其結果提升為 double 類型：  
  
```  
f_longer = f_short * f_short;  
```  
  
## <a name="see-also"></a>另請參閱  
 [基本類型的儲存空間](../c-language/storage-of-basic-types.md)
