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
ms.openlocfilehash: da9d588811361d3dfd72d44d5b9ced8460d23936
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319748"
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
|[CMonthCalCtrl:cmonthCalCtrl](#cmonthcalctrl)|建構 `CMonthCalCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMonthCalctrl::建立](#create)|創建月曆控制件並將其附加到`CMonthCalCtrl`物件。|
|[CMonthCalctrl::取得行事曆邊框](#getcalendarborder)|檢索當前月日曆控件的邊框的寬度。|
|[CMonthCalctrl::取得日曆計數](#getcalendarcount)|檢索當前月份日曆控件中顯示的日曆數。|
|[CMonthCalctrl::取得行事曆格資訊](#getcalendargridinfo)|檢索有關當月日曆控件的資訊。|
|[CMonthCalctrl::GetCalID](#getcalid)|檢索當月日曆控件的行事曆標識符。|
|[CMonthCalctrl:取得顏色](#getcolor)|獲取月份行事曆控制件的指定區域的顏色。|
|[CMonthCalctrl::取得電流視圖](#getcurrentview)|檢索目前由當前月份日曆控件顯示的視圖。|
|[CMonthCalctrl::取得CurSel](#getcursel)|檢索當前選擇的日期指示的系統時間。|
|[CmonthCalctrl:取得第一天周](#getfirstdayofweek)|獲取要顯示在日曆最左側列中的一周的第一天。|
|[CMonthCalctrl::取得MaxSelCount](#getmaxselcount)|檢索可在月份日曆控件中選擇的當前最大天數。|
|[CMonthCalctrl::獲取今天最大寬度](#getmaxtodaywidth)|檢索當前月份日曆控件的"今天"字串的最大寬度。|
|[CMonthCalctrl::取得MinReqrect](#getminreqrect)|檢索在月份日曆控件中顯示完整月份所需的最小大小。|
|[CMonthCalctrl::獲取月德爾塔](#getmonthdelta)|檢索一個月日曆控件的滾動速率。|
|[CMonthCalctrl:取得月航程](#getmonthrange)|檢索表示月曆控件顯示的上限和低點的日期資訊。|
|[CMonthCalctrl:取得範圍](#getrange)|檢索在月份日曆控件中設置的當前最小和最大日期。|
|[CMonthCalctrl::GetSelRange](#getselrange)|檢索表示使用者當前選擇的日期範圍的上限和下限的日期資訊。|
|[CMonthCalctrl:今天獲取](#gettoday)|檢索指定為"今天"的日期的日期資訊,用於一個月的日曆控件。|
|[CMonthCalctrl:hitTest](#hittest)|確定月曆控件的哪個部分位於螢幕上的給定點。|
|[CMonthCalctrl:Is世紀檢視](#iscenturyview)|指示當前月曆控件的視圖是否是世紀視圖。|
|[CMonthCalctrl::是十年視圖](#isdecadeview)|指示當前月日曆控件的當前視圖是否是十年視圖。|
|[CMonthCalctrl::IsMonthView](#ismonthview)|指示當前月日曆控件的當前視圖是否是月視圖。|
|[CMonthCalctrl:isYearView](#isyearview)|指示當前月日曆控件的當前檢視是否是年份視圖。|
|[CMonthCalctrl::設定行事曆邊框](#setcalendarborder)|設置當前月日曆控件的邊框的寬度。|
|[CMonthCalctrl::設定行事曆邊框預設](#setcalendarborderdefault)|設置當前月日曆控件邊框的預設寬度。|
|[CMonthCalctrl::SetCalID](#setcalid)|設置當月日曆控件的行事曆標識符。|
|[CMonthCalctrl::設定世紀檢視](#setcenturyview)|設置當前月曆控件以顯示世紀視圖。|
|[CMonthCalctrl::設定顏色](#setcolor)|設置月曆控制件的指定區域的顏色。|
|[CMonthCalctrl::設定電流檢視](#setcurrentview)|設置當前月曆控制項以顯示指定的檢視。|
|[CMonthCalctrl::SetCurSel](#setcursel)|設置月份行事曆控制件的當前選定日期。|
|[CMonthCalctrl:setDayState](#setdaystate)|設置一個月日曆控件中的天數的顯示。|
|[CMonthCalctrl::設置十年檢視](#setdecadeview)|將當前月曆控件設置到十年視圖。|
|[CmonthCalctrl::每周第一天](#setfirstdayofweek)|將要顯示在日曆最左側列中的星期幾。|
|[CMonthCalctrl::SetMaxSelCount](#setmaxselcount)|設置可在月份日曆控件中選擇的最大天數。|
|[CMonthCalctrl::設置月德爾塔](#setmonthdelta)|設置月曆控件的滾動速率。|
|[CMonthCalctrl::設定月景](#setmonthview)|設置當前月曆控件以顯示月視圖。|
|[CMonthCalctrl::SetRange](#setrange)|設置月曆控制件的最小和最大允許日期。|
|[CMonthCalctrl::SetSelRange](#setselrange)|將月份日曆控件的選擇設置為給定日期範圍。|
|[CMonthCalctrl::今天設置](#settoday)|設置當天的日曆控件。|
|[CMonthCalctrl::SetYearView](#setyearview)|將當前月日曆控件設置為年視圖。|
|[CMonthCalctrl::SizeMinReq](#sizeminreq)|將月曆控件重新繪製為其最小一個月大小。|
|[CmonthCalctrl::大小雷克特明](#sizerecttomin)|對於當前月曆控制件,計算可以包含適合指定矩形的所有日曆的最小矩形。|

## <a name="remarks"></a>備註

月曆控件為使用者提供了一個簡單的日曆介面,用戶可以從中選擇日期。 使用者可以透過以下變更顯示:

- 逐月向後滾動和向前滾動。

- 按下「今天」文本以顯示當前天(如果未使用MCS_NOTODAY樣式)。

- 從彈出式功能表中選擇一個月或一年。

您可以在建立物件時對物件應用各種樣式來自定義月曆控制件。 這些樣式在 Windows SDK 中的[月曆控制樣式](/windows/win32/Controls/month-calendar-control-styles)中描述。

月曆控件可以顯示超過一個月,並且可以通過粗體日期來指示特殊日期(如假日)。

有關使用月曆控制件的詳細資訊,請參閱[使用 CMonthCalCtrl](../../mfc/using-cmonthcalctrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CMonthCalCtrl`

## <a name="requirements"></a>需求

**標題:** afxdtctl.h

## <a name="cmonthcalctrlcmonthcalctrl"></a><a name="cmonthcalctrl"></a>CMonthCalCtrl:cmonthCalCtrl

建構 `CMonthCalCtrl` 物件。

```
CMonthCalCtrl();
```

### <a name="remarks"></a>備註

構造對象`Create`後 必須調用。

## <a name="cmonthcalctrlcreate"></a><a name="create"></a>CMonthCalctrl::建立

創建月曆控制件並將其附加到`CMonthCalCtrl`物件。

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
指定應用於月曆控制件的 Windows 樣式的組合。 有關樣式的詳細資訊,請參閱 Windows SDK 中的[月行事曆控制元件樣式](/windows/win32/Controls/month-calendar-control-styles)。

*矩形*<br/>
對[RECT](/previous-versions/dd162897\(v=vs.85\))結構的引用。 包含月曆控制件的位置和大小。

*pt*<br/>
對標識月曆控件位置的[POINT](/previous-versions/dd162805\(v=vs.85\))結構的引用。

*pparentwnd*<br/>
指向[CWnd](../../mfc/reference/cwnd-class.md)物件的指標,該物件是月曆控件的父視窗。 它不得為 NULL。

*nID*<br/>
指定月曆控制件的控制 ID。

### <a name="return-value"></a>傳回值

初始化成功時非零;否則 0。

### <a name="remarks"></a>備註

通過兩個步驟建立月曆控制項:

1. 調用[CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)`CMonthCalCtrl`構造 物件。

1. 調用此成員函數,該函數創建月曆控件並將其附加到`CMonthCalCtrl`物件。

呼叫`Create`時呼叫 ,將初始化公共控制項。 呼叫的版本`Create`決定了其大小:

- 要讓 MFC 自動將控制器大小調整為一個月,請呼叫使用*pt*參數的重寫。

- 要自行調整控制項的大小,請呼叫使用*rect*參數的此函數的重寫。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_1.cpp)]

## <a name="cmonthcalctrlgetcalendarborder"></a><a name="getcalendarborder"></a>CMonthCalctrl::取得行事曆邊框

檢索當前月日曆控件的邊框的寬度。

```
int GetCalendarBorder() const;
```

### <a name="return-value"></a>傳回值

控件邊框的寬度(以像素為單位)。

### <a name="remarks"></a>備註

此方法發送[MCM_GETCALENDARBORDER](/windows/win32/Controls/mcm-getcalendarborder)消息,這在 Windows SDK 中介紹。

## <a name="cmonthcalctrlgetcalendarcount"></a><a name="getcalendarcount"></a>CMonthCalctrl::取得日曆計數

檢索當前月份日曆控件中顯示的日曆數。

```
int GetCalendarCount() const;
```

### <a name="return-value"></a>傳回值

當前顯示在月份日曆控件中的日曆數。 允許的最大日曆數為 12。

### <a name="remarks"></a>備註

此方法發送[MCM_GETCALENDARCOUNT](/windows/win32/Controls/mcm-getcalendarcount)消息,這在 Windows SDK 中介紹。

## <a name="cmonthcalctrlgetcalendargridinfo"></a><a name="getcalendargridinfo"></a>CMonthCalctrl::取得行事曆格資訊

檢索有關當月日曆控件的資訊。

```
BOOL GetCalendarGridInfo(PMCGRIDINFO pmcGridInfo) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*pmcGrid資訊*|[出]指向接收有關當月日曆控件資訊的[MCGRIDINFO](/windows/win32/api/commctrl/ns-commctrl-mcgridinfo)結構的指標。 調用方負責分配和初始化此結構。|

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法發送[MCM_GETCALENDARGRIDINFO](/windows/win32/Controls/mcm-getcalendargridinfo)消息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

以下代碼範例定義用於以程式設計方式存`m_monthCalCtrl`取 月份行事曆控制的變數 。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>範例

以下代碼示例使用`GetCalendarGridInfo`方法 檢索當前月份日曆控件顯示的日曆日期。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_3.cpp)]

## <a name="cmonthcalctrlgetcalid"></a><a name="getcalid"></a>CMonthCalctrl::GetCalID

檢索當月日曆控件的行事曆標識符。

```
CALID GetCalID() const;
```

### <a name="return-value"></a>傳回值

[日曆標識符](/windows/win32/Intl/calendar-identifiers)常量之一。

### <a name="remarks"></a>備註

日曆標識符表示特定於區域的日曆,例如公曆(本地化)、日語或 Hijri 日曆。 您的應用程式可以使用具有各種語言支援功能的行事曆標識符。

此方法發送[MCM_GETCALID](/windows/win32/Controls/mcm-getcalid)消息,這在 Windows SDK 中介紹。

## <a name="cmonthcalctrlgetcolor"></a><a name="getcolor"></a>CMonthCalctrl:取得顏色

檢索*n 區域*指定的月曆控制件的區域的顏色。

```
COLORREF GetColor(int nRegion) const;
```

### <a name="parameters"></a>參數

*n 區域*<br/>
從中檢索顏色的月曆控件的區域。 有關值清單,請參閱[SetColor](#setcolor)的*n 區域*參數。

### <a name="return-value"></a>傳回值

指定與月曆控制件部分關聯的顏色(如果成功)的[COLORREF](/windows/win32/gdi/colorref)值。 否則,此成員函數返回 -1。

## <a name="cmonthcalctrlgetcurrentview"></a><a name="getcurrentview"></a>CMonthCalctrl::取得電流視圖

檢索目前由當前月份日曆控件顯示的視圖。

```
DWORD GetCurrentView() const;
```

### <a name="return-value"></a>傳回值

目前檢視,由以下值之一指示:

|值|意義|
|-----------|-------------|
|MCMV_MONTH|每月檢視|
|MCMV_YEAR|年度檢視|
|MCMV_DECADE|十年檢視|
|MCMV_CENTURY|世紀景觀|

### <a name="remarks"></a>備註

此方法發送[MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview)消息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

以下代碼範例定義用於以程式設計方式存`m_monthCalCtrl`取 月份行事曆控制的變數 。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>範例

顯示以下查看月曆控件的代碼示例報告。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_4.cpp)]

## <a name="cmonthcalctrlgetcursel"></a><a name="getcursel"></a>CMonthCalctrl::取得CurSel

檢索當前選擇的日期指示的系統時間。

```
BOOL GetCurSel(COleDateTime& refDateTime) const;  BOOL GetCurSel(CTime& refDateTime) const;

BOOL GetCurSel(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>參數

*參考日期時間*<br/>
對[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件或[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的引用。 接收當前時間。

*pDateTime*<br/>
指向[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標,該結構將接收當前選擇的日期資訊。 此參數必須是有效位址,不能為 NULL。

### <a name="return-value"></a>傳回值

如果成功,則非零;其他w化0。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[MCM_GETCURSEL](/windows/win32/Controls/mcm-getcursel)的行為,如 Windows SDK 中所述。

> [!NOTE]
> 如果設置了樣式MCS_MULTISELECT,則此成員函數將失敗。

在 MFC`GetCurSel`的 實現`COleDateTime`中,`CTime`可以指定用法`SYSTEMTIME`、用法或 結構用法。

## <a name="cmonthcalctrlgetfirstdayofweek"></a><a name="getfirstdayofweek"></a>CmonthCalctrl:取得第一天周

獲取要顯示在日曆最左側列中的一周的第一天。

```
int GetFirstDayOfWeek(BOOL* pbLocal = NULL) const;
```

### <a name="parameters"></a>參數

*pb 本地*<br/>
指向 BOOL 值的指標。 如果值為非零,則控制項的設置與控制面板中的設置不匹配。

### <a name="return-value"></a>傳回值

表示一周第一天的整數值。 有關這些整數代表的內容的詳細資訊,請參閱**備註**。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[MCM_GETFIRSTDAYOFWEEK](/windows/win32/Controls/mcm-getfirstdayofweek)的行為,如 Windows SDK 中所述。 星期的天數表示為整數,如下所示。

|值|星期一|
|-----------|---------------------|
|0|星期一|
|1|Tuesday|
|2|星期三|
|3|Thursday|
|4|星期五|
|5|星期六|
|6|星期日|

### <a name="example"></a>範例

  請參閱[CMonthCalCtrl 的範例::設定第一天周](#setfirstdayofweek)。

## <a name="cmonthcalctrlgetmaxselcount"></a><a name="getmaxselcount"></a>CMonthCalctrl::取得MaxSelCount

檢索可在月份日曆控件中選擇的當前最大天數。

```
int GetMaxSelCount() const;
```

### <a name="return-value"></a>傳回值

表示可以為控制項選擇的天數的總天數的整數值。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[MCM_GETMAXSELCOUNT](/windows/win32/Controls/mcm-getmaxselcount)的行為,如 Windows SDK 中所述。 對於具有MCS_MULTISELECT樣式集的控制項,使用此成員函數。

### <a name="example"></a>範例

  請參閱[CMonthCalCtrl 的範例::SetMaxSelCount](#setmaxselcount)。

## <a name="cmonthcalctrlgetmaxtodaywidth"></a><a name="getmaxtodaywidth"></a>CMonthCalctrl::獲取今天最大寬度

檢索當前月份日曆控件的"今天"字串的最大寬度。

```
DWORD GetMaxTodayWidth() const;
```

### <a name="return-value"></a>傳回值

"今天"字串的寬度(以像素為單位)。

### <a name="example"></a>範例

以下代碼範例定義用於以程式設計方式存`m_monthCalCtrl`取 月份行事曆控制的變數 。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>範例

以下代碼範例展示該方法`GetMaxTodayWidth`。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_5.cpp)]

### <a name="remarks"></a>備註

使用者可以通過按一下「今天」字串返回到當前日期,該字串顯示在月曆控制件的底部。 "今天"字串包括標籤文本和日期文字。

此方法發送[MCM_GETMAXTODAYWIDTH](/windows/win32/Controls/mcm-getmaxtodaywidth)消息,這在 Windows SDK 中介紹。

## <a name="cmonthcalctrlgetminreqrect"></a><a name="getminreqrect"></a>CMonthCalctrl::取得MinReqrect

檢索在月份日曆控件中顯示完整月份所需的最小大小。

```
BOOL GetMinReqRect(RECT* pRect) const;
```

### <a name="parameters"></a>參數

*普雷克*<br/>
指向[RECT](/previous-versions/dd162897\(v=vs.85\))結構的指標,該結構將接收邊界矩形資訊。 此參數必須是有效位址,不能為 NULL。

### <a name="return-value"></a>傳回值

如果成功,此成員函數將返回非零`lpRect`並接收適用的邊界資訊。 如果不成功,成員函數返回 0。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[MCM_GETMINREQRECT](/windows/win32/Controls/mcm-getminreqrect)的行為,如 Windows SDK 中所述。

## <a name="cmonthcalctrlgetmonthdelta"></a><a name="getmonthdelta"></a>CMonthCalctrl::獲取月德爾塔

檢索一個月日曆控件的滾動速率。

```
int GetMonthDelta() const;
```

### <a name="return-value"></a>傳回值

月曆控件的滾動速率。 滾動速率是當用戶單擊滾動按鈕一次時控件移動其顯示的月數。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[MCM_GETMONTHDELTA](/windows/win32/Controls/mcm-getmonthdelta)的行為,如 Windows SDK 中所述。

## <a name="cmonthcalctrlgetmonthrange"></a><a name="getmonthrange"></a>CMonthCalctrl:取得月航程

檢索表示月曆控件顯示的上限和低點的日期資訊。

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
對包含允許的最小日期的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的引用。

*refMaxRange*<br/>
對包含允許的最大`COleDateTime`日期`CTime`的或物件的引用。

*普明朗*<br/>
指向[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標,其中包含範圍最底層的日期。

*pMaxRange*<br/>
指向`SYSTEMTIME`包含範圍最高端日期的結構的指標。

*dwFlags*<br/>
指定要檢索的範圍限制的範圍的值。 此值必須是以下值之一。

|值|意義|
|-----------|-------------|
|GMR_DAYSTATE|包括僅部分顯示的可見範圍的前幾個月和後幾個月。|
|GMR_VISIBLE|僅包括完全顯示的月份。|

### <a name="return-value"></a>傳回值

以月表示範圍的整數,由第一和第二版本中*refMinRange*和*refMaxRange*指示的兩個限制,或第三版本中*的 pMinRange*和*pMaxRange*表示。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[MCM_GETMONTHRANGE](/windows/win32/Controls/mcm-getmonthrange)的行為,如 Windows SDK 中所述。 在 MFC`GetMonthRange`的實現`COleDateTime`中,`CTime`可以指定用`SYSTEMTIME`法、用法 或結構用法。

### <a name="example"></a>範例

  請參考[CMonthCalCtrl 的範例:SetDayState](#setdaystate)。

## <a name="cmonthcalctrlgetrange"></a><a name="getrange"></a>CMonthCalctrl:取得範圍

檢索在月份日曆控件中設置的當前最小和最大日期。

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

*普明朗*<br/>
指向`COleDateTime`物件`CTime`、 物件或[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標,其中包含範圍最底層的日期。

*pMaxRange*<br/>
指向`COleDateTime`物件`CTime`、 物件或[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標,其中包含範圍最高端的日期。

### <a name="return-value"></a>傳回值

可以為零(不設置限制)的 DWORD 或指定限制資訊的以下值的組合。

|值|意義|
|-----------|-------------|
|GDTR_MAX|為控件設置了最大限制;*pMaxRange*有效,包含適用日期資訊。|
|GDTR_MIN|為控件設置了最小限制;*pMinRange*有效,包含適用日期資訊。|

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[MCM_GETRANGE](/windows/win32/Controls/mcm-getrange)的行為,如 Windows SDK 中所述。 在 MFC`GetRange`的 實現`COleDateTime`中,`CTime`可以指定用法`SYSTEMTIME`、用法或 結構用法。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_6.cpp)]

## <a name="cmonthcalctrlgetselrange"></a><a name="getselrange"></a>CMonthCalctrl::GetSelRange

檢索表示使用者當前選擇的日期範圍的上限和下限的日期資訊。

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
對包含允許的最小日期的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的引用。

*refMaxRange*<br/>
對包含允許的最大`COleDateTime`日期`CTime`的或物件的引用。

*普明朗*<br/>
指向[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標,其中包含範圍最底層的日期。

*pMaxRange*<br/>
指向`SYSTEMTIME`包含範圍最高端日期的結構的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[MCM_GETSELRANGE](/windows/win32/Controls/mcm-getselrange)的行為,如 Windows SDK 中所述。 `GetSelRange`如果應用於不使用MCS_MULTISELECT樣式的月曆控件,將失敗。

在 MFC`GetSelRange`的實現`COleDateTime`中,`CTime`可以指定用`SYSTEMTIME`法、用法 或結構用法。

## <a name="cmonthcalctrlgettoday"></a><a name="gettoday"></a>CMonthCalctrl:今天獲取

檢索指定為"今天"的日期的日期資訊,用於一個月的日曆控件。

```
BOOL GetToday(COleDateTime& refDateTime) const;  BOOL GetToday(COleDateTime& refDateTime) const;

BOOL GetToday(LPSYSTEMTIME pDateTime) const;
```

### <a name="parameters"></a>參數

*參考日期時間*<br/>
對指示當前日期的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的引用。

*pDateTime*<br/>
指向將接收日期資訊的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標。 此參數必須是有效位址,不能為 NULL。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[MCM_GETTODAY](/windows/win32/Controls/mcm-gettoday)的行為,如 Windows SDK 中所述。 在 MFC`GetToday`的 實現`COleDateTime`中,`CTime`可以指定用法`SYSTEMTIME`、用法或 結構用法。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_7.cpp)]

## <a name="cmonthcalctrlhittest"></a><a name="hittest"></a>CMonthCalctrl:hitTest

確定哪個月曆控件(如果有)處於指定位置。

```
DWORD HitTest(PMCHITTESTINFO pMCHitTest);
```

### <a name="parameters"></a>參數

*pMCHitTest*<br/>
指向[MCHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-mchittestinfo)結構的指標,其中包含月份日曆控件的熱門測試點。

### <a name="return-value"></a>傳回值

DWORD 值。 等於`MCHITTESTINFO`結構的**uHit**成員。

### <a name="remarks"></a>備註

`HitTest`使用包含`MCHITTESTINFO`測試信息的結構。

## <a name="cmonthcalctrliscenturyview"></a><a name="iscenturyview"></a>CMonthCalctrl:Is世紀檢視

指示當前月曆控件的視圖是否是世紀視圖。

```
BOOL IsCenturyView() const;
```

### <a name="return-value"></a>傳回值

如果當前視圖是世紀視圖,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法發送[MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview)消息,這在 Windows SDK 中介紹。 如果該消息返回MCMV_CENTURY,則此方法返回 TRUE。

## <a name="cmonthcalctrlisdecadeview"></a><a name="isdecadeview"></a>CMonthCalctrl::是十年視圖

指示當前月日曆控件的當前視圖是否是十年視圖。

```
BOOL IsDecadeView() const;
```

### <a name="return-value"></a>傳回值

如果當前視圖是十年視圖,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法發送[MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview)消息,這在 Windows SDK 中介紹。 如果該消息返回MCMV_DECADE,則此方法返回 TRUE。

## <a name="cmonthcalctrlismonthview"></a><a name="ismonthview"></a>CMonthCalctrl::IsMonthView

指示當前月日曆控件的當前視圖是否是月視圖。

```
BOOL IsMonthView() const;
```

### <a name="return-value"></a>傳回值

如果當前檢視是月視圖,則為 TRUE;如果當前視圖為"月視圖",則為 TRUE。否則,FALSE。

### <a name="remarks"></a>備註

此方法發送[MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview)消息,這在 Windows SDK 中介紹。 如果該消息返回MCMV_MONTH,則此方法返回 TRUE。

## <a name="cmonthcalctrlisyearview"></a><a name="isyearview"></a>CMonthCalctrl:isYearView

指示當前月日曆控件的當前檢視是否是年份視圖。

```
BOOL IsYearView() const;
```

### <a name="return-value"></a>傳回值

如果當前視圖是年份視圖,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法發送[MCM_GETCURRENTVIEW](/windows/win32/Controls/mcm-getcurrentview)消息,這在 Windows SDK 中介紹。 如果該消息返回MCMV_YEAR,則此方法返回 TRUE。

## <a name="cmonthcalctrlsetcalendarborder"></a><a name="setcalendarborder"></a>CMonthCalctrl::設定行事曆邊框

設置當前月日曆控件的邊框的寬度。

```
void SetCalendarBorder(int cxyBorder);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*cxy 邊界*|[在]邊框的寬度(以像素為單位)。|

### <a name="remarks"></a>備註

如果此方法成功,邊框寬度將設置為*cxyBorder*參數。 否則,邊框寬度將重置為當前[主題](/windows/win32/Controls/visual-styles-overview)指定的預設值,如果未使用主題,則將重置為零。

此方法發送[MCM_SETCALENDARBORDER](/windows/win32/Controls/mcm-setcalendarborder)消息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

以下代碼範例定義用於以程式設計方式存`m_monthCalCtrl`取 月份行事曆控制的變數 。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>範例

以下代碼示例將月曆控件的邊框寬度設置為 8 圖元。 使用[CMonthCalCtrl::GetCalendarBorder](#getcalendarborder)方法確定此方法是否成功。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_8.cpp)]

## <a name="cmonthcalctrlsetcalendarborderdefault"></a><a name="setcalendarborderdefault"></a>CMonthCalctrl::設定行事曆邊框預設

設置當前月日曆控件邊框的預設寬度。

```
void SetCalendarBorderDefault();
```

### <a name="remarks"></a>備註

邊框寬度設置為當前[主題](/windows/win32/Controls/visual-styles-overview)指定的預設值,如果未使用主題,則為零。

此方法發送[MCM_SETCALENDARBORDER](/windows/win32/Controls/mcm-setcalendarborder)消息,這在 Windows SDK 中介紹。

## <a name="cmonthcalctrlsetcalid"></a><a name="setcalid"></a>CMonthCalctrl::SetCalID

設置當月日曆控件的行事曆標識符。

```
BOOL SetCalID(CALID calid);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*卡利德*|[在][日曆標識符](/windows/win32/Intl/calendar-identifiers)常量之一。|

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

日曆標識符指定特定於區域的日曆,例如公曆(本地化)、日語或 Hijri 日曆。 如果電腦上`SetCalID`安裝了包含日曆的區域設置,則使用方法顯示由*校準*參數指定的日曆。

此方法發送[MCM_SETCALID](/windows/win32/Controls/mcm-setcalid)消息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

以下代碼範例定義用於以程式設計方式存`m_monthCalCtrl`取 月份行事曆控制的變數 。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>範例

以下代碼示例設置月曆控件以顯示日本天皇時代日曆。 僅當`SetCalID`計算機上安裝了該日曆時,該方法才會成功。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_9.cpp)]

## <a name="cmonthcalctrlsetcenturyview"></a><a name="setcenturyview"></a>CMonthCalctrl::設定世紀檢視

設置當前月曆控件以顯示世紀視圖。

```
BOOL SetCenturyView();
```

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法使用[CMonthCalCtrl::SetCurrentView](#setcurrentview)方法將檢視設置`MCMV_CENTURY`為 ,表示世紀視圖。

## <a name="cmonthcalctrlsetcolor"></a><a name="setcolor"></a>CMonthCalctrl::設定顏色

設置月曆控制件的指定區域的顏色。

```
COLORREF SetColor(
    int nRegion,
    COLORREF ref);
```

### <a name="parameters"></a>參數

*n 區域*<br/>
指定要設置的月曆顏色的整數值。 此值可以是以下值之一。

|值|意義|
|-----------|-------------|
|MCSC_BACKGROUND|月份之間顯示的背景顏色。|
|MCSC_MONTHBK|月份內顯示的背景顏色。|
|MCSC_TEXT|用於在一個月內顯示文本的顏色。|
|MCSC_TITLEBK|行事曆標題中顯示的背景顏色。|
|MCSC_TITLETEXT|用於在行事曆標題中顯示文字的顏色。|
|MCSC_TRAILINGTEXT|用於顯示標題和尾隨日文字的顏色。 標題和尾隨日是當前日曆上顯示的前一個月和後幾個月的天數。|

*ref*<br/>
月曆控制件指定部分的新顏色設定的 COLORREF 值。

### <a name="return-value"></a>傳回值

COLORREF 值,表示月份行事曆控制項指定部分的上一個顏色設置(如果成功)。 否則,此消息返回 -1。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[MCM_SETCOLOR](/windows/win32/Controls/mcm-setcolor)的行為,如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_10.cpp)]

## <a name="cmonthcalctrlsetcurrentview"></a><a name="setcurrentview"></a>CMonthCalctrl::設定電流檢視

設置當前月曆控制項以顯示指定的檢視。

```
BOOL SetCurrentView(DWORD dwNewView);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*dwNewView*|[在]指定每月、年度、十年或世紀視圖的以下值之一。<br /><br /> MCMV_MONTH:每月檢視<br /><br /> MCMV_YEAR:年度檢視<br /><br /> MCMV_DECADE:十年視圖<br /><br /> MCMV_CENTURY:世紀景觀|

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法發送[MCM_SETCURRENTVIEW](/windows/win32/Controls/mcm-setcurrentview)消息,這在 Windows SDK 中介紹。

## <a name="cmonthcalctrlsetcursel"></a><a name="setcursel"></a>CMonthCalctrl::SetCurSel

設置月份行事曆控制件的當前選定日期。

```
BOOL SetCurSel(const COleDateTime& refDateTime);
BOOL SetCurSel(const CTime& refDateTime);
BOOL SetCurSel(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>參數

*參考日期時間*<br/>
對指示當前選擇的月份行事曆控制件的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)或[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的引用。

*pDateTime*<br/>
指向包含要設置為當前選擇的日期的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[MCM_SETCURSEL](/windows/win32/Controls/mcm-setcursel)的行為,如 Windows SDK 中所述。 在 MFC`SetCurSel`的 實現`COleDateTime`中,`CTime`可以指定用法`SYSTEMTIME`、用法或 結構用法。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#5](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_11.cpp)]

## <a name="cmonthcalctrlsetdaystate"></a><a name="setdaystate"></a>CMonthCalctrl:setDayState

設置一個月日曆控件中的天數的顯示。

```
BOOL SetDayState(
    int nMonths,
    LPMONTHDAYSTATE pStates);
```

### <a name="parameters"></a>參數

*nmonths*<br/>
指示*pA 指向*的陣列中的元素數的值。

*p國家*<br/>
指向[「月日狀態](/windows/win32/Controls/monthdaystate)」值陣列的指標,用於定義月曆控件每天在顯示中如何繪製。 MonthDAYSTATE 數據類型是位欄位,其中每個位(1 到 31)表示一個月內一天的狀態。 如果位元是開啟的，則對應的日期會以粗體顯示；否則就不會強調其顯示。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[MCM_SETDAYSTATE](/windows/win32/Controls/mcm-setdaystate)的行為,如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_12.cpp)]

## <a name="cmonthcalctrlsetdecadeview"></a><a name="setdecadeview"></a>CMonthCalctrl::設置十年檢視

將當前月曆控件設置到十年視圖。

```
BOOL SetDecadeView();
```

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法使用[CMonthCalCtrl::SetCurrentView](#setcurrentview)方法將檢視設置`MCMV_DECADE`為 ,表示十年視圖。

## <a name="cmonthcalctrlsetfirstdayofweek"></a><a name="setfirstdayofweek"></a>CmonthCalctrl::每周第一天

將要顯示在日曆最左側列中的星期幾。

```
BOOL SetFirstDayOfWeek(
    int iDay,
    int* lpnOld = NULL);
```

### <a name="parameters"></a>參數

*iDay*<br/>
表示將哪一天設置為星期的第一天的整數值。 此值必須是天數之一。 有關日數的說明,請參閱獲取第一[天](#getfirstdayofweek)。

*lpnOld*<br/>
指向一個整數的指標,指示之前設置的一周的第一天。

### <a name="return-value"></a>傳回值

如果星期的前一天設置為LOCALE_IFIRSTDAYOFWEEK的值(控制面板設置中指示的當天)以外的值,則非零。 否則,此函數返回 0。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[的行為MCM_SETFIRSTDAYOFWEEK](/windows/win32/Controls/mcm-setfirstdayofweek),如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_13.cpp)]

## <a name="cmonthcalctrlsetmaxselcount"></a><a name="setmaxselcount"></a>CMonthCalctrl::SetMaxSelCount

設置可在月份日曆控件中選擇的最大天數。

```
BOOL SetMaxSelCount(int nMax);
```

### <a name="parameters"></a>參數

*nMax*<br/>
將設置為表示可選擇天數的最大值。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[MCM_SETMAXSELCOUNT](/windows/win32/Controls/mcm-setmaxselcount)的行為,如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CMonthCalCtrl#8](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_14.cpp)]

## <a name="cmonthcalctrlsetmonthdelta"></a><a name="setmonthdelta"></a>CMonthCalctrl::設置月德爾塔

設置月曆控件的滾動速率。

```
int SetMonthDelta(int iDelta);
```

### <a name="parameters"></a>參數

*iDelta*<br/>
要設置為控制式滾動速率的月數。 如果此值為零,則月份增量將重置為預設值,即控件中顯示的月數。

### <a name="return-value"></a>傳回值

以前的滾動速率。 如果以前未設置滾動速率,則返回值為 0。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[MCM_SETMONTHDELTA](/windows/win32/Controls/mcm-setmonthdelta)的行為,如 Windows SDK 中所述。

## <a name="cmonthcalctrlsetmonthview"></a><a name="setmonthview"></a>CMonthCalctrl::設定月景

設置當前月曆控件以顯示月視圖。

```
BOOL SetMonthView();
```

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法使用[CMonthCalCtrl::SetCurrentView](#setcurrentview)方法將檢視設置為MCMV_MONTH,該視圖表示月視圖。

### <a name="example"></a>範例

以下代碼範例定義用於以程式設計方式存`m_monthCalCtrl`取 月份行事曆控制的變數 。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]

### <a name="example"></a>範例

以下代碼示例將月曆控件設置以顯示月份、年份、十年和世紀視圖。

[!code-cpp[NVC_MFC_CMonthCalCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_15.cpp)]

## <a name="cmonthcalctrlsetrange"></a><a name="setrange"></a>CMonthCalctrl::SetRange

設置月曆控制件的最小和最大允許日期。

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

*普明朗*<br/>
指向`COleDateTime`物件`CTime`、 物件或[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標,其中包含範圍最底層的日期。

*pMaxRange*<br/>
指向`COleDateTime`物件`CTime`、`SYSTEMTIME`物件或 結構的指標,其中包含範圍最高端的日期。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[MCM_SETRANGE](/windows/win32/Controls/mcm-setrange)的行為,如 Windows SDK 中所述。 在 MFC`SetRange`的實現`COleDateTime`中,`CTime`可以指定用`SYSTEMTIME`法、用法 或結構用法。

### <a name="example"></a>範例

  請參考[CMonthCalCtrl 的範例::取得範圍](#getrange)。

## <a name="cmonthcalctrlsetselrange"></a><a name="setselrange"></a>CMonthCalctrl::SetSelRange

將月份日曆控件的選擇設置為給定日期範圍。

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

*普明朗*<br/>
指向`COleDateTime`物件`CTime`、 物件或[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標,其中包含範圍最底層的日期。

*pMaxRange*<br/>
指向`COleDateTime`物件`CTime`、`SYSTEMTIME`物件或 結構的指標,其中包含範圍最高端的日期。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[的行為MCM_SETSELRANGE](/windows/win32/Controls/mcm-setselrange),如 Windows SDK 中所述。 在 MFC`SetSelRange`的實現`COleDateTime`中,`CTime`可以指定用`SYSTEMTIME`法、用法 或結構用法。

## <a name="cmonthcalctrlsettoday"></a><a name="settoday"></a>CMonthCalctrl::今天設置

設置當天的日曆控件。

```
void SetToday(const COleDateTime& refDateTime);
void SetToday(const CTime* pDateTime);
void SetToday(const LPSYSTEMTIME pDateTime);
```

### <a name="parameters"></a>參數

*參考日期時間*<br/>
對包含當前日期的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件的引用。

*pDateTime*<br/>
在第二個版本中,指向包含當前日期資訊的[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的指標。 在第三個版本中,指向包含當前日期資訊的[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[MCM_SETTODAY](/windows/win32/Controls/mcm-settoday)的行為,如 Windows SDK 中所述。

### <a name="example"></a>範例

  請參閱[CMonthCalCtrl 的範例::取得今天](#gettoday)。

## <a name="cmonthcalctrlsetyearview"></a><a name="setyearview"></a>CMonthCalctrl::SetYearView

將當前月日曆控件設置為年視圖。

```
BOOL SetYearView();
```

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法使用[CMonthCalCtrl::SetCurrentView](#setcurrentview)方法將檢視設置為MCMV_YEAR,該視圖表示年度檢視。

## <a name="cmonthcalctrlsizeminreq"></a><a name="sizeminreq"></a>CMonthCalctrl::SizeMinReq

將月曆控制項顯示為顯示一個月的最小大小。

```
BOOL SizeMinReq(BOOL bRepaint = TRUE);
```

### <a name="parameters"></a>參數

*bRepaint*<br/>
指定是否要重新繪製控制件。 預設情況下,TRUE。 如果 FALSE,則不進行重新繪製。

### <a name="return-value"></a>傳回值

如果月曆控件的大小調整到其最小值,則非零;否則 0。

### <a name="remarks"></a>備註

呼叫`SizeMinReq`成功顯示一個月日曆的整個月曆控件。

## <a name="cmonthcalctrlsizerecttomin"></a><a name="sizerecttomin"></a>CmonthCalctrl::大小雷克特明

對於當前月曆控制件,計算可以包含適合指定矩形的所有日曆的最小矩形。

```
LPRECT SizeRectToMin(LPRECT lpRect);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*lpRect*|[在]指向[RECT](/previous-versions/dd162897\(v=vs.85\))結構的指標,該結構定義包含所需行事曆數的矩形。|

### <a name="return-value"></a>傳回值

指向[RECT](/previous-versions/dd162897\(v=vs.85\))結構的指標,該結構定義大小小於或等於*lpRect*參數定義的矩形的矩形。

### <a name="remarks"></a>備註

此方法計算*lpRect*參數指定的矩形中可以容納的日曆數,然後返回可以包含該行曆數的最小矩形。 實際上,此方法收縮指定的矩形以完全適合所需的日曆數。

此方法發送[MCM_SIZERECTTOMIN](/windows/win32/Controls/mcm-sizerecttomin)消息,這在 Windows SDK 中介紹。

## <a name="see-also"></a>另請參閱

[MFC 樣品 CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDateTimeCtrl 類別](../../mfc/reference/cdatetimectrl-class.md)
