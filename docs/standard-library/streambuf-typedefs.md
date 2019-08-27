---
title: '&lt;streambuf&gt; typedef'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 178b489d92a4ed7340084490329fdf8fa16c2aa7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449580"
---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf&gt; typedef

|||
|-|-|
|[streambuf](#streambuf)|[wstreambuf](#wstreambuf)|

## <a name="streambuf"></a>  streambuf

的特製化`basic_streambuf` , 使用**char**做為範本參數。

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>備註

此類型與樣板類別[basic_streambuf](../standard-library/basic-streambuf-class.md)同義, 專門用於具有預設字元特性之**char**類型的元素。

## <a name="wstreambuf"></a>  wstreambuf

的特製化`basic_streambuf` , 使用**wchar_t**做為範本參數。

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>備註

此類型與樣板類別[basic_streambuf](../standard-library/basic-streambuf-class.md)同義, 專門用於具有預設字元特性之**wchar_t**類型的元素。

## <a name="see-also"></a>另請參閱

[\<streambuf>](../standard-library/streambuf.md)
