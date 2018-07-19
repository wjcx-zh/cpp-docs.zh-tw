---
title: '&lt;istream&gt; typedef | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- istream/std::iostream
- istream/std::istream
- istream/std::wiostream
- istream/std::wistream
ms.assetid: 55bc1f84-53a7-46ca-a36f-ac6ef75d0374
ms.openlocfilehash: bea06c9799783feafaff1f68f4019463e452a4f2
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38958851"
---
# <a name="ltistreamgt-typedefs"></a>&lt;istream&gt; typedef

||||
|-|-|-|
|[iostream](#iostream)|[istream](#istream)|[wiostream](#wiostream)|
|[wistream](#wistream)|

## <a name="iostream"></a>  iostream

型別`basic_iostream`特殊化**char**。

```cpp
typedef basic_iostream<char, char_traits<char>> iostream;
```

### <a name="remarks"></a>備註

類型是範本類別同義[basic_iostream](../standard-library/basic-iostream-class.md)類型的項目所特製化**char**具有預設字元特性。

## <a name="istream"></a>  istream

型別`basic_istream`特殊化**char**。

```cpp
typedef basic_istream<char, char_traits<char>> istream;
```

### <a name="remarks"></a>備註

類型是範本類別同義[basic_istream](../standard-library/basic-istream-class.md)類型的項目所特製化**char**具有預設字元特性。

## <a name="wiostream"></a>  wiostream

型別`basic_iostream`特殊化**wchar_t**。

```cpp
typedef basic_iostream<wchar_t, char_traits<wchar_t>> wiostream;
```

### <a name="remarks"></a>備註

類型是範本類別同義[basic_iostream](../standard-library/basic-iostream-class.md)類型的項目所特製化**wchar_t**具有預設字元特性。

## <a name="wistream"></a>  wistream

型別`basic_istream`特殊化**wchar_t**。

```cpp
typedef basic_istream<wchar_t, char_traits<wchar_t>> wistream;
```

### <a name="remarks"></a>備註

類型是範本類別同義[basic_istream](../standard-library/basic-istream-class.md)類型的項目所特製化**wchar_t**具有預設字元特性。

## <a name="see-also"></a>另請參閱

[\<istream>](../standard-library/istream.md)<br/>
