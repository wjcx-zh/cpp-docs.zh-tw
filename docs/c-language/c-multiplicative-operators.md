---
title: "C 乘法類運算子 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- arithmetic operators [C++], multiplicative operators
- / operator
- / operator, multiplicative operators
- remainder operator (%)
- operators [C], multiplication
- '% operator'
- slash (/) operator
- multiplication operator [C++], multiplicative operators
ms.assetid: 495471c9-319b-4eb4-bd97-039a025fd3a9
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 77b87e796f71258086aadd5aa6da9845de8095c5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="c-multiplicative-operators"></a>C 乘法類運算子
乘法類運算子會執行乘法 (**\***)、除法 (**/**) 和餘數 (`%`) 運算。  
  
 **語法**  
  
 *multiplicative-expression*：  
 *cast-expression*  
  
 *multiplicative-expression*  **\***  *cast-expression*  
  
 *multiplicative-expression*  **/**  *cast-expression*  
  
 *multiplicative-expression*  **%**  *cast-expression*  
  
 餘數運算子 (`%`) 的運算元必須為整數。 乘法 (**\***) 和除法 (**/**) 運算子可以接受整數類資料類型或浮點數類型運算元，運算元的類型可以不同。  
  
 乘法類運算子會對運算元執行一般算術轉換。 結果的類型是轉換後的運算元類型。  
  
> [!NOTE]
>  由於乘法類運算子所執行的轉換不提供溢位或反向溢位條件，因此，如果乘法類運算的結果無法以轉換後的運算元類型表示，則資訊可能會遺失。  
  
 C 乘法類運算子描述如下：  
  
|運算子|說明|  
|--------------|-----------------|  
|**\***|乘法運算子會使它的兩個運算元相乘。|  
|**/**|除法運算子會使第一個運算元除以第二個運算元。 如果兩個整數運算元相除且結果不是整數，則會根據下列規則截斷：|  
||-   根據 ANSI C 標準，除以 0 的結果是未定義。 Microsoft C 編譯器會在編譯時期或執行階段產生錯誤。|  
||-   如果兩個運算元都是正數或不帶正負號，結果會截斷小數點以下的小數部分。|  
||-   如果任一個運算元為負數，運算的結果為小於或等於代數商的最大整數或是大於或等於代數商的最小整數，是由實作所定義。 (請參閱下面的＜Microsoft 專有＞一節)。|  
|`%`|第一個運算元除以第二個時，餘數運算子的結果就是餘數。 當除法不精確時，結果會以下列規則決定：|  
||-   如果右運算元為零，則結果會是未定義。|  
||-   如果兩個運算元都是正數或不帶正負號，則結果為正數。|  
||-   如果任一個運算元為負數且結果不精確，則結果為實作所定義。 (請參閱下面的＜Microsoft 專有＞一節)。|  
  
 **Microsoft 特定的**  
  
 在任一個運算元為負數的除法中，攔截的方向為小數點以下的小數部分。  
  
 如果具有餘數運算子的除法中任一項運算為負數，則結果的正負號會與被除數 (運算式中的第一個運算元) 相同。  
  
 **END Microsoft 特定的**  
  
## <a name="examples"></a>範例  
 下面顯示的宣告用於下列範例：  
  
```  
int i = 10, j = 3, n;  
double x = 2.0, y;  
```  
  
 這個陳述式使用乘法運算子：  
  
```  
y = x * i;  
```  
  
 在這個案例中，`x` 會乘以 `i` 並得出值 20.0。 結果為 **double** 類型。  
  
```  
n = i / j;  
```  
  
 在這個範例中，10 是除以 3。 結果會截斷小數點以下的小數部分，產生整數值 3。  
  
```  
n = i % j;  
```  
  
 當 10 除以 3 時，這個陳述式會指派整數餘數 1 給 `n`。  
  
 **Microsoft 特定的**  
  
 餘數的正負號與被除數的正負號相同。 例如：  
  
```  
50 % -6 = 2  
-50 % 6 = -2  
```  
  
 在每個案例中，`50` 和 `2` 具有相同的正負號。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [乘法類運算子和模數運算子](../cpp/multiplicative-operators-and-the-modulus-operator.md)