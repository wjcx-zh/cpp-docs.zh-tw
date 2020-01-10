---
title: CTime 類別
ms.date: 10/18/2018
f1_keywords:
- CTime
- ATLTIME/ATL::CTime
- ATLTIME/ATL::CTime::CTime
- ATLTIME/ATL::CTime::Format
- ATLTIME/ATL::CTime::FormatGmt
- ATLTIME/ATL::CTime::GetAsDBTIMESTAMP
- ATLTIME/ATL::CTime::GetAsSystemTime
- ATLTIME/ATL::CTime::GetCurrentTime
- ATLTIME/ATL::CTime::GetDay
- ATLTIME/ATL::CTime::GetDayOfWeek
- ATLTIME/ATL::CTime::GetGmtTm
- ATLTIME/ATL::CTime::GetHour
- ATLTIME/ATL::CTime::GetLocalTm
- ATLTIME/ATL::CTime::GetMinute
- ATLTIME/ATL::CTime::GetMonth
- ATLTIME/ATL::CTime::GetSecond
- ATLTIME/ATL::CTime::GetTime
- ATLTIME/ATL::CTime::GetYear
- ATLTIME/ATL::CTime::Serialize64
helpviewer_keywords:
- CTime class
- shared classes, CTime
ms.assetid: 0a299544-485b-48dc-9d3c-fdc30f57d612
ms.openlocfilehash: daf2a0d884a6b7a74b5edde2ed7db3b6aeea368d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491579"
---
# <a name="ctime-class"></a>CTime 類別

代表絕對時間和日期。

## <a name="syntax"></a>語法

```
class CTime
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CTime：： CTime](#ctime)|以`CTime`各種方式來構造物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CTime::Format](#format)|根據當地時區，將物件轉換成格式化字串。`CTime`|
|[CTime::FormatGmt](#formatgmt)|`CTime`將物件轉換成格式化字串，以 UTC 為基礎。|
|[CTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|將儲存在`CTime`物件中的時間資訊，轉換為 Win32 相容的 DBTIMESTAMP 結構。|
|[CTime::GetAsSystemTime](#getassystemtime)|將儲存在`CTime`物件中的時間資訊，轉換為 Win32 相容的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構。|
|[CTime::GetCurrentTime](#getcurrenttime)|`CTime`建立物件，代表目前的時間（靜態成員函式）。|
|[CTime::GetDay](#getday)|傳回`CTime`物件所代表的日期。|
|[CTime::GetDayOfWeek](#getdayofweek)|傳回`CTime`物件所表示的一周的第幾天。|
|[CTime::GetGmtTm](#getgmttm)|將物件分解`CTime`成元件，以 UTC 為基礎。|
|[CTime::GetHour](#gethour)|傳回`CTime`物件所表示的小時。|
|[CTime::GetLocalTm](#getlocaltm)|根據當地時區，將物件細分為元件。`CTime`|
|[CTime：： GetMinute](#getminute)|傳回`CTime`物件所表示的分鐘數。|
|[CTime::GetMonth](#getmonth)|傳回`CTime`物件所表示的月份。|
|[CTime::GetSecond](#getsecond)|傳回`CTime`物件所表示的第二個。|
|[CTime::GetTime](#gettime)|傳回給定 `CTime`物件的 __time64_t 值。|
|[CTime：： GetYear](#getyear)|傳回`CTime`物件所表示的年份。|
|[CTime::Serialize64](#serialize64)|將資料序列化至封存或從中封存。|

### <a name="operators"></a>運算子

|||
|-|-|
|[operator +-](#operator_add_-)|這些運算子會加入和`CTimeSpan`減去`CTime`和物件。|
|[operator +=, -=](#operator_add_eq_-_eq)|這些運算子會在`CTimeSpan`物件中加入和減去物件。 `CTime`|
|[operator =](#operator_eq)|指派運算子。|
|[operator = =、< 等。](#ctime_comparison_operators)|比較運算子。|

## <a name="remarks"></a>備註

`CTime`沒有基類。

`CTime`值是以國際標準時間（UTC）為基礎，相當於國際標準時間（格林威治標準時間，GMT）。 如需如何決定時區的詳細資訊，請參閱[時間管理](../../c-runtime-library/time-management.md)。

當您建立`CTime`物件時，請`nDST`將參數設定為0，以指出標準時間有效，或大於0的值表示日光節約時間有效，或小於零的值，以使用 C 執行時間程式庫程式碼電腦e 標準時間或日光節約時間是否有效。 `tm_isdst` 是必要的欄位。 如果未設定，則其值為未定義，且來自[mktime](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)的傳回值無法預測。 如果`timeptr`指向先前呼叫[asctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)、 [_gmtime_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)或[localtime_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md) `tm_isdst`所傳回的 tm 結構，欄位會包含正確的值。

隨附類別[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)代表時間間隔。

`CTime` 和`CTimeSpan`類別不是針對衍生而設計的。 由於沒有虛擬函式， `CTime`和`CTimeSpan`物件的大小正好為8個位元組。 大部分的成員函式是內嵌的。

> [!NOTE]
>  日期上限為12/31/3000。 較低的限制是 1/1/1970 12:00:00 AM GMT。

如需有關使用`CTime`的詳細資訊，請參閱《執行時間程式庫參考》中的文章[日期和時間](../../atl-mfc-shared/date-and-time.md)和[時間管理](../../c-runtime-library/time-management.md)。

> [!NOTE]
>  `CTime`結構從 mfc 7.1 變更為 mfc 8.0。 如果您使用運算子`CTime`來序列化結構 < 在 mfc 8.0 或更新版本下 **<** ，產生的檔案將無法在較舊版本的 mfc 上讀取。

## <a name="requirements"></a>需求

**標頭：** atltime。h

##  <a name="ctime_comparison_operators"></a>CTime 比較運算子

比較運算子。

```
bool operator==(CTime time) const throw();
bool operator!=(CTime time) const throw();
bool operator<(CTime time) const throw();
bool operator>(CTime time) const throw();
bool operator<=(CTime time) const throw();
bool operator>=(CTime time) const throw();
```

### <a name="parameters"></a>參數

*time*<br/>
要比較的 `CTime` 物件。

### <a name="return-value"></a>傳回值

這些運算子會比較兩個絕對時間，如果條件為 true，則傳回 TRUE;否則為 FALSE。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#161](../../atl-mfc-shared/codesnippet/cpp/ctime-class_1.cpp)]

##  <a name="ctime"></a>CTime：： CTime

建立以指定`CTime`的時間初始化的新物件。

```
CTime() throw();
CTime(__time64_t time) throw();
CTime(int nYear, int nMonth, int nDay,
      int nHour, int nMin, int nSec, int nDST = -1);
CTime(WORD wDosDate, WORD wDosTime, int nDST = -1);
CTime(const SYSTEMTIME& st, int nDST = - 1) throw();
CTime(const FILETIME& ft, int nDST = - 1);
CTime(const DBTIMESTAMP& dbts, int nDST = -1) throw();
```

### <a name="parameters"></a>參數

*timeSrc*<br/>
表示已存在的物件。`CTime`

*time*<br/>
`__time64_t`時間值，這是1970年1月1日之後的秒數。 請注意，這將會調整為您的當地時間。 例如，如果您在紐約，並藉由傳遞參數`CTime` 0 來建立物件，則[CTime：： GetMonth](#getmonth)會傳回12。

*nYear*、 *nMonth*、 *nDay*、 *nHour*、 *n 每天下限*、 *nSec*<br/>
表示要複製到新`CTime`物件中的日期和時間值。

*nDST*<br/>
指出日光節約時間是否有效。 可以有下列三個值的其中一個：

- *nDST*設定為 0Standard time 已生效。

- *nDST*設定為大於0Daylight 節約時間的值生效。

- *nDST*設定為小於0The 預設值。 自動計算標準時間或日光節約時間是否有效。

*wDosDate*、 *wDosTime*<br/>
要轉換成日期/時間值並複製到新`CTime`物件的 MS-DOS 日期和時間值。

*st*<br/>
要轉換成日期/時間值並複製到新`CTime`物件的 [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) 結構。

*ft*<br/>
要轉換成日期/時間值並複製到新`CTime`物件的 [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) 結構。

*dbts*<br/>
DBTIMESTAMP 結構的參考，其中包含目前的本地時間。

### <a name="remarks"></a>備註

每個函數描述如下：

- `CTime();`構造未初始化`CTime`的物件。 這個函數可讓您定義`CTime`物件陣列。 在使用之前，您應該使用有效的時間來初始化這類陣列。

- `CTime( const CTime& );`從另一個`CTime`值來構造物件。`CTime`

- `CTime( __time64_t );`從 __time64_t `CTime`類型中，建立物件。 此函式需要 UTC 時間，並將結果轉換為本機時間，然後再儲存結果。

- `CTime( int, int, ...);`從當地`CTime`時間元件中，將每個元件都限制為下列範圍的物件：

   |元件|Range|
   |---------------|-----------|
   |*nYear*|1970-3000|
   |*nMonth*|1-12|
   |*nDay*|1-31|
   |*nHour*|0-23|
   |*nMin*|0-59|
   |*nSec*|0-59|

   此函式會對 UTC 進行適當的轉換。 如果一或多個時間元件超出範圍，MFC 程式庫的 Debug 版本會判斷提示。 您必須先驗證引數，再呼叫。 此函式需要當地時間。

- `CTime( WORD, WORD );`從指定的 MS-DOS 日期和時間值來構造物件。`CTime` 此函式需要當地時間。

- `CTime( const SYSTEMTIME& );`從結構中構造`CTime`物件 `SYSTEMTIME` 。 此函式需要當地時間。

- `CTime( const FILETIME& );`從結構中構造`CTime`物件 `FILETIME` 。 您很可能不會直接`CTime FILETIME`使用初始化。 如果您`CFile`使用物件來操作檔案，請透過`CFile::GetStatus`以`FILETIME`結構初始化的`CTime`物件，抓取檔案時間戳記。 此函式會根據 UTC 來假設時間，並自動將值轉換成當地時間，然後再儲存結果。

   > [!NOTE]
   > 只有當包含`DBTIMESTAMP`了 OLEDB 時，才可以使用參數的函式。

如需詳細資訊，請參閱 Windows SDK 中的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)和[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)結構。 另請參閱 Windows SDK 中的[MS-DOS 日期和時間](/windows/win32/SysInfo/ms-dos-date-and-time)專案。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#148](../../atl-mfc-shared/codesnippet/cpp/ctime-class_2.cpp)]

##  <a name="format"></a>CTime：： Format

呼叫這個成員函式，以建立日期時間值的格式化表示。

```
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>參數

*pszFormat*<br/>
格式化字串，類似`printf`于格式字串。 格式化程式碼（前面加上百分比`%`（）符號）會由對應`CTime`的元件所取代。 格式字串中的其他字元會原封不動地複製到傳回的字串。 如需格式化程式碼的清單，請參閱執行時間函式[strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) 。

*nFormatID*<br/>
識別此格式之字串的識別碼。

### <a name="return-value"></a>傳回值

包含格式化時間的[CString](../../atl-mfc-shared/reference/cstringt-class.md) 。

### <a name="remarks"></a>備註

如果這個`CTime`物件的狀態是 null，則傳回值是空字串。

如果要格式化的日期時間值不是從1970年1月1日午夜到3000國際標準時間（UTC），這個方法就會擲回例外狀況。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#149](../../atl-mfc-shared/codesnippet/cpp/ctime-class_3.cpp)]

##  <a name="formatgmt"></a>CTime：： FormatGmt

產生對應于這個`CTime`物件的格式化字串。

```
CString FormatGmt(LPCTSTR pszFormat) const;
CString FormatGmt(UINT nFormatID) const;
```

### <a name="parameters"></a>參數

*pszFormat*<br/>
指定格式字串，類似`printf`于格式字串。 如需詳細資訊，請參閱執行時間函式[strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) 。

*nFormatID*<br/>
識別此格式之字串的識別碼。

### <a name="return-value"></a>傳回值

包含格式化時間的[CString](../../atl-mfc-shared/reference/cstringt-class.md) 。

### <a name="remarks"></a>備註

時間值不會轉換，因此會反映 UTC。

如果要格式化的日期時間值不是從1970年1月1日午夜到3000國際標準時間（UTC），這個方法就會擲回例外狀況。

### <a name="example"></a>範例

請參閱[CTime：： Format](#format)的範例。

##  <a name="getasdbtimestamp"></a>CTime：： GetAsDBTIMESTAMP

呼叫這個成員函式，將儲存在`CTime`物件中的時間資訊轉換成與 Win32 相容的 DBTIMESTAMP 結構。

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```

### <a name="parameters"></a>參數

*dbts*<br/>
DBTIMESTAMP 結構的參考，其中包含目前的本地時間。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

將產生的時間儲存在參考的*dbts*結構中。 此`DBTIMESTAMP`函式所初始化的資料結構會將`fraction`其成員設定為零。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#150](../../atl-mfc-shared/codesnippet/cpp/ctime-class_4.cpp)]

##  <a name="getassystemtime"></a>CTime：： GetAsSystemTime

呼叫這個成員函式，將儲存在`CTime`物件中的時間資訊轉換成與 Win32 相容的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構。

```
bool GetAsSystemTime(SYSTEMTIME& st) const throw();
```

### <a name="parameters"></a>參數

*timeDest*<br/>
[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的參考，將會保存`CTime`物件的已轉換日期/時間值。

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

`GetAsSystemTime`將產生的時間儲存在參考的*timeDest*結構中。 此`SYSTEMTIME`函式所初始化的資料結構會將`wMilliseconds`其成員設定為零。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#151](../../atl-mfc-shared/codesnippet/cpp/ctime-class_5.cpp)]

##  <a name="getcurrenttime"></a>CTime：： GetCurrentTime

傳回表示目前時間的物件。`CTime`

```
static CTime WINAPI GetCurrentTime() throw();
```

### <a name="remarks"></a>備註

以國際標準時間（UTC）傳回目前的系統日期和時間。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#152](../../atl-mfc-shared/codesnippet/cpp/ctime-class_6.cpp)]

##  <a name="getday"></a>CTime：： GetDay

傳回`CTime`物件所代表的日期。

```
int GetDay() const throw();
```

### <a name="return-value"></a>傳回值

傳回以本地時間為基礎的月份日，範圍介於1到31之間。

### <a name="remarks"></a>備註

此函式`GetLocalTm`會呼叫，它會使用內部靜態配置的緩衝區。 因為呼叫其他`CTime`成員函式，所以會覆寫這個緩衝區中的資料。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#153](../../atl-mfc-shared/codesnippet/cpp/ctime-class_7.cpp)]

##  <a name="getdayofweek"></a>CTime：： GetDayOfWeek

傳回`CTime`物件所表示的一周的第幾天。

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>傳回值

傳回以當地時間為基礎的星期日期;1 = 星期日、2 = 星期一、7 = 星期六。

### <a name="remarks"></a>備註

此函式`GetLocalTm`會呼叫，它會使用內部靜態配置的緩衝區。 因為呼叫其他`CTime`成員函式，所以會覆寫這個緩衝區中的資料。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#154](../../atl-mfc-shared/codesnippet/cpp/ctime-class_8.cpp)]

##  <a name="getgmttm"></a>CTime：： GetGmtTm

取得**結構 tm** ，其中包含此`CTime`物件中包含的時間分解。

```
struct tm* GetGmtTm(struct tm* ptm) const;
```

### <a name="parameters"></a>參數

*ptm*<br/>
指向將會接收時間資料的緩衝區。 如果此指標為 Null，則會擲回例外狀況。

### <a name="return-value"></a>傳回值

包含檔案時間中所定義之實心**結構 tm**的指標。H. 如需結構配置，請參閱[gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) 。

### <a name="remarks"></a>備註

`GetGmtTm`傳回 UTC。

*ptm*不可以是 Null。 如果您想要還原成舊的行為，在此情況下， *ptm*可能會是 Null，表示應該使用內部靜態配置的緩衝區，然後取消定義 _SECURE_ATL。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#155](../../atl-mfc-shared/codesnippet/cpp/ctime-class_9.cpp)]

##  <a name="gethour"></a>CTime：： GetHour

傳回`CTime`物件所表示的小時。

```
int GetHour() const throw();
```

### <a name="return-value"></a>傳回值

根據當地時間傳回小時，範圍介於0到23之間。

### <a name="remarks"></a>備註

此函式`GetLocalTm`會呼叫，它會使用內部靜態配置的緩衝區。 因為呼叫其他`CTime`成員函式，所以會覆寫這個緩衝區中的資料。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#156](../../atl-mfc-shared/codesnippet/cpp/ctime-class_10.cpp)]

##  <a name="getlocaltm"></a>CTime：： GetLocalTm

取得**結構 tm** ，其中包含此`CTime`物件中包含的時間分解。

```
struct tm* GetLocalTm(struct tm* ptm) const;
```

### <a name="parameters"></a>參數

*ptm*<br/>
指向將會接收時間資料的緩衝區。 如果此指標為 Null，則會擲回例外狀況。

### <a name="return-value"></a>傳回值

包含檔案時間中所定義之實心**結構 tm**的指標。H. 如需結構配置，請參閱[gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) 。

### <a name="remarks"></a>備註

`GetLocalTm`傳回本地時間。

*ptm*不可以是 Null。 如果您想要還原成舊的行為，在此情況下， *ptm*可能會是 Null，表示應該使用內部靜態配置的緩衝區，然後取消定義 _SECURE_ATL。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#157](../../atl-mfc-shared/codesnippet/cpp/ctime-class_11.cpp)]

##  <a name="getminute"></a>CTime：： GetMinute

傳回`CTime`物件所表示的分鐘數。

```
int GetMinute() const throw();
```

### <a name="return-value"></a>傳回值

根據當地時間傳回分鐘，範圍介於0到59之間。

### <a name="remarks"></a>備註

此函式`GetLocalTm`會呼叫，它會使用內部靜態配置的緩衝區。 因為呼叫其他`CTime`成員函式，所以會覆寫這個緩衝區中的資料。

### <a name="example"></a>範例

請參閱[GetHour](#gethour)的範例。

##  <a name="getmonth"></a>CTime：： GetMonth

傳回`CTime`物件所表示的月份。

```
int GetMonth() const throw();
```

### <a name="return-value"></a>傳回值

傳回以本地時間為基礎的月份，範圍介於1到12之間（1 = 一月）。

### <a name="remarks"></a>備註

此函式`GetLocalTm`會呼叫，它會使用內部靜態配置的緩衝區。 因為呼叫其他`CTime`成員函式，所以會覆寫這個緩衝區中的資料。

### <a name="example"></a>範例

請參閱[GetDay](#getday)的範例。

##  <a name="getsecond"></a>CTime：： GetSecond

傳回`CTime`物件所表示的第二個。

```
int GetSecond() const throw();
```

### <a name="return-value"></a>傳回值

根據本地時間傳回第二個，範圍介於0到59之間。

### <a name="remarks"></a>備註

此函式`GetLocalTm`會呼叫，它會使用內部靜態配置的緩衝區。 因為呼叫其他`CTime`成員函式，所以會覆寫這個緩衝區中的資料。

### <a name="example"></a>範例

請參閱[GetHour](#gethour)的範例。

##  <a name="gettime"></a>CTime：： GetTime

傳回給定 `CTime`物件的 __time64_t 值。

```
__time64_t GetTime() const throw();
```

### <a name="return-value"></a>傳回值

`GetTime`會傳回目前`CTime`物件與1970年1月1日之間的秒數。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#158](../../atl-mfc-shared/codesnippet/cpp/ctime-class_12.cpp)]

##  <a name="getyear"></a>CTime：： GetYear

傳回`CTime`物件所表示的年份。

```
int GetYear();
```

### <a name="return-value"></a>傳回值

根據當地時間傳回年份，範圍介於1970年1月1日至2038年1月18日（含）之間。

### <a name="remarks"></a>備註

此函式`GetLocalTm`會呼叫，它會使用內部靜態配置的緩衝區。 因為呼叫其他`CTime`成員函式，所以會覆寫這個緩衝區中的資料。

### <a name="example"></a>範例

請參閱[GetDay](#getday)的範例。

##  <a name="operator_eq"></a>CTime：： operator =

指派運算子。

```
CTime& operator=(__time64_t time) throw();
```

### <a name="parameters"></a>參數

*time*<br/>
新的日期/時間值。

### <a name="return-value"></a>傳回值

已更新`CTime`的物件。

### <a name="remarks"></a>備註

這個多載指派運算子會將來源時間複製`CTime`到這個物件。 `CTime`物件中的內部時間儲存體與時區無關。 指派期間並不需要時區轉換。

##  <a name="operator_add_-"></a>CTime：： operator +、-

這些運算子會加入和`CTimeSpan`減去`CTime`和物件。

```
CTime operator+(CTimeSpan timeSpan) const throw();
CTime operator-(CTimeSpan timeSpan) const throw();
CTimeSpan operator-(CTime time) const throw();
```

### <a name="parameters"></a>參數

*timeSpan*<br/>
要`CTimeSpan`新增或減去的物件。

*time*<br/>
要`CTime`減去的物件。

### <a name="return-value"></a>傳回值

`CTime` 或`CTimeSpan`物件，表示運算的結果。

### <a name="remarks"></a>備註

`CTime`物件代表絕對時間， `CTimeSpan`物件代表相對時間。 前兩個運算子可讓您在物件之間`CTimeSpan` `CTime`加入和減去物件。 第三個運算子可讓您從`CTime`另一個物件減去一個物件`CTimeSpan` ，以產生物件。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#159](../../atl-mfc-shared/codesnippet/cpp/ctime-class_13.cpp)]

##  <a name="operator_add_eq_-_eq"></a>CTime：： operator + =、-=

這些運算子會在`CTimeSpan`物件中加入和減去物件。 `CTime`

```
CTime& operator+=(CTimeSpan span) throw();
CTime& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>參數

*span*<br/>
要`CTimeSpan`新增或減去的物件。

### <a name="return-value"></a>傳回值

已更新`CTime`的物件。

### <a name="remarks"></a>備註

這些運算子可讓您在此`CTimeSpan` `CTime`物件之間加入和減去物件。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#160](../../atl-mfc-shared/codesnippet/cpp/ctime-class_14.cpp)]

##  <a name="serialize64"></a>CTime：： Serialize64

> [!NOTE]
> 這個方法僅適用于 MFC 專案。

將與成員變數相關聯的資料，從封存中序列化。

```
CArchive& Serialize64(CArchive& ar);
```

### <a name="parameters"></a>參數

*ar*<br/>
您`CArchive`想要更新的物件。

### <a name="return-value"></a>傳回值

已更新`CArchive`的物件。

## <a name="see-also"></a>另請參閱

[asctime_s、_wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)<br/>
[_ftime_s、_ftime32_s、_ftime64_s](../../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)<br/>
[gmtime_s、_gmtime32_s、_gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s、_localtime32_s、_localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)<br/>
[strftime、wcsftime、_strftime_l、_wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[CTimeSpan 類別](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)
