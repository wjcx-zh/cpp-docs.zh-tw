---
title: COleDateTimeSpan 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- timespan
- time span
- shared classes, COleDateTimeSpan
- Date data type, MFC encapsulation of
- COleDateTimeSpan class
ms.assetid: 7441526d-a30a-4019-8fb3-3fee6f897cbe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: be0e05d61d4949deaee683c5b8f43d18e0501d23
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808975"
---
# <a name="coledatetimespan-class"></a>COleDateTimeSpan 類別

代表相對的時間，時間範圍。

## <a name="syntax"></a>語法

```
class COleDateTimeSpan
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleDateTimeSpan::COleDateTimeSpan](#coledatetimespan)|建構 `COleDateTimeSpan` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleDateTimeSpan::Format](#format)|產生的格式化的字串表示`COleDateTimeSpan`物件。|
|[COleDateTimeSpan::GetDays](#getdays)|這會傳回範圍的日期部份`COleDateTimeSpan`物件表示。|
|[COleDateTimeSpan::GetHours](#gethours)|這會傳回範圍的小時部分`COleDateTimeSpan`物件表示。|
|[COleDateTimeSpan::GetMinutes](#getminutes)|這會傳回範圍的分鐘部分`COleDateTimeSpan`物件表示。|
|[COleDateTimeSpan::GetSeconds](#getseconds)|這會傳回範圍的第二個部分`COleDateTimeSpan`物件表示。|
|[COleDateTimeSpan::GetStatus](#getstatus)|取得這個狀態 （有效性）`COleDateTimeSpan`物件。|
|[COleDateTimeSpan::GetTotalDays](#gettotaldays)|這會傳回天數`COleDateTimeSpan`物件表示。|
|[COleDateTimeSpan::GetTotalHours](#gettotalhours)|傳回此數`COleDateTimeSpan`物件表示。|
|[COleDateTimeSpan::GetTotalMinutes](#gettotalminutes)|這會傳回的分鐘數`COleDateTimeSpan`物件表示。|
|[COleDateTimeSpan::GetTotalSeconds](#gettotalseconds)|這會傳回的秒數`COleDateTimeSpan`物件表示。|
|[COleDateTimeSpan::SetDateTimeSpan](#setdatetimespan)|設定值，這個`COleDateTimeSpan`物件。|
|[COleDateTimeSpan::SetStatus](#setstatus)|設定此狀態 （有效性）`COleDateTimeSpan`物件。|

### <a name="public-operators"></a>公用運算子

|||
|-|-|
|[運算子 +、-](#operator_add_-)|新增、 subtract、 及變更符號`COleDateTimeSpan`值。|
|[運算子 + =、 =](#operator_add_eq_-_eq)|加法和減法`COleDateTimeSpan`值從這個`COleDateTimeSpan`值。|
|[operator =](#operator_eq)|複製`COleDateTimeSpan`值。|
|[運算子 = =、 <、 < =](#coledatetimespan_relational_operators)|比較兩個`COleDateTimeSpan`值。|
|[運算子 double](#operator_double)|這會將轉換`COleDateTimeSpan`值加入**double**。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[COleDateTimeSpan::m_span](#m_span)|包含的基礎**雙**這個`COleDateTimeSpan`物件。|
|[COleDateTimeSpan::m_status](#m_status)|包含這個狀態`COleDateTimeSpan`物件。|

## <a name="remarks"></a>備註

`COleDateTimeSpan` 沒有基底類別。

A`COleDateTimeSpan`持續時間，以天為單位。

`COleDateTimeSpan` 搭配其附屬類別[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)。 `COleDateTime` 封裝`DATE`OLE automation 資料類型。 `COleDateTime` 表示絕對時間值。 所有`COleDateTime`計算涉及`COleDateTimeSpan`值。 這些類別之間的關聯性相當於之間[CTime](../../atl-mfc-shared/reference/ctime-class.md)並[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)。

如需詳細資訊`COleDateTime`並`COleDateTimeSpan`類別，請參閱本文[日期和時間： Automation 支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

## <a name="requirements"></a>需求

**標頭：** ATLComTime.h

##  <a name="coledatetimespan_relational_operators"></a>  COleDateTimeSpan 關係運算子

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

這些運算子比較兩個日期/時間範圍值並傳回 TRUE 的條件為 true; 如果否則為 FALSE。

### <a name="remarks"></a>備註

> [!NOTE]
>  如果任一個運算元無效，會發生 ATLASSERT。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#25](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#26](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_2.cpp)]

##  <a name="coledatetimespan"></a>  COleDateTimeSpan::COleDateTimeSpan

建構 `COleDateTimeSpan` 物件。

```
COleDateTimeSpan() throw();
COleDateTimeSpan(double dblSpanSrc) throw();
COleDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>參數

*dblSpanSrc*<br/>
若要複製到新的天數`COleDateTimeSpan`物件。

*lDays*， *nHours*， *nMins*， *nSecs*  
表示要複製到新的日期和時間值`COleDateTimeSpan`物件。

### <a name="remarks"></a>備註

這些建構函式的所有新建`COleDateTimeSpan`物件初始化為指定的值。 每個這些建構函式的簡短描述如下：

- **COleDateTimeSpan （)** 建構`COleDateTimeSpan`物件初始化為 0。

- **COleDateTimeSpan (** `dblSpanSrc` **)** 建構`COleDateTimeSpan`從浮點值的物件。

- **COleDateTimeSpan (** `lDays` **，** `nHours` **，** `nMins` **，** `nSecs` **)** 建構`COleDateTimeSpan`物件初始化為指定的數值。

新的狀態`COleDateTimeSpan`物件設定為有效。

如需有關的界限`COleDateTimeSpan`值，請參閱文章[日期和時間： Automation 支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#14](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_3.cpp)]

##  <a name="format"></a>  COleDateTimeSpan::Format

產生的格式化的字串表示`COleDateTimeSpan`物件。

```
CString Format(LPCTSTR pFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>參數

*pFormat*<br/>
格式化字串類似於`printf`格式化字串。 格式化程式碼，加上百分比 (`%`) 登入，會取代對應`COleDateTimeSpan`元件。 格式化字串中的其他字元會複製到傳回的字串不變。 值和格式化的程式碼的意義`Format`如下所示：

- **%H**當天的時數

- **%M**目前小時的分鐘數

- **%S**中目前的分鐘的秒數

- **%%** 百分比符號

以上所列的四個格式化程式碼會接受格式的唯一代碼。

-

*nID*<br/>
格式控制字串資源識別碼。

### <a name="return-value"></a>傳回值

A `CString` ，包含已格式化的日期/時間範圍值。

### <a name="remarks"></a>備註

呼叫這些函式來建立格式化的表示法的時間範圍值。 如果這個狀態`COleDateTimeSpan`物件為 null，則傳回的值為空字串。 如果狀態不正確，字串資源 IDS_INVALID_DATETIMESPAN 被指定傳回的字串。

此函式之表單的簡短描述如下：

**格式 (** *pFormat* **)**  
此表單會使用格式字串，其中包含特殊格式化的程式碼會加上百分比符號 （%），將值格式化中`printf`。 格式化的字串做為參數傳遞至函式。

**格式 (** *nID* **)**  
此表單會使用格式字串，其中包含特殊格式化的程式碼會加上百分比符號 （%），將值格式化中`printf`。 格式化的字串是資源。 此字串資源的識別碼會當做參數傳遞。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#15](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_4.cpp)]

##  <a name="getdays"></a>  COleDateTimeSpan::GetDays

擷取此日期/時間範圍值的日期部分。

```
LONG GetDays() const throw();
```

### <a name="return-value"></a>傳回值

此日期/時間範圍值的日期部份。

### <a name="remarks"></a>備註

傳回值在這個函式範圍中之間大約-3,615,000 和 3,615,000。

其他查詢的值的函式`COleDateTimeSpan`物件，請參閱下列成員函式：

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#16](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_5.cpp)]

##  <a name="gethours"></a>  COleDateTimeSpan::GetHours

擷取此日期/時間範圍值的小時部分。

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>傳回值

此日期/時間範圍值的小時部分。

### <a name="remarks"></a>備註

在這個函式範圍中-23 到 23 之間傳回的值。

其他查詢的值的函式`COleDateTimeSpan`物件，請參閱下列成員函式：

- [GetDays](#getdays)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#17](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_6.cpp)]

##  <a name="getminutes"></a>  COleDateTimeSpan::GetMinutes

擷取此日期/時間範圍值的分鐘部分。

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>傳回值

此日期/時間範圍值的分鐘部分。

### <a name="remarks"></a>備註

從這個函式的範圍介於-59 到 59 之間的傳回值。

其他查詢的值的函式`COleDateTimeSpan`物件，請參閱下列成員函式：

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#18](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_7.cpp)]

##  <a name="getseconds"></a>  COleDateTimeSpan::GetSeconds

擷取此日期/時間範圍值的第二個部分。

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>傳回值

此日期/時間範圍值的秒數部分。

### <a name="remarks"></a>備註

從這個函式的範圍介於-59 到 59 之間的傳回值。

其他查詢的值的函式`COleDateTimeSpan`物件，請參閱下列成員函式：

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#19](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_8.cpp)]

##  <a name="getstatus"></a>  COleDateTimeSpan::GetStatus

取得這個狀態 （有效性）`COleDateTimeSpan`物件。

```
DateTimeSpanStatus GetStatus() const throw();
```

### <a name="return-value"></a>傳回值

這個狀態`COleDateTimeSpan`值。

### <a name="remarks"></a>備註

傳回值由定義`DateTimeSpanStatus`列舉型別，其定義內`COleDateTimeSpan`類別。

```
enum DateTimeSpanStatus{  
   valid = 0,  
   invalid = 1,  
   null = 2,  
};  
```

如這些狀態值的簡短描述，請參閱下列清單：

- `COleDateTimeSpan::valid` 指出這個`COleDateTimeSpan`物件是否有效。

- `COleDateTimeSpan::invalid` 指出這個`COleDateTimeSpan`物件無效，也就是它的值可能不正確。

- `COleDateTimeSpan::null` 指出這個`COleDateTimeSpan`物件為 null，也就是這個物件尚未提供任何值。 （這是"null"中資料庫的 「 沒有值，"而不是 c + + NULL）。

狀態`COleDateTimeSpan`在下列情況中的物件無效：

- 如果這個物件發生溢位或反向溢位算術的指派作業期間，亦即`+=`或`-=`。

- 如果無效的值已指派給這個物件。

- 如果此物件的狀態已明確設定為無效的使用`SetStatus`。

如需可能會將狀態設為無效的作業的詳細資訊，請參閱[COleDateTimeSpan::operator +、-](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-)並[COleDateTimeSpan::operator + =、-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq)。

如需有關的界限`COleDateTimeSpan`值，請參閱文章[日期和時間： Automation 支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

##  <a name="gettotaldays"></a>  COleDateTimeSpan::GetTotalDays

擷取以天為單位來表示此日期/時間範圍值。

```
double GetTotalDays() const throw();
```

### <a name="return-value"></a>傳回值

以天為單位來表示此日期/時間範圍值。 雖然此函式是原型才能傳回雙精度浮點數，但它一定會傳回整數值。

### <a name="remarks"></a>備註

此函式和之間的範圍大約-3.65e6 3.65e6 從傳回的值。

其他查詢的值的函式`COleDateTimeSpan`物件，請參閱下列成員函式：

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#20](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_9.cpp)]

##  <a name="gettotalhours"></a>  COleDateTimeSpan::GetTotalHours

擷取以小時為單位來表示此日期/時間範圍值。

```
double GetTotalHours() const throw();
```

### <a name="return-value"></a>傳回值

以小時為單位來表示此日期/時間範圍值。 雖然此函式是原型才能傳回雙精度浮點數，但它一定會傳回整數值。

### <a name="remarks"></a>備註

此函式和之間的範圍大約-8.77e7 8.77e7 從傳回的值。

其他查詢的值的函式`COleDateTimeSpan`物件，請參閱下列成員函式：

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>範例

範例，請參閱[GetTotalDays](#gettotaldays)。

##  <a name="gettotalminutes"></a>  COleDateTimeSpan::GetTotalMinutes

擷取以分鐘為單位來表示此日期/時間範圍值。

```
double GetTotalMinutes() const throw();
```

### <a name="return-value"></a>傳回值

以分鐘為單位來表示此日期/時間範圍值。 雖然此函式是原型才能傳回雙精度浮點數，但它一定會傳回整數值。

### <a name="remarks"></a>備註

此函式和之間的範圍大約-5.26e9 5.26e9 從傳回的值。

其他查詢的值的函式`COleDateTimeSpan`物件，請參閱下列成員函式：

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>範例

範例，請參閱[GetTotalDays](#gettotaldays)。

##  <a name="gettotalseconds"></a>  COleDateTimeSpan::GetTotalSeconds

擷取此日期/時間範圍值，表示以秒為單位。

```
double GetTotalSeconds() const throw();
```

### <a name="return-value"></a>傳回值

以秒為單位來表示此日期/時間範圍值。 雖然此函式是原型才能傳回雙精度浮點數，但它一定會傳回整數值。

### <a name="remarks"></a>備註

此函式的傳回值介於大約-3.16e11 至 3.16e11。

其他查詢的值的函式`COleDateTimeSpan`物件，請參閱下列成員函式：

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

### <a name="example"></a>範例

範例，請參閱[GetTotalDays](#gettotaldays)。

##  <a name="m_span"></a>  COleDateTimeSpan::m_span

基礎**雙**值，這個`COleDateTime`物件。

```
double m_span;
```

### <a name="remarks"></a>備註

這個值表示日期/時間範圍以天為單位。

> [!CAUTION]
>  變更中的值**雙**資料成員，這個值將`COleDateTimeSpan`物件。 它不會變更這個狀態`COleDateTimeSpan`物件。

##  <a name="m_status"></a>  COleDateTimeSpan::m_status

此資料成員的類型是列舉型別`DateTimeSpanStatus`，其定義內`COleDateTimeSpan`類別。

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

如這些狀態值的簡短描述，請參閱下列清單：

- `COleDateTimeSpan::valid` 指出這個`COleDateTimeSpan`物件是否有效。

- `COleDateTimeSpan::invalid` 指出這個`COleDateTimeSpan`物件無效，也就是它的值可能不正確。

- `COleDateTimeSpan::null` 指出這個`COleDateTimeSpan`物件為 null，也就是這個物件尚未提供任何值。 （這是"null"中資料庫的 「 沒有值，"而不是 c + + NULL）。

狀態`COleDateTimeSpan`在下列情況中的物件無效：

- 如果這個物件發生溢位或反向溢位算術的指派作業期間，亦即`+=`或`-=`。

- 如果無效的值已指派給這個物件。

- 如果此物件的狀態已明確設定為無效的使用[SetStatus](#setstatus)。

如需可能會將狀態設為無效的作業的詳細資訊，請參閱[COleDateTimeSpan::operator +、-](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-)並[COleDateTimeSpan::operator + =、-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq)。

> [!CAUTION]
>  此資料成員是針對進階程式設計的情況。 您應該使用的內嵌成員函式[GetStatus](#getstatus)並[SetStatus](#setstatus)。 請參閱`SetStatus`的進一步注意事項，關於明確設定此資料成員。

如需有關的界限`COleDateTimeSpan`值，請參閱文章[日期和時間： Automation 支援](../../atl-mfc-shared/date-and-time-automation-support.md)。

##  <a name="operator_eq"></a>  COleDateTimeSpan::operator =

複製`COleDateTimeSpan`值。

```
COleDateTimeSpan& operator=(double dblSpanSrc) throw();
```

### <a name="remarks"></a>備註

此多載的指派運算子會將來源日期/時間範圍值複製到這個`COleDateTimeSpan`物件。

##  <a name="operator_add_-"></a>  COleDateTimeSpan::operator +、-

新增、 subtract、 及變更符號`COleDateTimeSpan`值。

```
COleDateTimeSpan operator+(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-() const throw();
```

### <a name="remarks"></a>備註

前兩個運算子可讓您加入和減去日期/時間範圍值。 第三個可讓您變更日期/時間範圍值的正負號。

如果任一個運算元是 null，結果狀態`COleDateTimeSpan`值是 null。

如果任一運算元無效，而且其他不是 null，結果狀態`COleDateTimeSpan`值無效。

如需有關有效、 無效和 null 的狀態值的詳細資訊，請參閱[m_status](#m_status)成員變數。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#23](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_10.cpp)]

##  <a name="operator_add_eq_-_eq"></a>  COleDateTimeSpan::operator + =、 =

加法和減法`COleDateTimeSpan`值從這個`COleDateTimeSpan`值。

```
COleDateTimeSpan& operator+=(const COleDateTimeSpan dateSpan) throw();
COleDateTimeSpan& operator-=(const COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>備註

這些運算子可讓您加入和減去日期/時間範圍值，從這個`COleDateTimeSpan`物件。 如果任一個運算元是 null，結果狀態`COleDateTimeSpan`值是 null。

如果任一運算元無效，而且其他不是 null，結果狀態`COleDateTimeSpan`值無效。

如需有關有效、 無效和 null 的狀態值的詳細資訊，請參閱[m_status](#m_status)成員變數。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#24](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_11.cpp)]

##  <a name="operator_double"></a>  COleDateTimeSpan::operator double

這會將轉換`COleDateTimeSpan`值加入**double**。

```
operator double() const throw();
```

### <a name="remarks"></a>備註

這個運算子會傳回值，這個`COleDateTimeSpan`天浮點數的值。

##  <a name="setdatetimespan"></a>  COleDateTimeSpan::SetDateTimeSpan

設定此日期/時間範圍值的值。

```
void SetDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>參數

*lDays*， *nHours*， *nMins*， *nSecs*  
表示要複製到這個範圍內的日期和時間範圍值`COleDateTimeSpan`物件。

### <a name="remarks"></a>備註

查詢的值的函式`COleDateTimeSpan`物件，請參閱下列成員函式：

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

##  <a name="setstatus"></a>  COleDateTimeSpan::SetStatus

設定此狀態 （有效性）`COleDateTimeSpan`物件。

```
void SetStatus(DateTimeSpanStatus status) throw();
```

### <a name="parameters"></a>參數

*status*<br/>
這個新的狀態值`COleDateTimeSpan`物件。

### <a name="remarks"></a>備註

*狀態*參數值由定義`DateTimeSpanStatus`列舉型別，其定義內`COleDateTimeSpan`類別。

```
enum DateTimeSpanStatus{  
   valid = 0,  
   invalid = 1,  
   null = 2,  
   };  
```

如這些狀態值的簡短描述，請參閱下列清單：

- `COleDateTimeSpan::valid` 指出這個`COleDateTimeSpan`物件是否有效。

- `COleDateTimeSpan::invalid` 指出這個`COleDateTimeSpan`物件無效，也就是它的值可能不正確。

- `COleDateTimeSpan::null` 指出這個`COleDateTimeSpan`物件為 null，也就是這個物件尚未提供任何值。 （這是"null"中資料庫的 「 沒有值，"而不是 c + + NULL）。

   > [!CAUTION]
   > 此函式是進階程式設計的情況。 此函式不會更改此物件中的資料。 它將最常使用的狀態設為**null**或是**無效**。 請注意，指派運算子 ([運算子 =](#eq)) 和[SetDateTimeSpan](#setdatetimespan)沒有設定的基礎來源值的物件狀態。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#22](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_13.cpp)]

## <a name="see-also"></a>另請參閱

[COleDateTime 類別](../../atl-mfc-shared/reference/coledatetime-class.md)<br/>
[CTime 類別](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan 類別](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)

