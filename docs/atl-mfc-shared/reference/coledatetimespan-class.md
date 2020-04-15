---
title: COleDateTimeSpan 類別
ms.date: 03/27/2019
f1_keywords:
- COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::Format
- ATLCOMTIME/ATL::COleDateTimeSpan::GetDays
- ATLCOMTIME/ATL::COleDateTimeSpan::GetHours
- ATLCOMTIME/ATL::COleDateTimeSpan::GetMinutes
- ATLCOMTIME/ATL::COleDateTimeSpan::GetSeconds
- ATLCOMTIME/ATL::COleDateTimeSpan::GetStatus
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalDays
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalHours
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalMinutes
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalSeconds
- ATLCOMTIME/ATL::COleDateTimeSpan::SetDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::SetStatus
- ATLCOMTIME/ATL::COleDateTimeSpan::m_span
- ATLCOMTIME/ATL::COleDateTimeSpan::m_status
helpviewer_keywords:
- timespan
- time span
- shared classes, COleDateTimeSpan
- Date data type, MFC encapsulation of
- COleDateTimeSpan class
ms.assetid: 7441526d-a30a-4019-8fb3-3fee6f897cbe
ms.openlocfilehash: 7173fa0b6261ea718a02d399d944a1b5bb98b9f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317733"
---
# <a name="coledatetimespan-class"></a>COleDateTimeSpan 類別

表示相對時間、時間跨度。

## <a name="syntax"></a>語法

```
class COleDateTimeSpan
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleDate時間跨度:COleDatetimeSpan](#coledatetimespan)|建構 `COleDateTimeSpan` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleDate時間跨度::格式](#format)|生成`COleDateTimeSpan`物件的格式化字串表示形式。|
|[COleDate時間跨度:取得天數](#getdays)|返回此`COleDateTimeSpan`物件表示的跨值的天部分。|
|[COleDateTimeSpan:取得小時數](#gethours)|返回此`COleDateTimeSpan`物件表示的跨值的小時部分。|
|[COleDateTimeSpan:取得分鐘數](#getminutes)|返回此`COleDateTimeSpan`物件表示的跨值的分鐘部分。|
|[COleDate時間跨度:取得秒數](#getseconds)|返回此`COleDateTimeSpan`物件表示的跨範圍的第二部分。|
|[COleDate 時間跨度:取得狀態](#getstatus)|獲取此`COleDateTimeSpan`物件的狀態(有效性)。|
|[COleDate時間跨度:取得總天數](#gettotaldays)|返回此`COleDateTimeSpan`物件表示的天數。|
|[COleDateTimeSpan:取得總小時數](#gettotalhours)|返回此`COleDateTimeSpan`物件表示的小時數。|
|[COleDateTimeSpan:取得總分鐘數](#gettotalminutes)|返回此`COleDateTimeSpan`物件表示的分鐘數。|
|[COleDate時間跨度::取得總秒數](#gettotalseconds)|返回此`COleDateTimeSpan`物件表示的秒數。|
|[COleDate時間跨度::設定時間跨度](#setdatetimespan)|設置此`COleDateTimeSpan`物件的值。|
|[COleDate 時間跨度::設定狀態](#setstatus)|設置此`COleDateTimeSpan`物件的狀態(有效性)。|

### <a name="public-operators"></a>公用運算子

|||
|-|-|
|[運算符 +, -](#operator_add_-)|添加、減去和更改值的`COleDateTimeSpan`符號。|
|[運算子 *, -]](#operator_add_eq_-_eq)|從此值`COleDateTimeSpan`中添加`COleDateTimeSpan`和減去值。|
|[運算符 |](#operator_eq)|複製值`COleDateTimeSpan`。|
|[運算符 =、<、<|](#coledatetimespan_relational_operators)|比較兩`COleDateTimeSpan`個值。|
|[運算子 double](#operator_double)|將此值`COleDateTimeSpan`轉換為**雙精度**值。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COleDate 時間跨度::m_span](#m_span)|包含此`COleDateTimeSpan`物件的基礎**雙精度值**。|
|[COleDate時間跨度::m_status](#m_status)|包含此`COleDateTimeSpan`物件的狀態。|

## <a name="remarks"></a>備註

`COleDateTimeSpan`沒有基類。

A`COleDateTimeSpan`以天保持時間。

`COleDateTimeSpan`使用[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)。 `COleDateTime`封裝 OLE`DATE`自動化的數據類型。 `COleDateTime`表示絕對時間值。 所有`COleDateTime`計算都涉及`COleDateTimeSpan`值。 這些類別之間的關係類似於 CTime 和[CTimeSpan](../../atl-mfc-shared/reference/ctime-class.md)之間的關係[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)。

有關`COleDateTime``COleDateTimeSpan`和類的詳細資訊,請參閱文章[「日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)」。。

## <a name="requirements"></a>需求

**標題:** ATLComTime.h

## <a name="coledatetimespan-relational-operators"></a><a name="coledatetimespan_relational_operators"></a>COleDateTimeSpan關係運算子

比較運算符。

```
bool operator==(const COleDateTimeSpan& dateSpan) const throw();
bool operator!=(const COleDateTimeSpan& dateSpan) const throw();
bool operator<(const COleDateTimeSpan& dateSpan) const throw();
bool operator>(const COleDateTimeSpan& dateSpan) const throw();
bool operator<=(const COleDateTimeSpan& dateSpan) const throw();
bool operator>=(const COleDateTimeSpan& dateSpan) const throw();
```

### <a name="parameters"></a>參數

*日期斯潘*<br/>
要比較的 `COleDateTimeSpan`。

### <a name="return-value"></a>傳回值

這些運算元比較兩個日期/時間跨度值,如果條件為 true,則返回 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

> [!NOTE]
> 如果任一操作數無效,將發生 ATLASSERT。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#25](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#26](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_2.cpp)]

## <a name="coledatetimespancoledatetimespan"></a><a name="coledatetimespan"></a>COleDate時間跨度:COleDatetimeSpan

建構 `COleDateTimeSpan` 物件。

```
COleDateTimeSpan() throw();
COleDateTimeSpan(double dblSpanSrc) throw();
COleDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>參數

*德布爾斯潘斯克*<br/>
要複製到新`COleDateTimeSpan`物件的天數。

*l 天*, *nHours*, *nMins*, *nSecs*<br/>
指示要複製到新`COleDateTimeSpan`物件的日時值。

### <a name="remarks"></a>備註

所有這些構造函數都創建新`COleDateTimeSpan`的物件,初始化到指定值。 每個構造函數的簡要描述如下:

- **COleDateTimeSpan)** 建構初始化`COleDateTimeSpan`為 0 的物件。

- **COleDateTimeSpan)** `dblSpanSrc` **)** 從浮點`COleDateTimeSpan`值構造物件。

- **COleDateTimeSpan(** `lDays` **,** `nHours` **,** `nMins` **,** `nSecs` **)** 建構初始化`COleDateTimeSpan`為指定數值的物件。

新`COleDateTimeSpan`物件的狀態設置為有效。

有關`COleDateTimeSpan`值邊界的詳細資訊,請參閱文章[「日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)」。。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#14](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_3.cpp)]

## <a name="coledatetimespanformat"></a><a name="format"></a>COleDate時間跨度::格式

生成`COleDateTimeSpan`物件的格式化字串表示形式。

```
CString Format(LPCTSTR pFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>參數

*p格式*<br/>
類似於格式字串的`printf`格式字串。 格式代碼(前面為百分比`%`( ) 符號`COleDateTimeSpan`,由相應的 元件替換。 格式字串中的其他字元將複製到傳回的字串。 下面列出格式化`Format`代碼的值與含義:

- **%H**當天的小時數

- **%M**目前的小時內的分鐘數

- **%S**目前分鐘中的秒數

- **%%** 百分比符號

上面列出的四個格式代碼是格式將接受的唯一代碼。

-

*nID*<br/>
格式控制字串的資源識別碼。

### <a name="return-value"></a>傳回值

包含`CString`格式化日期/時間跨度值的 。

### <a name="remarks"></a>備註

調用這些函數以創建時間跨度值的格式化表示形式。 如果此`COleDateTimeSpan`物件的狀態為 null,則傳回值為空字串。 如果狀態無效,則返回字串由字串資源IDS_INVALID_DATETIMESPAN指定。

此函數的表單的簡要說明如下:

**格式(** *pFormat* **)**<br/>
此表單使用格式字串設定值,該格式字串包含特殊格式碼,前面有百分比符號 (%),如中`printf`。 格式化字串作為參數傳遞給函數。

**格式***(nID)* **)**<br/>
此表單使用格式字串設定值,該格式字串包含特殊格式碼,前面有百分比符號 (%),如中`printf`。 格式化字串是一個資源。 此字串資源的 ID 作為參數傳遞。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#15](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_4.cpp)]

## <a name="coledatetimespangetdays"></a><a name="getdays"></a>COleDate時間跨度:取得天數

檢索此日期/時間跨度值的天部分。

```
LONG GetDays() const throw();
```

### <a name="return-value"></a>傳回值

此日期/時間跨度值的日部分。

### <a name="remarks"></a>備註

此函數的返回值介於大約 - 3,615,000 和 3,615,000 之間。

對於查詢`COleDateTimeSpan`物件值的其他函數,請參閱以下成員函數:

- [GetHours](#gethours)

- [取得分鐘](#getminutes)

- [取得秒數](#getseconds)

- [取得總天數](#gettotaldays)

- [取得總小時數](#gettotalhours)

- [取得總分鐘數](#gettotalminutes)

- [取得總秒數](#gettotalseconds)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#16](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_5.cpp)]

## <a name="coledatetimespangethours"></a><a name="gethours"></a>COleDateTimeSpan:取得小時數

檢索此日期/時間跨度值的小時部分。

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>傳回值

此日期/時間跨度值的工時部分。

### <a name="remarks"></a>備註

此函數的返回值範圍介於 - 23 和 23 之間。

對於查詢`COleDateTimeSpan`物件值的其他函數,請參閱以下成員函數:

- [取得天數](#getdays)

- [取得分鐘](#getminutes)

- [取得秒數](#getseconds)

- [取得總天數](#gettotaldays)

- [取得總小時數](#gettotalhours)

- [取得總分鐘數](#gettotalminutes)

- [取得總秒數](#gettotalseconds)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#17](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_6.cpp)]

## <a name="coledatetimespangetminutes"></a><a name="getminutes"></a>COleDateTimeSpan:取得分鐘數

檢索此日期/時間跨度值的分鐘部分。

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>傳回值

此日期/時間跨度值的分鐘部分。

### <a name="remarks"></a>備註

此函數的返回值範圍介於 - 59 和 59 之間。

對於查詢`COleDateTimeSpan`物件值的其他函數,請參閱以下成員函數:

- [取得天數](#getdays)

- [GetHours](#gethours)

- [取得秒數](#getseconds)

- [取得總天數](#gettotaldays)

- [取得總小時數](#gettotalhours)

- [取得總分鐘數](#gettotalminutes)

- [取得總秒數](#gettotalseconds)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#18](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_7.cpp)]

## <a name="coledatetimespangetseconds"></a><a name="getseconds"></a>COleDate時間跨度:取得秒數

檢索此日期/時間跨度值的第二部分。

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>傳回值

此日期/時間跨度值的秒部分。

### <a name="remarks"></a>備註

此函數的返回值範圍介於 - 59 和 59 之間。

對於查詢`COleDateTimeSpan`物件值的其他函數,請參閱以下成員函數:

- [取得天數](#getdays)

- [GetHours](#gethours)

- [取得分鐘](#getminutes)

- [取得總天數](#gettotaldays)

- [取得總小時數](#gettotalhours)

- [取得總分鐘數](#gettotalminutes)

- [取得總秒數](#gettotalseconds)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#19](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_8.cpp)]

## <a name="coledatetimespangetstatus"></a><a name="getstatus"></a>COleDate 時間跨度:取得狀態

獲取此`COleDateTimeSpan`物件的狀態(有效性)。

```
DateTimeSpanStatus GetStatus() const throw();
```

### <a name="return-value"></a>傳回值

此值`COleDateTimeSpan`的狀態。

### <a name="remarks"></a>備註

返回值由`DateTimeSpanStatus`枚舉類型定義,該類型在類`COleDateTimeSpan`中 定義。

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
};
```

有關這些狀態值的簡要說明,請參閱以下清單:

- `COleDateTimeSpan::valid`指示此`COleDateTimeSpan`物件有效。

- `COleDateTimeSpan::invalid`指示此物件`COleDateTimeSpan`無效;如果表明此物件無效。也就是說,其值可能不正確。

- `COleDateTimeSpan::null`指示此`COleDateTimeSpan`物件為 null,即未為此物件提供任何值。 (這是"無值"的資料庫意義上的"空",而不是C++ NULL。

在以下情況下,`COleDateTimeSpan`物件的狀態無效:

- 如果此物件在算術賦值操作期間(即`+=``-=`或 ) 經歷了溢出或下溢。

- 如果為此物件分配了無效值。

- 如果此物件的狀態被顯式設定為無效使用`SetStatus`。

有關可能將狀態設定為無效的操作的詳細資訊,請參閱[COleDateTimeSpan::運算符 *,-](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-)和[COleDateTimeSpan::運算符 *,-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq)。

有關`COleDateTimeSpan`值邊界的詳細資訊,請參閱文章[「日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)」。。

## <a name="coledatetimespangettotaldays"></a><a name="gettotaldays"></a>COleDate時間跨度:取得總天數

檢索以天表示的此日期/時間跨度值。

```
double GetTotalDays() const throw();
```

### <a name="return-value"></a>傳回值

此日期/時間跨度值以天表示。 儘管此函數是原型返回 double,但它始終將返回整數值。

### <a name="remarks"></a>備註

此函數的返回值介於大約 - 3.65e6 和 3.65e6 之間。

對於查詢`COleDateTimeSpan`物件值的其他函數,請參閱以下成員函數:

- [取得天數](#getdays)

- [GetHours](#gethours)

- [取得分鐘](#getminutes)

- [取得秒數](#getseconds)

- [取得總小時數](#gettotalhours)

- [取得總分鐘數](#gettotalminutes)

- [取得總秒數](#gettotalseconds)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#20](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_9.cpp)]

## <a name="coledatetimespangettotalhours"></a><a name="gettotalhours"></a>COleDateTimeSpan:取得總小時數

檢索以小時表示的此日期/時間跨度值。

```
double GetTotalHours() const throw();
```

### <a name="return-value"></a>傳回值

此日期/時間跨度值以小時表示。 儘管此函數是原型返回 double,但它始終將返回整數值。

### <a name="remarks"></a>備註

此函數的返回值介於大約 - 8.77e7 和 8.77e7 之間。

對於查詢`COleDateTimeSpan`物件值的其他函數,請參閱以下成員函數:

- [取得天數](#getdays)

- [GetHours](#gethours)

- [取得分鐘](#getminutes)

- [取得秒數](#getseconds)

- [取得總天數](#gettotaldays)

- [取得總分鐘數](#gettotalminutes)

- [取得總秒數](#gettotalseconds)

### <a name="example"></a>範例

請參考[GetTotalDays 的範例](#gettotaldays)。

## <a name="coledatetimespangettotalminutes"></a><a name="gettotalminutes"></a>COleDateTimeSpan:取得總分鐘數

檢索以分鐘表示的此日期/時間跨度值。

```
double GetTotalMinutes() const throw();
```

### <a name="return-value"></a>傳回值

此日期/時間跨度值以分鐘表示。 儘管此函數是原型返回 double,但它始終將返回整數值。

### <a name="remarks"></a>備註

此函數的返回值介於大約 - 5.26e9 和 5.26e9 之間。

對於查詢`COleDateTimeSpan`物件值的其他函數,請參閱以下成員函數:

- [取得天數](#getdays)

- [GetHours](#gethours)

- [取得分鐘](#getminutes)

- [取得秒數](#getseconds)

- [取得總天數](#gettotaldays)

- [取得總小時數](#gettotalhours)

- [取得總秒數](#gettotalseconds)

### <a name="example"></a>範例

請參考[GetTotalDays 的範例](#gettotaldays)。

## <a name="coledatetimespangettotalseconds"></a><a name="gettotalseconds"></a>COleDate時間跨度::取得總秒數

檢索以秒表示的此日期/時間跨度值。

```
double GetTotalSeconds() const throw();
```

### <a name="return-value"></a>傳回值

此日期/時間跨度值以秒為單位表示。 儘管此函數是原型返回 double,但它始終將返回整數值。

### <a name="remarks"></a>備註

此函數的返回值介於大約 - 3.16e11 到 3.16e11 之間。

對於查詢`COleDateTimeSpan`物件值的其他函數,請參閱以下成員函數:

- [取得天數](#getdays)

- [GetHours](#gethours)

- [取得分鐘](#getminutes)

- [取得秒數](#getseconds)

- [取得總天數](#gettotaldays)

- [取得總小時數](#gettotalhours)

- [取得總分鐘數](#gettotalminutes)

### <a name="example"></a>範例

請參考[GetTotalDays 的範例](#gettotaldays)。

## <a name="coledatetimespanm_span"></a><a name="m_span"></a>COleDate 時間跨度::m_span

此`COleDateTime`物件的基礎**雙精度值**。

```
double m_span;
```

### <a name="remarks"></a>備註

此值表示日期/時間跨度(以天表示)。

> [!CAUTION]
> 更改**雙**資料成員中的值將`COleDateTimeSpan`更改此 物件的值。 它不會更改此`COleDateTimeSpan`物件的狀態。

## <a name="coledatetimespanm_status"></a><a name="m_status"></a>COleDate時間跨度::m_status

此數據成員的類型是枚舉類型`DateTimeSpanStatus`,在類`COleDateTimeSpan`中 定義。

```
DateTimeSpanStatus m_status;
```

### <a name="remarks"></a>備註

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
   };
```

有關這些狀態值的簡要說明,請參閱以下清單:

- `COleDateTimeSpan::valid`指示此`COleDateTimeSpan`物件有效。

- `COleDateTimeSpan::invalid`指示此物件`COleDateTimeSpan`無效;如果表明此物件無效。也就是說,其值可能不正確。

- `COleDateTimeSpan::null`指示此`COleDateTimeSpan`物件為 null,即未為此物件提供任何值。 (這是"無值"的資料庫意義上的"空",而不是C++ NULL。

在以下情況下,`COleDateTimeSpan`物件的狀態無效:

- 如果此物件在算術賦值操作期間(即`+=``-=`或 ) 經歷了溢出或下溢。

- 如果為此物件分配了無效值。

- 如果此物件的狀態被顯式設定為無效使用[SetStatus](#setstatus)。

有關可能將狀態設定為無效的操作的詳細資訊,請參閱[COleDateTimeSpan::運算符 *,-](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-)和[COleDateTimeSpan::運算符 *,-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq)。

> [!CAUTION]
> 此數據成員適用於高級程式設計情況。 應使用內聯成員函數[「獲取狀態」](#getstatus)和[「設定狀態](#setstatus)」 。 有關`SetStatus`顯式設置此數據成員的進一步注意事項,請參閱。

有關`COleDateTimeSpan`值邊界的詳細資訊,請參閱文章[「日期和時間:自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)」。。

## <a name="coledatetimespanoperator-"></a><a name="operator_eq"></a>COleDate時間跨度::運算符 |

複製值`COleDateTimeSpan`。

```
COleDateTimeSpan& operator=(double dblSpanSrc) throw();
```

### <a name="remarks"></a>備註

此重載分配運算子將源日期/時間跨度值複製到此`COleDateTimeSpan`物件中。

## <a name="coledatetimespanoperator---"></a><a name="operator_add_-"></a>COleDateTimeSpan::運算符 +, -

添加、減去和更改值的`COleDateTimeSpan`符號。

```
COleDateTimeSpan operator+(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-() const throw();
```

### <a name="remarks"></a>備註

前兩個運算子允許您添加和減去日期/時間跨度值。 第三個允許您更改日期/時間跨度值的符號。

如果任一操作數為空,則結果`COleDateTimeSpan`值的狀態為 null。

如果任一操作數無效,另一個操作數不為空,則結果`COleDateTimeSpan`值的狀態無效。

有關有效、無效和 null 狀態值的詳細資訊,請參閱[m_status](#m_status)成員變數。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#23](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_10.cpp)]

## <a name="coledatetimespanoperator---"></a><a name="operator_add_eq_-_eq"></a>COleDate時間跨度::運算符 *,-*

從此值`COleDateTimeSpan`中添加`COleDateTimeSpan`和減去值。

```
COleDateTimeSpan& operator+=(const COleDateTimeSpan dateSpan) throw();
COleDateTimeSpan& operator-=(const COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>備註

這些運算元允許您在此`COleDateTimeSpan`物件中添加和減去日期/時間跨度值。 如果任一操作數為空,則結果`COleDateTimeSpan`值的狀態為 null。

如果任一操作數無效,另一個操作數不為空,則結果`COleDateTimeSpan`值的狀態無效。

有關有效、無效和 null 狀態值的詳細資訊,請參閱[m_status](#m_status)成員變數。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#24](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_11.cpp)]

## <a name="coledatetimespanoperator-double"></a><a name="operator_double"></a>COleDate 時間跨度::運算元雙精度

將此值`COleDateTimeSpan`轉換為**雙精度**值。

```
operator double() const throw();
```

### <a name="remarks"></a>備註

此運算符將此值`COleDateTimeSpan`的值作為浮點天數返回。

## <a name="coledatetimespansetdatetimespan"></a><a name="setdatetimespan"></a>COleDate時間跨度::設定時間跨度

設置此日期/時間跨度值的值。

```
void SetDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>參數

*l 天*, *nHours*, *nMins*, *nSecs*<br/>
指示要複製到此`COleDateTimeSpan`物件的日期跨度和時間跨度值。

### <a name="remarks"></a>備註

對於查詢`COleDateTimeSpan`物件值的函數,請參閱以下成員函數:

- [取得天數](#getdays)

- [GetHours](#gethours)

- [取得分鐘](#getminutes)

- [取得秒數](#getseconds)

- [取得總天數](#gettotaldays)

- [取得總小時數](#gettotalhours)

- [取得總分鐘數](#gettotalminutes)

- [取得總秒數](#gettotalseconds)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#21](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_12.cpp)]

## <a name="coledatetimespansetstatus"></a><a name="setstatus"></a>COleDate 時間跨度::設定狀態

設置此`COleDateTimeSpan`物件的狀態(有效性)。

```
void SetStatus(DateTimeSpanStatus status) throw();
```

### <a name="parameters"></a>參數

*狀態*<br/>
此`COleDateTimeSpan`物件的新狀態值。

### <a name="remarks"></a>備註

*狀態*參數值`DateTimeSpanStatus`由 枚舉類型定義,該類型在`COleDateTimeSpan`類中 定義。

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
   };
```

有關這些狀態值的簡要說明,請參閱以下清單:

- `COleDateTimeSpan::valid`指示此`COleDateTimeSpan`物件有效。

- `COleDateTimeSpan::invalid`指示此物件`COleDateTimeSpan`無效;如果表明此物件無效。也就是說,其值可能不正確。

- `COleDateTimeSpan::null`指示此`COleDateTimeSpan`物件為 null,即未為此物件提供任何值。 (這是"無值"的資料庫意義上的"空",而不是C++ NULL。

   > [!CAUTION]
   > 此功能適用於高級程式設計情況。 此函數不會更改此物件中的數據。 它最常用於將狀態設定為**null**或**無效**。 請注意,賦值運算符 ([運算符 =](#operator_eq)) 和[SetDateTimeSpan](#setdatetimespan)確實根據來源值設定物件的狀態。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#22](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_13.cpp)]

## <a name="see-also"></a>另請參閱

[COleDateTime 類別](../../atl-mfc-shared/reference/coledatetime-class.md)<br/>
[CTime 類別](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan 類別](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)
