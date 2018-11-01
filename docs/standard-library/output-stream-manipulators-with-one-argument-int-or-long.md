---
title: 具有單一引數 (int 或 long) 的輸出資料流操作工具
ms.date: 11/04/2016
helpviewer_keywords:
- output streams, int or long argument manipulators
ms.assetid: 338f3164-b5e2-4c5a-a605-7d9dc3629ca1
ms.openlocfilehash: e093512af2741329c58db0b613453f3388bacdf2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530984"
---
# <a name="output-stream-manipulators-with-one-argument-int-or-long"></a>具有單一引數 (int 或 long) 的輸出資料流操作工具

iostream 類別程式庫提供一組巨集，可用來建立參數化的操作工具。 具有單一操作工具**int**或是**長**引數是特殊案例。 若要建立輸出資料流操作工具會接受單一**int**或**長**引數 (例如`setw`)，您必須使用的 _Smanip 巨集，其定義於\<iomanip> >。 本範例定義 `fillblank` 操作工具，它會將指定的空格數目插入資料流中：

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

[使用引數來建立自訂操作工具](../standard-library/custom-manipulators-with-arguments.md)<br/>
