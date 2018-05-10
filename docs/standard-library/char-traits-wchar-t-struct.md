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
ms.openlocfilehash: a117a7f9299591d971ecbfdd0a681b008937da33
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="chartraitsltwchartgt-struct"></a>char_traits&lt;wchar_t&gt; 結構

類別，其為類型 `wchar_t` 之元素的樣板結構 **char_traits\<CharType>** 的特製化。

## <a name="syntax"></a>語法

```cpp
template <>
struct char_traits<wchar_t>;
```

## <a name="remarks"></a>備註

特製化可讓結構利用操作此 `wchar_t` 類型物件的程式庫函式。

## <a name="requirements"></a>需求

**標頭：**\<string>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[char_traits 結構](../standard-library/char-traits-struct.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
