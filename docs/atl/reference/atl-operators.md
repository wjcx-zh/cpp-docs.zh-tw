---
title: ATL 運算子
ms.date: 11/04/2016
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
ms.openlocfilehash: 8c15daa1d2b12c58323ef5ef75559a2ab911ad93
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319227"
---
# <a name="atl-operators"></a>ATL 運算子

本節包含 ATL 全域運算符的參考主題。

|運算子|描述|
|--------------|-----------------|
|[運算符 |](#operator_eq_eq)|比較兩`CSid`個對`SID`象 或結構以表示相等。|
|[操作員 !]](#operator_neq)|比較兩`CSid`個對`SID`象 或結構的不等式。|
|[運算子<](#operator_lt)|測試運算符`CSid`左側 的物件或`SID`結構是否小於`CSid`右側 的`SID`物件或結構(對於C++標準庫相容性)。|
|[運算子>](#operator_gt)|測試運算符`CSid`左側 的物件或`SID`結構是否大於`CSid`右側 的`SID`物件或結構(對於C++標準庫相容性)。|
|[操作員<|](#operator_lt__eq)|測試運算符`CSid`左側 的物件或`SID`結構是否小於或等於`CSid`右側 的`SID`物件或結構(對於C++標準庫相容性)。|
|[操作員>|](#operator_gt__eq)|測試運算符`CSid`左側 的物件或`SID`結構是否大於或等於`CSid`右側 的`SID`物件或結構(C++標準庫相容性)。|

## <a name="requirements"></a>需求

**標題:** atlsecurity.h.

## <a name="operator-"></a><a name="operator_eq_eq"></a>運算符 |

比較`CSid`物件`SID`或 (安全標識符)結構以獲得相等性。

```
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*<br/>
要比較`CSid`的第一`SID`個對象或結構。

*rhs*<br/>
要比較`CSid`的第二`SID`個對象或結構。

### <a name="return-value"></a>傳回值

如果物件相等,則返回 TRUE,如果物件不相等,則返回 FALSE。

## <a name="operator-"></a><a name="operator_neq"></a>操作員 !]

比較`CSid`物件`SID`或 (安全標識符)結構的不等式。

```
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*<br/>
要比較`CSid`的第一`SID`個對象或結構。

*rhs*<br/>
要比較`CSid`的第二`SID`個對象或結構。

### <a name="return-value"></a>傳回值

如果物件不相等,則返回 TRUE;如果物件相等,則返回 FALSE。

## <a name="operator-"></a><a name="operator_lt"></a>運算子<

測試運算符`CSid`左側 的物件或`SID`結構是否小於`CSid`右側 的`SID`物件或結構(對於C++標準庫相容性)。

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*<br/>
要比較`CSid`的第一`SID`個對象或結構。

*rhs*<br/>
要比較`CSid`的第二`SID`個對象或結構。

### <a name="return-value"></a>傳回值

如果*lhs*物件的位址小於*rhs*物件的位址,則返回 TRUE,否則為 FALSE。

### <a name="remarks"></a>備註

此運算符作用於`CSid`物件或`SID`結構的位址,並實現該運算符是為了提供與C++標準庫集合類的相容性。

## <a name="operator-"></a><a name="operator_gt"></a>運算子>

測試運算符`CSid`左側 的物件或`SID`結構是否大於`CSid`右側 的`SID`物件或結構(對於C++標準庫相容性)。

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*<br/>
要比較`CSid`的第一`SID`個對象或結構。

*rhs*<br/>
要比較`CSid`的第二`SID`個對象或結構。

### <a name="return-value"></a>傳回值

如果*lhs*的位址大於*rhs*的位址,則返回 TRUE,否則返回 FALSE。

### <a name="remarks"></a>備註

此運算符作用於`CSid`物件或`SID`結構的位址,並實現該運算符是為了提供與C++標準庫集合類的相容性。

## <a name="operator-"></a><a name="operator_lt__eq"></a>操作員<|

測試運算符`CSid`左側 的物件或`SID`結構是否小於或等於`CSid`右側 的`SID`物件或結構(對於C++標準庫相容性)。

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*<br/>
要比較`CSid`的第一`SID`個對象或結構。

*rhs*<br/>
要比較`CSid`的第二`SID`個對象或結構。

### <a name="return-value"></a>傳回值

如果*lhs*的位址小於或等於*rhs*的位址,則返回 TRUE,否則。

### <a name="remarks"></a>備註

此運算符作用於`CSid`物件或`SID`結構的位址,並實現該運算符是為了提供與C++標準庫集合類的相容性。

## <a name="operator-"></a><a name="operator_gt__eq"></a>操作員>|

測試運算符`CSid`左側 的物件或`SID`結構是否大於或等於`CSid`右側 的`SID`物件或結構(C++標準庫相容性)。

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*<br/>
要比較`CSid`的第一`SID`個對象或結構。

*rhs*<br/>
要比較`CSid`的第二`SID`個對象或結構。

### <a name="return-value"></a>傳回值

如果*lhs*的位址大於或等於*rhs*的位址,則返回 TRUE,否則。

### <a name="remarks"></a>備註

此運算符作用於`CSid`物件或`SID`結構的位址,並實現該運算符是為了提供與C++標準庫集合類的相容性。
