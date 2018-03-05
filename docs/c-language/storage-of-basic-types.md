---
title: "基本類型的儲存空間 | Microsoft Docs"
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dff8df934a0c812ca798d5a1e87188e2468902ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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