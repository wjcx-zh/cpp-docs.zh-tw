---
title: '&lt;memory&gt; 列舉'
ms.date: 11/04/2016
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
ms.openlocfilehash: 78cdb0fe6c0d9487500804d21fe4ad4870fcad0f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78884064"
---
# <a name="ltmemorygt-enums"></a>&lt;memory&gt; 列舉

## <a name="pointer_safety"></a>pointer_safety 列舉

`get_pointer_safety` 的可能傳回值列舉。

```cpp
class pointer_safety {
   relaxed,
   preferred,
   strict
};
```

### <a name="remarks"></a>備註

已限定範圍的**列舉**會定義可由 `get_pointer_safety()`傳回的值：

`relaxed` -- 以相同方式處理不是以安全方式衍生的指標 (顯然是已宣告或配置之物件的指標) 和以安全方式衍生的指標。

`preferred` -- 與先前一樣，但對於不是以安全方式衍生的指標不應取值。

`strict` -- 可能以不同方式處理不是以安全方式衍生的指標和以安全方式衍生的指標。
