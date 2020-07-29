---
title: '&lt;strstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <strstream>
helpviewer_keywords:
- strstream header
ms.assetid: eaa9d0d4-d217-4f28-8a68-9b9ad7b1c0f5
ms.openlocfilehash: a7df541049aafd191e969eaa392ab3706f171926
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224600"
---
# <a name="ltstrstreamgt"></a>&lt;strstream&gt;

定義數個類別，以支援儲存在物件的已配置陣列中之序列的 iostreams 作業 **`char`** 。 這類序列會輕易地與 C 字串相互轉換。

## <a name="requirements"></a>需求

**標頭：**\<strstream>

**命名空間：** std

## <a name="remarks"></a>備註

類型的物件 `strstream` 會使用 **`char`** * （也就是 C 字串）。 使用 [\<sstream>](../standard-library/sstream.md) 來處理[basic_string](../standard-library/basic-string-class.md)類型的物件。

> [!NOTE]
> \<strstream> 中的類別已被取代。 請考慮改用 \<sstream> 中的類別。

## <a name="members"></a>成員

### <a name="classes"></a>類別

|||
|-|-|
|[strstreambuf 類別](../standard-library/strstreambuf-class.md)|類別描述的資料流程緩衝區，可控制在陣列物件中儲存的專案序列之間的元素傳輸 **`char`** 。|
|[istrstream 類別](../standard-library/istrstream-class.md)|此類別說明一個物件，該物件可控制如何從類別 [strstreambuf](../standard-library/strstreambuf-class.md) 的資料流緩衝區中擷取項目和編碼物件。|
|[ostrstream 類別](../standard-library/ostrstream-class.md)|此類別說明一個物件，該物件可控制如何在類別 [strstreambuf](../standard-library/strstreambuf-class.md) 的資料流緩衝區中插入項目和編碼物件。|
|[strstream 類別](../standard-library/strstream-class.md)|此類別說明一個物件，該物件可控制如何使用類別 [strstreambuf](../standard-library/strstreambuf-class.md) 的資料流緩衝區來插入及擷取項目和編碼物件。|

### <a name="functions"></a>函式

```cpp
void freeze(bool freezefl = true);
char* str();
int pcount();
```

## <a name="see-also"></a>另請參閱

[\<strstream>](../standard-library/strstream.md)\
[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 程式設計](../standard-library/iostream-programming.md)\
[iostreams 慣例](../standard-library/iostreams-conventions.md)
