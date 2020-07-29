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
ms.openlocfilehash: 8fc163255a5ab342938f56f8a22af3984a48e56a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216618"
---
# <a name="_bstr_t-relational-operators"></a>_bstr_t 關係運算子

**Microsoft 特定的**

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

這些運算子會針對兩個 `_bstr_t` 物件進行字彙上的比較。 **`true`** 如果比較保留，則運算子會傳回，否則會傳回 **`false`** 。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[_bstr_t 類別](../cpp/bstr-t-class.md)
