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
ms.openlocfilehash: 963aecfed4f6eb67a0ab227df06fce98c0778f7f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504552"
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
|[CMonthCalCtrl::Create](#create)|建立月曆控制項並將其附加至`CMonthCalCtrl`物件。|
|[CMonthCalCtrl::GetCalendarBorder](#getcalendarborder)|抓取目前月曆控制項的框線寬度。|
|[CMonthCalCtrl::GetCalendarCount](#getcalendarcount)|抓取目前月曆控制項中顯示的行事歷數目。|
|[CMonthCalCtrl::GetCalendarGridInfo](#getcalendargridinfo)|抓取目前月曆控制項的相關資訊。|
|[CMonthCalCtrl::GetCalID](#getcalid)|抓取目前月曆控制項的行事曆識別碼。|
|[CMonthCalCtrl::GetColor](#getcolor)|取得月曆控制項中指定區域的色彩。|
|[CMonthCalCtrl::GetCurrentView](#getcurrentview)|抓取目前月曆控制項目前顯示的視圖。|
|[CMonthCalCtrl::GetCurSel](#getcursel)|依照目前所選日期的指示, 抓取系統時間。|
|[CMonthCalCtrl::GetFirstDayOfWeek](#getfirstdayofweek)|取得要在行事曆最左邊的資料行中顯示的第一天。|
|[CMonthCalCtrl::GetMaxSelCount](#getmaxselcount)|抓取月曆控制項中可選取的目前最大天數。|
|[CMonthCalCtrl::GetMaxTodayWidth](#getmaxtodaywidth)|抓取目前月曆控制項之 "Today" 字串的最大寬度。|
|[CMonthCalCtrl::GetMinReqRect](#getminreqrect)|抓取在月曆控制項中顯示完整月份所需的最小大小。|
|[CMonthCalCtrl::GetMonthDelta](#getmonthdelta)|抓取月曆控制項的捲軸速率。|
|[CMonthCalCtrl::GetMonthRange](#getmonthrange)|抓取代表月曆控制項顯示之高和低限制的日期資訊。|
|[CMonthCalCtrl::GetRange](#getrange)|抓取月曆控制項中目前設定的最小和最大日期。|
|[CMonthCalCtrl::GetSelRange](#getselrange)|抓取日期資訊, 表示使用者目前選取之日期範圍的上限和下限。|
|[CMonthCalCtrl::GetToday](#gettoday)|針對月曆控制項, 抓取指定為 "today" 之日期的日期資訊。|
|[CMonthCalCtrl::HitTest](#hittest)|決定月曆控制項的哪一個區段位於螢幕上的指定點。|
|[CMonthCalCtrl::IsCenturyView](#iscenturyview)|指出目前月曆控制項目前的視圖是否為世紀視圖。|
|[CMonthCalCtrl::IsDecadeView](#isdecadeview)|指出目前月曆控制項目前的視圖是否為十年的視圖。|
|[CMonthCalCtrl::IsMonthView](#ismonthview)|指出目前月曆控制項目前的視圖是否為月份視圖。|
|[CMonthCalCtrl::IsYearView](#isyearview)|指出目前月曆控制項目前的視圖是否為年份視圖。|
|[CMonthCalCtrl::SetCalendarBorder](#setcalendarborder)|設定目前月曆控制項的框線寬度。|
|[CMonthCalCtrl::SetCalendarBorderDefault](#setcalendarborderdefault)|設定目前月曆控制項框線的預設寬度。|
|[CMonthCalCtrl::SetCalID](#setcalid)|設定目前月曆控制項的行事曆識別碼。|
|[CMonthCalCtrl::SetCenturyView](#setcenturyview)|設定目前月曆控制項以顯示 [世紀] 視圖。|
|[CMonthCalCtrl::SetColor](#setcolor)|設定月曆控制項中指定區域的色彩。|
|[CMonthCalCtrl::SetCurrentView](#setcurrentview)|設定目前月曆控制項以顯示指定的視圖。|
|[CMonthCalCtrl::SetCurSel](#setcursel)|設定月曆控制項目前所選取的日期。|
|[CMonthCalCtrl::SetDayState](#setdaystate)|設定月曆控制項中的天數顯示。|
|[CMonthCalCtrl::SetDecadeView](#setdecadeview)|將當月行事曆控制項設定為十年的視圖。|
|[CMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek)|設定要在行事曆最左邊的資料行中顯示的周間日。|
|[CMonthCalCtrl::SetMaxSelCount](#setmaxselcount)|設定月曆控制項中可選取的最多天數。|
|[CMonthCalCtrl::SetMonthDelta](#setmonthdelta)|設定月曆控制項的捲軸速率。|
|[CMonthCalCtrl::SetMonthView](#setmonthview)|設定目前月曆控制項以顯示月份的視圖。|
|[CMonthCalCtrl::SetRange](#setrange)|設定月曆控制項允許的最小日期和最大值。|
|[CMonthCalCtrl::SetSelRange](#setselrange)|將月曆控制項的選擇設定為指定的日期範圍。|
|[CMonthCalCtrl::SetToday](#settoday)|設定目前日期的行事曆控制項。|
|[CMonthCalCtrl::SetYearView](#setyearview)|將 [月曆] 控制項設定為 [年視圖]。|
|[CMonthCalCtrl::SizeMinReq](#sizeminreq)|將月曆控制項重新繪製為最小的一個月大小。|
|[CMonthCalCtrl::SizeRectToMin](#sizerecttomin)|對於目前的月曆控制項, 會計算最小矩形, 其中可以包含符合指定矩形的所有行事曆。|

## <a name="remarks"></a>備註

月曆控制項提供使用者一個簡單的行事曆介面, 使用者可以從中選取日期。 使用者可以透過下列方式變更顯示:

- 向前和向後移動, 從 month 到 month。

- 按一下 [今天] 文字以顯示目前的日期 (如果未使用 MCS_NOTODAY 樣式)。

- 從快顯功能表中挑選一個月或一年。

您可以自訂月曆控制項, 方法是在建立物件時套用各種樣式。 這些樣式在 Windows SDK 中的月曆[控制項樣式](/windows/win32/Controls/month-calendar-control-styles)中有所描述。

月曆控制項可以顯示超過一個月, 而且可以藉由粗體日期來表示特殊天數 (例如假日)。

如需使用月曆控制項的詳細資訊, 請參閱[使用 CMonthCalCtrl](../../mfc/using-cmonthcalctrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CMonthCalCtrl`

## <a name="requirements"></a>需求

**標頭:** afxdtctl。h

##  <a name="cmonthcalctrl"></a>CMonthCalCtrl:: CMonthCalCtrl

建構 `CMonthCalCtrl` 物件。

```
CMonthCalCtrl();
```

### <a name="remarks"></a>備註

您必須在`Create`建立物件之後呼叫。

##  <a name="create"></a>CMonthCalCtrl:: Create

建立月曆控制項並將其附加至`CMonthCalCtrl`物件。

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
指定套用至月曆控制項的 Windows 樣式組合。 如需樣式的詳細資訊, 請參閱 Windows SDK 中的月曆[控制項樣式](/windows/win32/Controls/month-calendar-control-styles)。

*rect*<br/>
[RECT](/previous-versions/dd162897\(v=vs.85\))結構的參考。 包含月曆控制項的位置和大小。

*pt*<br/>
[點](/previous-versions/dd162805\(v=vs.85\))結構的參考, 可識別月曆控制項的位置。

*pParentWnd*<br/>
[CWnd](../../mfc/reference/cwnd-class.md)物件的指標, 這是月曆控制項的父視窗。 不得為 Null。

*nID*<br/>
指定月曆控制項的控制項 ID。

### <a name="return-value"></a>傳回值

如果初始化成功, 則為非零;否則為0。

### <a name="remarks"></a>備註

以兩個步驟建立月曆控制項:

1. 呼叫[CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)來建立`CMonthCalCtrl`物件。

1. 呼叫這個成員函式, 這會建立月曆控制項並將其附加至`CMonthCalCtrl`物件。

當您呼叫`Create`時, 會初始化通用控制項。 `Create`您呼叫的版本會決定其大小:

- 若要讓 MFC 自動將控制項的大小調整為一個月, 請呼叫使用*pt*參數的覆寫。

- 若要自行調整控制項的大小, 請呼叫此函式的覆寫, 該函式會使用*rect*參數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_1.cpp)]

##  <a name="getcalendarborder"></a>CMonthCalCtrl:: GetCalendarBorder

抓取目前月曆控制項的框線寬度。

```
int GetCalendarBorder() const;
```

### <a name="return-value"></a>傳回值

控制項框線的寬度 (以圖元為單位)。

### <a name="remarks"></a>備註

這個方法會傳送[MCM_GETCALENDARBORDER](/windows/win32/Controls/mcm-getcalendarborder)訊息, 如 Windows SDK 中所述。

##  <a name="getcalendarcount"></a>CMonthCalCtrl:: GetCalendarCount

抓取目前月曆控制項中顯示的行事歷數目。

```
int GetCalendarCount() const;
```

### <a name="return-value"></a>傳回值

月曆控制項中目前顯示的行事歷數目。 允許的行事歷數目上限為12。

### <a name="remarks"></a>備註

這個方法會傳送[MCM_GETCALENDARCOUNT](/windows/win32/Controls/mcm-getcalendarcount)訊息, 如 Windows SDK 中所述。

##  <a name="getcalendargridinfo"></a>CMonthCalCtrl:: GetCalendarGridInfo

抓取目前月曆控制項的相關資訊。

```
BOOL GetCalendarGridInfo(PMCGRIDINFO pmcGridInfo) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*pmcGridInfo*|脫銷[MCGRIDINFO](/windows/win32/api/commctrl/ns-commctrl-mcgridinfo)結構的指標, 它會接收當月行事曆控制項的相關資訊。 呼叫端負責配置及初始化此結構。|

### <a name="return-value"></a>傳回值

如果此方法成功, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[MCM_GETCALENDARGRIDINFO](/windows/win32/Controls/mcm-getcalendargridinfo)訊息, 如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義用來`m_monthCalCtrl`以程式設計方式存取月曆控制項的變數。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>範例

下列程式碼範例會使用`GetCalendarGridInfo`方法來取出當月行事曆控制項顯示的行事曆日期。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_3.cpp)]

##  <a name="getcalid"></a>CMonthCalCtrl:: GetCalID

抓取目前月曆控制項的行事曆識別碼。

```
CALID GetCalID() const;
```

### <a name="return-value"></a>傳回值

其中一個行事[曆識別碼](/windows/win32/Intl/calendar-identifiers)常數。

### <a name="remarks"></a>備註

行事曆識別碼代表區域特定的行事曆, 例如西曆 (當地語系化)、日文或回曆。 您的應用程式可以使用具有各種語言支援功能的行事曆識別碼。

這個方法會傳送[MCM_GETCALID](/windows/win32/Controls/mcm-getcalid)訊息, 如 Windows SDK 中所述。

##  <a name="getcolor"></a>CMonthCalCtrl:: GetColor

抓取*nRegion*指定之月曆控制項區域的色彩。

```
COLORREF GetColor(int nRegion) const;
```

### <a name="parameters"></a>參數

*nRegion*<br/>
從中抓取色彩的月曆控制項區域。 如需值清單, 請參閱[SetColor](#setcolor)的*nRegion*參數。

### <a name="return-value"></a>傳回值

[COLORREF](/windows/win32/gdi/colorref)值, 指定與月曆控制項部分相關聯的色彩 (如果成功的話)。 否則, 此成員函式會傳回-1。

##  <a name="getcurrentview"></a>CMonthCalCtrl:: GetCurrentView

抓取目前月曆控制項目前顯示的視圖。

```
DWORD GetCurrentView() const;
```

### <a name="return-value"></a>傳回值

目前的視圖, 以下列其中一個值表示:

|值|意義|
|-----------|-------------|
|MCMV_MONTH|每月檢視|
|MCMV_YEAR|年度視圖|
|MCMV_DECADE|十年的觀點|
|MCMV_CENTURY|世紀視圖|

### <a name="remarks"></a>備註

這個方法會傳送[MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview)訊息, 如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義用來`m_monthCalCtrl`以程式設計方式存取月曆控制項的變數。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>範例

下列程式碼範例會報告目前顯示月曆控制項的哪一個視圖。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_4.cpp)]

##  <a name="getcursel"></a>CMonthCalCtrl:: GetCurSel

依照目前所選日期的指示, 抓取系統時間。

```
BOOL GetCurSel(COleDateTime& refDateTime) const;  BOOL GetCurSel(CTime& refDateTime) const;

BOOL GetCurSel(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>參數

*refDateTime*<br/>
[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件或[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的參考。 接收目前的時間。

*pDateTime*<br/>
[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標, 會接收目前選取的日期資訊。 這個參數必須是有效的位址, 而且不能是 Null。

### <a name="return-value"></a>傳回值

如果成功, 則為非零;otherwize 0。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [MCM_GETCURSEL](/windows/win32/Controls/mcm-getcursel)的行為, 如 Windows SDK 中所述。

> [!NOTE]
>  如果已設定樣式 MCS_MULTISELECT, 此成員函式會失敗。

在 MFC 的`GetCurSel`執行中, 您可以`COleDateTime`指定使用量、 `CTime`使用方式或`SYSTEMTIME`結構使用方式。

##  <a name="getfirstdayofweek"></a>CMonthCalCtrl:: GetFirstDayOfWeek

取得要在行事曆最左邊的資料行中顯示的第一天。

```
int GetFirstDayOfWeek(BOOL* pbLocal = NULL) const;
```

### <a name="parameters"></a>參數

*pbLocal*<br/>
BOOL 值的指標。 如果值不是零, 則控制項的設定不符合 [控制台] 中的設定。

### <a name="return-value"></a>傳回值

整數值, 代表一周的第一天。 如需這些整數所代表之意義的詳細資訊, 請參閱**備註**。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [MCM_GETFIRSTDAYOFWEEK](/windows/win32/Controls/mcm-getfirstdayofweek)的行為, 如 Windows SDK 中所述。 一周中的天數會以整數表示, 如下所示。

|值|一周中的日|
|-----------|---------------------|
|0|星期一|
|1|星期二|
|2|星期三|
|3|星期四|
|4|星期五|
|5|星期六|
|6|星期日|

### <a name="example"></a>範例

  請參閱[CMonthCalCtrl:: SetFirstDayOfWeek](#setfirstdayofweek)的範例。

##  <a name="getmaxselcount"></a>CMonthCalCtrl:: GetMaxSelCount

抓取月曆控制項中可選取的目前最大天數。

```
int GetMaxSelCount() const;
```

### <a name="return-value"></a>傳回值

整數值, 表示可以為控制項選取的總天數。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [MCM_GETMAXSELCOUNT](/windows/win32/Controls/mcm-getmaxselcount)的行為, 如 Windows SDK 中所述。 將此成員函式用於具有 MCS_MULTISELECT 樣式集的控制項。

### <a name="example"></a>範例

  請參閱[CMonthCalCtrl:: SetMaxSelCount](#setmaxselcount)的範例。

##  <a name="getmaxtodaywidth"></a>CMonthCalCtrl:: GetMaxTodayWidth

抓取目前月曆控制項之 "Today" 字串的最大寬度。

```
DWORD GetMaxTodayWidth() const;
```

### <a name="return-value"></a>傳回值

"Today" 字串的寬度 (以圖元為單位)。

### <a name="example"></a>範例

下列程式碼範例會定義用來`m_monthCalCtrl`以程式設計方式存取月曆控制項的變數。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>範例

下列程式碼範例示範`GetMaxTodayWidth`方法。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_5.cpp)]

### <a name="remarks"></a>備註

使用者可以按一下月曆控制項底部顯示的「今天」字串, 返回目前的日期。 "Today" 字串包含標籤文字和日期文字。

這個方法會傳送[MCM_GETMAXTODAYWIDTH](/windows/win32/Controls/mcm-getmaxtodaywidth)訊息, 如 Windows SDK 中所述。

##  <a name="getminreqrect"></a>CMonthCalCtrl:: GetMinReqRect

抓取在月曆控制項中顯示完整月份所需的最小大小。

```
BOOL GetMinReqRect(RECT* pRect) const;
```

### <a name="parameters"></a>參數

*pRect*<br/>
將接收周框資訊之[RECT](/previous-versions/dd162897\(v=vs.85\))結構的指標。 這個參數必須是有效的位址, 而且不能是 Null。

### <a name="return-value"></a>傳回值

如果成功, 此成員函式會傳回`lpRect`非零值, 並接收適用的界限資訊。 如果失敗, 成員函式會傳回0。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [MCM_GETMINREQRECT](/windows/win32/Controls/mcm-getminreqrect)的行為, 如 Windows SDK 中所述。

##  <a name="getmonthdelta"></a>CMonthCalCtrl:: GetMonthDelta

抓取月曆控制項的捲軸速率。

```
int GetMonthDelta() const;
```

### <a name="return-value"></a>傳回值

月曆控制項的捲軸速率。 [捲軸速率] 是當使用者按一下捲軸按鈕一次時, 控制項移動其顯示的月數。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [MCM_GETMONTHDELTA](/windows/win32/Controls/mcm-getmonthdelta)的行為, 如 Windows SDK 中所述。

##  <a name="getmonthrange"></a>CMonthCalCtrl:: GetMonthRange

抓取代表月曆控制項顯示之高和低限制的日期資訊。

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
[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的參考, 其中包含允許的最小日期。

*refMaxRange*<br/>
`COleDateTime` 或`CTime`物件的參考, 其中包含允許的最大日期。

*pMinRange*<br/>
[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標, 其中包含範圍最低結尾的日期。

*pMaxRange*<br/>
`SYSTEMTIME`結構的指標, 包含範圍最高結尾的日期。

*dwFlags*<br/>
值, 指定要抓取範圍限制的範圍。 此值必須為下列其中一項。

|值|意義|
|-----------|-------------|
|GMR_DAYSTATE|包含只有部分顯示的可見範圍先前和尾端月份。|
|GMR_VISIBLE|只包含完全顯示的月份。|

### <a name="return-value"></a>傳回值

以月為單位的整數, 表示第一個和第二個版本中*refMinRange*和*refMaxRange*所指示的兩個限制範圍, 或第三個版本中的*pMinRange*和*pMaxRange* 。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [MCM_GETMONTHRANGE](/windows/win32/Controls/mcm-getmonthrange)的行為, 如 Windows SDK 中所述。 在`GetMonthRange`MFC 的執行中, 您可以指定`COleDateTime`使用方式、 `CTime`使用方式或`SYSTEMTIME`結構用法。

### <a name="example"></a>範例

  請參閱[CMonthCalCtrl:: SetDayState](#setdaystate)的範例。

##  <a name="getrange"></a>CMonthCalCtrl:: GetRange

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
物件、物件或[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標, 其中包含範圍最低結尾的日期。 `CTime` `COleDateTime`

*pMaxRange*<br/>
物件、物件或[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標, 其中包含範圍最大結尾的日期。 `CTime` `COleDateTime`

### <a name="return-value"></a>傳回值

可以是零的 DWORD (未設定任何限制), 或指定限制資訊的下列值的組合。

|值|意義|
|-----------|-------------|
|GDTR_MAX|已設定控制項的最大限制;*pMaxRange*有效, 而且包含適用的日期資訊。|
|GDTR_MIN|針對控制項設定最小限制;*pMinRange*有效, 而且包含適用的日期資訊。|

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [MCM_GETRANGE](/windows/win32/Controls/mcm-getrange)的行為, 如 Windows SDK 中所述。 在 MFC 的`GetRange`執行中, 您可以`COleDateTime`指定使用量、 `CTime`使用方式或`SYSTEMTIME`結構使用方式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_6.cpp)]

##  <a name="getselrange"></a>CMonthCalCtrl:: GetSelRange

抓取日期資訊, 表示使用者目前選取之日期範圍的上限和下限。

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
[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的參考, 其中包含允許的最小日期。

*refMaxRange*<br/>
`COleDateTime` 或`CTime`物件的參考, 其中包含允許的最大日期。

*pMinRange*<br/>
[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標, 其中包含範圍最低結尾的日期。

*pMaxRange*<br/>
`SYSTEMTIME`結構的指標, 包含範圍最高結尾的日期。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [MCM_GETSELRANGE](/windows/win32/Controls/mcm-getselrange)的行為, 如 Windows SDK 中所述。 `GetSelRange`如果套用至不使用 MCS_MULTISELECT 樣式的月曆控制項, 將會失敗。

在`GetSelRange`MFC 的執行中, 您可以指定`COleDateTime`使用方式、 `CTime`使用方式或`SYSTEMTIME`結構用法。

##  <a name="gettoday"></a>CMonthCalCtrl:: GetToday

針對月曆控制項, 抓取指定為 "today" 之日期的日期資訊。

```
BOOL GetToday(COleDateTime& refDateTime) const;  BOOL GetToday(COleDateTime& refDateTime) const;

BOOL GetToday(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>參數

*refDateTime*<br/>
[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的參考, 指出目前的日期。

*pDateTime*<br/>
將接收日期資訊之[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標。 這個參數必須是有效的位址, 而且不能是 Null。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [MCM_GETTODAY](/windows/win32/Controls/mcm-gettoday)的行為, 如 Windows SDK 中所述。 在 MFC 的`GetToday`執行中, 您可以`COleDateTime`指定使用量、 `CTime`使用方式或`SYSTEMTIME`結構使用方式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_7.cpp)]

##  <a name="hittest"></a>CMonthCalCtrl:: HitTest

判斷月曆控制項 (如果有的話) 位於指定的位置。

```
DWORD HitTest(PMCHITTESTINFO pMCHitTest);
```

### <a name="parameters"></a>參數

*pMCHitTest*<br/>
[MCHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-mchittestinfo)結構的指標, 其中包含月曆控制項的點擊測試點。

### <a name="return-value"></a>傳回值

DWORD 值。 等於`MCHITTESTINFO`結構的**uHit**成員。

### <a name="remarks"></a>備註

`HitTest``MCHITTESTINFO`使用結構, 其中包含點擊測試的相關資訊。

##  <a name="iscenturyview"></a>CMonthCalCtrl:: IsCenturyView

指出目前月曆控制項目前的視圖是否為世紀視圖。

```
BOOL IsCenturyView() const;
```

### <a name="return-value"></a>傳回值

如果目前的視圖是世紀視圖, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview)訊息, 如 Windows SDK 中所述。 如果該訊息傳回 MCMV_CENTURY, 則這個方法會傳回 TRUE。

##  <a name="isdecadeview"></a>CMonthCalCtrl:: IsDecadeView

指出目前月曆控制項目前的視圖是否為十年的視圖。

```
BOOL IsDecadeView() const;
```

### <a name="return-value"></a>傳回值

如果目前的視圖是十年的視圖, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview)訊息, 如 Windows SDK 中所述。 如果該訊息傳回 MCMV_DECADE, 則這個方法會傳回 TRUE。

##  <a name="ismonthview"></a>CMonthCalCtrl:: IsMonthView

指出目前月曆控制項目前的視圖是否為月份視圖。

```
BOOL IsMonthView() const;
```

### <a name="return-value"></a>傳回值

如果目前的 view 為 month 視圖, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview)訊息, 如 Windows SDK 中所述。 如果該訊息傳回 MCMV_MONTH, 則這個方法會傳回 TRUE。

##  <a name="isyearview"></a>CMonthCalCtrl:: IsYearView

指出目前月曆控制項目前的視圖是否為年份視圖。

```
BOOL IsYearView() const;
```

### <a name="return-value"></a>傳回值

如果目前的視圖為年份視圖, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview)訊息, 如 Windows SDK 中所述。 如果該訊息傳回 MCMV_YEAR, 則這個方法會傳回 TRUE。

##  <a name="setcalendarborder"></a>CMonthCalCtrl:: SetCalendarBorder

設定目前月曆控制項的框線寬度。

```
void SetCalendarBorder(int cxyBorder);
```

### <a name="parameters"></a>參數

|參數|說明|
|---------------|-----------------|
|*cxyBorder*|在框線的寬度 (以圖元為單位)。|

### <a name="remarks"></a>備註

如果此方法成功, 則框線寬度會設定為*cxyBorder*參數。 否則, 框線寬度會重設為目前[主題](/windows/win32/Controls/visual-styles-overview)所指定的預設值, 如果未使用主題, 則為零。

這個方法會傳送[MCM_SETCALENDARBORDER](/windows/win32/Controls/mcm-setcalendarborder)訊息, 如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義用來`m_monthCalCtrl`以程式設計方式存取月曆控制項的變數。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>範例

下列程式碼範例會將月曆控制項的框線寬度設定為八個圖元。 請使用[CMonthCalCtrl:: GetCalendarBorder](#getcalendarborder)方法來判斷這個方法是否成功。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_8.cpp)]

##  <a name="setcalendarborderdefault"></a>CMonthCalCtrl:: SetCalendarBorderDefault

設定目前月曆控制項框線的預設寬度。

```
void SetCalendarBorderDefault();
```

### <a name="remarks"></a>備註

框線寬度設定為目前[主題](/windows/win32/Controls/visual-styles-overview)所指定的預設值, 如果未使用主題則為零。

這個方法會傳送[MCM_SETCALENDARBORDER](/windows/win32/Controls/mcm-setcalendarborder)訊息, 如 Windows SDK 中所述。

##  <a name="setcalid"></a>CMonthCalCtrl:: SetCalID

設定目前月曆控制項的行事曆識別碼。

```
BOOL SetCalID(CALID calid);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*calid*|在其中一個行事[曆識別碼](/windows/win32/Intl/calendar-identifiers)常數。|

### <a name="return-value"></a>傳回值

如果此方法成功, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

行事曆識別碼會指定特定地區行事曆, 例如西曆 (當地語系化)、日文或回曆。 如果您的電腦上已安裝包含行事曆的地區設定, 請使用方法來顯示calid參數所指定的行事`SetCalID`曆。

這個方法會傳送[MCM_SETCALID](/windows/win32/Controls/mcm-setcalid)訊息, 如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義用來`m_monthCalCtrl`以程式設計方式存取月曆控制項的變數。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>範例

下列程式碼範例會設定月曆控制項, 以顯示日本天皇紀元行事曆。 只有`SetCalID`當您的電腦上已安裝該行事歷時, 此方法才會成功。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_9.cpp)]

##  <a name="setcenturyview"></a>CMonthCalCtrl:: SetCenturyView

設定目前月曆控制項以顯示 [世紀] 視圖。

```
BOOL SetCenturyView();
```

### <a name="return-value"></a>傳回值

如果此方法成功, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會使用[CMonthCalCtrl:: SetCurrentView](#setcurrentview)方法, 將 view 設定為`MCMV_CENTURY`, 其代表世紀視圖。

##  <a name="setcolor"></a>CMonthCalCtrl:: SetColor

設定月曆控制項中指定區域的色彩。

```
COLORREF SetColor(
    int nRegion,
    COLORREF ref);
```

### <a name="parameters"></a>參數

*nRegion*<br/>
整數值, 指定要設定的月曆色彩。 這個值可以是下列其中一項。

|值|意義|
|-----------|-------------|
|MCSC_BACKGROUND|在月份之間顯示的背景色彩。|
|MCSC_MONTHBK|在月份內顯示的背景色彩。|
|MCSC_TEXT|用來在月份中顯示文字的色彩。|
|MCSC_TITLEBK|顯示在行事曆標題中的背景色彩。|
|MCSC_TITLETEXT|用來在行事曆標題中顯示文字的色彩。|
|MCSC_TRAILINGTEXT|用來顯示標頭和尾端日期文字的色彩。 [標頭] 和 [尾端天數] 是在目前行事曆上出現的過去和之後幾天。|

*ref*<br/>
月曆控制項之指定部分的新色彩設定的 COLORRE光圈值。

### <a name="return-value"></a>傳回值

COLORRE光圈值, 表示月曆控制項指定部分的上一個色彩設定 (如果成功的話)。 否則, 此訊息會傳回-1。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [MCM_SETCOLOR](/windows/win32/Controls/mcm-setcolor)的行為, 如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_10.cpp)]

##  <a name="setcurrentview"></a>CMonthCalCtrl:: SetCurrentView

設定目前月曆控制項以顯示指定的視圖。

```
BOOL SetCurrentView(DWORD dwNewView);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*dwNewView*|在下列其中一個指定每月、每年、十年或世紀視圖的值。<br /><br /> MCMV_MONTH:每月檢視<br /><br /> MCMV_YEAR:年度視圖<br /><br /> MCMV_DECADE:十年的觀點<br /><br /> MCMV_CENTURY:世紀視圖|

### <a name="return-value"></a>傳回值

如果此方法成功, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[MCM_SETCURRENTVIEW](/windows/win32/Controls/mcm-setcurrentview)訊息, 如 Windows SDK 中所述。

##  <a name="setcursel"></a>CMonthCalCtrl:: SetCurSel

設定月曆控制項目前所選取的日期。

```
BOOL SetCurSel(const COleDateTime& refDateTime);
BOOL SetCurSel(const CTime& refDateTime);
BOOL SetCurSel(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>參數

*refDateTime*<br/>
[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的參考, 指出目前選取的月曆控制項。

*pDateTime*<br/>
[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標, 其中包含要設定為目前選取範圍的日期。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [MCM_SETCURSEL](/windows/win32/Controls/mcm-setcursel)的行為, 如 Windows SDK 中所述。 在 MFC 的`SetCurSel`執行中, 您可以`COleDateTime`指定使用量、 `CTime`使用方式或`SYSTEMTIME`結構使用方式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#5](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_11.cpp)]

##  <a name="setdaystate"></a>CMonthCalCtrl:: SetDayState

設定月曆控制項中的天數顯示。

```
BOOL SetDayState(
    int nMonths,
    LPMONTHDAYSTATE pStates);
```

### <a name="parameters"></a>參數

*nMonths*<br/>
指出*pStates*指向的陣列中有多少元素的值。

*pStates*<br/>
值的[MONTHDAYSTATE](/windows/win32/Controls/monthdaystate)陣列指標, 定義月曆控制項在其顯示中每天繪製的方式。 MONTHDAYSTATE 資料類型是位欄位, 其中每個位 (1 到 31) 代表一個月中某一天的狀態。 如果位元是開啟的，則對應的日期會以粗體顯示；否則就不會強調其顯示。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [MCM_SETDAYSTATE](/windows/win32/Controls/mcm-setdaystate)的行為, 如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_12.cpp)]

##  <a name="setdecadeview"></a>CMonthCalCtrl:: SetDecadeView

將當月行事曆控制項設定為十年的視圖。

```
BOOL SetDecadeView();
```

### <a name="return-value"></a>傳回值

如果此方法成功, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會使用[CMonthCalCtrl:: SetCurrentView](#setcurrentview)方法, 將 view 設定為`MCMV_DECADE`, 這代表十年的視圖。

##  <a name="setfirstdayofweek"></a>CMonthCalCtrl:: SetFirstDayOfWeek

設定要在行事曆最左邊的資料行中顯示的周間日。

```
BOOL SetFirstDayOfWeek(
    int iDay,
    int* lpnOld = NULL);
```

### <a name="parameters"></a>參數

*iDay*<br/>
整數值, 表示要將哪一天設定為一周的第一天。 此值必須是其中一個日期數位。 如需日號的說明, 請參閱[GetFirstDayOfWeek](#getfirstdayofweek) 。

*lpnOld*<br/>
整數的指標, 表示先前設定之一周的第一天。

### <a name="return-value"></a>傳回值

如果上周的第一天設定為 LOCALE_IFIRSTDAYOFWEEK 以外的值, 則為非零, 這是 [控制台] 設定中所指出的日期。 否則, 此函數會傳回0。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [MCM_SETFIRSTDAYOFWEEK](/windows/win32/Controls/mcm-setfirstdayofweek)的行為, 如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_13.cpp)]

##  <a name="setmaxselcount"></a>CMonthCalCtrl:: SetMaxSelCount

設定月曆控制項中可選取的最多天數。

```
BOOL SetMaxSelCount(int nMax);
```

### <a name="parameters"></a>參數

*nMax*<br/>
將設定為的值, 表示可選取的天數上限。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [MCM_SETMAXSELCOUNT](/windows/win32/Controls/mcm-setmaxselcount)的行為, 如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#8](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_14.cpp)]

##  <a name="setmonthdelta"></a>  CMonthCalCtrl::SetMonthDelta

設定月曆控制項的捲軸速率。

```
int SetMonthDelta(int iDelta);
```

### <a name="parameters"></a>參數

*iDelta*<br/>
要設定為控制項的滾動速率的月份數。 如果此值為零, 則會將月份差異重設為預設值, 這是控制項中顯示的月數。

### <a name="return-value"></a>傳回值

先前的滾動速率。 如果先前尚未設定捲軸速率, 則傳回值為0。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [MCM_SETMONTHDELTA](/windows/win32/Controls/mcm-setmonthdelta)的行為, 如 Windows SDK 中所述。

##  <a name="setmonthview"></a>CMonthCalCtrl:: SetMonthView

設定目前月曆控制項以顯示月份的視圖。

```
BOOL SetMonthView();
```

### <a name="return-value"></a>傳回值

如果此方法成功, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會使用[CMonthCalCtrl:: SetCurrentView](#setcurrentview)方法, 將 view 設定為 MCMV_MONTH, 這代表月份的觀點。

### <a name="example"></a>範例

下列程式碼範例會定義用來`m_monthCalCtrl`以程式設計方式存取月曆控制項的變數。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>範例

下列程式碼範例會設定月曆控制項, 以顯示 [月]、[年]、[十年] 和 [世紀] 的觀點。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_15.cpp)]

##  <a name="setrange"></a>CMonthCalCtrl:: SetRange

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
物件、物件或[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標, 其中包含範圍最低結尾的日期。 `CTime` `COleDateTime`

*pMaxRange*<br/>
`COleDateTime` 物件`CTime` 、物件或`SYSTEMTIME`結構的指標, 其中包含範圍最大結尾的日期。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [MCM_SETRANGE](/windows/win32/Controls/mcm-setrange)的行為, 如 Windows SDK 中所述。 在`SetRange`MFC 的執行中, 您可以指定`COleDateTime`使用方式、 `CTime`使用方式或`SYSTEMTIME`結構用法。

### <a name="example"></a>範例

  請參閱[CMonthCalCtrl:: GetRange](#getrange)的範例。

##  <a name="setselrange"></a>CMonthCalCtrl:: SetSelRange

將月曆控制項的選擇設定為指定的日期範圍。

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
物件、物件或[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標, 其中包含範圍最低結尾的日期。 `CTime` `COleDateTime`

*pMaxRange*<br/>
`COleDateTime` 物件`CTime` 、物件或`SYSTEMTIME`結構的指標, 其中包含範圍最大結尾的日期。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [MCM_SETSELRANGE](/windows/win32/Controls/mcm-setselrange)的行為, 如 Windows SDK 中所述。 在`SetSelRange`MFC 的執行中, 您可以指定`COleDateTime`使用方式、 `CTime`使用方式或`SYSTEMTIME`結構用法。

##  <a name="settoday"></a>CMonthCalCtrl:: SetToday

設定目前日期的行事曆控制項。

```
void SetToday(const COleDateTime& refDateTime);
void SetToday(const CTime* pDateTime);
void SetToday(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>參數

*refDateTime*<br/>
包含目前日期之[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件的參考。

*pDateTime*<br/>
在第二個版本中, 包含目前日期資訊的[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件指標。 在第三個版本中, [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標, 其中包含目前的日期資訊。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [MCM_SETTODAY](/windows/win32/Controls/mcm-settoday)的行為, 如 Windows SDK 中所述。

### <a name="example"></a>範例

  請參閱[CMonthCalCtrl:: GetToday](#gettoday)的範例。

##  <a name="setyearview"></a>CMonthCalCtrl:: SetYearView

將 [月曆] 控制項設定為 [年視圖]。

```
BOOL SetYearView();
```

### <a name="return-value"></a>傳回值

如果此方法成功, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會使用[CMonthCalCtrl:: SetCurrentView](#setcurrentview)方法, 將 view 設定為 MCMV_YEAR, 這代表年度視圖。

##  <a name="sizeminreq"></a>CMonthCalCtrl:: SizeMinReq

將月曆控制項顯示為顯示一個月的最小大小。

```
BOOL SizeMinReq(BOOL bRepaint = TRUE);
```

### <a name="parameters"></a>參數

*bRepaint*<br/>
指定是否要重新繪製控制項。 預設為 TRUE。 如果為 FALSE, 則不會進行重新繪製。

### <a name="return-value"></a>傳回值

如果月曆控制項的大小調整為最小值, 則為非零值;否則為0。

### <a name="remarks"></a>備註

[ `SizeMinReq`呼叫成功] 會顯示一個月行事曆的整個月曆控制項。

##  <a name="sizerecttomin"></a>CMonthCalCtrl:: SizeRectToMin

對於目前的月曆控制項, 會計算最小矩形, 其中可以包含符合指定矩形的所有行事曆。

```
LPRECT SizeRectToMin(LPRECT lpRect);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*lpRect*|在[RECT](/previous-versions/dd162897\(v=vs.85\))結構的指標, 定義包含所需行事歷數目的矩形。|

### <a name="return-value"></a>傳回值

[RECT](/previous-versions/dd162897\(v=vs.85\))結構的指標, 定義其大小小於或等於*lpRect*參數所定義之矩形的矩形。

### <a name="remarks"></a>備註

這個方法會計算*lpRect*參數所指定矩形中可以容納多少個行事曆, 然後傳回可包含該行事歷數目的最小矩形。 實際上, 這個方法會縮小指定的矩形, 使其完全符合所需的行事歷數目。

這個方法會傳送[MCM_SIZERECTTOMIN](/windows/win32/Controls/mcm-sizerecttomin)訊息, 如 Windows SDK 中所述。

## <a name="see-also"></a>另請參閱

[MFC 範例 CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDateTimeCtrl 類別](../../mfc/reference/cdatetimectrl-class.md)
