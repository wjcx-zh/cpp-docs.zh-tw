---
title: CFileTime 類別
ms.date: 10/18/2018
f1_keywords:
- CFileTime
- ATLTIME/ATL::CFileTime
- ATLTIME/ATL::CFileTime::CFileTime
- ATLTIME/ATL::CFileTime::GetCurrentTime
- ATLTIME/ATL::CFileTime::GetTime
- ATLTIME/ATL::CFileTime::LocalToUTC
- ATLTIME/ATL::CFileTime::SetTime
- ATLTIME/ATL::CFileTime::UTCToLocal
- ATLTIME/ATL::CFileTime::Day
- ATLTIME/ATL::CFileTime::Hour
- ATLTIME/ATL::CFileTime::Millisecond
- ATLTIME/ATL::CFileTime::Minute
- ATLTIME/ATL::CFileTime::Second
- ATLTIME/ATL::CFileTime::Week
helpviewer_keywords:
- CFileTime class
- shared classes, CFileTime
ms.assetid: 1a358a65-1383-4124-b0d4-59b026e6860f
ms.openlocfilehash: 07b888b031a38dc2f09404a14e729e26b3eaa019
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62235129"
---
# <a name="cfiletime-class"></a>CFileTime 類別

這個類別提供方法來管理與檔案相關聯的日期和時間值。

## <a name="syntax"></a>語法

```
class CFileTime :  public FILETIME
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CFileTime::CFileTime](#cfiletime)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CFileTime::GetCurrentTime](#getcurrenttime)|呼叫此靜態函式來擷取`CFileTime`物件，表示目前的系統日期和時間。|
|[CFileTime::GetTime](#gettime)|呼叫這個方法來擷取從時間`CFileTime`物件。|
|[CFileTime::LocalToUTC](#localtoutc)|呼叫這個方法來將本機檔案時間轉換為以 Coordinated Universal Time (UTC) 上檔案時間。|
|[CFileTime::SetTime](#settime)|呼叫此方法以設定的日期和時間儲存`CFileTime`物件。|
|[CFileTime::UTCToLocal](#utctolocal)|呼叫這個方法來轉換以時間為基礎在 Coordinated Universal Time (UTC) 到本機檔案的時間。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CFileTime::operator -](#operator_-)|此運算子用上執行減法`CFileTime`或`CFileTimeSpan`物件。|
|[CFileTime::operator !=](#operator_neq)|此運算子比較兩個`CFileTime`物件是否不相等。|
|[CFileTime::operator +](#operator_add)|此運算子用在 `CFileTimeSpan` 物件上執行加法。|
|[CFileTime::operator +=](#operator_add_eq)|此運算子用在 `CFileTimeSpan` 物件上執行加法並指派結果給目前物件。|
|[CFileTime::operator &lt;](#operator_lt)|此運算子比較兩個 `CFileTime` 物件來判斷何者較小。|
|[CFileTime::operator &lt;=](#operator_lt_eq)|此運算子比較兩個 `CFileTime` 物件來判斷是否相等或何者較小。|
|[CFileTime::operator =](#operator_eq)|指派運算子。|
|[CFileTime::operator -=](#operator_-_eq)|此運算子用上執行減法`CFileTimeSpan`物件，並將結果指派給目前的物件。|
|[CFileTime::operator ==](#operator_eq_eq)|此運算子比較兩個 `CFileTime` 物件是否相等。|
|[CFileTime::operator &gt;](#operator_gt)|此運算子比較兩個 `CFileTime` 物件來判斷何者較大。|
|[CFileTime::operator &gt;=](#operator_gt_eq)|此運算子比較兩個 `CFileTime` 物件來判斷是否相等或何者較大。|

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[CFileTime::Day](#day)|構成一天儲存 100 奈秒間隔數的靜態資料成員。|
|[CFileTime::Hour](#hour)|靜態資料成員，用來儲存構成一小時的 100 奈秒間隔數。|
|[CFileTime::Millisecond](#millisecond)|靜態資料成員，用來儲存構成一毫秒的 100 奈秒間隔數。|
|[CFileTime::Minute](#minute)|靜態資料成員，用來儲存構成一分鐘的 100 奈秒間隔數。|
|[CFileTime::Second](#second)|組成一個第二個儲存的 100 奈秒間隔數的靜態資料成員。|
|[CFileTime::Week](#week)|靜態資料成員，用來儲存構成一週的 100 奈秒間隔數。|

## <a name="remarks"></a>備註

這個類別提供方法來管理與建立、 存取和修改檔案相關聯的日期和時間值。 這個類別的資料會使用方法和經常搭配`CFileTimeSpan`處理相對時間值的物件。

日期和時間值會儲存為 64 位元值，表示自 1601 年 1 月 1 日起的 100 奈秒間隔數。 這是國際標準時間 (UTC) 格式。

以下列靜態 const 成員變數會提供簡化的計算：

|成員變數|100 奈秒間隔的數目|
|---------------------|-----------------------------------------|
|Millisecond|10,000|
|Second|毫秒\*1000|
|Minute|第二個\*60|
|Hour|分鐘\*60|
|Day|小時\*24|
|一週|天\*7|

**請注意**並非所有的檔案系統可以記錄建立和上次存取時間和不是所有的檔案系統會將其記錄在相同的方式。 範例中的，在 Windows NT FAT 檔案系統中，建立時間的解析度為 10 毫秒，寫入時間有解析度為 2 秒，而且存取時間有 1 天 （存取的日期） 的解決方案。 在 NTFS，存取時間會有 1 小時的解決方案。 此外，FAT 當地時間，記錄在磁碟上的時間，但 NTFS 會記錄在磁碟上的時間-utc 時區。 如需詳細資訊，請參閱 <<c0> [ 檔案的時間](/windows/desktop/SysInfo/file-times)。

## <a name="inheritance-hierarchy"></a>繼承階層

`FILETIME`

`CFileTime`

## <a name="requirements"></a>需求

**標頭：** atltime.h

##  <a name="cfiletime"></a>  CFileTime::CFileTime

建構函式。

```
CFileTime() throw();
CFileTime(const FILETIME& ft) throw();
CFileTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>參數

*ft*<br/>
A [FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime)結構。

*nTime*<br/>
表示日期和時間做為 64 位元值。

### <a name="remarks"></a>備註

`CFileTime`物件可以使用現有的日期和時間建立`FILETIME`結構，或表示成 64 位元值 （在本機或 Coordinated Universal Time (UTC) 時間格式）。 預設建構函式會設定為 0 的時間。

##  <a name="day"></a>  CFileTime::Day

構成一天儲存 100 奈秒間隔數的靜態資料成員。

```
static const ULONGLONG Day = Hour* 24;
```

### <a name="example"></a>範例

範例，請參閱[CFileTime::Millisecond](#millisecond)。

##  <a name="getcurrenttime"></a>  CFileTime::GetCurrentTime

呼叫此靜態函式來擷取`CFileTime`物件，表示目前的系統日期和時間。

```
static CFileTime GetCurrentTime() throw();
```

### <a name="return-value"></a>傳回值

傳回目前的系統日期和時間，格式為 Coordinated Universal Time (UTC)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#41](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_1.cpp)]

##  <a name="gettime"></a>  CFileTime::GetTime

呼叫這個方法來擷取從時間`CFileTime`物件。

```
ULONGLONG GetTime() const throw();
```

### <a name="return-value"></a>傳回值

傳回的日期和時間為 64 位元數字，可能會在本機或 Coordinated Universal Time (UTC) 格式。

##  <a name="hour"></a>  CFileTime::Hour

靜態資料成員，用來儲存構成一小時的 100 奈秒間隔數。

```
static const ULONGLONG Hour = Minute* 60;
```

### <a name="example"></a>範例

範例，請參閱[CFileTime::Millisecond](#millisecond)。

##  <a name="localtoutc"></a>  CFileTime::LocalToUTC

呼叫這個方法來將本機檔案時間轉換為以 Coordinated Universal Time (UTC) 上檔案時間。

```
CFileTime LocalToUTC() const throw();
```

### <a name="return-value"></a>傳回值

傳回`CFileTime`物件，其中包含時間以 UTC 格式。

### <a name="example"></a>範例

範例，請參閱[CFileTime::UTCToLocal](#utctolocal)。

##  <a name="millisecond"></a>  CFileTime::Millisecond

靜態資料成員，用來儲存構成一毫秒的 100 奈秒間隔數。

```
static const ULONGLONG Millisecond = 10000;
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#44](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_2.cpp)]

##  <a name="minute"></a>  CFileTime::Minute

靜態資料成員，用來儲存構成一分鐘的 100 奈秒間隔數。

```
static const ULONGLONG Minute = Second* 60;
```

### <a name="example"></a>範例

範例，請參閱[CFileTime::Millisecond](#millisecond)。

##  <a name="operator_-"></a>  CFileTime::operator -

此運算子用上執行減法`CFileTime`或`CFileTimeSpan`物件。

```
CFileTime operator-(CFileTimeSpan span) const throw();
CFileTimeSpan operator-(CFileTime ft) const throw();
```

### <a name="parameters"></a>參數

*span*<br/>
`CFileTimeSpan` 物件。

*ft*<br/>
`CFileTime` 物件。

### <a name="return-value"></a>傳回值

傳回`CFileTime`物件或`CFileTimeSpan`物件，表示兩個物件之間的時間差異的結果。

##  <a name="operator_neq"></a>  CFileTime::operator ！ =

此運算子比較兩個`CFileTime`物件是否不相等。

```
bool operator!=(CFileTime ft) const throw();
```

### <a name="parameters"></a>參數

*ft*<br/>
要比較的 `CFileTime` 物件。

### <a name="return-value"></a>傳回值

要比較的項目是否不相等，則傳回 TRUE`CFileTime`物件，否則為 FALSE。

##  <a name="operator_add"></a>  CFileTime::operator +

此運算子用在 `CFileTimeSpan` 物件上執行加法。

```
CFileTime operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*span*<br/>
`CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

傳回`CFileTime`物件，表示結果的原始時間加上相對的時間。

##  <a name="operator_add_eq"></a>  CFileTime::operator + =

此運算子用在 `CFileTimeSpan` 物件上執行加法並指派結果給目前物件。

```
CFileTime& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>參數

*span*<br/>
`CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

傳回已更新`CFileTime`物件，表示結果的原始時間加上相對的時間。

##  <a name="operator_lt"></a>  CFileTime::operator &lt;

此運算子比較兩個 `CFileTime` 物件來判斷何者較小。

```
bool operator<(CFileTime ft) const throw();
```

### <a name="parameters"></a>參數

*ft*<br/>
要比較的 `CFileTime` 物件。

### <a name="return-value"></a>傳回值

為 true，則會傳回第一個物件是否小於 （稍早的時間），第二個，FALSE 否則。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#43](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_3.cpp)]

##  <a name="operator_lt_eq"></a>  CFileTime::operator &lt;=

此運算子比較兩個 `CFileTime` 物件來判斷是否相等或何者較小。

```
bool operator<=(CFileTime ft) const throw();
```

### <a name="parameters"></a>參數

*ft*<br/>
要比較的 `CFileTime` 物件。

### <a name="return-value"></a>傳回值

會傳回 TRUE，如果第一個物件小於 （早的時間） 或等於第二個，否則為 FALSE。

##  <a name="operator_eq"></a>  CFileTime::operator =

指派運算子。

```
CFileTime& operator=(const FILETIME& ft) throw();
```

### <a name="parameters"></a>參數

*ft*<br/>
A`CFileTime`物件，其中包含新的時間和日期。

### <a name="return-value"></a>傳回值

傳回已更新`CFileTime`物件。

##  <a name="operator_-_eq"></a>  CFileTime::operator -=

此運算子用上執行減法`CFileTimeSpan`物件，並將結果指派給目前的物件。

```
CFileTime& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>參數

*span*<br/>
A`CFileTimeSpan`物件，其中包含要減去的相對時間。

### <a name="return-value"></a>傳回值

傳回已更新`CFileTime`物件。

##  <a name="operator_eq_eq"></a>  CFileTime::operator = =

此運算子比較兩個 `CFileTime` 物件是否相等。

```
bool operator==(CFileTime ft) const throw();
```

### <a name="parameters"></a>參數

*ft*<br/>
`CFileTime`来比較的物件。

### <a name="return-value"></a>傳回值

如果物件相等，否則為 FALSE，則傳回 TRUE。

##  <a name="operator_gt"></a>  CFileTime::operator &gt;

此運算子比較兩個 `CFileTime` 物件來判斷何者較大。

```
bool operator>(CFileTime ft) const throw();
```

### <a name="parameters"></a>參數

*ft*<br/>
要比較的 `CFileTime` 物件。

### <a name="return-value"></a>傳回值

會傳回 TRUE，如果第一個物件大於 （稍後時間） 第二個，否則為 FALSE。

##  <a name="operator_gt_eq"></a>  CFileTime::operator &gt;=

此運算子比較兩個 `CFileTime` 物件來判斷是否相等或何者較大。

```
bool operator>=(CFileTime ft) const throw();
```

### <a name="parameters"></a>參數

*ft*<br/>
要比較的 `CFileTime` 物件。

### <a name="return-value"></a>傳回值

會傳回 TRUE，如果第一個物件 （稍後時間） 大於或等於第二個，否則為 FALSE。

##  <a name="second"></a>  CFileTime::Second

構成一天儲存 100 奈秒間隔數的靜態資料成員。

```
static const ULONGLONG Second = Millisecond* 1000;
```

### <a name="example"></a>範例

範例，請參閱[CFileTime::Millisecond](#millisecond)。

##  <a name="settime"></a>  CFileTime::SetTime

呼叫此方法以設定的日期和時間儲存`CFileTime`物件。

```
void SetTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>參數

*nTime*<br/>
64 位元值，其代表的日期和時間，請在本機或 Coordinated Universal Time (UTC) 格式。

##  <a name="utctolocal"></a>  CFileTime::UTCToLocal

呼叫這個方法來轉換以時間為基礎在 Coordinated Universal Time (UTC) 到本機檔案的時間。

```
CFileTime UTCToLocal() const throw();
```

### <a name="return-value"></a>傳回值

傳回`CFileTime`物件，其中包含本機檔案的時間格式的時間。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#42](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_4.cpp)]

##  <a name="week"></a>  CFileTime::Week

靜態資料成員，用來儲存構成一週的 100 奈秒間隔數。

```
static const ULONGLONG Week = Day* 7;
```

### <a name="example"></a>範例

範例，請參閱[CFileTime::Millisecond](#millisecond)。

## <a name="see-also"></a>另請參閱

[FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime)<br/>
[CFileTimeSpan 類別](../../atl-mfc-shared/reference/cfiletimespan-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)
