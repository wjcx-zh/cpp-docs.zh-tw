---
title: 緩衝區溢位
ms.date: 11/04/2016
helpviewer_keywords:
- buffers [C++], character sizes
- buffer overflows [C++]
- MBCS [C++], buffer overflow
ms.assetid: f2b7e40a-f02b-46d8-a449-51d26fc0c663
ms.openlocfilehash: 71877ed770384190cb7f856567d9e7e845e3da19
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217320"
---
# <a name="buffer-overflow"></a>緩衝區溢位

當您將字元放入緩衝區時，不同的字元大小可能會造成問題。 請考慮下列程式碼，它會將字串中的字元複製 `sz` 到緩衝區， `rgch` 如下所示：

```cpp
cb = 0;
while( cb < sizeof( rgch ) )
    rgch[ cb++ ] = *sz++;
```

問題是：最後一個位元組複製了前導位元組嗎？ 下列動作無法解決此問題，因為它可能會使緩衝區溢位：

```cpp
cb = 0;
while( cb < sizeof( rgch ) )
{
    _mbccpy( rgch + cb, sz );
    cb += _mbclen( sz );
    sz = _mbsinc( sz );
}
```

`_mbccpy`呼叫會嘗試執行正確的動作—複製完整的字元，不論是1或2個位元組。 但是，如果字元寬2個位元組，則不會考慮複製的最後一個字元可能不適合緩衝區。 正確的解決方案是：

```cpp
cb = 0;
while( (cb + _mbclen( sz )) <= sizeof( rgch ) )
{
    _mbccpy( rgch + cb, sz );
    cb += _mbclen( sz );
    sz = _mbsinc( sz );
}
```

這段程式碼會使用 `_mbclen` 測試所指向的目前字元大小，測試迴圈測試中可能的緩衝區溢位 `sz` 。 藉由呼叫函式 `_mbsnbcpy` ，您可以使用一行程式碼來取代迴圈中的程式碼 **`while`** 。 例如：

```cpp
_mbsnbcpy( rgch, sz, sizeof( rgch ) );
```

## <a name="see-also"></a>另請參閱

[MBCS 程式設計提示](../text/mbcs-programming-tips.md)
