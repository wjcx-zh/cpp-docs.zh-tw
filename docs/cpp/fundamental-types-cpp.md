---
title: 基本類型 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __int128_cpp
- __wchar_t_cpp
- char_cpp
- double_cpp
- float_cpp
- int_cpp
- long_cpp
- long_double_cpp
- short_cpp
- signed_cpp
- unsigned_cpp
- unsigned_int_cpp
- wchar_t_cpp
dev_langs:
- C++
helpviewer_keywords:
- specifiers [C++], type
- float keyword [C++]
- char keyword [C++]
- __wchar_t keyword [C++]
- signed types [C++], summary of data types
- Integer data type [C++], C++ data types
- arithmetic operations [C++], types
- int data type
- unsigned types [C++], summary of data types
- short data type [C++]
- double data type [C++], summary of types
- long long keyword [C++]
- long double keyword [C++]
- unsigned types [C++]
- signed types [C++]
- void keyword [C++]
- storage [C++], basic type
- integral types, C++
- wchar_t keyword [C++]
- floating-point numbers [C++], C++ data types
- long keyword [C++]
- type specifiers [C++]
- integral types
- long keyword [C++], C++ data types
- storing types [C++]
- data types [C++], void
ms.assetid: 58b0106a-0406-4b74-a430-7cbd315c0f89
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d91971b7d96b09fe1fd0d14a2a711f7771503a6a
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941472"
---
# <a name="fundamental-types--c"></a>基本類型 (C++)
C++ 中的基本類型分為三類：整數、浮點和 void。 整數類資料類型能夠處理整數。 浮點類型可以指定可能有小數部分的值。  
  
 [void](../cpp/void-cpp.md) 類型描述一組空值。 任何類型的變數**void**可以指定 — 它主要用來宣告沒有傳回值的函式或宣告泛型指標不具類型或任意具型別資料。 任何運算式可以明確地轉換或轉型為**void**。 不過，這類運算式僅限於下列用法：  
  
-   運算陳述式 (如需詳細資訊，請參閱 [運算式](../cpp/expressions-cpp.md))。  
  
-   逗號運算子的左運算元 (如需詳細資訊，請參閱 [逗號運算子](../cpp/comma-operator.md) )。  
  
-   條件運算子的第二個或第三個運算元 (`? :`)。 (如需詳細資訊，請參閱 [含條件運算子的運算式](../cpp/conditional-operator-q.md) )。  
  
 下表說明類型大小的限制。 這些限制與 Microsoft 實作無關。  
  
### <a name="fundamental-types-of-the-c-language"></a>C++ 語言的基本類型  
  
|分類|類型|內容|  
|--------------|----------|--------------|  
|整數|**char**|型別**char**是整數類資料類型通常包含基本執行字元集的成員 — 根據預設，這是 Microsoft c + + 中的 ASCII。<br /><br /> C + + 編譯器會將類型的變數**char**， **char&lt;3**，並**unsigned char**為具有不同的型別。 類型的變數**char**升級到**int**彷彿它們是型別**char&lt;3**根據預設，除非使用 /J 編譯選項。 在此情況下則會視為型別**unsigned char**並且升級到**int**不帶正負。|  
||**bool**|型別**bool**是整數類資料類型可以有兩個值的其中一個 **，則為 true**或是**false**。 它的大小並未指定。|  
||**short**|型別**short int** (簡稱**簡短**) 是大於或等於類型大小的整數類資料型別**char**，但短於或等於類型大小的**int**。<br /><br /> 類型的物件**簡短**可以宣告為**帶正負號短**或是**unsigned short**。 **帶正負號短**同義**簡短**。|  
||**int**|型別**int**大於或等於類型大小的整數類資料類型**short int**，但短於或等於類型大小**長**。<br /><br /> 類型的物件**int**可以宣告為**帶正負號 int**或是**不帶正負號的 int**。**帶正負號 int**同義**int**。|  
||**__int8**， **__int16**， **__int32**， **__int64**|可調整大小的整數 `__int n`，其中 `n` 是整數變數的大小 (以位元為單位)。 **__int8**， **__int16**， **__int32**並 **__int64**是 Microsoft 專有的關鍵字。 並非所有類型都都適用於所有架構。 (**__int128**不支援。)|  
||**long**|型別**長**(或**long int**) 是大於或等於類型大小的整數類資料型別**int**。<br /><br /> 類型的物件**長**可以宣告為**帶正負號長**或是**不帶正負號長**。 **帶正負號長**同義**長**。|  
||**long long**|大於不帶正負號**長**。<br /><br /> 類型的物件**長長**可以宣告為**簽署 long long**或**unsigned long long**。 **帶正負號長長**同義**long long**。|  
||**wchar_t**， **__wchar_t**|類型的變數**wchar_t**指定寬字元或多位元組字元類型。 根據預設， **wchar_t**原生類型，但您可以使用[/zc: wchar_t-](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)進行**wchar_t** typedef **unsigned short**。 **__Wchar_t**類型是原生 Microsoft 特有同義字**wchar_t**型別。<br /><br /> 在字元或字串常數之前使用 L 前置詞，指定寬字元類型。|  
|浮點|**float**|型別**浮點數**是最小的浮點類型。|  
||**double**|型別**雙**浮點數類型是大於或等於**float**，但短於或等於類型大小**長雙精度**。<br /><br /> Microsoft 專有： 的表示法**長雙精度**並**double**完全相同。 不過，**長雙精度**並**double**是不同的類型。|  
||**long double**|型別**長雙精度**是浮動點類型是大於或等於**double**。|  
  
 **Microsoft 專屬**  
  
 下表列出 Microsoft C++ 的基本類型所需的儲存空間量。  
  
### <a name="sizes-of-fundamental-types"></a>基本類型的大小  
  
|類型|大小|  
|----------|----------|  
|**bool**， **char**， **unsigned char**， **char&lt;3**， **__int8**|1 個位元組|  
|**__int16**，**簡短**， **unsigned short**， **wchar_t**， **__wchar_t**|2 個位元組|  
|**浮點數**， **__int32**， **int**，**不帶正負號的 int**， **long**，**不帶正負號長時間**|4 個位元組|  
|**雙精度浮點**， **__int64**，**長雙精度**， **long long**|8 個位元組|  
  
 **結束 Microsoft 專屬**  
  
 如需每個類型值範圍的摘要，請參閱 [資料類型範圍](../cpp/data-type-ranges.md) 。  
  
 如需類型轉換的詳細資訊，請參閱 [標準轉換](../cpp/standard-conversions.md)。  
  
## <a name="see-also"></a>另請參閱  
 [資料類型範圍](../cpp/data-type-ranges.md)