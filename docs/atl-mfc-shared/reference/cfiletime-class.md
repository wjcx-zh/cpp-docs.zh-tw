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
ms.openlocfilehash: b24d1e4d3e670a820c41735617b7db6780ff137c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491488"
---
# <a name="cfiletime-class"></a>CFileTime 類別

這個類別提供管理與檔案相關聯之日期和時間值的方法。

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
|[CFileTime::GetCurrentTime](#getcurrenttime)|呼叫此靜態函式以`CFileTime`抓取代表目前系統日期和時間的物件。|
|[CFileTime::GetTime](#gettime)|呼叫這個方法, 以從`CFileTime`物件取出時間。|
|[CFileTime::LocalToUTC](#localtoutc)|呼叫這個方法, 以根據國際標準時間 (UTC) 將本機檔案時間轉換成檔案時間。|
|[CFileTime::SetTime](#settime)|呼叫這個方法, 以設定`CFileTime`物件所儲存的日期和時間。|
|[CFileTime::UTCToLocal](#utctolocal)|呼叫這個方法, 以根據國際標準時間 (UTC) 將時間轉換為本機檔案時間。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CFileTime:: operator-](#operator_-)|這個運算子是用來在`CFileTime`或`CFileTimeSpan`物件上執行減法。|
|[CFileTime:: operator! =](#operator_neq)|這個運算子會比較`CFileTime`兩個物件是否不相等。|
|[CFileTime:: operator +](#operator_add)|此運算子用在 `CFileTimeSpan` 物件上執行加法。|
|[CFileTime:: operator + =](#operator_add_eq)|此運算子用在 `CFileTimeSpan` 物件上執行加法並指派結果給目前物件。|
|[CFileTime:: operator&lt;](#operator_lt)|此運算子比較兩個 `CFileTime` 物件來判斷何者較小。|
|[CFileTime:: operator&lt;=](#operator_lt_eq)|此運算子比較兩個 `CFileTime` 物件來判斷是否相等或何者較小。|
|[CFileTime:: operator =](#operator_eq)|指派運算子。|
|[CFileTime::operator -=](#operator_-_eq)|這個運算子是用來在`CFileTimeSpan`物件上執行減法運算, 並將結果指派給目前的物件。|
|[CFileTime:: operator = =](#operator_eq_eq)|此運算子比較兩個 `CFileTime` 物件是否相等。|
|[CFileTime:: operator&gt;](#operator_gt)|此運算子比較兩個 `CFileTime` 物件來判斷何者較大。|
|[CFileTime:: operator&gt;=](#operator_gt_eq)|此運算子比較兩個 `CFileTime` 物件來判斷是否相等或何者較大。|

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[CFileTime::Day](#day)|靜態資料成員, 用來儲存構成一天的100毫微秒間隔數。|
|[CFileTime::Hour](#hour)|靜態資料成員, 用來儲存構成一小時的100毫微秒間隔數。|
|[CFileTime:: 毫秒](#millisecond)|靜態資料成員, 用來儲存構成一毫秒的100毫微秒間隔數。|
|[CFileTime::Minute](#minute)|靜態資料成員, 用來儲存構成一分鐘的100毫微秒間隔數。|
|[CFileTime::Second](#second)|靜態資料成員, 用來儲存構成一秒的100毫微秒間隔數。|
|[CFileTime::Week](#week)|靜態資料成員, 用來儲存組成一周的100毫微秒間隔數。|

## <a name="remarks"></a>備註

這個類別會提供方法來管理與建立、存取和修改檔案相關聯的日期和時間值。 這個類別的方法和資料經常會與`CFileTimeSpan`處理相對時間值的物件搭配使用。

日期和時間值會儲存為64位值, 代表自1601年1月1日起的100毫微秒間隔數目。 這是國際標準時間 (UTC) 格式。

提供下列靜態 const 成員變數來簡化計算:

|成員變數|100-秒數間隔|
|---------------------|-----------------------------------------|
|Millisecond|10,000|
|第二個|毫秒\* 1000|
|Minute|第\*二個60|
|Hour|分鐘\* 60|
|Day|小時\* 24|
|那個|第\* 7 天|

**注意**並非所有檔案系統都可以記錄建立和上次存取時間, 而且並非所有檔案系統都會以相同的方式記錄它們。 例如, 在 Windows NT FAT 檔案系統上, 「建立時間」的解析度為10毫秒、「寫入時間」的解析度為2秒, 而「存取時間」則為1天的解決方式 (存取日期)。 在 NTFS 上, 存取時間的解析度為1小時。 此外, FAT 會在磁片上以當地時間記錄時間, 但 NTFS 會以 UTC 記錄磁片的時間。 如需詳細資訊, 請參閱檔案[時間](/windows/win32/SysInfo/file-times)。

## <a name="inheritance-hierarchy"></a>繼承階層

`FILETIME`

`CFileTime`

## <a name="requirements"></a>需求

**標頭:** atltime。h

##  <a name="cfiletime"></a>CFileTime::CFileTime

建構函式。

```
CFileTime() throw();
CFileTime(const FILETIME& ft) throw();
CFileTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>參數

*ft*<br/>
[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)結構。

*nTime*<br/>
以64位值表示的日期和時間。

### <a name="remarks"></a>備註

物件可以使用`FILETIME`結構中現有的日期和時間來建立, 或以64位值表示 (以當地或國際標準時間 (UTC) 時間格式表示)。 `CFileTime` 預設的函式會將時間設定為0。

##  <a name="day"></a>CFileTime::D ay

靜態資料成員, 用來儲存構成一天的100毫微秒間隔數。

```
static const ULONGLONG Day = Hour* 24;
```

### <a name="example"></a>範例

請參閱[CFileTime:: 毫秒](#millisecond)的範例。

##  <a name="getcurrenttime"></a>CFileTime::GetCurrentTime

呼叫此靜態函式以`CFileTime`抓取代表目前系統日期和時間的物件。

```
static CFileTime GetCurrentTime() throw();
```

### <a name="return-value"></a>傳回值

傳回目前的系統日期和時間, 格式為國際標準時間 (UTC)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#41](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_1.cpp)]

##  <a name="gettime"></a>CFileTime:: GetTime

呼叫這個方法, 以從`CFileTime`物件取出時間。

```
ULONGLONG GetTime() const throw();
```

### <a name="return-value"></a>傳回值

以64位數位傳回日期和時間, 這可能是本地或國際標準時間 (UTC) 格式。

##  <a name="hour"></a>CFileTime:: Hour

靜態資料成員, 用來儲存構成一小時的100毫微秒間隔數。

```
static const ULONGLONG Hour = Minute* 60;
```

### <a name="example"></a>範例

請參閱[CFileTime:: 毫秒](#millisecond)的範例。

##  <a name="localtoutc"></a>CFileTime::LocalToUTC

呼叫這個方法, 以根據國際標準時間 (UTC) 將本機檔案時間轉換成檔案時間。

```
CFileTime LocalToUTC() const throw();
```

### <a name="return-value"></a>傳回值

`CFileTime`傳回物件, 其中包含 UTC 格式的時間。

### <a name="example"></a>範例

請參閱[CFileTime:: UTCToLocal](#utctolocal)的範例。

##  <a name="millisecond"></a>CFileTime:: 毫秒

靜態資料成員, 用來儲存構成一毫秒的100毫微秒間隔數。

```
static const ULONGLONG Millisecond = 10000;
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#44](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_2.cpp)]

##  <a name="minute"></a>CFileTime:: Minute

靜態資料成員, 用來儲存構成一分鐘的100毫微秒間隔數。

```
static const ULONGLONG Minute = Second* 60;
```

### <a name="example"></a>範例

請參閱[CFileTime:: 毫秒](#millisecond)的範例。

##  <a name="operator_-"></a>CFileTime:: operator-

這個運算子是用來在`CFileTime`或`CFileTimeSpan`物件上執行減法。

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

`CFileTime`傳回物件`CFileTimeSpan`或物件, 代表兩個物件之間的時間差結果。

##  <a name="operator_neq"></a>CFileTime:: operator! =

這個運算子會比較`CFileTime`兩個物件是否不相等。

```
bool operator!=(CFileTime ft) const throw();
```

### <a name="parameters"></a>參數

*ft*<br/>
要比較的 `CFileTime` 物件。

### <a name="return-value"></a>傳回值

如果要比較的專案不等於`CFileTime`物件, 則傳回 TRUE, 否則傳回 FALSE。

##  <a name="operator_add"></a>CFileTime:: operator +

此運算子用在 `CFileTimeSpan` 物件上執行加法。

```
CFileTime operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*span*<br/>
          `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

`CFileTime`傳回物件, 代表原始時間加上相對時間的結果。

##  <a name="operator_add_eq"></a>CFileTime:: operator + =

此運算子用在 `CFileTimeSpan` 物件上執行加法並指派結果給目前物件。

```
CFileTime& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>參數

*span*<br/>
          `CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

傳回已更新`CFileTime`的物件, 代表原始時間加上相對時間的結果。

##  <a name="operator_lt"></a>CFileTime:: operator&lt;

此運算子比較兩個 `CFileTime` 物件來判斷何者較小。

```
bool operator<(CFileTime ft) const throw();
```

### <a name="parameters"></a>參數

*ft*<br/>
要比較的 `CFileTime` 物件。

### <a name="return-value"></a>傳回值

如果第一個物件小於第二個, 則傳回 TRUE, 否則傳回 FALSE。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#43](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_3.cpp)]

##  <a name="operator_lt_eq"></a>CFileTime:: operator&lt;=

此運算子比較兩個 `CFileTime` 物件來判斷是否相等或何者較小。

```
bool operator<=(CFileTime ft) const throw();
```

### <a name="parameters"></a>參數

*ft*<br/>
要比較的 `CFileTime` 物件。

### <a name="return-value"></a>傳回值

如果第一個物件小於 (較早的時間) 或等於第二個物件, 則傳回 TRUE, 否則傳回 FALSE。

##  <a name="operator_eq"></a>CFileTime:: operator =

指派運算子。

```
CFileTime& operator=(const FILETIME& ft) throw();
```

### <a name="parameters"></a>參數

*ft*<br/>
`CFileTime`物件, 其中包含新的時間和日期。

### <a name="return-value"></a>傳回值

傳回已更新`CFileTime`的物件。

##  <a name="operator_-_eq"></a>CFileTime:: operator-=

這個運算子是用來在`CFileTimeSpan`物件上執行減法運算, 並將結果指派給目前的物件。

```
CFileTime& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>參數

*span*<br/>
`CFileTimeSpan`物件, 包含要減去的相對時間。

### <a name="return-value"></a>傳回值

傳回已更新`CFileTime`的物件。

##  <a name="operator_eq_eq"></a>CFileTime:: operator = =

此運算子比較兩個 `CFileTime` 物件是否相等。

```
bool operator==(CFileTime ft) const throw();
```

### <a name="parameters"></a>參數

*ft*<br/>
要`CFileTime`比較的物件。

### <a name="return-value"></a>傳回值

如果物件相等, 則傳回 TRUE, 否則傳回 FALSE。

##  <a name="operator_gt"></a>CFileTime:: operator&gt;

此運算子比較兩個 `CFileTime` 物件來判斷何者較大。

```
bool operator>(CFileTime ft) const throw();
```

### <a name="parameters"></a>參數

*ft*<br/>
要比較的 `CFileTime` 物件。

### <a name="return-value"></a>傳回值

如果第一個物件大於 (晚于時間), 則傳回 TRUE, 否則傳回 FALSE。

##  <a name="operator_gt_eq"></a>CFileTime:: operator&gt;=

此運算子比較兩個 `CFileTime` 物件來判斷是否相等或何者較大。

```
bool operator>=(CFileTime ft) const throw();
```

### <a name="parameters"></a>參數

*ft*<br/>
要比較的 `CFileTime` 物件。

### <a name="return-value"></a>傳回值

如果第一個物件大於 (晚于時間) 或等於第二個物件, 則傳回 TRUE, 否則傳回 FALSE。

##  <a name="second"></a>CFileTime:: Second

靜態資料成員, 用來儲存構成一天的100毫微秒間隔數。

```
static const ULONGLONG Second = Millisecond* 1000;
```

### <a name="example"></a>範例

請參閱[CFileTime:: 毫秒](#millisecond)的範例。

##  <a name="settime"></a>CFileTime:: SetTime

呼叫這個方法, 以設定`CFileTime`物件所儲存的日期和時間。

```
void SetTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>參數

*nTime*<br/>
代表日期和時間的64位值, 格式為當地或國際標準時間 (UTC)。

##  <a name="utctolocal"></a>CFileTime::UTCToLocal

呼叫這個方法, 以根據國際標準時間 (UTC) 將時間轉換為本機檔案時間。

```
CFileTime UTCToLocal() const throw();
```

### <a name="return-value"></a>傳回值

`CFileTime`傳回物件, 其中包含本機檔案時間格式的時間。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#42](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_4.cpp)]

##  <a name="week"></a>CFileTime:: Week

靜態資料成員, 用來儲存組成一周的100毫微秒間隔數。

```
static const ULONGLONG Week = Day* 7;
```

### <a name="example"></a>範例

請參閱[CFileTime:: 毫秒](#millisecond)的範例。

## <a name="see-also"></a>另請參閱

[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)<br/>
[CFileTimeSpan 類別](../../atl-mfc-shared/reference/cfiletimespan-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)
