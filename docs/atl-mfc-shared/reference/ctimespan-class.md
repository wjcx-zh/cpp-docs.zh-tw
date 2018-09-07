---
title: CTimeSpan 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- elapsed time, CTimeSpan object
- timespan
- time span
- CTimeSpan class
- shared classes, CTimeSpan
- time, elapsed
ms.assetid: ee1e42f6-1839-477a-8435-fb26ad475140
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c06da499ed463404cc917fef7c8aebd52695061e
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44109728"
---
# <a name="ctimespan-class"></a>CTimeSpan 類別

一段時間，這會在內部儲存為時間範圍中的秒數。

## <a name="syntax"></a>語法

```
class CTimeSpan
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CTimeSpan::CTimeSpan](#ctimespan)|建構`CTimeSpan`以各種方式的物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CTimeSpan::Format](#format)|將轉換`CTimeSpan`轉換為格式化的字串。|
|[CTimeSpan::GetDays](#getdays)|傳回值，這個值表示的完整天數，在此`CTimeSpan`。|
|[CTimeSpan::GetHours](#gethours)|傳回值，這個值表示目前的日期 (-23 到 23) 中的小時數。|
|[CTimeSpan::GetMinutes](#getminutes)|傳回值，這個值表示目前的小時 (-59 到 59) 中的分鐘數。|
|[CTimeSpan::GetSeconds](#getseconds)|傳回值，這個值表示目前的分鐘 (-59 到 59) 中的秒數。|
|[CTimeSpan::GetTimeSpan](#gettimespan)|傳回的值`CTimeSpan`物件。|
|[CTimeSpan::GetTotalHours](#gettotalhours)|傳回值，這個值表示在這個完成的小時總數`CTimeSpan`。|
|[CTimeSpan::GetTotalMinutes](#gettotalminutes)|傳回值，這個值表示在這個完成的分鐘總數`CTimeSpan`。|
|[CTimeSpan::GetTotalSeconds](#gettotalseconds)|傳回值，這個值表示在這個完成的秒數的總數`CTimeSpan`。|
|[CTimeSpan::Serialize64](#serialize64)|將序列化資料，或從封存。|

### <a name="operators"></a>運算子

|||
|-|-|
|[運算子 +-](#operator_add_-)|加入和減去`CTimeSpan`物件。|
|[operator + = =](#operator_add_eq_-_eq)|加入和減去`CTimeSpan`物件並從這個`CTimeSpan`。|
|[運算子 = = < 等。](#ctimespan_comparison_operators)|比較兩個相對時間值。|

## <a name="remarks"></a>備註

`CTimeSpan` 沒有基底類別。

`CTimeSpan` 函式會轉換各種組合的天數、 小時、 分鐘、 秒和秒數。

`CTimeSpan`物件會儲存在 **__time64_t**結構，也就是 8 個位元組。

附屬類別[CTime](../../atl-mfc-shared/reference/ctime-class.md)，表示絕對的時間。

`CTime`和`CTimeSpan`類別並未設計成衍生。 因為沒有虛擬函式，這兩者的大小`CTime`和`CTimeSpan`物件是完全 8 個位元組。 大部分的成員函式會以內嵌方式。

如需有關使用`CTimeSpan`，請參閱文章[日期和時間](../../atl-mfc-shared/date-and-time.md)，以及[時間管理](../../c-runtime-library/time-management.md)中*執行階段程式庫參考*。

## <a name="requirements"></a>需求

**標頭：** atltime.h

##  <a name="ctimespan_comparison_operators"></a>  CTimeSpan 比較運算子

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

*範圍*  
要比較的物件。

### <a name="return-value"></a>傳回值

這些運算子比較兩個相對時間值。 條件為 true; 如果為 true，則傳回否則為 FALSE。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#169](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_1.cpp)]

##  <a name="ctimespan"></a>  CTimeSpan::CTimeSpan

建構`CTimeSpan`以各種方式的物件。

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

*timeSpanSrc*  
A`CTimeSpan`已經存在的物件。

*time*  
A **__time64_t**時間值，也就是在時間範圍內的秒數。

*lDays*， *nHours*， *nMins*， *nSecs*  
天、 小時、 分鐘、 和秒數，分別。

### <a name="remarks"></a>備註

所有這些建構函式建立新`CTimeSpan`初始化使用指定的相對時間的物件。 每個建構函式會如下所述：

- `CTimeSpan( );` 建構未初始化`CTimeSpan`物件。

- `CTimeSpan( const CTimeSpan& );` 建構`CTimeSpan`物件從另一個`CTimeSpan`值。

- `CTimeSpan( __time64_t );` 建構`CTimeSpan`物件從 **__time64_t**型別。

- `CTimeSpan( LONG, int, int, int );` 建構`CTimeSpan`從每個元件的元件物件限制為下列範圍：

    |元件|範圍|  
    |---------------|-----------|  
    |*lDays*|0-25,000 （大約）|  
    |*nHours*|0-23|  
    |*nMins*|0-59|  
    |*nSecs*|0-59|

請注意，偵錯版本的 Mfc 程式庫判斷提示，如果有一個或多個日期時間元件 je mimo rozsah。 您必須負責驗證之前呼叫的引數。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#162](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_2.cpp)]

##  <a name="format"></a>  CTimeSpan::Format

會產生格式化的字串，對應至這個`CTimeSpan`。

```
CString Format(LPCSTR pFormat) const;
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>參數

*pFormat*， *pszFormat*  
格式化字串類似於`printf`格式化字串。 格式化程式碼，加上百分比 (`%`) 登入，會取代對應`CTimeSpan`元件。 格式化字串中的其他字元會複製到傳回的字串不變。 值和格式化的程式碼的意義`Format`如下所示：

- **%D**總天數，在此 `CTimeSpan`

- **%H**當天的時數

- **%M**目前小時的分鐘數

- **%S**中目前的分鐘的秒數

- **%%** 百分比符號

*nID*  
識別此格式的字串識別碼。

### <a name="return-value"></a>傳回值

A`CString`物件，其中包含格式的時間。

### <a name="remarks"></a>備註

程式庫的偵錯版本會檢查格式化程式碼，並判斷提示程式碼是否不在上述清單中。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#163](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_3.cpp)]

##  <a name="getdays"></a>  CTimeSpan::GetDays

傳回值，這個值表示的完整天數，在此`CTimeSpan`。

```
LONGLONG GetDays() const throw();
```

### <a name="return-value"></a>傳回值

傳回天數完成 24 小時制的時間範圍中。 這個值可能是負數，如果時間範圍為負數。

### <a name="remarks"></a>備註

請注意，日光節約時間可能會導致`GetDays`傳回可能令人驚訝的結果。 例如，當 DST 是作用中，`GetDays`回報年 1 月 1 日之間的天數為 29，不 30 日，因為在 4 月的一天一小時已縮短，因此不算是完整的一天。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#164](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_4.cpp)]

##  <a name="gethours"></a>  CTimeSpan::GetHours

傳回值，這個值表示目前的日期 (-23 到 23) 中的小時數。

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>傳回值

傳回目前日期的小時數。 範圍是從-23 到 23。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#165](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_5.cpp)]

##  <a name="getminutes"></a>  CTimeSpan::GetMinutes

傳回值，這個值表示目前的小時 (-59 到 59) 中的分鐘數。

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>傳回值

傳回在目前的小時的分鐘數。 範圍是從-59 到 59。

### <a name="example"></a>範例

範例，請參閱[GetHours](#gethours)。

##  <a name="getseconds"></a>  CTimeSpan::GetSeconds

傳回值，這個值表示目前的分鐘 (-59 到 59) 中的秒數。

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>傳回值

傳回在目前的分鐘的秒數。 範圍是從-59 到 59。

### <a name="example"></a>範例

範例，請參閱[GetHours](#gethours)。

##  <a name="gettimespan"></a>  CTimeSpan::GetTimeSpan

傳回的值`CTimeSpan`物件。

```
__ time64_t GetTimeSpan() const throw();
```

### <a name="return-value"></a>傳回值

傳回目前的值`CTimeSpan`物件。

##  <a name="gettotalhours"></a>  CTimeSpan::GetTotalHours

傳回值，這個值表示在這個完成的小時總數`CTimeSpan`。

```
LONGLONG GetTotalHours() const throw();
```

### <a name="return-value"></a>傳回值

在此會傳回完整的小時總數`CTimeSpan`。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#166](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_6.cpp)]

##  <a name="gettotalminutes"></a>  CTimeSpan::GetTotalMinutes

傳回值，這個值表示在這個完成的分鐘總數`CTimeSpan`。

```
LONGLONG GetTotalMinutes() const throw();
```

### <a name="return-value"></a>傳回值

在此會傳回完整的分鐘總數`CTimeSpan`。

### <a name="example"></a>範例

範例，請參閱[GetTotalHours](#gettotalhours)。

##  <a name="gettotalseconds"></a>  CTimeSpan::GetTotalSeconds

傳回值，這個值表示在這個完成的秒數的總數`CTimeSpan`。

```
LONGLONG GetTotalSeconds() const throw();
```

### <a name="return-value"></a>傳回值

在此傳回總完成的秒數`CTimeSpan`。

### <a name="example"></a>範例

範例，請參閱[GetTotalHours](#gettotalhours)。

##  <a name="operator_add_-"></a>  CTimeSpan::operator +、-

加入和減去`CTimeSpan`物件。

```
CTimeSpan operator+(CTimeSpan span) const throw();
CTimeSpan operator-(CTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*範圍*  
要加入至值`CTimeSpan`物件。

### <a name="return-value"></a>傳回值

A`CTimeSpan`物件，表示作業的結果。

### <a name="remarks"></a>備註

這兩個運算子可讓您加入和減去`CTimeSpan`物件與彼此。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#167](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_7.cpp)]

##  <a name="operator_add_eq_-_eq"></a>  CTimeSpan::operator + =、 =

加入和減去`CTimeSpan`物件並從這個`CTimeSpan`。

```
CTimeSpan& operator+=(CTimeSpan span) throw();
CTimeSpan& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>參數

*範圍*  
要加入至值`CTimeSpan`物件。

### <a name="return-value"></a>傳回值

已更新`CTimeSpan`物件。

### <a name="remarks"></a>備註

這些運算子可讓您加入和減去`CTimeSpan`物件並從這個`CTimeSpan`。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#168](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_8.cpp)]

##  <a name="serialize64"></a>  CTimeSpan::Serialize64

> [!NOTE]
>  只有在 MFC 專案中，您可以使用這個方法。

將序列化的成員變數，或從封存相關聯的資料。

```
CArchive& Serialize64(CArchive& ar);
```

### <a name="parameters"></a>參數

*ar*  
`CArchive`您想要更新的物件。

### <a name="return-value"></a>傳回值

已更新`CArchive`物件。

## <a name="see-also"></a>另請參閱

[asctime、_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
[_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
[gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
[localtime、_localtime32、_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
[strftime、wcsftime、_strftime_l、_wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
[time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)   
[階層架構圖表](../../mfc/hierarchy-chart.md)   
[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)

