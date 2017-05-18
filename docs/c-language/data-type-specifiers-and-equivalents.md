---
title: "資料類型規範和對應項 | Microsoft Docs"
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
- type specifiers [C++], list
- widening integers
- data types [C++], equivalents
- sign-extending integral types
- zero-extending
- identifiers, data type
- data types [C++], specifiers
- simple types, names
- type names [C++], simple
ms.assetid: 0d4b515a-4f68-4786-83cf-a5d43c7cb6f3
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
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: de625abc04fcfde9d39205d024f09dc64d6c82ae
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="data-type-specifiers-and-equivalents"></a>資料類型規範和對應項
本書通常會使用下表中所列類型規範的格式，而不是完整格式，同時會依預設來假設 `char` 類型為帶正負號的類型。 因此，在本書中，`char` 相當於 **signed char**。  
  
### <a name="type-specifiers-and-equivalents"></a>類型規範及對等項目  
  
|類型規範|對等項目|  
|--------------------|---------------------|  
|**signed char**1|**char**|  
|**signed int**|**signed**、**int**|  
|**signed short int**|**short**、**signed short**|  
|**signed long int**|**long**、**signed long**|  
|**unsigned char**|—|  
|**unsigned int**|**unsigned**|  
|**unsigned short int**|**unsigned short**|  
|**unsigned long int**|**unsigned long**|  
|**float**|—|  
|**long double**2|—|  
  
 1   當您依預設使用不帶正符號的 **char** 類型時 (藉由指定 /J 編譯器選項)，無法將 **signed char** 縮寫為 **char**。  
  
 2   在 32 位元和 64 位元作業系統中，Microsoft C 編譯器會將 **long double** 對應到 **double** 類型。  
  
 **Microsoft 特定的**  
  
 您可以指定 /J 編譯器選項來將預設為帶正符號的 **char** 類型轉換為不帶正負號的類型。 當這個選項生效時，表示 **char** 與 **unsigned char** 相同；因此，您必須使用 **signed** 關鍵字來宣告帶正負號的字元值。 如果明確地將 **char** 值宣告為帶正負號類型時，/J 選項不會生效，且該值在擴展為 **int** 類型時，會以帶正負號的形式進行擴充。 **char** 類型在擴充至 **int** 類型時，是以零擴充的方式加以擴充。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [C 類型規範](../c-language/c-type-specifiers.md)
