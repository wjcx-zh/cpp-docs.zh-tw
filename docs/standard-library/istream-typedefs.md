---
title: '&lt;istream&gt; typedef | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- istream/std::iostream
- istream/std::istream
- istream/std::wiostream
- istream/std::wistream
ms.assetid: 55bc1f84-53a7-46ca-a36f-ac6ef75d0374
caps.latest.revision: 10
manager: ghogen
ms.openlocfilehash: 0c27a5fcb3efab861b2f7da4ea4a5fdf978bbbb1
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="ltistreamgt-typedefs"></a>&lt;istream&gt; typedef

||||
|-|-|-|
|[iostream](#iostream)|[istream](#istream)|[wiostream](#wiostream)|
|[wistream](#wistream)|

## <a name="iostream"></a>  iostream

`char` 的特殊化類型 `basic_iostream`。

```cpp
typedef basic_iostream<char, char_traits<char>> iostream;
```

### <a name="remarks"></a>備註

此類型與範本類別 [basic_iostream](../standard-library/basic-iostream-class.md) 同義，該範本類別是為具有預設字元特性之 `char` 類型的元素特製化的範本類別。

## <a name="istream"></a>  istream

`char` 的特殊化類型 `basic_istream`。

```cpp
typedef basic_istream<char, char_traits<char>> istream;
```

### <a name="remarks"></a>備註

此類型與範本類別 [basic_istream](../standard-library/basic-istream-class.md) 同義，該範本類別是為具有預設字元特性之 `char` 類型的元素特製化的範本類別。

## <a name="wiostream"></a>  wiostream

`wchar_t` 的特殊化類型 `basic_iostream`。

```cpp
typedef basic_iostream<wchar_t, char_traits<wchar_t>> wiostream;
```

### <a name="remarks"></a>備註

此類型與範本類別 [basic_iostream](../standard-library/basic-iostream-class.md) 同義，該範本類別是為具有預設字元特性之 `wchar_t` 類型的元素特製化的範本類別。

## <a name="wistream"></a>  wistream

`wchar_t` 的特殊化類型 `basic_istream`。

```cpp
typedef basic_istream<wchar_t, char_traits<wchar_t>> wistream;
```

### <a name="remarks"></a>備註

此類型與範本類別 [basic_istream](../standard-library/basic-istream-class.md) 同義，該範本類別是為具有預設字元特性之 `wchar_t` 類型的元素特製化的範本類別。

## <a name="see-also"></a>另請參閱

[\<istream>](../standard-library/istream.md)<br/>
