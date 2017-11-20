---
title: "C 浮點常數 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- types [C], constants
- floating-point numbers, floating-point constants
- constants, floating-point
- floating-point constants
- floating-point constants, about floating-point constants
- double data type, floating-point constants
ms.assetid: e1bd9b44-d6ab-470c-93e5-07142c7a2062
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7bd4bd3e0dc2dcd1388c7e8db5c9fcf209a9b47c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="c-floating-point-constants"></a>C 浮點常數
「浮點常數」是代表帶正負號實數的十進位數字。 帶正負號的實數表示包含整數部分、分數部分和指數。 使用浮點常數表示不能變更的浮點值。  
  
## <a name="syntax"></a>語法  
 *floating-point-constant*：  
 &nbsp;&nbsp; *fractional-constant exponent-part*<sub>opt</sub> *floating-suffix*<sub>opt</sub>  
 &nbsp;&nbsp; *digit-sequence exponent-part floating-suffix*<sub>opt</sub>  
  
 *fractional-constant*：  
 &nbsp;&nbsp; *digit-sequence*<sub>opt</sub> **.** *digit-sequence*  
 &nbsp;&nbsp; *digit-sequence*  **.**  
  
 *exponent-part*：  
 &nbsp;&nbsp; **e**  *sign*<sub>opt</sub> *digit-sequence*  
 &nbsp;&nbsp; **E**  *sign*<sub>opt</sub> *digit-sequence*  
  
 *sign*：下列其中一個  
 &nbsp;&nbsp; **+ -**  
  
 *digit-sequence*：  
 &nbsp;&nbsp; *digit*  
 &nbsp;&nbsp; *digit-sequence digit*  
  
 *floating-suffix*：下列其中一個  
 &nbsp;&nbsp; **f l F L**  
  
 您可以省略小數點之前的數字 (值的整數部分)，或小數點之後的數字 (分數部分)，但不能省略兩者。 只有在加入指數時，才可以省略小數點。 不能使用空白字元分隔常數的數字或字元。  
  
 下列範例說明某些形式的浮點常數和表示式︰  
  
```  
15.75  
1.575E1   /* = 15.75   */  
1575e-2   /* = 15.75   */  
-2.5e-3   /* = -0.0025 */  
25E-4     /* =  0.0025 */  
```  
  
 除非前面加上負號 (**-**)，否則浮點常數為正數。 此時，負號會視為一元算術負運算子。 浮點常數有 `float`、`double` 或 `long double` 型別。  
  
 沒有**f**、**F**、**l** 或 **L** 後置字元的浮點常數是 `double` 型別。 如果後置字元是字母 **f** 或 **F**，常數則是 `float` 型別。 如果後置字元是字母 **l** 或 **L**，則是 `long double` 型別。 例如:   
  
```  
100L  /* Has type long double  */  
100F  /* Has type float        */  
```  
  
 請注意，Microsoft C 編譯器在內部將 `long double` 表示為 `double` 型別。 請參閱[基本型別的儲存空間](../c-language/storage-of-basic-types.md)了解 `double`、`float` 和 `long double` 型別的相關資訊。  
  
 您可以省略浮點常數的整數部分，如下列範例所示。 數字 .75 可以包括下列多種方式表示︰  
  
```  
.0075e2  
0.075e1  
.075e1  
75e-2  
```  
  
## <a name="see-also"></a>另請參閱  
 [C 常數](../c-language/c-constants.md)