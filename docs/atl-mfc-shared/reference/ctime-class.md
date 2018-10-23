---
title: CTime 類別 |Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CTime class
- shared classes, CTime
ms.assetid: 0a299544-485b-48dc-9d3c-fdc30f57d612
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8c99fe44b5012e08a4b32a9e84d4255e4ee2b7e0
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808832"
---
# <a name="ctime-class"></a>CTime 類別

表示絕對的時間和日期。

## <a name="syntax"></a>語法

```
class CTime
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CTime::CTime](#ctime)|建構`CTime`以各種方式的物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CTime::Format](#format)|將轉換`CTime`格式化的字串物件 — 根據當地時區。|
|[CTime::FormatGmt](#formatgmt)|將轉換`CTime`格式化的字串物件 — 根據 UTC。|
|[CTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|將時間資訊儲存在轉換`CTime`Win32 相容 DBTIMESTAMP 結構的物件。|
|[CTime::GetAsSystemTime](#getassystemtime)|將時間資訊儲存在轉換`CTime`Win32 相容的物件[SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)結構。|
|[CTime::GetCurrentTime](#getcurrenttime)|建立`CTime`物件，表示目前的時間 （靜態成員函式）。|
|[CTime::GetDay](#getday)|傳回由天代表`CTime`物件。|
|[CTime::GetDayOfWeek](#getdayofweek)|傳回所代表之一週的日`CTime`物件。|
|[CTime::GetGmtTm](#getgmttm)|細分`CTime`成元件的物件 — 根據 UTC。|
|[CTime::GetHour](#gethour)|傳回代表的小時`CTime`物件。|
|[CTime::GetLocalTm](#getlocaltm)|細分`CTime`成元件的物件 — 根據當地時區。|
|[CTime::GetMinute](#getminute)|傳回所表示分鐘`CTime`物件。|
|[CTime::GetMonth](#getmonth)|傳回所代表月份`CTime`物件。|
|[CTime::GetSecond](#getsecond)|傳回由第二個`CTime`物件。|
|[CTime::GetTime](#gettime)|傳回 **__time64_t**值指定`CTime`物件。|
|[CTime::GetYear](#getyear)|傳回所表示的年份`CTime`物件。|
|[CTime::Serialize64](#serialize64)|將序列化資料，或從封存。|

### <a name="operators"></a>運算子

|||
|-|-|
|[運算子 +-](#operator_add_-)|這些運算子加法和減法`CTimeSpan`和`CTime`物件。|
|[運算子 + =、 =](#operator_add_eq_-_eq)|這些運算子加法和減法`CTimeSpan`物件並從這個`CTime`物件。|
|[operator =](#operator_eq)|指派運算子。|
|[運算子 = =，<，依此類推。](#ctime_comparison_operators)|比較運算子。|

## <a name="remarks"></a>備註

`CTime` 沒有基底類別。

`CTime` 值根據國際標準時間 (UTC)，這相當於國際標準時間 （格林威治標準時間，GMT）。 請參閱[時間管理](../../c-runtime-library/time-management.md)如需有關如何判斷時區資訊。

當您建立`CTime`物件，設定`nDST`參數為 0，表示標準時間已生效，或讓值大於 0，表示日光節約時間處於作用中，或值小於零將 C 執行階段程式庫程式碼電腦e 標準時間或日光節約時間是否生效。 `tm_isdst` 是必要的欄位。 如果未設定，其值為未定義和傳回值[mktime](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)無法預期。 如果`timeptr`指向由先前呼叫所傳回 tm 結構[asctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)， [_gmtime_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)，或[localtime_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)，`tm_isdst`欄位包含正確的值。

附屬類別[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)，代表時間間隔。

`CTime`和`CTimeSpan`類別並未設計成衍生。 因為沒有任何虛擬函式的大小`CTime`和`CTimeSpan`物件是完全 8 個位元組。 大部分的成員函式會以內嵌方式。

> [!NOTE]
>  上方的日期限制為 12/31/3000。 下限是 1/1/1970年 12:00:00 AM GMT。

如需使用詳細資訊`CTime`，請參閱文章[日期和時間](../../atl-mfc-shared/date-and-time.md)，以及[時間管理](../../c-runtime-library/time-management.md)執行階段程式庫參考中。

> [!NOTE]
>  `CTime`結構變更從 MFC 7.1 MFC 8.0。 如果您將序列化`CTime`使用的結構**運算子 <<** MFC 8.0 或更新版本，在產生的檔案將無法讀取在舊版的 MFC。

## <a name="requirements"></a>需求

**標頭：** atltime.h

##  <a name="ctime_comparison_operators"></a>  CTime 比較運算子

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

這些運算子比較兩個絕對的時間，並傳回 TRUE 的條件為 true; 如果否則為 FALSE。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#161](../../atl-mfc-shared/codesnippet/cpp/ctime-class_1.cpp)]

##  <a name="ctime"></a>  CTime::CTime

建立新`CTime`物件初始化使用指定的時間。

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
指出`CTime`已經存在的物件。

*time*<br/>
A **__time64_t**時間值，也就是在 1970 年 1 月 1 日 UTC 之後的秒數。 請注意，這將會調整為您的當地時間。 例如，如果您位在紐約，並建立`CTime`物件，並傳遞的參數為 0， [CTime::GetMonth](#getmonth)會傳回 12。

*nYear*， *nMonth*， *n*，*當天的時數*， *nMin*， *nSec*<br/>
表示要複製到新的日期和時間值`CTime`物件。

*nDST*<br/>
指出日光節約時間是否生效。 可以有三個值之一：

- *nDST* 0Standard 時間設為作用中。

- *nDST*設的值大於 0Daylight 省下時間已生效。

- *nDST*設為小於 0The 預設的值。 自動計算標準時間或日光節約時間是否生效。

*wDosDate*， *wDosTime*<br/>
MS-DOS 日期和時間值轉換成日期/時間值，並複製到新`CTime`物件。

*st*<br/>
A [SYSTEMTIME](../../mfc/reference/systemtime-structure.md)轉換成日期/時間值，並複製到新的結構`CTime`物件。

*全文檢索*<br/>
A [FILETIME](../../mfc/reference/filetime-structure.md)轉換成日期/時間值，並複製到新的結構`CTime`物件。

*dbts*<br/>
DBTIMESTAMP 結構，包含目前的當地時間的參考。

### <a name="remarks"></a>備註

每個建構函式會如下所述：

- `CTime();` 建構未初始化`CTime`物件。 這個建構函式可讓您定義`CTime`物件陣列。 您應該初始化有效的時間，才能使用這類陣列。

- `CTime( const CTime& );` 建構`CTime`物件從另一個`CTime`值。

- `CTime( __time64_t );` 建構`CTime`物件從 **__time64_t**型別。 這個建構函式必須要有 UTC 時間，並儲存結果之前，將結果轉換為當地時間。

- `CTime( int, int, ...);` 建構`CTime`物件從當地時間元件，每個元件都受限於下列範圍：

   |元件|範圍|
   |---------------|-----------|
   |*nYear*|1970-3000|
   |*nMonth*|1-12|
   |*n*|1-31|
   |*當天的時數*|0-23|
   |*nMin*|0-59|
   |*nSec*|0-59|

   這個建構函式可讓適當的轉換為 UTC。 Microsoft Foundation 類別庫的偵錯版本判斷提示，如果有一個或多個時間元件會超出範圍。 您必須先驗證再呼叫的引數。 這個建構函式需要本地時間。

- `CTime( WORD, WORD );` 建構`CTime`從指定的 MS-DOS 日期和時間值的物件。 這個建構函式需要本地時間。

- `CTime( const SYSTEMTIME& );` 建構`CTime`物件從`SYSTEMTIME`結構。 這個建構函式需要本地時間。

- `CTime( const FILETIME& );` 建構`CTime`物件從`FILETIME`結構。 您很可能不會使用`CTime FILETIME`直接初始化。 如果您使用`CFile`物件來管理檔案，`CFile::GetStatus`讓您透過擷取檔案時間戳記`CTime`物件初始化`FILETIME`結構。 這個建構函式會假設根據 UTC 時間，並儲存結果之前，會自動將值轉換為當地時間。

   > [!NOTE]
   > 建構函式使用`DBTIMESTAMP`OLEDB.h 包含在內時，才可用參數。

如需詳細資訊，請參閱 < [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)並[FILETIME](https://msdn.microsoft.com/library/windows/desktop/ms724284) Windows SDK 中的結構。 另請參閱[MS-DOS 日期和時間](/windows/desktop/SysInfo/ms-dos-date-and-time)Windows SDK 中的項目。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#148](../../atl-mfc-shared/codesnippet/cpp/ctime-class_2.cpp)]

##  <a name="format"></a>  CTime::Format

呼叫此成員函式來建立格式化的日期時間值的表示法。

```
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>參數

*pszFormat*<br/>
格式化字串類似於`printf`格式化字串。 格式化程式碼，加上百分比 (`%`) 登入，會取代對應`CTime`元件。 格式化字串中的其他字元會複製到傳回的字串不變。 請參閱執行階段函式[strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)的格式化程式碼清單。

*nFormatID*<br/>
識別此格式的字串識別碼。

### <a name="return-value"></a>傳回值

A [CString](../../atl-mfc-shared/reference/cstringt-class.md) ，其中包含格式的時間。

### <a name="remarks"></a>備註

如果這個狀態`CTime`物件為 null，則傳回的值為空字串。

此方法擲回例外狀況，如果要格式化的日期時間值範圍並不是從 1970 年 1 月 1 日到 3000 年 12 月 31 日午夜 Universal Coordinated Time (UTC)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#149](../../atl-mfc-shared/codesnippet/cpp/ctime-class_3.cpp)]

##  <a name="formatgmt"></a>  CTime::FormatGmt

會產生格式化的字串，對應至這個`CTime`物件。

```
CString FormatGmt(LPCTSTR pszFormat) const;
CString FormatGmt(UINT nFormatID) const;
```

### <a name="parameters"></a>參數

*pszFormat*<br/>
指定的格式化字串，類似於`printf`格式化字串。 請參閱執行階段函式[strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)如需詳細資訊。

*nFormatID*<br/>
識別此格式的字串識別碼。

### <a name="return-value"></a>傳回值

A [CString](../../atl-mfc-shared/reference/cstringt-class.md) ，其中包含格式的時間。

### <a name="remarks"></a>備註

時間值不會被轉換，並因此會反映 UTC。

此方法擲回例外狀況，如果要格式化的日期時間值範圍並不是從 1970 年 1 月 1 日到 3000 年 12 月 31 日午夜 Universal Coordinated Time (UTC)。

### <a name="example"></a>範例

範例，請參閱[CTime::Format](#format)。

##  <a name="getasdbtimestamp"></a>  CTime::GetAsDBTIMESTAMP

呼叫此成員函式，將時間資訊儲存在轉換`CTime`Win32 相容 DBTIMESTAMP 結構的物件。

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```

### <a name="parameters"></a>參數

*dbts*<br/>
DBTIMESTAMP 結構，包含目前的當地時間的參考。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

將產生的時間儲存在參考*dbts*結構。 `DBTIMESTAMP`由此函式初始化的資料結構會有其`fraction`成員設定為零。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#150](../../atl-mfc-shared/codesnippet/cpp/ctime-class_4.cpp)]

##  <a name="getassystemtime"></a>  CTime::GetAsSystemTime

呼叫此成員函式，將時間資訊儲存在轉換`CTime`Win32 相容的物件[SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)結構。

```
bool GetAsSystemTime(SYSTEMTIME& st) const throw();
```

### <a name="parameters"></a>參數

*timeDest*<br/>
參考[SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)會保存已轉換的日期/時間值的結構`CTime`物件。

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

`GetAsSystemTime` 將產生的時間儲存在參考*timeDest*結構。 `SYSTEMTIME`由此函式初始化的資料結構會有其`wMilliseconds`成員設定為零。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#151](../../atl-mfc-shared/codesnippet/cpp/ctime-class_5.cpp)]

##  <a name="getcurrenttime"></a>  CTime::GetCurrentTime

傳回`CTime`物件，表示目前的時間。

```
static CTime WINAPI GetCurrentTime() throw();
```

### <a name="remarks"></a>備註

傳回目前的系統日期和時間以 Coordinated Universal Time (UTC)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#152](../../atl-mfc-shared/codesnippet/cpp/ctime-class_6.cpp)]

##  <a name="getday"></a>  CTime::GetDay

傳回由天代表`CTime`物件。

```
int GetDay() const throw();
```

### <a name="return-value"></a>傳回值

傳回月份，根據本機時間，範圍介於 1 到 31 天。

### <a name="remarks"></a>備註

此函式會呼叫`GetLocalTm`，它會使用內部的靜態配置的緩衝區。 這個緩衝區中的資料會覆寫，因為其他的呼叫，所以`CTime`成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#153](../../atl-mfc-shared/codesnippet/cpp/ctime-class_7.cpp)]

##  <a name="getdayofweek"></a>  CTime::GetDayOfWeek

傳回所代表之一週的日`CTime`物件。

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>傳回值

傳回本地時間為基礎的一週天數1 = 星期日，2 = 星期一，7 = 星期六。

### <a name="remarks"></a>備註

此函式會呼叫`GetLocalTm`，它會使用靜態內部配置緩衝區。 這個緩衝區中的資料會覆寫，因為其他的呼叫，所以`CTime`成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#154](../../atl-mfc-shared/codesnippet/cpp/ctime-class_8.cpp)]

##  <a name="getgmttm"></a>  CTime::GetGmtTm

取得**struct tm** ，其中包含的時間中所包含的分解`CTime`物件。

```
struct tm* GetGmtTm(struct tm* ptm) const;
```

### <a name="parameters"></a>參數

*ptm*<br/>
指向接收時間資料的緩衝區。 如果此指標為 NULL，則會擲回例外狀況。

### <a name="return-value"></a>傳回值

填滿的指標**struct tm** include 檔時間中所定義。H. 請參閱[gmtime _gmtime32，_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)結構版面配置。

### <a name="remarks"></a>備註

`GetGmtTm` 傳回 UTC。

*ptm*不能是 NULL。 如果您想要還原成舊的行為，所在*ptm*可能是 NULL，表示內部，必須使用靜態配置的緩衝區，然後取消 _SECURE_ATL。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#155](../../atl-mfc-shared/codesnippet/cpp/ctime-class_9.cpp)]

##  <a name="gethour"></a>  CTime::GetHour

傳回代表的小時`CTime`物件。

```
int GetHour() const throw();
```

### <a name="return-value"></a>傳回值

傳回根據本機時間，介於 0 到 23 的小時。

### <a name="remarks"></a>備註

此函式會呼叫`GetLocalTm`，它會使用靜態內部配置緩衝區。 這個緩衝區中的資料會覆寫，因為其他的呼叫，所以`CTime`成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#156](../../atl-mfc-shared/codesnippet/cpp/ctime-class_10.cpp)]

##  <a name="getlocaltm"></a>  CTime::GetLocalTm

取得**struct tm**內含的時間中所包含的分解`CTime`物件。

```
struct tm* GetLocalTm(struct tm* ptm) const;
```

### <a name="parameters"></a>參數

*ptm*<br/>
指向接收時間資料的緩衝區。 如果此指標為 NULL，則會擲回例外狀況。

### <a name="return-value"></a>傳回值

填滿的指標**struct tm** include 檔時間中所定義。H. 請參閱[gmtime _gmtime32，_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)結構版面配置。

### <a name="remarks"></a>備註

`GetLocalTm` 傳回本地時間。

*ptm*不能是 NULL。 如果您想要還原成舊的行為，所在*ptm*可能是 NULL，表示內部，必須使用靜態配置的緩衝區，然後取消 _SECURE_ATL。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#157](../../atl-mfc-shared/codesnippet/cpp/ctime-class_11.cpp)]

##  <a name="getminute"></a>  CTime::GetMinute

傳回所表示分鐘`CTime`物件。

```
int GetMinute() const throw();
```

### <a name="return-value"></a>傳回值

傳回分鐘，範圍從 0 到 59 的本地時間為基礎。

### <a name="remarks"></a>備註

此函式會呼叫`GetLocalTm`，它會使用靜態內部配置緩衝區。 這個緩衝區中的資料會覆寫，因為其他的呼叫，所以`CTime`成員函式。

### <a name="example"></a>範例

範例，請參閱[GetHour](#gethour)。

##  <a name="getmonth"></a>  CTime::GetMonth

傳回所代表月份`CTime`物件。

```
int GetMonth() const throw();
```

### <a name="return-value"></a>傳回值

傳回月份，範圍介於 1 到 12 的本地時間為基礎 (1 = 一月)。

### <a name="remarks"></a>備註

此函式會呼叫`GetLocalTm`，它會使用靜態內部配置緩衝區。 這個緩衝區中的資料會覆寫，因為其他的呼叫，所以`CTime`成員函式。

### <a name="example"></a>範例

範例，請參閱[GetDay](#getday)。

##  <a name="getsecond"></a>  CTime::GetSecond

傳回由第二個`CTime`物件。

```
int GetSecond() const throw();
```

### <a name="return-value"></a>傳回值

傳回第二個，範圍從 0 到 59 的本地時間為基礎。

### <a name="remarks"></a>備註

此函式會呼叫`GetLocalTm`，它會使用靜態內部配置緩衝區。 這個緩衝區中的資料會覆寫，因為其他的呼叫，所以`CTime`成員函式。

### <a name="example"></a>範例

範例，請參閱[GetHour](#gethour)。

##  <a name="gettime"></a>  CTime::GetTime

傳回 **__time64_t**值指定`CTime`物件。

```
__time64_t GetTime() const throw();
```

### <a name="return-value"></a>傳回值

`GetTime` 會傳回目前間的秒數`CTime`物件，並從 1970 年 1 月 1 日。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#158](../../atl-mfc-shared/codesnippet/cpp/ctime-class_12.cpp)]

##  <a name="getyear"></a>  CTime::GetYear

傳回所表示的年份`CTime`物件。

```
int GetYear();
```

### <a name="return-value"></a>傳回值

傳回年份，根據本機時間，在範圍內年 1 月 1,1970，來年 1 月 18 2038 日 （含）。

### <a name="remarks"></a>備註

此函式會呼叫`GetLocalTm`，它會使用靜態內部配置緩衝區。 這個緩衝區中的資料會覆寫，因為其他的呼叫，所以`CTime`成員函式。

### <a name="example"></a>範例

範例，請參閱[GetDay](#getday)。

##  <a name="operator_eq"></a>  CTime::operator =

指派運算子。

```
CTime& operator=(__time64_t time) throw();
```

### <a name="parameters"></a>參數

*time*<br/>
新的日期/時間值。

### <a name="return-value"></a>傳回值

已更新`CTime`物件。

### <a name="remarks"></a>備註

此多載的指派運算子複製到這個來源時間`CTime`物件。 中的內部時間儲存體`CTime`物件無關的時區。 在指派期間，不需要時區轉換。

##  <a name="operator_add_-"></a>  CTime::operator +、-

這些運算子加法和減法`CTimeSpan`和`CTime`物件。

```
CTime operator+(CTimeSpan timeSpan) const throw();
CTime operator-(CTimeSpan timeSpan) const throw();
CTimeSpan operator-(CTime time) const throw();
```

### <a name="parameters"></a>參數

*時間範圍*<br/>
`CTimeSpan`要加入或減去的物件。

*time*<br/>
`CTime`来減去的物件。

### <a name="return-value"></a>傳回值

A`CTime`或`CTimeSpan`物件，表示作業的結果。

### <a name="remarks"></a>備註

`CTime` 物件代表絕對的時間，`CTimeSpan`物件代表相對的時間。 前兩個運算子可讓您加入和減去`CTimeSpan`物件與`CTime`物件。 第三個運算子可讓您減一`CTime`物件從另一個產生`CTimeSpan`物件。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#159](../../atl-mfc-shared/codesnippet/cpp/ctime-class_13.cpp)]

##  <a name="operator_add_eq_-_eq"></a>  CTime::operator + =、 =

這些運算子加法和減法`CTimeSpan`物件並從這個`CTime`物件。

```
CTime& operator+=(CTimeSpan span) throw();
CTime& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>參數

*範圍*<br/>
`CTimeSpan`要加入或減去的物件。

### <a name="return-value"></a>傳回值

已更新`CTime`物件。

### <a name="remarks"></a>備註

這些運算子可讓您加入和減去`CTimeSpan`物件並從這個`CTime`物件。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#160](../../atl-mfc-shared/codesnippet/cpp/ctime-class_14.cpp)]

##  <a name="serialize64"></a>  CTime::Serialize64

> [!NOTE]
> 只有在 MFC 專案中，您可以使用這個方法。

將序列化的成員變數，或從封存相關聯的資料。

```
CArchive& Serialize64(CArchive& ar);
```

### <a name="parameters"></a>參數

*ar*<br/>
`CArchive`您想要更新的物件。

### <a name="return-value"></a>傳回值

已更新`CArchive`物件。

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
