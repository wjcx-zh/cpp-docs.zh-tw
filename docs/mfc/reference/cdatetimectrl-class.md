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
ms.openlocfilehash: 5acac454bd0b22b994b74a052bd3cf0b0eee2614
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54894337"
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
|[CDateTimeCtrl::CDateTimeCtrl](#cdatetimectrl)|建構 `CDateTimeCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDateTimeCtrl::CloseMonthCal](#closemonthcal)|關閉目前的日期和時間選擇器控制項。|
|[CDateTimeCtrl::Create](#create)|建立日期和時間選擇器控制項，並將它附加至`CDateTimeCtrl`物件。|
|[CDateTimeCtrl::GetDateTimePickerInfo](#getdatetimepickerinfo)|擷取目前的日期和時間選擇器控制項的相關資訊。|
|[CDateTimeCtrl::GetIdealSize](#getidealsize)|傳回，才可顯示目前的日期或時間的日期和時間選擇器控制項的理想大小。|
|[CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor)|擷取月份行事曆的日期和時間選擇器控制項中的某一部分的色彩。|
|[CDateTimeCtrl::GetMonthCalCtrl](#getmonthcalctrl)|擷取`CMonthCalCtrl`與日期和時間選擇器控制項關聯的物件。|
|[CDateTimeCtrl::GetMonthCalFont](#getmonthcalfont)|擷取目前的日期和時間選擇器控制項的子系月曆控制項所使用的字型。|
|[CDateTimeCtrl::GetMonthCalStyle](#getmonthcalstyle)|取得目前的日期和時間選擇器控制項的樣式。|
|[CDateTimeCtrl::GetRange](#getrange)|擷取目前的最小和最大允許的日期和時間選擇器控制項的系統時間。|
|[CDateTimeCtrl::GetTime](#gettime)|擷取日期和時間選擇器控制項中目前選取的時間，並將它放在指定的`SYSTEMTIME`結構。|
|[CDateTimeCtrl::SetFormat](#setformat)|設定符合指定的格式字串的日期和時間選擇器控制項的顯示方式。|
|[CDateTimeCtrl::SetMonthCalColor](#setmonthcalcolor)|設定月曆的日期和時間選擇器控制項內的某一部分的色彩。|
|[CDateTimeCtrl::SetMonthCalFont](#setmonthcalfont)|設定日期和時間選擇器控制項的子系月曆控制項將使用的字型。|
|[CDateTimeCtrl::SetMonthCalStyle](#setmonthcalstyle)|將目前的日期和時間選擇器控制項的樣式設定。|
|[CDateTimeCtrl::SetRange](#setrange)|設定日期和時間選擇器控制項的最小和最大允許的系統時間。|
|[CDateTimeCtrl::SetTime](#settime)|日期和時間選擇器控制項中設定的時間。|

## <a name="remarks"></a>備註

日期和時間選擇器控制項 （DTP 控制項） 提供簡單的介面，用來交換與使用者的日期和時間資訊。 這個介面包含的欄位，其中每一個會顯示儲存在控制項的日期和時間資訊的一部分。 使用者可以變更藉由變更的內容中指定的欄位的字串儲存在控制項中的資訊。 使用者可以移動欄位的使用滑鼠或鍵盤。

您可以將各種不同的樣式套用至物件，當您在建立時，自訂日期和時間選擇器控制項。 請參閱[日期和時間選擇器控制項樣式](/windows/desktop/Controls/date-and-time-picker-control-styles)Windows SDK 中針對特定日期和時間選擇器控制項的樣式的詳細資訊。 您可以設定使用的格式樣式 DTP 控制項的顯示格式。 這些格式樣式會在 「 格式樣式 」 Windows SDK > 主題所述[日期和時間選擇器控制項樣式](/windows/desktop/Controls/date-and-time-picker-control-styles)。

日期和時間選擇器控制項也會使用通知和所述的回呼[使用 CDateTimeCtrl](../../mfc/using-cdatetimectrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDateTimeCtrl`

## <a name="requirements"></a>需求

**標頭：** afxdtctl.h

##  <a name="cdatetimectrl"></a>  CDateTimeCtrl::CDateTimeCtrl

建構 `CDateTimeCtrl` 物件。

```
CDateTimeCtrl();
```

##  <a name="closemonthcal"></a>  CDateTimeCtrl::CloseMonthCal

關閉目前的日期和時間選擇器控制項。

```
void CloseMonthCal() const;
```

### <a name="remarks"></a>備註

這個方法會傳送[DTM_CLOSEMONTHCAL](/windows/desktop/Controls/dtm-closemonthcal)訊息，Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義變數*m_dateTimeCtrl*，也就是用來以程式設計方式存取 日期和時間選擇器控制項。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>範例

下列程式碼範例會關閉目前的日期和時間選擇器控制項的下拉式月曆。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_2.cpp)]

##  <a name="create"></a>  CDateTimeCtrl::Create

建立日期和時間選擇器控制項，並將它附加至`CDateTimeCtrl`物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定日期時間控制項的樣式的組合。 請參閱[日期和時間選擇器控制項樣式](/windows/desktop/Controls/date-and-time-picker-control-styles)日期和時間選擇器樣式的詳細資訊的 Windows SDK 中。

*rect*<br/>
參考[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構，也就是日期和時間選擇器控制項的大小與位置。

*pParentWnd*<br/>
指標[CWnd](../../mfc/reference/cwnd-class.md)是日期和時間選擇器控制項的父視窗的物件。 它必須不是 NULL。

*nID*<br/>
指定日期和時間選擇器控制項的控制項 id。

### <a name="return-value"></a>傳回值

非零值，如果建立成功;否則為 0。

### <a name="remarks"></a>備註

##### <a name="to-create-a-date-and-time-picker-control"></a>若要建立的日期和時間選擇器控制項

1. 呼叫[CDateTimeCtrl](#cdatetimectrl)建構`CDateTimeCtrl`物件。

1. 呼叫此成員函式，會建立 Windows 日期和時間選擇器控制項，並將它附加至`CDateTimeCtrl`物件。

當您呼叫`Create`，常見的控制項都已初始化。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CDateTimeCtrl#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_3.cpp)]

##  <a name="getdatetimepickerinfo"></a>  CDateTimeCtrl::GetDateTimePickerInfo

擷取目前的日期和時間選擇器控制項的相關資訊。

```
BOOL GetDateTimePickerInfo(LPDATETIMEPICKERINFO pDateTimePickerInfo) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*pDateTimePickerInfo*|[out]指標[DATETIMEPICKERINFO](/windows/desktop/api/commctrl/ns-commctrl-tagdatetimepickerinfo)接收的目前日期和時間選擇器控制項描述的結構。<br /><br /> 呼叫端會負責配置這個結構。 不過，這個方法會初始化*cbSize*結構成員。|

### <a name="return-value"></a>傳回值

如果成功，這個方法，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[DTM_GETDATETIMEPICKERINFO](/windows/desktop/Controls/dtm-getdatetimepickerinfo)訊息，Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義變數*m_dateTimeCtrl*，也就是用來以程式設計方式存取 日期和時間選擇器控制項。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>範例

下列程式碼範例指出它是否已成功擷取目前的日期和時間選擇器控制項的相關資訊。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_4.cpp)]

##  <a name="getmonthcalcolor"></a>  CDateTimeCtrl::GetMonthCalColor

擷取月份行事曆的日期和時間選擇器控制項中的某一部分的色彩。

```
COLORREF GetMonthCalColor(int iColor) const;
```

### <a name="parameters"></a>參數

*iColor*<br/>
**Int**值，指定要擷取的月份行事曆的色彩區域。 如需值的清單，請參閱 < *iColor*參數[SetMonthCalColor](#setmonthcalcolor)。

### <a name="return-value"></a>傳回值

COLORREF 值，表示月曆控制項如果是成功的指定部分的色彩設定。 如果不成功，函式會傳回-1。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[DTM_GETMCCOLOR](/windows/desktop/Controls/dtm-getmccolor)、 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CDateTimeCtrl#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_5.cpp)]

##  <a name="getmonthcalctrl"></a>  CDateTimeCtrl::GetMonthCalCtrl

擷取`CMonthCalCtrl`與日期和時間選擇器控制項關聯的物件。

```
CMonthCalCtrl* GetMonthCalCtrl() const;
```

### <a name="return-value"></a>傳回值

指標[CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)物件，則為 NULL 如果不成功，或如果看不到視窗。

### <a name="remarks"></a>備註

日期和時間選擇器控制項建立子月曆控制項，當使用者按一下下拉箭號。 當`CMonthCalCtrl`不再需要物件、 被損毀，因此您的應用程式必須不依賴儲存物件，表示日期時間選擇器控制項的子系月份的行事曆。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CDateTimeCtrl#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_6.cpp)]

##  <a name="getmonthcalfont"></a>  CDateTimeCtrl::GetMonthCalFont

取得目前的日期和時間選擇器控制項的月曆控制項所使用的字型。

```
CFont* GetMonthCalFont() const;
```

### <a name="return-value"></a>傳回值

指標[CFont](../../mfc/reference/cfont-class.md)物件，或如果不成功則為 NULL。

### <a name="remarks"></a>備註

`CFont`傳回的值所指向的物件是暫存物件，並在下一步 的閒置處理期間終結。

##  <a name="getmonthcalstyle"></a>  CDateTimeCtrl::GetMonthCalStyle

取得下拉式月曆控制項與目前的日期和時間選擇器控制項相關聯的樣式。

```
DWORD GetMonthCalStyle() const;
```

### <a name="return-value"></a>傳回值

樣式的下拉式月曆控制項，也就是位元合併組成 （或者） 的日期和時間選擇器控制項的樣式。 如需詳細資訊，請參閱 <<c0> [ 月份的行事曆控制項樣式](/windows/desktop/Controls/month-calendar-control-styles)。

### <a name="remarks"></a>備註

這個方法會傳送[DTM_GETMCSTYLE](/windows/desktop/Controls/dtm-getmcstyle)訊息，Windows SDK 中所述。

##  <a name="getrange"></a>  CDateTimeCtrl::GetRange

擷取目前的最小和最大允許的日期和時間選擇器控制項的系統時間。

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
指標[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件或[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件，包含在允許的最早時間`CDateTimeCtrl`物件。

*pMaxRange*<br/>
指標`COleDateTime`物件或`CTime`物件，包含在允許的最新時間`CDateTimeCtrl`物件。

### <a name="return-value"></a>傳回值

包含旗標，表示哪些範圍已設定的 DWORD 值。 如果

`return value & GDTR_MAX` == 0

然後第二個參數才有效。 同樣地，如果

`return value & GDTR_MIN` == 0

然後第一個參數是有效的。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[DTM_GETRANGE](/windows/desktop/Controls/dtm-getrange)、 Windows SDK 中所述。 在 MFC 的實作中，您可以指定`COleDateTime`或`CTime`使用方式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CDateTimeCtrl#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_7.cpp)]

##  <a name="gettime"></a>  CDateTimeCtrl::GetTime

擷取日期和時間選擇器控制項中目前選取的時間，並將它放在指定的`SYSTEMTIME`結構。

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>參數

*timeDest*<br/>
在第一個版本中，參考[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)會收到系統時間資訊的物件。 在第二個版本中，參考[CTime](../../atl-mfc-shared/reference/ctime-class.md)會收到系統時間資訊的物件。

*pTimeDest*<br/>
指標[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)接收系統時間資訊的結構。 必須不是 NULL。

### <a name="return-value"></a>傳回值

在第一個版本中，如果已成功寫入時間為非零`COleDateTime`物件; 否則為 0。 在第二個和第三個版本中，DWORD 值等於*dwFlag*成員集中[NMDATETIMECHANGE](/windows/desktop/api/commctrl/ns-commctrl-tagnmdatetimechange)結構。 請參閱**備註**如需詳細資訊，如下一節。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[DTM_GETSYSTEMTIME](/windows/desktop/Controls/dtm-getsystemtime)、 Windows SDK 中所述。 中的 MFC 實作`GetTime`，您可以使用`COleDateTime`或是`CTime`類別，或者您可以使用`SYSTEMTIME`結構，來儲存時間資訊。

傳回的 DWORD 值的第二個和第三個版本中，以上所述，指出是否要將日期和時間選擇器控制項設為 「 沒有日期 」 狀態，如所示[NMDATETIMECHANGE](/windows/desktop/api/commctrl/ns-commctrl-tagnmdatetimechange)結構成員*dwFlags*. 如果傳回的值等於 GDT_NONE，控制項就會設為 「 沒有日期 」 狀態，並使用 DTS_SHOWNONE 樣式。 如果傳回的值等於 GDT_VALID，系統時間已成功儲存中的目的地位置。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CDateTimeCtrl#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_8.cpp)]

##  <a name="getidealsize"></a>  CDateTimeCtrl::GetIdealSize

傳回，才可顯示目前的日期或時間的日期和時間選擇器控制項的理想大小。

```
BOOL GetIdealSize(LPSIZE psize) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*psize*|[out]指標[大小](/windows/desktop/api/windef/ns-windef-tagsize)結構，包含控制項的理想大小。|

### <a name="return-value"></a>傳回值

傳回值永遠是 TRUE。

### <a name="remarks"></a>備註

這個方法會傳送[DTM_GETIDEALSIZE](/windows/desktop/Controls/dtm-getidealsize)訊息，Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義變數*m_dateTimeCtrl*，也就是用來以程式設計方式存取 日期和時間選擇器控制項。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>範例

下列程式碼範例會擷取要顯示日期和時間選擇器控制項的理想大小。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_9.cpp)]

##  <a name="setformat"></a>  CDateTimeCtrl::SetFormat

設定符合指定的格式字串的日期和時間選擇器控制項的顯示方式。

```
BOOL SetFormat(LPCTSTR pstrFormat);
```

### <a name="parameters"></a>參數

*pstrFormat*<br/>
定義所要的顯示為零結束之格式字串的指標。 將此參數設定為 NULL，將控制項重設目前的樣式的預設格式字串。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

> [!NOTE]
>  使用者輸入不會判斷成功或失敗，此呼叫。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[DTM_SETFORMAT](/windows/desktop/Controls/dtm-setformat)、 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CDateTimeCtrl#6](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_10.cpp)]

##  <a name="setmonthcalcolor"></a>  CDateTimeCtrl::SetMonthCalColor

設定月曆的日期和時間選擇器控制項內的某一部分的色彩。

```
COLORREF SetMonthCalColor(
    int iColor,
    COLORREF ref);
```

### <a name="parameters"></a>參數

*iColor*<br/>
**int**值，指定設定月曆控制項的區域。 這個值可以是下列其中一個項目。

|值|意義|
|-----------|-------------|
|MCSC_BACKGROUND|設定月份間所顯示的背景色彩。|
|MCSC_MONTHBK|設定顯示在一個月內的背景色彩。|
|MCSC_TEXT|設定用來在一個月內顯示的文字色彩。|
|MCSC_TITLEBK|設定行事曆的標題中顯示的背景色彩。|
|MCSC_TITLETEXT|設定用來顯示行事曆的標題中文字的色彩。|
|MCSC_TRAILINGTEXT|設定用來顯示標頭和結尾的一天的文字色彩。 標頭和結尾的日期是目前行事曆會出現前面和後面幾個月的天數。|

*ref*<br/>
COLORREF 值，表示將月份行事曆的指定區域的色彩。

### <a name="return-value"></a>傳回值

COLORREF 值，表示月曆控制項如果是成功的指定部分的上一個色彩設定。 否則，訊息會傳回-1。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[DTM_SETMCCOLOR](/windows/desktop/Controls/dtm-setmccolor)、 Windows SDK 中所述。

### <a name="example"></a>範例

  範例，請參閱[CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor)。

##  <a name="setmonthcalfont"></a>  CDateTimeCtrl::SetMonthCalFont

設定日期和時間選擇器控制項的子系月曆控制項將使用的字型。

```
void SetMonthCalFont(
    HFONT hFont,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>參數

*hFont*<br/>
將字型的控制代碼。

*bRedraw*<br/>
指定是否在控制項必須重繪立即時設定的字型。 將此參數設定為 TRUE，會使控制項重繪其本身。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[DTM_SETMCFONT](/windows/desktop/Controls/dtm-setmcfont)、 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CDateTimeCtrl#7](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_11.cpp)]

> [!NOTE]
>  如果您使用此程式碼時，您會想要的成員您`CDialog`-衍生的類別稱為*m_MonthFont*型別的`CFont`。

##  <a name="setmonthcalstyle"></a>  CDateTimeCtrl::SetMonthCalStyle

設定下拉式月曆控制項與目前的日期和時間選擇器控制項相關聯的樣式。

```
DWORD SetMonthCalStyle(DWORD dwStyle);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*dwStyle*|[in]新的月份行事曆月份行事曆控制項樣式位元結合 (OR) 的控制項樣式。 如需詳細資訊，請參閱 <<c0> [ 月份的行事曆控制項樣式](/windows/desktop/Controls/month-calendar-control-styles)。|

### <a name="return-value"></a>傳回值

下拉式月曆控制項先前的樣式。

### <a name="remarks"></a>備註

這個方法會傳送[DTM_SETMCSTYLE](/windows/desktop/Controls/dtm-setmcstyle)訊息，Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義變數*m_dateTimeCtrl*，也就是用來以程式設計方式存取 日期和時間選擇器控制項。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>範例

下列程式碼範例會設定日期和時間選擇器控制項來顯示週數字、 縮寫名稱的一週，和任何今日的指標。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_12.cpp)]

##  <a name="setrange"></a>  CDateTimeCtrl::SetRange

設定日期和時間選擇器控制項的最小和最大允許的系統時間。

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
指標[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件或[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件，包含在允許的最早時間`CDateTimeCtrl`物件。

*pMaxRange*<br/>
指標`COleDateTime`物件或`CTime`物件，包含在允許的最新時間`CDateTimeCtrl`物件。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[DTM_SETRANGE](/windows/desktop/Controls/dtm-setrange)、 Windows SDK 中所述。 在 MFC 的實作中，您可以指定`COleDateTime`或`CTime`使用方式。 如果`COleDateTime`物件具有 NULL 狀態，將會移除範圍。 如果`CTime`指標或`COleDateTime`指標為 NULL，會移除範圍。

### <a name="example"></a>範例

  範例，請參閱[CDateTimeCtrl::GetRange](#getrange)。

##  <a name="settime"></a>  CDateTimeCtrl::SetTime

日期和時間選擇器控制項中設定的時間。

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* pTimeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew = NULL);
```

### <a name="parameters"></a>參數

*timeNew*<br/>
參考[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件，包含控制項設定。

*pTimeNew*<br/>
在第二個版本以上的指標[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件，包含控制項設定的時間。 在第三個版本以上的指標[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)結構，包含控制項設定的時間。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[DTM_SETSYSTEMTIME](/windows/desktop/Controls/dtm-setsystemtime)、 Windows SDK 中所述。 中的 MFC 實作`SetTime`，您可以使用`COleDateTime`或是`CTime`類別，或者您可以使用`SYSTEMTIME`結構，來設定的時間資訊。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CDateTimeCtrl#8](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_13.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 CMNCTRL1](../../visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CMonthCalCtrl 類別](../../mfc/reference/cmonthcalctrl-class.md)
