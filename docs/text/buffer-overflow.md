---
title: 緩衝區溢位
ms.date: 11/04/2016
helpviewer_keywords:
- buffers [C++], character sizes
- buffer overflows [C++]
- MBCS [C++], buffer overflow
ms.assetid: f2b7e40a-f02b-46d8-a449-51d26fc0c663
ms.openlocfilehash: 7f9864e6b49446ea68d82e76e877ce9c677b893d
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741376"
---
# <a name="buffer-overflow"></a>緩衝區溢位

當您將字元放入緩衝區，不同的字元大小會造成問題。 請考慮下列程式碼，從字串中複製的字元， `sz`，到緩衝區， `rgch`:

```cpp
cb = 0;
while( cb < sizeof( rgch ) )
    rgch[ cb++ ] = *sz++;
```

問題是：是最後一個位元組會複製一個前導位元組嗎？ 下列無法解決問題因為它會溢位的緩衝區：

```cpp
cb = 0;
while( cb < sizeof( rgch ) )
{
    _mbccpy( rgch + cb, sz );
    cb += _mbclen( sz );
    sz = _mbsinc( sz );
}
```

`_mbccpy`呼叫會嘗試執行正確的動作 — 複製完整的字元，不論它是 1 或 2 個位元組。 但它不會考慮複製的最後一個字元可能不符合緩衝區如果字元是 2 個位元組寬。 正確的解決方法是：

```cpp
cb = 0;
while( (cb + _mbclen( sz )) <= sizeof( rgch ) )
{
    _mbccpy( rgch + cb, sz );
    cb += _mbclen( sz );
    sz = _mbsinc( sz );
}
```

此程式碼測試可能會發生緩衝區溢位，迴圈中測試，請使用`_mbclen`若要測試的目前所指向的字元大小`sz`。 藉由呼叫`_mbsnbcpy`函式，您可以取代中的程式碼**雖然**迴圈使用一行程式碼。 例如: 

```cpp
_mbsnbcpy( rgch, sz, sizeof( rgch ) );
```

## <a name="see-also"></a>另請參閱

[MBCS 程式設計提示](../text/mbcs-programming-tips.md)
