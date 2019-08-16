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
ms.openlocfilehash: a254019d1efe916365799affa3d2c5271883bafb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491264"
---
# <a name="coledatetime-class"></a>COleDateTime 類別

封裝 OLE `DATE` automation 中使用的資料類型。

## <a name="syntax"></a>語法

```
class COleDateTime
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleDateTime:: COleDateTime](#coledatetime)|建構 `COleDateTime` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleDateTime::Format](#format)|產生`COleDateTime`物件的格式化字串表示。|
|[COleDateTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|呼叫這個方法, 以取得`COleDateTime`物件中的時間`DBTIMESTAMP`做為資料結構。|
|[COleDateTime::GetAsSystemTime](#getassystemtime)|呼叫這個方法, 以取得`COleDateTime`物件中的時間做為[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)資料結構。|
|[COleDateTime::GetAsUDATE](#getasudate)|呼叫這個方法, 以取得中`COleDateTime`的時間`UDATE`做為資料結構。|
|[COleDateTime::GetCurrentTime](#getcurrenttime)|`COleDateTime`建立物件, 代表目前的時間 (靜態成員函式)。|
|[COleDateTime::GetDay](#getday)|傳回此`COleDateTime`物件表示的日期 (1-31)。|
|[COleDateTime::GetDayOfWeek](#getdayofweek)|傳回此`COleDateTime`物件表示的周中的第幾天 (星期日 = 1)。|
|[COleDateTime::GetDayOfYear](#getdayofyear)|傳回此`COleDateTime`物件表示的一年中的第幾天 (Jan 1 = 1)。|
|[COleDateTime::GetHour](#gethour)|傳回此`COleDateTime`物件表示的小時 (0-23)。|
|[COleDateTime::GetMinute](#getminute)|傳回此`COleDateTime`物件表示的分鐘數 (0-59)。|
|[COleDateTime::GetMonth](#getmonth)|傳回此`COleDateTime`物件表示的月份 (1-12)。|
|[COleDateTime::GetSecond](#getsecond)|傳回此`COleDateTime`物件表示的第二個 (0-59)。|
|[COleDateTime::GetStatus](#getstatus)|取得這個`COleDateTime`物件的狀態 (有效性)。|
|[COleDateTime::GetYear](#getyear)|傳回此`COleDateTime`物件表示的年份。|
|[COleDateTime::ParseDateTime](#parsedatetime)|從字串讀取日期/時間值, 並設定的值`COleDateTime`。|
|[COleDateTime::SetDate](#setdate)|將這個`COleDateTime`物件的值設定為指定的僅限日期值。|
|[COleDateTime::SetDateTime](#setdatetime)|將這個`COleDateTime`物件的值設定為指定的日期/時間值。|
|[COleDateTime::SetStatus](#setstatus)|設定這個`COleDateTime`物件的狀態 (有效性)。|
|[COleDateTime::SetTime](#settime)|將這個`COleDateTime`物件的值設定為指定的僅限時間值。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[COleDateTime:: operator = =、COleDateTime:: operator < 等。](#coledatetime_relational_operators)|比較兩`COleDateTime`個值。|
|[COleDateTime:: operator +、COleDateTime:: operator-](#operator_add_-)|加入和減去`COleDateTime`值。|
|[COleDateTime:: operator + =、COleDateTime:: operator-=](#operator_add_eq_-_eq)|新增和減去此`COleDateTime` `COleDateTime`物件中的值。|
|[COleDateTime:: operator =](#operator_eq)|`COleDateTime`複製值。|
|[COleDateTime:: operator DATE, COleDateTime:: operator Date *](#operator_date)|將值轉換`DATE`為或`DATE*`。 `COleDateTime`|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[COleDateTime::m_dt](#m_dt)|包含這個`DATE` `COleDateTime`物件的基礎。|
|[COleDateTime:: m_status](#m_status)|包含此`COleDateTime`物件的狀態。|

## <a name="remarks"></a>備註

`COleDateTime`沒有基類。

這是 OLE automation 的[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)資料類型可能的類型之一。 `COleDateTime`值代表絕對日期和時間值。

`DATE`型別會實作為浮點值。 天數是從1899年12月30日午夜算起。 下表顯示一些日期和其相關聯的值:

|Date|值|
|----------|-----------|
|1899年12月29日, 午夜|-1.0|
|1899年12月29日, 第6個. M|-1.25|
|1899年12月30日, 午夜|0.0|
|1899年12月31日, 午夜|1.0|
|1900年1月1日, 上午6點|2.25|

> [!CAUTION]
> 在上表中, 雖然日期值會在1899年12月30日午夜之前變成負值, 但時間值不是。 例如, 6:00 AM 一律以小數值0.25 表示, 而不論代表日期的整數是正數 (12 月 30 1899 日之後) 或負面 (在1899年12月30日之前)。 這表示簡單的浮點比較會錯誤地排序, 代表`COleDateTime`在同一日代表 7:00 am的12/29/1899 上的 6:00 am。

`COleDateTime`類別會處理從100年1月1日到9999年12月31日的日期。 `COleDateTime`類別使用西曆, 不支援 Julian 日期。 `COleDateTime`忽略日光節約時間。 (請[參閱日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md))。

> [!NOTE]
> 您可以使用`%y`格式, 只針對從1900開始的日期, 取出兩位數的年份。 如果您在 1900 `%y`之前的日期使用格式, 則程式碼會產生判斷提示失敗。

這個類型也會用來表示僅限日期或僅限時間的值。 依照慣例, 日期 0 (1899 年12月30日) 用於僅限時間的值, 而時間 00:00 (午夜) 用於僅限日期的值。

如果您使用小於`COleDateTime` 100 的日期來建立物件, 則會接受日期, 但後續`GetYear`呼叫、 `GetMonth`、 `GetDay` `GetHour` `GetMinute`、、和`GetSecond`會失敗, 並傳回-1。 之前, 您可以使用兩位數的日期, 但 MFC 4.2 和更新版本中的日期必須是100或更大。

若要避免發生問題, 請指定四位數的日期。 例如：

[!code-cpp[NVC_ATLMFC_Utilities#1](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_1.cpp)]

`COleDateTime`值的基本算數運算會使用隨附類別[COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)。 `COleDateTimeSpan`值會定義時間間隔。 這些類別之間的關聯性類似于[CTime](../../atl-mfc-shared/reference/ctime-class.md)和[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)之間的關係。

如需`COleDateTime`和`COleDateTimeSpan`類別的詳細資訊, 請參閱文章[日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

## <a name="requirements"></a>需求

**標頭：** ATLComTime.h

##  <a name="coledatetime_relational_operators"></a>COleDateTime 關係運算子

比較運算子。

```
bool operator==(const COleDateTime& date) const throw();
bool operator!=(const COleDateTime& date) const throw();
bool operator<(const COleDateTime& date) const throw();
bool operator>(const COleDateTime& date) const throw();
bool operator<=(const COleDateTime& date) const throw();
bool operator>=(const COleDateTime& date) const throw();
```

### <a name="parameters"></a>參數

*date*<br/>
要比較的 `COleDateTime` 物件。

### <a name="remarks"></a>備註

> [!NOTE]
>  如果兩個運算元的其中一個無效, 就會發生 ATLASSERT。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#13](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_2.cpp)]

### <a name="example"></a>範例

運算子 **>=** ， **\<=** ， **>** ，與 **<** ，如果會判斷提示`COleDateTime`物件設定為 null。

[!code-cpp[NVC_ATLMFC_Utilities#170](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_3.cpp)]

##  <a name="coledatetime"></a>COleDateTime:: COleDateTime

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

*dateSrc*<br/>
要複製`COleDateTime`到新`COleDateTime`物件中的現有物件。

*varSrc*<br/>
要轉換`VARIANT`成日期/時間值`COleVariant` (VT_DATE) 並複製到新`COleDateTime`物件中的現有資料結構 (可能是物件)。

*dtSrc*<br/>
要複製到新`DATE` `COleDateTime`物件的日期/時間 () 值。

*timeSrc*<br/>
要轉換`__time64_t`成日期/時間值並複製到新`COleDateTime`物件的或值。`time_t`

*systimeSrc*<br/>
要轉換成日期/時間值並複製到新`COleDateTime`物件的結構。`SYSTEMTIME`

*filetimeSrc*<br/>
要轉換成日期/時間值並複製到新`COleDateTime`物件的結構。`FILETIME` 會`FILETIME`使用國際標準時間 (UTC), 因此, 如果您在結構中傳遞當地時間, 您的結果將會不正確。 如需詳細資訊, 請參閱 Windows SDK 中的檔案[時間](/windows/win32/SysInfo/file-times)。

*nYear*、 *nMonth*、 *nDay*、 *nHour*、 *n 每天下限*、 *nSec*<br/>
指出要複製到新`COleDateTime`物件的日期和時間值。

*wDosDate*、 *wDosTime*<br/>
要轉換成日期/時間值並複製到新`COleDateTime`物件的 MS-DOS 日期和時間值。

*timeStamp*<br/>
[DBTimeStamp](/dotnet/api/system.data.oledb.oledbtype)結構的參考, 其中包含目前的本地時間。

### <a name="remarks"></a>備註

所有這些函式都會`COleDateTime`建立新的物件, 並初始化為指定的值。 下表顯示每個日期和時間元件的有效範圍:

|日期/時間元件|有效範圍|
|--------------------------|-----------------|
|年|100 - 9999|
|月|0 - 12|
|天|0 - 31|
|hour|0 - 23|
|minute|0 - 59|
|second|0 - 59|

請注意, day 元件的實際上限會根據 month 和 year 元件而有所不同。 如需詳細資訊, `SetDate`請`SetDateTime`參閱或成員函式。

以下是每個函式的簡短說明:

- `COleDateTime(` **) 會**將物件初始化為0(午夜,1899年12月30日)。`COleDateTime`

- `COleDateTime(`) 會從`COleDateTime` 現有`COleDateTime`的物件來建立物件。 `dateSrc`

- `COleDateTime(`*varSrc* **)** 會構造`COleDateTime`物件。 嘗試將`VARIANT`結構或[COleVariant](../../mfc/reference/colevariant-class.md)物件轉換成日期/時間 ( `VT_DATE`) 值。 如果這種轉換成功, 轉換後的值會複製到新`COleDateTime`的物件中。 如果不是, 則`COleDateTime`物件的值會設定為 0 (午夜, 1899 年12月30日), 而其狀態為「無效」。

- `COleDateTime(`) 會從 值`DATE`中建立物件。`COleDateTime` `dtSrc`

- `COleDateTime(`) 會從 值`time_t`中建立物件。`COleDateTime` `timeSrc`

- `COleDateTime(`*systimeSrc* **) 會**從`SYSTEMTIME`值中建立物件。`COleDateTime`

- `COleDateTime(`) 會從 值`FILETIME`中建立物件。`COleDateTime` `filetimeSrc` . 會`FILETIME`使用國際標準時間 (UTC), 因此, 如果您在結構中傳遞當地時間, 您的結果將會不正確。 如需詳細資訊, 請參閱 Windows SDK 中的檔案[時間](/windows/win32/SysInfo/file-times)。

- `COleDateTime(``nYear`、 、、`nDay` 、、)`nSec`會從指定的數值來構造`COleDateTime`物件。 `nMin` `nHour` `nMonth`

- `COleDateTime(`,) 從指定`COleDateTime`的 MS-DOS 日期和時間值, `wDosTime`來建立物件。 `wDosDate`

如需有關`time_t`資料類型的詳細資訊, 請參閱《*執行時間程式庫參考*》中的[time](../../c-runtime-library/reference/time-time32-time64.md)函數。

如需詳細資訊, 請參閱 Windows SDK 中的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)和[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)結構。

如需`COleDateTime`值界限的詳細資訊, 請參閱文章[日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

> [!NOTE]
> 只有當包含`DBTIMESTAMP`了 OLEDB 時, 才可以使用參數的函式。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#2](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_4.cpp)]

##  <a name="format"></a>COleDateTime:: Format

建立日期/時間值的格式化表示。

```
CString Format(DWORD dwFlags = 0,  LCID lcid = LANG_USER_DEFAULT) const;
CString Format(LPCTSTR lpszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
指出下列其中一個地區設定旗標:

- LOCALE_NOUSEROVERRIDE 使用系統預設地區設定, 而不是自訂使用者設定。

- VAR_TIMEVALUEONLY 會忽略剖析期間的日期部分。

- VAR_DATEVALUEONLY 會在剖析期間忽略時間部分。

*lcid*<br/>
表示用於轉換的地區設定識別碼。 如需語言識別項的詳細資訊, 請參閱[語言識別項](/windows/win32/Intl/language-identifiers)。

*lpszFormat*<br/>
格式化字串, 類似`printf`于格式字串。 每個格式化程式碼 (前面加上`%`百分比 () 符號) 都會由對應`COleDateTime`的元件所取代。 格式字串中的其他字元會原封不動地複製到傳回的字串。 如需詳細資訊, 請參閱執行時間函式[strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)。 的格式設定代碼`Format`的值與意義如下:

- `%H`當天的時數

- `%M`目前小時內的分鐘數

- `%S`目前分鐘的秒數

- `%%`百分比符號

*nFormatID*<br/>
格式控制字元串的資源識別碼。

### <a name="return-value"></a>傳回值

`CString` , 其中包含格式化的日期/時間值。

### <a name="remarks"></a>備註

如果這個`COleDateTime`物件的狀態是 null, 則傳回值是空字串。 如果狀態無效, 則傳回字串會由字串資源 ATL_IDS_DATETIME_INVALID 指定。

此函式的三種表單簡要說明如下:

`Format`( *dwFlags*, *lcid*)<br/>
此表單會使用日期和時間的語言規格 (地區設定識別碼) 來格式化值。 使用預設參數時, 除非時間部分為 0 (午夜), 否則此表單會列印日期和時間, 在這種情況下, 它只會列印日期, 或日期部分為 0 (1899 年12月30日), 在這種情況下, 它只會列印時間。 如果日期/時間值為 0 (1899 年12月30日, 午夜), 此表單的預設參數將會在午夜列印。

`Format`( *lpszFormat*)<br/>
這個表單會使用包含前面加上百分比符號 (%) 的格式字串來格式化值, 如中`printf`所示。 格式化字串會當做參數傳遞給函式。 如需格式化程式碼的詳細資訊, 請參閱《執行時間程式庫參考》中的[strftime、wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) 。

`Format`( *nFormatID*)<br/>
這個表單會使用包含前面加上百分比符號 (%) 的格式字串來格式化值, 如中`printf`所示。 格式化字串是一種資源。 這個字串資源的識別碼會當做參數傳遞。 如需格式化程式碼的詳細資訊, 請參閱《*執行時間程式庫參考*》中的[strftime、wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) 。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#3](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_5.cpp)]

##  <a name="getasdbtimestamp"></a>COleDateTime:: GetAsDBTIMESTAMP

呼叫這個方法, 以取得`COleDateTime`物件中的時間`DBTIMESTAMP`做為資料結構。

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& timeStamp) const throw();
```

### <a name="parameters"></a>參數

*timeStamp*<br/>
[DBTimeStamp](/dotnet/api/system.data.oledb.oledbtype)結構的參考。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

將產生的時間儲存在參考的*時間戳記*結構中。 此`DBTIMESTAMP`函式所初始化的資料結構會將`fraction`其成員設定為零。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#4](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_6.cpp)]

##  <a name="getassystemtime"></a>COleDateTime:: GetAsSystemTime

呼叫這個方法, 以取得`COleDateTime`物件中的時間`SYSTEMTIME`做為資料結構。

```
bool GetAsSystemTime(SYSTEMTIME& sysTime) const throw();
```

### <a name="parameters"></a>參數

*sysTime*<br/>
[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的參考, 用來接收來自`COleDateTime`物件的已轉換日期/時間值。

### <a name="return-value"></a>傳回值

如果成功, 則傳回 TRUE;如果轉換失敗, 或`COleDateTime`物件為 Null 或無效, 則為 FALSE。

### <a name="remarks"></a>備註

`GetAsSystemTime`將產生的時間儲存在參考的*sysTime*物件中。 此`SYSTEMTIME`函式所初始化的資料結構會將`wMilliseconds`其成員設定為零。

如需`COleDateTime`物件中所保存之狀態資訊的詳細資訊, 請參閱[GetStatus](#getstatus)。

##  <a name="getasudate"></a>COleDateTime:: GetAsUDATE

呼叫這個方法, 以取得`COleDateTime`物件中的時間`UDATE`做為資料結構。

```
bool GetAsUDATE(UDATE& uDate) const throw();
```

### <a name="parameters"></a>參數

*uDate*<br/>
`UDATE`結構的參考, 用來接收`COleDateTime`來自物件的已轉換日期/時間值。

### <a name="return-value"></a>傳回值

如果成功, 則傳回 TRUE;如果轉換失敗, 或`COleDateTime`物件為 Null 或無效, 則為 FALSE。

### <a name="remarks"></a>備註

`UDATE`結構代表「已解壓縮」的日期。

##  <a name="getcurrenttime"></a>COleDateTime:: GetCurrentTime

呼叫此靜態成員函式以傳回目前的日期/時間值。

```
static COleDateTime WINAPI GetCurrentTime() throw();
```

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#5](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_7.cpp)]

##  <a name="getday"></a>COleDateTime:: GetDay

取得此日期/時間值所表示的月份日期。

```
int GetDay() const throw();
```

### <a name="return-value"></a>傳回值

`COleDateTime` 這個`COleDateTime::error`物件的值所代表的月份日期, 如果無法取得日期, 則為。

### <a name="remarks"></a>備註

有效的傳回值範圍介於1到31之間。

如需查詢此`COleDateTime`物件值之其他成員函式的詳細資訊, 請參閱下列成員函式:

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#6](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_8.cpp)]

##  <a name="getdayofweek"></a>COleDateTime:: GetDayOfWeek

取得此日期/時間值所表示的月份日期。

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>傳回值

以這個`COleDateTime` `COleDateTime::error`物件的值表示的星期幾, 如果無法取得星期幾的日期, 則為。

### <a name="remarks"></a>備註

有效的傳回值範圍介於1到7之間, 其中 1 = 星期日、2 = 星期一等等。

如需查詢此`COleDateTime`物件值之其他成員函式的詳細資訊, 請參閱下列成員函式:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#7](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_9.cpp)]

##  <a name="getdayofyear"></a>COleDateTime:: GetDayOfYear

取得此日期/時間值所表示之年份的日期。

```
int GetDayOfYear() const throw();
```

### <a name="return-value"></a>傳回值

以這個`COleDateTime` `COleDateTime::error`物件的值表示的年份日期, 如果無法取得年份的日期, 則為。

### <a name="remarks"></a>備註

有效的傳回值範圍介於1到366之間, 在1月1日 = 1。

如需查詢此`COleDateTime`物件值之其他成員函式的詳細資訊, 請參閱下列成員函式:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#8](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_10.cpp)]

##  <a name="gethour"></a>COleDateTime:: GetHour

取得此日期/時間值所表示的小時。

```
int GetHour() const throw();
```

### <a name="return-value"></a>傳回值

`COleDateTime` 這個`COleDateTime::error`物件的值所表示的小時, 如果無法取得小時, 則為。

### <a name="remarks"></a>備註

有效的傳回值範圍介於0到23之間。

如需查詢此`COleDateTime`物件值之其他成員函式的詳細資訊, 請參閱下列成員函式:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#9](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_11.cpp)]

##  <a name="getminute"></a>COleDateTime:: GetMinute

取得此日期/時間值所表示的分鐘。

```
int GetMinute() const throw();
```

### <a name="return-value"></a>傳回值

以這個`COleDateTime` `COleDateTime::error`物件的值表示的分鐘, 如果無法取得分鐘, 則為。

### <a name="remarks"></a>備註

有效的傳回值範圍介於0到59之間。

如需查詢此`COleDateTime`物件值之其他成員函式的詳細資訊, 請參閱下列成員函式:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>範例

請參閱[GetHour](#gethour)的範例。

##  <a name="getmonth"></a>COleDateTime:: GetMonth

取得此日期/時間值所表示的月份。

```
int GetMonth() const throw();
```

### <a name="return-value"></a>傳回值

以這個`COleDateTime` `COleDateTime::error`物件的值表示的月份, 如果無法取得月份, 則為。

### <a name="remarks"></a>備註

有效的傳回值範圍介於1到12之間。

如需查詢此`COleDateTime`物件值之其他成員函式的詳細資訊, 請參閱下列成員函式:

- [GetDay](#getday)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>範例

請參閱[GetDay](#getday)的範例。

##  <a name="getsecond"></a>COleDateTime:: GetSecond

取得此日期/時間值所表示的第二個。

```
int GetSecond() const throw();
```

### <a name="return-value"></a>傳回值

以這個`COleDateTime` `COleDateTime::error`物件的值表示的第二個, 如果無法取得第二個, 則為。

### <a name="remarks"></a>備註

有效的傳回值範圍介於0到59之間。

> [!NOTE]
>  `COleDateTime`類別不支援閏秒。

如需有關如何執行`COleDateTime`的詳細資訊, 請參閱文章[日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

如需查詢此`COleDateTime`物件值之其他成員函式的詳細資訊, 請參閱下列成員函式:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>範例

請參閱[GetHour](#gethour)的範例。

##  <a name="getstatus"></a>COleDateTime:: GetStatus

取得給定`COleDateTime`物件的狀態 (有效性)。

```
DateTimeStatus GetStatus() const throw();
```

### <a name="return-value"></a>傳回值

傳回此`COleDateTime`值的狀態。 如果您在`GetStatus`以預設`COleDateTime`值所建立的物件上呼叫, 它會傳回有效的。 如果您在`GetStatus`初始化的`COleDateTime`物件上呼叫, 並將此函式`GetStatus`設定為 null, 則會傳回 null。

### <a name="remarks"></a>備註

傳回值是由`DateTimeStatus`列舉型別 (在`COleDateTime`類別內定義) 所定義。

```
enum DateTimeStatus
{
   error = -1,
   valid = 0,
   invalid = 1,    // Invalid date (out of range, etc.)
   null = 2,       // Literally has no value
};
```

如需這些狀態值的簡短描述, 請參閱下列清單:

- `COleDateTime::error`表示嘗試取得部分的日期/時間值時發生錯誤。

- `COleDateTime::valid`指出這個`COleDateTime`物件是有效的。

- `COleDateTime::invalid`指出這個`COleDateTime`物件無效; 也就是說, 它的值可能不正確。

- `COleDateTime::null`指出這個`COleDateTime`物件是 null, 也就是沒有為這個物件提供任何值。 (這是「沒有值」的資料庫意義中的「null」, 而不是C++ null)。

在下列情況下`COleDateTime` , 物件的狀態無效:

- 如果其值是由`VARIANT`無法轉換為日期/時間值的或`COleVariant`值所設定。

- 如果它的值是由`time_t`無法轉換為有效日期/時間值的、 `SYSTEMTIME`或`FILETIME`值所設定。

- 如果其值是由`SetDateTime`不正確參數值所設定。

- 如果這個物件在算術指派作業期間發生溢位或下溢, 即`+=`為或。 `-=`

- 如果將不正確值指派給這個物件, 則為。

- 如果這個物件的狀態已使用`SetStatus`明確設定為無效。

如需可能將狀態設定為無效之作業的詳細資訊, 請參閱下列成員函式:

- [COleDateTime](#coledatetime)

- [SetDateTime](#setdatetime)

- [operator +、-](#operator_add_-)

- [operator +=, -=](#operator_add_eq_-_eq)

如需`COleDateTime`值界限的詳細資訊, 請參閱文章[日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#10](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_12.cpp)]

##  <a name="getyear"></a>COleDateTime:: GetYear

取得此日期/時間值所表示的年份。

```
int GetYear() const throw();
```

### <a name="return-value"></a>傳回值

以這個`COleDateTime` `COleDateTime::error`物件的值表示的年份, 如果無法取得年份, 則為。

### <a name="remarks"></a>備註

有效的傳回值範圍介於100和9999之間, 包括世紀。

如需查詢此`COleDateTime`物件值之其他成員函式的詳細資訊, 請參閱下列成員函式:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

如需`COleDateTime`值界限的詳細資訊, 請參閱文章[日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

### <a name="example"></a>範例

請參閱[GetDay](#getday)的範例。

##  <a name="m_dt"></a>COleDateTime:: m_dt

`DATE` 這個`COleDateTime`物件的基礎結構。

```
DATE m_dt;
```

### <a name="remarks"></a>備註

> [!CAUTION]
>  變更此函式所`DATE`傳回之指標所存取物件中的值, 將會變更這個`COleDateTime`物件的值。 它不會變更此`COleDateTime`物件的狀態。

如需有關如何執行`DATE`物件的詳細資訊, 請參閱文章[日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

##  <a name="m_status"></a>COleDateTime:: m_status

包含此`COleDateTime`物件的狀態。

```
DateTimeStatus m_status;
```

### <a name="remarks"></a>備註

這個資料成員的型別是列舉型`DateTimeStatus`別, 它是在`COleDateTime`類別內定義的。 如需詳細資訊, 請參閱[COleDateTime:: GetStatus](#getstatus)。

> [!CAUTION]
>  此資料成員適用于先進的程式設計情況。 您應該使用內嵌成員函式[GetStatus](#getstatus)和[SetStatus](#setstatus)。 如`SetStatus`需有關明確設定此資料成員的進一步警告, 請參閱。

##  <a name="operator_eq"></a>COleDateTime:: operator =

`COleDateTime`複製值。

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

這些多載指派運算子會將來源日期/時間值複製`COleDateTime`到這個物件。 這些多載指派運算子的簡短說明如下:

- **operator = (** `dateSrc` **)** 將運算元的值和狀態複製到這個`COleDateTime`物件。

- **operator = (** *varSrc* **)** 如果將[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)值 (或[COleVariant](../../mfc/reference/colevariant-class.md)物件) 轉換為日期/時間 (VT_DATE) 成功, 轉換的值會複製到這個`COleDateTime`物件, 而且其狀態會設定為有效。 如果轉換不成功, 此物件的值會設定為零 (1899 年12月30日, 午夜), 其狀態為「無效」。

- **operator = (** `dtSrc` `COleDateTime` )`DATE`此值會複製到這個物件中, 而且其狀態會設定為有效。

- **operator = (** `timeSrc` `COleDateTime` **)** `time_t` :或`__time64_t`值會轉換並複製到這個物件。 如果轉換成功, 則此物件的狀態會設定為 [有效];如果失敗, 則會設為無效。

- **operator = (** *systimeSrc* **)** [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)值會轉換並複製到這個`COleDateTime`物件中。 如果轉換成功, 則此物件的狀態會設定為 [有效];如果失敗, 則會設為無效。

- **operator = (** `uDate` `COleDateTime` )`UDATE`此值會轉換並複製到這個物件中。 如果轉換成功, 則此物件的狀態會設定為 [有效];如果失敗, 則會設為無效。 `UDATE`結構代表「已解壓縮」的日期。 如需詳細資訊, 請參閱函數[VarDateFromUdate](/windows/win32/api/oleauto/nf-oleauto-vardatefromudate)。

- **operator = (** `filetimeSrc` **)** [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)值會轉換並複製到這個`COleDateTime`物件中。 如果轉換成功, 則此物件的狀態會設定為 [有效];否則會設為無效。 `FILETIME`使用國際標準時間 (UTC), 因此, 如果您在結構中傳遞 UTC 時間, 您的結果將會從 UTC 時間轉換為本地時間, 並且會儲存為 variant 時間。 這個行為與 Visual C++ 6.0 和 visual C++.net 2003 SP2 中的相同。 如需詳細資訊, 請參閱 Windows SDK 中的檔案[時間](/windows/win32/SysInfo/file-times)。

如需詳細資訊, 請參閱 Windows SDK 中的[VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant)專案。

如需有關`time_t`資料類型的詳細資訊, 請參閱《*執行時間程式庫參考*》中的[time](../../c-runtime-library/reference/time-time32-time64.md)函數。

如需詳細資訊, 請參閱 Windows SDK 中的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)和[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)結構。

如需`COleDateTime`值界限的詳細資訊, 請參閱文章[日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

##  <a name="operator_add_-"></a>COleDateTime:: operator +,-

加入和減去`ColeDateTime`值。

```
COleDateTime operator+(COleDateTimeSpan dateSpan) const throw();
COleDateTime operator-(COleDateTimeSpan dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTime& date) const throw();
```

### <a name="remarks"></a>備註

`COleDateTime`物件代表絕對的時間。 [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)物件代表相對的時間。 前兩個運算子可讓您新增和減去`COleDateTimeSpan` `COleDateTime`值的值。 第三個運算子可讓您減去`COleDateTime`另一個值, 以`COleDateTimeSpan`產生值。

如果其中一個運算元為 null, 則產生`COleDateTime`值的狀態會是 null。

如果產生`COleDateTime`的值超出可接受值的範圍, 該值的狀態`COleDateTime`就會是不正確。

如果其中一個運算元無效, 而另一個不是 null, 則產生`COleDateTime`值的狀態會無效。

如果物件設定為 null **-** **,和運算子將會判斷提示。+** `COleDateTime` 如需範例, 請參閱[COleDateTime 關係運算子](#coledatetime_relational_operators)。

如需有效、無效和 null 狀態值的詳細資訊, 請參閱[m_status](#m_status)成員變數。

如需`COleDateTime`值界限的詳細資訊, 請參閱文章[日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#12](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_13.cpp)]

##  <a name="operator_add_eq_-_eq"></a>COleDateTime:: operator + =、-=

新增和減去此`ColeDateTime` `COleDateTime`物件中的值。

```
COleDateTime& operator+=(COleDateTimeSpan dateSpan) throw();
COleDateTime& operator-=(COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>備註

這些運算子可讓您在此`COleDateTimeSpan` `COleDateTime`加上和減去值。 如果其中一個運算元為 null, 則產生`COleDateTime`值的狀態會是 null。

如果產生`COleDateTime`的值超出可接受值的範圍, 此`COleDateTime`值的狀態會設定為 [無效]。

如果其中一個運算元無效, 而 other 不是 null, 則產生`COleDateTime`值的狀態會無效。

如需有效、無效和 null 狀態值的詳細資訊, 請參閱[m_status](#m_status)成員變數。

如果物件設定為 null **-=** **,和運算子將會判斷提示。+=** `COleDateTime` 如需範例, 請參閱[COleDateTime 關係運算子](#coledatetime_relational_operators)。

如需`COleDateTime`值界限的詳細資訊, 請參閱文章[日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

##  <a name="operator_date"></a>COleDateTime:: operator 日期

將值轉換成`DATE`。 `ColeDateTime`

```
operator DATE() const throw();
```

### <a name="remarks"></a>備註

這個運算子`DATE`會傳回物件, 其值是`COleDateTime`從此物件複製而來。 如需有關如何執行`DATE`物件的詳細資訊, 請參閱文章[日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

如果物件設定為 null,運算子會判斷提示。`DATE` `COleDateTime` 如需範例, 請參閱[COleDateTime 關係運算子](#coledatetime_relational_operators)。

##  <a name="parsedatetime"></a>COleDateTime::P arseDateTime

剖析字串以讀取日期/時間值。

```
bool ParseDateTime(
    LPCTSTR lpszDate,
    DWORD dwFlags = 0,
    LCID lcid = LANG_USER_DEFAULT) throw();
```

### <a name="parameters"></a>參數

*lpszDate*<br/>
要剖析之以 null 終止之字串的指標。 如需詳細資料，請參閱＜備註＞。

*dwFlags*<br/>
指出地區設定和剖析的旗標。 下列一個或多個旗標:

- LOCALE_NOUSEROVERRIDE 會使用系統預設的地區設定, 而不是自訂的使用者設定。

- VAR_TIMEVALUEONLY 會忽略剖析期間的日期部分。

- VAR_DATEVALUEONLY 會在剖析期間忽略時間部分。

*lcid*<br/>
表示用於轉換的地區設定識別碼。

### <a name="return-value"></a>傳回值

如果字串已成功轉換為日期/時間值, 則傳回 TRUE, 否則傳回 FALSE。

### <a name="remarks"></a>備註

如果字串已成功轉換為日期/時間值, 則此`COleDateTime`物件的值會設定為該值, 且其狀態會是 [有效]。

> [!NOTE]
>  年份值必須介於100到 9999 (含) 之間。

*LpszDate*參數可以採用各種格式。 例如, 下列字串包含可接受的日期/時間格式:

`"25 January 1996"`

`"8:30:00"`

`"20:30:00"`

`"January 25, 1996 8:30:00"`

`"8:30:00 Jan. 25, 1996"`

`"1/25/1996 8:30:00"  // always specify the full year, even in a 'short date' format`

地區設定識別碼也會影響字串格式是否可接受轉換成日期/時間值。

在 VAR_DATEVALUEONLY 的案例中, 時間值設定為 [時間 0] 或 [午夜]。 在 VAR_TIMEVALUEONLY 的案例中, 日期值會設為日期 0, 這表示1899年12月30日。

如果無法將字串轉換成日期/時間值, 或如果有數值溢位, 這個`COleDateTime`物件的狀態就會是不正確。

如需`COleDateTime`值之界限和實作為的詳細資訊, 請參閱[文章日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

##  <a name="setdate"></a>COleDateTime:: SetDate

設定這個`COleDateTime`物件的日期。

```
int SetDate(
    int nYear,
    int nMonth,
    int nDay) throw();
```

### <a name="parameters"></a>參數

*nYear*、 *nMonth*、 *nDay*<br/>
指出要複製到這個`COleDateTime`物件的日期元件。

### <a name="return-value"></a>傳回值

如果已成功設定這個`COleDateTime`物件的值, 則為零, 否則為1。 這個傳回值是以`DateTimeStatus`列舉型別為基礎。 如需詳細資訊, 請參閱[SetStatus](#setstatus)成員函式。

### <a name="remarks"></a>備註

日期會設定為指定的值。 時間會設定為 [時間 0, 午夜]。

請參閱下表以取得參數值的界限:

|參數|超出|
|---------------|------------|
|*nYear*|100 - 9999|
|*nMonth*|1 - 12|
|*nDay*|0 - 31|

如果月份的日溢位, 則會將它轉換成下個月的正確日, 而月份和/或年份會相應增加。 日期值為零表示上個月的最後一天。 行為與相同`SystemTimeToVariantTime`。

如果參數所指定的日期值無效, 則此物件的狀態會設定為`COleDateTime::invalid`。 您應該使用[GetStatus](#getstatus)來檢查`DATE`值的有效性, 而且不應假設[m_dt](#m_dt)的值會保持未修改。

以下是一些日期值的範例:

|*nYear*|*nMonth*|*nDay*|值|
|-------------|--------------|------------|-----------|
|2000|2|29|2000年2月29日|
|1776|7|4|1776年7月4日|
|1925|4|35|35年4月1925日 (不正確日期)|
|10000|1|1|10000年1月1日 (不正確日期)|

若要設定日期和時間, 請參閱[COleDateTime:: SetDateTime](#setdatetime)。

如需查詢此`COleDateTime`物件值之成員函式的詳細資訊, 請參閱下列成員函式:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

如需`COleDateTime`值界限的詳細資訊, 請參閱文章[日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#11](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_14.cpp)]

##  <a name="setdatetime"></a>COleDateTime:: SetDateTime

設定這個`COleDateTime`物件的日期和時間。

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

*nYear*、 *nMonth*、 *nDay*、 *nHour*、 *n 每天下限*、 *nSec*<br/>
指出要複製到這個`COleDateTime`物件的日期和時間元件。

### <a name="return-value"></a>傳回值

如果已成功設定這個`COleDateTime`物件的值, 則為零, 否則為1。 這個傳回值是以`DateTimeStatus`列舉型別為基礎。 如需詳細資訊, 請參閱[SetStatus](#setstatus)成員函式。

### <a name="remarks"></a>備註

請參閱下表以取得參數值的界限:

|參數|超出|
|---------------|------------|
|*nYear*|100 - 9999|
|*nMonth*|1 - 12|
|*nDay*|0 - 31|
|*nHour*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

如果月份的日溢位, 則會將它轉換成下個月的正確日, 而月份和/或年份會相應增加。 日期值為零表示上個月的最後一天。 行為與[SystemTimeToVariantTime](/windows/win32/api/oleauto/nf-oleauto-systemtimetovarianttime)相同。

如果參數所指定的日期或時間值無效, 則此物件的狀態會設定為無效, 而且這個物件的值不會變更。

以下是一些時間值的範例:

|*nHour*|*nMin*|*nSec*|值|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|無效|
|9|60|0|無效|

以下是一些日期值的範例:

|*nYear*|*nMonth*|*nDay*|值|
|-------------|--------------|------------|-----------|
|1995|4|15|1995年4月15日|
|1789|7|14|1789年7月17日|
|1925|2|30|無效|
|10000|1|1|無效|

若只要設定日期, 請參閱[COleDateTime:: SetDate](#setdate)。 若只要設定時間, 請參閱[COleDateTime:: SetTime](#settime)。

如需查詢此`COleDateTime`物件值之成員函式的詳細資訊, 請參閱下列成員函式:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

如需`COleDateTime`值界限的詳細資訊, 請參閱文章[日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

### <a name="example"></a>範例

請參閱[GetStatus](#getstatus)的範例。

##  <a name="setstatus"></a>COleDateTime:: SetStatus

設定這個`COleDateTime`物件的狀態。

```
void SetStatus(DateTimeStatus status) throw();
```

### <a name="parameters"></a>參數

*status*<br/>
這個`COleDateTime`物件的新狀態值。

### <a name="remarks"></a>備註

*狀態*參數值是由`DateTimeStatus`列舉型別所定義, 此類型定義于`COleDateTime`類別內。 如需詳細資訊, 請參閱[COleDateTime:: GetStatus](#getstatus) 。

> [!CAUTION]
>  這個函數適用于先進的程式設計情況。 此函式不會改變這個物件中的資料。 最常用來將狀態設定為**null**或**無效**。 指派運算子 ([operator =](#operator_eq)) 和[SetDateTime](#setdatetime)會根據來源值來設定物件的狀態。

### <a name="example"></a>範例

請參閱[GetStatus](#getstatus)的範例。

##  <a name="settime"></a>COleDateTime:: SetTime

設定這個`COleDateTime`物件的時間。

```
int SetTime(
    int nHour,
    int nMin,
    int nSec) throw();
```

### <a name="parameters"></a>參數

*nHour*、 *n 每天下限*、 *nSec*<br/>
指出要複製到這個`COleDateTime`物件的時間元件。

### <a name="return-value"></a>傳回值

如果已成功設定這個`COleDateTime`物件的值, 則為零, 否則為1。 這個傳回值是以`DateTimeStatus`列舉型別為基礎。 如需詳細資訊, 請參閱[SetStatus](#setstatus)成員函式。

### <a name="remarks"></a>備註

時間會設定為指定的值。 日期會設定為日期 0, 表示1899年12月30日。

請參閱下表以取得參數值的界限:

|參數|超出|
|---------------|------------|
|*nHour*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

如果參數指定的時間值無效, 則此物件的狀態會設定為無效, 而且這個物件的值不會變更。

以下是一些時間值的範例:

|*nHour*|*nMin*|*nSec*|值|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|無效|
|9|60|0|無效|

若要設定日期和時間, 請參閱[COleDateTime:: SetDateTime](#setdatetime)。

如需查詢此`COleDateTime`物件值之成員函式的詳細資訊, 請參閱下列成員函式:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

如需`COleDateTime`值界限的詳細資訊, 請參閱文章[日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

### <a name="example"></a>範例

請參閱[SetDate](#setdate)的範例。

## <a name="see-also"></a>另請參閱

[COleVariant 類別](../../mfc/reference/colevariant-class.md)<br/>
[CTime 類別](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan 類別](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)
