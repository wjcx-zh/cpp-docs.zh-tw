---
title: "reinterpret_cast 運算子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- reinterpret_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- reinterpret_cast keyword [C++]
ms.assetid: eb3283c7-7f88-467e-affd-407d37b46d6c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0957a696d7675a932aa86531d39f2e4895ba1ff9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="reinterpretcast-operator"></a>reinterpret_cast 運算子
可將所有指標轉換成任何其他指標類型。 也可將任何整數類資料類型轉換成任何指標類型 (反之亦然)。  
  
## <a name="syntax"></a>語法  
  
```  
reinterpret_cast < type-id > ( expression )  
```  
  
## <a name="remarks"></a>備註  
 誤用 `reinterpret_cast` 運算子非常不安全。 除非所需的轉換本質屬於低階轉換，否則您應使用其他任一轉型運算子。  
  
 `reinterpret_cast` 運算子可用於進行 `char*` 至 `int*` 或 `One_class*` 至 `Unrelated_class*` 之類的轉換，這類轉換原本就不安全。  
  
 除了轉型為原始類型外，無法將 `reinterpret_cast` 的結果用於其他安全的用途。 其他用途的最佳情況是不可攜。  
  
 `reinterpret_cast`運算子不能沒有**const**， `volatile`，或**__unaligned**屬性。 請參閱[const_cast 運算子](../cpp/const-cast-operator.md)如需移除這些屬性的資訊。  
  
 `reinterpret_cast` 運算子會將 null 指標值轉換為目的類型的 null 指標值。  
  
 `reinterpret_cast` 的實際用途之一是用於雜湊函式，雜湊函式會將值對應至索引，使兩個不同的值罕見地以相同索引結束。  
  
```  
#include <iostream>  
using namespace std;  
  
// Returns a hash code based on an address  
unsigned short Hash( void *p ) {  
   unsigned int val = reinterpret_cast<unsigned int>( p );  
   return ( unsigned short )( val ^ (val >> 16));  
}  
  
using namespace std;  
int main() {  
   int a[20];  
   for ( int i = 0; i < 20; i++ )  
      cout << Hash( a + i ) << endl;  
}  
  
Output:   
64641  
64645  
64889  
64893  
64881  
64885  
64873  
64877  
64865  
64869  
64857  
64861  
64849  
64853  
64841  
64845  
64833  
64837  
64825  
64829  
```  
  
 `reinterpret_cast` 允許將指標視為整數類資料類型。 結果隨即位元移位並與其本身 XOR，以產生唯一的索引 (高可攜性獨有)。 之後，標準 C-Style 轉換會將該索引截斷為函式的傳回型別。  
  
## <a name="see-also"></a>請參閱  
 [轉型運算子](../cpp/casting-operators.md)   
 [關鍵字](../cpp/keywords-cpp.md)