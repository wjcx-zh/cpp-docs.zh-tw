---
title: '&lt;streambuf&gt; typedef'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 3c5dbefba8e2106c6e3e678002bce26fffd26a62
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215617"
---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf&gt; typedef

|||
|-|-|
|[streambuf](#streambuf)|[wstreambuf](#wstreambuf)|

## <a name="streambuf"></a><a name="streambuf"></a>streambuf

`basic_streambuf`使用 **`char`** 做為範本參數的特製化。

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>備註

此類型是類別樣板[basic_streambuf](../standard-library/basic-streambuf-class.md)的同義字，專門用於 **`char`** 具有預設字元特性之類型的元素。

## <a name="wstreambuf"></a><a name="wstreambuf"></a>wstreambuf

`basic_streambuf`使用 **`wchar_t`** 做為範本參數的特製化。

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>備註

此類型是類別樣板[basic_streambuf](../standard-library/basic-streambuf-class.md)的同義字，專門用於 **`wchar_t`** 具有預設字元特性之類型的元素。

## <a name="see-also"></a>另請參閱

[\<streambuf>](../standard-library/streambuf.md)
