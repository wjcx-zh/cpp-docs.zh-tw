---
title: CMonthCalCtrl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl::CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl::Create
- AFXDTCTL/CMonthCalCtrl::GetCalendarBorder
- AFXDTCTL/CMonthCalCtrl::GetCalendarCount
- AFXDTCTL/CMonthCalCtrl::GetCalendarGridInfo
- AFXDTCTL/CMonthCalCtrl::GetCalID
- AFXDTCTL/CMonthCalCtrl::GetColor
- AFXDTCTL/CMonthCalCtrl::GetCurrentView
- AFXDTCTL/CMonthCalCtrl::GetCurSel
- AFXDTCTL/CMonthCalCtrl::GetFirstDayOfWeek
- AFXDTCTL/CMonthCalCtrl::GetMaxSelCount
- AFXDTCTL/CMonthCalCtrl::GetMaxTodayWidth
- AFXDTCTL/CMonthCalCtrl::GetMinReqRect
- AFXDTCTL/CMonthCalCtrl::GetMonthDelta
- AFXDTCTL/CMonthCalCtrl::GetMonthRange
- AFXDTCTL/CMonthCalCtrl::GetRange
- AFXDTCTL/CMonthCalCtrl::GetSelRange
- AFXDTCTL/CMonthCalCtrl::GetToday
- AFXDTCTL/CMonthCalCtrl::HitTest
- AFXDTCTL/CMonthCalCtrl::IsCenturyView
- AFXDTCTL/CMonthCalCtrl::IsDecadeView
- AFXDTCTL/CMonthCalCtrl::IsMonthView
- AFXDTCTL/CMonthCalCtrl::IsYearView
- AFXDTCTL/CMonthCalCtrl::SetCalendarBorder
- AFXDTCTL/CMonthCalCtrl::SetCalendarBorderDefault
- AFXDTCTL/CMonthCalCtrl::SetCalID
- AFXDTCTL/CMonthCalCtrl::SetCenturyView
- AFXDTCTL/CMonthCalCtrl::SetColor
- AFXDTCTL/CMonthCalCtrl::SetCurrentView
- AFXDTCTL/CMonthCalCtrl::SetCurSel
- AFXDTCTL/CMonthCalCtrl::SetDayState
- AFXDTCTL/CMonthCalCtrl::SetDecadeView
- AFXDTCTL/CMonthCalCtrl::SetFirstDayOfWeek
- AFXDTCTL/CMonthCalCtrl::SetMaxSelCount
- AFXDTCTL/CMonthCalCtrl::SetMonthDelta
- AFXDTCTL/CMonthCalCtrl::SetMonthView
- AFXDTCTL/CMonthCalCtrl::SetRange
- AFXDTCTL/CMonthCalCtrl::SetSelRange
- AFXDTCTL/CMonthCalCtrl::SetToday
- AFXDTCTL/CMonthCalCtrl::SetYearView
- AFXDTCTL/CMonthCalCtrl::SizeMinReq
- AFXDTCTL/CMonthCalCtrl::SizeRectToMin
dev_langs:
- C++
helpviewer_keywords:
- CMonthCalCtrl [MFC], CMonthCalCtrl
- CMonthCalCtrl [MFC], Create
- CMonthCalCtrl [MFC], GetCalendarBorder
- CMonthCalCtrl [MFC], GetCalendarCount
- CMonthCalCtrl [MFC], GetCalendarGridInfo
- CMonthCalCtrl [MFC], GetCalID
- CMonthCalCtrl [MFC], GetColor
- CMonthCalCtrl [MFC], GetCurrentView
- CMonthCalCtrl [MFC], GetCurSel
- CMonthCalCtrl [MFC], GetFirstDayOfWeek
- CMonthCalCtrl [MFC], GetMaxSelCount
- CMonthCalCtrl [MFC], GetMaxTodayWidth
- CMonthCalCtrl [MFC], GetMinReqRect
- CMonthCalCtrl [MFC], GetMonthDelta
- CMonthCalCtrl [MFC], GetMonthRange
- CMonthCalCtrl [MFC], GetRange
- CMonthCalCtrl [MFC], GetSelRange
- CMonthCalCtrl [MFC], GetToday
- CMonthCalCtrl [MFC], HitTest
- CMonthCalCtrl [MFC], IsCenturyView
- CMonthCalCtrl [MFC], IsDecadeView
- CMonthCalCtrl [MFC], IsMonthView
- CMonthCalCtrl [MFC], IsYearView
- CMonthCalCtrl [MFC], SetCalendarBorder
- CMonthCalCtrl [MFC], SetCalendarBorderDefault
- CMonthCalCtrl [MFC], SetCalID
- CMonthCalCtrl [MFC], SetCenturyView
- CMonthCalCtrl [MFC], SetColor
- CMonthCalCtrl [MFC], SetCurrentView
- CMonthCalCtrl [MFC], SetCurSel
- CMonthCalCtrl [MFC], SetDayState
- CMonthCalCtrl [MFC], SetDecadeView
- CMonthCalCtrl [MFC], SetFirstDayOfWeek
- CMonthCalCtrl [MFC], SetMaxSelCount
- CMonthCalCtrl [MFC], SetMonthDelta
- CMonthCalCtrl [MFC], SetMonthView
- CMonthCalCtrl [MFC], SetRange
- CMonthCalCtrl [MFC], SetSelRange
- CMonthCalCtrl [MFC], SetToday
- CMonthCalCtrl [MFC], SetYearView
- CMonthCalCtrl [MFC], SizeMinReq
- CMonthCalCtrl [MFC], SizeRectToMin
ms.assetid: a42f6bd6-ab5c-4335-82f8-839982fc64a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 537cbe3f1ccf563114f5a32f61cafe39e8006746
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078137"
---
# <a name="cmonthcalctrl-class"></a>CMonthCalCtrl 類別

封裝月曆控制項的功能。

## <a name="syntax"></a>語法

```
class CMonthCalCtrl : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMonthCalCtrl::CMonthCalCtrl](#cmonthcalctrl)|建構 `CMonthCalCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMonthCalCtrl::Create](#create)|建立月曆控制項，並將它附加至`CMonthCalCtrl`物件。|
|[CMonthCalCtrl::GetCalendarBorder](#getcalendarborder)|擷取目前的月曆控制項的框線寬度。|
|[CMonthCalCtrl::GetCalendarCount](#getcalendarcount)|擷取目前的月份行事曆控制項中顯示的行事曆的數目。|
|[CMonthCalCtrl::GetCalendarGridInfo](#getcalendargridinfo)|擷取目前的月曆控制項的相關資訊。|
|[CMonthCalCtrl::GetCalID](#getcalid)|擷取目前的月曆控制項的行事曆識別碼。|
|[CMonthCalCtrl::GetColor](#getcolor)|取得指定區域的月曆控制項中的色彩。|
|[CMonthCalCtrl::GetCurrentView](#getcurrentview)|擷取目前顯示月份行事曆控制項的檢視。|
|[CMonthCalCtrl::GetCurSel](#getcursel)|擷取系統時間，以在目前選取的日期。|
|[CMonthCalCtrl::GetFirstDayOfWeek](#getfirstdayofweek)|取得要顯示的行事曆的最左邊資料行中一週的第一天。|
|[CMonthCalCtrl::GetMaxSelCount](#getmaxselcount)|擷取目前的最大數目的月曆控制項中可選取的天數。|
|[CMonthCalCtrl::GetMaxTodayWidth](#getmaxtodaywidth)|擷取目前的月曆控制項的 「 今天 」 字串的最大寬度。|
|[CMonthCalCtrl::GetMinReqRect](#getminreqrect)|擷取月份行事曆控制項中顯示完整月份所需的最小大小。|
|[CMonthCalCtrl::GetMonthDelta](#getmonthdelta)|擷取月曆控制項的捲動速率。|
|[CMonthCalCtrl::GetMonthRange](#getmonthrange)|擷取的日期表示月曆控制項的顯示的高低限制的資訊。|
|[CMonthCalCtrl::GetRange](#getrange)|擷取在月曆控制項中設定的目前最小和最大日期。|
|[CMonthCalCtrl::GetSelRange](#getselrange)|擷取表示目前使用者所選取的日期範圍的上限與下限的日期資訊。|
|[CMonthCalCtrl::GetToday](#gettoday)|擷取指定為"today"的月曆控制項的日期的日期資訊。|
|[CMonthCalCtrl::HitTest](#hittest)|判斷在螢幕上的指定點在月曆控制項的哪個區段。|
|[CMonthCalCtrl::IsCenturyView](#iscenturyview)|指出目前的月曆控制項的目前檢視是否為世紀檢視。|
|[CMonthCalCtrl::IsDecadeView](#isdecadeview)|指出目前的月曆控制項的目前檢視是否為十年來檢視。|
|[CMonthCalCtrl::IsMonthView](#ismonthview)|指出目前的月曆控制項的目前檢視是否為 [月] 檢視。|
|[CMonthCalCtrl::IsYearView](#isyearview)|指出目前的月曆控制項的目前檢視是否為 [年] 檢視。|
|[CMonthCalCtrl::SetCalendarBorder](#setcalendarborder)|設定目前的月份行事曆控制項的框線寬度。|
|[CMonthCalCtrl::SetCalendarBorderDefault](#setcalendarborderdefault)|設定目前的月份行事曆控制項的框線的預設寬度。|
|[CMonthCalCtrl::SetCalID](#setcalid)|設定目前的月曆控制項的行事曆識別碼。|
|[CMonthCalCtrl::SetCenturyView](#setcenturyview)|設定目前的月份行事曆控制，以顯示世紀檢視。|
|[CMonthCalCtrl::SetColor](#setcolor)|設定月曆控制項的指定區域的色彩。|
|[CMonthCalCtrl::SetCurrentView](#setcurrentview)|設定目前的月份行事曆控制，以顯示指定的檢視。|
|[CMonthCalCtrl::SetCurSel](#setcursel)|設定月曆控制項的目前選取的日期。|
|[Cmonthcalctrl:: Setdaystate](#setdaystate)|設定月曆控制項中的天數的顯示。|
|[CMonthCalCtrl::SetDecadeView](#setdecadeview)|設定目前的月曆控制項到十年來檢視。|
|[CMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek)|設定要顯示的行事曆的最左邊資料行中的星期幾。|
|[CMonthCalCtrl::SetMaxSelCount](#setmaxselcount)|設定月曆控制項中可選取最大天數。|
|[CMonthCalCtrl::SetMonthDelta](#setmonthdelta)|設定月曆控制項的捲動速率。|
|[CMonthCalCtrl::SetMonthView](#setmonthview)|設定目前的月份行事曆控制，以顯示 [月] 檢視。|
|[CMonthCalCtrl::SetRange](#setrange)|設定最小值和最多允許月曆控制項的日期。|
|[CMonthCalCtrl::SetSelRange](#setselrange)|設定月份行事曆的選取範圍來控制對指定的日期範圍。|
|[CMonthCalCtrl::SetToday](#settoday)|設定目前日期的日曆控制項。|
|[CMonthCalCtrl::SetYearView](#setyearview)|設定目前月份行事曆年度檢視控制項。|
|[CMonthCalCtrl::SizeMinReq](#sizeminreq)|重繪月份行事曆控制項為其最小值、 一個月的大小。|
|[CMonthCalCtrl::SizeRectToMin](#sizerecttomin)|目前月份的行事曆控制項中，會計算最小的矩形可以包含符合指定的矩形中的所有行事曆。|

## <a name="remarks"></a>備註

月曆控制項提供簡單的行事曆介面，使用者可以從中選取一個日期的使用者。 使用者可以變更所顯示：

- 捲動向後和向前，個月的月。

- 按一下目前的文字 （如果不使用 MCS_NOTODAY 樣式） 顯示目前的日期。

- 挑選一個月或年，以從快顯功能表。

您可以自訂每月月曆控制項將各種不同的樣式套用至物件，當您在建立時。 這些樣式所述[月份的行事曆控制項樣式](/windows/desktop/Controls/month-calendar-control-styles)Windows SDK 中。

月曆控制項可以顯示超過一個月，且可以指出特殊天 （例如假日） 的粗體日期。

如需有關使用月曆控制項的詳細資訊，請參閱 <<c0> [ 使用 CMonthCalCtrl](../../mfc/using-cmonthcalctrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CMonthCalCtrl`

## <a name="requirements"></a>需求

**標頭：** afxdtctl.h

##  <a name="cmonthcalctrl"></a>  CMonthCalCtrl::CMonthCalCtrl

建構 `CMonthCalCtrl` 物件。

```
CMonthCalCtrl();
```

### <a name="remarks"></a>備註

您必須呼叫`Create`建構物件之後。

##  <a name="create"></a>  CMonthCalCtrl::Create

建立月曆控制項，並將它附加至`CMonthCalCtrl`物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);

virtual BOOL Create(
    DWORD dwStyle,
    const POINT& pt,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*cheaderctrl:: Create*<br/>
指定套用至月曆控制項的 Windows 樣式的組合。 請參閱[月份的行事曆控制項樣式](/windows/desktop/Controls/month-calendar-control-styles)樣式的詳細資訊的 Windows SDK 中。

*rect*<br/>
參考[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構。 包含月曆控制項的大小與位置。

*太平洋時間*<br/>
參考[點](https://msdn.microsoft.com/library/windows/desktop/dd162805)結構，辨識月曆控制項的位置。

*pParentWnd*<br/>
指標[CWnd](../../mfc/reference/cwnd-class.md)是月曆控制項的父視窗的物件。 它必須不是 NULL。

*nID*<br/>
指定月曆控制項的控制項 id。

### <a name="return-value"></a>傳回值

非零值，如果初始化成功;否則為 0。

### <a name="remarks"></a>備註

建立一個月月曆控制項在兩個步驟：

1. 呼叫[CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)建構`CMonthCalCtrl`物件。

1. 呼叫此成員函式，會建立月曆控制項，並將它附加至`CMonthCalCtrl`物件。

當您呼叫`Create`，常見的控制項都已初始化。 版本`Create`您呼叫可讓您決定其大小的方式：

- 若要讓自動調整大小為一個月的控制項的 MFC，呼叫會覆寫*pt*參數。

- 若要自行調整控制項，呼叫會使用此函式的覆寫*rect*參數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_1.cpp)]

##  <a name="getcalendarborder"></a>  CMonthCalCtrl::GetCalendarBorder

擷取目前的月曆控制項的框線寬度。

```
int GetCalendarBorder() const;
```

### <a name="return-value"></a>傳回值

控制項框線，單位為像素的寬度。

### <a name="remarks"></a>備註

這個方法會傳送[MCM_GETCALENDARBORDER](/windows/desktop/Controls/mcm-getcalendarborder)訊息，Windows SDK 中所述。

##  <a name="getcalendarcount"></a>  CMonthCalCtrl::GetCalendarCount

擷取目前的月份行事曆控制項中顯示的行事曆的數目。

```
int GetCalendarCount() const;
```

### <a name="return-value"></a>傳回值

月曆控制項中目前顯示的行事曆的數目。 行事曆的最大允許的數目是 12。

### <a name="remarks"></a>備註

這個方法會傳送[MCM_GETCALENDARCOUNT](/windows/desktop/Controls/mcm-getcalendarcount)訊息，Windows SDK 中所述。

##  <a name="getcalendargridinfo"></a>  CMonthCalCtrl::GetCalendarGridInfo

擷取目前的月曆控制項的相關資訊。

```
BOOL GetCalendarGridInfo(PMCGRIDINFO pmcGridInfo) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*pmcGridInfo*|[out]指標[MCGRIDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagmcgridinfo)接收目前月份的行事曆控制項的相關資訊的結構。 呼叫端負責配置和初始化此結構。|

### <a name="return-value"></a>傳回值

如果成功，這個方法，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[MCM_GETCALENDARGRIDINFO](/windows/desktop/Controls/mcm-getcalendargridinfo)訊息，Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義變數`m_monthCalCtrl`，也就是用來以程式設計方式存取月曆控制項。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>範例

下列程式碼範例使用`GetCalendarGridInfo`方法來擷取目前的月份行事曆控制項顯示的行事曆日期。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_3.cpp)]

##  <a name="getcalid"></a>  CMonthCalCtrl::GetCalID

擷取目前的月曆控制項的行事曆識別碼。

```
CALID GetCalID() const;
```

### <a name="return-value"></a>傳回值

其中一個[行事曆識別碼](/windows/desktop/Intl/calendar-identifiers)常數。

### <a name="remarks"></a>備註

行事曆識別碼代表特定地區行事曆，例如西曆 （已當地語系化）、 日文或回曆行事曆。 您的應用程式可以使用各種語言支援函式的行事曆識別碼。

這個方法會傳送[MCM_GETCALID](/windows/desktop/Controls/mcm-getcalid)訊息，Windows SDK 中所述。

##  <a name="getcolor"></a>  CMonthCalCtrl::GetColor

每月區域的色彩行事曆的指定控制項的擷取*nRegion*。

```
COLORREF GetColor(int nRegion) const;
```

### <a name="parameters"></a>參數

*nRegion*<br/>
月曆控制項從中擷取色彩區域。 如需值的清單，請參閱 < *nRegion*的參數[SetColor](#setcolor)。

### <a name="return-value"></a>傳回值

A [COLORREF](/windows/desktop/gdi/colorref)值，指定成功的部分月曆控制項，與相關聯的色彩。 否則，此成員函式會傳回-1。

##  <a name="getcurrentview"></a>  CMonthCalCtrl::GetCurrentView

擷取目前顯示月份行事曆控制項的檢視。

```
DWORD GetCurrentView() const;
```

### <a name="return-value"></a>傳回值

目前檢視 由下列值之一：

|值|意義|
|-----------|-------------|
|MCMV_MONTH|每月檢視|
|MCMV_YEAR|每年的檢視|
|MCMV_DECADE|十年來檢視|
|MCMV_CENTURY|世紀檢視|

### <a name="remarks"></a>備註

這個方法會傳送[MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview)訊息，Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義變數`m_monthCalCtrl`，也就是用來以程式設計方式存取月曆控制項。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>範例

下列程式碼範例報表以檢視該月份行事曆控制目前顯示。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_4.cpp)]

##  <a name="getcursel"></a>  CMonthCalCtrl::GetCurSel

擷取系統時間，以在目前選取的日期。

```
BOOL GetCurSel(COleDateTime& refDateTime) const;  BOOL GetCurSel(CTime& refDateTime) const;

BOOL GetCurSel(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>參數

*refDateTime*<br/>
參考[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件或[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件。 接收目前的時間。

*pDateTime*<br/>
指標[SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)會收到將目前選取的日期資訊的結構。 這個參數必須是有效的位址，而且不能是 NULL。

### <a name="return-value"></a>傳回值

如果成功則為非零otherwize 0。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[MCM_GETCURSEL](/windows/desktop/Controls/mcm-getcursel)、 Windows SDK 中所述。

> [!NOTE]
>  如果 style 設 MCS_MULTISELECT，此成員函式將會失敗。

在 MFC 的實作`GetCurSel`，您可以指定`COleDateTime`使用量`CTime`使用量，或`SYSTEMTIME`結構使用方式。

##  <a name="getfirstdayofweek"></a>  CMonthCalCtrl::GetFirstDayOfWeek

取得要顯示的行事曆的最左邊資料行中一週的第一天。

```
int GetFirstDayOfWeek(BOOL* pbLocal = NULL) const;
```

### <a name="parameters"></a>參數

*pbLocal*<br/>
BOOL 值的指標。 如果值為非零，控制項的設定不符合在控制台中的設定。

### <a name="return-value"></a>傳回值

表示一週的第一天的整數值。 請參閱**備註**如需有關這些整數的表示。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[MCM_GETFIRSTDAYOFWEEK](/windows/desktop/Controls/mcm-getfirstdayofweek)、 Windows SDK 中所述。 一周天數會表示為整數，如下所示。

|值|在星期幾|
|-----------|---------------------|
|0|週一|
|1|星期二|
|2|週三|
|3|星期四|
|4|週五|
|5|星期六|
|6|星期日|

### <a name="example"></a>範例

  範例，請參閱[CMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek)。

##  <a name="getmaxselcount"></a>  CMonthCalCtrl::GetMaxSelCount

擷取目前的最大數目的月曆控制項中可選取的天數。

```
int GetMaxSelCount() const;
```

### <a name="return-value"></a>傳回值

整數值，表示控制項可選取天的總數。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[MCM_GETMAXSELCOUNT](/windows/desktop/Controls/mcm-getmaxselcount)、 Windows SDK 中所述。 您可以使用此成員函式讓 MCS_MULTISELECT 設定樣式的控制項。

### <a name="example"></a>範例

  範例，請參閱[CMonthCalCtrl::SetMaxSelCount](#setmaxselcount)。

##  <a name="getmaxtodaywidth"></a>  CMonthCalCtrl::GetMaxTodayWidth

擷取目前的月曆控制項的 「 今天 」 字串的最大寬度。

```
DWORD GetMaxTodayWidth() const;
```

### <a name="return-value"></a>傳回值

「 今天 」 字串中，單位為像素寬度。

### <a name="example"></a>範例

下列程式碼範例會定義變數`m_monthCalCtrl`，也就是用來以程式設計方式存取月曆控制項。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>範例

下列程式碼範例示範`GetMaxTodayWidth`方法。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_5.cpp)]

### <a name="remarks"></a>備註

使用者可以按一下 「 今天 」 字串，在月曆控制項底部顯示傳回目前的日期。 「 今天 」 字串包含標籤文字和日期的文字。

這個方法會傳送[MCM_GETMAXTODAYWIDTH](/windows/desktop/Controls/mcm-getmaxtodaywidth)訊息，Windows SDK 中所述。

##  <a name="getminreqrect"></a>  CMonthCalCtrl::GetMinReqRect

擷取月份行事曆控制項中顯示完整月份所需的最小大小。

```
BOOL GetMinReqRect(RECT* pRect) const;
```

### <a name="parameters"></a>參數

*pRect*<br/>
指標[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構，將會收到週框矩形的資訊。 這個參數必須是有效的位址，而且不能是 NULL。

### <a name="return-value"></a>傳回值

如果成功，此成員函式會傳回非零值和`lpRect`接收適用週框的資訊。 如果不成功，則此成員函式會傳回 0。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[MCM_GETMINREQRECT](/windows/desktop/Controls/mcm-getminreqrect)、 Windows SDK 中所述。

##  <a name="getmonthdelta"></a>  CMonthCalCtrl::GetMonthDelta

擷取月曆控制項的捲動速率。

```
int GetMonthDelta() const;
```

### <a name="return-value"></a>傳回值

月曆控制項的捲動速率。 捲動速率是控制項會在使用者按一下捲軸按鈕一次時，會移動其顯示的月數。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[MCM_GETMONTHDELTA](/windows/desktop/Controls/mcm-getmonthdelta)、 Windows SDK 中所述。

##  <a name="getmonthrange"></a>  CMonthCalCtrl::GetMonthRange

擷取的日期表示月曆控制項的顯示的高低限制的資訊。

```
int GetMonthRange(
    COleDateTime& refMinRange,
    COleDateTime& refMaxRange,
    DWORD dwFlags) const;

int GetMonthRange(
    CTime& refMinRange,
    CTime& refMaxRange,
    DWORD dwFlags) const;

int GetMonthRange(
    LPSYSTEMTIME pMinRange,
    LPSYSTEMTIME pMaxRange,
    DWORD dwFlags) const;
```

### <a name="parameters"></a>參數

*refMinRange*<br/>
參考[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或是[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件，其中包含允許的最小日期。

*refMaxRange*<br/>
參考`COleDateTime`或`CTime`物件，其中包含允許的最大日期。

*pMinRange*<br/>
指標[SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)結構，包含在最低範圍的結束日期。

*pMaxRange*<br/>
指標`SYSTEMTIME`結構，其中包含的日期範圍的最高的結尾。

*dwFlags*<br/>
值，指定要擷取的範圍限制的範圍。 此值必須是下列其中一個項目。

|值|意義|
|-----------|-------------|
|GMR_DAYSTATE|包括前置和後端的可見範圍僅部分顯示的月數。|
|GMR_VISIBLE|包含只在完全顯示的月份。|

### <a name="return-value"></a>傳回值

整數，表示合併兩個限制的範圍，幾個月，由*refMinRange*並*refMaxRange*的第一個和第二個版本中，或*pMinRange*並*pMaxRange*中的第三個版本。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[MCM_GETMONTHRANGE](/windows/desktop/Controls/mcm-getmonthrange)、 Windows SDK 中所述。 在 MFC 的實作`GetMonthRange`，您可以指定`COleDateTime`使用量`CTime`使用量，或`SYSTEMTIME`結構使用方式。

### <a name="example"></a>範例

  範例，請參閱[cmonthcalctrl:: Setdaystate](#setdaystate)。

##  <a name="getrange"></a>  CMonthCalCtrl::GetRange

擷取在月曆控制項中設定的目前最小和最大日期。

```
DWORD GetRange(
    COleDateTime* pMinRange,
    COleDateTime* pMaxRange) const;

DWORD GetRange(
    CTime* pMinRange,
    CTime* pMaxRange) const;

DWORD GetRange(
    LPSYSTEMTIME pMinRange,
    LPSYSTEMTIME pMaxRange) const;
```

### <a name="parameters"></a>參數

*pMinRange*<br/>
指標`COleDateTime`物件，`CTime`物件，或[SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)結構，包含在最低範圍的結束日期。

*pMaxRange*<br/>
指標`COleDateTime`物件，`CTime`物件，或[SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)結構，其中包含的日期範圍的最高的結尾。

### <a name="return-value"></a>傳回值

一個 DWORD，可以是零 （設定無限制） 或指定的限制資訊的下列值的組合。

|值|意義|
|-----------|-------------|
|GDTR_MAX|最大限制是設定的控制項;*pMaxRange*有效，且包含適用於日期資訊。|
|GDTR_MIN|最小限制為控制項;*pMinRange*有效，且包含適用於日期資訊。|

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[MCM_GETRANGE](/windows/desktop/Controls/mcm-getrange)、 Windows SDK 中所述。 在 MFC 的實作`GetRange`，您可以指定`COleDateTime`使用量`CTime`使用量，或`SYSTEMTIME`結構使用方式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_6.cpp)]

##  <a name="getselrange"></a>  CMonthCalCtrl::GetSelRange

擷取表示目前使用者所選取的日期範圍的上限與下限的日期資訊。

```
BOOL GetSelRange(
    COleDateTime& refMinRange,
    COleDateTime& refMaxRange) const;

BOOL GetSelRange(
    CTime& refMinRange,
    CTime& refMaxRange) const;

BOOL GetSelRange(
    LPSYSTEMTIME pMinRange,
    LPSYSTEMTIME pMaxRange) const;
```

### <a name="parameters"></a>參數

*refMinRange*<br/>
參考[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或是[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件，其中包含允許的最小日期。

*refMaxRange*<br/>
參考`COleDateTime`或`CTime`物件，其中包含允許的最大日期。

*pMinRange*<br/>
指標[SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)結構，包含在最低範圍的結束日期。

*pMaxRange*<br/>
指標`SYSTEMTIME`結構，其中包含的日期範圍的最高的結尾。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[MCM_GETSELRANGE](/windows/desktop/Controls/mcm-getselrange)、 Windows SDK 中所述。 `GetSelRange` 如果套用至月曆控制項不會使用 MCS_MULTISELECT 樣式，將會失敗。

在 MFC 的實作`GetSelRange`，您可以指定`COleDateTime`使用量`CTime`使用量，或`SYSTEMTIME`結構使用方式。

##  <a name="gettoday"></a>  CMonthCalCtrl::GetToday

擷取指定為"today"的月曆控制項的日期的日期資訊。

```
BOOL GetToday(COleDateTime& refDateTime) const;  BOOL GetToday(COleDateTime& refDateTime) const;

BOOL GetToday(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>參數

*refDateTime*<br/>
參考[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或是[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件，表示目前的日期。

*pDateTime*<br/>
指標[SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)接收日期資訊的結構。 這個參數必須是有效的位址，而且不能是 NULL。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[MCM_GETTODAY](/windows/desktop/Controls/mcm-gettoday)、 Windows SDK 中所述。 在 MFC 的實作`GetToday`，您可以指定`COleDateTime`使用量`CTime`使用量，或`SYSTEMTIME`結構使用方式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_7.cpp)]

##  <a name="hittest"></a>  CMonthCalCtrl::HitTest

如果有任何項目，是在指定的位置，請判斷哪一個月曆控制項。

```
DWORD HitTest(PMCHITTESTINFO pMCHitTest);
```

### <a name="parameters"></a>參數

*pMCHitTest*<br/>
指標[MCHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-mchittestinfo)的月曆控制項的結構，包含點擊測試點。

### <a name="return-value"></a>傳回值

DWORD 值。 相等**uHit**隸屬`MCHITTESTINFO`結構。

### <a name="remarks"></a>備註

`HitTest` 使用`MCHITTESTINFO`結構，其中包含的點擊測試的相關資訊。

##  <a name="iscenturyview"></a>  CMonthCalCtrl::IsCenturyView

指出目前的月曆控制項的目前檢視是否為世紀檢視。

```
BOOL IsCenturyView() const;
```

### <a name="return-value"></a>傳回值

如果目前的檢視是世紀的檢視;，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview)訊息，Windows SDK 中所述。 如果該訊息傳回 MCMV_CENTURY，這個方法會傳回 TRUE。

##  <a name="isdecadeview"></a>  CMonthCalCtrl::IsDecadeView

指出目前的月曆控制項的目前檢視是否為十年來檢視。

```
BOOL IsDecadeView() const;
```

### <a name="return-value"></a>傳回值

如果目前的檢視是十年來的檢視;，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview)訊息，Windows SDK 中所述。 如果該訊息傳回 MCMV_DECADE，這個方法會傳回 TRUE。

##  <a name="ismonthview"></a>  CMonthCalCtrl::IsMonthView

指出目前的月曆控制項的目前檢視是否為 [月] 檢視。

```
BOOL IsMonthView() const;
```

### <a name="return-value"></a>傳回值

如果目前的檢視是 [月] 檢視中，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview)訊息，Windows SDK 中所述。 如果該訊息傳回 MCMV_MONTH，這個方法會傳回 TRUE。

##  <a name="isyearview"></a>  CMonthCalCtrl::IsYearView

指出目前的月曆控制項的目前檢視是否為 [年] 檢視。

```
BOOL IsYearView() const;
```

### <a name="return-value"></a>傳回值

如果目前的檢視是 [year] 檢視中，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[MCM_GETCURRENTVIEW](/windows/desktop/Controls/mcm-getcurrentview)訊息，Windows SDK 中所述。 如果該訊息傳回 MCMV_YEAR，這個方法會傳回 TRUE。

##  <a name="setcalendarborder"></a>  CMonthCalCtrl::SetCalendarBorder

設定目前的月份行事曆控制項的框線寬度。

```
void SetCalendarBorder(int cxyBorder);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*cxyBorder*|[in]框線寬度，單位為像素。|

### <a name="remarks"></a>備註

如果這個方法成功，若要設定框線寬度*cxyBorder*參數。 否則，框線寬度會重設為目前所指定的預設值[佈景主題](/windows/desktop/Controls/visual-styles-overview)，零，如果不會使用佈景主題。

這個方法會傳送[MCM_SETCALENDARBORDER](/windows/desktop/Controls/mcm-setcalendarborder)訊息，Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義變數`m_monthCalCtrl`，也就是用來以程式設計方式存取月曆控制項。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>範例

下列程式碼範例會設定為八個像素控制的月份行事曆的框線寬度。 使用[CMonthCalCtrl::GetCalendarBorder](#getcalendarborder)方法，以判斷這個方法是否成功。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_8.cpp)]

##  <a name="setcalendarborderdefault"></a>  CMonthCalCtrl::SetCalendarBorderDefault

設定目前的月份行事曆控制項的框線的預設寬度。

```
void SetCalendarBorderDefault();
```

### <a name="remarks"></a>備註

框線寬度設定為指定目前的預設值[佈景主題](/windows/desktop/Controls/visual-styles-overview)，或如果不會使用佈景主題為零。

這個方法會傳送[MCM_SETCALENDARBORDER](/windows/desktop/Controls/mcm-setcalendarborder)訊息，Windows SDK 中所述。

##  <a name="setcalid"></a>  CMonthCalCtrl::SetCalID

設定目前的月曆控制項的行事曆識別碼。

```
BOOL SetCalID(CALID calid);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*calid*|[in]其中一個[行事曆識別碼](/windows/desktop/Intl/calendar-identifiers)常數。|

### <a name="return-value"></a>傳回值

如果成功，這個方法，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

行事曆識別碼指定特定地區行事曆，例如西曆 （已當地語系化）、 日文或回曆行事曆。 使用`SetCalID`方法，以顯示所指定的行事曆*calid*參數，如果您的電腦上安裝包含行事曆的地區設定。

這個方法會傳送[MCM_SETCALID](/windows/desktop/Controls/mcm-setcalid)訊息，Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義變數`m_monthCalCtrl`，也就是用來以程式設計方式存取月曆控制項。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>範例

下列程式碼範例會設定月曆控制項來顯示日文皇帝紀元行事曆。 `SetCalID`方法在您的電腦上已安裝該行事曆時，才會成功。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_9.cpp)]

##  <a name="setcenturyview"></a>  CMonthCalCtrl::SetCenturyView

設定目前的月份行事曆控制，以顯示世紀檢視。

```
BOOL SetCenturyView();
```

### <a name="return-value"></a>傳回值

如果成功，這個方法，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會使用[CMonthCalCtrl::SetCurrentView](#setcurrentview)方法，以檢視設為`MCMV_CENTURY`，代表世紀檢視。

##  <a name="setcolor"></a>  CMonthCalCtrl::SetColor

設定月曆控制項的指定區域的色彩。

```
COLORREF SetColor(
    int nRegion,
    COLORREF ref);
```

### <a name="parameters"></a>參數

*nRegion*<br/>
整數值，指定要設定哪一個月份行事曆色彩。 這個值可以是下列其中一個項目。

|值|意義|
|-----------|-------------|
|MCSC_BACKGROUND|顯示月份間的背景色彩。|
|MCSC_MONTHBK|顯示的背景色彩的當月內。|
|MCSC_TEXT|用來在一個月內顯示的文字色彩。|
|MCSC_TITLEBK|顯示在行事曆的標題背景色彩。|
|MCSC_TITLETEXT|用來顯示行事曆的標題中文字的色彩。|
|MCSC_TRAILINGTEXT|用來顯示標頭和結尾的一天的文字色彩。 標頭和結尾的日期是目前行事曆會出現前面和後面幾個月的天數。|

*ref*<br/>
月曆控制項的指定部分的新色彩設定為 COLORREF 值。

### <a name="return-value"></a>傳回值

COLORREF 值，表示上一個色彩，月曆控制項的指定部分的設定，如果成功。 否則此訊息會傳回-1。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[MCM_SETCOLOR](/windows/desktop/Controls/mcm-setcolor)、 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_10.cpp)]

##  <a name="setcurrentview"></a>  CMonthCalCtrl::SetCurrentView

設定目前的月份行事曆控制，以顯示指定的檢視。

```
BOOL SetCurrentView(DWORD dwNewView);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*dwNewView*|[in]指定每月、 年、 十年或世紀檢視下列值之一。<br /><br /> MCMV_MONTH： 每月檢視<br /><br /> MCMV_YEAR： 年度檢視<br /><br /> MCMV_DECADE： 十年來檢視<br /><br /> MCMV_CENTURY： 世紀檢視|

### <a name="return-value"></a>傳回值

如果成功，這個方法，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[MCM_SETCURRENTVIEW](/windows/desktop/Controls/mcm-setcurrentview)訊息，Windows SDK 中所述。

##  <a name="setcursel"></a>  CMonthCalCtrl::SetCurSel

設定月曆控制項的目前選取的日期。

```
BOOL SetCurSel(const COleDateTime& refDateTime);
BOOL SetCurSel(const CTime& refDateTime);
  BOOL SetCurSel(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>參數

*refDateTime*<br/>
參考[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或是[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件，表示目前選取的月份行事曆控制項。

*pDateTime*<br/>
指標[SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)結構，其中包含要設定為目前的選取範圍的日期。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[MCM_SETCURSEL](/windows/desktop/Controls/mcm-setcursel)、 Windows SDK 中所述。 在 MFC 的實作`SetCurSel`，您可以指定`COleDateTime`使用量`CTime`使用量，或`SYSTEMTIME`結構使用方式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#5](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_11.cpp)]

##  <a name="setdaystate"></a>  Cmonthcalctrl:: Setdaystate

設定月曆控制項中的天數的顯示。

```
BOOL SetDayState(
    int nMonths,
    LPMONTHDAYSTATE pStates);
```

### <a name="parameters"></a>參數

*nMonths*<br/>
值，指出陣列中有多少項目， *pStates*指向。

*pStates*<br/>
指標[MONTHDAYSTATE](/windows/desktop/Controls/monthdaystate)定義如何月曆控制項時，將其顯示在繪製每一天的值陣列。 MONTHDAYSTATE 資料類型是位元欄位，其中每個位元 (1 到 31) 都代表一個月裡一天的狀態。 如果位元是開啟的，則對應的日期會以粗體顯示；否則就不會強調其顯示。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[MCM_SETDAYSTATE](/windows/desktop/Controls/mcm-setdaystate)、 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_12.cpp)]

##  <a name="setdecadeview"></a>  CMonthCalCtrl::SetDecadeView

設定目前的月曆控制項到十年來檢視。

```
BOOL SetDecadeView();
```

### <a name="return-value"></a>傳回值

如果成功，這個方法，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會使用[CMonthCalCtrl::SetCurrentView](#setcurrentview)方法，以檢視設為`MCMV_DECADE`，這代表十年來檢視。

##  <a name="setfirstdayofweek"></a>  CMonthCalCtrl::SetFirstDayOfWeek

設定要顯示的行事曆的最左邊資料行中的星期幾。

```
BOOL SetFirstDayOfWeek(
    int iDay,
    int* lpnOld = NULL);
```

### <a name="parameters"></a>參數

*iDay*<br/>
整數值，表示哪一天是設為一週的第一天。 此值必須是其中一個日期的數字。 請參閱[GetFirstDayOfWeek](#getfirstdayofweek)日數字的說明。

*lpnOld*<br/>
設定整數，表示先前的當週的第一天的指標。

### <a name="return-value"></a>傳回值

如果先前的第一天一週的設定的 LOCALE_IFIRSTDAYOFWEEK 以外的值為非零值，這是控制面板設定中指出的日期。 否則，此函式會傳回 0。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[MCM_SETFIRSTDAYOFWEEK](/windows/desktop/Controls/mcm-setfirstdayofweek)、 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_13.cpp)]

##  <a name="setmaxselcount"></a>  CMonthCalCtrl::SetMaxSelCount

設定月曆控制項中可選取最大天數。

```
BOOL SetMaxSelCount(int nMax);
```

### <a name="parameters"></a>參數

*nMax*<br/>
將會設定為代表最大天數可選取的值。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[MCM_SETMAXSELCOUNT](/windows/desktop/Controls/mcm-setmaxselcount)、 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#8](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_14.cpp)]

##  <a name="setmonthdelta"></a>  CMonthCalCtrl::SetMonthDelta

設定月曆控制項的捲動速率。

```
int SetMonthDelta(int iDelta);
```

### <a name="parameters"></a>參數

*iDelta*<br/>
若要設定為控制項的捲動速率的月數。 如果此值為零，月份差異會重設為預設值，也就是在控制項中顯示的月數。

### <a name="return-value"></a>傳回值

先前的捲動速率。 如果先前尚未設定的捲動速率，則傳回的值為 0。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[MCM_SETMONTHDELTA](/windows/desktop/Controls/mcm-setmonthdelta)、 Windows SDK 中所述。

##  <a name="setmonthview"></a>  CMonthCalCtrl::SetMonthView

設定目前的月份行事曆控制，以顯示 [月] 檢視。

```
BOOL SetMonthView();
```

### <a name="return-value"></a>傳回值

如果成功，這個方法，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會使用[CMonthCalCtrl::SetCurrentView](#setcurrentview)設 MCMV_MONTH，代表 [月] 檢視中檢視的方法。

### <a name="example"></a>範例

下列程式碼範例會定義變數`m_monthCalCtrl`，也就是用來以程式設計方式存取月曆控制項。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>範例

下列程式碼中，設定要顯示月份、 年、 十年和世紀檢視月曆控制項。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_15.cpp)]

##  <a name="setrange"></a>  CMonthCalCtrl::SetRange

設定月曆控制項的最小和最大允許日期。

```
BOOL SetRange(
    const COleDateTime* pMinRange,
    const COleDateTime* pMaxRange);

BOOL SetRange(
    const CTime* pMinRange,
    const CTime* pMaxRange);

BOOL SetRange(
    const LPSYSTEMTIME pMinRange,
    const LPSYSTEMTIME pMaxRange);
```

### <a name="parameters"></a>參數

*pMinRange*<br/>
指標`COleDateTime`物件，`CTime`物件，或[SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)結構，包含在最低範圍的結束日期。

*pMaxRange*<br/>
指標`COleDateTime`物件，`CTime`物件，或`SYSTEMTIME`結構，其中包含的日期範圍的最高的結尾。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[MCM_SETRANGE](/windows/desktop/Controls/mcm-setrange)、 Windows SDK 中所述。 在 MFC 的實作`SetRange`，您可以指定`COleDateTime`使用量`CTime`使用量，或`SYSTEMTIME`結構使用方式。

### <a name="example"></a>範例

  範例，請參閱[CMonthCalCtrl::GetRange](#getrange)。

##  <a name="setselrange"></a>  CMonthCalCtrl::SetSelRange

設定月份行事曆的選取範圍來控制對指定的日期範圍。

```
BOOL SetSelRange(
    const COleDateTime& pMinRange,
    const COleDateTime& pMaxRange);

BOOL SetSelRange(
    const CTime& pMinRange,
    const CTime& pMaxRange);

BOOL SetSelRange(
    const LPSYSTEMTIME pMinRange,
    const LPSYSTEMTIME pMaxRange);
```

### <a name="parameters"></a>參數

*pMinRange*<br/>
指標`COleDateTime`物件，`CTime`物件，或[SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)結構，包含在最低範圍的結束日期。

*pMaxRange*<br/>
指標`COleDateTime`物件，`CTime`物件，或`SYSTEMTIME`結構，其中包含的日期範圍的最高的結尾。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[MCM_SETSELRANGE](/windows/desktop/Controls/mcm-setselrange)、 Windows SDK 中所述。 在 MFC 的實作`SetSelRange`，您可以指定`COleDateTime`使用量`CTime`使用量，或`SYSTEMTIME`結構使用方式。

##  <a name="settoday"></a>  CMonthCalCtrl::SetToday

設定目前日期的日曆控制項。

```
void SetToday(const COleDateTime& refDateTime);
void SetToday(const CTime* pDateTime);
  void SetToday(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>參數

*refDateTime*<br/>
參考[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件，包含目前的日期。

*pDateTime*<br/>
在第二個版本中，指標[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件，包含目前的日期資訊。 在第三個版本中，指標[SYSTEMTIME](https://msdn.microsoft.com/library/windows/desktop/ms724950)結構，包含目前的日期資訊。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[MCM_SETTODAY](/windows/desktop/Controls/mcm-settoday)、 Windows SDK 中所述。

### <a name="example"></a>範例

  範例，請參閱[CMonthCalCtrl::GetToday](#gettoday)。

##  <a name="setyearview"></a>  CMonthCalCtrl::SetYearView

設定目前月份行事曆年度檢視控制項。

```
BOOL SetYearView();
```

### <a name="return-value"></a>傳回值

如果成功，這個方法，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會使用[CMonthCalCtrl::SetCurrentView](#setcurrentview)方法，以檢視設 MCMV_YEAR，表示每年的檢視。

##  <a name="sizeminreq"></a>  CMonthCalCtrl::SizeMinReq

顯示的月份行事曆控制項的最小大小，會顯示一個月。

```
BOOL SizeMinReq(BOOL bRepaint = TRUE);
```

### <a name="parameters"></a>參數

*bRepaint*<br/>
指定是否重新繪製控制項。 根據預設，傳回 TRUE。 如果為 FALSE，未重新繪製，就會發生。

### <a name="return-value"></a>傳回值

月曆控制項調整大小，以其最小值; 如果為非零否則為 0。

### <a name="remarks"></a>備註

呼叫`SizeMinReq`成功的一個月的行事曆顯示一整個月的行事曆控制項。

##  <a name="sizerecttomin"></a>  CMonthCalCtrl::SizeRectToMin

目前月份的行事曆控制項中，會計算最小的矩形可以包含符合指定的矩形中的所有行事曆。

```
LPRECT SizeRectToMin(LPRECT lpRect);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*lpRect*|[in]指標[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構，定義包含行事曆所需的數目的矩形。|

### <a name="return-value"></a>傳回值

指標[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)所定義的結構，定義的矩形，其大小小於或等於矩形*lpRect*參數。

### <a name="remarks"></a>備註

這個方法會計算所指定的矩形內可容納的幾個行事曆*lpRect*參數，然後傳回最小的矩形可以包含該數目的行事曆。 實際上，這個方法會縮小以完全符合所需的行事曆數目指定的矩形。

這個方法會傳送[MCM_SIZERECTTOMIN](/windows/desktop/Controls/mcm-sizerecttomin)訊息，Windows SDK 中所述。

## <a name="see-also"></a>另請參閱

[MFC 範例 CMNCTRL1](../../visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDateTimeCtrl 類別](../../mfc/reference/cdatetimectrl-class.md)
