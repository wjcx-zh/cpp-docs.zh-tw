---
title: '&lt;ostream&gt; typedefs | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: 3f5511cfbf73ddf74fa12954e1a108d8accf875e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33852575"
---
# <a name="ltostreamgt-typedefs"></a>&lt;ostream&gt; typedefs

|||
|-|-|
|[ostream](#ostream)|[wostream](#wostream)|

## <a name="ostream"></a>  ostream

從根據 `char` 特製化的 basic_ostream 和根據 `char` 特製化的 `char_traits` 建立型別。

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>備註

這個型別與專為具有預設字元特性之 `char` 型別項目所特製的樣板類別 [basic_ostream](../standard-library/basic-ostream-class.md) 同義。

## <a name="wostream"></a>  wostream

從根據 `wchar_t` 特製化的 basic_ostream 和根據 `wchar_t` 特製化的 `char_traits` 建立型別。

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>備註

這個型別與專為具有預設字元特性之 `wchar_t` 型別項目所特製的樣板類別 [basic_ostream](../standard-library/basic-ostream-class.md) 同義。

## <a name="see-also"></a>另請參閱

[\<ostream>](../standard-library/ostream.md)<br/>
