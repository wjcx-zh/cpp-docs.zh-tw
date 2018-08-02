---
title: reinterpret_cast 運算子 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- reinterpret_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- reinterpret_cast keyword [C++]
ms.assetid: eb3283c7-7f88-467e-affd-407d37b46d6c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 27522cb4d3bb15912b7988e0152a121616480330
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464830"
---
# <a name="reinterpretcast-operator"></a>reinterpret_cast 運算子
可將所有指標轉換成任何其他指標類型。 也可將任何整數類資料類型轉換成任何指標類型 (反之亦然)。  
  
## <a name="syntax"></a>語法  
  
```  
reinterpret_cast < type-id > ( expression )  
```  
  
## <a name="remarks"></a>備註  
 誤用**reinterpret_cast**運算子可以很輕易就不安全。 除非所需的轉換本質屬於低階轉換，否則您應使用其他任一轉型運算子。  
  
 **Reinterpret_cast**運算子可用來轉換這類`char*`要`int*`，或`One_class*`至`Unrelated_class*`，這是原本就不安全。  
  
 結果**reinterpret_cast**無法安全地用於要轉換回其原始型別以外的任何項目。 其他用途的最佳情況是不可攜。  
  
 **Reinterpret_cast**運算子不能**const**， **volatile**，或 **__unaligned**屬性。 請參閱[const_cast 運算子](../cpp/const-cast-operator.md)如需移除這些屬性的詳細資訊。  
  
 **Reinterpret_cast**運算子會將 null 指標值轉換成目的地類型的 null 指標值。  
  
 實際用途之一**reinterpret_cast**雜湊函式，並對應至兩個不同的方式中的索引值的值罕見結束註冊具有相同索引中。  
  
```cpp 
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
  
 **Reinterpret_cast**允許將指標視為整數類資料類型。 結果隨即位元移位並與其本身 XOR，以產生唯一的索引 (高可攜性獨有)。 之後，標準 C-Style 轉換會將該索引截斷為函式的傳回型別。  
  
## <a name="see-also"></a>另請參閱  
 [轉型運算子](../cpp/casting-operators.md)   
 [關鍵字](../cpp/keywords-cpp.md)