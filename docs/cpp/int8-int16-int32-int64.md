---
title: "__int8、__int16、__int32、__int64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__int8_cpp"
  - "__int64"
  - "__int8"
  - "__int16"
  - "__int16_cpp"
  - "__int64_cpp"
  - "__int32_cpp"
  - "__int32"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__int16 關鍵字 [C++]"
  - "__int32 關鍵字 [C++]"
  - "__int64 關鍵字 [C++]"
  - "__int8 關鍵字 [C++]"
  - "integer 資料類型, C++ 中的整數類型"
  - "整數類型 [C++]"
ms.assetid: 8e384602-2578-4980-8cc8-da63842356b2
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# __int8、__int16、__int32、__int64
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定的  
 Microsoft C\/C\+\+ 的功能支援可調整大小的整數類型。  您可以使用 **\_\_int***n* 類型規範來宣告 8、16、32 或 64 位元整數變數，其中 *n* 是 8、16、32 或 64。  
  
 下列範例為其中每個可調整大小整數類型宣告一個變數：  
  
```  
__int8 nSmall;      // Declares 8-bit integer  
__int16 nMedium;    // Declares 16-bit integer  
__int32 nLarge;     // Declares 32-bit integer  
__int64 nHuge;      // Declares 64-bit integer  
```  
  
 類型 `__int8`、`__int16` 和 `__int32` 對於相同大小的 ANSI 類型是同義字，適用於撰寫跨多重平台作用完全相同的可攜式程式碼。  `__int8` 資料類型與類型 `char` 是同義字，`__int16` 與類型 **short** 是同義字，`__int32` 與類型 `int` 是同義字。  `__int64` 類型沒有 ANSI 對等用法。  
  
## 範例  
 下列範例顯示 \_\_int*xx* 參數將提升至 `int`：  
  
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
  
  **func**   
## END Microsoft 特定的  
  
## 請參閱  
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [基本類型](../cpp/fundamental-types-cpp.md)   
 [資料類型範圍](../cpp/data-type-ranges.md)