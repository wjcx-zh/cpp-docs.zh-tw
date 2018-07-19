---
title: 具有單一引數 (int 或 long) 的輸出資料流操作工具 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- output streams, int or long argument manipulators
ms.assetid: 338f3164-b5e2-4c5a-a605-7d9dc3629ca1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f569b064d2ee5de5bd1aa39c9d443c8a49ca2677
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961847"
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
