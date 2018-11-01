---
title: '&lt;streambuf&gt; typedef'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 505739861771a05dd39741f432579a6e9b2d0c26
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50664057"
---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf&gt; typedef

|||
|-|-|
|[streambuf](#streambuf)|[wstreambuf](#wstreambuf)|

## <a name="streambuf"></a>  streambuf

特製化`basic_streambuf`使用**char**做為樣板參數。

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>備註

型別是此範本類別同義[basic_streambuf](../standard-library/basic-streambuf-class.md)類型的項目所特製化**char**具有預設字元特性。

## <a name="wstreambuf"></a>  wstreambuf

特製化`basic_streambuf`使用**wchar_t**做為樣板參數。

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>備註

型別是此範本類別同義[basic_streambuf](../standard-library/basic-streambuf-class.md)類型的項目所特製化**wchar_t**具有預設字元特性。

## <a name="see-also"></a>另請參閱

[\<streambuf>](../standard-library/streambuf.md)<br/>
