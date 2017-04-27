---
title: "整數類型 | Microsoft Docs"
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
- integer data type, integer types in C++
- integer constants
- integer types
- integers, types
ms.assetid: c8926a5e-0e98-4e37-9b05-ce97961379bd
caps.latest.revision: 7
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
ms.openlocfilehash: 7b03bfad7912aa74c5520f6dfc23f70856188f0e
ms.lasthandoff: 04/01/2017

---
# <a name="integer-types"></a>整數類型
每個整數常數都會根據其值和表示方式而被指定特定類型。 您可以將所有整數常數的類型強制指定為 **long**，方法是在常數結尾加上字母 **l** 或 **L**；也可以將其類型強制指定為 `unsigned`，方法是在其值後面加上 **u** 或 **U**。 小寫字母 **l** 與數字 1 容易混淆，應予以避免。 部分 **long** 形式的整數常數如下：  
  
```  
/* Long decimal constants */  
10L  
79L  
  
/* Long octal constants */  
012L  
0115L  
  
/* Long hexadecimal constants */  
0xaL or 0xAL  
0X4fL or 0x4FL  
  
/* Unsigned long decimal constant */  
776745UL  
778866LU  
```  
  
 您指派給常數的類型取決於該常數所代表的值。 常數的值必須介於其類型可以代表的值的範圍內。 常數的類型決定在運算式中使用該常數或套用負號 (**-**) 時所要執行的轉換。 這份清單摘要說明整數常數的轉換規則。  
  
-   十進位常數的類型 (沒有尾碼) 是 `int`、**long int** 或 **unsigned long int**。 在可以表示常數值的這三種類型中，會將第一種指派給常數。  
  
-   視常數的大小而定，指派給八進位和十六進位常數 (沒有尾碼) 的類型是 `int`、`unsigned int`、**long int** 或 **unsigned long int**。  
  
-   視常數的大小而定，指派給尾碼為 **u** 或 **U** 之常數的類型是 **unsigned int** 或 **unsigned long int**。  
  
-   視常數的大小而定，指派給尾碼為 **l** 或 **L** 之常數的類型是 **long int** 或 **unsigned long int**。  
  
-   指派給尾碼為 **u** 或 **U** 及 **l** 或 **L** 之常數的類型是 **unsigned long int**。  
  
## <a name="see-also"></a>另請參閱  
 [C 整數常數](../c-language/c-integer-constants.md)
