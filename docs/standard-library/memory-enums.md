---
title: '&lt;memory&gt; 列舉'
ms.date: 11/04/2016
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
ms.openlocfilehash: 5c5f87905b772ef277a72ef11defef8cb1001661
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412835"
---
# <a name="ltmemorygt-enums"></a>&lt;memory&gt; 列舉

||
|-|
|[pointer_safety](#pointer_safety)|

## <a name="pointer_safety"></a>  pointer_safety 列舉

`get_pointer_safety` 的可能傳回值列舉。

class pointer_safety { relaxed, preferred, strict };

### <a name="remarks"></a>備註

已設定領域**enum**定義可傳回的值`get_pointer_safety()`:

`relaxed` -- 以相同方式處理不是以安全方式衍生的指標 (顯然是已宣告或配置之物件的指標) 和以安全方式衍生的指標。

`preferred` -- 與先前一樣，但對於不是以安全方式衍生的指標不應取值。

`strict` -- 可能以不同方式處理不是以安全方式衍生的指標和以安全方式衍生的指標。

## <a name="see-also"></a>另請參閱

[\<memory>](../standard-library/memory.md)<br/>
