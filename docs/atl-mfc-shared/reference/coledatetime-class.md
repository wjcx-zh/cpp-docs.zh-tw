---
title: COleDateTime 類別
ms.date: 03/27/2019
f1_keywords:
- COleDateTime
- ATLCOMTIME/ATL::COleDateTime
- ATLCOMTIME/ATL::COleDateTime::COleDateTime
- ATLCOMTIME/ATL::COleDateTime::Format
- ATLCOMTIME/ATL::COleDateTime::GetAsDBTIMESTAMP
- ATLCOMTIME/ATL::COleDateTime::GetAsSystemTime
- ATLCOMTIME/ATL::COleDateTime::GetAsUDATE
- ATLCOMTIME/ATL::COleDateTime::GetCurrentTime
- ATLCOMTIME/ATL::COleDateTime::GetDay
- ATLCOMTIME/ATL::COleDateTime::GetDayOfWeek
- ATLCOMTIME/ATL::COleDateTime::GetDayOfYear
- ATLCOMTIME/ATL::COleDateTime::GetHour
- ATLCOMTIME/ATL::COleDateTime::GetMinute
- ATLCOMTIME/ATL::COleDateTime::GetMonth
- ATLCOMTIME/ATL::COleDateTime::GetSecond
- ATLCOMTIME/ATL::COleDateTime::GetStatus
- ATLCOMTIME/ATL::COleDateTime::GetYear
- ATLCOMTIME/ATL::COleDateTime::ParseDateTime
- ATLCOMTIME/ATL::COleDateTime::SetDate
- ATLCOMTIME/ATL::COleDateTime::SetDateTime
- ATLCOMTIME/ATL::COleDateTime::SetStatus
- ATLCOMTIME/ATL::COleDateTime::SetTime
- ATLCOMTIME/ATL::COleDateTime::m_dt
- ATLCOMTIME/ATL::COleDateTime::m_status
helpviewer_keywords:
- shared classes, COleDateTime
- time-only values
- Date data type, MFC encapsulation of
- COleDateTime class
- dates, handling in MFC
- time, handling in MFC
ms.assetid: e718f294-16ec-4649-88b6-a4dbae5178fb
ms.openlocfilehash: 610cbec6cb65d4e9616c5e0e0d64e729f39febcc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317755"
---
# <a name="coledatetime-class"></a>COleDateTime 類別

封裝 OLE`DATE`自動化中使用的數據類型。

## <a name="syntax"></a>語法

```
class COleDateTime
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleDate時間:COleDatetime](#coledatetime)|建構 `COleDateTime` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleDateTime::格式](#format)|生成`COleDateTime`物件的格式化字串表示形式。|
|[COleDatetime:取得 ASDBTIMESTAMP](#getasdbtimestamp)|調用此方法以獲取`COleDateTime`對象`DBTIMESTAMP`中作為數據結構的時間。|
|[COleDatetime:取得系統時間](#getassystemtime)|呼叫此方法以獲取`COleDateTime`物件中作為[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)資料結構的時間。|
|[COleDate時間:取得日期](#getasudate)|調用此方法以獲取 數據結構`COleDateTime``UDATE`中的時間。|
|[COleDateTime:取得目前時間](#getcurrenttime)|創建`COleDateTime`表示當前時間的物件(靜態成員函數)。|
|[COleDateTime時間:取得日](#getday)|返回此`COleDateTime`物件表示的當天 (1 - 31)。|
|[COleDatetime:取得周](#getdayofweek)|返回此`COleDateTime`物件表示的一周中的一天(星期日 = 1)。|
|[COleDatetime:取得一年](#getdayofyear)|返回此`COleDateTime`物件表示的一年中的一天(1 月 1 日 = 1)。|
|[COleDatetime:取得小時](#gethour)|返回此`COleDateTime`物件表示的小時 (0 - 23)。|
|[COleDatetime:取得分鐘](#getminute)|返回此`COleDateTime`物件表示的分鐘 (0 - 59)。|
|[COleDateTime時間:取得月](#getmonth)|返回此`COleDateTime`物件表示的月份 (1 - 12)。|
|[COleDateTime時間:取得第二](#getsecond)|返回此`COleDateTime`物件表示的第二個物件 (0 - 59)。|
|[COleDateTime時間:取得狀態](#getstatus)|獲取此`COleDateTime`物件的狀態(有效性)。|
|[COleDate時間:取得年份](#getyear)|返回此`COleDateTime`物件表示的年份。|
|[COleDateTime::P時間](#parsedatetime)|從字串讀取日期/時間值並設定的值`COleDateTime`。|
|[COleDate 時間::設定日期](#setdate)|將此`COleDateTime`物件的值設置為指定的僅日期值。|
|[COleDate時間::設定日期時間](#setdatetime)|將此`COleDateTime`物件的值設置為指定的日期/時間值。|
|[COleDatetime::設定狀態](#setstatus)|設置此`COleDateTime`物件的狀態(有效性)。|
|[COleDateTime::設定時間](#settime)|將此`COleDateTime`物件的值設置為指定的僅時間值。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[COleDateTime::運算符 =,COleDateTime::運算符<等。](#coledatetime_relational_operators)|比較兩`COleDateTime`個值。|
|[COleDateTime::運算符 +,COleDateTime::運算符 -](#operator_add_-)|添加和減去`COleDateTime`值。|
|[COleDateTime::運算符 =,COleDateTime::運算符 -*](#operator_add_eq_-_eq)|從該`COleDateTime`物件`COleDateTime`中 添加和減去值。|
|[COleDateTime::運算符 |](#operator_eq)|複製值`COleDateTime`。|
|[COleDateTime::操作員日期,COleDate時間::操作員日期*](#operator_date)|轉換`COleDateTime`成或值轉換`DATE`為`DATE*`或 。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COleDate時間::m_dt](#m_dt)|包含此`COleDateTime`物件的`DATE`基礎 。|
|[COleDate時間::m_status](#m_status)|包含此`COleDateTime`物件的狀態。|

## <a name="remarks"></a>備註

`COleDateTime`沒有基類。

它是 OLE 自動化[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)資料類型的可能類型之一。 值`COleDateTime`表示絕對日期和時間值。

該`DATE`類型作為浮點值實現。 從 1899 年 12 月 30 日午夜開始測量天數。 下表顯示了一些日期及其關聯的值:

|Date|值|
|----------|-----------|
|1899年12月29日,午夜|-1.0|
|1899年12月29日,上午6時|-1.25|
|1899年12月30日 午夜|0.0|
|1899年12月31日 午夜|1.0|
|1900 年 1 月 1 日,上午 6 點|2.25|

> [!CAUTION]
> 在上表中,雖然 1899 年 12 月 30 日午夜前日值變為負值,但時間值不會。 例如,無論表示該日的整數是正數(1899 年 12 月 30 日之後)還是負值(1899 年 12 月 30 日之前),6:00 AM 始終由分數值 0.25 表示。 這意味著,簡單的浮點比較會錯誤地將`COleDateTime`1899 年 12 月 29 日早上 6:00 的表示排序為**晚**於當天 7:00 表示的浮點。

該`COleDateTime`課程處理日期從 1 月 1 日到 9999 年 12 月 31 日。 類`COleDateTime`使用公曆;它不支援朱利安日期。 `COleDateTime`忽略夏令時。 (請參閱[日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md).)

> [!NOTE]
> 您可以使用該`%y`格式僅檢索從 1900 年開始的日期的兩位數年份。 如果在 1900 年之前的`%y`日期使用 該格式,則代碼將生成 ASSERT 失敗。

此類型還用於表示僅日期或僅時間值。 按照慣例,日期 0(1899 年 12 月 30 日)用於僅時間值,時間 00:00(午夜)用於僅日期值。

`COleDateTime`如果使用少於 100 的日期創建物件,則接受該日期,但隨後`GetYear``GetMonth`調`GetMinute``GetSecond``GetDay``GetHour`用 、、、、、、、、、 失敗並返回 -1。 以前,您可以使用兩位數日期,但在 MFC 4.2 及更高版本中,日期必須為 100 或更大。

為避免問題,請指定一個四位數的日期。 例如：

[!code-cpp[NVC_ATLMFC_Utilities#1](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_1.cpp)]

`COleDateTime`值的基本算術運算使用配套類別[COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)。 `COleDateTimeSpan`值定義時間間隔。 這些類之間的關係類似於 CTime 和[CTimeSpan](../../atl-mfc-shared/reference/ctime-class.md)[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)之間的關係。

有關`COleDateTime``COleDateTimeSpan`和類的詳細資訊,請參閱文章[「日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)」。。

## <a name="requirements"></a>需求

**標題:** ATLComTime.h

## <a name="coledatetime-relational-operators"></a><a name="coledatetime_relational_operators"></a>COleDateTime 關係運算子

比較運算符。

```
bool operator==(const COleDateTime& date) const throw();
bool operator!=(const COleDateTime& date) const throw();
bool operator<(const COleDateTime& date) const throw();
bool operator>(const COleDateTime& date) const throw();
bool operator<=(const COleDateTime& date) const throw();
bool operator>=(const COleDateTime& date) const throw();
```

### <a name="parameters"></a>參數

*日期*<br/>
要比較的 `COleDateTime` 物件。

### <a name="remarks"></a>備註

> [!NOTE]
> 如果兩個操作數中的任何一個無效,則會發生 ATLASSERT。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#13](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_2.cpp)]

### <a name="example"></a>範例

如果物件**>=** 設定**\<** 為**>** null,**<**`COleDateTime`則運算子 、、和將斷言。

[!code-cpp[NVC_ATLMFC_Utilities#170](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_3.cpp)]

## <a name="coledatetimecoledatetime"></a><a name="coledatetime"></a>COleDate時間:COleDatetime

建構 `COleDateTime` 物件。

```
COleDateTime() throw();
COleDateTime(const VARIANT& varSrc) throw();
COleDateTime(DATE dtSrc) throw();
COleDateTime(time_t timeSrc) throw();
COleDateTime(__time64_t timeSrc) throw();
COleDateTime(const SYSTEMTIME& systimeSrc) throw();
COleDateTime(const FILETIME& filetimeSrc) throw();

COleDateTime(int nYear,
    int nMonth,
    int nDay,
    int nHour,
    int nMin,
    int nSec) throw();

COleDateTime(WORD wDosDate,
    WORD wDosTime) throw();
COleDateTime(const DBTIMESTAMP& timeStamp) throw();
```

### <a name="parameters"></a>參數

*日期Src*<br/>
要複製到`COleDateTime`新`COleDateTime`物件的現有物件。

*varSrc*<br/>
要轉換為`VARIANT`日期/時間值(VT_DATE)並複製到新`COleVariant``COleDateTime`物件的現有數據結構(可能是物件)。

*德茨爾克*<br/>
要複製到新`COleDateTime`物件的`DATE`日期 /時間 ( ) 值。

*時間Src*<br/>
要`time_t`轉換為`__time64_t`日期/時間值並複製到新`COleDateTime`物件中的或值。

*系統時間Src*<br/>
要`SYSTEMTIME`轉換為日期/時間值並複製到新`COleDateTime`物件的結構。

*檔案時間Src*<br/>
要`FILETIME`轉換為日期/時間值並複製到新`COleDateTime`物件的結構。 A`FILETIME`使用通用協調時間 (UTC),因此,如果在結構中傳遞本地時間,則結果將不正確。 關於詳細資訊,請參閱 Windows SDK[中的檔案時間](/windows/win32/SysInfo/file-times)。

*nYear*, *nMonth*, *nDay*, *nHour*, *nMin*, *nSec*<br/>
指示要複製到新`COleDateTime`物件的日期和時間值。

*wDosDate*, *wDosTime*<br/>
要轉換為日期/時間值並複製到新`COleDateTime`物件的 MS-DOS 日期和時間值。

*時間 戳*<br/>
對包含當前本地時間的[DBTimeStamp](/dotnet/api/system.data.oledb.oledbtype)結構的引用。

### <a name="remarks"></a>備註

所有這些構造函數都創建初始化`COleDateTime`為指定值的新物件。 下表顯示每個日期和時間元件的有效範圍:

|日期/時間元件|有效範圍|
|--------------------------|-----------------|
|year|100 - 9999|
|月|0 - 12|
|day|0 - 31|
|hour|0 - 23|
|minute|0 - 59|
|second|0 - 59|

請注意,日元件的實際上限因月份和年份元件而異。 有關詳細資訊,請參閱`SetDate``SetDateTime`或成員函數。

以下是每個建構函數的簡要說明:

- `COleDateTime(`**)** 構造`COleDateTime`初始 化為 0 的物件(1899 年 12 月 30 日午夜)。

- `COleDateTime(``dateSrc` **)** 從`COleDateTime``COleDateTime`現有 對象構造物件。

- `COleDateTime(`*varSrc* **)**`COleDateTime`建構 一個物件。 嘗試將`VARIANT`結構或[COleVariant](../../mfc/reference/colevariant-class.md)物件轉換為日期`VT_DATE`/ 時間 ( ) 值。 如果此轉換成功,則轉換後的值將複製到`COleDateTime`新 物件中。 如果不是,`COleDateTime`則物件的值設置為 0(1899 年 12 月 30 日午夜),其狀態無效。

- `COleDateTime(``dtSrc` **)**`DATE`從`COleDateTime`值 構造物件。

- `COleDateTime(``timeSrc` **)**`time_t`從`COleDateTime`值 構造物件。

- `COleDateTime(`*systimeSrc* **)**)`COleDateTime``SYSTEMTIME`從 值建構物件。

- `COleDateTime(``filetimeSrc` **)**`FILETIME`從`COleDateTime`值 構造物件。 . A`FILETIME`使用通用協調時間 (UTC),因此,如果在結構中傳遞本地時間,則結果將不正確。 關於詳細資訊,請參閱 Windows SDK 中的[檔案時間](/windows/win32/SysInfo/file-times)。

- `COleDateTime(``nYear``nMonth`、、、、、、、、`nDay``nHour`從指定`COleDateTime`的數值建構物件。`nMin``nSec`**)**

- `COleDateTime(`) 從指定的 MS-DOS 日期和時間`COleDateTime`值建構 物件。 **)** `wDosDate` `wDosTime`

有關`time_t`數據類型的詳細資訊,請參閱*運行時庫參考*中[的時間](../../c-runtime-library/reference/time-time32-time64.md)函數。

有關詳細資訊,請參閱 Windows SDK 中的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)和[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)結構。

有關`COleDateTime`值邊界的詳細資訊,請參閱文章[「日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)」。。

> [!NOTE]
> 僅當包含 OLEDB.h 時`DBTIMESTAMP`,使用 參數的構造函數才可用。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#2](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_4.cpp)]

## <a name="coledatetimeformat"></a><a name="format"></a>COleDateTime::格式

創建日期/時間值的格式化表示形式。

```
CString Format(DWORD dwFlags = 0,  LCID lcid = LANG_USER_DEFAULT) const;
CString Format(LPCTSTR lpszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
指示以下區域設定標誌之一:

- LOCALE_NOUSEROVERRIDE 使用系統默認區域設置,而不是自定義用戶設置。

- VAR_TIMEVALUEONLY在分析過程中忽略日期部分。

- VAR_DATEVALUEONLY在分析過程中忽略時間部分。

*lcid*<br/>
指示用於轉換區域設置 ID。 有關語言識別碼的詳細資訊,請參閱[語言識別碼](/windows/win32/Intl/language-identifiers)。

*lpsz格式*<br/>
類似於格式字串的`printf`格式字串。 每個格式代碼(前面有百分比`%`( ) 符號`COleDateTime`,由相應的 元件替換。 格式字串中的其他字元將複製到傳回的字串。 有關詳細資訊,請參閱執行時函數[strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)。 格式化`Format`代碼的值與含義是:

- `%H`當天的小時數

- `%M`目前的小時內的分鐘數

- `%S`目前分鐘中的秒數

- `%%`百分比符號

*nFormatID*<br/>
格式控制字串的資源識別碼。

### <a name="return-value"></a>傳回值

包含`CString`格式化日期/時間值的 。

### <a name="remarks"></a>備註

如果此`COleDateTime`物件的狀態為 null,則傳回值為空字串。 如果狀態無效,則返回字串由字串資源ATL_IDS_DATETIME_INVALID指定。

此函數的三種窗體的簡要說明如下:

`Format`*(dwFlags*, *lcid*)<br/>
此表單使用日期和時間的語言規範(區域設置指示)設定值格式。 使用預設參數,此窗體將列印日期和時間,除非時間部分為 0(午夜),在這種情況下,它將只列印日期,或日期部分為 0(1899 年 12 月 30 日),在這種情況下,它將只列印時間。 如果日期/時間值為 0(1899 年 12 月 30 日午夜),則此包含默認參數的窗體將在午夜列印。

`Format`*(lpszFormat*)<br/>
此表單使用格式字串設定值,該字串包含特殊格式碼,前面有百分比符號 (%),如中`printf`。 格式化字串作為參數傳遞給函數。 有關格式代碼的詳細資訊,請參閱運行時庫參考中的[「時刻」和「wcsftime」。。](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)

`Format`( *nFormatID*)<br/>
此表單使用格式字串設定值,該字串包含特殊格式碼,前面有百分比符號 (%),如中`printf`。 格式化字串是一個資源。 此字串資源的 ID 作為參數傳遞。 有關格式代碼的詳細資訊,請參閱*運行時庫參考*中的[「時刻」和 wcsftime。](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#3](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_5.cpp)]

## <a name="coledatetimegetasdbtimestamp"></a><a name="getasdbtimestamp"></a>COleDatetime:取得 ASDBTIMESTAMP

調用此方法以獲取`COleDateTime`對象`DBTIMESTAMP`中作為數據結構的時間。

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& timeStamp) const throw();
```

### <a name="parameters"></a>參數

*時間 戳*<br/>
對[DBTimeStamp](/dotnet/api/system.data.oledb.oledbtype)結構的引用。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

將結果時間存儲在引用*的時間戳*結構中。 此`DBTIMESTAMP`函數初始化的數據結構將使其`fraction`成員設置為零。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#4](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_6.cpp)]

## <a name="coledatetimegetassystemtime"></a><a name="getassystemtime"></a>COleDatetime:取得系統時間

調用此方法以獲取`COleDateTime`對象`SYSTEMTIME`中作為數據結構的時間。

```
bool GetAsSystemTime(SYSTEMTIME& sysTime) const throw();
```

### <a name="parameters"></a>參數

*sysTime*<br/>
對[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的引用,`COleDateTime`用於從 物件接收轉換的日期/時間值。

### <a name="return-value"></a>傳回值

如果成功,則返回 TRUE;如果轉換失敗,或者物件為 NULL`COleDateTime`或無效,則 FALSE。

### <a name="remarks"></a>備註

`GetAsSystemTime`在引用的*sysTime*物件中儲存生成的時間。 此`SYSTEMTIME`函數初始化的數據結構將使其`wMilliseconds`成員設置為零。

有關`COleDateTime`物件中持有的狀態資訊的詳細資訊,請參閱[獲取狀態](#getstatus)。

## <a name="coledatetimegetasudate"></a><a name="getasudate"></a>COleDate時間:取得日期

調用此方法以獲取`COleDateTime`對象`UDATE`中作為數據結構的時間。

```
bool GetAsUDATE(UDATE& uDate) const throw();
```

### <a name="parameters"></a>參數

*uDate*<br/>
對結構的`UDATE`引用,用於`COleDateTime`從 物件接收轉換的日期/時間值。

### <a name="return-value"></a>傳回值

如果成功,則返回 TRUE;如果轉換失敗,或者物件為 NULL`COleDateTime`或無效,則 FALSE。

### <a name="remarks"></a>備註

結構`UDATE`表示"未包裝"日期。

## <a name="coledatetimegetcurrenttime"></a><a name="getcurrenttime"></a>COleDateTime:取得目前時間

調用此靜態成員函數以返回當前日期/時間值。

```
static COleDateTime WINAPI GetCurrentTime() throw();
```

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#5](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_7.cpp)]

## <a name="coledatetimegetday"></a><a name="getday"></a>COleDateTime時間:取得日

獲取由此日期/時間值表示的月份日期。

```
int GetDay() const throw();
```

### <a name="return-value"></a>傳回值

由此`COleDateTime`物件的值表示的月份當天,或者`COleDateTime::error`如果 無法獲取該天。

### <a name="remarks"></a>備註

有效返回值範圍在 1 和 31 之間。

有關查詢此`COleDateTime`物件值的其他成員函數的資訊,請參閱以下成員函數:

- [取得月](#getmonth)

- [取得年份](#getyear)

- [取得小時](#gethour)

- [取得分鐘](#getminute)

- [取得第二](#getsecond)

- [取得周](#getdayofweek)

- [獲得新年](#getdayofyear)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#6](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_8.cpp)]

## <a name="coledatetimegetdayofweek"></a><a name="getdayofweek"></a>COleDatetime:取得周

獲取由此日期/時間值表示的月份日期。

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>傳回值

由此`COleDateTime`物件的值表示的星期數,或者`COleDateTime::error`如果 無法獲取星期一。

### <a name="remarks"></a>備註

有效返回值的範圍介於 1 和 7 之間,其中 1=星期日、2=星期一等。

有關查詢此`COleDateTime`物件值的其他成員函數的資訊,請參閱以下成員函數:

- [取得日](#getday)

- [取得月](#getmonth)

- [取得年份](#getyear)

- [取得小時](#gethour)

- [取得分鐘](#getminute)

- [取得第二](#getsecond)

- [獲得新年](#getdayofyear)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#7](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_9.cpp)]

## <a name="coledatetimegetdayofyear"></a><a name="getdayofyear"></a>COleDatetime:取得一年

獲取由此日期/時間值表示的一年中的日期。

```
int GetDayOfYear() const throw();
```

### <a name="return-value"></a>傳回值

以此`COleDateTime`物件的值表示的一年中的天,或者`COleDateTime::error`如果 無法獲取該年份的當天。

### <a name="remarks"></a>備註

有效返回值的範圍介於 1 和 366 之間,其中 1 月 1 = 1。

有關查詢此`COleDateTime`物件值的其他成員函數的資訊,請參閱以下成員函數:

- [取得日](#getday)

- [取得月](#getmonth)

- [取得年份](#getyear)

- [取得小時](#gethour)

- [取得分鐘](#getminute)

- [取得第二](#getsecond)

- [取得周](#getdayofweek)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#8](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_10.cpp)]

## <a name="coledatetimegethour"></a><a name="gethour"></a>COleDatetime:取得小時

獲取此日期/時間值表示的小時。

```
int GetHour() const throw();
```

### <a name="return-value"></a>傳回值

由此`COleDateTime`物件的值表示的小時,或者`COleDateTime::error`如果 無法獲取小時。

### <a name="remarks"></a>備註

有效返回值範圍介於 0 和 23 之間。

有關查詢此`COleDateTime`物件值的其他成員函數的資訊,請參閱以下成員函數:

- [取得日](#getday)

- [取得月](#getmonth)

- [取得年份](#getyear)

- [取得分鐘](#getminute)

- [取得第二](#getsecond)

- [取得周](#getdayofweek)

- [獲得新年](#getdayofyear)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#9](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_11.cpp)]

## <a name="coledatetimegetminute"></a><a name="getminute"></a>COleDatetime:取得分鐘

獲取此日期/時間值表示的分鐘。

```
int GetMinute() const throw();
```

### <a name="return-value"></a>傳回值

由此`COleDateTime`物件的值表示的分鐘,或者`COleDateTime::error`如果 無法獲取分鐘。

### <a name="remarks"></a>備註

有效返回值範圍介於 0 和 59 之間。

有關查詢此`COleDateTime`物件值的其他成員函數的資訊,請參閱以下成員函數:

- [取得日](#getday)

- [取得月](#getmonth)

- [取得年份](#getyear)

- [取得小時](#gethour)

- [取得第二](#getsecond)

- [取得周](#getdayofweek)

- [獲得新年](#getdayofyear)

### <a name="example"></a>範例

請參閱[GetHour](#gethour)的範例。

## <a name="coledatetimegetmonth"></a><a name="getmonth"></a>COleDateTime時間:取得月

獲取由此日期/時間值表示的月份。

```
int GetMonth() const throw();
```

### <a name="return-value"></a>傳回值

由此`COleDateTime`物件的值表示的月份,或者`COleDateTime::error`如果 無法獲取該月。

### <a name="remarks"></a>備註

有效返回值的範圍在 1 和 12 之間。

有關查詢此`COleDateTime`物件值的其他成員函數的資訊,請參閱以下成員函數:

- [取得日](#getday)

- [取得年份](#getyear)

- [取得小時](#gethour)

- [取得分鐘](#getminute)

- [取得第二](#getsecond)

- [取得周](#getdayofweek)

- [獲得新年](#getdayofyear)

### <a name="example"></a>範例

請參閱[GetDay](#getday)的範例。

## <a name="coledatetimegetsecond"></a><a name="getsecond"></a>COleDateTime時間:取得第二

獲取此日期/時間值表示的第二個。

```
int GetSecond() const throw();
```

### <a name="return-value"></a>傳回值

第二個由此`COleDateTime`物件的值表示`COleDateTime::error`或 第二個無法獲取。

### <a name="remarks"></a>備註

有效返回值範圍介於 0 和 59 之間。

> [!NOTE]
> 類`COleDateTime`不支援閏秒。

有關的`COleDateTime`實現的詳細資訊,請參閱文章["日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)"。

有關查詢此`COleDateTime`物件值的其他成員函數的資訊,請參閱以下成員函數:

- [取得日](#getday)

- [取得月](#getmonth)

- [取得年份](#getyear)

- [取得小時](#gethour)

- [取得分鐘](#getminute)

- [取得周](#getdayofweek)

- [獲得新年](#getdayofyear)

### <a name="example"></a>範例

請參閱[GetHour](#gethour)的範例。

## <a name="coledatetimegetstatus"></a><a name="getstatus"></a>COleDateTime時間:取得狀態

獲取給定`COleDateTime`物件的狀態(有效性)。

```
DateTimeStatus GetStatus() const throw();
```

### <a name="return-value"></a>傳回值

返回此值`COleDateTime`的狀態。 如果調用`GetStatus`使用預設值建`COleDateTime`構 的物件,它將返回有效。 如果呼叫`GetStatus``COleDateTime`使用 建構函數設定為 null`GetStatus`初始化的物件, 則傳回 null。

### <a name="remarks"></a>備註

返回值由`DateTimeStatus`枚舉類型定義,該類型在類`COleDateTime`中 定義。

```
enum DateTimeStatus
{
   error = -1,
   valid = 0,
   invalid = 1,    // Invalid date (out of range, etc.)
   null = 2,       // Literally has no value
};
```

有關這些狀態值的簡要說明,請參閱以下清單:

- `COleDateTime::error`指示嘗試獲取部分日期/時間值時出錯。

- `COleDateTime::valid`指示此`COleDateTime`物件有效。

- `COleDateTime::invalid`指示此物件`COleDateTime`無效;如果表明此物件無效。也就是說,其值可能不正確。

- `COleDateTime::null`指示此`COleDateTime`物件為 null,即未為此物件提供任何值。 (這是"無值"的資料庫意義上的"空",而不是C++ NULL。

在以下情況下,`COleDateTime`物件的狀態無效:

- 如果其值從 無法轉換`VARIANT`為`COleVariant`日期 /時間值的 或 值設置。

- 如果其值從`time_t`、`SYSTEMTIME``FILETIME`或無法轉換為有效日期/時間值的值設定。

- 如果其值由`SetDateTime`無效參數值設置。

- 如果此物件在算術賦值操作期間(即`+=``-=`或 ) 經歷了溢出或下溢。

- 如果為此物件分配了無效值。

- 如果此物件的狀態被顯式設定為無效使用`SetStatus`。

有關可能將狀態設置為無效的操作的詳細資訊,請參閱以下成員函數:

- [COleDateTime](#coledatetime)

- [設定日期時間](#setdatetime)

- [運算符 +, -](#operator_add_-)

- [運算子 *, -]](#operator_add_eq_-_eq)

有關`COleDateTime`值邊界的詳細資訊,請參閱文章[「日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)」。。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#10](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_12.cpp)]

## <a name="coledatetimegetyear"></a><a name="getyear"></a>COleDate時間:取得年份

獲取由此日期/時間值表示的年份。

```
int GetYear() const throw();
```

### <a name="return-value"></a>傳回值

由此`COleDateTime`物件的值表示的年份,或者`COleDateTime::error`如果 無法獲得該年份。

### <a name="remarks"></a>備註

有效返回值範圍介於 100 和 9999 之間,其中包括世紀。

有關查詢此`COleDateTime`物件值的其他成員函數的資訊,請參閱以下成員函數:

- [取得日](#getday)

- [取得月](#getmonth)

- [取得小時](#gethour)

- [取得分鐘](#getminute)

- [取得第二](#getsecond)

- [取得周](#getdayofweek)

- [獲得新年](#getdayofyear)

有關`COleDateTime`值邊界的詳細資訊,請參閱文章[「日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)」。。

### <a name="example"></a>範例

請參閱[GetDay](#getday)的範例。

## <a name="coledatetimem_dt"></a><a name="m_dt"></a>COleDate時間::m_dt

此`COleDateTime`對`DATE`象的基礎結構。

```
DATE m_dt;
```

### <a name="remarks"></a>備註

> [!CAUTION]
> 更改此函數返回的`DATE`指標存取的物件中的值將更改此`COleDateTime`物件的值。 它不會更改此`COleDateTime`物件的狀態。

有關物件的實現的詳細資訊,`DATE`請參閱文章[「日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)」。。

## <a name="coledatetimem_status"></a><a name="m_status"></a>COleDate時間::m_status

包含此`COleDateTime`物件的狀態。

```
DateTimeStatus m_status;
```

### <a name="remarks"></a>備註

此數據成員的類型是枚舉類型`DateTimeStatus`,在類`COleDateTime`中 定義。 有關詳細資訊,請參閱[COleDateTime::取得狀態](#getstatus)。

> [!CAUTION]
> 此數據成員適用於高級程式設計情況。 應使用內聯成員函數[「獲取狀態」](#getstatus)和[「設定狀態](#setstatus)」 。 有關`SetStatus`顯式設置此數據成員的進一步注意事項,請參閱。

## <a name="coledatetimeoperator-"></a><a name="operator_eq"></a>COleDateTime::運算符 |

複製值`COleDateTime`。

```
COleDateTime& operator=(const VARIANT& varSrc) throw();
COleDateTime& operator=(DATE dtSrc) throw();
COleDateTime& operator=(const time_t& timeSrc) throw();
COleDateTime& operator=(const __time64_t& timeSrc) throw();
COleDateTime& operator=(const SYSTEMTIME& systimeSrc) throw();
COleDateTime& operator=(const FILETIME& filetimeSrc) throw();
COleDateTime& operator=(const UDATE& uDate) throw();
```

### <a name="remarks"></a>備註

這些重載分配運算子將源日期/時間值複製到此`COleDateTime`物件中。 下面簡要說明每個重載分配運算符號:

- **運算子 *(** `dateSrc` **)** 操作數的值和狀態將複製到此`COleDateTime`物件中。

- 運算子 **(varSrc* **operator =(** **)** 如果[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)值(或[COleVariant](../../mfc/reference/colevariant-class.md)物件)轉換為日期/時間 (VT_DATE) 成功,則轉換`COleDateTime`后的值將複製到此 物件中,其狀態設置為有效。 如果轉換不成功,則此物件的值設置為零(1899 年 12 月 30 日午夜),其狀態設置為無效。

- **運算子 *(** `dtSrc` **)** 該`DATE`值將複製到`COleDateTime`此 物件,其狀態設置為有效。

- **運算子 *(** `timeSrc` **)** 或`time_t``__time64_t`值將轉換並複製到此`COleDateTime`物件中。 如果轉換成功,則此物件的狀態設置為有效;如果轉換成功,則此物件的狀態將設置為"有效"。如果不成功,則將其設置為無效。

- **運算子 =(***系統Src)* **)**[系統時間](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)值將轉換並複製到此`COleDateTime`物件。 如果轉換成功,則此物件的狀態設置為有效;如果轉換成功,則此物件的狀態將設置為"有效"。如果不成功,則將其設置為無效。

- **運算子 *(** `uDate` **)** 該`UDATE`值將轉換並複製到此`COleDateTime`物件。 如果轉換成功,則此物件的狀態設置為有效;如果轉換成功,則此物件的狀態將設置為"有效"。如果不成功,則將其設置為無效。 結構`UDATE`表示"未包裝"日期。 有關詳細資訊,請參閱函數[VarDateFromUdate](/windows/win32/api/oleauto/nf-oleauto-vardatefromudate)。

- **運算子 *(** `filetimeSrc` **)**[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)值將轉換並複製到`COleDateTime`此 物件中。 如果轉換成功,則此物件的狀態設置為有效;如果轉換成功,則此物件的狀態將設置為"有效"。否則,它設置為無效。 `FILETIME`使用通用協調時間 (UTC),因此,如果您在結構中傳遞 UTC 時間,則結果將從 UTC 時間轉換為本地時間,並將儲存為變體時間。 此行為與 Visual C++ 6.0 和 Visual C++.NET 2003 SP2 中的行為相同。 關於詳細資訊,請參閱 Windows SDK 中的[檔案時間](/windows/win32/SysInfo/file-times)。

有關詳細資訊,請參閱 Windows SDK 中的[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)條目。

有關`time_t`數據類型的詳細資訊,請參閱*運行時庫參考*中[的時間](../../c-runtime-library/reference/time-time32-time64.md)函數。

有關詳細資訊,請參閱 Windows SDK 中的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)和[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)結構。

有關`COleDateTime`值邊界的詳細資訊,請參閱文章[「日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)」。。

## <a name="coledatetimeoperator---"></a><a name="operator_add_-"></a>COleDateTime::操作員 +, -

添加和減去`ColeDateTime`值。

```
COleDateTime operator+(COleDateTimeSpan dateSpan) const throw();
COleDateTime operator-(COleDateTimeSpan dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTime& date) const throw();
```

### <a name="remarks"></a>備註

`COleDateTime`物件表示絕對時間。 [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)物件表示相對時間。 前兩個運算子允許您從值中新增和減去`COleDateTimeSpan`值`COleDateTime`。 第三個運算子允許您從另一`COleDateTime`個值中減去一個`COleDateTimeSpan`值以生成值。

如果任一操作數為空,則結果`COleDateTime`值的狀態為 null。

如果生成的`COleDateTime`值超出可接受值的邊界,則`COleDateTime`該 值的狀態無效。

如果任一操作數無效,另一個操作數不為空,則結果`COleDateTime`值的狀態無效。

如果**+****-** 物件設定為 null,`COleDateTime`和 運算子將斷言。 有關範例,請參閱[COleDateTime 關係運算子](#coledatetime_relational_operators)。

有關有效、無效和 null 狀態值的詳細資訊,請參閱[m_status](#m_status)成員變數。

有關`COleDateTime`值邊界的詳細資訊,請參閱文章[「日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)」。。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#12](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_13.cpp)]

## <a name="coledatetimeoperator---"></a><a name="operator_add_eq_-_eq"></a>COleDate時間::操作員*,-*

從該`COleDateTime`物件`ColeDateTime`中 添加和減去值。

```
COleDateTime& operator+=(COleDateTimeSpan dateSpan) throw();
COleDateTime& operator-=(COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>備註

這些運算子允許您在此與 中新增與`COleDateTimeSpan`減去值`COleDateTime`。 如果任一操作數為空,則結果`COleDateTime`值的狀態為 null。

如果生成的`COleDateTime`值超出可接受值的邊界,則此`COleDateTime`值 的狀態設置為無效。

如果任一操作數無效,而其他操作數不為空,則結果`COleDateTime`值的狀態無效。

有關有效、無效和 null 狀態值的詳細資訊,請參閱[m_status](#m_status)成員變數。

如果**+=****-=** 物件設定為 null,`COleDateTime`和 運算子將斷言。 有關範例,請參閱[COleDateTime 關係運算子](#coledatetime_relational_operators)。

有關`COleDateTime`值邊界的詳細資訊,請參閱文章[「日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)」。。

## <a name="coledatetimeoperator-date"></a><a name="operator_date"></a>COleDate 時間::操作員日期

轉換`ColeDateTime`成值轉換為`DATE`。

```
operator DATE() const throw();
```

### <a name="remarks"></a>備註

此運算符返回其`DATE`值從此`COleDateTime`物件複製的物件。 有關物件的實現的詳細資訊,`DATE`請參閱文章[「日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)」。。

如果`DATE`物件設定為 null,`COleDateTime`則運算符將斷言。 有關範例,請參閱[COleDateTime 關係運算子](#coledatetime_relational_operators)。

## <a name="coledatetimeparsedatetime"></a><a name="parsedatetime"></a>COleDateTime::P時間

分析要讀取日期/時間值的字串。

```
bool ParseDateTime(
    LPCTSTR lpszDate,
    DWORD dwFlags = 0,
    LCID lcid = LANG_USER_DEFAULT) throw();
```

### <a name="parameters"></a>參數

*lpszDate*<br/>
指向要解析的 null 終止字串的指標。 如需詳細資料，請參閱＜備註＞。

*dwFlags*<br/>
指示區域設置和解析的標誌。 以下一個或多個標誌:

- LOCALE_NOUSEROVERRIDE 使用系統默認區域設置,而不是自定義用戶設置。

- VAR_TIMEVALUEONLY在分析過程中忽略日期部分。

- VAR_DATEVALUEONLY在分析過程中忽略時間部分。

*lcid*<br/>
指示用於轉換區域設置 ID。

### <a name="return-value"></a>傳回值

如果字串已成功轉換為日期/時間值(否則為 FALSE),則返回 TRUE。

### <a name="remarks"></a>備註

如果字串已成功轉換為日期/時間值,則此`COleDateTime`物件的值將設置為該值,其狀態將有效。

> [!NOTE]
> 年值必須介於 100 和 9999 之間(包括)。

*lpszDate*參數可以採用各種格式。 例如,以下字串包含可接受的日期/時間格式:

`"25 January 1996"`

`"8:30:00"`

`"20:30:00"`

`"January 25, 1996 8:30:00"`

`"8:30:00 Jan. 25, 1996"`

`"1/25/1996 8:30:00"  // always specify the full year, even in a 'short date' format`

區域設置 ID 還將影響字串格式是否可以轉換為日期/ 時間值。

在VAR_DATEVALUEONLY的情況下,時間值設置為時間 0 或午夜。 就VAR_TIMEVALUEONLY而言,日期值設置為日期 0,即 1899 年 12 月 30 日。

如果無法將字串轉換為日期/時間值,或者存在數位溢出,則此`COleDateTime`物件的狀態無效。

有關`COleDateTime`值的邊界和實現的詳細資訊,請參閱文章[「日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)」。。

## <a name="coledatetimesetdate"></a><a name="setdate"></a>COleDate 時間::設定日期

設置此`COleDateTime`物件的日期。

```
int SetDate(
    int nYear,
    int nMonth,
    int nDay) throw();
```

### <a name="parameters"></a>參數

*n 年*, *n月*, *nDay*<br/>
指示要複製到此`COleDateTime`物件的日期元件。

### <a name="return-value"></a>傳回值

如果已成功設置此`COleDateTime`物件的值,則為零;否則,1。 此返回值基於`DateTimeStatus`枚舉類型。 有關詳細資訊,請參閱["設置狀態"](#setstatus)成員函數。

### <a name="remarks"></a>備註

日期設定為指定的值。 時間設置為時間 0,午夜。

有關參數值的邊界,請參閱下表:

|參數|Bounds|
|---------------|------------|
|*n年*|100 - 9999|
|*n月*|1 - 12|
|*nDay*|0 - 31|

如果月中的天溢出,它將轉換為下個月的正確日,月份和/或年份將相應地增加。 零的日值表示上個月的最後一天。 行為與`SystemTimeToVariantTime`相同。

如果參數指定的日期值無效,則此物件的狀態將設定為`COleDateTime::invalid`。 應使用[GetStatus](#getstatus)檢查`DATE`該值的有效性,並且不應假定[m_dt](#m_dt)的值將保持未修改狀態。

下面是日期值的一些範例:

|*n年*|*n月*|*nDay*|值|
|-------------|--------------|------------|-----------|
|2000|2|29|2000年2月29日|
|1776|7|4|1776年7月4日|
|1925|4|35|1925年4月35日(無效日期)|
|10000|1|1|10000 年 1 月 1 日(無效日期)|

要同時設定日期和時間,請參閱[COleDateTime:::設定日期時間](#setdatetime)。

有關查詢此`COleDateTime`物件值的成員函數的資訊,請參閱以下成員函數:

- [取得日](#getday)

- [取得月](#getmonth)

- [取得年份](#getyear)

- [取得小時](#gethour)

- [取得分鐘](#getminute)

- [取得第二](#getsecond)

- [取得周](#getdayofweek)

- [獲得新年](#getdayofyear)

有關`COleDateTime`值邊界的詳細資訊,請參閱文章[「日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)」。。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#11](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_14.cpp)]

## <a name="coledatetimesetdatetime"></a><a name="setdatetime"></a>COleDate時間::設定日期時間

設置此`COleDateTime`物件的日期和時間。

```
int SetDateTime(
    int nYear,
    int nMonth,
    int nDay,
    int nHour,
    int nMin,
    int nSec) throw();
```

### <a name="parameters"></a>參數

*nYear*, *nMonth*, *nDay*, *nHour*, *nMin*, *nSec*<br/>
指示要複製到此`COleDateTime`物件的日期和時間元件。

### <a name="return-value"></a>傳回值

如果已成功設置此`COleDateTime`物件的值,則為零;否則,1。 此返回值基於`DateTimeStatus`枚舉類型。 有關詳細資訊,請參閱["設置狀態"](#setstatus)成員函數。

### <a name="remarks"></a>備註

有關參數值的邊界,請參閱下表:

|參數|Bounds|
|---------------|------------|
|*n年*|100 - 9999|
|*n月*|1 - 12|
|*nDay*|0 - 31|
|*nHour*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

如果月中的天溢出,它將轉換為下個月的正確日,月份和/或年份將相應地增加。 零的日值表示上個月的最後一天。 該行為與[系統時間到變數時間](/windows/win32/api/oleauto/nf-oleauto-systemtimetovarianttime)相同。

如果參數指定的日期或時間值無效,則此物件的狀態設置為無效,並且不會更改此物件的值。

下面是一些時間值範例:

|*nHour*|*nMin*|*nSec*|值|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|無效|
|9|60|0|無效|

下面是日期值的一些範例:

|*n年*|*n月*|*nDay*|值|
|-------------|--------------|------------|-----------|
|1995|4|15|1995年4月15日|
|1789|7|14|17 7月17日 1789|
|1925|2|30|無效|
|10000|1|1|無效|

要設定日期,請參閱[COleDateTime:::設定日期](#setdate)。 要設定時間,請參閱[COleDateTime:::設定時間](#settime)。

有關查詢此`COleDateTime`物件值的成員函數的資訊,請參閱以下成員函數:

- [取得日](#getday)

- [取得月](#getmonth)

- [取得年份](#getyear)

- [取得小時](#gethour)

- [取得分鐘](#getminute)

- [取得第二](#getsecond)

- [取得周](#getdayofweek)

- [獲得新年](#getdayofyear)

有關`COleDateTime`值邊界的詳細資訊,請參閱文章[「日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)」。。

### <a name="example"></a>範例

請參考[取狀態的範例](#getstatus)。

## <a name="coledatetimesetstatus"></a><a name="setstatus"></a>COleDatetime::設定狀態

設置此`COleDateTime`物件的狀態。

```
void SetStatus(DateTimeStatus status) throw();
```

### <a name="parameters"></a>參數

*狀態*<br/>
此`COleDateTime`物件的新狀態值。

### <a name="remarks"></a>備註

*狀態*參數值`DateTimeStatus`由 枚舉類型定義,該類型在`COleDateTime`類中 定義。 關於詳細資訊[,請參閱 COleDateTime:取得狀態](#getstatus)。

> [!CAUTION]
> 此功能適用於高級程式設計情況。 此函數不會更改此物件中的數據。 它最常用於將狀態設定為**null**或**無效**。 賦值運算符 ([運算符 =](#operator_eq)) 和[SetDateTime](#setdatetime)會根據來源值設定物件的狀態。

### <a name="example"></a>範例

請參考[取狀態的範例](#getstatus)。

## <a name="coledatetimesettime"></a><a name="settime"></a>COleDateTime::設定時間

設置此`COleDateTime`物件的時間。

```
int SetTime(
    int nHour,
    int nMin,
    int nSec) throw();
```

### <a name="parameters"></a>參數

*nHour*, *nMin*, *nSec*<br/>
指示要複製到此`COleDateTime`物件的時間元件。

### <a name="return-value"></a>傳回值

如果已成功設置此`COleDateTime`物件的值,則為零;否則,1。 此返回值基於`DateTimeStatus`枚舉類型。 有關詳細資訊,請參閱["設置狀態"](#setstatus)成員函數。

### <a name="remarks"></a>備註

時間設置為指定的值。 日期設置為日期 0,即 1899 年 12 月 30 日。

有關參數值的邊界,請參閱下表:

|參數|Bounds|
|---------------|------------|
|*nHour*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

如果參數指定的時間值無效,則此物件的狀態設置為無效,並且不會更改此物件的值。

下面是一些時間值範例:

|*nHour*|*nMin*|*nSec*|值|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|無效|
|9|60|0|無效|

要同時設定日期和時間,請參閱[COleDateTime:::設定日期時間](#setdatetime)。

有關查詢此`COleDateTime`物件值的成員函數的資訊,請參閱以下成員函數:

- [取得日](#getday)

- [取得月](#getmonth)

- [取得年份](#getyear)

- [取得小時](#gethour)

- [取得分鐘](#getminute)

- [取得第二](#getsecond)

- [取得周](#getdayofweek)

- [獲得新年](#getdayofyear)

有關`COleDateTime`值邊界的詳細資訊,請參閱文章[「日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)」。。

### <a name="example"></a>範例

請參閱[SetDate](#setdate)的範例。

## <a name="see-also"></a>另請參閱

[COleVariant 類別](../../mfc/reference/colevariant-class.md)<br/>
[CTime 類別](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan 類別](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)
