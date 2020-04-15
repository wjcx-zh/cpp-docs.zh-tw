---
title: '&lt;codecvt&gt; 列舉'
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_mode
ms.assetid: 46a8b073-01bc-46d3-b3d3-a8540f9422c1
helpviewer_keywords:
- std::codecvt_mode
ms.openlocfilehash: e67290d8de0b8251191c4a93b66b7e19a293ed61
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371936"
---
# <a name="ltcodecvtgt-enums"></a>&lt;codecvt&gt; 列舉

## <a name="codecvt_mode-enumeration"></a><a name="codecvt_mode"></a>codecvt_mode枚舉

指定[區域設定](../standard-library/locale-class.md)方面的設定資訊。

```cpp
enum codecvt_mode {
    consume_header = 4,
    generate_header = 2,
    little_endian = 1
};
```

### <a name="remarks"></a>備註

枚舉定義了三個常量,這些常量向[\<codecvt>](../standard-library/codecvt.md)中聲明的區域設置面提供配置資訊。 相異值如下：

- `consume_header` 可在讀取多位元組序列時使用初始的標頭順序，並判斷後續多位元組序列的讀取位元組序。

- `generate_header` 可在寫入多位元組序列時產生初始的標頭順序，以建議後續多位元組序列的寫入位元組序。

- `little_endian` 可依位元組由小到大的順序 (而不是預設的位元組由大到小順序) 產生多位元組序列。

這些常數可以任意組合搭配使用 OR。

## <a name="see-also"></a>另請參閱

[\<編碼>](../standard-library/codecvt.md)
