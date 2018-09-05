---
title: CFileTimeSpan 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::GetTimeSpan
- ATLTIME/ATL::CFileTimeSpan::SetTimeSpan
dev_langs:
- C++
helpviewer_keywords:
- shared classes, CFileTimeSpan
- CFileTimeSpan class
ms.assetid: 5856fb39-9c82-4027-8ccf-8760890491ec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 06a9f4275ff6acfcef7b7173fbfc6f9abf89b4f3
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43766002"
---
# <a name="cfiletimespan-class"></a>CFileTimeSpan 類別

這個類別會提供管理相對的日期和時間值與檔案相關聯的方法。

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
|[CFileTimeSpan::GetTimeSpan](#gettimespan)|呼叫這個方法來擷取時間範圍內，從`CFileTimeSpan`物件。|
|[CFileTimeSpan::SetTimeSpan](#settimespan)|呼叫此方法以設定的時間範圍內`CFileTimeSpan`物件。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CFileTimeSpan::operator-](#operator_-)|在上執行減法`CFileTimeSpan`物件。|
|[CFileTimeSpan::operator ！ =](#operator_neq)|比較兩個 `CFileTimeSpan` 物件是否不相等。|
|[CFileTimeSpan::operator +](#operator_add)|在上執行加法`CFileTimeSpan`物件。|
|[CFileTimeSpan::operator + =](#operator_add_eq)|在上執行加法`CFileTimeSpan`物件，並將結果指派給目前的物件。|
|[CFileTimeSpan::operator &lt;](#operator_lt)|比較兩個`CFileTimeSpan`物件來判斷較小者。|
|[CFileTimeSpan::operator &lt;=](#operator_lt_eq)|比較兩個`CFileTimeSpan`物件來判斷是否相等或較小者。|
|[CFileTimeSpan::operator =](#operator_eq)|指派運算子。|
|[CFileTimeSpan::operator =](#operator_-_eq)|在上執行減法`CFileTimeSpan`物件，並將結果指派給目前的物件。|
|[CFileTimeSpan::operator = =](#operator_eq_eq)|比較兩個 `CFileTimeSpan` 物件是否相等。|
|[CFileTimeSpan::operator &gt;](#operator_gt)|比較兩個`CFileTimeSpan`判斷較大的物件。|
|[CFileTimeSpan::operator &gt;=](#operator_gt_eq)|比較兩個`CFileTimeSpan`來判斷是否相等或較大的物件。|

## <a name="remarks"></a>備註

這個類別會提供方法來管理相對週期的時間執行時相關的作業時，通常會遇到的檔案已建立、 上一次存取或上次修改。 這個類別的方法通常用於搭配[CFileTime 類別](../../atl-mfc-shared/reference/cfiletime-class.md)物件。

## <a name="example"></a>範例

範例，請參閱[CFileTime::Millisecond](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond)。

## <a name="requirements"></a>需求

**標頭：** atltime.h

##  <a name="cfiletimespan"></a>  CFileTimeSpan::CFileTimeSpan

建構函式。

```
CFileTimeSpan() throw();
CFileTimeSpan(const CFileTimeSpan& span) throw();
CFileTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>參數

*範圍*  
現有的 `CFileTimeSpan` 物件。

*nSpan*  
一段時間 （毫秒）。

### <a name="remarks"></a>備註

`CFileTimeSpan`可以建立物件，使用現有`CFileTimeSpan`物件，或以 64 位元值。 預設建構函式會將時間範圍設為 0。

##  <a name="gettimespan"></a>  CFileTimeSpan::GetTimeSpan

呼叫這個方法來擷取時間範圍內，從`CFileTimeSpan`物件。

```
LONGLONG GetTimeSpan() const throw();
```

### <a name="return-value"></a>傳回值

傳回的時間範圍，以毫秒為單位。

##  <a name="operator_-"></a>  CFileTimeSpan::operator-

在上執行減法`CFileTimeSpan`物件。

```
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*範圍*  
`CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

傳回`CFileTimeSpan`物件，表示兩個時間範圍之間的差異的結果。

##  <a name="operator_neq"></a>  CFileTimeSpan::operator ！ =

比較兩個 `CFileTimeSpan` 物件是否不相等。

```
bool operator!=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*範圍*  
要比較的 `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

要比較的項目是否不相等，則傳回 TRUE`CFileTimeSpan`物件，否則為 FALSE。

##  <a name="operator_add"></a>  CFileTimeSpan::operator +

在上執行加法`CFileTimeSpan`物件。

```
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*範圍*  
`CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

傳回`CFileTimeSpan`物件包含兩個時間的總和的跨越。

##  <a name="operator_add_eq"></a>  CFileTimeSpan::operator + =

在上執行加法`CFileTimeSpan`物件，並將結果指派給目前的物件。

```
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>參數

*範圍*  
`CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

傳回已更新`CFileTimeSpan`物件包含兩個時間的總和的跨越。

##  <a name="operator_lt"></a>  CFileTimeSpan::operator &lt;

比較兩個`CFileTimeSpan`物件來判斷較小者。

```
bool operator<(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*範圍*  
要比較的 `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

會傳回 TRUE，如果第一個物件小於 （也就是代表較短的時間） 第二個，否則為 FALSE。

##  <a name="operator_lt_eq"></a>  CFileTimeSpan::operator &lt;=

比較兩個`CFileTimeSpan`物件來判斷是否相等或較小者。

```
bool operator<=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*範圍*  
要比較的 `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

傳回值為 TRUE 的第一個物件小於 （也就是代表較短的時間） 或等於第二個，否則為 FALSE。

##  <a name="operator_eq"></a>  CFileTimeSpan::operator =

指派運算子。

```
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```

### <a name="parameters"></a>參數

*範圍*  
`CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

傳回已更新`CFileTimeSpan`物件。

##  <a name="operator_-_eq"></a>  CFileTimeSpan::operator =

在上執行減法`CFileTimeSpan`物件，並將結果指派給目前的物件。

```
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>參數

*範圍*  
`CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

傳回已更新`CFileTimeSpan`物件。

##  <a name="operator_eq_eq"></a>  CFileTimeSpan::operator = =

比較兩個 `CFileTimeSpan` 物件是否相等。

```
bool operator==(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*範圍*  
要比較的 `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

如果物件相等，否則為 FALSE，則傳回 TRUE。

##  <a name="operator_gt"></a>  CFileTimeSpan::operator &gt;

比較兩個`CFileTimeSpan`判斷較大的物件。

```
bool operator>(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*範圍*  
要比較的 `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

會傳回 TRUE，如果第一個物件大於 （也就是代表較長的時間週期） 第二個，否則為 FALSE。

##  <a name="operator_gt_eq"></a>  CFileTimeSpan::operator &gt;=

比較兩個`CFileTimeSpan`來判斷是否相等或較大的物件。

```
bool operator>=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*範圍*  
要比較的 `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

會傳回 TRUE，如果第一個物件大於 （也就是代表較長的時間期間） 或等於第二個，否則為 FALSE。

##  <a name="settimespan"></a>  CFileTimeSpan::SetTimeSpan

呼叫此方法以設定的時間範圍內`CFileTimeSpan`物件。

```
void SetTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>參數

*nSpan*  
時間範圍內，以毫秒為單位的新值。

## <a name="see-also"></a>另請參閱

[FILETIME](https://msdn.microsoft.com/library/windows/desktop/ms724284)   
[CFileTime 類別](../../atl-mfc-shared/reference/cfiletime-class.md)   
[階層架構圖表](../../mfc/hierarchy-chart.md)   
[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)

