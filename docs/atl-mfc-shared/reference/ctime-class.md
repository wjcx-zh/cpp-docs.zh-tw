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
ms.openlocfilehash: e6e471fe648c5fa370cce750e8569e158eb1ffe4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317561"
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
|[時間::CTime](#ctime)|以各種方式構造`CTime`物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C時間::格式](#format)|根據本地時區`CTime`將物件轉換為格式化字串。|
|[時間::格式Gmt](#formatgmt)|根據 UTC`CTime`將物件轉換為格式化字串。|
|[C時間:取得 ASDBTIMESTAMP](#getasdbtimestamp)|將存儲在物件中`CTime`的時間資訊轉換為與 Win32 相容的 DBTIMESTAMP 結構。|
|[時間::取得系統時間](#getassystemtime)|將儲存在物件中`CTime`的時間資訊轉換為與 Win32 相容的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構。|
|[時間::取得目前的時間](#getcurrenttime)|創建`CTime`表示當前時間的物件(靜態成員函數)。|
|[C時間::取得日](#getday)|返回物件表示的`CTime`天。|
|[時間::取得周](#getdayofweek)|返回由`CTime`物件表示的星期一。|
|[時間::取得GmtTm](#getgmttm)|根據UTC`CTime`將物件分解為元件。|
|[時間::取得小時](#gethour)|返回物件表示的`CTime`小時。|
|[時間::取得本地Tm](#getlocaltm)|根據本地時區`CTime`將物件分解為元件。|
|[C時間::取得分鐘](#getminute)|返回物件表示的`CTime`分鐘。|
|[時間::取得月份](#getmonth)|返回物件表示的`CTime`月份。|
|[C時間::取得第二](#getsecond)|返回由物件表示的第二`CTime`個。|
|[時間::取得時間](#gettime)|返回給定 **__time64_t**`CTime`物件的__time64_t值。|
|[C時間::取得年份](#getyear)|返回物件表示的`CTime`年份。|
|[時間::序列化64](#serialize64)|將資料序列化到存檔或從存檔中序列化。|

### <a name="operators"></a>操作員

|||
|-|-|
|[運算子 = -](#operator_add_-)|這些運算子新增、減去`CTimeSpan`物件`CTime`。|
|[運算子 *, -]](#operator_add_eq_-_eq)|這些運算符在此`CTimeSpan``CTime`物件中添加和減去物件。|
|[運算符 |](#operator_eq)|分配運算符。|
|[運算符 *,< 等。](#ctime_comparison_operators)|比較運算符。|

## <a name="remarks"></a>備註

`CTime`沒有基類。

`CTime`值基於協調的通用時間 (UTC),這相當於協調通用時間(格林威治標準時間、GMT)。 有關如何確定時區的資訊,請參閱[時間管理](../../c-runtime-library/time-management.md)。

創建`CTime`物件時,`nDST`將 參數設置為 0 以指示標準時間有效,或設置為大於 0 的值以指示夏令時有效,或設置為小於零的值,以便 C 運行時庫代碼計算標準時間或夏令時是否有效。 `tm_isdst` 是必要的欄位。 如果未設定,則其值未定義,[來自 mktime](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)的返回值不可預測。 如果`timeptr`指向以前調用[asctime_s、_gmtime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)或[_gmtime_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)[localtime_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)返回的`tm_isdst`tm 結構,則 該欄位包含正確的值。

配套類[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)表示時間間隔。

和`CTime``CTimeSpan`類不是為派生而設計的。 由於沒有虛擬函數,因此和`CTime``CTimeSpan`物件的大小正好為 8 個字節。 大多數成員函數是內聯的。

> [!NOTE]
> 上限為 12/31/3000。 下限為 1970 年 1 月 1 日 12:00:00 GMT。

有關使用`CTime`的詳細資訊,請參閱「執行時庫參考」中的文章[日期和時間](../../atl-mfc-shared/date-and-time.md), 以及[時間管理](../../c-runtime-library/time-management.md)。

> [!NOTE]
> 結構`CTime`從 MFC 7.1 更改為 MFC 8.0。 如果使用 MFC `CTime` 8.0 或更高版本的**運算符 <<** 對結構進行序列化,則生成的檔在舊版本的 MFC 上是不可讀的。

## <a name="requirements"></a>需求

**標題:** atltime.h

## <a name="ctime-comparison-operators"></a><a name="ctime_comparison_operators"></a>CTime 比較運算子

比較運算符。

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

如果條件為 true,這些運算元比較兩個絕對時間並返回 TRUE;否則 FALSE。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#161](../../atl-mfc-shared/codesnippet/cpp/ctime-class_1.cpp)]

## <a name="ctimectime"></a><a name="ctime"></a>時間::CTime

建立使用指定`CTime`時間初始化的新物件。

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

*時間Src*<br/>
指示已`CTime`存在的物件。

*time*<br/>
`__time64_t`時間值,即 1970 年 1 月 1 日之後的秒數 UTC。 請注意,這將根據您的本地時間進行調整。 例如,如果您在紐約,並通過傳遞參數 0`CTime`來 創建物件[,CTime::getMonth](#getmonth)將返回 12。

*nYear*, *nMonth*, *nDay*, *nHour*, *nMin*, *nSec*<br/>
指示要複製到新`CTime`物件的日期和時間值。

*nDST*<br/>
指示夏令時是否有效。 可以具有三個值之一:

- *nDST*設置為 0 標準時間有效。

- *nDST*設置為大於 0 夏令時的值有效。

- *nDST*設置為小於 0 的值預設值。 自動計算標準時間或夏令時是否有效。

*wDosDate*, *wDosTime*<br/>
要轉換為日期/時間值並複製到新`CTime`物件的 MS-DOS 日期和時間值。

*聖*<br/>
要轉換為日期/時間值並複製到新`CTime`物件的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構。

*英呎*<br/>
要轉換為日期/時間值並複製到新`CTime`物件的[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)結構。

*dbts*<br/>
對包含當前本地時間的 DBTIMESTAMP 結構的引用。

### <a name="remarks"></a>備註

下面將介紹每個建構函數:

- `CTime();`構造未初始化`CTime`的物件。 此建構函數允許您定義`CTime`物件陣列。 在使用之前,應用有效時間初始化此類陣列。

- `CTime( const CTime& );`從另一`CTime`個`CTime`值構造物件。

- `CTime( __time64_t );`從__time64_t類型`CTime`構造物件。 **__time64_t** 此建構函數需要 UTC 時間,並在儲存結果之前將結果轉換為本地時間。

- `CTime( int, int, ...);`建構來自本地`CTime`時間元件的物件,每個元件都受限制在以下範圍:

   |元件|範圍|
   |---------------|-----------|
   |*n年*|1970-3000|
   |*n月*|1-12|
   |*nDay*|1-31|
   |*nHour*|0-23|
   |*nMin*|0-59|
   |*nSec*|0-59|

   此建構函數進行適當的轉換到UTC。 Microsoft 基礎類庫的調試版本斷言一個或多個時間元件是否超過範圍。 在調用之前,必須驗證參數。 此建構函數需要本地時間。

- `CTime( WORD, WORD );`從指定的`CTime`MS-DOS 日期和時間值建構物件。 此建構函數需要本地時間。

- `CTime( const SYSTEMTIME& );`從`SYSTEMTIME`結構構造`CTime`物件。 此建構函數需要本地時間。

- `CTime( const FILETIME& );`從`FILETIME`結構構造`CTime`物件。 您很可能不會直接使用`CTime FILETIME`初始化。 如果使用`CFile`物件操作檔,`CFile::GetStatus`則透過`CTime``FILETIME`使用結構初始化的物件檢索檔時間戳。 此建構函數假定基於 UTC 的時間,並在儲存結果之前自動將值轉換為本地時間。

   > [!NOTE]
   > 僅當包含 OLEDB.h 時`DBTIMESTAMP`,使用 參數的構造函數才可用。

有關詳細資訊,請參閱 Windows SDK 中的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)和[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)結構。 另請參閱 Windows SDK 中的[MS-DOS 日期和時間](/windows/win32/SysInfo/ms-dos-date-and-time)條目。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#148](../../atl-mfc-shared/codesnippet/cpp/ctime-class_2.cpp)]

## <a name="ctimeformat"></a><a name="format"></a>C時間::格式

呼叫此成員函數以創建日期時間值的格式化表示形式。

```
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>參數

*psz格式*<br/>
類似於格式字串的`printf`格式字串。 格式代碼(前面為百分比`%`( ) 符號`CTime`,由相應的 元件替換。 格式字串中的其他字元將複製到傳回的字串。 有關格式代碼清單,請參閱運行時函數[時刻。](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)

*nFormatID*<br/>
識別此格式的字串的識別碼。

### <a name="return-value"></a>傳回值

包含格式化時間的[CString。](../../atl-mfc-shared/reference/cstringt-class.md)

### <a name="remarks"></a>備註

如果此`CTime`物件的狀態為 null,則傳回值為空字串。

如果格式化的日期和時間值範圍不是從 1970 年 1 月 1 日午夜到 3000 年 12 月 31 日通用協調時間 (UTC),則此方法將引發異常。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#149](../../atl-mfc-shared/codesnippet/cpp/ctime-class_3.cpp)]

## <a name="ctimeformatgmt"></a><a name="formatgmt"></a>時間::格式Gmt

產生對應於此`CTime`物件的格式化字串。

```
CString FormatGmt(LPCTSTR pszFormat) const;
CString FormatGmt(UINT nFormatID) const;
```

### <a name="parameters"></a>參數

*psz格式*<br/>
指定類似於格式字串的`printf`格式字串。 有關詳細資訊,請參閱運行時函數[時刻。](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)

*nFormatID*<br/>
識別此格式的字串的識別碼。

### <a name="return-value"></a>傳回值

包含格式化時間的[CString。](../../atl-mfc-shared/reference/cstringt-class.md)

### <a name="remarks"></a>備註

時間值不會轉換,因此反映 UTC。

如果格式化的日期和時間值範圍不是從 1970 年 1 月 1 日午夜到 3000 年 12 月 31 日通用協調時間 (UTC),則此方法將引發異常。

### <a name="example"></a>範例

請參閱[CTime::格式](#format)的範例。

## <a name="ctimegetasdbtimestamp"></a><a name="getasdbtimestamp"></a>C時間:取得 ASDBTIMESTAMP

調用此成員函數將儲存在物件中`CTime`的時間資訊轉換為與 Win32 相容的 DBTIMESTAMP 結構。

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```

### <a name="parameters"></a>參數

*dbts*<br/>
對包含當前本地時間的 DBTIMESTAMP 結構的引用。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

將結果的時間存儲在引用的*dbts*結構中。 此`DBTIMESTAMP`函數初始化的數據結構將使其`fraction`成員設置為零。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#150](../../atl-mfc-shared/codesnippet/cpp/ctime-class_4.cpp)]

## <a name="ctimegetassystemtime"></a><a name="getassystemtime"></a>時間::取得系統時間

調用此成員函數將儲存在物件中`CTime`的時間資訊轉換為與 Win32 相容的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構。

```
bool GetAsSystemTime(SYSTEMTIME& st) const throw();
```

### <a name="parameters"></a>參數

*時間時間*<br/>
對將保存`CTime`物件轉換的日期/時間值的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的引用。

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

`GetAsSystemTime`將生成的時間存儲在引用*的時間最點一元*結構中。 此`SYSTEMTIME`函數初始化的數據結構將使其`wMilliseconds`成員設置為零。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#151](../../atl-mfc-shared/codesnippet/cpp/ctime-class_5.cpp)]

## <a name="ctimegetcurrenttime"></a><a name="getcurrenttime"></a>時間::取得目前的時間

返回表示`CTime`當前時間的物件。

```
static CTime WINAPI GetCurrentTime() throw();
```

### <a name="remarks"></a>備註

在協調通用時間 (UTC) 中傳回目前系統日期和時間。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#152](../../atl-mfc-shared/codesnippet/cpp/ctime-class_6.cpp)]

## <a name="ctimegetday"></a><a name="getday"></a>C時間::取得日

返回物件表示的`CTime`天。

```
int GetDay() const throw();
```

### <a name="return-value"></a>傳回值

返回每月的一天,基於本地時間,在範圍 1 到 31 中。

### <a name="remarks"></a>備註

此函數調用`GetLocalTm`,它使用內部靜態分配的緩衝區。 由於調用其他成員`CTime`函數,此緩衝區中的數據將被覆蓋。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#153](../../atl-mfc-shared/codesnippet/cpp/ctime-class_7.cpp)]

## <a name="ctimegetdayofweek"></a><a name="getdayofweek"></a>時間::取得周

返回由`CTime`物件表示的星期一。

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>傳回值

根據本地時間返回星期一;1 = 周日,2 = 星期一,到 7 = 星期六。

### <a name="remarks"></a>備註

此函數調用`GetLocalTm`,它使用內部靜態分配的緩衝區。 由於調用其他成員`CTime`函數,此緩衝區中的數據將被覆蓋。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#154](../../atl-mfc-shared/codesnippet/cpp/ctime-class_8.cpp)]

## <a name="ctimegetgmttm"></a><a name="getgmttm"></a>時間::取得GmtTm

獲取包含此`CTime`物件中包含的時間的分解**結構tm。**

```
struct tm* GetGmtTm(struct tm* ptm) const;
```

### <a name="parameters"></a>參數

*ptm*<br/>
指向將接收時間數據的緩衝區。 如果此指標為 NULL,則引發異常。

### <a name="return-value"></a>傳回值

指向包含檔 TIME 中定義的填充**結構 tm 的**指標。H。 有關結構佈局,請參閱[gmtime、_gmtime32、_gmtime64。](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)

### <a name="remarks"></a>備註

`GetGmtTm`返回 UTC。

*ptm*不能為 NULL。 如果要還原到舊行為(其中*ptm*可以是 NULL 以指示應使用內部靜態分配的緩衝區),則取消定義_SECURE_ATL。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#155](../../atl-mfc-shared/codesnippet/cpp/ctime-class_9.cpp)]

## <a name="ctimegethour"></a><a name="gethour"></a>時間::取得小時

返回物件表示的`CTime`小時。

```
int GetHour() const throw();
```

### <a name="return-value"></a>傳回值

返回基於本地時間在範圍 0 到 23 中的小時。

### <a name="remarks"></a>備註

此函數調用`GetLocalTm`,它使用內部靜態分配的緩衝區。 由於調用其他成員`CTime`函數,此緩衝區中的數據將被覆蓋。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#156](../../atl-mfc-shared/codesnippet/cpp/ctime-class_10.cpp)]

## <a name="ctimegetlocaltm"></a><a name="getlocaltm"></a>時間::取得本地Tm

獲取包含此`CTime`物件中包含的時間的分解**結構tm。**

```
struct tm* GetLocalTm(struct tm* ptm) const;
```

### <a name="parameters"></a>參數

*ptm*<br/>
指向將接收時間數據的緩衝區。 如果此指標為 NULL,則引發異常。

### <a name="return-value"></a>傳回值

指向包含檔 TIME 中定義的填充**結構 tm 的**指標。H。 有關結構佈局,請參閱[gmtime、_gmtime32、_gmtime64。](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)

### <a name="remarks"></a>備註

`GetLocalTm`返回本地時間。

*ptm*不能為 NULL。 如果要還原到舊行為(其中*ptm*可以是 NULL 以指示應使用內部靜態分配的緩衝區),則取消定義_SECURE_ATL。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#157](../../atl-mfc-shared/codesnippet/cpp/ctime-class_11.cpp)]

## <a name="ctimegetminute"></a><a name="getminute"></a>C時間::取得分鐘

返回物件表示的`CTime`分鐘。

```
int GetMinute() const throw();
```

### <a name="return-value"></a>傳回值

返回基於本地時間的範圍 0 到 59 的分鐘。

### <a name="remarks"></a>備註

此函數調用`GetLocalTm`,它使用內部靜態分配的緩衝區。 由於調用其他成員`CTime`函數,此緩衝區中的數據將被覆蓋。

### <a name="example"></a>範例

請參閱[GetHour](#gethour)的範例。

## <a name="ctimegetmonth"></a><a name="getmonth"></a>時間::取得月份

返回物件表示的`CTime`月份。

```
int GetMonth() const throw();
```

### <a name="return-value"></a>傳回值

返回基於本地時間的範圍 1 到 12(1 = 1 月)的月份。

### <a name="remarks"></a>備註

此函數調用`GetLocalTm`,它使用內部靜態分配的緩衝區。 由於調用其他成員`CTime`函數,此緩衝區中的數據將被覆蓋。

### <a name="example"></a>範例

請參閱[GetDay](#getday)的範例。

## <a name="ctimegetsecond"></a><a name="getsecond"></a>C時間::取得第二

返回由物件表示的第二`CTime`個。

```
int GetSecond() const throw();
```

### <a name="return-value"></a>傳回值

返回基於本地時間的第二個範圍 0 到 59。

### <a name="remarks"></a>備註

此函數調用`GetLocalTm`,它使用內部靜態分配的緩衝區。 由於調用其他成員`CTime`函數,此緩衝區中的數據將被覆蓋。

### <a name="example"></a>範例

請參閱[GetHour](#gethour)的範例。

## <a name="ctimegettime"></a><a name="gettime"></a>時間::取得時間

返回給定 **__time64_t**`CTime`物件的__time64_t值。

```
__time64_t GetTime() const throw();
```

### <a name="return-value"></a>傳回值

`GetTime`將返回當前`CTime`物件與 1970 年 1 月 1 日之間的秒數。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#158](../../atl-mfc-shared/codesnippet/cpp/ctime-class_12.cpp)]

## <a name="ctimegetyear"></a><a name="getyear"></a>C時間::取得年份

返回物件表示的`CTime`年份。

```
int GetYear();
```

### <a name="return-value"></a>傳回值

返回 1970 年 1 月 1 日至 2038 年 1 月 18 日(含)的年份,基於本地時間。

### <a name="remarks"></a>備註

此函數調用`GetLocalTm`,它使用內部靜態分配的緩衝區。 由於調用其他成員`CTime`函數,此緩衝區中的數據將被覆蓋。

### <a name="example"></a>範例

請參閱[GetDay](#getday)的範例。

## <a name="ctimeoperator-"></a><a name="operator_eq"></a>時間::運算符 |

分配運算符。

```
CTime& operator=(__time64_t time) throw();
```

### <a name="parameters"></a>參數

*time*<br/>
新的日期/時間值。

### <a name="return-value"></a>傳回值

更新`CTime`的物件。

### <a name="remarks"></a>備註

此重載賦值運算符將源時間複製到此`CTime`物件中。 `CTime`物件中的內部時間存儲與時區無關。 在分配期間不需要時區轉換。

## <a name="ctimeoperator---"></a><a name="operator_add_-"></a>CTime::運算符 +, -

這些運算子新增、減去`CTimeSpan`物件`CTime`。

```
CTime operator+(CTimeSpan timeSpan) const throw();
CTime operator-(CTimeSpan timeSpan) const throw();
CTimeSpan operator-(CTime time) const throw();
```

### <a name="parameters"></a>參數

*時間跨度*<br/>
要`CTimeSpan`添加或減去的物件。

*time*<br/>
要`CTime`減去的物件。

### <a name="return-value"></a>傳回值

`CTime`表示操作結果`CTimeSpan`的物件。

### <a name="remarks"></a>備註

`CTime`物件表示絕對時間,`CTimeSpan`物件表示相對時間。 前兩個運算符允許您在`CTimeSpan``CTime`物件中添加和減去物件。 第三個運算符允許您從另一`CTime`個對象中減去一`CTimeSpan`個 物件以產生一個物件。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#159](../../atl-mfc-shared/codesnippet/cpp/ctime-class_13.cpp)]

## <a name="ctimeoperator---"></a><a name="operator_add_eq_-_eq"></a>C時間::運算符 *,-*

這些運算符在此`CTimeSpan``CTime`物件中添加和減去物件。

```
CTime& operator+=(CTimeSpan span) throw();
CTime& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>參數

*跨度*<br/>
要`CTimeSpan`添加或減去的物件。

### <a name="return-value"></a>傳回值

更新`CTime`的物件。

### <a name="remarks"></a>備註

這些運算子允許您在此`CTimeSpan``CTime`物件中添加和減去物件。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#160](../../atl-mfc-shared/codesnippet/cpp/ctime-class_14.cpp)]

## <a name="ctimeserialize64"></a><a name="serialize64"></a>時間::序列化64

> [!NOTE]
> 此方法僅在 MFC 專案中可用。

序列化與成員變數關聯的存檔或從存檔中的數據。

```
CArchive& Serialize64(CArchive& ar);
```

### <a name="parameters"></a>參數

*ar*<br/>
要`CArchive`更新的物件。

### <a name="return-value"></a>傳回值

更新`CArchive`的物件。

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
