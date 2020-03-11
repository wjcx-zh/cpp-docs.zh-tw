---
title: CDateTimeCtrl 類別
ms.date: 11/04/2016
f1_keywords:
- CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl::CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl::CloseMonthCal
- AFXDTCTL/CDateTimeCtrl::Create
- AFXDTCTL/CDateTimeCtrl::GetDateTimePickerInfo
- AFXDTCTL/CDateTimeCtrl::GetIdealSize
- AFXDTCTL/CDateTimeCtrl::GetMonthCalColor
- AFXDTCTL/CDateTimeCtrl::GetMonthCalCtrl
- AFXDTCTL/CDateTimeCtrl::GetMonthCalFont
- AFXDTCTL/CDateTimeCtrl::GetMonthCalStyle
- AFXDTCTL/CDateTimeCtrl::GetRange
- AFXDTCTL/CDateTimeCtrl::GetTime
- AFXDTCTL/CDateTimeCtrl::SetFormat
- AFXDTCTL/CDateTimeCtrl::SetMonthCalColor
- AFXDTCTL/CDateTimeCtrl::SetMonthCalFont
- AFXDTCTL/CDateTimeCtrl::SetMonthCalStyle
- AFXDTCTL/CDateTimeCtrl::SetRange
- AFXDTCTL/CDateTimeCtrl::SetTime
helpviewer_keywords:
- CDateTimeCtrl [MFC], CDateTimeCtrl
- CDateTimeCtrl [MFC], CloseMonthCal
- CDateTimeCtrl [MFC], Create
- CDateTimeCtrl [MFC], GetDateTimePickerInfo
- CDateTimeCtrl [MFC], GetIdealSize
- CDateTimeCtrl [MFC], GetMonthCalColor
- CDateTimeCtrl [MFC], GetMonthCalCtrl
- CDateTimeCtrl [MFC], GetMonthCalFont
- CDateTimeCtrl [MFC], GetMonthCalStyle
- CDateTimeCtrl [MFC], GetRange
- CDateTimeCtrl [MFC], GetTime
- CDateTimeCtrl [MFC], SetFormat
- CDateTimeCtrl [MFC], SetMonthCalColor
- CDateTimeCtrl [MFC], SetMonthCalFont
- CDateTimeCtrl [MFC], SetMonthCalStyle
- CDateTimeCtrl [MFC], SetRange
- CDateTimeCtrl [MFC], SetTime
ms.assetid: 7113993b-5d37-4148-939f-500a190c5bdc
ms.openlocfilehash: ec9060ba60c4d9877e5ee32bc68da0134f0ccf20
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866930"
---
# <a name="cdatetimectrl-class"></a>CDateTimeCtrl 類別

封裝日期與時間選擇器控制項的功能。

## <a name="syntax"></a>語法

```
class CDateTimeCtrl : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CDateTimeCtrl：： CDateTimeCtrl](#cdatetimectrl)|建構 `CDateTimeCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDateTimeCtrl：： CloseMonthCal](#closemonthcal)|關閉目前的日期和時間選擇器控制項。|
|[CDateTimeCtrl：： Create](#create)|建立日期和時間選擇器控制項，並將它附加至 `CDateTimeCtrl` 物件。|
|[CDateTimeCtrl：： GetDateTimePickerInfo](#getdatetimepickerinfo)|抓取目前日期和時間選擇器控制項的相關資訊。|
|[CDateTimeCtrl：： GetIdealSize](#getidealsize)|傳回顯示目前日期或時間所需之日期和時間選擇器控制項的理想大小。|
|[CDateTimeCtrl：： GetMonthCalColor](#getmonthcalcolor)|在日期和時間選擇器控制項內，抓取月曆特定部分的色彩。|
|[CDateTimeCtrl：： GetMonthCalCtrl](#getmonthcalctrl)|抓取與日期和時間選擇器控制項相關聯的 `CMonthCalCtrl` 物件。|
|[CDateTimeCtrl：： GetMonthCalFont](#getmonthcalfont)|抓取日期和時間選擇器控制項的子月曆控制項目前使用的字型。|
|[CDateTimeCtrl：： GetMonthCalStyle](#getmonthcalstyle)|取得目前日期和時間選擇器控制項的樣式。|
|[CDateTimeCtrl：： GetRange](#getrange)|抓取日期和時間選擇器控制項的最小和最大允許系統時間。|
|[CDateTimeCtrl：： GetTime](#gettime)|從日期和時間選擇器控制項抓取目前選取的時間，並將它放在指定的 `SYSTEMTIME` 結構中。|
|[CDateTimeCtrl：： SetFormat](#setformat)|根據指定的格式字串，設定日期和時間選擇器控制項的顯示。|
|[CDateTimeCtrl：： SetMonthCalColor](#setmonthcalcolor)|設定日期和時間選擇器控制項內月曆的特定部分色彩。|
|[CDateTimeCtrl：： SetMonthCalFont](#setmonthcalfont)|設定日期和時間選擇器控制項的子月份行事曆控制項將使用的字型。|
|[CDateTimeCtrl：： SetMonthCalStyle](#setmonthcalstyle)|設定目前日期和時間選擇器控制項的樣式。|
|[CDateTimeCtrl：： SetRange](#setrange)|設定日期和時間選擇器控制項的最小和最大允許系統時間。|
|[CDateTimeCtrl：： SetTime](#settime)|設定日期和時間選擇器控制項中的時間。|

## <a name="remarks"></a>備註

日期和時間選擇器控制項（DTP 控制項）提供了一個簡單的介面，可與使用者交換日期和時間資訊。 此介面包含欄位，其中每一個都會顯示儲存在控制項中的日期和時間資訊的一部分。 使用者可以藉由變更指定欄位中字串的內容，來變更儲存在控制項中的資訊。 使用者可以使用滑鼠或鍵盤，從 [欄位] 移至 [欄位]。

您可以自訂 [日期和時間選擇器] 控制項，其方式是在建立物件時，將各種樣式套用至物件。 如需日期和時間選擇器控制項特定樣式的詳細資訊，請參閱 Windows SDK 中的[日期和時間選擇器控制項樣式](/windows/win32/Controls/date-and-time-picker-control-styles)。 您可以使用格式樣式來設定 DTP 控制項的顯示格式。 這些格式樣式會在 Windows SDK 主題[日期和時間選擇器控制項樣式](/windows/win32/Controls/date-and-time-picker-control-styles)的「格式樣式」下說明。

日期和時間選擇器控制項也會使用通知和回呼，如[使用 CDateTimeCtrl](../../mfc/using-cdatetimectrl.md)中所述。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDateTimeCtrl`

## <a name="requirements"></a>需求

**標頭：** afxdtctl。h

##  <a name="cdatetimectrl"></a>CDateTimeCtrl：： CDateTimeCtrl

建構 `CDateTimeCtrl` 物件。

```
CDateTimeCtrl();
```

##  <a name="closemonthcal"></a>CDateTimeCtrl：： CloseMonthCal

關閉目前的日期和時間選擇器控制項。

```
void CloseMonthCal() const;
```

### <a name="remarks"></a>備註

這個方法會傳送[DTM_CLOSEMONTHCAL](/windows/win32/Controls/dtm-closemonthcal)訊息，如 Windows SDK 所述。

### <a name="example"></a>範例

下列程式碼範例會定義用來以程式設計方式存取日期和時間選擇器控制項的變數*m_dateTimeCtrl*。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>範例

下列程式碼範例會關閉目前日期和時間選擇器控制項的下拉式日曆。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_2.cpp)]

##  <a name="create"></a>CDateTimeCtrl：： Create

建立日期和時間選擇器控制項，並將它附加至 `CDateTimeCtrl` 物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定日期時間控制項樣式的組合。 如需日期和時間選擇器樣式的詳細資訊，請參閱 Windows SDK 中的[日期和時間選擇器控制項樣式](/windows/win32/Controls/date-and-time-picker-control-styles)。

*各種*<br/>
[RECT](/previous-versions/dd162897\(v=vs.85\))結構的參考，這是日期和時間選擇器控制項的位置和大小。

*pParentWnd*<br/>
[CWnd](../../mfc/reference/cwnd-class.md)物件的指標，這是日期和時間選擇器控制項的父視窗。 它不得為 NULL。

*nID*<br/>
指定日期和時間選擇器控制項的控制項 ID。

### <a name="return-value"></a>傳回值

如果建立成功則為非零;否則為0。

### <a name="remarks"></a>備註

##### <a name="to-create-a-date-and-time-picker-control"></a>建立日期和時間選擇器控制項

1. 呼叫[CDateTimeCtrl](#cdatetimectrl)來建立 `CDateTimeCtrl` 物件。

1. 呼叫這個成員函式，它會建立 Windows 日期和時間選擇器控制項，並將它附加至 `CDateTimeCtrl` 物件。

當您呼叫 `Create`時，會初始化通用控制項。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CDateTimeCtrl#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_3.cpp)]

##  <a name="getdatetimepickerinfo"></a>CDateTimeCtrl：： GetDateTimePickerInfo

抓取目前日期和時間選擇器控制項的相關資訊。

```
BOOL GetDateTimePickerInfo(LPDATETIMEPICKERINFO pDateTimePickerInfo) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*pDateTimePickerInfo*|脫銷[DATETIMEPICKERINFO](/windows/win32/api/commctrl/ns-commctrl-datetimepickerinfo)結構的指標，它會接收目前日期和時間選擇器控制項的描述。<br /><br /> 呼叫端負責配置這個結構。 不過，這個方法會初始化結構的*cbSize*成員。|

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[DTM_GETDATETIMEPICKERINFO](/windows/win32/Controls/dtm-getdatetimepickerinfo)訊息，如 Windows SDK 所述。

### <a name="example"></a>範例

下列程式碼範例會定義用來以程式設計方式存取日期和時間選擇器控制項的變數*m_dateTimeCtrl*。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>範例

下列程式碼範例會指出它是否能成功地抓取目前日期和時間選擇器控制項的相關資訊。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_4.cpp)]

##  <a name="getmonthcalcolor"></a>CDateTimeCtrl：： GetMonthCalColor

在日期和時間選擇器控制項內，抓取月曆特定部分的色彩。

```
COLORREF GetMonthCalColor(int iColor) const;
```

### <a name="parameters"></a>參數

*iColor*<br/>
**Int**值，指定要抓取之月曆的哪一個色彩區域。 如需值清單，請參閱[SetMonthCalColor](#setmonthcalcolor)的*iColor*參數。

### <a name="return-value"></a>傳回值

COLORRE光圈值，代表月曆控制項指定部分的色彩設定（如果成功的話）。 如果失敗，此函式會傳回-1。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 中的說明，實作用[DTM_GETMCCOLOR](/windows/win32/Controls/dtm-getmccolor)Win32 訊息的行為。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CDateTimeCtrl#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_5.cpp)]

##  <a name="getmonthcalctrl"></a>CDateTimeCtrl：： GetMonthCalCtrl

抓取與日期和時間選擇器控制項相關聯的 `CMonthCalCtrl` 物件。

```
CMonthCalCtrl* GetMonthCalCtrl() const;
```

### <a name="return-value"></a>傳回值

[CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)物件的指標，如果不成功或視窗不是可見的，則為 Null。

### <a name="remarks"></a>備註

日期和時間選擇器控制項會在使用者按一下下拉箭號時，建立一個月曆控制項。 當不再需要 `CMonthCalCtrl` 物件時，就會終結它，因此您的應用程式不能依賴儲存代表日期時間選擇器控制項之子月份行事曆的物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CDateTimeCtrl#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_6.cpp)]

##  <a name="getmonthcalfont"></a>CDateTimeCtrl：： GetMonthCalFont

取得日期和時間選擇器控制項的月曆控制項目前使用的字型。

```
CFont* GetMonthCalFont() const;
```

### <a name="return-value"></a>傳回值

[CFont](../../mfc/reference/cfont-class.md)物件的指標，如果不成功則為 Null。

### <a name="remarks"></a>備註

傳回值所指向的 `CFont` 物件是暫存物件，並在下一個空閒處理時間終結。

##  <a name="getmonthcalstyle"></a>CDateTimeCtrl：： GetMonthCalStyle

取得與目前日期和時間選擇器控制項相關聯之下拉式月曆控制項的樣式。

```
DWORD GetMonthCalStyle() const;
```

### <a name="return-value"></a>傳回值

下拉式月曆控制項的樣式，這是日期和時間選擇器控制項樣式的位元組合（OR）。 如需詳細資訊，請參閱[月曆控制項樣式](/windows/win32/Controls/month-calendar-control-styles)。

### <a name="remarks"></a>備註

這個方法會傳送[DTM_GETMCSTYLE](/windows/win32/Controls/dtm-getmcstyle)訊息，如 Windows SDK 所述。

##  <a name="getrange"></a>CDateTimeCtrl：： GetRange

抓取日期和時間選擇器控制項的最小和最大允許系統時間。

```
DWORD GetRange(
    COleDateTime* pMinRange,
    COleDateTime* pMaxRange) const;

DWORD GetRange(
    CTime* pMinRange,
    CTime* pMaxRange) const;
```

### <a name="parameters"></a>參數

*pMinRange*<br/>
[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件或[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的指標，其中包含 `CDateTimeCtrl` 物件中允許的最早時間。

*pMaxRange*<br/>
`COleDateTime` 物件或 `CTime` 物件的指標，其中包含 `CDateTimeCtrl` 物件中允許的最新時間。

### <a name="return-value"></a>傳回值

DWORD 值，其中包含表示已設定之範圍的旗標。 If

`return value & GDTR_MAX` == 0

然後第二個參數是有效的。 同樣地，如果

`return value & GDTR_MIN` == 0

然後第一個參數有效。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 中的說明，實作用[DTM_GETRANGE](/windows/win32/Controls/dtm-getrange)Win32 訊息的行為。 在 MFC 的執行中，您可以指定 `COleDateTime` 或 `CTime` 使用方式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CDateTimeCtrl#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_7.cpp)]

##  <a name="gettime"></a>CDateTimeCtrl：： GetTime

從日期和時間選擇器控制項抓取目前選取的時間，並將它放在指定的 `SYSTEMTIME` 結構中。

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>參數

*timeDest*<br/>
在第一個版本中，是[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件的參考，將會接收系統時間資訊。 在第二個版本中，是會接收系統時間資訊之[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的參考。

*pTimeDest*<br/>
要接收系統時間資訊之[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標。 不得為 Null。

### <a name="return-value"></a>傳回值

在第一個版本中，如果已成功將時間寫入 `COleDateTime` 物件，則為非零。否則為0。 在第二個和第三個版本中，DWORD 值等於[NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange)結構中所設定的*dwFlag*成員。 如需詳細資訊，請參閱下面的「**備註**」一節。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 中的說明，實作用[DTM_GETSYSTEMTIME](/windows/win32/Controls/dtm-getsystemtime)Win32 訊息的行為。 在 `GetTime`的 MFC 執行中，您可以使用 `COleDateTime` 或 `CTime` 類別，也可以使用 `SYSTEMTIME` 結構來儲存時間資訊。

上述第二個和第三個版本中的傳回值 DWORD 會指出日期和時間選擇器控制項是否設定為「沒有日期」狀態，如[NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange)結構成員*dwFlags*中所示。 如果傳回的值等於 GDT_NONE，則控制項會設定為「沒有日期」狀態，並使用 DTS_SHOWNONE 樣式。 如果傳回的值等於 GDT_VALID，系統時間就會成功地儲存在目的地位置。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CDateTimeCtrl#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_8.cpp)]

##  <a name="getidealsize"></a>CDateTimeCtrl：： GetIdealSize

傳回顯示目前日期或時間所需之日期和時間選擇器控制項的理想大小。

```
BOOL GetIdealSize(LPSIZE psize) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*psize*|脫銷[大小](/windows/win32/api/windef/ns-windef-size)結構的指標，其中包含控制項的理想大小。|

### <a name="return-value"></a>傳回值

傳回值一律為 TRUE。

### <a name="remarks"></a>備註

這個方法會傳送[DTM_GETIDEALSIZE](/windows/win32/Controls/dtm-getidealsize)訊息，如 Windows SDK 所述。

### <a name="example"></a>範例

下列程式碼範例會定義用來以程式設計方式存取日期和時間選擇器控制項的變數*m_dateTimeCtrl*。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>範例

下列程式碼範例會抓取理想的大小，以顯示日期和時間選擇器控制項。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_9.cpp)]

##  <a name="setformat"></a>CDateTimeCtrl：： SetFormat

根據指定的格式字串，設定日期和時間選擇器控制項的顯示。

```
BOOL SetFormat(LPCTSTR pstrFormat);
```

### <a name="parameters"></a>參數

*pstrFormat*<br/>
以零結束的格式字串指標，定義所需的顯示。 將此參數設定為 Null 會將控制項重設為目前樣式的預設格式字串。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

> [!NOTE]
>  使用者輸入不會判斷此呼叫的成功或失敗。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 中的說明，實作用[DTM_SETFORMAT](/windows/win32/Controls/dtm-setformat)Win32 訊息的行為。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CDateTimeCtrl#6](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_10.cpp)]

##  <a name="setmonthcalcolor"></a>CDateTimeCtrl：： SetMonthCalColor

設定日期和時間選擇器控制項內月曆的特定部分色彩。

```
COLORREF SetMonthCalColor(
    int iColor,
    COLORREF ref);
```

### <a name="parameters"></a>參數

*iColor*<br/>
**int**值，指定要設定的月曆控制項的哪個區域。 這個值可以是下列其中一項。

|值|意義|
|-----------|-------------|
|MCSC_BACKGROUND|設定顯示月份之間的背景色彩。|
|MCSC_MONTHBK|設定顯示在一個月內的背景色彩。|
|MCSC_TEXT|設定用來在一個月內顯示文字的色彩。|
|MCSC_TITLEBK|設定顯示在行事曆標題中的背景色彩。|
|MCSC_TITLETEXT|設定用來在行事曆標題中顯示文字的色彩。|
|MCSC_TRAILINGTEXT|設定用來顯示標頭和尾端日期文字的色彩。 [標頭] 和 [尾端天數] 是在目前行事曆上出現的過去和之後幾天。|

*ref*<br/>
COLORRE光圈值，代表將針對月曆的指定區域設定的色彩。

### <a name="return-value"></a>傳回值

COLORRE光圈值，代表月曆控制項指定部分的上一個色彩設定（如果成功的話）。 否則，訊息會傳回-1。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 中的說明，實作用[DTM_SETMCCOLOR](/windows/win32/Controls/dtm-setmccolor)Win32 訊息的行為。

### <a name="example"></a>範例

  請參閱[CDateTimeCtrl：： GetMonthCalColor](#getmonthcalcolor)的範例。

##  <a name="setmonthcalfont"></a>CDateTimeCtrl：： SetMonthCalFont

設定日期和時間選擇器控制項的子月份行事曆控制項將使用的字型。

```
void SetMonthCalFont(
    HFONT hFont,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>參數

*hFont*<br/>
將設定之字型的控制碼。

*bRedraw*<br/>
指定是否應該在設定字型時立即重新繪製控制項。 將此參數設定為 TRUE 會導致控制項自行重繪。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 中的說明，實作用[DTM_SETMCFONT](/windows/win32/Controls/dtm-setmcfont)Win32 訊息的行為。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CDateTimeCtrl#7](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_11.cpp)]

> [!NOTE]
>  如果您使用此程式碼，您會想要將 `CDialog`衍生類別的成員，稱為*m_MonthFont*類型 `CFont`。

##  <a name="setmonthcalstyle"></a>CDateTimeCtrl：： SetMonthCalStyle

設定與目前日期和時間選擇器控制項相關聯之下拉式月曆控制項的樣式。

```
DWORD SetMonthCalStyle(DWORD dwStyle);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*dwStyle*|在新的月曆控制項樣式，這是月曆控制項樣式的位合（OR）。 如需詳細資訊，請參閱[月曆控制項樣式](/windows/win32/Controls/month-calendar-control-styles)。|

### <a name="return-value"></a>傳回值

下拉式月曆控制項的上一個樣式。

### <a name="remarks"></a>備註

這個方法會傳送[DTM_SETMCSTYLE](/windows/win32/Controls/dtm-setmcstyle)訊息，如 Windows SDK 所述。

### <a name="example"></a>範例

下列程式碼範例會定義用來以程式設計方式存取日期和時間選擇器控制項的變數*m_dateTimeCtrl*。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>範例

下列程式碼範例會設定日期和時間選擇器控制項，以顯示周數、星期幾的縮寫名稱，以及目前的指標。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_12.cpp)]

##  <a name="setrange"></a>CDateTimeCtrl：： SetRange

設定日期和時間選擇器控制項的最小和最大允許系統時間。

```
BOOL SetRange(
    const COleDateTime* pMinRange,
    const COleDateTime* pMaxRange);

BOOL SetRange(
    const CTime* pMinRange,
    const CTime* pMaxRange);
```

### <a name="parameters"></a>參數

*pMinRange*<br/>
[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件或[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的指標，其中包含 `CDateTimeCtrl` 物件中允許的最早時間。

*pMaxRange*<br/>
`COleDateTime` 物件或 `CTime` 物件的指標，其中包含 `CDateTimeCtrl` 物件中允許的最新時間。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 中的說明，實作用[DTM_SETRANGE](/windows/win32/Controls/dtm-setrange)Win32 訊息的行為。 在 MFC 的執行中，您可以指定 `COleDateTime` 或 `CTime` 使用方式。 如果 `COleDateTime` 物件的狀態為 Null，則會移除範圍。 如果 `CTime` 指標或 `COleDateTime` 指標是 Null，則會移除範圍。

### <a name="example"></a>範例

  請參閱[CDateTimeCtrl：： GetRange](#getrange)的範例。

##  <a name="settime"></a>CDateTimeCtrl：： SetTime

設定日期和時間選擇器控制項中的時間。

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* pTimeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew = NULL);
```

### <a name="parameters"></a>參數

*timeNew*<br/>
[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件的參考，其中包含將設定控制項的。

*pTimeNew*<br/>
在上述的第二個版本中，包含將設定控制項之時間的[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件指標。 在上述的第三個版本中， [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標，其中包含將設定控制項的時間。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 中的說明，實作用[DTM_SETSYSTEMTIME](/windows/win32/Controls/dtm-setsystemtime)Win32 訊息的行為。 在 `SetTime`的 MFC 執行中，您可以使用 `COleDateTime` 或 `CTime` 類別，也可以使用 `SYSTEMTIME` 結構來設定時間資訊。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CDateTimeCtrl#8](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_13.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CMonthCalCtrl 類別](../../mfc/reference/cmonthcalctrl-class.md)
