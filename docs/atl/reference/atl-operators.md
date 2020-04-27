---
title: ATL 運算子
ms.date: 11/04/2016
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
ms.openlocfilehash: fe5363d3d05123c17e45254898e2210797400022
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168848"
---
# <a name="atl-operators"></a>ATL 運算子

本章節包含 ATL 全域運算子的參考主題。

|運算子|描述|
|--------------|-----------------|
|[operator = =](#operator_eq_eq)|比較兩`CSid`個物件`SID`或結構是否相等。|
|[operator！ =](#operator_neq)|比較兩`CSid`個物件`SID`或結構是否不相等。|
|[運算子 <](#operator_lt)|測試運算子左邊`CSid`的物件`SID`或結構是否小於右邊的`CSid`物件或`SID`結構（適用于 c + + 標準程式庫相容性）。|
|[運算子 >](#operator_gt)|測試運算子左邊`CSid`的物件`SID`或結構是否大於右邊的`CSid`物件或`SID`結構（適用于 c + + 標準程式庫相容性）。|
|[運算子 <=](#operator_lt__eq)|測試運算子左邊`CSid`的物件`SID`或結構是否小於或等於右邊的`CSid`物件或`SID`結構（適用于 c + + 標準程式庫相容性）。|
|[運算子 >=](#operator_gt__eq)|測試運算子左邊`CSid`的物件`SID`或結構是否大於或等於右邊的`CSid`物件或`SID`結構（適用于 c + + 標準程式庫相容性）。|

## <a name="requirements"></a>需求

**標頭：** atlsecurity. h。

## <a name="operator-"></a><a name="operator_eq_eq"></a>operator = =

比較`CSid`物件或`SID` （安全識別碼）結構是否相等。

```cpp
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*<br/>
要比較`CSid`的第`SID`一個物件或結構。

*rhs*<br/>
要比較`CSid`的第`SID`二個物件或結構。

### <a name="return-value"></a>傳回值

如果物件相等，則傳回 TRUE，如果不相等，則傳回 FALSE。

## <a name="operator-"></a><a name="operator_neq"></a>operator！ =

比較`CSid`物件或`SID` （安全識別碼）結構是否不相等。

```cpp
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*<br/>
要比較`CSid`的第`SID`一個物件或結構。

*rhs*<br/>
要比較`CSid`的第`SID`二個物件或結構。

### <a name="return-value"></a>傳回值

如果物件不相等，則傳回 TRUE，如果相等，則傳回 FALSE。

## <a name="operator-"></a><a name="operator_lt"></a>運算子 <

測試運算子左邊`CSid`的物件`SID`或結構是否小於右邊的`CSid`物件或`SID`結構（適用于 c + + 標準程式庫相容性）。

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*<br/>
要比較`CSid`的第`SID`一個物件或結構。

*rhs*<br/>
要比較`CSid`的第`SID`二個物件或結構。

### <a name="return-value"></a>傳回值

如果*lhs*物件的位址小於*rhs*物件的位址，則傳回 TRUE，否則傳回 FALSE。

### <a name="remarks"></a>備註

這個運算子會處理`CSid`物件或`SID`結構的位址，並實作為提供與 c + + 標準程式庫集合類別的相容性。

## <a name="operator-"></a><a name="operator_gt"></a>運算子 >

測試運算子左邊`CSid`的物件`SID`或結構是否大於右邊的`CSid`物件或`SID`結構（適用于 c + + 標準程式庫相容性）。

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*<br/>
要比較`CSid`的第`SID`一個物件或結構。

*rhs*<br/>
要比較`CSid`的第`SID`二個物件或結構。

### <a name="return-value"></a>傳回值

如果*lhs*的位址大於*rhs*的位址，則傳回 TRUE，否則傳回 FALSE。

### <a name="remarks"></a>備註

這個運算子會處理`CSid`物件或`SID`結構的位址，並實作為提供與 c + + 標準程式庫集合類別的相容性。

## <a name="operator-"></a><a name="operator_lt__eq"></a>運算子 <=

測試運算子左邊`CSid`的物件`SID`或結構是否小於或等於右邊的`CSid`物件或`SID`結構（適用于 c + + 標準程式庫相容性）。

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*<br/>
要比較`CSid`的第`SID`一個物件或結構。

*rhs*<br/>
要比較`CSid`的第`SID`二個物件或結構。

### <a name="return-value"></a>傳回值

如果*lhs*的位址小於或等於*rhs*的位址，則傳回 TRUE，否則傳回 FALSE。

### <a name="remarks"></a>備註

這個運算子會處理`CSid`物件或`SID`結構的位址，並實作為提供與 c + + 標準程式庫集合類別的相容性。

## <a name="operator-"></a><a name="operator_gt__eq"></a>運算子 >=

測試運算子左邊`CSid`的物件`SID`或結構是否大於或等於右邊的`CSid`物件或`SID`結構（適用于 c + + 標準程式庫相容性）。

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>參數

*lhs*<br/>
要比較`CSid`的第`SID`一個物件或結構。

*rhs*<br/>
要比較`CSid`的第`SID`二個物件或結構。

### <a name="return-value"></a>傳回值

如果*lhs*的位址大於或等於*rhs*的位址，則傳回 TRUE，否則傳回 FALSE。

### <a name="remarks"></a>備註

這個運算子會處理`CSid`物件或`SID`結構的位址，並實作為提供與 c + + 標準程式庫集合類別的相容性。
