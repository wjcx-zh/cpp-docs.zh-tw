---
title: CFileTimeSpan 類別
ms.date: 01/06/2020
f1_keywords:
- CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::GetTimeSpan
- ATLTIME/ATL::CFileTimeSpan::SetTimeSpan
helpviewer_keywords:
- shared classes, CFileTimeSpan
- CFileTimeSpan class
ms.assetid: 5856fb39-9c82-4027-8ccf-8760890491ec
ms.openlocfilehash: 9220ed8373e78db727b43ecb59880dcfbcc98f96
ms.sourcegitcommit: 7bd3567fc6a0e7124aab51cad63bbdb44a99a848
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75755060"
---
# <a name="cfiletimespan-class"></a>CFileTimeSpan 類別

這個類別會提供方法來管理與檔案相關聯的相對日期和時間值。

## <a name="syntax"></a>語法

```cpp
class CFileTimeSpan
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公用建構函式

|Name|描述|
|----------|-----------------|
|[CFileTimeSpan::CFileTimeSpan](#cfiletimespan)|建構函式。|

### <a name="public-methods"></a>公用方法

|Name|描述|
|----------|-----------------|
|[CFileTimeSpan::GetTimeSpan](#gettimespan)|呼叫這個方法，以從 `CFileTimeSpan` 物件中取出時間範圍。|
|[CFileTimeSpan::SetTimeSpan](#settimespan)|呼叫這個方法來設定 `CFileTimeSpan` 物件的時間範圍。|

### <a name="public-operators"></a>公用運算子

|Name|描述|
|----------|-----------------|
|[CFileTimeSpan：： operator-](#operator_-)|在 `CFileTimeSpan` 物件上執行減法運算。|
|[CFileTimeSpan：： operator！ =](#operator_neq)|比較兩個 `CFileTimeSpan` 物件是否不相等。|
|[CFileTimeSpan：： operator +](#operator_add)|在 `CFileTimeSpan` 物件上執行加法。|
|[CFileTimeSpan：： operator + =](#operator_add_eq)|在 `CFileTimeSpan` 物件上執行加法，並將結果指派給目前的物件。|
|[CFileTimeSpan：： operator &lt;](#operator_lt)|比較兩個 `CFileTimeSpan` 的物件，以判斷較小者。|
|[CFileTimeSpan：： operator &lt;=](#operator_lt_eq)|比較兩個 `CFileTimeSpan` 的物件，以判斷是否相等或較小。|
|[CFileTimeSpan：： operator =](#operator_eq)|指派運算子。|
|[CFileTimeSpan：： operator-=](#operator_-_eq)|在 `CFileTimeSpan` 物件上執行減法運算，並將結果指派給目前的物件。|
|[CFileTimeSpan：： operator = =](#operator_eq_eq)|比較兩個 `CFileTimeSpan` 物件是否相等。|
|[CFileTimeSpan：： operator &gt;](#operator_gt)|比較兩個 `CFileTimeSpan` 的物件，以判斷較大的。|
|[CFileTimeSpan：： operator &gt;=](#operator_gt_eq)|比較兩個 `CFileTimeSpan` 的物件，以判斷是否相等或較大。|

## <a name="remarks"></a>備註

這個類別會提供方法來處理檔案系統使用之單位的相對時間週期。 這些單位通常用於關於建立、上次存取或上次修改檔案時的作業。 這個類別的方法經常與[CFileTime 類別](../../atl-mfc-shared/reference/cfiletime-class.md)物件搭配使用。

## <a name="example"></a>範例

請參閱[CFileTime：：毫秒](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond)的範例。

## <a name="requirements"></a>需求

**標頭：** atltime。h

## <a name="cfiletimespan"></a>CFileTimeSpan::CFileTimeSpan

建構函式。

```cpp
CFileTimeSpan() throw();
CFileTimeSpan(const CFileTimeSpan& span) throw();
CFileTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>參數

*span*\
現有的 `CFileTimeSpan` 物件。

*nSpan*\
一段時間（以毫秒為單位）。

### <a name="remarks"></a>備註

`CFileTimeSpan` 物件可以使用現有的 `CFileTimeSpan` 物件來建立，或以64位值表示。 預設的函式會將時間範圍設定為0。

## <a name="gettimespan"></a>CFileTimeSpan::GetTimeSpan

呼叫這個方法，以從 `CFileTimeSpan` 物件中取出時間範圍。

```cpp
LONGLONG GetTimeSpan() const throw();
```

### <a name="return-value"></a>傳回值

傳回時間範圍（以毫秒為單位）。

## <a name="operator_-"></a>CFileTimeSpan：： operator-

在 `CFileTimeSpan` 物件上執行減法運算。

```cpp
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*span*\
`CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

傳回 `CFileTimeSpan` 物件，代表兩個時間範圍間差異的結果。

## <a name="operator_neq"></a>CFileTimeSpan：： operator！ =

比較兩個 `CFileTimeSpan` 物件是否不相等。

```cpp
bool operator!=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*span*\
要比較的 `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

如果要比較的專案不等於 `CFileTimeSpan` 物件，則傳回 TRUE;否則為 FALSE。

## <a name="operator_add"></a>CFileTimeSpan：： operator +

在 `CFileTimeSpan` 物件上執行加法。

```cpp
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*span*\
`CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

傳回包含兩個時間範圍總和的 `CFileTimeSpan` 物件。

## <a name="operator_add_eq"></a>CFileTimeSpan：： operator + =

在 `CFileTimeSpan` 物件上執行加法，並將結果指派給目前的物件。

```cpp
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>參數

*span*\
`CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

傳回已更新的 `CFileTimeSpan` 物件，其中包含兩個時間範圍的總和。

## <a name="operator_lt"></a>CFileTimeSpan：： operator &lt;

比較兩個 `CFileTimeSpan` 的物件，以判斷較小者。

```cpp
bool operator<(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*span*\
要比較的 `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

如果第一個物件小於第二個，則傳回 TRUE，否則傳回 FALSE。

## <a name="operator_lt_eq"></a>CFileTimeSpan：： operator &lt;=

比較兩個 `CFileTimeSpan` 的物件，以判斷是否相等或較小。

```cpp
bool operator<=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*span*\
要比較的 `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

如果第一個物件小於（也就是代表較短的時間週期）或等於第二個物件，則傳回 TRUE，否則傳回 FALSE。

## <a name="operator_eq"></a>CFileTimeSpan：： operator =

指派運算子。

```cpp
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```

### <a name="parameters"></a>參數

*span*\
`CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

傳回已更新的 `CFileTimeSpan` 物件。

## <a name="operator_-_eq"></a>CFileTimeSpan：： operator-=

在 `CFileTimeSpan` 物件上執行減法運算，並將結果指派給目前的物件。

```cpp
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>參數

*span*\
`CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

傳回已更新的 `CFileTimeSpan` 物件。

## <a name="operator_eq_eq"></a>CFileTimeSpan：： operator = =

比較兩個 `CFileTimeSpan` 物件是否相等。

```cpp
bool operator==(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*span*\
要比較的 `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

如果物件相等，則傳回 TRUE，否則傳回 FALSE。

## <a name="operator_gt"></a>CFileTimeSpan：： operator &gt;

比較兩個 `CFileTimeSpan` 的物件，以判斷較大的。

```cpp
bool operator>(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*span*\
要比較的 `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

如果第一個物件大於（也就是表示較長的時間週期），則傳回 TRUE，否則傳回 FALSE。

## <a name="operator_gt_eq"></a>CFileTimeSpan：： operator &gt;=

比較兩個 `CFileTimeSpan` 的物件，以判斷是否相等或較大。

```cpp
bool operator>=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*span*\
要比較的 `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

如果第一個物件大於（也就是代表較長的時間週期）或等於第二個物件，則傳回 TRUE，否則傳回 FALSE。

## <a name="settimespan"></a>CFileTimeSpan::SetTimeSpan

呼叫這個方法來設定 `CFileTimeSpan` 物件的時間範圍。

```cpp
void SetTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>參數

*nSpan*\
時間範圍的新值（以 100-毫微秒為單位）。 如需詳細資訊，請參閱[CFileTime](cfiletime-class.md)。

## <a name="see-also"></a>請參閱

[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)\
[CFileTime 類別](cfiletime-class.md)\
階層架構[圖表](../../mfc/hierarchy-chart.md)\
[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)
