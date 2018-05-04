---
title: __int8、 __int16、 __int32、 __int64 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __int8_cpp
- __int16_cpp
- __int32_cpp
- __int64_cpp
dev_langs:
- C++
helpviewer_keywords:
- __int16 keyword [C++]
- integer data type [C++], integer types in C++
- __int32 keyword [C++]
- integer types [C++]
- __int8 keyword [C++]
- __int64 keyword [C++]
ms.assetid: 8e384602-2578-4980-8cc8-da63842356b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8083d37d2526820ccd75104f9ee8a748eb5d33bc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="int8-int16-int32-int64"></a>__int8、__int16、__int32、__int64
## <a name="microsoft-specific"></a>Microsoft 特定的  
 Microsoft C/C++ 的功能支援可調整大小的整數類型。 您可以使用來宣告 8-16、 32 或 64 位元整數變數 **__int * * * n*類型規範，其中*n*是 8、 16、 32 或 64。  
  
 下列範例為其中每個可調整大小整數類型宣告一個變數：  
  
```  
__int8 nSmall;      // Declares 8-bit integer  
__int16 nMedium;    // Declares 16-bit integer  
__int32 nLarge;     // Declares 32-bit integer  
__int64 nHuge;      // Declares 64-bit integer  
```  
  
 類型 `__int8`、`__int16` 和 `__int32` 對於相同大小的 ANSI 類型是同義字，適用於撰寫跨多重平台作用完全相同的可攜式程式碼。 `__int8`資料類型是類型的同義詞`char`，`__int16`與類型**簡短**，和`__int32`與類型`int`。 `__int64`類型是類型的同義詞`long long`。  
  
## <a name="example"></a>範例  
 下列範例顯示 __int*xx*參數將會升級為`int`:  
  
```  
// sized_int_types.cpp  
  
#include <stdio.h>  
  
void func(int i) {  
    printf_s("%s\n", __FUNCTION__);  
}  
  
int main()  
{  
    __int8 i8 = 100;  
    func(i8);   // no void func(__int8 i8) function  
                // __int8 will be promoted to int  
}  
```  
  
```Output  
func  
```  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [關鍵字](../cpp/keywords-cpp.md)   
 [基本類型](../cpp/fundamental-types-cpp.md)   
 [資料類型範圍](../cpp/data-type-ranges.md)