---
title: CTimeSpan 類別
ms.date: 10/18/2018
f1_keywords:
- CTimeSpan
- ATLTIME/ATL::CTimeSpan
- ATLTIME/ATL::CTimeSpan::CTimeSpan
- ATLTIME/ATL::CTimeSpan::Format
- ATLTIME/ATL::CTimeSpan::GetDays
- ATLTIME/ATL::CTimeSpan::GetHours
- ATLTIME/ATL::CTimeSpan::GetMinutes
- ATLTIME/ATL::CTimeSpan::GetSeconds
- ATLTIME/ATL::CTimeSpan::GetTimeSpan
- ATLTIME/ATL::CTimeSpan::GetTotalHours
- ATLTIME/ATL::CTimeSpan::GetTotalMinutes
- ATLTIME/ATL::CTimeSpan::GetTotalSeconds
- ATLTIME/ATL::CTimeSpan::Serialize64
helpviewer_keywords:
- elapsed time, CTimeSpan object
- timespan
- time span
- CTimeSpan class
- shared classes, CTimeSpan
- time, elapsed
ms.assetid: ee1e42f6-1839-477a-8435-fb26ad475140
ms.openlocfilehash: 0c13aa0d8f6c46db3b018283ab2a408a3f9531e1
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832018"
---
# <a name="ctimespan-class"></a>CTimeSpan 類別

一段時間，在內部儲存為時間範圍中的秒數。

## <a name="syntax"></a>語法

```
class CTimeSpan
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CTimeSpan：： CTimeSpan](#ctimespan)|`CTimeSpan`以各種方式來結構物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CTimeSpan：： Format](#format)|將轉換 `CTimeSpan` 成格式化的字串。|
|[CTimeSpan：： GetDays](#getdays)|傳回值，這個值表示此中的完整天數 `CTimeSpan` 。|
|[CTimeSpan：： GetHours](#gethours)|傳回值，這個值表示目前的日期 (-23 到 23) 的小時數。|
|[CTimeSpan：： GetMinutes](#getminutes)|傳回值，這個值表示目前小時 (-59 到 59) 的分鐘數。|
|[CTimeSpan：： GetSeconds](#getseconds)|傳回值，這個值表示目前分鐘 (-59 到 59) 的秒數。|
|[CTimeSpan：： GetTimeSpan](#gettimespan)|傳回物件的值 `CTimeSpan` 。|
|[CTimeSpan：： GetTotalHours](#gettotalhours)|傳回值，這個值表示這個中的完整時數總數 `CTimeSpan` 。|
|[CTimeSpan：： GetTotalMinutes](#gettotalminutes)|傳回值，這個值表示這個中完整分鐘數的總分鐘數 `CTimeSpan` 。|
|[CTimeSpan：： GetTotalSeconds](#gettotalseconds)|傳回值，這個值表示這個中完整秒數的總秒數 `CTimeSpan` 。|
|[CTimeSpan：： Serialize64](#serialize64)|序列化封存的資料。|

### <a name="operators"></a>運算子

|名稱|描述|
|-|-|
|[運算子 +-](#operator_add_-)|加入和減去 `CTimeSpan` 物件。|
|[運算子 + =-=](#operator_add_eq_-_eq)|將 `CTimeSpan` 物件加入至這個的或從中減去 `CTimeSpan` 。|
|[operator = = < 等等。](#ctimespan_comparison_operators)|比較兩個相對時間值。|

## <a name="remarks"></a>備註

`CTimeSpan` 沒有基類。

`CTimeSpan` 函數會將秒數轉換成不同的天數、時數、分鐘數和秒數的組合。

`CTimeSpan`物件儲存在 **__time64_t**結構中，也就是8個位元組。

附屬類別（ [CTime](../../atl-mfc-shared/reference/ctime-class.md)）表示絕對時間。

`CTime`和 `CTimeSpan` 類別並非針對衍生而設計。 因為沒有虛擬函式，所以和物件的大小 `CTime` `CTimeSpan` 正好是8個位元組。 大部分的成員函式都是內嵌的。

如需有關使用的詳細資訊 `CTimeSpan` ，請參閱《*執行時間程式庫參考*》中的文章[日期和時間](../../atl-mfc-shared/date-and-time.md)以及[時間管理](../../c-runtime-library/time-management.md)。

## <a name="requirements"></a>規格需求

**標頭：** atltime。h

## <a name="ctimespan-comparison-operators"></a><a name="ctimespan_comparison_operators"></a> CTimeSpan 比較運算子

比較運算子。

```
bool operator==(CTimeSpan span) const throw();
bool operator!=(CTimeSpan span) const throw();
bool operator<(CTimeSpan span) const throw();
bool operator>(CTimeSpan span) const throw();
bool operator<=(CTimeSpan span) const throw();
bool operator>=(CTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*跨度*<br/>
要比較的物件。

### <a name="return-value"></a>傳回值

這些運算子會比較兩個相對時間值。 如果條件為 true，則會傳回 TRUE;否則為 FALSE。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#169](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_1.cpp)]

## <a name="ctimespanctimespan"></a><a name="ctimespan"></a> CTimeSpan：： CTimeSpan

`CTimeSpan`以各種方式來結構物件。

```
CTimeSpan() throw();
CTimeSpan(__time64_t time) throw();

CTimeSpan(
    LONG lDays,
    int nHours,
    int nMins,
    int nSecs) throw();
```

### <a name="parameters"></a>參數

*timeSpanSrc*<br/>
`CTimeSpan`已經存在的物件。

*time*<br/>
**__Time64_t**時間值，這是時間範圍中的秒數。

*lDays*、 *nHours*、 *nMins*、 *nSecs*<br/>
分別是天、小時、分鐘和秒。

### <a name="remarks"></a>備註

所有這些函式都會建立 `CTimeSpan` 以指定的相對時間初始化的新物件。 以下說明每個函式：

- `CTimeSpan( );` 結構未初始化的 `CTimeSpan` 物件。

- `CTimeSpan( const CTimeSpan& );``CTimeSpan`從另一個值中建立物件 `CTimeSpan` 。

- `CTimeSpan( __time64_t );``CTimeSpan`從 **__time64_t**類型中建立物件。

- `CTimeSpan( LONG, int, int, int );``CTimeSpan`從元件中，將每個元件限制為下列範圍的物件：

   |元件|範圍|
   |---------------|-----------|
   |*lDays*|0-25000 (大約) |
   |*nHours*|0-23|
   |*nMins*|0-59|
   |*nSecs*|0-59|

請注意，如果有一或多個時間範圍元件超出範圍，MFC 程式庫的偵錯工具會進行判斷提示。 在呼叫之前，您必須負責驗證引數。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#162](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_2.cpp)]

## <a name="ctimespanformat"></a><a name="format"></a> CTimeSpan：： Format

產生對應于這個的格式化字串 `CTimeSpan` 。

```
CString Format(LPCSTR pFormat) const;
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>參數

*pformatetc 架構*、 *pszFormat*<br/>
格式化字串，類似于 `printf` 格式化字串。 格式化程式碼（前面加上% (`%`) 號）會取代為對應的 `CTimeSpan` 元件。 格式化字串中的其他字元會原封不動地複製到傳回的字串。 的格式化程式碼的值和意義如下所示 `Format` ：

- **% D** 此中的總天數 `CTimeSpan`

- **% H** 當天的小時數

- **% M** 目前小時的分鐘數

- **% S** 目前分鐘的秒數

- **%%** 百分比符號

*nID*<br/>
識別此格式之字串的識別碼。

### <a name="return-value"></a>傳回值

`CString`包含格式化時間的物件。

### <a name="remarks"></a>備註

如果程式碼不在上述清單中，則程式庫的偵錯工具會檢查格式化程式碼和判斷提示。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#163](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_3.cpp)]

## <a name="ctimespangetdays"></a><a name="getdays"></a> CTimeSpan：： GetDays

傳回值，這個值表示此中的完整天數 `CTimeSpan` 。

```
LONGLONG GetDays() const throw();
```

### <a name="return-value"></a>傳回值

傳回時間範圍內的完整24小時數。 如果時間範圍是負數，則這個值可能是負數。

### <a name="remarks"></a>備註

請注意，日光節約時間可能會導致傳回 `GetDays` 可能令人驚訝的結果。 例如，當 DST 生效時，會 `GetDays` 報告在4月1日到5月1日到29日之間的天數，而不是30，因為四月的一天會縮短一小時，因此不會計算為完整一天。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#164](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_4.cpp)]

## <a name="ctimespangethours"></a><a name="gethours"></a> CTimeSpan：： GetHours

傳回值，這個值表示目前的日期 (-23 到 23) 的小時數。

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>傳回值

傳回目前日期中的時數。 範圍是-23 到23。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#165](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_5.cpp)]

## <a name="ctimespangetminutes"></a><a name="getminutes"></a> CTimeSpan：： GetMinutes

傳回值，這個值表示目前小時 (-59 到 59) 的分鐘數。

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>傳回值

傳回目前小時的分鐘數。 範圍是-59 到59。

### <a name="example"></a>範例

請參閱 [GetHours](#gethours)的範例。

## <a name="ctimespangetseconds"></a><a name="getseconds"></a> CTimeSpan：： GetSeconds

傳回值，這個值表示目前分鐘 (-59 到 59) 的秒數。

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>傳回值

傳回目前分鐘的秒數。 範圍是-59 到59。

### <a name="example"></a>範例

請參閱 [GetHours](#gethours)的範例。

## <a name="ctimespangettimespan"></a><a name="gettimespan"></a> CTimeSpan：： GetTimeSpan

傳回物件的值 `CTimeSpan` 。

```
__ time64_t GetTimeSpan() const throw();
```

### <a name="return-value"></a>傳回值

傳回物件的目前值 `CTimeSpan` 。

## <a name="ctimespangettotalhours"></a><a name="gettotalhours"></a> CTimeSpan：： GetTotalHours

傳回值，這個值表示這個中的完整時數總數 `CTimeSpan` 。

```
LONGLONG GetTotalHours() const throw();
```

### <a name="return-value"></a>傳回值

傳回這個中完成的總時數 `CTimeSpan` 。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#166](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_6.cpp)]

## <a name="ctimespangettotalminutes"></a><a name="gettotalminutes"></a> CTimeSpan：： GetTotalMinutes

傳回值，這個值表示這個中完整分鐘數的總分鐘數 `CTimeSpan` 。

```
LONGLONG GetTotalMinutes() const throw();
```

### <a name="return-value"></a>傳回值

傳回這個中的完整分鐘數總計 `CTimeSpan` 。

### <a name="example"></a>範例

請參閱 [GetTotalHours](#gettotalhours)的範例。

## <a name="ctimespangettotalseconds"></a><a name="gettotalseconds"></a> CTimeSpan：： GetTotalSeconds

傳回值，這個值表示這個中完整秒數的總秒數 `CTimeSpan` 。

```
LONGLONG GetTotalSeconds() const throw();
```

### <a name="return-value"></a>傳回值

傳回這個中完成的總秒數 `CTimeSpan` 。

### <a name="example"></a>範例

請參閱 [GetTotalHours](#gettotalhours)的範例。

## <a name="ctimespanoperator---"></a><a name="operator_add_-"></a> CTimeSpan：： operator +、-

加入和減去 `CTimeSpan` 物件。

```
CTimeSpan operator+(CTimeSpan span) const throw();
CTimeSpan operator-(CTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*跨度*<br/>
要加入至物件的值 `CTimeSpan` 。

### <a name="return-value"></a>傳回值

`CTimeSpan`物件，代表運算的結果。

### <a name="remarks"></a>備註

這兩個運算子可讓您在彼此之間新增和減少 `CTimeSpan` 物件。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#167](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_7.cpp)]

## <a name="ctimespanoperator---"></a><a name="operator_add_eq_-_eq"></a> CTimeSpan：： operator + =，-=

將 `CTimeSpan` 物件加入至這個的或從中減去 `CTimeSpan` 。

```
CTimeSpan& operator+=(CTimeSpan span) throw();
CTimeSpan& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>參數

*跨度*<br/>
要加入至物件的值 `CTimeSpan` 。

### <a name="return-value"></a>傳回值

更新的 `CTimeSpan` 物件。

### <a name="remarks"></a>備註

這些運算子可讓您在此加入和減去 `CTimeSpan` 物件 `CTimeSpan` 。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#168](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_8.cpp)]

## <a name="ctimespanserialize64"></a><a name="serialize64"></a> CTimeSpan：： Serialize64

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

[asctime、_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)<br/>
[_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)<br/>
[localtime，_localtime32，_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)<br/>
[strftime、wcsftime、_strftime_l、_wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)
