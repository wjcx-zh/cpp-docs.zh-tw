---
title: CMonthCalCtrl 類別
ms.date: 11/04/2016
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
ms.openlocfilehash: d986aa5f8e232f0ab94858dbdfae5754536ccdb9
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562138"
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
|[CMonthCalCtrl：： CMonthCalCtrl](#cmonthcalctrl)|建構 `CMonthCalCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMonthCalCtrl：： Create](#create)|建立月曆控制項並將其附加至 `CMonthCalCtrl` 物件。|
|[CMonthCalCtrl：： GetCalendarBorder](#getcalendarborder)|抓取當月月曆控制項的框線寬度。|
|[CMonthCalCtrl：： GetCalendarCount](#getcalendarcount)|抓取目前月曆控制項中顯示的行事歷數目。|
|[CMonthCalCtrl：： GetCalendarGridInfo](#getcalendargridinfo)|抓取當月月曆控制項的相關資訊。|
|[CMonthCalCtrl：： GetCalID](#getcalid)|抓取當月月曆控制項的行事曆識別碼。|
|[CMonthCalCtrl：： GetColor](#getcolor)|取得月曆控制項之指定區域的色彩。|
|[CMonthCalCtrl：： GetCurrentView](#getcurrentview)|抓取目前的月曆控制項目前所顯示的視圖。|
|[CMonthCalCtrl：： GetCurSel](#getcursel)|依照目前選取日期的指示，抓取系統時間。|
|[CMonthCalCtrl：： GetFirstDayOfWeek](#getfirstdayofweek)|取得要在行事曆最左邊的資料行中顯示的第一天。|
|[CMonthCalCtrl：： GetMaxSelCount](#getmaxselcount)|抓取月曆控制項中可選取的目前最大天數。|
|[CMonthCalCtrl：： GetMaxTodayWidth](#getmaxtodaywidth)|抓取目前月曆控制項之 "Today" 字串的最大寬度。|
|[CMonthCalCtrl：： GetMinReqRect](#getminreqrect)|抓取在月曆控制項中顯示全月所需的最小大小。|
|[CMonthCalCtrl：： GetMonthDelta](#getmonthdelta)|抓取月曆控制項的滾動速率。|
|[CMonthCalCtrl：： GetMonthRange](#getmonthrange)|抓取表示月曆控制項顯示之最高和最低限制的日期資訊。|
|[CMonthCalCtrl：： GetRange](#getrange)|抓取月曆控制項中目前設定的最小和最大日期。|
|[CMonthCalCtrl：： GetSelRange](#getselrange)|抓取日期資訊，代表使用者目前所選取日期範圍的上限和下限。|
|[CMonthCalCtrl：： GetToday](#gettoday)|針對月曆控制項的日期，抓取指定為 "today" 的日期資訊。|
|[CMonthCalCtrl：： System.windows.media.visualtreehelper.hittest](#hittest)|判斷月曆控制項中的哪一個區段位於螢幕上的指定點。|
|[CMonthCalCtrl：： IsCenturyView](#iscenturyview)|指出目前月曆控制項目前的視圖是否為世紀的觀點。|
|[CMonthCalCtrl：： IsDecadeView](#isdecadeview)|指出目前月曆控制項的目前觀點是否為十年的觀點。|
|[CMonthCalCtrl：： IsMonthView](#ismonthview)|指出目前月曆控制項目前的視圖是否為月份視圖。|
|[CMonthCalCtrl：： IsYearView](#isyearview)|指出目前月曆控制項目前的視圖是否為年份視圖。|
|[CMonthCalCtrl：： SetCalendarBorder](#setcalendarborder)|設定當月月曆控制項的框線寬度。|
|[CMonthCalCtrl：： SetCalendarBorderDefault](#setcalendarborderdefault)|設定當月月曆控制項框線的預設寬度。|
|[CMonthCalCtrl：： SetCalID](#setcalid)|設定當月月曆控制項的行事曆識別碼。|
|[CMonthCalCtrl：： SetCenturyView](#setcenturyview)|設定目前的月曆控制項，以顯示世紀的觀點。|
|[CMonthCalCtrl：： SetColor](#setcolor)|設定月曆控制項之指定區域的色彩。|
|[CMonthCalCtrl：： SetCurrentView](#setcurrentview)|設定目前的月曆控制項，以顯示指定的視圖。|
|[CMonthCalCtrl：： SetCurSel](#setcursel)|針對月曆控制項設定目前選取的日期。|
|[CMonthCalCtrl：： SetDayState](#setdaystate)|設定月曆控制項中的天數顯示。|
|[CMonthCalCtrl：： SetDecadeView](#setdecadeview)|將目前的月曆控制項設定為十年的觀點。|
|[CMonthCalCtrl：： SetFirstDayOfWeek](#setfirstdayofweek)|設定要在行事曆最左邊的資料行中顯示的星期幾。|
|[CMonthCalCtrl：： SetMaxSelCount](#setmaxselcount)|設定可在月曆控制項中選取的最大天數。|
|[CMonthCalCtrl：： SetMonthDelta](#setmonthdelta)|設定月曆控制項的滾動速率。|
|[CMonthCalCtrl：： SetMonthView](#setmonthview)|設定當月月曆控制項，以顯示月份的觀點。|
|[CMonthCalCtrl：： SetRange](#setrange)|設定月曆控制項允許的最小和最大日期。|
|[CMonthCalCtrl：： SetSelRange](#setselrange)|將月曆控制項的選取範圍設定為指定的日期範圍。|
|[CMonthCalCtrl：： SetToday](#settoday)|設定目前日期的行事曆控制項。|
|[CMonthCalCtrl：： SetYearView](#setyearview)|將目前的月曆控制項設定為 year view。|
|[CMonthCalCtrl：： SizeMinReq](#sizeminreq)|將月曆控制項重新繪製為一個月的最小值。|
|[CMonthCalCtrl：： SizeRectToMin](#sizerecttomin)|針對目前的月曆控制項，會計算最小矩形，其中可以包含符合指定矩形的所有行事曆。|

## <a name="remarks"></a>備註

月曆控制項為使用者提供簡單的行事曆介面，讓使用者可以從中選取日期。 使用者可以透過下列方式變更顯示：

- 從 month 到 month 的向前及向後滾動。

- 如果未) MCS_NOTODAY 的樣式，請按一下 [Today] 文字以顯示目前的日期 (。

- 從快顯功能表中挑選一個月或一年。

您可以自訂月曆控制項，方法是在建立時將各種樣式套用至物件。 這些樣式在 Windows SDK 的 [月曆控制項樣式](/windows/win32/Controls/month-calendar-control-styles) 中有描述。

月曆控制項可以顯示多個月，而且可能會指出特殊日子 (例如，將日期加上粗體) 的假日。

如需使用月曆控制項的詳細資訊，請參閱 [使用 CMonthCalCtrl](../../mfc/using-cmonthcalctrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CMonthCalCtrl`

## <a name="requirements"></a>規格需求

**標頭：** afxdtctl。h

## <a name="cmonthcalctrlcmonthcalctrl"></a><a name="cmonthcalctrl"></a> CMonthCalCtrl：： CMonthCalCtrl

建構 `CMonthCalCtrl` 物件。

```
CMonthCalCtrl();
```

### <a name="remarks"></a>備註

您必須在 `Create` 建立物件之後呼叫。

## <a name="cmonthcalctrlcreate"></a><a name="create"></a> CMonthCalCtrl：： Create

建立月曆控制項並將其附加至 `CMonthCalCtrl` 物件。

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

*dwStyle*<br/>
指定套用至月曆控制項的 Windows 樣式組合。 如需樣式的詳細資訊，請參閱 Windows SDK 中的 [月曆控制項樣式](/windows/win32/Controls/month-calendar-control-styles) 。

*矩形*<br/>
[RECT](/windows/win32/api/windef/ns-windef-rect)結構的參考。 包含月曆控制項的位置和大小。

*pt*<br/>
[點](/windows/win32/api/windef/ns-windef-point)結構的參考，該結構會識別月曆控制項的位置。

*pParentWnd*<br/>
[CWnd](../../mfc/reference/cwnd-class.md)物件的指標，該物件是月曆控制項的父視窗。 它不得為 NULL。

*nID*<br/>
指定月曆控制項的控制項識別碼。

### <a name="return-value"></a>傳回值

如果初始化成功，則為非零;否則為0。

### <a name="remarks"></a>備註

以兩個步驟建立月曆控制項：

1. 呼叫 [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) 來建立 `CMonthCalCtrl` 物件。

1. 呼叫此成員函式，此函式會建立月曆控制項並將其附加至 `CMonthCalCtrl` 物件。

當您呼叫時 `Create` ，會初始化通用控制項。 `Create`您呼叫的版本會決定其大小：

- 若要讓 MFC 自動將控制項的大小調整為一個月，請呼叫使用 *pt* 參數的覆寫。

- 若要自行調整控制項的大小，請呼叫此函式使用 *rect* 參數的覆寫。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_1.cpp)]

## <a name="cmonthcalctrlgetcalendarborder"></a><a name="getcalendarborder"></a> CMonthCalCtrl：： GetCalendarBorder

抓取當月月曆控制項的框線寬度。

```
int GetCalendarBorder() const;
```

### <a name="return-value"></a>傳回值

控制項框線的寬度（以圖元為單位）。

### <a name="remarks"></a>備註

這個方法會傳送 [MCM_GETCALENDARBORDER](/windows/win32/Controls/mcm-getcalendarborder) 的訊息，如 Windows SDK 中所述。

## <a name="cmonthcalctrlgetcalendarcount"></a><a name="getcalendarcount"></a> CMonthCalCtrl：： GetCalendarCount

抓取目前月曆控制項中顯示的行事歷數目。

```
int GetCalendarCount() const;
```

### <a name="return-value"></a>傳回值

月曆控制項目前顯示的行事歷數目。 允許的行事歷數目上限為12。

### <a name="remarks"></a>備註

這個方法會傳送 [MCM_GETCALENDARCOUNT](/windows/win32/Controls/mcm-getcalendarcount) 的訊息，如 Windows SDK 中所述。

## <a name="cmonthcalctrlgetcalendargridinfo"></a><a name="getcalendargridinfo"></a> CMonthCalCtrl：： GetCalendarGridInfo

抓取當月月曆控制項的相關資訊。

```
BOOL GetCalendarGridInfo(PMCGRIDINFO pmcGridInfo) const;
```

### <a name="parameters"></a>參數

*pmcGridInfo*\
擴展 [MCGRIDINFO](/windows/win32/api/commctrl/ns-commctrl-mcgridinfo) 結構的指標，此結構會接收當月月曆控制項的相關資訊。 呼叫端負責配置和初始化此結構。

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送 [MCM_GETCALENDARGRIDINFO](/windows/win32/Controls/mcm-getcalendargridinfo) 的訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例 `m_monthCalCtrl` 會定義用來以程式設計方式存取月曆控制項的變數。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>範例

下列程式碼範例會使用 `GetCalendarGridInfo` 方法，以取得目前月曆控制項顯示的行事曆日期。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_3.cpp)]

## <a name="cmonthcalctrlgetcalid"></a><a name="getcalid"></a> CMonthCalCtrl：： GetCalID

抓取當月月曆控制項的行事曆識別碼。

```
CALID GetCalID() const;
```

### <a name="return-value"></a>傳回值

其中一個行事 [曆識別碼](/windows/win32/Intl/calendar-identifiers) 常數。

### <a name="remarks"></a>備註

行事曆識別碼代表特定區域的行事曆，例如西曆 (當地語系化的) 、日文或 Hijri 日曆。 您的應用程式可以使用具有多種語言支援功能的行事曆識別碼。

這個方法會傳送 [MCM_GETCALID](/windows/win32/Controls/mcm-getcalid) 的訊息，如 Windows SDK 中所述。

## <a name="cmonthcalctrlgetcolor"></a><a name="getcolor"></a> CMonthCalCtrl：： GetColor

抓取 *nRegion*所指定月曆控制項區域的色彩。

```
COLORREF GetColor(int nRegion) const;
```

### <a name="parameters"></a>參數

*nRegion*<br/>
從中取出色彩的月曆控制項的區域。 如需值的清單，請參閱[SetColor](#setcolor)的*nRegion*參數。

### <a name="return-value"></a>傳回值

[COLORREF](/windows/win32/gdi/colorref)值，指定與月曆控制項的部分相關聯的色彩（如果成功的話）。 否則，此成員函式會傳回-1。

## <a name="cmonthcalctrlgetcurrentview"></a><a name="getcurrentview"></a> CMonthCalCtrl：： GetCurrentView

抓取目前的月曆控制項目前所顯示的視圖。

```
DWORD GetCurrentView() const;
```

### <a name="return-value"></a>傳回值

目前的視圖，以下列其中一個值表示：

|值|意義|
|-----------|-------------|
|MCMV_MONTH|每月檢視|
|MCMV_YEAR|年度觀點|
|MCMV_DECADE|十年的觀點|
|MCMV_CENTURY|世紀視圖|

### <a name="remarks"></a>備註

這個方法會傳送 [MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview) 的訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例 `m_monthCalCtrl` 會定義用來以程式設計方式存取月曆控制項的變數。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>範例

下列程式碼範例會報告目前顯示月曆控制項的觀點。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_4.cpp)]

## <a name="cmonthcalctrlgetcursel"></a><a name="getcursel"></a> CMonthCalCtrl：： GetCurSel

依照目前選取日期的指示，抓取系統時間。

```
BOOL GetCurSel(COleDateTime& refDateTime) const;  BOOL GetCurSel(CTime& refDateTime) const;

BOOL GetCurSel(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>參數

*refDateTime*<br/>
[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件或[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的參考。 接收目前的時間。

*pDateTime*<br/>
[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標，此結構會接收目前選取的日期資訊。 此參數必須是有效的位址，而且不可以是 Null。

### <a name="return-value"></a>傳回值

如果成功，則為非零;otherwize 0。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [MCM_GETCURSEL](/windows/win32/Controls/mcm-getcursel)的行為。

> [!NOTE]
> 如果設定了樣式 MCS_MULTISELECT，此成員函式會失敗。

在 MFC 的執行中 `GetCurSel` ，您可以指定 `COleDateTime` 使用方式、 `CTime` 使用方式或 `SYSTEMTIME` 結構使用方式。

## <a name="cmonthcalctrlgetfirstdayofweek"></a><a name="getfirstdayofweek"></a> CMonthCalCtrl：： GetFirstDayOfWeek

取得要在行事曆最左邊的資料行中顯示的第一天。

```
int GetFirstDayOfWeek(BOOL* pbLocal = NULL) const;
```

### <a name="parameters"></a>參數

*pbLocal*<br/>
BOOL 值的指標。 如果此值不是零，則控制項的設定與 [控制台] 中的設定不相符。

### <a name="return-value"></a>傳回值

代表一周第一天的整數值。 如需這些整數所代表之意義的詳細資訊，請參閱 **備註** 。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [MCM_GETFIRSTDAYOFWEEK](/windows/win32/Controls/mcm-getfirstdayofweek)的行為。 一周中的天數會以整數表示，如下所示。

|值|星期幾|
|-----------|---------------------|
|0|星期一|
|1|Tuesday|
|2|星期三|
|3|Thursday|
|4|星期五|
|5|星期六|
|6|星期日|

### <a name="example"></a>範例

  請參閱 [CMonthCalCtrl：： SetFirstDayOfWeek](#setfirstdayofweek)的範例。

## <a name="cmonthcalctrlgetmaxselcount"></a><a name="getmaxselcount"></a> CMonthCalCtrl：： GetMaxSelCount

抓取月曆控制項中可選取的目前最大天數。

```
int GetMaxSelCount() const;
```

### <a name="return-value"></a>傳回值

整數值，代表可以為控制項選取的總天數。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [MCM_GETMAXSELCOUNT](/windows/win32/Controls/mcm-getmaxselcount)的行為。 針對 MCS_MULTISELECT 樣式集的控制項，請使用這個成員函式。

### <a name="example"></a>範例

  請參閱 [CMonthCalCtrl：： SetMaxSelCount](#setmaxselcount)的範例。

## <a name="cmonthcalctrlgetmaxtodaywidth"></a><a name="getmaxtodaywidth"></a> CMonthCalCtrl：： GetMaxTodayWidth

抓取目前月曆控制項之 "Today" 字串的最大寬度。

```
DWORD GetMaxTodayWidth() const;
```

### <a name="return-value"></a>傳回值

"Today" 字串的寬度（以圖元為單位）。

### <a name="example"></a>範例

下列程式碼範例 `m_monthCalCtrl` 會定義用來以程式設計方式存取月曆控制項的變數。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>範例

下列程式碼範例會示範 `GetMaxTodayWidth` 方法。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_5.cpp)]

### <a name="remarks"></a>備註

使用者可以藉由按一下 [Today] 字串（顯示在月曆控制項的底部）來返回目前的日期。 "Today" 字串包含標籤文字和日期文字。

這個方法會傳送 [MCM_GETMAXTODAYWIDTH](/windows/win32/Controls/mcm-getmaxtodaywidth) 的訊息，如 Windows SDK 中所述。

## <a name="cmonthcalctrlgetminreqrect"></a><a name="getminreqrect"></a> CMonthCalCtrl：： GetMinReqRect

抓取在月曆控制項中顯示全月所需的最小大小。

```
BOOL GetMinReqRect(RECT* pRect) const;
```

### <a name="parameters"></a>參數

*pRect*<br/>
[矩形](/windows/win32/api/windef/ns-windef-rect)結構的指標，此結構會接收周框的資訊。 此參數必須是有效的位址，而且不可以是 Null。

### <a name="return-value"></a>傳回值

如果成功，此成員函式會傳回非零值，並 `lpRect` 接收適用的界限資訊。 如果不成功，則成員函式會傳回0。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [MCM_GETMINREQRECT](/windows/win32/Controls/mcm-getminreqrect)的行為。

## <a name="cmonthcalctrlgetmonthdelta"></a><a name="getmonthdelta"></a> CMonthCalCtrl：： GetMonthDelta

抓取月曆控制項的滾動速率。

```
int GetMonthDelta() const;
```

### <a name="return-value"></a>傳回值

月曆控制項的滾動速率。 捲軸速率是當使用者按下滾動按鈕一次時，控制項移動其顯示的月數。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [MCM_GETMONTHDELTA](/windows/win32/Controls/mcm-getmonthdelta)的行為。

## <a name="cmonthcalctrlgetmonthrange"></a><a name="getmonthrange"></a> CMonthCalCtrl：： GetMonthRange

抓取表示月曆控制項顯示之最高和最低限制的日期資訊。

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
[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的參考，其中包含所允許的最小日期。

*refMaxRange*<br/>
或物件的參考 `COleDateTime` ， `CTime` 其中包含允許的最大日期。

*pMinRange*<br/>
[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標，其中包含範圍最小結尾的日期。

*pMaxRange*<br/>
結構的指標，該 `SYSTEMTIME` 結構包含範圍最高結尾的日期。

*dwFlags*<br/>
值，指定要抓取範圍限制的範圍。 此值必須是下列其中一項。

|值|意義|
|-----------|-------------|
|GMR_DAYSTATE|包含只部分顯示之可見範圍的前置和尾端月份。|
|GMR_VISIBLE|只包含完全顯示的月份。|

### <a name="return-value"></a>傳回值

整數，表示在第一個和第二個版本中， *refMinRange* 和 *refMaxRange* 所指出的兩個限制（以月為單位），或第三個版本中的 *pMinRange* 和 *pMaxRange* 。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [MCM_GETMONTHRANGE](/windows/win32/Controls/mcm-getmonthrange)的行為。 在 MFC 的執行中 `GetMonthRange` ，您可以指定 `COleDateTime` 使用方式、 `CTime` 使用方式或 `SYSTEMTIME` 結構使用方式。

### <a name="example"></a>範例

  請參閱 [CMonthCalCtrl：： SetDayState](#setdaystate)的範例。

## <a name="cmonthcalctrlgetrange"></a><a name="getrange"></a> CMonthCalCtrl：： GetRange

抓取月曆控制項中目前設定的最小和最大日期。

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
`COleDateTime`物件、 `CTime` 物件或[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標，該結構包含範圍最低結尾的日期。

*pMaxRange*<br/>
`COleDateTime`物件、 `CTime` 物件或[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標，其中包含範圍最高結尾的日期。

### <a name="return-value"></a>傳回值

DWORD 可以是零 (沒有設定任何限制) 或下列值的組合，這些值會指定限制資訊。

|值|意義|
|-----------|-------------|
|GDTR_MAX|為控制項設定了上限， *pMaxRange* 有效，且包含適用的日期資訊。|
|GDTR_MIN|針對控制項設定的最小限制為; *pMinRange* 有效，且包含適用的日期資訊。|

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [MCM_GETRANGE](/windows/win32/Controls/mcm-getrange)的行為。 在 MFC 的執行中 `GetRange` ，您可以指定 `COleDateTime` 使用方式、 `CTime` 使用方式或 `SYSTEMTIME` 結構使用方式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_6.cpp)]

## <a name="cmonthcalctrlgetselrange"></a><a name="getselrange"></a> CMonthCalCtrl：： GetSelRange

抓取日期資訊，代表使用者目前所選取日期範圍的上限和下限。

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
[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的參考，其中包含所允許的最小日期。

*refMaxRange*<br/>
或物件的參考 `COleDateTime` ， `CTime` 其中包含允許的最大日期。

*pMinRange*<br/>
[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標，其中包含範圍最小結尾的日期。

*pMaxRange*<br/>
結構的指標，該 `SYSTEMTIME` 結構包含範圍最高結尾的日期。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [MCM_GETSELRANGE](/windows/win32/Controls/mcm-getselrange)的行為。 `GetSelRange` 如果套用至不使用 MCS_MULTISELECT 樣式的月曆控制項，將會失敗。

在 MFC 的執行中 `GetSelRange` ，您可以指定 `COleDateTime` 使用方式、 `CTime` 使用方式或 `SYSTEMTIME` 結構使用方式。

## <a name="cmonthcalctrlgettoday"></a><a name="gettoday"></a> CMonthCalCtrl：： GetToday

針對月曆控制項的日期，抓取指定為 "today" 的日期資訊。

```
BOOL GetToday(COleDateTime& refDateTime) const;  BOOL GetToday(COleDateTime& refDateTime) const;

BOOL GetToday(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>參數

*refDateTime*<br/>
[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的參考，指出目前的日期。

*pDateTime*<br/>
[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標，此結構會接收日期資訊。 此參數必須是有效的位址，而且不可以是 Null。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [MCM_GETTODAY](/windows/win32/Controls/mcm-gettoday)的行為。 在 MFC 的執行中 `GetToday` ，您可以指定 `COleDateTime` 使用方式、 `CTime` 使用方式或 `SYSTEMTIME` 結構使用方式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_7.cpp)]

## <a name="cmonthcalctrlhittest"></a><a name="hittest"></a> CMonthCalCtrl：： System.windows.media.visualtreehelper.hittest

判斷月曆控制項（如果有的話）位於指定的位置。

```
DWORD HitTest(PMCHITTESTINFO pMCHitTest);
```

### <a name="parameters"></a>參數

*pMCHitTest*<br/>
[MCHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-mchittestinfo)結構的指標，其中包含月曆控制項的點擊測試點。

### <a name="return-value"></a>傳回值

DWORD 值。 等於結構的 **uHit** 成員 `MCHITTESTINFO` 。

### <a name="remarks"></a>備註

`HitTest` 使用 `MCHITTESTINFO` 結構，其中包含點擊測試的相關資訊。

## <a name="cmonthcalctrliscenturyview"></a><a name="iscenturyview"></a> CMonthCalCtrl：： IsCenturyView

指出目前月曆控制項目前的視圖是否為世紀的觀點。

```
BOOL IsCenturyView() const;
```

### <a name="return-value"></a>傳回值

如果目前 view 為世紀視圖，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送 [MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview) 的訊息，如 Windows SDK 中所述。 如果該訊息傳回 MCMV_CENTURY，這個方法會傳回 TRUE。

## <a name="cmonthcalctrlisdecadeview"></a><a name="isdecadeview"></a> CMonthCalCtrl：： IsDecadeView

指出目前月曆控制項的目前觀點是否為十年的觀點。

```
BOOL IsDecadeView() const;
```

### <a name="return-value"></a>傳回值

如果目前的視圖是十年的視圖，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送 [MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview) 的訊息，如 Windows SDK 中所述。 如果該訊息傳回 MCMV_DECADE，這個方法會傳回 TRUE。

## <a name="cmonthcalctrlismonthview"></a><a name="ismonthview"></a> CMonthCalCtrl：： IsMonthView

指出目前月曆控制項目前的視圖是否為月份視圖。

```
BOOL IsMonthView() const;
```

### <a name="return-value"></a>傳回值

如果目前的視圖是月份視圖，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送 [MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview) 的訊息，如 Windows SDK 中所述。 如果該訊息傳回 MCMV_MONTH，這個方法會傳回 TRUE。

## <a name="cmonthcalctrlisyearview"></a><a name="isyearview"></a> CMonthCalCtrl：： IsYearView

指出目前月曆控制項目前的視圖是否為年份視圖。

```
BOOL IsYearView() const;
```

### <a name="return-value"></a>傳回值

如果目前 view 為 year 視圖，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送 [MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview) 的訊息，如 Windows SDK 中所述。 如果該訊息傳回 MCMV_YEAR，這個方法會傳回 TRUE。

## <a name="cmonthcalctrlsetcalendarborder"></a><a name="setcalendarborder"></a> CMonthCalCtrl：： SetCalendarBorder

設定當月月曆控制項的框線寬度。

```cpp
void SetCalendarBorder(int cxyBorder);
```

### <a name="parameters"></a>參數

*cxyBorder*\
在框線的寬度（以圖元為單位）。

### <a name="remarks"></a>備註

如果此方法成功，則框線寬度會設定為 *cxyBorder* 參數。 否則，框線寬度會重設為目前 [主題](/windows/win32/Controls/visual-styles-overview)所指定的預設值，如果未使用主題則為零。

這個方法會傳送 [MCM_SETCALENDARBORDER](/windows/win32/Controls/mcm-setcalendarborder) 的訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例 `m_monthCalCtrl` 會定義用來以程式設計方式存取月曆控制項的變數。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>範例

下列程式碼範例會將月曆控制項的框線寬度設定為8圖元。 您可以使用 [CMonthCalCtrl：： GetCalendarBorder](#getcalendarborder) 方法來判斷這個方法是否成功。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_8.cpp)]

## <a name="cmonthcalctrlsetcalendarborderdefault"></a><a name="setcalendarborderdefault"></a> CMonthCalCtrl：： SetCalendarBorderDefault

設定當月月曆控制項框線的預設寬度。

```cpp
void SetCalendarBorderDefault();
```

### <a name="remarks"></a>備註

框線寬度設定為目前 [主題](/windows/win32/Controls/visual-styles-overview)所指定的預設值，如果未使用主題則為零。

這個方法會傳送 [MCM_SETCALENDARBORDER](/windows/win32/Controls/mcm-setcalendarborder) 的訊息，如 Windows SDK 中所述。

## <a name="cmonthcalctrlsetcalid"></a><a name="setcalid"></a> CMonthCalCtrl：： SetCalID

設定當月月曆控制項的行事曆識別碼。

```
BOOL SetCalID(CALID calid);
```

### <a name="parameters"></a>參數

*calid*\
在其中一個行事 [曆識別碼](/windows/win32/Intl/calendar-identifiers) 常數。

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

行事曆識別碼會指定特定區域的行事曆，例如西曆 (當地語系化的) 、日文或 Hijri 日曆。 `SetCalID`如果您的電腦上已安裝包含行事曆的地區設定，請使用方法來顯示*calid*參數所指定的行事曆。

這個方法會傳送 [MCM_SETCALID](/windows/win32/Controls/mcm-setcalid) 的訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例 `m_monthCalCtrl` 會定義用來以程式設計方式存取月曆控制項的變數。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>範例

下列程式碼範例會設定月曆控制項，以顯示日文天皇紀元行事曆。 `SetCalID`只有當您的電腦上已安裝該行事歷時，此方法才會成功。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_9.cpp)]

## <a name="cmonthcalctrlsetcenturyview"></a><a name="setcenturyview"></a> CMonthCalCtrl：： SetCenturyView

設定目前的月曆控制項，以顯示世紀的觀點。

```
BOOL SetCenturyView();
```

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會使用 [CMonthCalCtrl：： SetCurrentView](#setcurrentview) 方法將 view 設定為 `MCMV_CENTURY` ，其代表世紀的觀點。

## <a name="cmonthcalctrlsetcolor"></a><a name="setcolor"></a> CMonthCalCtrl：： SetColor

設定月曆控制項之指定區域的色彩。

```
COLORREF SetColor(
    int nRegion,
    COLORREF ref);
```

### <a name="parameters"></a>參數

*nRegion*<br/>
整數值，指定要設定的月曆色彩。 這個值可以是下列其中一項。

|值|意義|
|-----------|-------------|
|MCSC_BACKGROUND|在月份之間顯示的背景色彩。|
|MCSC_MONTHBK|月份內顯示的背景色彩。|
|MCSC_TEXT|用來顯示一個月內文字的色彩。|
|MCSC_TITLEBK|行事曆標題中顯示的背景色彩。|
|MCSC_TITLETEXT|用來顯示行事曆標題內文字的色彩。|
|MCSC_TRAILINGTEXT|用來顯示頁首和尾端日文字的色彩。 標頭和後端天是顯示在目前行事曆上的上個月和之後幾天。|

*裁判*<br/>
月曆控制項之指定部分的新色彩設定的 COLORRE光圈值。

### <a name="return-value"></a>傳回值

COLORRE光圈值，代表月曆控制項之指定部分的先前色彩設定（如果成功）。 否則，此訊息會傳回-1。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [MCM_SETCOLOR](/windows/win32/Controls/mcm-setcolor)的行為。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_10.cpp)]

## <a name="cmonthcalctrlsetcurrentview"></a><a name="setcurrentview"></a> CMonthCalCtrl：： SetCurrentView

設定目前的月曆控制項，以顯示指定的視圖。

```
BOOL SetCurrentView(DWORD dwNewView);
```

### <a name="parameters"></a>參數

*dwNewView*\
在下列其中一個值，指定每月、每年、十年或世紀的觀點。

- `MCMV_MONTH`：每月檢視
- `MCMV_YEAR`：年度視圖
- `MCMV_DECADE`：十年的觀點
- `MCMV_CENTURY`：世紀視圖

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送 [MCM_SETCURRENTVIEW](/windows/win32/Controls/mcm-setcurrentview) 的訊息，如 Windows SDK 中所述。

## <a name="cmonthcalctrlsetcursel"></a><a name="setcursel"></a> CMonthCalCtrl：： SetCurSel

針對月曆控制項設定目前選取的日期。

```
BOOL SetCurSel(const COleDateTime& refDateTime);
BOOL SetCurSel(const CTime& refDateTime);
BOOL SetCurSel(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>參數

*refDateTime*<br/>
[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的參考，指出目前選取的月曆控制項。

*pDateTime*<br/>
[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標，其中包含要設定為目前選取範圍的日期。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [MCM_SETCURSEL](/windows/win32/Controls/mcm-setcursel)的行為。 在 MFC 的執行中 `SetCurSel` ，您可以指定 `COleDateTime` 使用方式、 `CTime` 使用方式或 `SYSTEMTIME` 結構使用方式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#5](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_11.cpp)]

## <a name="cmonthcalctrlsetdaystate"></a><a name="setdaystate"></a> CMonthCalCtrl：： SetDayState

設定月曆控制項中的天數顯示。

```
BOOL SetDayState(
    int nMonths,
    LPMONTHDAYSTATE pStates);
```

### <a name="parameters"></a>參數

*nMonths*<br/>
值，指出 *pStates* 所指向陣列中的元素數目。

*pStates*<br/>
[MONTHDAYSTATE](/windows/win32/Controls/monthdaystate)值陣列的指標，定義月曆控制項在其顯示中的每一天將如何繪製。 MONTHDAYSTATE 資料類型是位欄位，其中每個位 (1 到 31) 代表一個月中某一天的狀態。 如果位元是開啟的，則對應的日期會以粗體顯示；否則就不會強調其顯示。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [MCM_SETDAYSTATE](/windows/win32/Controls/mcm-setdaystate)的行為。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_12.cpp)]

## <a name="cmonthcalctrlsetdecadeview"></a><a name="setdecadeview"></a> CMonthCalCtrl：： SetDecadeView

將目前的月曆控制項設定為十年的觀點。

```
BOOL SetDecadeView();
```

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會使用 [CMonthCalCtrl：： SetCurrentView](#setcurrentview) 方法將 view 設定為 `MCMV_DECADE` ，其代表十年的觀點。

## <a name="cmonthcalctrlsetfirstdayofweek"></a><a name="setfirstdayofweek"></a> CMonthCalCtrl：： SetFirstDayOfWeek

設定要在行事曆最左邊的資料行中顯示的星期幾。

```
BOOL SetFirstDayOfWeek(
    int iDay,
    int* lpnOld = NULL);
```

### <a name="parameters"></a>參數

*iDay*<br/>
整數值，表示要將哪一天設定為星期幾的第一天。 此值必須是一天的數位。 如需日數位的描述，請參閱 [GetFirstDayOfWeek](#getfirstdayofweek) 。

*lpnOld*<br/>
整數的指標，指出先前設定之周的第一天。

### <a name="return-value"></a>傳回值

如果在第一周的第一天設定為 LOCALE_IFIRSTDAYOFWEEK 以外的值，則為非零值，也就是在 [控制台] 設定中指出的日期。 否則，此函式會傳回0。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [MCM_SETFIRSTDAYOFWEEK](/windows/win32/Controls/mcm-setfirstdayofweek)的行為。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_13.cpp)]

## <a name="cmonthcalctrlsetmaxselcount"></a><a name="setmaxselcount"></a> CMonthCalCtrl：： SetMaxSelCount

設定可在月曆控制項中選取的最大天數。

```
BOOL SetMaxSelCount(int nMax);
```

### <a name="parameters"></a>參數

*N 上限*<br/>
值，這個值會設定為代表可選取之天數的最大數目。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [MCM_SETMAXSELCOUNT](/windows/win32/Controls/mcm-setmaxselcount)的行為。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#8](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_14.cpp)]

## <a name="cmonthcalctrlsetmonthdelta"></a><a name="setmonthdelta"></a> CMonthCalCtrl：： SetMonthDelta

設定月曆控制項的滾動速率。

```
int SetMonthDelta(int iDelta);
```

### <a name="parameters"></a>參數

*iDelta*<br/>
要設定為控制項滾動速率的月數。 如果此值為零，則會將月份差異重設為預設值，也就是顯示在控制項中的月份數。

### <a name="return-value"></a>傳回值

上一個滾動速率。 如果之前未設定捲軸率，則傳回值為0。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [MCM_SETMONTHDELTA](/windows/win32/Controls/mcm-setmonthdelta)的行為。

## <a name="cmonthcalctrlsetmonthview"></a><a name="setmonthview"></a> CMonthCalCtrl：： SetMonthView

設定當月月曆控制項，以顯示月份的觀點。

```
BOOL SetMonthView();
```

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會使用 [CMonthCalCtrl：： SetCurrentView](#setcurrentview) 方法，將 view 設定為 MCMV_MONTH，這代表月份的觀點。

### <a name="example"></a>範例

下列程式碼範例 `m_monthCalCtrl` 會定義用來以程式設計方式存取月曆控制項的變數。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>範例

下列程式碼範例會設定月曆控制項來顯示 month、year、十和世紀的觀點。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_15.cpp)]

## <a name="cmonthcalctrlsetrange"></a><a name="setrange"></a> CMonthCalCtrl：： SetRange

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
`COleDateTime`物件、 `CTime` 物件或[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標，該結構包含範圍最低結尾的日期。

*pMaxRange*<br/>
`COleDateTime`物件、物件或結構的指標，該物件 `CTime` `SYSTEMTIME` 包含範圍最高結尾的日期。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [MCM_SETRANGE](/windows/win32/Controls/mcm-setrange)的行為。 在 MFC 的執行中 `SetRange` ，您可以指定 `COleDateTime` 使用方式、 `CTime` 使用方式或 `SYSTEMTIME` 結構使用方式。

### <a name="example"></a>範例

  請參閱 [CMonthCalCtrl：： GetRange](#getrange)的範例。

## <a name="cmonthcalctrlsetselrange"></a><a name="setselrange"></a> CMonthCalCtrl：： SetSelRange

將月曆控制項的選取範圍設定為指定的日期範圍。

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
`COleDateTime`物件、 `CTime` 物件或[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標，該結構包含範圍最低結尾的日期。

*pMaxRange*<br/>
`COleDateTime`物件、物件或結構的指標，該物件 `CTime` `SYSTEMTIME` 包含範圍最高結尾的日期。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [MCM_SETSELRANGE](/windows/win32/Controls/mcm-setselrange)的行為。 在 MFC 的執行中 `SetSelRange` ，您可以指定 `COleDateTime` 使用方式、 `CTime` 使用方式或 `SYSTEMTIME` 結構使用方式。

## <a name="cmonthcalctrlsettoday"></a><a name="settoday"></a> CMonthCalCtrl：： SetToday

設定目前日期的行事曆控制項。

```cpp
void SetToday(const COleDateTime& refDateTime);
void SetToday(const CTime* pDateTime);
void SetToday(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>參數

*refDateTime*<br/>
[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件的參考，其中包含目前的日期。

*pDateTime*<br/>
在第二個版本中，包含目前日期資訊的 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 物件指標。 在第三個版本中，是 [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) 結構的指標，其中包含目前的日期資訊。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [MCM_SETTODAY](/windows/win32/Controls/mcm-settoday)的行為。

### <a name="example"></a>範例

  請參閱 [CMonthCalCtrl：： GetToday](#gettoday)的範例。

## <a name="cmonthcalctrlsetyearview"></a><a name="setyearview"></a> CMonthCalCtrl：： SetYearView

將目前的月曆控制項設定為 year view。

```
BOOL SetYearView();
```

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會使用 [CMonthCalCtrl：： SetCurrentView](#setcurrentview) 方法，將 view 設定為 MCMV_YEAR，這代表年度的觀點。

## <a name="cmonthcalctrlsizeminreq"></a><a name="sizeminreq"></a> CMonthCalCtrl：： SizeMinReq

將月曆控制項顯示為顯示一個月的最小大小。

```
BOOL SizeMinReq(BOOL bRepaint = TRUE);
```

### <a name="parameters"></a>參數

*bRepaint*<br/>
指定是否要重新繪製控制項。 預設為 TRUE。 如果為 FALSE，則不會發生重新繪製。

### <a name="return-value"></a>傳回值

如果月曆控制項的大小調整為最小值，則為非零。否則為0。

### <a name="remarks"></a>備註

成功呼叫會 `SizeMinReq` 顯示一個月行事曆的整個月曆控制項。

## <a name="cmonthcalctrlsizerecttomin"></a><a name="sizerecttomin"></a> CMonthCalCtrl：： SizeRectToMin

針對目前的月曆控制項，會計算最小矩形，其中可以包含符合指定矩形的所有行事曆。

```
LPRECT SizeRectToMin(LPRECT lpRect);
```

### <a name="parameters"></a>參數

*lpRect*\
在 [矩形結構的](/windows/win32/api/windef/ns-windef-rect) 指標，該結構定義包含所需行事歷數目的矩形。

### <a name="return-value"></a>傳回值

[矩形結構的](/windows/win32/api/windef/ns-windef-rect)指標，該結構定義其大小小於或等於*lpRect*參數所定義之矩形的矩形。

### <a name="remarks"></a>備註

這個方法會計算 *lpRect* 參數所指定的矩形中可以容納多少行事曆，然後傳回可包含該行事歷數目的最小矩形。 實際上，這個方法會縮小指定的矩形，使其完全符合所需的行事歷數目。

這個方法會傳送 [MCM_SIZERECTTOMIN](/windows/win32/Controls/mcm-sizerecttomin) 的訊息，如 Windows SDK 中所述。

## <a name="see-also"></a>另請參閱

[MFC 範例 CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDateTimeCtrl 類別](../../mfc/reference/cdatetimectrl-class.md)
