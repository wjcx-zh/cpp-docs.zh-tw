---
title: to_chars_result 結構
ms.date: 07/22/2020
f1_keywords:
- charconv/std::to_chars_result
helpviewer_keywords:
- to_chars_result class
- to_chars_result structure
ms.openlocfilehash: 4e46d1cc9d0b6a02d731ad25c2e85c99300d7234
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509649"
---
# <a name="to_chars_result-struct"></a>to_chars_result 結構

## <a name="syntax"></a>語法

```cpp
struct to_chars_result {
    char* ptr;
    errc ec;
};
```

## <a name="members"></a>成員

|member|描述|
|--|--|
|`ptr`| 如果 `ec` 等於 `errc{}` ，則轉換會成功，而且 `ptr` 是寫入字元的最後一端指標。 否則， `ptr` 會有參數的值 `to_chars()` `last` ，而且 \[ 不會指定最後一個) 的範圍內容。|
|`ec` | 轉換錯誤碼。 如需特定錯誤碼，請參閱 [`errc`](system-error-enums.md#errc) 。|

## <a name="requirements"></a>需求

**標頭：**\<charconv>

**命名空間：** std

**編譯器選項：** 需要/std： c + + 17 或更新版本

## <a name="see-also"></a>另請參閱

[to_chars](charconv-functions.md#to_chars)
