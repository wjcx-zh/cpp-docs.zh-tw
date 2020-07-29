---
title: to_chars_result 結構
ms.date: 07/22/2020
f1_keywords:
- charconv/std::to_chars_result
helpviewer_keywords:
- to_chars_result class
- to_chars_result structure
ms.openlocfilehash: a840b8d030f0ed0d2a4afcc57e1bef1161c76ff3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212057"
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

|成員|說明|
|--|--|
|`ptr`| 如果 `ec` 等於，則 `errc{}` 轉換成功，而且 `ptr` 是所寫入字元的一個過去端指標。 否則， `ptr` 會有參數的值 `to_chars()` `last` ，而且 \[ 不會指定範圍 first，last）的內容。|
|`ec` | 轉換錯誤碼。 如需特定的錯誤碼，請參閱 [`errc`](system-error-enums.md#errc) 。|

## <a name="requirements"></a>需求

**標頭：**\<charconv>

**命名空間：** std

**編譯器選項：** /std： c + + 17 或更新版本是必要項

## <a name="see-also"></a>另請參閱

[to_chars](charconv-functions.md#to_chars)