---
title: '&lt;ostream&gt; typedefs | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
caps.latest.revision: 11
manager: ghogen
ms.openlocfilehash: 8c451b16a581ab13f87c7bcca793efe3a0f07bf5
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
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
