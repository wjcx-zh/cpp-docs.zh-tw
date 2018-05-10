---
title: 基本類型的儲存空間 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- specifiers [C++], type
- integral types, storage
- storage [C++], types
- floating-point numbers, storage
- type specifiers [C++], sizes
- arithmetic operations [C++], types
- int data type
- short data type
- signed types [C++], storage
- long double keyword [C], storage
- long keyword [C]
- double data type, storage
- types [C], arithmetic
- integral types
- data types [C], specifiers
- storing types [C++]
- unsigned types [C++], storage
- data types [C], storage
ms.assetid: bd1f33c1-c6b9-4558-8a72-afb21aef3318
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eafe81dc684300cb7fdf65137c2f7e45010285b0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="storage-of-basic-types"></a>基本類型的儲存空間
下表摘要說明與每個基本類型相關聯的儲存區。  
  
### <a name="sizes-of-fundamental-types"></a>基本類型的大小  
  
|類型|存放裝置|  
|----------|-------------|  
|`char`、`unsigned char`、**signed char**|1 個位元組|  
|**short**、**unsigned short**|2 個位元組|  
|`int`, `unsigned int`|4 個位元組|  
|**long**、`unsigned long`|4 個位元組|  
|**float**|4 個位元組|  
|**double**|8 個位元組|  
|`long double`|8 個位元組|  
  
 C 資料類型屬於一般分類。 「整數類資料類型」包括 `char`、`int`、**short**、**long**、**signed**、`unsigned` 和 `enum`。 「浮點類型」包括 **float**、**double** 和 `long double`。 「算術類型」包括所有浮點和整數類資料類型。  
  
## <a name="see-also"></a>請參閱  
 [宣告和類型](../c-language/declarations-and-types.md)