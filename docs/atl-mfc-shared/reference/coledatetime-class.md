---
title: COleDateTime 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- shared classes, COleDateTime
- time-only values
- Date data type, MFC encapsulation of
- COleDateTime class
- dates, handling in MFC
- time, handling in MFC
ms.assetid: e718f294-16ec-4649-88b6-a4dbae5178fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 92761508a5e93c7ef0d0a4099dde587987a50dad
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49809157"
---
# <a name="coledatetime-class"></a>COleDateTime 類別

封裝`DATE`OLE automation 中使用的資料類型。

## <a name="syntax"></a>語法

```
class COleDateTime
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleDateTime::COleDateTime](#coledatetime)|建構 `COleDateTime` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleDateTime::Format](#format)|產生的格式化的字串表示`COleDateTime`物件。|
|[COleDateTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|呼叫這個方法來取得時間`COleDateTime`物件做為`DBTIMESTAMP`資料結構。|
|[COleDateTime::GetAsSystemTime](#getassystemtime)|呼叫這個方法來取得時間`COleDateTime`物件做[SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)資料結構。|
|[COleDateTime::GetAsUDATE](#getasudate)|呼叫這個方法來取得時間`COleDateTime`做為`UDATE`資料結構。|
|[COleDateTime::GetCurrentTime](#getcurrenttime)|建立`COleDateTime`物件，表示目前的時間 （靜態成員函式）。|
|[COleDateTime::GetDay](#getday)|這會傳回一天`COleDateTime`物件都代表 (1 – 31)。|
|[COleDateTime::GetDayOfWeek](#getdayofweek)|這會傳回一週的星期幾`COleDateTime`物件的代表 （星期日 = 1）。|
|[COleDateTime::GetDayOfYear](#getdayofyear)|這會傳回的一年天數`COleDateTime`物件的代表 （1 年 1 月 = 1）。|
|[COleDateTime::GetHour](#gethour)|傳回小時這`COleDateTime`物件代表 (0-23)。|
|[COleDateTime::GetMinute](#getminute)|這會傳回分鐘`COleDateTime`物件代表 (0-59)。|
|[COleDateTime::GetMonth](#getmonth)|這會傳回月份`COleDateTime`物件都代表 (1-12)。|
|[COleDateTime::GetSecond](#getsecond)|這會傳回第二個`COleDateTime`物件代表 (0-59)。|
|[COleDateTime::GetStatus](#getstatus)|取得這個狀態 （有效性）`COleDateTime`物件。|
|[COleDateTime::GetYear](#getyear)|這會傳回年度`COleDateTime`物件表示。|
|[COleDateTime::ParseDateTime](#parsedatetime)|從字串讀取日期/時間值，並設定的值`COleDateTime`。|
|[COleDateTime::SetDate](#setdate)|設定值，這個`COleDateTime`物件到指定的僅限日期的值。|
|[COleDateTime::SetDateTime](#setdatetime)|設定值，這個`COleDateTime`物件到指定的日期/時間值。|
|[COleDateTime::SetStatus](#setstatus)|設定此狀態 （有效性）`COleDateTime`物件。|
|[COleDateTime::SetTime](#settime)|設定值，這個`COleDateTime`物件到指定的時間專用值。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[COleDateTime::operator = =、 COleDateTime::operator < 等等。](#coledatetime_relational_operators)|比較兩個`COleDateTime`值。|
|[COleDateTime::operator + COleDateTime::operator-](#operator_add_-)|加法和減法`COleDateTime`值。|
|[COleDateTime::operator + =、 COleDateTime::operator =](#operator_add_eq_-_eq)|加法和減法`COleDateTime`值從這個`COleDateTime`物件。|
|[COleDateTime::operator =](#operator_eq)|複製`COleDateTime`值。|
|[COleDateTime::operator 日 COleDateTime::operator 日期 *](#operator_date)|將轉換`COleDateTime`值貼`DATE`或`DATE*`。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COleDateTime::m_dt](#m_dt)|包含的基礎`DATE`這個`COleDateTime`物件。|
|[COleDateTime::m_status](#m_status)|包含這個狀態`COleDateTime`物件。|

## <a name="remarks"></a>備註

`COleDateTime` 沒有基底類別。

它是其中一個可能的類型，如[VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant) OLE automation 資料類型。 A`COleDateTime`值會表示為絕對日期和時間值。

`DATE`實作類型為浮點值。 天被測量從 1899 年 12 月 30 日，在午夜。 下表顯示一些日期和其相關聯的值：

|日期|值|
|----------|-----------|
|1899 年 12 月 29日日午夜|-1.0|
|1899 年 12 月 29日日 6 點|-1.25|
|1899 年 12 月 30日日午夜|0.0|
|1899 年 12 月 31日日午夜|1.0|
|1900 年 1 月 1日日，上午 6 點|2.25|

> [!CAUTION]
> 請注意，在上表中，雖然日期值變成負數 1899 年 12 月 30 日午夜以前的日期時間值不會。 例如，上午 6:00 一律被以分數值 0.25 而不論是否代表日期的整數 （之後 1899 年 12 月 30 日) 正數或負數 （之前 1899 年 12 月 30 日)。 這表示簡單的浮動點比較會錯誤地排序`COleDateTime`表示 12/29/1899 為上午 6:00**稍後**1 代表上午 7:00 在同一天。

`COleDateTime`類別會處理從 100 年 1 月 1 日到 12 月 31 日的日期到 9999。 `COleDateTime`類別會使用西曆; 它不支援凱撒曆日期。 `COleDateTime` 會忽略日光節約時間。 (請參閱[日期和時間： Automation 支援](../../atl-mfc-shared/date-and-time-automation-support.md)。)

> [!NOTE]
> 您可以使用`%y`来擷取的開始 1900年的日期才兩位數年份格式。 如果您使用`%y`格式日期早於 1900 年，程式碼會產生判斷提示失敗。

此類型也用來代表僅限日期或時間專用的值。 依照慣例，日期為 0 (1899 年 12 月 30 日) 使用於僅限時間的值，並用於僅限日期的值時間 00:00 （午夜）。

如果您建立`COleDateTime`藉由使用日期的物件少於 100 個，日期是已接受，但後續呼叫`GetYear`， `GetMonth`， `GetDay`， `GetHour`， `GetMinute`，和`GetSecond`失敗，並傳回-1。 先前，您可以使用兩位數日期，但是日期必須是 100 或更大，在 MFC 4.2 和更新版本。

若要避免發生問題，指定四位數的日期。 例如: 

[!code-cpp[NVC_ATLMFC_Utilities#1](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_1.cpp)]

針對基本的算術運算`COleDateTime`值會使用附屬類別[COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)。 `COleDateTimeSpan` 值會定義時間間隔。 這些類別之間的關聯性是類似之間[CTime](../../atl-mfc-shared/reference/ctime-class.md)並[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)。

如需詳細資訊`COleDateTime`並`COleDateTimeSpan`類別，請參閱本文[日期和時間： Automation 支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

## <a name="requirements"></a>需求

**標頭：** ATLComTime.h

##  <a name="coledatetime_relational_operators"></a>  COleDateTime 關係運算子

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
>  如果兩個運算元的其中一個無效，會發生 ATLASSERT。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#13](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_2.cpp)]

### <a name="example"></a>範例

運算子**>=**， **\< =**， **>**，與**<**，如果會判斷提示`COleDateTime`物件設定為 null。

[!code-cpp[NVC_ATLMFC_Utilities#170](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_3.cpp)]

##  <a name="coledatetime"></a>  COleDateTime::COleDateTime

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
COleDateTime(const DBTIMESTAMP& dbts) throw();
```

### <a name="parameters"></a>參數

*dateSrc*<br/>
將現有`COleDateTime`複製到新的物件`COleDateTime`物件。

*varSrc*<br/>
將現有`VARIANT`資料結構 (可能`COleVariant`物件) 轉換成日期/時間值 (VT_DATE)，並複製到新`COleDateTime`物件。

*dtSrc*<br/>
日期/時間 (`DATE`) 複製到新的值`COleDateTime`物件。

*timeSrc*<br/>
A`time_t`或是`__time64_t`值轉換成日期/時間值，並複製到新`COleDateTime`物件。

*systimeSrc*<br/>
A`SYSTEMTIME`結構轉換成日期/時間值，並複製到新`COleDateTime`物件。

*filetimeSrc*<br/>
A`FILETIME`結構轉換成日期/時間值，並複製到新`COleDateTime`物件。 請注意，`FILETIME`使用 Universal Coordinated Time (UTC)，因此如果您傳遞結構中的當地時間，結果將會不正確。 請參閱[檔案的時間](/windows/desktop/SysInfo/file-times)Windows sdk for 的詳細資訊。

*nYear*， *nMonth*， *n*，*當天的時數*， *nMin*， *nSec*  
表示要複製到新的日期和時間值`COleDateTime`物件。

*wDosDate*， *wDosTime*  
MS-DOS 日期和時間值轉換成日期/時間值，並複製到新`COleDateTime`物件。

*dbts*<br/>
參考[DBTimeStamp](https://msdn.microsoft.com/library/system.data.oledb.oledbtype)結構，包含目前的當地時間。

### <a name="remarks"></a>備註

所有這些建構函式建立新`COleDateTime`物件初始化為指定的值。 下表顯示每個日期和時間元件的有效範圍：

|日期/時間元件|有效範圍|
|--------------------------|-----------------|
|年|100 - 9999|
|月|0 - 12|
|天|0 - 31|
|小時|0 - 23|
|分鐘|0 - 59|
|第二個|0 - 59|

請注意，實際上限的日元件而異根據年份和月份元件。 如需詳細資訊，請參閱 <<c0> `SetDate` 或`SetDateTime`成員函式。

以下是每個建構函式的簡短描述：

- `COleDateTime(` **)** 建構`COleDateTime`物件初始化為 0 （午夜，30 年 12 月 1899年）。

- `COleDateTime(` `dateSrc` **)** 建構`COleDateTime`從現有的物件`COleDateTime`物件。

- `COleDateTime(` *varSrc* **)** 建構`COleDateTime`物件。 嘗試轉換`VARIANT`結構或[COleVariant](../../mfc/reference/colevariant-class.md)日期/時間的物件 ( `VT_DATE`) 值。 如果這項轉換成功，已轉換的值會複製到新`COleDateTime`物件。 如果不是，windows 7`COleDateTime`物件設定為 0 （午夜，30 年 12 月 1899年） 和其狀態變更為無效。

- `COleDateTime(` `dtSrc` **)** 建構`COleDateTime`物件從`DATE`值。

- `COleDateTime(` `timeSrc` **)** 建構`COleDateTime`物件從`time_t`值。

- `COleDateTime(` *systimeSrc* **)** 建構`COleDateTime`物件`SYSTEMTIME`值。

- `COleDateTime(` `filetimeSrc` **)** 建構`COleDateTime`物件從`FILETIME`值。 。 請注意，`FILETIME`使用 Universal Coordinated Time (UTC)，因此如果您傳遞結構中的當地時間，結果將會不正確。 請參閱[檔案的時間](/windows/desktop/SysInfo/file-times)Windows sdk for 的詳細資訊。

- `COleDateTime(` `nYear``nMonth`， `nDay`， `nHour`， `nMin`， `nSec` **)** 建構`COleDateTime`物件從指定的數值。

- `COleDateTime(` `wDosDate``wDosTime` **)** 建構`COleDateTime`從指定的 MS-DOS 日期和時間值的物件。

如需詳細資訊`time_t`資料類型，請參閱[時間](../../c-runtime-library/reference/time-time32-time64.md)函式中*執行階段程式庫參考*。

如需詳細資訊，請參閱 < [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)並[FILETIME](https://msdn.microsoft.com/library/windows/desktop/ms724284) Windows SDK 中的結構。

如需有關的界限`COleDateTime`值，請參閱文章[日期和時間： Automation 支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

> [!NOTE]
> 建構函式使用`DBTIMESTAMP`OLEDB.h 包含在內時，才可用參數。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#2](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_4.cpp)]

##  <a name="format"></a>  COleDateTime::Format

建立日期/時間值的格式化的表示。

```
CString Format(DWORD dwFlags = 0,  LCID lcid = LANG_USER_DEFAULT) const;
CString Format(LPCTSTR lpszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>參數

*dwFlags*<br/>
指出其中一個下列的地區設定旗標：

- LOCALE_NOUSEROVERRIDE 使用系統預設地區設定，而不是自訂使用者設定。

- VAR_TIMEVALUEONLY 在剖析期間忽略日期部分。

- VAR_DATEVALUEONLY 在剖析期間忽略之時間部分。

*lcid*<br/>
表示要用於轉換的地區設定識別碼。 如需有關語言識別碼的詳細資訊，請參閱 <<c0> [ 語言識別碼](/windows/desktop/Intl/language-identifiers)。

*lpszFormat*<br/>
格式化字串類似於`printf`格式化字串。 每個格式化程式碼，加上百分比 ( `%`) 登入，會取代對應`COleDateTime`元件。 格式化字串中的其他字元會複製到傳回的字串不變。 請參閱執行階段函式[strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)如需詳細資訊。 值和格式化的程式碼的意義`Format`是：

- `%H` 目前日期的小時

- `%M` 目前的小時的分鐘數

- `%S` 目前的分鐘的秒數

- `%%` 百分比符號

*nFormatID*<br/>
格式控制字串資源識別碼。

### <a name="return-value"></a>傳回值

A `CString` ，其中包含已格式化的日期/時間值。

### <a name="remarks"></a>備註

如果這個狀態`COleDateTime`物件為 null，則傳回的值為空字串。 如果狀態不正確，字串資源 ATL_IDS_DATETIME_INVALID 被指定傳回的字串。

此函式的三種形式的簡短描述如下：

`Format`( *dwFlags*， *lcid*)  
此表單會使用語言規格 （也就是地區設定識別碼） 將值格式化日期和時間。 使用預設參數，此表單會列印日期和時間，除非時間部分則為 0 （午夜），在此情況下它只會列印只是日期或日期部分是 0 (30 1899 年 12 月，) 在這種情況下，它會列印只的時間。 如果日期/時間值為 0 (30 年 12 月 1899 午夜)，這份表單的預設參數會列印午夜。

`Format`( *lpszFormat*)  
這種形式中使用格式字串，其中包含特殊格式化的程式碼會加上百分比符號 （%），來格式化值`printf`。 格式化的字串做為參數傳遞至函式。 如需格式化程式碼的詳細資訊，請參閱[strftime、 wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)執行階段程式庫參考中。

`Format`( *nFormatID*)  
這種形式中使用格式字串，其中包含特殊格式化的程式碼會加上百分比符號 （%），來格式化值`printf`。 格式化的字串是資源。 此字串資源的識別碼會當做參數傳遞。 如需格式化程式碼的詳細資訊，請參閱[strftime、 wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)中*執行階段程式庫參考*。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#3](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_5.cpp)]

##  <a name="getasdbtimestamp"></a>  COleDateTime::GetAsDBTIMESTAMP

呼叫這個方法來取得時間`COleDateTime`物件做為`DBTIMESTAMP`資料結構。

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```

### <a name="parameters"></a>參數

*dbts*<br/>
參考[DBTimeStamp](https://msdn.microsoft.com/library/system.data.oledb.oledbtype)結構。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

將產生的時間儲存在參考*dbts*結構。 `DBTIMESTAMP`由此函式初始化的資料結構會有其`fraction`成員設定為零。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#4](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_6.cpp)]

##  <a name="getassystemtime"></a>  COleDateTime::GetAsSystemTime

呼叫這個方法來取得時間`COleDateTime`物件做為`SYSTEMTIME`資料結構。

```
bool GetAsSystemTime(SYSTEMTIME& sysTime) const throw();
```

### <a name="parameters"></a>參數

*sysTime*<br/>
參考[SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)接收從已轉換的日期/時間值的結構`COleDateTime`物件。

### <a name="return-value"></a>傳回值

如果成功則傳回 TRUEFALSE 則轉換會失敗，則`COleDateTime`物件為 NULL 或無效。

### <a name="remarks"></a>備註

`GetAsSystemTime` 將產生的時間儲存在參考*sysTime*物件。 `SYSTEMTIME`由此函式初始化的資料結構會有其`wMilliseconds`成員設定為零。

請參閱[GetStatus](#getstatus)的更多有關的狀態資訊保留在`COleDateTime`物件。

##  <a name="getasudate"></a>  COleDateTime::GetAsUDATE

呼叫這個方法來取得時間`COleDateTime`物件做為`UDATE`資料結構。

```
bool GetAsUDATE(UDATE& udate) const throw();
```

### <a name="parameters"></a>參數

*udate*<br/>
參考`UDATE`結構，以接收已轉換的日期/時間值從`COleDateTime`物件。

### <a name="return-value"></a>傳回值

如果成功則傳回 TRUEFALSE 則轉換會失敗，則`COleDateTime`物件為 NULL 或無效。

### <a name="remarks"></a>備註

A`UDATE`結構代表 「 解壓縮 」 日期。

##  <a name="getcurrenttime"></a>  COleDateTime::GetCurrentTime

呼叫此靜態成員函式可傳回目前的日期/時間值。

```
static COleDateTime WINAPI GetCurrentTime() throw();
```

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#5](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_7.cpp)]

##  <a name="getday"></a>  COleDateTime::GetDay

取得此日期/時間值所表示月份天數。

```
int GetDay() const throw();
```

### <a name="return-value"></a>傳回值

這個值來表示月份天數`COleDateTime`物件或`COleDateTime::error`如果無法取得一天。

### <a name="remarks"></a>備註

有效的傳回值的範圍是介於 1 到 31 之間。

如需查詢的值，這個其他成員函式`COleDateTime`物件，請參閱下列成員函式：

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#6](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_8.cpp)]

##  <a name="getdayofweek"></a>  COleDateTime::GetDayOfWeek

取得此日期/時間值所表示月份天數。

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>傳回值

這個值來表示星期幾`COleDateTime`物件或`COleDateTime::error`如果無法取得的一週天數。

### <a name="remarks"></a>備註

有效的傳回值的範圍是介於 1 到 7 之間，其中 1 = 星期日，2 = 星期一，依此類推。

如需查詢的值，這個其他成員函式`COleDateTime`物件，請參閱下列成員函式：

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#7](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_9.cpp)]

##  <a name="getdayofyear"></a>  COleDateTime::GetDayOfYear

取得此日期/時間值所表示之年份的日期。

```
int GetDayOfYear() const throw();
```

### <a name="return-value"></a>傳回值

這個值所表示的一年天數`COleDateTime`物件或`COleDateTime::error`如果無法取得的一年天數。

### <a name="remarks"></a>備註

有效的傳回值的範圍是 1 到 366 之間，其中 1 年 1 月 = 1。

如需查詢的值，這個其他成員函式`COleDateTime`物件，請參閱下列成員函式：

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#8](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_10.cpp)]

##  <a name="gethour"></a>  COleDateTime::GetHour

取得此日期/時間值所表示的小時。

```
int GetHour() const throw();
```

### <a name="return-value"></a>傳回值

這個值所表示的小時`COleDateTime`物件或`COleDateTime::error`如果無法取得在一小時。

### <a name="remarks"></a>備註

有效的傳回值的範圍是介於 0 到 23 之間。

如需查詢的值，這個其他成員函式`COleDateTime`物件，請參閱下列成員函式：

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#9](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_11.cpp)]

##  <a name="getminute"></a>  COleDateTime::GetMinute

取得此日期/時間值所表示分鐘。

```
int GetMinute() const throw();
```

### <a name="return-value"></a>傳回值

這個值所表示分鐘`COleDateTime`物件或`COleDateTime::error`如果無法取得分鐘數。

### <a name="remarks"></a>備註

有效的傳回值範圍介於 0 到 59 之間。

如需查詢的值，這個其他成員函式`COleDateTime`物件，請參閱下列成員函式：

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>範例

範例，請參閱[GetHour](#gethour)。

##  <a name="getmonth"></a>  COleDateTime::GetMonth

取得此日期/時間值所表示的月份。

```
int GetMonth() const throw();
```

### <a name="return-value"></a>傳回值

這個值所表示的月份`COleDateTime`物件或`COleDateTime::error`如果無法取得月份。

### <a name="remarks"></a>備註

有效的傳回值的範圍是 1 到 12 之間。

如需查詢的值，這個其他成員函式`COleDateTime`物件，請參閱下列成員函式：

- [GetDay](#getday)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>範例

範例，請參閱[GetDay](#getday)。

##  <a name="getsecond"></a>  COleDateTime::GetSecond

取得此日期/時間值所表示的第二個。

```
int GetSecond() const throw();
```

### <a name="return-value"></a>傳回值

這個值來表示第二個`COleDateTime`物件或`COleDateTime::error`如果無法取得第二個。

### <a name="remarks"></a>備註

有效的傳回值範圍介於 0 到 59 之間。

> [!NOTE]
>  `COleDateTime`類別不支援閏秒。

如需有關實作`COleDateTime`，請參閱文章[日期和時間： Automation 支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

如需查詢的值，這個其他成員函式`COleDateTime`物件，請參閱下列成員函式：

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>範例

範例，請參閱[GetHour](#gethour)。

##  <a name="getstatus"></a>  COleDateTime::GetStatus

取得狀態 （有效性） 指定`COleDateTime`物件。

```
DateTimeStatus GetStatus() const throw();
```

### <a name="return-value"></a>傳回值

傳回這個狀態`COleDateTime`值。 如果您呼叫`GetStatus`上`COleDateTime`含有預設建構物件，它會傳回有效。 如果您呼叫`GetStatus`上`COleDateTime`物件的建構函式設定為 null，初始化`GetStatus`會傳回 null。 請參閱**備註**如需詳細資訊。

### <a name="remarks"></a>備註

傳回值由定義`DateTimeStatus`列舉型別，其定義內`COleDateTime`類別。

```
enum DateTimeStatus  
{  
   error = -1,  
   valid = 0,  
   invalid = 1,    // Invalid date (out of range, etc.)  
   null = 2,       // Literally has no value  
};  
```

如這些狀態值的簡短描述，請參閱下列清單：

- `COleDateTime::error` 表示嘗試取得日期/時間值的一部分時，發生錯誤。

- `COleDateTime::valid` 指出這個`COleDateTime`物件是否有效。

- `COleDateTime::invalid` 指出這個`COleDateTime`物件無效，也就是它的值可能不正確。

- `COleDateTime::null` 指出這個`COleDateTime`物件為 null，也就是這個物件尚未提供任何值。 （這是"null"中資料庫的 「 沒有值，"而不是 c + + NULL）。

狀態`COleDateTime`在下列情況中的物件無效：

- 如果其值將來自`VARIANT`或`COleVariant`無法轉換成日期/時間值的值。

- 如果其值將來自`time_t`， `SYSTEMTIME`，或`FILETIME`無法轉換為有效的日期/時間值的值。

- 如果其值由設定`SetDateTime`具有無效的參數值。

- 如果這個物件發生溢位或反向溢位算術的指派作業期間，亦即`+=`或`-=`。

- 如果無效的值已指派給這個物件。

- 如果此物件的狀態已明確設定為無效的使用`SetStatus`。

如需詳細的作業，也可能設定的狀態無效，請參閱下列成員函式的詳細資訊：

- [COleDateTime](#coledatetime)

- [SetDateTime](#setdatetime)

- [運算子 +、-](#operator_add_-)

- [運算子 + =、 =](#operator_add_eq_-_eq)

如需有關的界限`COleDateTime`值，請參閱文章[日期和時間： Automation 支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#10](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_12.cpp)]

##  <a name="getyear"></a>  COleDateTime::GetYear

取得此日期/時間值所表示的年份。

```
int GetYear() const throw();
```

### <a name="return-value"></a>傳回值

這個值所表示的年份`COleDateTime`物件或`COleDateTime::error`如果無法取得一年。

### <a name="remarks"></a>備註

傳回有效值的範圍介於 100 到 9999，其中包含一個世紀。

如需查詢的值，這個其他成員函式`COleDateTime`物件，請參閱下列成員函式：

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

如需有關的界限`COleDateTime`值，請參閱文章[日期和時間： Automation 支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

### <a name="example"></a>範例

範例，請參閱[GetDay](#getday)。

##  <a name="m_dt"></a>  COleDateTime::m_dt

基礎`DATE`這個結構`COleDateTime`物件。

```
DATE m_dt;
```

### <a name="remarks"></a>備註

> [!CAUTION]
>  變更中的值`DATE`物件存取這個函式所傳回的指標會變更這個值`COleDateTime`物件。 它不會變更這個狀態`COleDateTime`物件。

如需實作的詳細資訊`DATE`物件，請參閱文章[日期和時間： Automation 支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

##  <a name="m_status"></a>  COleDateTime::m_status

包含這個狀態`COleDateTime`物件。

```
DateTimeStatus m_status;
```

### <a name="remarks"></a>備註

此資料成員的類型是列舉型別`DateTimeStatus`，其定義內`COleDateTime`類別。 請參閱[COleDateTime::GetStatus](#getstatus)如需詳細資訊。

> [!CAUTION]
>  此資料成員是針對進階程式設計的情況。 您應該使用的內嵌成員函式[GetStatus](#getstatus)並[SetStatus](#setstatus)。 請參閱`SetStatus`的進一步注意事項，關於明確設定此資料成員。

##  <a name="operator_eq"></a>  COleDateTime::operator =

複製`COleDateTime`值。

```
COleDateTime& operator=(const VARIANT& varSrc) throw();
COleDateTime& operator=(DATE dtSrc) throw();
COleDateTime& operator=(const time_t& timeSrc) throw();
COleDateTime& operator=(const __time64_t& timeSrc) throw();
COleDateTime& operator=(const SYSTEMTIME& systimeSrc) throw();
COleDateTime& operator=(const FILETIME& filetimeSrc) throw();
COleDateTime& operator=(const UDATE& udate) throw();
```

### <a name="remarks"></a>備註

這些多載的指派運算子會將來源的日期/時間值複製到這個`COleDateTime`物件。 簡短描述每一個這類多載指派運算子如下所示：

- **運算子 = (** `dateSrc` **)** 的值和運算元的狀態複製到這個`COleDateTime`物件。

- **運算子 = (** *varSrc* **)** 如果轉換[VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant)值 (或[COleVariant](../../mfc/reference/colevariant-class.md)物件) 至日期/時間 (VT_日期） 成功，已轉換的值會複製到這個`COleDateTime`物件和其狀態設為有效。 如果轉換不成功，這個物件的值設為零 (30 年 12 月 1899 午夜) 和其狀態變更為無效。

- **運算子 = (** `dtSrc` **)** `DATE`值會複製到這個`COleDateTime`物件和其狀態設為有效。

- **運算子 = (** `timeSrc` **)** `time_t`或是`__time64_t`值會轉換並複製到這個`COleDateTime`物件。 如果轉換成功，這個物件的狀態設定為有效的;如果不成功，它會設定為無效。

- **運算子 = (** *systimeSrc* **)** [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)值會轉換並複製到這個`COleDateTime`物件。 如果轉換成功，這個物件的狀態設定為有效的;如果不成功，它會設定為無效。

- **運算子 = (** `udate` **)** `UDATE`值會轉換並複製到這個`COleDateTime`物件。 如果轉換成功，這個物件的狀態設定為有效的;如果不成功，它會設定為無效。 A`UDATE`結構代表 「 解壓縮 」 日期。 請參閱函數[VarDateFromUdate](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-vardatefromudate)如需詳細資訊。

- **運算子 = (** `filetimeSrc` **)** [FILETIME](https://msdn.microsoft.com/library/windows/desktop/ms724284)值會轉換並複製到這個`COleDateTime`物件。 如果轉換成功，這個物件的狀態設定為有效的;否則，會設定為無效。 `FILETIME` 使用全球定位時間 (UTC)，因此為 UTC 時間結構中，您的結果會從 UTC 時間轉換為當地時間，而且將會儲存為 variant 的時間。 此行為是與 Visual c + + 6.0 和 Visual c + +.NET 2003 SP2 相同。 請參閱[檔案的時間](/windows/desktop/SysInfo/file-times)Windows sdk for 的詳細資訊。

如需詳細資訊，請參閱 < [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant) Windows SDK 中的項目。

如需詳細資訊`time_t`資料類型，請參閱[時間](../../c-runtime-library/reference/time-time32-time64.md)函式中*執行階段程式庫參考*。

如需詳細資訊，請參閱 < [SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)並[FILETIME](https://msdn.microsoft.com/library/windows/desktop/ms724284) Windows SDK 中的結構。

如需有關的界限`COleDateTime`值，請參閱文章[日期和時間： Automation 支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

##  <a name="operator_add_-"></a>  COleDateTime::operator +、-

加法和減法`ColeDateTime`值。

```
COleDateTime operator+(COleDateTimeSpan dateSpan) const throw();
COleDateTime operator-(COleDateTimeSpan dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTime& date) const throw();
```

### <a name="remarks"></a>備註

`COleDateTime` 物件代表絕對的時間。 [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)物件表示相對的時間。 前兩個運算子可讓您加入和減去`COleDateTimeSpan`值從`COleDateTime`值。 第三個運算子可讓您減一`COleDateTime`值來產生`COleDateTimeSpan`值。

如果任一個運算元是 null，結果狀態`COleDateTime`值是 null。

如果產生`COleDateTime`值超出可接受的值，該狀態的界限`COleDateTime`值無效。

如果任一運算元無效，而且其他不是 null，結果狀態`COleDateTime`值無效。

**+** 並**-** 運算子會判斷提示，如果`COleDateTime`物件設定為 null。 請參閱[COleDateTime 關係運算子](#coledatetime_relational_operators)的範例。

如需有關有效、 無效和 null 的狀態值的詳細資訊，請參閱[m_status](#m_status)成員變數。

如需有關的界限`COleDateTime`值，請參閱文章[日期和時間： Automation 支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#12](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_13.cpp)]

##  <a name="operator_add_eq_-_eq"></a>  COleDateTime::operator + =、 =

加法和減法`ColeDateTime`值從這個`COleDateTime`物件。

```
COleDateTime& operator+=(COleDateTimeSpan dateSpan) throw();
COleDateTime& operator-=(COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>備註

這些運算子可讓您加入和減去`COleDateTimeSpan`值與這個`COleDateTime`。 如果任一個運算元是 null，結果狀態`COleDateTime`值是 null。

如果產生`COleDateTime`值超出可接受的值，這個狀態的界限`COleDateTime`值設定為無效。

如果任一運算元無效，而且其他不是 null，結果狀態`COleDateTime`值無效。

如需有關有效、 無效和 null 的狀態值的詳細資訊，請參閱[m_status](#m_status)成員變數。

**+=** 並**-=** 運算子會判斷提示，如果`COleDateTime`物件設定為 null。 請參閱[COleDateTime 關係運算子](#coledatetime_relational_operators)的範例。

如需有關的界限`COleDateTime`值，請參閱文章[日期和時間： Automation 支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

##  <a name="operator_date"></a>  COleDateTime::operator 日期

將轉換`ColeDateTime`值貼`DATE`。

```
operator DATE() const throw();
```

### <a name="remarks"></a>備註

這個運算子會傳回`DATE`物件，其值從這個複製`COleDateTime`物件。 如需實作的詳細資訊`DATE`物件，請參閱文章[日期和時間： Automation 支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

`DATE`運算子會判斷提示，如果`COleDateTime`物件設定為 null。 請參閱[COleDateTime 關係運算子](#coledatetime_relational_operators)的範例。

##  <a name="parsedatetime"></a>  COleDateTime::ParseDateTime

剖析字串，以讀取日期/時間值。

```
bool ParseDateTime(  
LPCTSTR lpszDate,
DWORD dwFlags = 0,
LCID lcid = LANG_USER_DEFAULT) throw();
```

### <a name="parameters"></a>參數

*lpszDate*<br/>
要剖析的 null 終止字串指標。 如需詳細資料，請參閱＜備註＞。

*dwFlags*<br/>
表示地區設定和剖析的旗標。 一或多個下列旗標：

- LOCALE_NOUSEROVERRIDE 使用系統預設地區設定，而不是自訂使用者設定。

- VAR_TIMEVALUEONLY 在剖析期間忽略日期部分。

- VAR_DATEVALUEONLY 在剖析期間忽略之時間部分。

*lcid*<br/>
表示要用於轉換的地區設定識別碼。

### <a name="return-value"></a>傳回值

為 true，則會傳回字串已成功轉換為日期/時間值，否則為 FALSE。

### <a name="remarks"></a>備註

如果成功轉換為日期/時間的字串值，這個值`COleDateTime`物件設定為該值與其狀態變更為有效。

> [!NOTE]
>  年份值必須介於 100 到 9999 之間 （含） 之間。

*LpszDate*參數可以採用各種格式。 例如，下列字串會包含可接受的日期/時間格式：

`"25 January 1996"`

`"8:30:00"`

`"20:30:00"`

`"January 25, 1996 8:30:00"`

`"8:30:00 Jan. 25, 1996"`

`"1/25/1996 8:30:00"  // always specify the full year, even in a 'short date' format`

請注意，地區設定識別碼也會影響是否可接受的轉換成日期/時間值的字串格式。

如果 VAR_DATEVALUEONLY，時間值設定為 0 或午夜的時間。 如果 VAR_TIMEVALUEONLY，日期值設定為日期 0，這表示 30 年 12 月 1899年。

如果字串無法轉換成日期/時間值，或發生數值溢位，這個狀態`COleDateTime`物件無效。

如需有關繫結和實作`COleDateTime`值，請參閱文章[日期和時間： Automation 支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

##  <a name="setdate"></a>  COleDateTime::SetDate

設定這個日期`COleDateTime`物件。

```
int SetDate(  
int nYear,
int nMonth,
int nDay) throw();
```

### <a name="parameters"></a>參數

*nYear*， *nMonth*， *n*  
表示要複製到這個的日期元件`COleDateTime`物件。

### <a name="return-value"></a>傳回值

如果這個值`COleDateTime`物件已設定成功，則為 1。 這個傳回值根據`DateTimeStatus`列舉型別。 如需詳細資訊，請參閱 < [SetStatus](#setstatus)成員函式。

### <a name="remarks"></a>備註

日期會設定為指定的值。 時間設定時間 0，午夜。

請參閱下表中的參數值的範圍：

|參數|繫結|
|---------------|------------|
|*nYear*|100 - 9999|
|*nMonth*|1 - 12|
|*n*|0 - 31|

如果月份天數溢位，則會轉換成正確的下個月和月份日期及/或年份會隨之遞增。 一天的值為零表示上一個月份的最後一天。 行為是相同`SystemTimeToVariantTime`。

如果參數所指定的日期值無效，此物件的狀態設為`COleDateTime::invalid`。 您應該使用[GetStatus](#getstatus)若要檢查的有效性`DATE`值，而且不應該假設的值[m_dt](#m_dt)會保持不變。

以下是日期值的一些範例：

|*nYear*|*nMonth*|*n*|值|
|-------------|--------------|------------|-----------|
|2000|2|29|29 年 2 月 2000|
|1776|7|4|4 年 7 月 1776|
|1925|4|35|35 年 4 月 1925 （無效的日期）|
|10000|1|1|1 年 1 月 10000 （無效的日期）|

若要設定日期和時間，請參閱[COleDateTime::SetDateTime](#setdatetime)。

如需查詢這些值的成員函式`COleDateTime`物件，請參閱下列成員函式：

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

如需有關的界限`COleDateTime`值，請參閱文章[日期和時間： Automation 支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#11](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_14.cpp)]

##  <a name="setdatetime"></a>  COleDateTime::SetDateTime

設定日期和時間，這個`COleDateTime`物件。

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

*nYear*， *nMonth*， *n*，*當天的時數*， *nMin*， *nSec*  
表示要複製到這個日期和時間元件`COleDateTime`物件。

### <a name="return-value"></a>傳回值

如果這個值`COleDateTime`物件已設定成功，則為 1。 這個傳回值根據`DateTimeStatus`列舉型別。 如需詳細資訊，請參閱 < [SetStatus](#setstatus)成員函式。

### <a name="remarks"></a>備註

請參閱下表中的參數值的範圍：

|參數|繫結|
|---------------|------------|
|*nYear*|100 - 9999|
|*nMonth*|1 - 12|
|*n*|0 - 31|
|*當天的時數*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

如果月份天數溢位，則會轉換成正確的下個月和月份日期及/或年份會隨之遞增。 一天的值為零表示上一個月份的最後一天。 行為是相同[SystemTimeToVariantTime](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-systemtimetovarianttime)。

如果參數所指定的日期或時間值不是有效的這個物件的狀態設為無效，此物件的值不會變更。

以下是時間值的一些範例：

|*當天的時數*|*nMin*|*nSec*|值|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|無效的|
|9|60|0|無效的|

以下是日期值的一些範例：

|*nYear*|*nMonth*|*n*|值|
|-------------|--------------|------------|-----------|
|1995|4|15|15 年 4 月 1995 年|
|1789|7|14|17 年 7 月 1789|
|1925|2|30|無效的|
|10000|1|1|無效的|

若要設定日期，請參閱[COleDateTime::SetDate](#setdate)。 若要設定時，請參閱[COleDateTime::SetTime](#settime)。

如需查詢這些值的成員函式`COleDateTime`物件，請參閱下列成員函式：

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

如需有關的界限`COleDateTime`值，請參閱文章[日期和時間： Automation 支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

### <a name="example"></a>範例

範例，請參閱[GetStatus](#getstatus)。

##  <a name="setstatus"></a>  COleDateTime::SetStatus

設定這個狀態`COleDateTime`物件。

```
void SetStatus(DateTimeStatus status) throw();
```

### <a name="parameters"></a>參數

*status*<br/>
這個新的狀態值`COleDateTime`物件。

### <a name="remarks"></a>備註

*狀態*參數值由定義`DateTimeStatus`列舉型別，其定義內`COleDateTime`類別。 請參閱[COleDateTime::GetStatus](#getstatus)如需詳細資訊。

> [!CAUTION]
>  此函式是進階程式設計的情況。 此函式不會更改此物件中的資料。 它將最常使用的狀態設為**null**或是**無效**。 請注意，指派運算子 ([運算子 =](#eq)) 和[SetDateTime](#setdatetime)沒有設定的基礎來源值的物件狀態。

### <a name="example"></a>範例

範例，請參閱[GetStatus](#getstatus)。

##  <a name="settime"></a>  COleDateTime::SetTime

設定這個時間`COleDateTime`物件。

```
int SetTime(  
int nHour,
int nMin,
int nSec) throw();
```

### <a name="parameters"></a>參數

*當天的時數*， *nMin*， *nSec*  
表示要複製到這個階段元件`COleDateTime`物件。

### <a name="return-value"></a>傳回值

如果這個值`COleDateTime`物件已設定成功，則為 1。 這個傳回值根據`DateTimeStatus`列舉型別。 如需詳細資訊，請參閱 < [SetStatus](#setstatus)成員函式。

### <a name="remarks"></a>備註

時間設定為指定的值。 日期會設定日期 0，這表示 30 年 12 月 1899年。

請參閱下表中的參數值的範圍：

|參數|繫結|
|---------------|------------|
|*當天的時數*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

如果的時間參數所指定的值不是有效的這個物件的狀態設為無效，此物件的值不會變更。

以下是時間值的一些範例：

|*當天的時數*|*nMin*|*nSec*|值|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|無效的|
|9|60|0|無效的|

若要設定日期和時間，請參閱[COleDateTime::SetDateTime](#setdatetime)。

如需查詢這些值的成員函式`COleDateTime`物件，請參閱下列成員函式：

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

如需有關的界限`COleDateTime`值，請參閱文章[日期和時間： Automation 支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

### <a name="example"></a>範例

範例，請參閱[SetDate](#setdate)。

## <a name="see-also"></a>另請參閱

[COleVariant 類別](../../mfc/reference/colevariant-class.md)<br/>
[CTime 類別](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan 類別](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)

