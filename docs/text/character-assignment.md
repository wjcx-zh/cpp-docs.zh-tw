---
title: 字元設定
ms.date: 11/04/2016
helpviewer_keywords:
- characters [C++], assignments
- MBCS [C++], character assignments
ms.assetid: dcc329cd-92df-4e20-817d-364be62ff28f
ms.openlocfilehash: 0f627f88ca2b1d3533d3690cd0316ee047a327ad
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217307"
---
# <a name="character-assignment"></a>字元設定

請考慮下列範例，其中迴圈會 **`while`** 掃描字串，將 ' X ' 以外的所有字元複製到另一個字串：

```cpp
while( *sz2 )
{
    if( *sz2 != 'X' )
        *sz1++ = *sz2++;
    else
        sz2++;
}
```

此程式碼會將位元組複製 `sz2` 到所指向的位置 `sz1` ，然後再遞增 `sz1` 以接收下一個位元組。 但是，如果中的下一個字元 `sz2` 是雙位元組字元，則指派 `sz1` 只會複製第一個位元組。 下列程式碼會使用可移植的函式來安全地複製字元，而另一種則是遞增 `sz1` 且 `sz2` 正確的：

```cpp
while( *sz2 )
{
    if( *sz2 != 'X' )
    {
        _mbscpy_s( sz1, 1, sz2 );
        sz1 = _mbsinc( sz1 );
        sz2 = _mbsinc( sz2 );
    }
    else
        sz2 = _mbsinc( sz2 );
}
```

## <a name="see-also"></a>另請參閱

[MBCS 程式設計提示](../text/mbcs-programming-tips.md)<br/>
[字元比較](../text/character-comparison.md)
