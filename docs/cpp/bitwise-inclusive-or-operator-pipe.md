---
title: "位元包含 OR 運算子: | |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- bitor
- '|'
dev_langs: C++
helpviewer_keywords:
- OR operator [C++], bitwise inclusive
- bitwise operators [C++], OR operator
- inclusive OR operator
- '| operator'
ms.assetid: 4c8a6a68-d828-447d-875a-aedb4ce3aa9a
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 792a5ef5576f68925459d8e7a34168afa11871c5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="bitwise-inclusive-or-operator-"></a>位元非互斥 OR 運算子：|
## <a name="syntax"></a>語法  
  
```  
  
expression   
|  
 expression  
  
```  
  
## <a name="remarks"></a>備註  
 位元包含 OR 運算子 (**&#124;**) 會比較其第二個運算元的對應位元的第一個運算元的每個位元。 如果任一位元為 1，則對應結果位元會設為 1。 否則，對應結果位元會設為 0。  
  
 位元包含 OR 運算子的兩個運算元都必須為整數類資料類型。 中涵蓋的一般算術轉換[標準轉換](standard-conversions.md)適用於這些運算元。  
  
## <a name="operator-keyword-for-124"></a>運算子關鍵字 &#124;  
 `bitor`運算子相當於文字的**&#124;**。 有兩種方式來存取`bitor`您程式中的運算子： 包含標頭檔`iso646.h`，或使用編譯[/Za](../build/reference/za-ze-disable-language-extensions.md) （停用語言擴充功能） 編譯器選項。  
  
## <a name="example"></a>範例  
  
```  
// expre_Bitwise_Inclusive_OR_Operator.cpp  
// compile with: /EHsc  
// Demonstrate bitwise inclusive OR  
#include <iostream>  
using namespace std;  
  
int main() {  
   unsigned short a = 0x5555;      // pattern 0101 ...  
   unsigned short b = 0xAAAA;      // pattern 1010 ...  
  
   cout  << hex << ( a | b ) << endl;   // prints "ffff" pattern 1111 ...  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [C + + 內建運算子、 優先順序和關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [C 位元運算子](../c-language/c-bitwise-operators.md)

