---
title: '&lt;streambuf&gt; typedef'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: f08c08de0d6449714f953f5a65fadd2e0279ed44
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843192"
---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf&gt; typedef

[streambuf](#streambuf)\
[wstreambuf](#wstreambuf)

## <a name="streambuf"></a><a name="streambuf"></a> streambuf

的特製化 `basic_streambuf` ，它會使用 **`char`** 做為範本參數。

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>備註

此類型是類別樣板 [basic_streambuf](../standard-library/basic-streambuf-class.md)的同義字，專門針對 **`char`** 具有預設字元特性之類型的專案進行特製化。

## <a name="wstreambuf"></a><a name="wstreambuf"></a> wstreambuf

的特製化 `basic_streambuf` ，它會使用 **`wchar_t`** 做為範本參數。

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>備註

此類型是類別樣板 [basic_streambuf](../standard-library/basic-streambuf-class.md)的同義字，專門針對 **`wchar_t`** 具有預設字元特性之類型的專案進行特製化。

## <a name="see-also"></a>另請參閱

[\<streambuf>](../standard-library/streambuf.md)
