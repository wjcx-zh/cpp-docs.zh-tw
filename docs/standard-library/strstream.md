---
title: '&lt;strstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <strstream>
helpviewer_keywords:
- strstream header
ms.assetid: eaa9d0d4-d217-4f28-8a68-9b9ad7b1c0f5
ms.openlocfilehash: 72b96c300aba1729823462ce6671e2f9a5285761
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412263"
---
# <a name="ltstrstreamgt"></a>&lt;strstream&gt;

定義數個配置陣列中儲存之序列的 iostreams 作業提供支援的類別**char**物件。 這類序列會輕易地與 C 字串相互轉換。

## <a name="syntax"></a>語法

```cpp
#include <strstream>
```

## <a name="remarks"></a>備註

類型 `strstream` 的物件可與 `char` * (是 C 字串) 搭配運作。 使用 [\<sstream>](../standard-library/sstream.md)，來與類型 [basic_string](../standard-library/basic-string-class.md) 的物件搭配運作。

> [!NOTE]
> 中的類別\<strstream > 已被取代。 請考慮使用中的類別\<sstream > 改用。

### <a name="classes"></a>類別

|類別|描述|
|-|-|
|[strstreambuf 類別](../standard-library/strstreambuf-class.md)|此類別描述控制的項目中儲存之元素的順序來回傳輸的資料流緩衝區**char**陣列物件。|
|[istrstream 類別](../standard-library/istrstream-class.md)|此類別說明一個物件，該物件可控制如何從類別 [strstreambuf](../standard-library/strstreambuf-class.md) 的資料流緩衝區中擷取項目和編碼物件。|
|[ostrstream 類別](../standard-library/ostrstream-class.md)|此類別說明一個物件，該物件可控制如何在類別 [strstreambuf](../standard-library/strstreambuf-class.md) 的資料流緩衝區中插入項目和編碼物件。|
|[strstream 類別](../standard-library/strstream-class.md)|此類別說明一個物件，該物件可控制如何使用類別 [strstreambuf](../standard-library/strstreambuf-class.md) 的資料流緩衝區來插入及擷取項目和編碼物件。|

## <a name="see-also"></a>另請參閱

[\<strstream>](../standard-library/strstream.md)<br/>
[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 程式設計](../standard-library/iostream-programming.md)<br/>
[iostream 慣例](../standard-library/iostreams-conventions.md)<br/>
