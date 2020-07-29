---
title: from_chars_result 結構
ms.date: 7/23/2020
f1_keywords:
- std::from_chars_result
helpviewer_keywords:
- from_chars_result class
- from_chars_result structure
ms.openlocfilehash: 5a5dcfe6e5b59644e6ebf55d68ce43975e7d3c9d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215760"
---
# <a name="from_chars_result-struct"></a>from_chars_result 結構

## <a name="syntax"></a>語法

```cpp
struct from_chars_result {
    const char* ptr;
    errc ec;
};
```

|成員|說明|
|--|--|
|`ptr`| 如果 `ec` 等於 `errc{}` ，則轉換成功，並 `ptr` 指向不屬於辨識數位一部分的第一個字元。 |
|`ec` | 轉換錯誤碼。 如需特定的錯誤碼，請參閱 [`errc`](system-error-enums.md#errc) 。|

### <a name="remarks"></a>備註

範例：剖析 `"1729cats"` 為十進位整數將會成功，而且 `ptr` 會指向， `'c'` 其中是第一個非數位，而且也是的一個 `"1729"` 後端。

如果沒有任何字元符合數位模式， `from_chars_result.ptr` 會指向 `first` ，而 `from_chars_result.ec` 是 `errc::invalid_argument` 。

如果只有部分字元符合數位模式， `from_chars_result.ptr` 會指向不符合模式的第一個字元， `last` 如果所有字元都相符，則會包含參數的值。

如果剖析的值不符合所執行之轉換類型的範圍， `from_chars_result.ec` 會是 `errc::result_out_of_range` 。

## <a name="requirements"></a>需求

**標頭：**\<charconv>

**命名空間：** std

**編譯器選項：** /std： c + + 17 或更新版本是必要項

## <a name="see-also"></a>另請參閱

[from_chars](charconv-functions.md#from_chars)
