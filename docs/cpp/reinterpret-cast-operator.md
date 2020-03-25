---
title: reinterpret_cast 運算子
ms.date: 11/04/2016
f1_keywords:
- reinterpret_cast_cpp
helpviewer_keywords:
- reinterpret_cast keyword [C++]
ms.assetid: eb3283c7-7f88-467e-affd-407d37b46d6c
ms.openlocfilehash: 34c2fcb0e1f7f4df4e207d1737afc9c42e011feb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188281"
---
# <a name="reinterpret_cast-operator"></a>reinterpret_cast 運算子

可將所有指標轉換成任何其他指標類型。 也可將任何整數類資料類型轉換成任何指標類型 (反之亦然)。

## <a name="syntax"></a>語法

```
reinterpret_cast < type-id > ( expression )
```

## <a name="remarks"></a>備註

誤用**reinterpret_cast**操作員很容易就不安全。 除非所需的轉換本質屬於低階轉換，否則您應使用其他任一轉型運算子。

**Reinterpret_cast**運算子可用來進行轉換，例如 `char*` `int*`，或 `One_class*` 至 `Unrelated_class*`，這本身就是不安全的。

**Reinterpret_cast**的結果不能安全地用於轉換回其原始類型以外的任何專案。 其他用途的最佳情況是不可攜。

**Reinterpret_cast**運算子無法轉換成**const**、 **volatile**或 **__unaligned**屬性。 如需移除這些屬性的詳細資訊，請參閱[Const_cast 運算子](../cpp/const-cast-operator.md)。

**Reinterpret_cast**運算子會將 null 指標值轉換為目的地類型的 null 指標值。

**Reinterpret_cast**的一個實際用法是在雜湊函式中，這種方法會將值對應至索引，讓兩個相異值不常以相同的索引結束。

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

[轉型運算子](../cpp/casting-operators.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
