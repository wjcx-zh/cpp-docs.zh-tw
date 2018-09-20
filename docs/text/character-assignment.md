---
title: 字元指派 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- characters [C++], assignments
- MBCS [C++], character assignments
ms.assetid: dcc329cd-92df-4e20-817d-364be62ff28f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8e17ace90abef63ce4af1dd56b5bbe8dfed9510c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429548"
---
# <a name="character-assignment"></a>字元設定

下列範例中的，在其中，請考慮**雖然**迴圈會掃描字串，將 'X' 以外的所有字元都複製到另一個字串：

```cpp
while( *sz2 )
{
    if( *sz2 != 'X' )
        *sz1++ = *sz2++;
    else
        sz2++;
}
```

程式碼會複製在位元組`sz2`所指向的位置`sz1`，然後遞增`sz1`接收下一個位元組。 但是如果中的下一個字元`sz2`是雙位元組字元，指派給`sz1`複製第 1 個位元組。 下列程式碼會使用可移植的函式，來安全地複製字元和另一個的增量`sz1`和`sz2`正確：

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