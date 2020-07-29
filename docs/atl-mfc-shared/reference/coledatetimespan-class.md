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
ms.openlocfilehash: a3a59971ec57378aee2ec4f65f221b96c46300b5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219101"
---
# <a name="coledatetimespan-class"></a>COleDateTimeSpan 類別

表示相對時間（時間範圍）。

## <a name="syntax"></a>語法

```
class COleDateTimeSpan
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[COleDateTimeSpan::COleDateTimeSpan](#coledatetimespan)|建構 `COleDateTimeSpan` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[COleDateTimeSpan：： Format](#format)|產生物件的格式化字串表示 `COleDateTimeSpan` 。|
|[COleDateTimeSpan::GetDays](#getdays)|傳回此物件所代表之範圍的日部分 `COleDateTimeSpan` 。|
|[COleDateTimeSpan：： GetHours](#gethours)|傳回此物件所代表之範圍的小時部分 `COleDateTimeSpan` 。|
|[COleDateTimeSpan：： GetMinutes](#getminutes)|傳回此物件所代表之範圍的分鐘部分 `COleDateTimeSpan` 。|
|[COleDateTimeSpan：： GetSeconds](#getseconds)|傳回此物件所代表之範圍的第二個部分 `COleDateTimeSpan` 。|
|[COleDateTimeSpan：： GetStatus](#getstatus)|取得這個物件的狀態（有效性） `COleDateTimeSpan` 。|
|[COleDateTimeSpan::GetTotalDays](#gettotaldays)|傳回這個物件所代表的天數 `COleDateTimeSpan` 。|
|[COleDateTimeSpan::GetTotalHours](#gettotalhours)|傳回這個物件所代表的時數 `COleDateTimeSpan` 。|
|[COleDateTimeSpan::GetTotalMinutes](#gettotalminutes)|傳回這個物件所代表的分鐘數 `COleDateTimeSpan` 。|
|[COleDateTimeSpan::GetTotalSeconds](#gettotalseconds)|傳回這個物件所代表的秒數 `COleDateTimeSpan` 。|
|[COleDateTimeSpan::SetDateTimeSpan](#setdatetimespan)|設定這個物件的值 `COleDateTimeSpan` 。|
|[COleDateTimeSpan：： SetStatus](#setstatus)|設定這個物件的狀態（有效性） `COleDateTimeSpan` 。|

### <a name="public-operators"></a>公用運算子

|||
|-|-|
|[operator +、-](#operator_add_-)|新增、減去和變更值的正負號 `COleDateTimeSpan` 。|
|[operator + =、-=](#operator_add_eq_-_eq)|新增和減去 `COleDateTimeSpan` 此值的值 `COleDateTimeSpan` 。|
|[operator =](#operator_eq)|複製 `COleDateTimeSpan` 值。|
|[operator = =、<、<=](#coledatetimespan_relational_operators)|比較兩個 `COleDateTimeSpan` 值。|
|[運算子 double](#operator_double)|將這個 `COleDateTimeSpan` 值轉換為 **`double`** 。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[COleDateTimeSpan：： m_span](#m_span)|包含 **`double`** 這個物件的基礎 `COleDateTimeSpan` 。|
|[COleDateTimeSpan：： m_status](#m_status)|包含此物件的狀態 `COleDateTimeSpan` 。|

## <a name="remarks"></a>備註

`COleDateTimeSpan`沒有基類。

會 `COleDateTimeSpan` 保留時間（以天為單位）。

`COleDateTimeSpan`會搭配其隨附類別[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)使用。 `COleDateTime`封裝 `DATE` OLE automation 的資料類型。 `COleDateTime`表示絕對時間值。 所有 `COleDateTime` 計算都牽涉到 `COleDateTimeSpan` 值。 這些類別之間的關聯性類似于[CTime](../../atl-mfc-shared/reference/ctime-class.md)和[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)之間的關係。

如需和類別的詳細資訊 `COleDateTime` `COleDateTimeSpan` ，請參閱[日期和時間：自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)一文。

## <a name="requirements"></a>需求

**標頭：** Atlcomtime.h。h

## <a name="coledatetimespan-relational-operators"></a><a name="coledatetimespan_relational_operators"></a>COleDateTimeSpan 關係運算子

比較運算子。

```
bool operator==(const COleDateTimeSpan& dateSpan) const throw();
bool operator!=(const COleDateTimeSpan& dateSpan) const throw();
bool operator<(const COleDateTimeSpan& dateSpan) const throw();
bool operator>(const COleDateTimeSpan& dateSpan) const throw();
bool operator<=(const COleDateTimeSpan& dateSpan) const throw();
bool operator>=(const COleDateTimeSpan& dateSpan) const throw();
```

### <a name="parameters"></a>參數

*dateSpan*<br/>
要比較的 `COleDateTimeSpan`。

### <a name="return-value"></a>傳回值

這些運算子會比較兩個日期/時間範圍值，如果條件為 true，則傳回 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

> [!NOTE]
> 如果任一運算元無效，就會發生 ATLASSERT。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#25](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#26](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_2.cpp)]

## <a name="coledatetimespancoledatetimespan"></a><a name="coledatetimespan"></a>COleDateTimeSpan::COleDateTimeSpan

建構 `COleDateTimeSpan` 物件。

```
COleDateTimeSpan() throw();
COleDateTimeSpan(double dblSpanSrc) throw();
COleDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>參數

*dblSpanSrc*<br/>
要複製到新物件中的天數 `COleDateTimeSpan` 。

*lDays*、 *nHours*、 *nMins*、 *nSecs*<br/>
指出要複製到新物件中的日期和時間值 `COleDateTimeSpan` 。

### <a name="remarks"></a>備註

所有這些函式都會建立新 `COleDateTimeSpan` 的物件，並初始化為指定的值。 每一個這些函式的簡短說明如下：

- **COleDateTimeSpan （）** 將 `COleDateTimeSpan` 初始化為0的物件結構化。

- **COleDateTimeSpan （** `dblSpanSrc` **）** 會 `COleDateTimeSpan` 從浮點值來構造物件。

- **COleDateTimeSpan （** `lDays` **、** `nHours` **、** `nMins` **、** `nSecs` **）** 會將 `COleDateTimeSpan` 初始化為指定數值的物件進行結構化。

新物件的狀態 `COleDateTimeSpan` 會設定為 [有效]。

如需值界限的詳細資訊 `COleDateTimeSpan` ，請參閱[日期和時間：自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)一文。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#14](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_3.cpp)]

## <a name="coledatetimespanformat"></a><a name="format"></a>COleDateTimeSpan：： Format

產生物件的格式化字串表示 `COleDateTimeSpan` 。

```
CString Format(LPCTSTR pFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>參數

*pFormat*<br/>
格式化字串，類似于 `printf` 格式字串。 格式化程式碼（前面加上百分比（ `%` ）符號）會由對應的 `COleDateTimeSpan` 元件所取代。 格式字串中的其他字元會原封不動地複製到傳回的字串。 以下列出格式代碼的值與意義 `Format` ：

- **% H**當天的時數

- **% M**目前小時內的分鐘數

- **% S**目前分鐘的秒數

- **%%** 百分比符號

以上所列的四個格式代碼都是格式將接受的唯一代碼。

-

*nID*<br/>
格式控制字元串的資源識別碼。

### <a name="return-value"></a>傳回值

`CString`，其中包含格式化的日期/時間範圍值。

### <a name="remarks"></a>備註

呼叫這些函式以建立時間範圍值的格式化表示。 如果這個物件的狀態 `COleDateTimeSpan` 是 null，則傳回值是空字串。 如果狀態無效，則傳回字串會由字串資源識別碼S_INVALID_DATETIMESPAN 指定。

此函式的表單簡短描述如下：

**格式（** *pFormat* **）**<br/>
此表單會使用包含前面加上百分比符號（%）的格式字串來格式化值，如中所示 `printf` 。 格式化字串會當做參數傳遞給函式。

**格式（** *nID* **）**<br/>
此表單會使用包含前面加上百分比符號（%）的格式字串來格式化值，如中所示 `printf` 。 格式化字串是一種資源。 這個字串資源的識別碼會當做參數傳遞。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#15](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_4.cpp)]

## <a name="coledatetimespangetdays"></a><a name="getdays"></a>COleDateTimeSpan::GetDays

抓取此日期/時間範圍值的日期部分。

```
LONG GetDays() const throw();
```

### <a name="return-value"></a>傳回值

此日期/時間範圍值的日期部分。

### <a name="remarks"></a>備註

此函式的傳回值範圍大約是3615000和3615000。

如需查詢物件值的其他函數 `COleDateTimeSpan` ，請參閱下列成員函式：

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#16](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_5.cpp)]

## <a name="coledatetimespangethours"></a><a name="gethours"></a>COleDateTimeSpan：： GetHours

抓取此日期/時間範圍值的小時部分。

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>傳回值

此日期/時間範圍值的時數部分。

### <a name="remarks"></a>備註

此函式的傳回值範圍介於-23 到23之間。

如需查詢物件值的其他函數 `COleDateTimeSpan` ，請參閱下列成員函式：

- [GetDays](#getdays)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#17](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_6.cpp)]

## <a name="coledatetimespangetminutes"></a><a name="getminutes"></a>COleDateTimeSpan：： GetMinutes

抓取此日期/時間範圍值的分鐘部分。

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>傳回值

此日期/時間範圍值的分鐘部分。

### <a name="remarks"></a>備註

此函式的傳回值範圍介於-59 和59之間。

如需查詢物件值的其他函數 `COleDateTimeSpan` ，請參閱下列成員函式：

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#18](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_7.cpp)]

## <a name="coledatetimespangetseconds"></a><a name="getseconds"></a>COleDateTimeSpan：： GetSeconds

抓取此日期/時間範圍值的第二個部分。

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>傳回值

此日期/時間範圍值的秒數部分。

### <a name="remarks"></a>備註

此函式的傳回值範圍介於-59 和59之間。

如需查詢物件值的其他函數 `COleDateTimeSpan` ，請參閱下列成員函式：

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#19](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_8.cpp)]

## <a name="coledatetimespangetstatus"></a><a name="getstatus"></a>COleDateTimeSpan：： GetStatus

取得這個物件的狀態（有效性） `COleDateTimeSpan` 。

```
DateTimeSpanStatus GetStatus() const throw();
```

### <a name="return-value"></a>傳回值

此值的狀態 `COleDateTimeSpan` 。

### <a name="remarks"></a>備註

傳回值是由 `DateTimeSpanStatus` 列舉型別（在類別內定義）所定義 `COleDateTimeSpan` 。

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
};
```

如需這些狀態值的簡短描述，請參閱下列清單：

- `COleDateTimeSpan::valid`指出這個 `COleDateTimeSpan` 物件是有效的。

- `COleDateTimeSpan::invalid`指出這個 `COleDateTimeSpan` 物件無效; 也就是說，它的值可能不正確。

- `COleDateTimeSpan::null`指出這個 `COleDateTimeSpan` 物件是 null，也就是沒有為這個物件提供任何值。 （這是「沒有值」的資料庫意義中的「null」，而不是 c + + Null）。

`COleDateTimeSpan`在下列情況下，物件的狀態無效：

- 如果這個物件在算術指派作業期間發生溢位或下溢，即為 `+=` 或 `-=` 。

- 如果將不正確值指派給這個物件，則為。

- 如果這個物件的狀態已使用明確設定為無效 `SetStatus` 。

如需可能將狀態設定為無效之作業的詳細資訊，請參閱[COleDateTimeSpan：： operator +，-](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) and [COleDateTimeSpan：： operator + =，-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq)。

如需值界限的詳細資訊 `COleDateTimeSpan` ，請參閱[日期和時間：自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)一文。

## <a name="coledatetimespangettotaldays"></a><a name="gettotaldays"></a>COleDateTimeSpan::GetTotalDays

抓取此日期/時間範圍值（以天為單位）。

```
double GetTotalDays() const throw();
```

### <a name="return-value"></a>傳回值

此日期/時間範圍值（以天為單位）。 雖然此函式是傳回 double 的原型，但它一律會傳回整數值。

### <a name="remarks"></a>備註

此函式的傳回值範圍介於大約-3.65 e6 和 3.65 e6 之間。

如需查詢物件值的其他函數 `COleDateTimeSpan` ，請參閱下列成員函式：

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#20](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_9.cpp)]

## <a name="coledatetimespangettotalhours"></a><a name="gettotalhours"></a>COleDateTimeSpan::GetTotalHours

抓取此日期/時間範圍值（以小時表示）。

```
double GetTotalHours() const throw();
```

### <a name="return-value"></a>傳回值

此日期/時間範圍值以小時表示。 雖然此函式是傳回 double 的原型，但它一律會傳回整數值。

### <a name="remarks"></a>備註

此函式的傳回值範圍介於大約-8.77 e7 和 8.77 e7 之間。

如需查詢物件值的其他函數 `COleDateTimeSpan` ，請參閱下列成員函式：

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>範例

請參閱[GetTotalDays](#gettotaldays)的範例。

## <a name="coledatetimespangettotalminutes"></a><a name="gettotalminutes"></a>COleDateTimeSpan::GetTotalMinutes

抓取此日期/時間範圍值（以分鐘為單位）。

```
double GetTotalMinutes() const throw();
```

### <a name="return-value"></a>傳回值

此日期/時間範圍值（以分鐘為單位）。 雖然此函式是傳回 double 的原型，但它一律會傳回整數值。

### <a name="remarks"></a>備註

此函式的傳回值範圍介於大約-5.26 e 9 和 5.26 e 9 之間。

如需查詢物件值的其他函數 `COleDateTimeSpan` ，請參閱下列成員函式：

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>範例

請參閱[GetTotalDays](#gettotaldays)的範例。

## <a name="coledatetimespangettotalseconds"></a><a name="gettotalseconds"></a>COleDateTimeSpan::GetTotalSeconds

抓取此日期/時間範圍值（以秒為單位）。

```
double GetTotalSeconds() const throw();
```

### <a name="return-value"></a>傳回值

此日期/時間範圍值（以秒為單位）。 雖然此函式是傳回 double 的原型，但它一律會傳回整數值。

### <a name="remarks"></a>備註

此函式的傳回值範圍介於大約-3.16 e11 到 3.16 e11 之間。

如需查詢物件值的其他函數 `COleDateTimeSpan` ，請參閱下列成員函式：

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

### <a name="example"></a>範例

請參閱[GetTotalDays](#gettotaldays)的範例。

## <a name="coledatetimespanm_span"></a><a name="m_span"></a>COleDateTimeSpan：： m_span

**`double`** 這個物件的基礎值 `COleDateTime` 。

```
double m_span;
```

### <a name="remarks"></a>備註

此值表示日期/時間範圍（以天為單位）。

> [!CAUTION]
> 變更資料成員中的值 **`double`** 將會變更這個物件的值 `COleDateTimeSpan` 。 它不會變更此物件的狀態 `COleDateTimeSpan` 。

## <a name="coledatetimespanm_status"></a><a name="m_status"></a>COleDateTimeSpan：： m_status

這個資料成員的型別是列舉型別 `DateTimeSpanStatus` ，它是在類別內定義的 `COleDateTimeSpan` 。

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

如需這些狀態值的簡短描述，請參閱下列清單：

- `COleDateTimeSpan::valid`指出這個 `COleDateTimeSpan` 物件是有效的。

- `COleDateTimeSpan::invalid`指出這個 `COleDateTimeSpan` 物件無效; 也就是說，它的值可能不正確。

- `COleDateTimeSpan::null`指出這個 `COleDateTimeSpan` 物件是 null，也就是沒有為這個物件提供任何值。 （這是「沒有值」的資料庫意義中的「null」，而不是 c + + Null）。

`COleDateTimeSpan`在下列情況下，物件的狀態無效：

- 如果這個物件在算術指派作業期間發生溢位或下溢，即為 `+=` 或 `-=` 。

- 如果將不正確值指派給這個物件，則為。

- 如果這個物件的狀態是使用[SetStatus](#setstatus)明確設定為無效，則為。

如需可能將狀態設定為無效之作業的詳細資訊，請參閱[COleDateTimeSpan：： operator +，-](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) and [COleDateTimeSpan：： operator + =，-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq)。

> [!CAUTION]
> 此資料成員適用于先進的程式設計情況。 您應該使用內嵌成員函式[GetStatus](#getstatus)和[SetStatus](#setstatus)。 `SetStatus`如需有關明確設定此資料成員的進一步警告，請參閱。

如需值界限的詳細資訊 `COleDateTimeSpan` ，請參閱[日期和時間：自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)一文。

## <a name="coledatetimespanoperator-"></a><a name="operator_eq"></a>COleDateTimeSpan：： operator =

複製 `COleDateTimeSpan` 值。

```
COleDateTimeSpan& operator=(double dblSpanSrc) throw();
```

### <a name="remarks"></a>備註

這個多載指派運算子會將來源日期/時間範圍值複製到這個 `COleDateTimeSpan` 物件。

## <a name="coledatetimespanoperator---"></a><a name="operator_add_-"></a>COleDateTimeSpan：： operator +，-

新增、減去和變更值的正負號 `COleDateTimeSpan` 。

```
COleDateTimeSpan operator+(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-() const throw();
```

### <a name="remarks"></a>備註

前兩個運算子可讓您新增和減去日期/時間範圍值。 第三個可讓您變更日期/時間範圍值的正負號。

如果其中一個運算元為 null，則產生值的狀態 `COleDateTimeSpan` 會是 null。

如果其中一個運算元無效，而另一個不是 null，則產生值的狀態 `COleDateTimeSpan` 會無效。

如需有效、無效和 null 狀態值的詳細資訊，請參閱[m_status](#m_status)成員變數。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#23](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_10.cpp)]

## <a name="coledatetimespanoperator---"></a><a name="operator_add_eq_-_eq"></a>COleDateTimeSpan：： operator + =、-=

新增和減去 `COleDateTimeSpan` 此值的值 `COleDateTimeSpan` 。

```
COleDateTimeSpan& operator+=(const COleDateTimeSpan dateSpan) throw();
COleDateTimeSpan& operator-=(const COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>備註

這些運算子可讓您從這個物件加入和減去日期/時間範圍值 `COleDateTimeSpan` 。 如果其中一個運算元為 null，則產生值的狀態 `COleDateTimeSpan` 會是 null。

如果其中一個運算元無效，而另一個不是 null，則產生值的狀態 `COleDateTimeSpan` 會無效。

如需有效、無效和 null 狀態值的詳細資訊，請參閱[m_status](#m_status)成員變數。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#24](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_11.cpp)]

## <a name="coledatetimespanoperator-double"></a><a name="operator_double"></a>COleDateTimeSpan：： operator double

將這個 `COleDateTimeSpan` 值轉換為 **`double`** 。

```
operator double() const throw();
```

### <a name="remarks"></a>備註

這個運算子會傳回此值的值 `COleDateTimeSpan` 做為浮點數的浮點天數。

## <a name="coledatetimespansetdatetimespan"></a><a name="setdatetimespan"></a>COleDateTimeSpan::SetDateTimeSpan

設定此日期/時間範圍值的值。

```cpp
void SetDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>參數

*lDays*、 *nHours*、 *nMins*、 *nSecs*<br/>
指出要複製到這個物件的日期範圍和時間範圍值 `COleDateTimeSpan` 。

### <a name="remarks"></a>備註

如需查詢物件值的函式 `COleDateTimeSpan` ，請參閱下列成員函式：

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#21](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_12.cpp)]

## <a name="coledatetimespansetstatus"></a><a name="setstatus"></a>COleDateTimeSpan：： SetStatus

設定這個物件的狀態（有效性） `COleDateTimeSpan` 。

```cpp
void SetStatus(DateTimeSpanStatus status) throw();
```

### <a name="parameters"></a>參數

*status*<br/>
這個物件的新狀態值 `COleDateTimeSpan` 。

### <a name="remarks"></a>備註

*狀態*參數值是由列舉型別所定義 `DateTimeSpanStatus` ，此類型定義于 `COleDateTimeSpan` 類別內。

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
   };
```

如需這些狀態值的簡短描述，請參閱下列清單：

- `COleDateTimeSpan::valid`指出這個 `COleDateTimeSpan` 物件是有效的。

- `COleDateTimeSpan::invalid`指出這個 `COleDateTimeSpan` 物件無效; 也就是說，它的值可能不正確。

- `COleDateTimeSpan::null`指出這個 `COleDateTimeSpan` 物件是 null，也就是沒有為這個物件提供任何值。 （這是「沒有值」的資料庫意義中的「null」，而不是 c + + Null）。

   > [!CAUTION]
   > 這個函數適用于先進的程式設計情況。 此函式不會改變這個物件中的資料。 最常用來將狀態設定為**null**或**無效**。 請注意，指派運算子（[operator =](#operator_eq)）和[SetDateTimeSpan](#setdatetimespan)會根據來源值來設定物件的狀態。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#22](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_13.cpp)]

## <a name="see-also"></a>另請參閱

[COleDateTime 類別](../../atl-mfc-shared/reference/coledatetime-class.md)<br/>
[CTime 類別](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan 類別](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)
