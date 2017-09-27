---
title: "資料類型範圍 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- unsigned
- wchar_t
- char
- signed
- short
- long
- double
- float
- int
- long_double
dev_langs:
- C++
helpviewer_keywords:
- float keyword [C++]
- char keyword [C++]
- unsigned long
- __wchar_t keyword [C++]
- unsigned short int
- enum keyword
- unsigned char keyword [C++]
- integer data type, data type ranges
- int data type
- data types [C++], ranges
- unsigned int
- short data type
- short int data
- signed types [C++], data type ranges
- long long keyword [C++]
- long double keyword [C++]
- double data type, data type ranges
- signed short int
- unsigned short
- sized integer types
- signed int
- signed long int
- signed char keyword [C++]
- wchar_t keyword [C++]
- long keyword [C++]
- ranges [C++]
- unsigned types [C++], data type ranges
- floating-point numbers, data type ranges
- ranges [C++], data types
- long int keyword [C++]
- unsigned long int
ms.assetid: 3691ceca-05fb-4b82-b1ae-5c4618cda91a
caps.latest.revision: 25
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 372d65a3d862fee4fddc2c9ba67c94341d1a6c87
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="data-type-ranges"></a>資料類型範圍
Visual C++ 32 位元和 64 位元編譯器會辨識本文稍後所提供表格中的類型。  
  
-   `int` (`unsigned int`)  
  
-   `__int8` (`unsigned __int8`)  
  
-   `__int16` (`unsigned __int16`)  
  
-   `__int32` (`unsigned __int32`)  
  
-   `__int64` (`unsigned __int64`)  
  
-   `short` (`unsigned short`)  
  
-   `long` (`unsigned long`)  
  
-   `long` `long` (`unsigned long long`)  
  
 如果其名稱開頭為兩個底線 (`__`)，則資料類型是非標準的。  
  
 下表中指定的範圍是兩端皆包含。  
  
|類型名稱|位元組|其他名稱|值的範圍|  
|---------------|-----------|-----------------|---------------------|  
|int|4|signed|-2,147,483,648 至 2,147,483,647|  
|unsigned int|4|unsigned|0 到 4,294,967,295|  
|__int8|1|char|-128 到 127|  
|unsigned __int8|1|unsigned char|0 到 255|  
|__int16|2|short、short int、signed short int|-32,768 到 32,767|  
|unsigned __int16|2|unsigned short、unsigned short int|0 到 65,535|  
|__int32|4|signed、signed int、int|-2,147,483,648 至 2,147,483,647|  
|unsigned __int32|4|unsigned、unsigned int|0 到 4,294,967,295|  
|__int64|8|long long、signed long long|-9,223,372,036,854,775,808 到 9,223,372,036,854,775,807|  
|unsigned __int64|8|unsigned long long|0 到 18,446,744,073,709,551,615|  
|bool|1|無|false 或 true|  
|char|1|無|-128 至 127 預設<br /><br /> 使用 [/J](../build/reference/j-default-char-type-is-unsigned.md)編譯時為 0 至 255|  
|signed char|1|無|-128 到 127|  
|unsigned char|1|無|0 到 255|  
|short|2|short int、signed short int|-32,768 到 32,767|  
|unsigned short|2|unsigned short int|0 到 65,535|  
|long|4|long int、signed long int|-2,147,483,648 至 2,147,483,647|  
|unsigned long|4|unsigned long int|0 到 4,294,967,295|  
|long long|8|無 (但是相當於 __int64)|-9,223,372,036,854,775,808 到 9,223,372,036,854,775,807|  
|unsigned long long|8|無 (但是相當於 unsigned __int64)|0 到 18,446,744,073,709,551,615|  
|enum|視情況而定|無| |  
|浮動|4|無|3.4E +/- 38 (7 位數)|  
|double|8|無|1.7E +/- 308 (15 位數)|  
|長雙精度|與 double 相同|無|與 double 相同|  
|wchar_t|2|__wchar_t|0 到 65,535|  
  
 根據用法， `__wchar_t` 的變數會指定寬字元類型或多位元組字元類型。 在字元或字串常數之前使用 `L` 前置詞可指定寬字元類型常數。  
  
 `signed` 和 `unsigned` 為修飾詞，可搭配任何整數類資料類型使用，但不包括 `bool`。 請注意， `char`、 `signed char`和 `unsigned char` 是三個適用於像是多載和範本機制的不同類型。  
  
 `int` 和 `unsigned int` 類型的大小為四個位元組。 不過，可攜式程式碼不應依賴 `int` 的大小，因為語言標準允許依實作的特定用法。  
  
 Visual Studio 中的 C/C++ 也支援具大小的整數類型。 如需詳細資訊，請參閱 [__int8、\___int16、\___int32、\___int64](../cpp/int8-int16-int32-int64.md) 和[整數限制](../cpp/integer-limits.md)。  
  
 如需每個類型之大小限制的詳細資訊，請參閱[基本類型](../cpp/fundamental-types-cpp.md)。  
  
 列舉類型的範圍會根據語言內容和指定的編譯器旗標而變更。 如需詳細資訊，請參閱 [C 列舉宣告](../c-language/c-enumeration-declarations.md) 和 [列舉](../cpp/enumerations-cpp.md)。  
  
## <a name="see-also"></a>另請參閱  
 [關鍵字](../cpp/keywords-cpp.md)   
 [基本類型](../cpp/fundamental-types-cpp.md)
