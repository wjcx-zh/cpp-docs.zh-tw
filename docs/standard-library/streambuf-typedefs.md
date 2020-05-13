---
title: '&lt;streambuf&gt; typedef'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 8eb058f161a9f30ccf5e9d49307b50c215f79c22
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376688"
---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf&gt; typedef

|||
|-|-|
|[streambuf](#streambuf)|[wstreambuf](#wstreambuf)|

## <a name="streambuf"></a><a name="streambuf"></a>溪流布夫

使用`basic_streambuf`**char**作為範本參數的專門化。

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>備註

該類型是類範本[basic_streambuf](../standard-library/basic-streambuf-class.md)的同義詞,專門用於具有預設字元特徵的類型**字元**的元素。

## <a name="wstreambuf"></a><a name="wstreambuf"></a>韋克韋布夫

使用wchar_t作為`basic_streambuf`範本**wchar_t**參數的專門化。

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>備註

該類型是類範本[basic_streambuf](../standard-library/basic-streambuf-class.md)的同義詞,專門用於具有預設字元特徵**的類型wchar_t**元素。

## <a name="see-also"></a>另請參閱

[\<流布夫>](../standard-library/streambuf.md)
