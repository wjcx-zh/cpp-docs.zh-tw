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
ms.openlocfilehash: 746cfdce3265dff7e5b20a5135aa026aca9facdf
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832096"
---
# <a name="coledatetimespan-class"></a>COleDateTimeSpan 類別

代表時間範圍的相對時間。

## <a name="syntax"></a>語法

```
class COleDateTimeSpan
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleDateTimeSpan：： COleDateTimeSpan](#coledatetimespan)|建構 `COleDateTimeSpan` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleDateTimeSpan：： Format](#format)|產生物件的格式化字串表示 `COleDateTimeSpan` 。|
|[COleDateTimeSpan：： GetDays](#getdays)|傳回這個物件所代表之範圍的日部分 `COleDateTimeSpan` 。|
|[COleDateTimeSpan：： GetHours](#gethours)|傳回這個物件所代表之範圍的小時部分 `COleDateTimeSpan` 。|
|[COleDateTimeSpan：： GetMinutes](#getminutes)|傳回這個物件所代表之範圍的分鐘部分 `COleDateTimeSpan` 。|
|[COleDateTimeSpan：： GetSeconds](#getseconds)|傳回這個物件所代表之範圍的第二個部分 `COleDateTimeSpan` 。|
|[COleDateTimeSpan：： GetStatus](#getstatus)|取得此物件的狀態 (有效) `COleDateTimeSpan` 。|
|[COleDateTimeSpan：： GetTotalDays](#gettotaldays)|傳回這個物件所代表的天數 `COleDateTimeSpan` 。|
|[COleDateTimeSpan：： GetTotalHours](#gettotalhours)|傳回這個物件所代表的時數 `COleDateTimeSpan` 。|
|[COleDateTimeSpan：： GetTotalMinutes](#gettotalminutes)|傳回這個物件所代表的分鐘數 `COleDateTimeSpan` 。|
|[COleDateTimeSpan：： GetTotalSeconds](#gettotalseconds)|傳回這個物件所代表的秒數 `COleDateTimeSpan` 。|
|[COleDateTimeSpan：： SetDateTimeSpan](#setdatetimespan)|設定這個物件的值 `COleDateTimeSpan` 。|
|[COleDateTimeSpan：： SetStatus](#setstatus)|設定此物件的狀態 (有效) `COleDateTimeSpan` 。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|-|-|
|[運算子 +、-](#operator_add_-)|新增、減去及變更值的正負號 `COleDateTimeSpan` 。|
|[operator + =、-=](#operator_add_eq_-_eq)|`COleDateTimeSpan`從這個值加入值並加以減去 `COleDateTimeSpan` 。|
|[運算子 =](#operator_eq)|複製 `COleDateTimeSpan` 值。|
|[operator = =、<、<=](#coledatetimespan_relational_operators)|比較兩個 `COleDateTimeSpan` 值。|
|[運算子 double](#operator_double)|將此 `COleDateTimeSpan` 值轉換為 **`double`** 。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COleDateTimeSpan：： m_span](#m_span)|包含 **`double`** 這個物件的基礎 `COleDateTimeSpan` 。|
|[COleDateTimeSpan：： m_status](#m_status)|包含這個物件的狀態 `COleDateTimeSpan` 。|

## <a name="remarks"></a>備註

`COleDateTimeSpan` 沒有基類。

`COleDateTimeSpan`保留時間（以天為單位）。

`COleDateTimeSpan` 搭配其附屬類別 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)使用。 `COleDateTime` 封裝 `DATE` OLE automation 的資料類型。 `COleDateTime` 表示絕對時間值。 所有 `COleDateTime` 計算都包含 `COleDateTimeSpan` 值。 這些類別之間的關聯性，類似于 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 與 [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)之間的關聯性。

如需和類別的詳細資訊 `COleDateTime` `COleDateTimeSpan` ，請參閱文章 [日期和時間：自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

## <a name="requirements"></a>規格需求

**標頭：** Atlcomtime.h。h

## <a name="coledatetimespan-relational-operators"></a><a name="coledatetimespan_relational_operators"></a> COleDateTimeSpan 關係運算子

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

這些運算子會比較兩個日期/時間範圍值，如果條件為 true，則傳回 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

> [!NOTE]
> 如果任一個運算元無效，就會發生 ATLASSERT。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#25](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#26](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_2.cpp)]

## <a name="coledatetimespancoledatetimespan"></a><a name="coledatetimespan"></a> COleDateTimeSpan：： COleDateTimeSpan

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

所有這些函式都會建立 `COleDateTimeSpan` 初始化為指定值的新物件。 以下是每個這些函式的簡短描述：

- **COleDateTimeSpan ( ) ** 結構化的 `COleDateTimeSpan` 物件會初始化為0。

- **COleDateTimeSpan (** `dblSpanSrc`**) **`COleDateTimeSpan`從浮點值結構物件。

- **COleDateTimeSpan (** `lDays`**,** `nHours`**,** `nMins`**,** `nSecs`**) **將 `COleDateTimeSpan` 初始化為指定之數值的物件進行結構化。

新物件的狀態 `COleDateTimeSpan` 會設定為 [有效]。

如需有關值範圍的詳細資訊 `COleDateTimeSpan` ，請參閱文章 [日期和時間：自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#14](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_3.cpp)]

## <a name="coledatetimespanformat"></a><a name="format"></a> COleDateTimeSpan：： Format

產生物件的格式化字串表示 `COleDateTimeSpan` 。

```
CString Format(LPCTSTR pFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>參數

*Pformatetc 架構*<br/>
格式化字串，類似于 `printf` 格式化字串。 格式化程式碼（前面加上% (`%`) 號）會取代為對應的 `COleDateTimeSpan` 元件。 格式化字串中的其他字元會原封不動地複製到傳回的字串。 的格式化程式碼的值和意義如下所示 `Format` ：

- **% H** 當天的小時數

- **% M** 目前小時的分鐘數

- **% S** 目前分鐘的秒數

- **%%** 百分比符號

上面所列的四個格式代碼都是格式將接受的唯一代碼。

-

*nID*<br/>
格式控制字元串的資源識別碼。

### <a name="return-value"></a>傳回值

`CString`，其中包含格式化日期/時間範圍值。

### <a name="remarks"></a>備註

呼叫這些函式來建立時間範圍值的格式化表示。 如果此物件的狀態 `COleDateTimeSpan` 為 null，則傳回值為空字串。 如果狀態無效，則傳回字串是由字串資源識別碼S_INVALID_DATETIMESPAN 指定。

這項功能的表單簡短描述如下：

** (Pformatetc 架構格式的格式** *pFormat* **) **<br/>
此表單會使用格式字串來格式化值，此格式字串前面會加上百分比符號 (% ) ，如下所示 `printf` 。 格式化字串會以參數的形式傳遞至函式。

**格式 (** *nID* **) **<br/>
此表單會使用格式字串來格式化值，此格式字串前面會加上百分比符號 (% ) ，如下所示 `printf` 。 格式化字串為資源。 此字串資源的識別碼會以參數的形式傳遞。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#15](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_4.cpp)]

## <a name="coledatetimespangetdays"></a><a name="getdays"></a> COleDateTimeSpan：： GetDays

抓取此日期/時間範圍值的日部分。

```
LONG GetDays() const throw();
```

### <a name="return-value"></a>傳回值

此日期/時間範圍值的日部分。

### <a name="remarks"></a>備註

此函式的傳回值範圍介於大約-3615000 和3615000之間。

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

## <a name="coledatetimespangethours"></a><a name="gethours"></a> COleDateTimeSpan：： GetHours

抓取此日期/時間範圍值的小時部分。

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>傳回值

此日期/時間範圍值的小時部分。

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

## <a name="coledatetimespangetminutes"></a><a name="getminutes"></a> COleDateTimeSpan：： GetMinutes

抓取此日期/時間範圍值的分鐘部分。

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>傳回值

此日期/時間範圍值的分鐘部分。

### <a name="remarks"></a>備註

從-59 和59之間的這個函式範圍傳回值。

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

## <a name="coledatetimespangetseconds"></a><a name="getseconds"></a> COleDateTimeSpan：： GetSeconds

抓取此日期/時間範圍值的第二個部分。

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>傳回值

此日期/時間範圍值的秒數部分。

### <a name="remarks"></a>備註

從-59 和59之間的這個函式範圍傳回值。

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

## <a name="coledatetimespangetstatus"></a><a name="getstatus"></a> COleDateTimeSpan：： GetStatus

取得此物件的狀態 (有效) `COleDateTimeSpan` 。

```
DateTimeSpanStatus GetStatus() const throw();
```

### <a name="return-value"></a>傳回值

此值的狀態 `COleDateTimeSpan` 。

### <a name="remarks"></a>備註

傳回值是由 `DateTimeSpanStatus` 類別中定義的列舉類型所定義 `COleDateTimeSpan` 。

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
};
```

如需這些狀態值的簡短描述，請參閱下列清單：

- `COleDateTimeSpan::valid` 指出此 `COleDateTimeSpan` 物件有效。

- `COleDateTimeSpan::invalid` 指出此 `COleDateTimeSpan` 物件無效; 也就是說，其值可能不正確。

- `COleDateTimeSpan::null` 表示此 `COleDateTimeSpan` 物件為 null，也就是未提供這個物件的值。  (在「沒有值」的資料庫意義上為 "null"，而不是 c + + Null。 ) 

`COleDateTimeSpan`在下列情況下，物件的狀態無效：

- 如果這個物件在算術指派作業期間發生溢位或下溢，即為 `+=` 或 `-=` 。

- 如果將不正確值指派給這個物件。

- 如果這個物件的狀態已明確設為無效，則使用 `SetStatus` 。

如需可能將狀態設為無效之作業的詳細資訊，請參閱 [COleDateTimeSpan：： operator +、-](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) 和 [COleDateTimeSpan：： operator + =、-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq)。

如需有關值範圍的詳細資訊 `COleDateTimeSpan` ，請參閱文章 [日期和時間：自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

## <a name="coledatetimespangettotaldays"></a><a name="gettotaldays"></a> COleDateTimeSpan：： GetTotalDays

抓取此日期/時間範圍值（以天為單位）。

```
double GetTotalDays() const throw();
```

### <a name="return-value"></a>傳回值

此日期/時間範圍值（以天為單位）。 雖然此函式是原型來傳回雙精度浮點數，但它一律會傳回整數值。

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

## <a name="coledatetimespangettotalhours"></a><a name="gettotalhours"></a> COleDateTimeSpan：： GetTotalHours

抓取此日期/時間範圍值（以小時為單位）。

```
double GetTotalHours() const throw();
```

### <a name="return-value"></a>傳回值

此日期/時間範圍值（以小時表示）。 雖然此函式是原型來傳回雙精度浮點數，但它一律會傳回整數值。

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

請參閱 [GetTotalDays](#gettotaldays)的範例。

## <a name="coledatetimespangettotalminutes"></a><a name="gettotalminutes"></a> COleDateTimeSpan：： GetTotalMinutes

抓取此日期/時間範圍值（以分鐘為單位）。

```
double GetTotalMinutes() const throw();
```

### <a name="return-value"></a>傳回值

此日期/時間範圍值（以分鐘為單位）。 雖然此函式是原型來傳回雙精度浮點數，但它一律會傳回整數值。

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

請參閱 [GetTotalDays](#gettotaldays)的範例。

## <a name="coledatetimespangettotalseconds"></a><a name="gettotalseconds"></a> COleDateTimeSpan：： GetTotalSeconds

抓取此日期/時間範圍值（以秒為單位）。

```
double GetTotalSeconds() const throw();
```

### <a name="return-value"></a>傳回值

此日期/時間範圍值（以秒為單位）。 雖然此函式是原型來傳回雙精度浮點數，但它一律會傳回整數值。

### <a name="remarks"></a>備註

從此函式的傳回值，範圍介於大約-3.16 e11 到 3.16 e11 之間。

如需查詢物件值的其他函數 `COleDateTimeSpan` ，請參閱下列成員函式：

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

### <a name="example"></a>範例

請參閱 [GetTotalDays](#gettotaldays)的範例。

## <a name="coledatetimespanm_span"></a><a name="m_span"></a> COleDateTimeSpan：： m_span

**`double`** 這個物件的基礎值 `COleDateTime` 。

```
double m_span;
```

### <a name="remarks"></a>備註

此值表示日期/時間範圍（以天為單位）。

> [!CAUTION]
> 變更資料成員中的值 **`double`** 將會變更這個物件的值 `COleDateTimeSpan` 。 它不會變更此物件的狀態 `COleDateTimeSpan` 。

## <a name="coledatetimespanm_status"></a><a name="m_status"></a> COleDateTimeSpan：： m_status

此資料成員的類型是列舉類型 `DateTimeSpanStatus` ，定義于 `COleDateTimeSpan` 類別中。

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

- `COleDateTimeSpan::valid` 指出此 `COleDateTimeSpan` 物件有效。

- `COleDateTimeSpan::invalid` 指出此 `COleDateTimeSpan` 物件無效; 也就是說，其值可能不正確。

- `COleDateTimeSpan::null` 表示此 `COleDateTimeSpan` 物件為 null，也就是未提供這個物件的值。  (在「沒有值」的資料庫意義上為 "null"，而不是 c + + Null。 ) 

`COleDateTimeSpan`在下列情況下，物件的狀態無效：

- 如果這個物件在算術指派作業期間發生溢位或下溢，即為 `+=` 或 `-=` 。

- 如果將不正確值指派給這個物件。

- 如果這個物件的狀態是使用 [SetStatus](#setstatus)明確設定為無效，則為。

如需可能將狀態設為無效之作業的詳細資訊，請參閱 [COleDateTimeSpan：： operator +、-](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) 和 [COleDateTimeSpan：： operator + =、-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq)。

> [!CAUTION]
> 此資料成員適用于先進的程式設計情況。 您應該使用內嵌成員函式 [GetStatus](#getstatus) 和 [SetStatus](#setstatus)。 `SetStatus`如需有關明確設定此資料成員的進一步注意事項，請參閱。

如需有關值範圍的詳細資訊 `COleDateTimeSpan` ，請參閱文章 [日期和時間：自動化支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

## <a name="coledatetimespanoperator-"></a><a name="operator_eq"></a> COleDateTimeSpan：： operator =

複製 `COleDateTimeSpan` 值。

```
COleDateTimeSpan& operator=(double dblSpanSrc) throw();
```

### <a name="remarks"></a>備註

這個多載指派運算子會將來源日期/時間範圍值複製到這個 `COleDateTimeSpan` 物件中。

## <a name="coledatetimespanoperator---"></a><a name="operator_add_-"></a> COleDateTimeSpan：： operator +、-

新增、減去及變更值的正負號 `COleDateTimeSpan` 。

```
COleDateTimeSpan operator+(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-() const throw();
```

### <a name="remarks"></a>備註

前兩個運算子可讓您新增及減去日期/時間範圍值。 第三個可讓您變更日期/時間範圍值的正負號。

如果任一個運算元為 null，則結果值的狀態 `COleDateTimeSpan` 會是 null。

如果任一個運算元無效，而另一個不是 null，則結果值的狀態將 `COleDateTimeSpan` 會無效。

如需有效、無效和 null 狀態值的詳細資訊，請參閱 [m_status](#m_status) 成員變數。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#23](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_10.cpp)]

## <a name="coledatetimespanoperator---"></a><a name="operator_add_eq_-_eq"></a> COleDateTimeSpan：： operator + =，-=

`COleDateTimeSpan`從這個值加入值並加以減去 `COleDateTimeSpan` 。

```
COleDateTimeSpan& operator+=(const COleDateTimeSpan dateSpan) throw();
COleDateTimeSpan& operator-=(const COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>備註

這些運算子可讓您在此物件中新增及減去日期/時間範圍值 `COleDateTimeSpan` 。 如果任一個運算元為 null，則結果值的狀態 `COleDateTimeSpan` 會是 null。

如果任一個運算元無效，而另一個不是 null，則結果值的狀態將 `COleDateTimeSpan` 會無效。

如需有效、無效和 null 狀態值的詳細資訊，請參閱 [m_status](#m_status) 成員變數。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#24](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_11.cpp)]

## <a name="coledatetimespanoperator-double"></a><a name="operator_double"></a> COleDateTimeSpan：： operator double

將此 `COleDateTimeSpan` 值轉換為 **`double`** 。

```
operator double() const throw();
```

### <a name="remarks"></a>備註

這個運算子會將這個值的值傳回 `COleDateTimeSpan` 為浮點數的天數。

## <a name="coledatetimespansetdatetimespan"></a><a name="setdatetimespan"></a> COleDateTimeSpan：： SetDateTimeSpan

設定此日期/時間範圍值的值。

```cpp
void SetDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>參數

*lDays*、 *nHours*、 *nMins*、 *nSecs*<br/>
指出要複製到此物件中的日期範圍和時間範圍值 `COleDateTimeSpan` 。

### <a name="remarks"></a>備註

針對查詢物件值的函數 `COleDateTimeSpan` ，請參閱下列成員函式：

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

## <a name="coledatetimespansetstatus"></a><a name="setstatus"></a> COleDateTimeSpan：： SetStatus

設定此物件的狀態 (有效) `COleDateTimeSpan` 。

```cpp
void SetStatus(DateTimeSpanStatus status) throw();
```

### <a name="parameters"></a>參數

*status*<br/>
這個物件的新狀態值 `COleDateTimeSpan` 。

### <a name="remarks"></a>備註

*Status*參數值是由 `DateTimeSpanStatus` 類別中定義的列舉類型所定義 `COleDateTimeSpan` 。

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
   };
```

如需這些狀態值的簡短描述，請參閱下列清單：

- `COleDateTimeSpan::valid` 指出此 `COleDateTimeSpan` 物件有效。

- `COleDateTimeSpan::invalid` 指出此 `COleDateTimeSpan` 物件無效; 也就是說，其值可能不正確。

- `COleDateTimeSpan::null` 表示此 `COleDateTimeSpan` 物件為 null，也就是未提供這個物件的值。  (在「沒有值」的資料庫意義上為 "null"，而不是 c + + Null。 ) 

   > [!CAUTION]
   > 這項功能適用于先進的程式設計情況。 此函數不會改變此物件中的資料。 它最常用來將狀態設為 **null** 或 **無效**。 請注意，指派運算子 ([operator =](#operator_eq)) 和 [SetDateTimeSpan](#setdatetimespan) 會根據) 的來源 (值設定物件的狀態。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#22](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_13.cpp)]

## <a name="see-also"></a>另請參閱

[COleDateTime 類別](../../atl-mfc-shared/reference/coledatetime-class.md)<br/>
[CTime 類別](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan 類別](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)
