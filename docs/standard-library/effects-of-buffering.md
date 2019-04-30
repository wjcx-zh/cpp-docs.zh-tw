---
title: 緩衝的效果
ms.date: 11/04/2016
helpviewer_keywords:
- buffers, effects of buffering
- buffering, effects of
ms.assetid: 5d544812-e95e-4f28-b15a-edef3f3414fd
ms.openlocfilehash: e10b28edffdfe3411f86c031bfd12ea886410e20
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413784"
---
# <a name="effects-of-buffering"></a>緩衝的效果

下例會示範緩衝的效果。 您可能希望程式會列印 `please wait`，請等 5 秒鐘，然後再繼續。 不過，它不一定這樣運行，因為輸出經過緩衝處理。

```cpp
// effects_buffering.cpp
// compile with: /EHsc
#include <iostream>
#include <time.h>
using namespace std;

int main( )
{
   time_t tm = time( NULL ) + 5;
   cout << "Please wait...";
   while ( time( NULL ) < tm )
      ;
   cout << "\nAll done" << endl;
}
```

若要讓程式按邏輯工作， `cout` 物件必須在訊息要出現時清空自己本身。 若要排清 `ostream` 物件，請將 `flush` 操作工具傳給它：

```cpp
cout <<"Please wait..." <<flush;
```

這個步驟會排清緩衝區，確保訊息在等待前即印出。 您也可以使用`endl`操作工具，排清緩衝區以及輸出歸位換行，或者您可以使用`cin`物件。 這個物件 (與 `cerr` 或 `clog` 物件) 通常會繫結至 `cout` 物件。 因此，只要使用 `cin` (或 `cerr` 或 `clog` 物件) 就會排清 `cout` 物件。

## <a name="see-also"></a>另請參閱

[輸出資料流](../standard-library/output-streams.md)<br/>
