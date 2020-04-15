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
ms.openlocfilehash: bc9fe752898a5dfde2631352abd8c3cf5f8b378c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317898"
---
# <a name="cfiletime-class"></a>CFileTime 類別

此類提供用於管理與文件關聯的日期和時間值的方法。

## <a name="syntax"></a>語法

```
class CFileTime :  public FILETIME
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[檔案時間::檔案時間](#cfiletime)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[檔案時間::取得目前的時間](#getcurrenttime)|調用此靜態函數以檢索表示`CFileTime`當前系統日期和時間的物件。|
|[檔案時間:抓取時間](#gettime)|調用此方法以從`CFileTime`物件檢索時間。|
|[檔案時間::本機圖](#localtoutc)|呼叫此方法,根據協調通用時間 (UTC) 將本地檔案時間轉換為檔案時間。|
|[檔案時間::設定時間](#settime)|調用此方法以設置物件存儲的`CFileTime`日期和時間。|
|[檔案時間::UTC 到本地端](#utctolocal)|呼叫此方法,根據協調通用時間 (UTC) 將時間轉換為本地檔案時間。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[檔案時間::運算子 -](#operator_-)|此運算元用於對`CFileTime`或`CFileTimeSpan`物件執行減法。|
|[時間時間::操作員!*](#operator_neq)|此運算元比較兩`CFileTime`個物件為不等式。|
|[時間::操作員 |](#operator_add)|此運算子用在 `CFileTimeSpan` 物件上執行加法。|
|[時間::操作員 |](#operator_add_eq)|此運算子用在 `CFileTimeSpan` 物件上執行加法並指派結果給目前物件。|
|[檔案時間::運算子&lt;](#operator_lt)|此運算子比較兩個 `CFileTime` 物件來判斷何者較小。|
|[檔案時間::運算子&lt;=](#operator_lt_eq)|此運算子比較兩個 `CFileTime` 物件來判斷是否相等或何者較小。|
|[時間::操作員 |](#operator_eq)|分配運算符。|
|[檔案時間::運算子 -*](#operator_-_eq)|此運算元用於對`CFileTimeSpan`物件執行減法並將結果分配給當前物件。|
|[時間::操作員 |](#operator_eq_eq)|此運算子比較兩個 `CFileTime` 物件是否相等。|
|[檔案時間::運算子&gt;](#operator_gt)|此運算子比較兩個 `CFileTime` 物件來判斷何者較大。|
|[檔案時間::運算子&gt;=](#operator_gt_eq)|此運算子比較兩個 `CFileTime` 物件來判斷是否相等或何者較大。|

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[檔案時間::D](#day)|存儲構成一天的 100 納秒間隔數的靜態數據成員。|
|[時間時間:小時](#hour)|存儲構成一小時的 100 納秒間隔數的靜態數據成員。|
|[檔案時間::毫秒](#millisecond)|存儲構成一毫秒的 100 納秒間隔數的靜態數據成員。|
|[檔案時間:分鐘](#minute)|存儲構成一分鐘的 100 納秒間隔數的靜態數據成員。|
|[時間時間:第二](#second)|存儲構成一秒的 100 納秒間隔數的靜態數據成員。|
|[時間時間:周](#week)|存儲構成一周的 100 納秒間隔數的靜態數據成員。|

## <a name="remarks"></a>備註

此類提供用於管理與創建、訪問和修改文件關聯的日期和時間值的方法。 此類的方法和數據經常與`CFileTimeSpan`物件結合使用,對象處理相對的時間值。

日期和時間值存儲為 64 位值,表示自 1601 年 1 月 1 日以來的 100 納秒間隔數。 這是協調通用時間 (UTC) 格式。

提供以下靜態同流成員變數以簡化計算:

|成員變數|100奈秒間隔數|
|---------------------|-----------------------------------------|
|Millisecond|10,000|
|Second|毫秒\*1,000|
|Minute|第\*二 60|
|Hour|分鐘\*60|
|Day|小時\*24|
|週|第\*7 天|

**注意**並非所有檔案系統都可以記錄創建和最後訪問時間,並非所有檔案系統都能以相同的方式記錄它們。 例如,在 Windows NT FAT 檔案系統上,創建時間的解析度為 10 毫秒,寫入時間具有 2 秒的解析度,訪問時間的解析度為 1 天(訪問日期)。 在 NTFS 上,訪問時間具有 1 小時的解析度。 此外,FAT 記錄磁碟在本地時間的時間,但 NTFS 記錄在 UTC 中的磁碟上的時間。 有關詳細資訊,請參閱[檔案時間](/windows/win32/SysInfo/file-times)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`FILETIME`

`CFileTime`

## <a name="requirements"></a>需求

**標題:** atltime.h

## <a name="cfiletimecfiletime"></a><a name="cfiletime"></a>檔案時間::檔案時間

建構函式。

```
CFileTime() throw();
CFileTime(const FILETIME& ft) throw();
CFileTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>參數

*英呎*<br/>
[時間時間](/windows/win32/api/minwinbase/ns-minwinbase-filetime)結構。

*nTime*<br/>
以 64 位值表示的日期和時間。

### <a name="remarks"></a>備註

可以使用`CFileTime``FILETIME`結構中的現有日期和時間創建物件,或表示為 64 位值(以本地或協調通用時間 (UTC) 時間格式)。 默認構造函數將時間設置為 0。

## <a name="cfiletimeday"></a><a name="day"></a>檔案時間::D

存儲構成一天的 100 納秒間隔數的靜態數據成員。

```
static const ULONGLONG Day = Hour* 24;
```

### <a name="example"></a>範例

請參考[CFileTime::毫秒的範例](#millisecond)。

## <a name="cfiletimegetcurrenttime"></a><a name="getcurrenttime"></a>檔案時間::取得目前的時間

調用此靜態函數以檢索表示`CFileTime`當前系統日期和時間的物件。

```
static CFileTime GetCurrentTime() throw();
```

### <a name="return-value"></a>傳回值

以協調通用時間 (UTC) 格式傳回目前系統日期和時間。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#41](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_1.cpp)]

## <a name="cfiletimegettime"></a><a name="gettime"></a>檔案時間:抓取時間

調用此方法以從`CFileTime`物件檢索時間。

```
ULONGLONG GetTime() const throw();
```

### <a name="return-value"></a>傳回值

將日期和時間作為 64 位元數位傳回,該數位可能採用本地或協調通用時間 (UTC) 格式。

## <a name="cfiletimehour"></a><a name="hour"></a>時間時間:小時

存儲構成一小時的 100 納秒間隔數的靜態數據成員。

```
static const ULONGLONG Hour = Minute* 60;
```

### <a name="example"></a>範例

請參考[CFileTime::毫秒的範例](#millisecond)。

## <a name="cfiletimelocaltoutc"></a><a name="localtoutc"></a>檔案時間::本機圖

呼叫此方法,根據協調通用時間 (UTC) 將本地檔案時間轉換為檔案時間。

```
CFileTime LocalToUTC() const throw();
```

### <a name="return-value"></a>傳回值

返回包含`CFileTime`時間(UTC 格式)的物件。

### <a name="example"></a>範例

請參考[CFileTime 範例:UTCTolocal](#utctolocal)。

## <a name="cfiletimemillisecond"></a><a name="millisecond"></a>檔案時間::毫秒

存儲構成一毫秒的 100 納秒間隔數的靜態數據成員。

```
static const ULONGLONG Millisecond = 10000;
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#44](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_2.cpp)]

## <a name="cfiletimeminute"></a><a name="minute"></a>檔案時間:分鐘

存儲構成一分鐘的 100 納秒間隔數的靜態數據成員。

```
static const ULONGLONG Minute = Second* 60;
```

### <a name="example"></a>範例

請參考[CFileTime::毫秒的範例](#millisecond)。

## <a name="cfiletimeoperator--"></a><a name="operator_-"></a>檔案時間::運算子 -

此運算元用於對`CFileTime`或`CFileTimeSpan`物件執行減法。

```
CFileTime operator-(CFileTimeSpan span) const throw();
CFileTimeSpan operator-(CFileTime ft) const throw();
```

### <a name="parameters"></a>參數

*跨度*<br/>
`CFileTimeSpan` 物件。

*英呎*<br/>
`CFileTime` 物件。

### <a name="return-value"></a>傳回值

返回表示`CFileTime`兩`CFileTimeSpan`個 物件之間的時差結果的物件或物件。

## <a name="cfiletimeoperator-"></a><a name="operator_neq"></a>時間時間::操作員!*

此運算元比較兩`CFileTime`個物件為不等式。

```
bool operator!=(CFileTime ft) const throw();
```

### <a name="parameters"></a>參數

*英呎*<br/>
要比較的 `CFileTime` 物件。

### <a name="return-value"></a>傳回值

如果要比較的項不等於物件,`CFileTime`則返回 TRUE,否則為 FALSE。

## <a name="cfiletimeoperator-"></a><a name="operator_add"></a>時間::操作員 |

此運算子用在 `CFileTimeSpan` 物件上執行加法。

```
CFileTime operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*跨度*<br/>
`CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

返回表示`CFileTime`原始時間的結果加上相對時間的物件。

## <a name="cfiletimeoperator-"></a><a name="operator_add_eq"></a>時間::操作員 |

此運算子用在 `CFileTimeSpan` 物件上執行加法並指派結果給目前物件。

```
CFileTime& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>參數

*跨度*<br/>
`CFileTimeSpan` 物件。

### <a name="return-value"></a>傳回值

返回更新`CFileTime`的物件,表示原始時間的結果加上相對時間。

## <a name="cfiletimeoperator-lt"></a><a name="operator_lt"></a>檔案時間::運算子&lt;

此運算子比較兩個 `CFileTime` 物件來判斷何者較小。

```
bool operator<(CFileTime ft) const throw();
```

### <a name="parameters"></a>參數

*英呎*<br/>
要比較的 `CFileTime` 物件。

### <a name="return-value"></a>傳回值

如果第一個物件小於第二個物件(時間早期),則返回 TRUE,否則為 FALSE。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#43](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_3.cpp)]

## <a name="cfiletimeoperator-lt"></a><a name="operator_lt_eq"></a>檔案時間::運算子&lt;=

此運算子比較兩個 `CFileTime` 物件來判斷是否相等或何者較小。

```
bool operator<=(CFileTime ft) const throw();
```

### <a name="parameters"></a>參數

*英呎*<br/>
要比較的 `CFileTime` 物件。

### <a name="return-value"></a>傳回值

如果第一個物件小於(時間早期)或等於第二個對象,否則返回 TRUE,否則為 FALSE。

## <a name="cfiletimeoperator-"></a><a name="operator_eq"></a>時間::操作員 |

分配運算符。

```
CFileTime& operator=(const FILETIME& ft) throw();
```

### <a name="parameters"></a>參數

*英呎*<br/>
包含`CFileTime`新時間和日期的物件。

### <a name="return-value"></a>傳回值

返回更新`CFileTime`的物件。

## <a name="cfiletimeoperator--"></a><a name="operator_-_eq"></a>檔案時間::運算子 -*

此運算元用於對`CFileTimeSpan`物件執行減法並將結果分配給當前物件。

```
CFileTime& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>參數

*跨度*<br/>
包含`CFileTimeSpan`要減去的相對時間的物件。

### <a name="return-value"></a>傳回值

返回更新`CFileTime`的物件。

## <a name="cfiletimeoperator-"></a><a name="operator_eq_eq"></a>時間::操作員 |

此運算子比較兩個 `CFileTime` 物件是否相等。

```
bool operator==(CFileTime ft) const throw();
```

### <a name="parameters"></a>參數

*英呎*<br/>
要比較的 `CFileTime` 物件。

### <a name="return-value"></a>傳回值

如果物件相等,則返回 TRUE,否則為 FALSE。

## <a name="cfiletimeoperator-gt"></a><a name="operator_gt"></a>檔案時間::運算子&gt;

此運算子比較兩個 `CFileTime` 物件來判斷何者較大。

```
bool operator>(CFileTime ft) const throw();
```

### <a name="parameters"></a>參數

*英呎*<br/>
要比較的 `CFileTime` 物件。

### <a name="return-value"></a>傳回值

如果第一個物件大於(時間較晚)大於第二個物件,則返回 TRUE,否則為 FALSE。

## <a name="cfiletimeoperator-gt"></a><a name="operator_gt_eq"></a>檔案時間::運算子&gt;=

此運算子比較兩個 `CFileTime` 物件來判斷是否相等或何者較大。

```
bool operator>=(CFileTime ft) const throw();
```

### <a name="parameters"></a>參數

*英呎*<br/>
要比較的 `CFileTime` 物件。

### <a name="return-value"></a>傳回值

如果第一個物件大於(時間後期)或等於第二個對象,否則返回 TRUE,否則為 FALSE。

## <a name="cfiletimesecond"></a><a name="second"></a>時間時間:第二

存儲構成一天的 100 納秒間隔數的靜態數據成員。

```
static const ULONGLONG Second = Millisecond* 1000;
```

### <a name="example"></a>範例

請參考[CFileTime::毫秒的範例](#millisecond)。

## <a name="cfiletimesettime"></a><a name="settime"></a>檔案時間::設定時間

調用此方法以設置物件存儲的`CFileTime`日期和時間。

```
void SetTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>參數

*nTime*<br/>
以本地或協調通用時間 (UTC) 格式表示日期和時間的 64 位值。

## <a name="cfiletimeutctolocal"></a><a name="utctolocal"></a>檔案時間::UTC 到本地端

呼叫此方法,根據協調通用時間 (UTC) 將時間轉換為本地檔案時間。

```
CFileTime UTCToLocal() const throw();
```

### <a name="return-value"></a>傳回值

返回以`CFileTime`本地檔案時間格式包含時間的物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#42](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_4.cpp)]

## <a name="cfiletimeweek"></a><a name="week"></a>時間時間:周

存儲構成一周的 100 納秒間隔數的靜態數據成員。

```
static const ULONGLONG Week = Day* 7;
```

### <a name="example"></a>範例

請參考[CFileTime::毫秒的範例](#millisecond)。

## <a name="see-also"></a>另請參閱

[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)<br/>
[CFileTimeSpan 類別](../../atl-mfc-shared/reference/cfiletimespan-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)
