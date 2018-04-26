---
title: char_traits&lt;char32_t&gt; 結構 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- iosfwd/std::char_traits<char_32t>
- char_traits<char32_t>
dev_langs:
- C++
helpviewer_keywords:
- char_traits<char32_t> class
ms.assetid: c0315466-45d0-4a99-b83e-3b1dbfbfbbc3
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5ed195f6ed4d1319d079a58f736c65a03e397bd1
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="chartraitsltchar32tgt-struct"></a>char_traits&lt;char32_t&gt; 結構

結構，其為類型 `char32_t` 之元素的樣板結構 **char_traits\<CharType>** 的特製化。

## <a name="syntax"></a>語法

```cpp
template <>
struct char_traits<char32_t>;
```

## <a name="remarks"></a>備註

特製化可讓結構利用操作此 `char32_t` 類型物件的程式庫函式。

## <a name="requirements"></a>需求

**標頭：**\<string>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[\<string>](../standard-library/string.md)<br/>
[char_traits 結構](../standard-library/char-traits-struct.md)<br/>
