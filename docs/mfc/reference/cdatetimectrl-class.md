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
ms.openlocfilehash: d0433507c32c7359f8033836bf845defa8ad7f7a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321906"
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
|[CDateTimeCtrl::CDatetimeCtrl](#cdatetimectrl)|建構 `CDateTimeCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDateTimeCtrl::關閉月卡爾](#closemonthcal)|關閉當前日期和時間選取器控制項。|
|[CDateTimeCtrl::建立](#create)|創建日期和時間選取器控制項並將其附加到`CDateTimeCtrl`物件。|
|[CDateTimeCtrl::取得DateTime選取器資訊](#getdatetimepickerinfo)|檢索有關當前日期和時間選取器控制件的資訊。|
|[CDateTimeCtrl:取得理想尺寸](#getidealsize)|返回顯示當前日期和時間所需的日期和時間選取器控制項的理想大小。|
|[CDatetimeCtrl::取得月色](#getmonthcalcolor)|在日期和時間選取器控制項中檢索月曆給定部分的顏色。|
|[CDatetimeCtrl::取得月卡Ctrl](#getmonthcalctrl)|檢索與`CMonthCalCtrl`日期和時間選取器控制項關聯的物件。|
|[CDatetimeCtrl::取得月卡方](#getmonthcalfont)|檢索日期和時間選取器控制項的子月日曆控制項當前使用的字體。|
|[CDatetimeCtrl::取得月卡風格](#getmonthcalstyle)|獲取當前日期和時間選取器控制項的樣式。|
|[CDateTimeCtrl::取得範圍](#getrange)|檢索日期和時間選取器控制項的當前最小和最大允許的系統時間。|
|[CDateTimeCtrl:取得時間](#gettime)|從日期和時間選取器控制項檢索當前選擇的時間,並將其放入指定的`SYSTEMTIME`結構中。|
|[CDateTimeCtrl::設定格式](#setformat)|根據給定的格式字串設置日期和時間選取器控制項的顯示。|
|[CDatetimeCtrl::設定月色](#setmonthcalcolor)|在日期和時間選取器控制項內設置月曆給定部分的顏色。|
|[CDatetimeCtrl::設定月卡方](#setmonthcalfont)|設置日期和時間選取器控制件的子月日曆控制項將使用的字體。|
|[CDateTimeCtrl::設定月卡風格](#setmonthcalstyle)|設置當前日期和時間選取器控制項的樣式。|
|[CDateTimeCtrl::設定範圍](#setrange)|設置日期和時間選取器控制件的最小和最大允許的系統時間。|
|[CDateTimeCtrl::設定時間](#settime)|設置日期和時間選取器控制項中的時間。|

## <a name="remarks"></a>備註

日期和時間選取器控制件 (DTP 控件) 提供了一個簡單的介面,以便與使用者交換日期和時間資訊。 此介面包含欄位,每個欄位都顯示存儲在控制項中的日期和時間資訊的一部分。 使用者可以通過更改給定欄位中字串的內容來更改控制項中儲存的資訊。 用戶可以使用滑鼠或鍵盤從一個字段移動到一個字段。

您可以在創建物件時對物件應用各種樣式來自定義日期和時間選取器控制項。 有關特定於日期和時間選取器控制項的樣式的詳細資訊,請參閱 Windows SDK 中的[日期和時間選擇器控制元件樣式](/windows/win32/Controls/date-and-time-picker-control-styles)。 您可以使用格式樣式設定 DTP 控制項的顯示格式。 這些格式樣式在 Windows SDK 主題[「日期和時間選取器控制件樣式](/windows/win32/Controls/date-and-time-picker-control-styles)」中的「格式樣式」下進行了描述。

日期和時間選取器控制項還使用通知和回調,這在[使用 CDateTimeCtrl](../../mfc/using-cdatetimectrl.md)中描述。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CDateTimeCtrl`

## <a name="requirements"></a>需求

**標題:** afxdtctl.h

## <a name="cdatetimectrlcdatetimectrl"></a><a name="cdatetimectrl"></a>CDateTimeCtrl::CDatetimeCtrl

建構 `CDateTimeCtrl` 物件。

```
CDateTimeCtrl();
```

## <a name="cdatetimectrlclosemonthcal"></a><a name="closemonthcal"></a>CDateTimeCtrl::關閉月卡爾

關閉當前日期和時間選取器控制項。

```
void CloseMonthCal() const;
```

### <a name="remarks"></a>備註

此方法發送[DTM_CLOSEMONTHCAL](/windows/win32/Controls/dtm-closemonthcal)訊息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

以下代碼範例定義用於以程式設計方式存取日期和時間取取器控制項的變數*m_dateTimeCtrl*。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>範例

以下代碼示例關閉當前日期和時間選取器控制項的下拉日曆。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_2.cpp)]

## <a name="cdatetimectrlcreate"></a><a name="create"></a>CDateTimeCtrl::建立

創建日期和時間選取器控制項並將其附加到`CDateTimeCtrl`物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定日期時間控制樣式的組合。 關於日期與時間選取器樣式的詳細資訊,請參閱 Windows SDK 中的[日期與時間選取器控制項樣式](/windows/win32/Controls/date-and-time-picker-control-styles)。

*矩形*<br/>
對[RECT](/previous-versions/dd162897\(v=vs.85\))結構的引用,它是日期和時間選取器控制件的位置和大小。

*pparentwnd*<br/>
指向[CWnd](../../mfc/reference/cwnd-class.md)物件的指標,該物件是日期和時間選取器控制件的父視窗。 它不得為 NULL。

*nID*<br/>
指定日期和時間選取器控制項的控制 ID。

### <a name="return-value"></a>傳回值

如果創建成功,則非零;否則 0。

### <a name="remarks"></a>備註

##### <a name="to-create-a-date-and-time-picker-control"></a>建立日期與時間選取器控制項

1. 調用[CDateTimeCtrl](#cdatetimectrl)`CDateTimeCtrl`建構 物件。

1. 調用此成員函數,該函數創建 Windows 日期和時間選取器控制項並將其附加`CDateTimeCtrl`到 物件。

呼叫`Create`時呼叫 ,將初始化公共控制項。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CDateTimeCtrl#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_3.cpp)]

## <a name="cdatetimectrlgetdatetimepickerinfo"></a><a name="getdatetimepickerinfo"></a>CDateTimeCtrl::取得DateTime選取器資訊

檢索有關當前日期和時間選取器控制件的資訊。

```
BOOL GetDateTimePickerInfo(LPDATETIMEPICKERINFO pDateTimePickerInfo) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*pDateTime拾取資訊*|[出]指向[DATETIMEPICKERINFO](/windows/win32/api/commctrl/ns-commctrl-datetimepickerinfo)結構的指標,該結構接收當前日期和時間選取器控制項的說明。<br /><br /> 調用方負責分配此結構。 但是,此方法初始化結構的*cbSize*成員。|

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法發送[DTM_GETDATETIMEPICKERINFO](/windows/win32/Controls/dtm-getdatetimepickerinfo)消息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

以下代碼範例定義用於以程式設計方式存取日期和時間取取器控制項的變數*m_dateTimeCtrl*。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>範例

以下代碼示例指示它是否成功檢索有關當前日期和時間選取器控制件的資訊。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_4.cpp)]

## <a name="cdatetimectrlgetmonthcalcolor"></a><a name="getmonthcalcolor"></a>CDatetimeCtrl::取得月色

在日期和時間選取器控制項中檢索月曆給定部分的顏色。

```
COLORREF GetMonthCalColor(int iColor) const;
```

### <a name="parameters"></a>參數

*iColor*<br/>
指定要檢索的月曆的顏色區域的**int**值。 有關值清單,請參閱[SetMonthCalColor](#setmonthcalcolor)的*iColor*參數。

### <a name="return-value"></a>傳回值

COLORREF 值,表示月份日曆控件指定部分的顏色設置(如果成功)。 如果不成功,函數返回 -1。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[DTM_GETMCCOLOR](/windows/win32/Controls/dtm-getmccolor)的行為,如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CDateTimeCtrl#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_5.cpp)]

## <a name="cdatetimectrlgetmonthcalctrl"></a><a name="getmonthcalctrl"></a>CDatetimeCtrl::取得月卡Ctrl

檢索與`CMonthCalCtrl`日期和時間選取器控制項關聯的物件。

```
CMonthCalCtrl* GetMonthCalCtrl() const;
```

### <a name="return-value"></a>傳回值

指向[CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)物件的指標,如果不成功或視窗不可見,則指向 NULL。

### <a name="remarks"></a>備註

日期和時間選取器控制件在使用者按下拉箭頭時創建子月日曆控制件。 當不再需要`CMonthCalCtrl`該物件時,該物件將被銷毀,因此應用程式不得依賴存儲表示日期時間選取器控件的子月日曆的物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CDateTimeCtrl#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_6.cpp)]

## <a name="cdatetimectrlgetmonthcalfont"></a><a name="getmonthcalfont"></a>CDatetimeCtrl::取得月卡方

獲取日期和時間選取器控制件的月份行事曆控制項當前使用的字型。

```
CFont* GetMonthCalFont() const;
```

### <a name="return-value"></a>傳回值

指向[CFont](../../mfc/reference/cfont-class.md)物件的指標,如果不成功,則指向 NULL。

### <a name="remarks"></a>備註

返回`CFont`值指向的對像是臨時物件,並在下一個空閒處理期間銷毀。

## <a name="cdatetimectrlgetmonthcalstyle"></a><a name="getmonthcalstyle"></a>CDatetimeCtrl::取得月卡風格

獲取與當前日期和時間選取器控制項關聯的下拉月日曆控件的樣式。

```
DWORD GetMonthCalStyle() const;
```

### <a name="return-value"></a>傳回值

下拉月日曆控件的樣式,它是日期和時間選取器控制樣式的位組合 (OR)。 有關詳細資訊,請參閱[月曆控件樣式](/windows/win32/Controls/month-calendar-control-styles)。

### <a name="remarks"></a>備註

此方法發送[DTM_GETMCSTYLE](/windows/win32/Controls/dtm-getmcstyle)消息,這在 Windows SDK 中介紹。

## <a name="cdatetimectrlgetrange"></a><a name="getrange"></a>CDateTimeCtrl::取得範圍

檢索日期和時間選取器控制項的當前最小和最大允許的系統時間。

```
DWORD GetRange(
    COleDateTime* pMinRange,
    COleDateTime* pMaxRange) const;

DWORD GetRange(
    CTime* pMinRange,
    CTime* pMaxRange) const;
```

### <a name="parameters"></a>參數

*普明朗*<br/>
指向[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件的指標或`CDateTimeCtrl`包含 物件中允許的最早時間的[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的指標。

*pMaxRange*<br/>
指向`COleDateTime`物件或`CTime``CDateTimeCtrl`包含 物件中允許的最近時間的物件的指標。

### <a name="return-value"></a>傳回值

包含指示設置範圍的標誌的 DWORD 值。 If

`return value & GDTR_MAX` == 0

然後第二個參數有效。 同樣,如果

`return value & GDTR_MIN` == 0

然後第一個參數有效。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[DTM_GETRANGE](/windows/win32/Controls/dtm-getrange)的行為,如 Windows SDK 中所述。 在 MFC 的實現中,您`COleDateTime`可以`CTime`指定或用法。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CDateTimeCtrl#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_7.cpp)]

## <a name="cdatetimectrlgettime"></a><a name="gettime"></a>CDateTimeCtrl:取得時間

從日期和時間選取器控制項檢索當前選擇的時間,並將其放入指定的`SYSTEMTIME`結構中。

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>參數

*時間時間*<br/>
在第一個版本中,對將收到系統時間資訊的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件的引用。 在第二個版本中,對將收到系統時間資訊的[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的引用。

*pTimeD*<br/>
指向[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標,用於接收系統時間資訊。 不能為 NULL。

### <a name="return-value"></a>傳回值

在第一個版本中,如果時間已成功寫入`COleDateTime`物件,則非零;否則 0。 在第二和第三版本中,DWORD 值等於[NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange)結構中設置的*dwFlag*成員。 有關詳細資訊,請參閱下面的**備註**部分。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[DTM_GETSYSTEMTIME](/windows/win32/Controls/dtm-getsystemtime)的行為,如 Windows SDK 中所述。 在`GetTime`MFC 實現的 中`COleDateTime``CTime`,可以使用或類`SYSTEMTIME`,也可以使用 結構來存儲時間資訊。

上面第二和第三版本中的返回值 DWORD 指示日期和時間選取器控制項是否設置為「無日期」狀態,如[NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange)結構成員*dwFlags*中所示。 如果返回的值等於GDT_NONE,則控件設置為"無日期"狀態,並使用DTS_SHOWNONE樣式。 如果返回的值等於GDT_VALID,則系統時間將成功存儲在目標位置。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CDateTimeCtrl#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_8.cpp)]

## <a name="cdatetimectrlgetidealsize"></a><a name="getidealsize"></a>CDateTimeCtrl:取得理想尺寸

返回顯示當前日期和時間所需的日期和時間選取器控制項的理想大小。

```
BOOL GetIdealSize(LPSIZE psize) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*psize*|[出]指向包含控制項理想大小的[SIZE](/windows/win32/api/windef/ns-windef-size)結構的指標。|

### <a name="return-value"></a>傳回值

返回值始終為 TRUE。

### <a name="remarks"></a>備註

此方法發送[DTM_GETIDEALSIZE](/windows/win32/Controls/dtm-getidealsize)消息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

以下代碼範例定義用於以程式設計方式存取日期和時間取取器控制項的變數*m_dateTimeCtrl*。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>範例

以下代碼示例檢索理想大小以顯示日期和時間選取器控制項。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_9.cpp)]

## <a name="cdatetimectrlsetformat"></a><a name="setformat"></a>CDateTimeCtrl::設定格式

根據給定的格式字串設置日期和時間選取器控制項的顯示。

```
BOOL SetFormat(LPCTSTR pstrFormat);
```

### <a name="parameters"></a>參數

*pstrFormat*<br/>
指向定義所需顯示的零端接格式字串的指標。 將此參數設定為 NULL 會將控制項重置為目前的樣式的預設格式字串。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

> [!NOTE]
> 使用者輸入不能決定此調用的成功或失敗。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[的行為DTM_SETFORMAT](/windows/win32/Controls/dtm-setformat),如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CDateTimeCtrl#6](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_10.cpp)]

## <a name="cdatetimectrlsetmonthcalcolor"></a><a name="setmonthcalcolor"></a>CDatetimeCtrl::設定月色

在日期和時間選取器控制項內設置月曆給定部分的顏色。

```
COLORREF SetMonthCalColor(
    int iColor,
    COLORREF ref);
```

### <a name="parameters"></a>參數

*iColor*<br/>
**int**值,指定要設置的月曆控件的哪個區域。 此值可以是以下值之一。

|值|意義|
|-----------|-------------|
|MCSC_BACKGROUND|設置月份之間顯示的背景顏色。|
|MCSC_MONTHBK|設置一個月內顯示的背景顏色。|
|MCSC_TEXT|設置用於在一個月內顯示文本的顏色。|
|MCSC_TITLEBK|設定行事曆標題中顯示的背景顏色。|
|MCSC_TITLETEXT|設定用於在行事曆標題中顯示文本的顏色。|
|MCSC_TRAILINGTEXT|設定用於顯示標題和尾隨日文字的顏色。 標題和尾隨日是當前日曆上顯示的前一個月和後幾個月的天數。|

*ref*<br/>
表示將為月曆的指定區域設置的顏色的 COLORREF 值。

### <a name="return-value"></a>傳回值

COLORREF 值,表示月份行事曆控制項指定部分的上一個顏色設置(如果成功)。 否則,消息返回 -1。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[DTM_SETMCCOLOR](/windows/win32/Controls/dtm-setmccolor)的行為,如 Windows SDK 中所述。

### <a name="example"></a>範例

  請參考[CDateTimeCtrl 的範例:取得月卡顏色](#getmonthcalcolor)。

## <a name="cdatetimectrlsetmonthcalfont"></a><a name="setmonthcalfont"></a>CDatetimeCtrl::設定月卡方

設置日期和時間選取器控制件的子月日曆控制項將使用的字體。

```
void SetMonthCalFont(
    HFONT hFont,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>參數

*h字型*<br/>
處理要設置的字體。

*bredraw*<br/>
指定是否應在設置字型時立即重繪控制項。 將此參數設置為 TRUE 會導致控制項重新繪製自身。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[DTM_SETMCFONT](/windows/win32/Controls/dtm-setmcfont)的行為,如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CDateTimeCtrl#7](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_11.cpp)]

> [!NOTE]
> 如果使用此代碼,則需要使`CDialog`派生類別的成員稱為`CFont`*m_MonthFont*類型 。

## <a name="cdatetimectrlsetmonthcalstyle"></a><a name="setmonthcalstyle"></a>CDateTimeCtrl::設定月卡風格

設置與當前日期和時間選取器控制項關聯的下拉月日曆控件的樣式。

```
DWORD SetMonthCalStyle(DWORD dwStyle);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*dwStyle*|[在]新的月曆控制樣式,它是月曆控件樣式的位組合 (OR)。 有關詳細資訊,請參閱[月曆控件樣式](/windows/win32/Controls/month-calendar-control-styles)。|

### <a name="return-value"></a>傳回值

下拉月日曆控件的上一樣式。

### <a name="remarks"></a>備註

此方法發送[DTM_SETMCSTYLE](/windows/win32/Controls/dtm-setmcstyle)消息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

以下代碼範例定義用於以程式設計方式存取日期和時間取取器控制項的變數*m_dateTimeCtrl*。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]

### <a name="example"></a>範例

以下代碼示例將日期和時間選取器控制項設置以顯示周數、星期幾縮寫名稱和"今日指示器"。

[!code-cpp[NVC_MFC_CDateTimeCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_12.cpp)]

## <a name="cdatetimectrlsetrange"></a><a name="setrange"></a>CDateTimeCtrl::設定範圍

設置日期和時間選取器控制件的最小和最大允許的系統時間。

```
BOOL SetRange(
    const COleDateTime* pMinRange,
    const COleDateTime* pMaxRange);

BOOL SetRange(
    const CTime* pMinRange,
    const CTime* pMaxRange);
```

### <a name="parameters"></a>參數

*普明朗*<br/>
指向[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件的指標或`CDateTimeCtrl`包含 物件中允許的最早時間的[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的指標。

*pMaxRange*<br/>
指向`COleDateTime`物件或`CTime``CDateTimeCtrl`包含 物件中允許的最近時間的物件的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[DTM_SETRANGE](/windows/win32/Controls/dtm-setrange)的行為,如 Windows SDK 中所述。 在 MFC 的實現中,您`COleDateTime`可以`CTime`指定或用法。 如果`COleDateTime`物件具有 NULL 狀態,則該範圍將被刪除。 如果`CTime`指標或`COleDateTime`指標為 NULL,則將刪除該範圍。

### <a name="example"></a>範例

  請參考[CDateTimeCtrl 的範例::取得範圍](#getrange)。

## <a name="cdatetimectrlsettime"></a><a name="settime"></a>CDateTimeCtrl::設定時間

設置日期和時間選取器控制項中的時間。

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* pTimeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew = NULL);
```

### <a name="parameters"></a>參數

*時間新*<br/>
對包含要向其設置控制項的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件的參考。

*pTimeNew*<br/>
在上面的第二個版本中,指向[CTime](../../atl-mfc-shared/reference/ctime-class.md)物件的指標,其中包含將控制項設置為的時間。 在上面的第三個版本中,指向[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)結構的指標,其中包含將控制項設置為的時間。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[DTM_SETSYSTEMTIME](/windows/win32/Controls/dtm-setsystemtime)的行為,如 Windows SDK 中所述。 在 MFC`SetTime`的 實現中`COleDateTime`,`CTime`可以使用或類`SYSTEMTIME`,也可以使用 結構來設置時間資訊。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CDateTimeCtrl#8](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_13.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 樣品 CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CMonthCalCtrl 類別](../../mfc/reference/cmonthcalctrl-class.md)
