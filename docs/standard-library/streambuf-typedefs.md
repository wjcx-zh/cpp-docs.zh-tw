---
title: '&lt;streambuf&gt; typedef | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 8fb1713dfbc2d9766c488f21d324d801a4886d68
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf&gt; typedef

|||
|-|-|
|[streambuf](#streambuf)|[wstreambuf](#wstreambuf)|

## <a name="streambuf"></a>  streambuf

會使用 `char` 做為範本參數的 `basic_streambuf` 特製化。

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>備註

這個類型與 [basic_streambuf](../standard-library/basic-streambuf-class.md) 同義，已針對具有預設字元特性的 `char` 類型項目進行特製化。

## <a name="wstreambuf"></a>  wstreambuf

會使用 `wchar_t` 做為範本參數的 `basic_streambuf` 特製化。

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>備註

這個類型與 [basic_streambuf](../standard-library/basic-streambuf-class.md) 同義，已針對具有預設字元特性的 `wchar_t` 類型項目進行特製化。

## <a name="see-also"></a>另請參閱

[\<streambuf>](../standard-library/streambuf.md)<br/>
