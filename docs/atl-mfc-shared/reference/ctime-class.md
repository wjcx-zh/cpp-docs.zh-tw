---
title: CTime 類別
ms.date: 10/18/2018
f1_keywords:
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
ms.openlocfilehash: d551698a81921227dd0d7b7d80436bba960ed176
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832031"
---
# <a name="ctime-class"></a>CTime 類別

表示絕對時間和日期。

## <a name="syntax"></a>語法

```
class CTime
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CTime：： CTime](#ctime)|`CTime`以各種方式來結構物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CTime：： Format](#format)|`CTime`根據當地時區，將物件轉換成格式化的字串。|
|[CTime：： FormatGmt](#formatgmt)|`CTime`根據 UTC，將物件轉換成格式化的字串。|
|[CTime：： GetAsDBTIMESTAMP](#getasdbtimestamp)|將儲存在物件中的時間資訊轉換 `CTime` 成與 Win32 相容的 DBTIMESTAMP 結構。|
|[CTime：： GetAsSystemTime](#getassystemtime)|將儲存在物件中的時間資訊轉換 `CTime` 成與 Win32 相容的 [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) 結構。|
|[CTime：： GetCurrentTime](#getcurrenttime)|建立 `CTime` 物件，這個物件表示 (靜態成員函式) 的目前時間。|
|[CTime：： GetDay](#getday)|傳回物件代表的日 `CTime` 。|
|[CTime：： GetDayOfWeek](#getdayofweek)|傳回物件所表示之周中的日 `CTime` 。|
|[CTime：： GetGmtTm](#getgmttm)|將物件細分 `CTime` 為元件，以 UTC 為基礎。|
|[CTime：： GetHour](#gethour)|傳回物件所表示的小時 `CTime` 。|
|[CTime：： GetLocalTm](#getlocaltm)|`CTime`根據當地時區，將物件細分為元件。|
|[CTime：： GetMinute](#getminute)|傳回物件所表示的分鐘 `CTime` 。|
|[CTime：： GetMonth](#getmonth)|傳回物件所代表的月份 `CTime` 。|
|[CTime：： GetSecond](#getsecond)|傳回物件所表示的第二個 `CTime` 。|
|[CTime：： GetTime](#gettime)|傳回指定物件的 **__time64_t** 值 `CTime` 。|
|[CTime：： GetYear](#getyear)|傳回物件所表示的年份 `CTime` 。|
|[CTime：： Serialize64](#serialize64)|序列化封存的資料。|

### <a name="operators"></a>運算子

|名稱|描述|
|-|-|
|[運算子 +-](#operator_add_-)|這些運算子會新增及減去 `CTimeSpan` 和 `CTime` 物件。|
|[operator + =、-=](#operator_add_eq_-_eq)|這些運算子會在 `CTimeSpan` 此物件中加入和減去物件 `CTime` 。|
|[運算子 =](#operator_eq)|指派運算子。|
|[operator = =、< 等等。](#ctime_comparison_operators)|比較運算子。|

## <a name="remarks"></a>備註

`CTime` 沒有基類。

`CTime` 值是根據國際標準時間 (UTC) ，相當於國際標準時間 (格林威治標準時間（GMT）) 。 請參閱 [時間管理](../../c-runtime-library/time-management.md) 以取得時區判斷方式的相關資訊。

當您建立 `CTime` 物件時，請將 `nDST` 參數設定為0以表示標準時間有效，或設為大於0的值以表示日光節約時間有效，或小於零的值，讓 C 執行時間程式庫程式碼計算標準時間或日光節約時間是否生效。 `tm_isdst` 是必要的欄位。 如果未設定，則其值為未定義，而且 [mktime](../../c-runtime-library/reference/mktime-mktime32-mktime64.md) 的傳回值是無法預期的。 如果 `timeptr` 指向先前呼叫所傳回的 tm 結構 [asctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)、 [_gmtime_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)或 [localtime_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)，則 `tm_isdst` 欄位會包含正確的值。

隨附類別 [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)代表時間間隔。

`CTime`和 `CTimeSpan` 類別並非針對衍生而設計。 因為沒有虛擬函式，所以 `CTime` 和物件的大小 `CTimeSpan` 正好是8個位元組。 大部分的成員函式都是內嵌的。

> [!NOTE]
> 日期上限為12/31/3000。 較低的限制為 1/1/1970 12:00:00 AM GMT。

如需使用的詳細資訊 `CTime` ，請參閱《執行時間程式庫參考》中的文章 [日期和時間](../../atl-mfc-shared/date-and-time.md)以及 [時間管理](../../c-runtime-library/time-management.md) 。

> [!NOTE]
> `CTime`結構已從 mfc 7.1 變更為 mfc 8.0。 如果您 `CTime` 使用 **運算子 <<** 在 mfc 8.0 或更新版本下序列化結構，則在舊版的 mfc 上將無法讀取產生的檔案。

## <a name="requirements"></a>規格需求

**標頭：** atltime。h

## <a name="ctime-comparison-operators"></a><a name="ctime_comparison_operators"></a> CTime 比較運算子

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

這些運算子會比較兩次的絕對時間，並在條件為 true 時傳回 TRUE。否則為 FALSE。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#161](../../atl-mfc-shared/codesnippet/cpp/ctime-class_1.cpp)]

## <a name="ctimectime"></a><a name="ctime"></a> CTime：： CTime

建立 `CTime` 以指定的時間初始化的新物件。

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
表示 `CTime` 已經存在的物件。

*time*<br/>
`__time64_t`時間值，這是1970年1月1日之後的秒數。 請注意，這會調整為您的當地時間。 例如，如果您在紐約，並藉 `CTime` 由傳遞參數0來建立物件，則 [CTime：： GetMonth](#getmonth) 會傳回12。

*nYear*、 *nMonth*、 *nDay*、 *nHour*、 *n 每天下限*、 *nSec*<br/>
表示要複製到新物件中的日期和時間值 `CTime` 。

*nDST*<br/>
指出日光節約時間是否生效。 可以有三個值的其中一個：

- *nDST* 設定為 0Standard time 生效。

- *nDST* 設定為大於0Daylight 節約時間的值生效。

- *nDST* 設定為小於0The 的預設值。 自動計算標準時間或日光節約時間是否生效。

*wDosDate*、 *wDosTime*<br/>
要轉換成日期/時間值並複製到新物件的 MS-DOS 日期和時間值 `CTime` 。

*聖*<br/>
要轉換成日期/時間值的 [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) 結構，並複製到新的 `CTime` 物件。

*英尺*<br/>
要轉換成日期/時間值並複製到新物件的 [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) 結構 `CTime` 。

*dbts*<br/>
DBTIMESTAMP 結構的參考，其中包含目前的當地時間。

### <a name="remarks"></a>備註

以下說明每個函式：

- `CTime();` 結構未初始化的 `CTime` 物件。 這個函式可讓您定義 `CTime` 物件陣列。 在使用之前，您應該將這類陣列初始化為有效的時間。

- `CTime( const CTime& );``CTime`從另一個值中建立物件 `CTime` 。

- `CTime( __time64_t );``CTime`從 **__time64_t**類型中建立物件。 這個函式需要 UTC 時間，並將結果轉換成當地時間，然後再儲存結果。

- `CTime( int, int, ...);``CTime`從本機時間元件中，建立每個元件受限於下列範圍的物件：

   |元件|範圍|
   |---------------|-----------|
   |*nYear*|1970-3000|
   |*nMonth*|1-12|
   |*nDay*|1-31|
   |*nHour*|0-23|
   |*N 每天下限*|0-59|
   |*nSec*|0-59|

   這個函式會將適當轉換為 UTC。 如果有一或多個時間元件超出範圍，則為 MFC 程式庫判斷提示的偵錯工具版本。 在呼叫之前，您必須先驗證引數。 這個函式需要當地時間。

- `CTime( WORD, WORD );``CTime`從指定的 MS-DOS 日期和時間值來建立物件。 這個函式需要當地時間。

- `CTime( const SYSTEMTIME& );``CTime`從結構中結構的物件 `SYSTEMTIME` 。 這個函式需要當地時間。

- `CTime( const FILETIME& );``CTime`從結構中結構的物件 `FILETIME` 。 您很可能不會 `CTime FILETIME` 直接使用初始化。 如果您使用 `CFile` 物件來操作檔案，則 `CFile::GetStatus` 會透過以結構初始化的物件來為您抓取檔案時間戳記 `CTime` `FILETIME` 。 這個函式會假設以 UTC 為基礎的時間，並會在儲存結果之前，自動將值轉換為當地時間。

   > [!NOTE]
   > 使用參數的函式 `DBTIMESTAMP` 只有在包含 OLEDB 時才可使用。

如需詳細資訊，請參閱 Windows SDK 中的 [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) 和 [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) 結構。 另請參閱 Windows SDK 中的 [MS-DOS 日期和時間](/windows/win32/SysInfo/ms-dos-date-and-time) 專案。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#148](../../atl-mfc-shared/codesnippet/cpp/ctime-class_2.cpp)]

## <a name="ctimeformat"></a><a name="format"></a> CTime：： Format

呼叫此成員函式，以建立日期時間值的格式化表示。

```
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>參數

*pszFormat*<br/>
格式化字串，類似于 `printf` 格式化字串。 格式化程式碼（前面加上% (`%`) 號）會取代為對應的 `CTime` 元件。 格式化字串中的其他字元會原封不動地複製到傳回的字串。 如需格式化程式碼的清單，請參閱執行時間函數 [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) 。

*nFormatID*<br/>
識別此格式之字串的識別碼。

### <a name="return-value"></a>傳回值

包含格式化時間的 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 。

### <a name="remarks"></a>備註

如果此物件的狀態 `CTime` 為 null，則傳回值為空字串。

如果要格式化的日期時間值範圍不是從1970年1月1日午夜到3000全球協調時間 (UTC) ，此方法會擲回例外狀況。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#149](../../atl-mfc-shared/codesnippet/cpp/ctime-class_3.cpp)]

## <a name="ctimeformatgmt"></a><a name="formatgmt"></a> CTime：： FormatGmt

產生對應于這個物件的格式化字串 `CTime` 。

```
CString FormatGmt(LPCTSTR pszFormat) const;
CString FormatGmt(UINT nFormatID) const;
```

### <a name="parameters"></a>參數

*pszFormat*<br/>
指定類似于格式化字串的格式字串 `printf` 。 如需詳細資訊，請參閱執行時間函數 [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) 。

*nFormatID*<br/>
識別此格式之字串的識別碼。

### <a name="return-value"></a>傳回值

包含格式化時間的 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 。

### <a name="remarks"></a>備註

時間值不會轉換，因此會反映 UTC。

如果要格式化的日期時間值範圍不是從1970年1月1日午夜到3000全球協調時間 (UTC) ，此方法會擲回例外狀況。

### <a name="example"></a>範例

請參閱 [CTime：： Format](#format)的範例。

## <a name="ctimegetasdbtimestamp"></a><a name="getasdbtimestamp"></a> CTime：： GetAsDBTIMESTAMP

呼叫這個成員函式，將儲存在物件中的時間資訊轉換成與 `CTime` Win32 相容的 DBTIMESTAMP 結構。

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```

### <a name="parameters"></a>參數

*dbts*<br/>
DBTIMESTAMP 結構的參考，其中包含目前的當地時間。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

將產生的時間儲存在參考的 *dbts* 結構中。 `DBTIMESTAMP`此函數初始化的資料結構會將其 `fraction` 成員設定為零。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#150](../../atl-mfc-shared/codesnippet/cpp/ctime-class_4.cpp)]

## <a name="ctimegetassystemtime"></a><a name="getassystemtime"></a> CTime：： GetAsSystemTime

呼叫這個成員函式，將儲存在物件中的時間資訊轉換成與 `CTime` Win32 相容的 [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) 結構。

```
bool GetAsSystemTime(SYSTEMTIME& st) const throw();
```

### <a name="parameters"></a>參數

*timeDest*<br/>
[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的參考，該結構會保存物件的已轉換日期/時間值 `CTime` 。

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

`GetAsSystemTime` 將產生的時間儲存在參考的 *timeDest* 結構中。 `SYSTEMTIME`此函數初始化的資料結構會將其 `wMilliseconds` 成員設定為零。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#151](../../atl-mfc-shared/codesnippet/cpp/ctime-class_5.cpp)]

## <a name="ctimegetcurrenttime"></a><a name="getcurrenttime"></a> CTime：： GetCurrentTime

傳回 `CTime` 代表目前時間的物件。

```
static CTime WINAPI GetCurrentTime() throw();
```

### <a name="remarks"></a>備註

以國際標準時間 (UTC) 傳回目前的系統日期和時間。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#152](../../atl-mfc-shared/codesnippet/cpp/ctime-class_6.cpp)]

## <a name="ctimegetday"></a><a name="getday"></a> CTime：： GetDay

傳回物件代表的日 `CTime` 。

```
int GetDay() const throw();
```

### <a name="return-value"></a>傳回值

根據當地時間，以1到31的範圍傳回月份的日期。

### <a name="remarks"></a>備註

此函式呼叫會 `GetLocalTm` 使用內部靜態配置的緩衝區。 因為呼叫其他成員函式，所以會覆寫這個緩衝區中的資料 `CTime` 。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#153](../../atl-mfc-shared/codesnippet/cpp/ctime-class_7.cpp)]

## <a name="ctimegetdayofweek"></a><a name="getdayofweek"></a> CTime：： GetDayOfWeek

傳回物件所表示之周中的日 `CTime` 。

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>傳回值

傳回以當地時間為基礎的周間日期;1 = 星期日、2 = 星期一、7 = 星期六。

### <a name="remarks"></a>備註

此函式呼叫會 `GetLocalTm` 使用內部靜態配置的緩衝區。 因為呼叫其他成員函式，所以會覆寫這個緩衝區中的資料 `CTime` 。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#154](../../atl-mfc-shared/codesnippet/cpp/ctime-class_8.cpp)]

## <a name="ctimegetgmttm"></a><a name="getgmttm"></a> CTime：： GetGmtTm

取得 **結構 tm** ，其中包含此物件中包含的時間分解 `CTime` 。

```
struct tm* GetGmtTm(struct tm* ptm) const;
```

### <a name="parameters"></a>參數

*ptm*<br/>
指向將接收時間資料的緩衝區。 如果此指標為 Null，則會擲回例外狀況。

### <a name="return-value"></a>傳回值

在包含檔案時間中定義的已填入 **結構 tm** 指標。H。 如需結構配置，請參閱 [gmtime、_gmtime32 _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) 。

### <a name="remarks"></a>備註

`GetGmtTm` 傳回 UTC。

*ptm* 不可為 Null。 如果您想要還原為舊的行為，其中 *ptm* 可以是 Null，表示應該使用內部靜態配置的緩衝區，然後取消定義 _SECURE_ATL。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#155](../../atl-mfc-shared/codesnippet/cpp/ctime-class_9.cpp)]

## <a name="ctimegethour"></a><a name="gethour"></a> CTime：： GetHour

傳回物件所表示的小時 `CTime` 。

```
int GetHour() const throw();
```

### <a name="return-value"></a>傳回值

傳回以當地時間為單位的小時，範圍介於0到23之間。

### <a name="remarks"></a>備註

此函式呼叫會 `GetLocalTm` 使用內部靜態配置的緩衝區。 因為呼叫其他成員函式，所以會覆寫這個緩衝區中的資料 `CTime` 。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#156](../../atl-mfc-shared/codesnippet/cpp/ctime-class_10.cpp)]

## <a name="ctimegetlocaltm"></a><a name="getlocaltm"></a> CTime：： GetLocalTm

取得包含此物件所包含時間分解的 **結構 tm** `CTime` 。

```
struct tm* GetLocalTm(struct tm* ptm) const;
```

### <a name="parameters"></a>參數

*ptm*<br/>
指向將接收時間資料的緩衝區。 如果此指標為 Null，則會擲回例外狀況。

### <a name="return-value"></a>傳回值

在包含檔案時間中定義的已填入 **結構 tm** 指標。H。 如需結構配置，請參閱 [gmtime、_gmtime32 _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) 。

### <a name="remarks"></a>備註

`GetLocalTm` 傳回本地時間。

*ptm* 不可為 Null。 如果您想要還原為舊的行為，其中 *ptm* 可以是 Null，表示應該使用內部靜態配置的緩衝區，然後取消定義 _SECURE_ATL。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#157](../../atl-mfc-shared/codesnippet/cpp/ctime-class_11.cpp)]

## <a name="ctimegetminute"></a><a name="getminute"></a> CTime：： GetMinute

傳回物件所表示的分鐘 `CTime` 。

```
int GetMinute() const throw();
```

### <a name="return-value"></a>傳回值

根據當地時間傳回分鐘，範圍介於0到59之間。

### <a name="remarks"></a>備註

此函式呼叫會 `GetLocalTm` 使用內部靜態配置的緩衝區。 因為呼叫其他成員函式，所以會覆寫這個緩衝區中的資料 `CTime` 。

### <a name="example"></a>範例

請參閱 [GetHour](#gethour)的範例。

## <a name="ctimegetmonth"></a><a name="getmonth"></a> CTime：： GetMonth

傳回物件所代表的月份 `CTime` 。

```
int GetMonth() const throw();
```

### <a name="return-value"></a>傳回值

傳回以當地時間為基礎的月份，範圍從1到 12 (1 = 1 月) 。

### <a name="remarks"></a>備註

此函式呼叫會 `GetLocalTm` 使用內部靜態配置的緩衝區。 因為呼叫其他成員函式，所以會覆寫這個緩衝區中的資料 `CTime` 。

### <a name="example"></a>範例

請參閱 [GetDay](#getday)的範例。

## <a name="ctimegetsecond"></a><a name="getsecond"></a> CTime：： GetSecond

傳回物件所表示的第二個 `CTime` 。

```
int GetSecond() const throw();
```

### <a name="return-value"></a>傳回值

傳回以當地時間為基礎的秒，範圍介於0到59之間。

### <a name="remarks"></a>備註

此函式呼叫會 `GetLocalTm` 使用內部靜態配置的緩衝區。 因為呼叫其他成員函式，所以會覆寫這個緩衝區中的資料 `CTime` 。

### <a name="example"></a>範例

請參閱 [GetHour](#gethour)的範例。

## <a name="ctimegettime"></a><a name="gettime"></a> CTime：： GetTime

傳回指定物件的 **__time64_t** 值 `CTime` 。

```
__time64_t GetTime() const throw();
```

### <a name="return-value"></a>傳回值

`GetTime` 會傳回目前 `CTime` 物件與1970年1月1之間的秒數。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#158](../../atl-mfc-shared/codesnippet/cpp/ctime-class_12.cpp)]

## <a name="ctimegetyear"></a><a name="getyear"></a> CTime：： GetYear

傳回物件所表示的年份 `CTime` 。

```
int GetYear();
```

### <a name="return-value"></a>傳回值

傳回以當地時間為基礎的年份，其範圍是從1970年1月1日到2038年1月18日 (內含) 。

### <a name="remarks"></a>備註

此函式呼叫會 `GetLocalTm` 使用內部靜態配置的緩衝區。 因為呼叫其他成員函式，所以會覆寫這個緩衝區中的資料 `CTime` 。

### <a name="example"></a>範例

請參閱 [GetDay](#getday)的範例。

## <a name="ctimeoperator-"></a><a name="operator_eq"></a> CTime：： operator =

指派運算子。

```
CTime& operator=(__time64_t time) throw();
```

### <a name="parameters"></a>參數

*time*<br/>
新的日期/時間值。

### <a name="return-value"></a>傳回值

更新的 `CTime` 物件。

### <a name="remarks"></a>備註

這個多載指派運算子會將來源時間複製到這個 `CTime` 物件中。 物件中的內部時間儲存體 `CTime` 與時區無關。 指派期間不需要時區轉換。

## <a name="ctimeoperator---"></a><a name="operator_add_-"></a> CTime：： operator +、-

這些運算子會新增及減去 `CTimeSpan` 和 `CTime` 物件。

```
CTime operator+(CTimeSpan timeSpan) const throw();
CTime operator-(CTimeSpan timeSpan) const throw();
CTimeSpan operator-(CTime time) const throw();
```

### <a name="parameters"></a>參數

*timeSpan*<br/>
`CTimeSpan`要加入或減去的物件。

*time*<br/>
`CTime`要減去的物件。

### <a name="return-value"></a>傳回值

`CTime`表示作業結果的或 `CTimeSpan` 物件。

### <a name="remarks"></a>備註

`CTime` 物件代表絕對時間， `CTimeSpan` 物件代表相對時間。 前兩個運算子可讓您在物件中加入和減去 `CTimeSpan` 物件 `CTime` 。 第三個運算子可讓您 `CTime` 從另一個物件減去一個物件，以產生 `CTimeSpan` 物件。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#159](../../atl-mfc-shared/codesnippet/cpp/ctime-class_13.cpp)]

## <a name="ctimeoperator---"></a><a name="operator_add_eq_-_eq"></a> CTime：： operator + =、-=

這些運算子會在 `CTimeSpan` 此物件中加入和減去物件 `CTime` 。

```
CTime& operator+=(CTimeSpan span) throw();
CTime& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>參數

*跨度*<br/>
`CTimeSpan`要加入或減去的物件。

### <a name="return-value"></a>傳回值

更新的 `CTime` 物件。

### <a name="remarks"></a>備註

這些運算子可讓您在 `CTimeSpan` 這個物件中加入和減去物件 `CTime` 。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#160](../../atl-mfc-shared/codesnippet/cpp/ctime-class_14.cpp)]

## <a name="ctimeserialize64"></a><a name="serialize64"></a> CTime：： Serialize64

> [!NOTE]
> 這個方法僅適用于 MFC 專案。

將與成員變數相關聯的資料序列化至封存。

```
CArchive& Serialize64(CArchive& ar);
```

### <a name="parameters"></a>參數

*Ar*<br/>
`CArchive`您要更新的物件。

### <a name="return-value"></a>傳回值

更新的 `CArchive` 物件。

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
