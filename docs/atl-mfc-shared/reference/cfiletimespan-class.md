---
title: CFileTimeSpan 類別
ms.date: 10/18/2018
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
ms.openlocfilehash: f9bb42ba4c142f671a83dcfa7e99cff940fff047
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491285"
---
# <a name="cfiletimespan-class"></a>CFileTimeSpan 類別

這個類別會提供方法來管理與檔案相關聯的相對日期和時間值。

## <a name="syntax"></a>語法

```
class CFileTimeSpan
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CFileTimeSpan::CFileTimeSpan](#cfiletimespan)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CFileTimeSpan::GetTimeSpan](#gettimespan)|呼叫這個方法, 以從`CFileTimeSpan`物件取出時間範圍。|
|[CFileTimeSpan::SetTimeSpan](#settimespan)|呼叫這個方法以設定`CFileTimeSpan`物件的時間範圍。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[CFileTimeSpan:: operator-](#operator_-)|在`CFileTimeSpan`物件上執行減法。|
|[CFileTimeSpan::operator !=](#operator_neq)|比較兩個 `CFileTimeSpan` 物件是否不相等。|
|[CFileTimeSpan:: operator +](#operator_add)|在`CFileTimeSpan`物件上執行加法。|
|[CFileTimeSpan:: operator + =](#operator_add_eq)|在`CFileTimeSpan`物件上執行加法, 並將結果指派給目前的物件。|
|[CFileTimeSpan:: operator&lt;](#operator_lt)|比較兩`CFileTimeSpan`個物件以判斷較小者。|
|[CFileTimeSpan:: operator&lt;=](#operator_lt_eq)|比較兩`CFileTimeSpan`個物件來判斷是否相等或較小。|
|[CFileTimeSpan::operator =](#operator_eq)|指派運算子。|
|[CFileTimeSpan::operator -=](#operator_-_eq)|在`CFileTimeSpan`物件上執行減法, 並將結果指派給目前的物件。|
|[CFileTimeSpan:: operator = =](#operator_eq_eq)|比較兩個 `CFileTimeSpan` 物件是否相等。|
|[CFileTimeSpan:: operator&gt;](#operator_gt)|比較兩`CFileTimeSpan`個物件來判斷較大的。|
|[CFileTimeSpan:: operator&gt;=](#operator_gt_eq)|比較兩`CFileTimeSpan`個物件來判斷是否相等或更大。|

## <a name="remarks"></a>備註

這個類別提供了一些方法, 可用來管理在執行有關建立檔案、上次存取或上次修改檔案時所遇到的相關作業。 這個類別的方法經常與[CFileTime 類別](../../atl-mfc-shared/reference/cfiletime-class.md)物件搭配使用。

## <a name="example"></a>範例

請參閱[CFileTime:: 毫秒](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond)的範例。

## <a name="requirements"></a>需求

**標頭:** atltime。h

##  <a name="cfiletimespan"></a>CFileTimeSpan::CFileTimeSpan

建構函式。

```
CFileTimeSpan() throw();
CFileTimeSpan(const CFileTimeSpan& span) throw();
CFileTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>參數

*span*<br/>
現有的 `CFileTimeSpan` 物件。

*nSpan*<br/>
一段時間 (以毫秒為單位)。

### <a name="remarks"></a>備註

物件可以使用現有`CFileTimeSpan`的物件建立, 或以64位值表示。 `CFileTimeSpan` 預設的函式會將時間範圍設定為0。

##  <a name="gettimespan"></a>CFileTimeSpan::GetTimeSpan

呼叫這個方法, 以從`CFileTimeSpan`物件取出時間範圍。

```
LONGLONG GetTimeSpan() const throw();
```

### <a name="return-value"></a>傳回值

傳回時間範圍 (以毫秒為單位)。

##  <a name="operator_-"></a>CFileTimeSpan:: operator-

在`CFileTimeSpan`物件上執行減法。

```
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*span*<br/>
          `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

`CFileTimeSpan`傳回物件, 代表兩個時間範圍間差異的結果。

##  <a name="operator_neq"></a>CFileTimeSpan:: operator! =

比較兩個 `CFileTimeSpan` 物件是否不相等。

```
bool operator!=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*span*<br/>
要比較的 `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

如果要比較的專案不等於`CFileTimeSpan`物件, 則傳回 TRUE, 否則傳回 FALSE。

##  <a name="operator_add"></a>CFileTimeSpan:: operator +

在`CFileTimeSpan`物件上執行加法。

```
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*span*<br/>
          `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

`CFileTimeSpan`傳回物件, 其中包含兩個時間範圍的總和。

##  <a name="operator_add_eq"></a>CFileTimeSpan:: operator + =

在`CFileTimeSpan`物件上執行加法, 並將結果指派給目前的物件。

```
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>參數

*span*<br/>
          `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

傳回包含兩`CFileTimeSpan`個時間範圍總和的已更新物件。

##  <a name="operator_lt"></a>CFileTimeSpan:: operator&lt;

比較兩`CFileTimeSpan`個物件以判斷較小者。

```
bool operator<(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*span*<br/>
要比較的 `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

如果第一個物件小於第二個, 則傳回 TRUE, 否則傳回 FALSE。

##  <a name="operator_lt_eq"></a>CFileTimeSpan:: operator&lt;=

比較兩`CFileTimeSpan`個物件來判斷是否相等或較小。

```
bool operator<=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*span*<br/>
要比較的 `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

如果第一個物件小於 (也就是代表較短的時間週期) 或等於第二個物件, 則傳回 TRUE, 否則傳回 FALSE。

##  <a name="operator_eq"></a>CFileTimeSpan:: operator =

指派運算子。

```
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```

### <a name="parameters"></a>參數

*span*<br/>
          `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

傳回已更新`CFileTimeSpan`的物件。

##  <a name="operator_-_eq"></a>CFileTimeSpan:: operator-=

在`CFileTimeSpan`物件上執行減法運算, 並將結果指派給目前的物件。

```
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>參數

*span*<br/>
          `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

傳回已更新`CFileTimeSpan`的物件。

##  <a name="operator_eq_eq"></a>CFileTimeSpan:: operator = =

比較兩個 `CFileTimeSpan` 物件是否相等。

```
bool operator==(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*span*<br/>
要比較的 `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

如果物件相等, 則傳回 TRUE, 否則傳回 FALSE。

##  <a name="operator_gt"></a>CFileTimeSpan:: operator&gt;

比較兩`CFileTimeSpan`個物件來判斷較大的。

```
bool operator>(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*span*<br/>
要比較的 `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

如果第一個物件大於 (也就是表示較長的時間週期), 則傳回 TRUE, 否則傳回 FALSE。

##  <a name="operator_gt_eq"></a>CFileTimeSpan:: operator&gt;=

比較兩`CFileTimeSpan`個物件來判斷是否相等或更大。

```
bool operator>=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*span*<br/>
要比較的 `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

如果第一個物件大於 (也就是代表較長的時間週期) 或等於第二個物件, 則傳回 TRUE, 否則傳回 FALSE。

##  <a name="settimespan"></a>CFileTimeSpan::SetTimeSpan

呼叫這個方法以設定`CFileTimeSpan`物件的時間範圍。

```
void SetTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>參數

*nSpan*<br/>
時間範圍的新值 (以毫秒為單位)。

## <a name="see-also"></a>另請參閱

[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)<br/>
[CFileTime 類別](../../atl-mfc-shared/reference/cfiletime-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)
