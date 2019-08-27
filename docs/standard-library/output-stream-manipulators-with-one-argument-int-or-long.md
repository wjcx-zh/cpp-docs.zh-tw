---
title: 具有單一引數 (int 或 long) 的輸出資料流操作工具
ms.date: 11/04/2016
helpviewer_keywords:
- output streams, int or long argument manipulators
ms.assetid: 338f3164-b5e2-4c5a-a605-7d9dc3629ca1
ms.openlocfilehash: 93e4de25323514eb4105814b565dc3ddc3fbb737
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453002"
---
# <a name="output-stream-manipulators-with-one-argument-int-or-long"></a>具有單一引數 (int 或 long) 的輸出資料流操作工具

iostream 類別程式庫提供一組巨集，可用來建立參數化的操作工具。 具有單一**int**或**long**引數的操作工具是特殊案例。 若要建立可接受單一**int**或**long**引數 (例如`setw`) 的輸出資料流程操作工具, 您必須使用在 p > 中\<定義的 _Smanip 宏。 本範例定義 `fillblank` 操作工具，它會將指定的空格數目插入資料流中：

## <a name="example"></a>範例

```cpp
// output_stream_manip.cpp
// compile with: /GR /EHsc
#include <iostream>
#include <iomanip>
using namespace std;

void fb( ios_base& os, int l )
{
   ostream *pos = dynamic_cast<ostream*>(&os);
   if (pos)
   {
      for( int i=0; i < l; i++ )
      (*pos) << ' ';
   };
}

_Smanip<int>
   __cdecl fillblank(int no)
   {
   return (_Smanip<int>(&fb, no));
   }

int main( )
{
   cout << "10 blanks follow" << fillblank( 10 ) << ".\n";
}
```

## <a name="see-also"></a>另請參閱

[使用引數來建立自訂操作工具](../standard-library/custom-manipulators-with-arguments.md)
