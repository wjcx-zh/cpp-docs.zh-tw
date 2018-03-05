---
title: "位元 AND 運算子： &amp; |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- bitand
dev_langs:
- C++
helpviewer_keywords:
- AND operator
- bitwise operators [C++], AND operator
- '& operator [C++], bitwise operators'
ms.assetid: 76f40de3-c417-47b9-8a77-532f3fc990a5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f3d74a39c68e4c16e55837a87e027e9e5991351f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="bitwise-and-operator-amp"></a>位元 AND 運算子：&amp;
## <a name="syntax"></a>語法  
  
```  
  
expression   
&  
 expression  
  
```  
  
## <a name="remarks"></a>備註  
 運算式可以是其他 and 運算式或 (受限於如下所述的限制) 相等的運算式、關聯運算式，加法運算式、乘法運算式、成員運算式的指標、cast 運算式、一元運算式、後置運算式或主要運算式。  
  
 位元 AND 運算子 (**&**) 比較的第二個運算元的對應位元的第一個運算元的每個位元。 如果兩個位元皆為 1，則對應的結果位元會設為 1。 否則，對應結果位元會設為 0。  
  
 位元 AND 運算子的兩個運算元都必須為整數類型。 中涵蓋的一般算術轉換[標準轉換](standard-conversions.md)，適用於這些運算元。  
  
## <a name="operator-keyword-for-"></a>運算子關鍵字 （& s)  
 `bitand`運算子相當於文字的 **&** 。 有兩種方式來存取`bitand`您程式中的運算子： 包含標頭檔`iso646.h`，或使用編譯[/Za](../build/reference/za-ze-disable-language-extensions.md) （停用語言擴充功能） 編譯器選項。  
  
## <a name="example"></a>範例  
  
```  
// expre_Bitwise_AND_Operator.cpp  
// compile with: /EHsc  
// Demonstrate bitwise AND  
#include <iostream>  
using namespace std;  
int main() {  
   unsigned short a = 0xFFFF;      // pattern 1111 ...  
   unsigned short b = 0xAAAA;      // pattern 1010 ...  
  
   cout  << hex << ( a & b ) << endl;   // prints "aaaa", pattern 1010 ...  
}  
```  
  
## <a name="see-also"></a>請參閱  
 [C++ 內建運算子、優先順序和順序關聯性](cpp-built-in-operators-precedence-and-associativity.md)  
 [C + + 內建運算子、 優先順序和關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 位元運算子](../c-language/c-bitwise-operators.md)