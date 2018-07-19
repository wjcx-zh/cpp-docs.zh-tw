---
title: '&lt;memory&gt; 列舉 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
ms.openlocfilehash: 9b9ea485bb66292c3c0509036c22dd161a694dd3
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961411"
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
