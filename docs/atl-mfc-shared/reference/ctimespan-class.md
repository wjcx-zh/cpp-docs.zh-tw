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
ms.openlocfilehash: 14aa5eb52e2c631a92e40ae7053c566284e00e57
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317508"
---
# <a name="ctimespan-class"></a>CTimeSpan 類別

時間量,在內部存儲為時間跨度中的秒數。

## <a name="syntax"></a>語法

```
class CTimeSpan
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CTimeSpan:CTimeSpan](#ctimespan)|以各種方式構造`CTimeSpan`物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CTimeSpan:格式](#format)|轉換為`CTimeSpan`格式化的字串。|
|[CTimeSpan:抓取天](#getdays)|返回表示此`CTimeSpan`中完整天數的值。|
|[CTimeSpan:抓取小時數](#gethours)|返回表示當天小時數的值(-23 到 23)。|
|[CTimeSpan:取得分鐘數](#getminutes)|返回表示當前小時中的分鐘數的值 (-59 到 59)。|
|[CTimeSpan:取得秒數](#getseconds)|返回表示當前分鐘(-59 到 59)中的秒數的值。|
|[CTimeSpan:取得時間跨度](#gettimespan)|返回`CTimeSpan`物件的值。|
|[CTimeSpan:獲取總小時數](#gettotalhours)|返回表示此`CTimeSpan`中完整小時總數的值。|
|[CTimeSpan:獲取總分鐘數](#gettotalminutes)|返回表示此`CTimeSpan`中完整分鐘總數的值。|
|[CTimeSpan:取得總秒數](#gettotalseconds)|返回表示此`CTimeSpan`中完整秒總數的值。|
|[CTimeSpan:序列化64](#serialize64)|將資料序列化到存檔或從存檔中序列化。|

### <a name="operators"></a>操作員

|||
|-|-|
|[運算子 = -](#operator_add_-)|添加和減去`CTimeSpan`物件。|
|[運算子 = -}](#operator_add_eq_-_eq)|在此添加和減去`CTimeSpan`物件`CTimeSpan`。|
|[運算符 = < 等。](#ctimespan_comparison_operators)|比較兩個相對的時間值。|

## <a name="remarks"></a>備註

`CTimeSpan`沒有基類。

`CTimeSpan`函數將秒轉換為天、小時、分鐘和秒的各種組合。

物件`CTimeSpan`存儲在 **__time64_t**結構中,該結構為 8 個字節。

配套類[CTime](../../atl-mfc-shared/reference/ctime-class.md)表示絕對時間。

和`CTime``CTimeSpan`類不是為派生而設計的。 由於沒有虛擬函數,因此兩個`CTime`函數`CTimeSpan`和 物件的大小正好為 8 個字節。 大多數成員函數是內聯的。

`CTimeSpan`有關使用的詳細資訊,請參閱*執行時庫參考*中的文章[日期和時間](../../atl-mfc-shared/date-and-time.md), 以及[時間管理](../../c-runtime-library/time-management.md)。

## <a name="requirements"></a>需求

**標題:** atltime.h

## <a name="ctimespan-comparison-operators"></a><a name="ctimespan_comparison_operators"></a>CTimeSpan 比較運算子

比較運算符。

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

這些運算碼比較兩個相對時間值。 如果條件為 true,它們返回 TRUE;否則 FALSE。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#169](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_1.cpp)]

## <a name="ctimespanctimespan"></a><a name="ctimespan"></a>CTimeSpan:CTimeSpan

以各種方式構造`CTimeSpan`物件。

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

*時間斯潘斯克*<br/>
已`CTimeSpan`存在的物件。

*time*<br/>
**__time64_t**時間值,即時間跨度中的秒數。

*l 天*, *nHours*, *nMins*, *nSecs*<br/>
天、小時、分鐘和秒。

### <a name="remarks"></a>備註

所有這些構造函數都創建一個使用`CTimeSpan`指定相對時間初始化的新物件。 下面將介紹每個建構函數:

- `CTimeSpan( );`構造未初始化`CTimeSpan`的物件。

- `CTimeSpan( const CTimeSpan& );`從另一`CTimeSpan`個`CTimeSpan`值構造物件。

- `CTimeSpan( __time64_t );`從__time64_t類型`CTimeSpan`構造物件。 **__time64_t**

- `CTimeSpan( LONG, int, int, int );`從元件建構`CTimeSpan`一個物件,每個元件都受限制在以下範圍:

   |元件|範圍|
   |---------------|-----------|
   |*l 天*|0-25,000 (大約)|
   |*n小時*|0-23|
   |*n明斯*|0-59|
   |*nSecs*|0-59|

請注意,如果一個或多個時間日元件不在範圍內,Microsoft 基礎類庫的調試版本將斷言。 您有責任在調用之前驗證參數。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#162](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_2.cpp)]

## <a name="ctimespanformat"></a><a name="format"></a>CTimeSpan:格式

生成對應於此`CTimeSpan`的格式化字串。

```
CString Format(LPCSTR pFormat) const;
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>參數

*p 格式*, *psz 格式*<br/>
類似於格式字串的`printf`格式字串。 格式代碼(前面為百分比`%`( ) 符號`CTimeSpan`,由相應的 元件替換。 格式字串中的其他字元將複製到傳回的字串。 下面列出格式化`Format`代碼的值與含義:

- **%D**此總計天數`CTimeSpan`

- **%H**當天的小時數

- **%M**目前的小時內的分鐘數

- **%S**目前分鐘中的秒數

- **%%** 百分比符號

*nID*<br/>
識別此格式的字串的識別碼。

### <a name="return-value"></a>傳回值

包含`CString`格式化時間的物件。

### <a name="remarks"></a>備註

如果代碼不在上述清單中,則庫的調試版本將檢查格式代碼並斷言。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#163](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_3.cpp)]

## <a name="ctimespangetdays"></a><a name="getdays"></a>CTimeSpan:抓取天

返回表示此`CTimeSpan`中完整天數的值。

```
LONGLONG GetDays() const throw();
```

### <a name="return-value"></a>傳回值

返回時間跨度中已完成 24 小時天數的數量。 如果時間跨度為負數,則此值可能是負值。

### <a name="remarks"></a>備註

請注意,夏令時可能會導致`GetDays`返回可能令人驚訝的結果。 例如,當 DST 生效`GetDays`時, 將 4 月 1 日至 5 月 1 日期間的天數報告為 29 天,而不是 30 天,因為 4 月的一天縮短為一小時,因此不計為完整日期。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#164](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_4.cpp)]

## <a name="ctimespangethours"></a><a name="gethours"></a>CTimeSpan:抓取小時數

返回表示當天小時數的值(-23 到 23)。

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>傳回值

返回當天的小時數。 範圍為 -23 到 23。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#165](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_5.cpp)]

## <a name="ctimespangetminutes"></a><a name="getminutes"></a>CTimeSpan:取得分鐘數

返回表示當前小時中的分鐘數的值 (-59 到 59)。

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>傳回值

返回當前小時內的分鐘數。 範圍為 -59 到 59。

### <a name="example"></a>範例

請參閱[GetHours](#gethours)的範例。

## <a name="ctimespangetseconds"></a><a name="getseconds"></a>CTimeSpan:取得秒數

返回表示當前分鐘(-59 到 59)中的秒數的值。

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>傳回值

返回當前分鐘中的秒數。 範圍為 -59 到 59。

### <a name="example"></a>範例

請參閱[GetHours](#gethours)的範例。

## <a name="ctimespangettimespan"></a><a name="gettimespan"></a>CTimeSpan:取得時間跨度

返回`CTimeSpan`物件的值。

```
__ time64_t GetTimeSpan() const throw();
```

### <a name="return-value"></a>傳回值

返回`CTimeSpan`物件的當前值。

## <a name="ctimespangettotalhours"></a><a name="gettotalhours"></a>CTimeSpan:獲取總小時數

返回表示此`CTimeSpan`中完整小時總數的值。

```
LONGLONG GetTotalHours() const throw();
```

### <a name="return-value"></a>傳回值

返回此`CTimeSpan`中的完整小時總數。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#166](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_6.cpp)]

## <a name="ctimespangettotalminutes"></a><a name="gettotalminutes"></a>CTimeSpan:獲取總分鐘數

返回表示此`CTimeSpan`中完整分鐘總數的值。

```
LONGLONG GetTotalMinutes() const throw();
```

### <a name="return-value"></a>傳回值

返回此`CTimeSpan`中的完整分鐘總數。

### <a name="example"></a>範例

請參考[GetTotalHours 的範例](#gettotalhours)。

## <a name="ctimespangettotalseconds"></a><a name="gettotalseconds"></a>CTimeSpan:取得總秒數

返回表示此`CTimeSpan`中完整秒總數的值。

```
LONGLONG GetTotalSeconds() const throw();
```

### <a name="return-value"></a>傳回值

返回此`CTimeSpan`中的完整秒總數。

### <a name="example"></a>範例

請參考[GetTotalHours 的範例](#gettotalhours)。

## <a name="ctimespanoperator---"></a><a name="operator_add_-"></a>CTimeSpan::運算符 +, -

添加和減去`CTimeSpan`物件。

```
CTimeSpan operator+(CTimeSpan span) const throw();
CTimeSpan operator-(CTimeSpan span) const throw();
```

### <a name="parameters"></a>參數

*跨度*<br/>
要新增到物件的值`CTimeSpan`。

### <a name="return-value"></a>傳回值

表示`CTimeSpan`操作結果的物件。

### <a name="remarks"></a>備註

這兩個運算符允許您相互添加和減去`CTimeSpan`物件。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#167](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_7.cpp)]

## <a name="ctimespanoperator---"></a><a name="operator_add_eq_-_eq"></a>CTimeSpan::運算符 *,-*

在此添加和減去`CTimeSpan`物件`CTimeSpan`。

```
CTimeSpan& operator+=(CTimeSpan span) throw();
CTimeSpan& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>參數

*跨度*<br/>
要新增到物件的值`CTimeSpan`。

### <a name="return-value"></a>傳回值

更新`CTimeSpan`的物件。

### <a name="remarks"></a>備註

這些運算子允許您在此與 中新增與`CTimeSpan`減去`CTimeSpan`物件 。

### <a name="example"></a>範例

[!code-cpp[NVC_ATLMFC_Utilities#168](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_8.cpp)]

## <a name="ctimespanserialize64"></a><a name="serialize64"></a>CTimeSpan:序列化64

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

[asctime、_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)<br/>
[_ftime、_ftime32、_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)<br/>
[localtime、_localtime32、_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)<br/>
[strftime、wcsftime、_strftime_l、_wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time、_time32、_time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)
