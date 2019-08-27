---
title: '&lt;memory&gt; 列舉'
ms.date: 11/04/2016
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
ms.openlocfilehash: b2f5b50dc1344b95e88742d346e32fc55f821336
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243854"
---
# <a name="ltmemorygt-enums"></a>&lt;memory&gt; 列舉

## <a name="pointer_safety"></a> pointer_safety 列舉

`get_pointer_safety` 的可能傳回值列舉。

```
class pointer_safety {
   relaxed,
   preferred,
   strict
};
```

### <a name="remarks"></a>備註

已設定領域**enum**定義可傳回的值`get_pointer_safety()`:

`relaxed` -- 以相同方式處理不是以安全方式衍生的指標 (顯然是已宣告或配置之物件的指標) 和以安全方式衍生的指標。

`preferred` -- 與先前一樣，但對於不是以安全方式衍生的指標不應取值。

`strict` -- 可能以不同方式處理不是以安全方式衍生的指標和以安全方式衍生的指標。
