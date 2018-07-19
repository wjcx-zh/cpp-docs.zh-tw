---
title: char_traits&lt;wchar_t&gt; 結構 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- char_traits<wchar_t>
- iosfwd/std::char_traits<wchar_t>
dev_langs:
- C++
helpviewer_keywords:
- char_traits<wchar_t> class
ms.assetid: 31f34072-04d6-4871-88fe-48e17d473484
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c7d8b87b51bfeef68ef8bfe22c8e7e201929aa3f
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957070"
---
# <a name="chartraitsltwchartgt-struct"></a>char_traits&lt;wchar_t&gt; 結構

類別是特製化的樣板結構**char_traits\<CharType >** 類型之項目的**wchar_t**。

## <a name="syntax"></a>語法

```cpp
template <>
struct char_traits<wchar_t>;
```

## <a name="remarks"></a>備註

特製化可讓結構利用操作此類型物件的程式庫函式**wchar_t**。

## <a name="requirements"></a>需求

**標頭：**\<string>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[char_traits 結構](../standard-library/char-traits-struct.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
