---
title: _bstr_t 關係運算子
ms.date: 05/07/2019
f1_keywords:
- _bstr_t::operator>
- _bstr_t::operator==
- _bstr_t::operator>=
- _bstr_t::operator!=
- _bstr_t::operator<
- _bstr_t::operator<=
- _bstr_t::operator!
helpviewer_keywords:
- _bstr_t [C++]
ms.assetid: e153da72-37c3-4d8a-b8eb-730d65da64dd
ms.openlocfilehash: 57a9379be6d90cfb574ea0dcc033692762c47990
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222242"
---
# <a name="bstrt-relational-operators"></a>_bstr_t 關係運算子

**Microsoft 專屬**

比較兩個 `_bstr_t` 物件。

## <a name="syntax"></a>語法

```
bool operator!( ) const throw( );
bool operator==(const _bstr_t& str) const throw( );
bool operator!=(const _bstr_t& str) const throw( );
bool operator<(const _bstr_t& str) const throw( );
bool operator>(const _bstr_t& str) const throw( );
bool operator<=(const _bstr_t& str) const throw( );
bool operator>=(const _bstr_t& str) const throw( );
```

## <a name="remarks"></a>備註

這些運算子會針對兩個 `_bstr_t` 物件進行字彙上的比較。 這個運算子會傳回 TRUE 如果比較有效，否則傳回 FALSE。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_bstr_t 類別](../cpp/bstr-t-class.md)