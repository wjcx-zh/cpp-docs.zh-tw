---
title: CButton 類別
ms.date: 11/04/2016
f1_keywords:
- CButton
- AFXWIN/CButton
- AFXWIN/CButton::CButton
- AFXWIN/CButton::Create
- AFXWIN/CButton::DrawItem
- AFXWIN/CButton::GetBitmap
- AFXWIN/CButton::GetButtonStyle
- AFXWIN/CButton::GetCheck
- AFXWIN/CButton::GetCursor
- AFXWIN/CButton::GetIcon
- AFXWIN/CButton::GetIdealSize
- AFXWIN/CButton::GetImageList
- AFXWIN/CButton::GetNote
- AFXWIN/CButton::GetNoteLength
- AFXWIN/CButton::GetSplitGlyph
- AFXWIN/CButton::GetSplitImageList
- AFXWIN/CButton::GetSplitInfo
- AFXWIN/CButton::GetSplitSize
- AFXWIN/CButton::GetSplitStyle
- AFXWIN/CButton::GetState
- AFXWIN/CButton::GetTextMargin
- AFXWIN/CButton::SetBitmap
- AFXWIN/CButton::SetButtonStyle
- AFXWIN/CButton::SetCheck
- AFXWIN/CButton::SetCursor
- AFXWIN/CButton::SetDropDownState
- AFXWIN/CButton::SetIcon
- AFXWIN/CButton::SetImageList
- AFXWIN/CButton::SetNote
- AFXWIN/CButton::SetSplitGlyph
- AFXWIN/CButton::SetSplitImageList
- AFXWIN/CButton::SetSplitInfo
- AFXWIN/CButton::SetSplitSize
- AFXWIN/CButton::SetSplitStyle
- AFXWIN/CButton::SetState
- AFXWIN/CButton::SetTextMargin
helpviewer_keywords:
- CButton [MFC], CButton
- CButton [MFC], Create
- CButton [MFC], DrawItem
- CButton [MFC], GetBitmap
- CButton [MFC], GetButtonStyle
- CButton [MFC], GetCheck
- CButton [MFC], GetCursor
- CButton [MFC], GetIcon
- CButton [MFC], GetIdealSize
- CButton [MFC], GetImageList
- CButton [MFC], GetNote
- CButton [MFC], GetNoteLength
- CButton [MFC], GetSplitGlyph
- CButton [MFC], GetSplitImageList
- CButton [MFC], GetSplitInfo
- CButton [MFC], GetSplitSize
- CButton [MFC], GetSplitStyle
- CButton [MFC], GetState
- CButton [MFC], GetTextMargin
- CButton [MFC], SetBitmap
- CButton [MFC], SetButtonStyle
- CButton [MFC], SetCheck
- CButton [MFC], SetCursor
- CButton [MFC], SetDropDownState
- CButton [MFC], SetIcon
- CButton [MFC], SetImageList
- CButton [MFC], SetNote
- CButton [MFC], SetSplitGlyph
- CButton [MFC], SetSplitImageList
- CButton [MFC], SetSplitInfo
- CButton [MFC], SetSplitSize
- CButton [MFC], SetSplitStyle
- CButton [MFC], SetState
- CButton [MFC], SetTextMargin
ms.assetid: cdc76d5b-31da-43c5-bc43-fde4cb39de5b
ms.openlocfilehash: 7e2156c7fba6d5c621ab9e73b4739be45941fcc5
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561982"
---
# <a name="cbutton-class"></a>CButton 類別

提供 Windows 按鈕控制項的功能。

## <a name="syntax"></a>語法

```
class CButton : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CButton：： CButton](#cbutton)|建構 `CButton` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CButton：： Create](#create)|建立 Windows 按鈕控制項，並將其附加至 `CButton` 物件。|
|[CButton：:D rawItem](#drawitem)|覆寫以繪製主控描繪的 `CButton` 物件。|
|[CButton：： GetBitmap](#getbitmap)|抓取先前以 [SetBitmap](#setbitmap)設定之點陣圖的控制碼。|
|[CButton：： GetButtonStyle](#getbuttonstyle)|抓取按鈕控制項樣式的相關資訊。|
|[CButton：： GetCheck](#getcheck)|抓取按鈕控制項的檢查狀態。|
|[CButton：： GetCursor](#getcursor)|抓取先前以 [SetCursor](#setcursor)設定之資料指標映射的控制碼。|
|[CButton：： GetIcon](#geticon)|抓取先前以 [SetIcon](#seticon)設定之圖示的控制碼。|
|[CButton：： GetIdealSize](#getidealsize)|抓取按鈕控制項的理想大小。|
|[CButton：： GetImageList](#getimagelist)|抓取按鈕控制項的影像清單。|
|[CButton：： GetNote](#getnote)|抓取目前命令連結控制項的附注元件。|
|[CButton：： GetNoteLength](#getnotelength)|抓取目前命令連結控制項的附注文字長度。|
|[CButton：： GetSplitGlyph](#getsplitglyph)|抓取與目前分割按鈕控制項相關聯的圖像。|
|[CButton：： GetSplitImageList](#getsplitimagelist)|抓取目前分割按鈕控制項的影像清單。|
|[CButton：： GetSplitInfo](#getsplitinfo)|捕獲定義目前分割按鈕控制項的資訊。|
|[CButton：： GetSplitSize](#getsplitsize)|抓取目前分割按鈕控制項之下拉式元件的周框。|
|[CButton：： GetSplitStyle](#getsplitstyle)|抓取定義目前分割按鈕控制項的分割按鈕樣式。|
|[CButton：： >getstate](#getstate)|抓取按鈕控制項的檢查狀態、反白顯示狀態和焦點狀態。|
|[CButton：： GetTextMargin](#gettextmargin)|抓取按鈕控制項的文字邊界。|
|[CButton：： SetBitmap](#setbitmap)|指定要顯示在按鈕上的點陣圖。|
|[CButton：： SetButtonStyle](#setbuttonstyle)|變更按鈕的樣式。|
|[CButton：： SetCheck](#setcheck)|設定按鈕控制項的檢查狀態。|
|[CButton：： SetCursor](#setcursor)|指定要顯示在按鈕上的游標影像。|
|[CButton：： SetDropDownState](#setdropdownstate)|設定目前分割按鈕控制項的下拉式狀態。|
|[CButton：： SetIcon](#seticon)|指定要顯示在按鈕上的圖示。|
|[CButton：： SetImageList](#setimagelist)|設定按鈕控制項的影像清單。|
|[CButton：： SetNote](#setnote)|設定目前命令連結控制項的附注。|
|[CButton：： SetSplitGlyph](#setsplitglyph)|將指定的圖像與目前的分割按鈕控制項產生關聯。|
|[CButton：： SetSplitImageList](#setsplitimagelist)|將影像清單與目前的分割按鈕控制項產生關聯。|
|[CButton：： SetSplitInfo](#setsplitinfo)|指定定義目前分割按鈕控制項的資訊。|
|[CButton：： SetSplitSize](#setsplitsize)|設定目前分割按鈕控制項之下拉式元件的周框。|
|[CButton：： SetSplitStyle](#setsplitstyle)|設定目前分割按鈕控制項的樣式。|
|[CButton：： SetState](#setstate)|設定按鈕控制項的反白顯示狀態。|
|[CButton：： SetTextMargin](#settextmargin)|設定按鈕控制項的文字邊界。|

## <a name="remarks"></a>備註

按鈕控制項是一個小型的矩形子視窗，可以按一下和關閉。 按鈕可以單獨使用或在群組中，也可以在不使用文字的情況下標記或顯示。 當使用者按一下按鈕時，按鈕通常會變更外觀。

一般按鈕是核取方塊、選項按鈕和按鈕。 `CButton`根據[Create](#create)成員函式的初始化所指定的[按鈕樣式](../../mfc/reference/styles-used-by-mfc.md#button-styles)，物件可以變成其中任何一種。

此外，衍生自的 [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md) 類別 `CButton` 支援建立以點陣圖影像（而非文字）標記的按鈕控制項。 `CBitmapButton`可以針對按鈕的向上、向下、焦點和停用狀態，擁有個別的點陣圖。

您可以從對話方塊範本或直接在程式碼中建立按鈕控制項。 在這兩種情況下，請先呼叫此函式 `CButton` 來建立 `CButton` 物件，然後呼叫成員函式 `Create` 來建立 Windows 按鈕控制項，並將其附加至 `CButton` 物件。

在衍生自的類別中，結構可以是單一步驟的進程 `CButton` 。 撰寫衍生類別的函式，並從函式 `Create` 內呼叫。

如果您想要處理按鈕控制項傳送到其父系 (的 Windows 通知訊息，通常是衍生自 [CDialog](../../mfc/reference/cdialog-class.md)) 的類別，請將訊息對應專案和訊息處理常式成員函式加入至每個訊息的父類別。

每個訊息對應專案都採用下列格式：

**開啟 \_ **_通知_ ** (** _識別碼_， _memberFxn_ **) **

其中 *id* 指定傳送通知之控制項的子視窗識別碼，而 *memberFxn* 是您所撰寫用來處理通知的父成員函式的名稱。

父系的函式原型如下：

`afx_msg void memberFxn();`

可能的訊息對應專案如下所示：

|對應項目|傳送至父系 .。。|
|---------------|----------------------------|
|ON_BN_CLICKED|使用者按一下按鈕。|
|ON_BN_DOUBLECLICKED|使用者按兩下按鈕。|

如果您 `CButton` 從對話方塊資源建立物件， `CButton` 當使用者關閉對話方塊時，就會自動終結物件。

如果您在 `CButton` 視窗中建立物件，您可能需要終結它。 如果您使用函式在 `CButton` 堆積上建立物件 **`new`** ，您必須 **`delete`** 在物件上呼叫，以便在使用者關閉 Windows 按鈕控制項時終結它。 如果您在 `CButton` 堆疊上建立物件，或將它內嵌在父對話方塊物件中，則會自動將它終結。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CButton`

## <a name="requirements"></a>規格需求

**標題:** afxwin.h

## <a name="cbuttoncbutton"></a><a name="cbutton"></a> CButton：： CButton

建構 `CButton` 物件。

```
CButton();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CButton#1](../../mfc/reference/codesnippet/cpp/cbutton-class_1.cpp)]

## <a name="cbuttoncreate"></a><a name="create"></a> CButton：： Create

建立 Windows 按鈕控制項，並將其附加至 `CButton` 物件。

```
virtual BOOL Create(
    LPCTSTR lpszCaption,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*lpszCaption*<br/>
指定按鈕控制項的文字。

*dwStyle*<br/>
指定按鈕控制項的樣式。 將 [按鈕樣式](../../mfc/reference/styles-used-by-mfc.md#button-styles) 的任何組合套用至按鈕。

*矩形*<br/>
指定按鈕控制項的大小和位置。 它可以是 `CRect` 物件或 `RECT` 結構。

*pParentWnd*<br/>
指定按鈕控制項的父視窗，通常是 `CDialog` 。 它不得為 NULL。

*nID*<br/>
指定按鈕控制項的識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

您可以使用 `CButton` 兩個步驟來建立物件。 首先，呼叫此函式，然後呼叫 `Create` ，它會建立 Windows 按鈕控制項，並將其附加至 `CButton` 物件。

如果指定了 WS_VISIBLE 的樣式，Windows 會傳送按鈕控制項所有啟動的訊息，並顯示該按鈕。

將下列 [視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles) 套用至按鈕控制項：

- 一律 WS_CHILD

- 通常 WS_VISIBLE

- WS_DISABLED 很少

- WS_GROUP 至群組控制項

- WS_TABSTOP 在定位順序中包含按鈕

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CButton#2](../../mfc/reference/codesnippet/cpp/cbutton-class_2.cpp)]

## <a name="cbuttondrawitem"></a><a name="drawitem"></a> CButton：:D rawItem

當主控描繪按鈕的視覺外觀變更時，由架構呼叫。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>參數

*lpDrawItemStruct*<br/>
[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)結構的長指標。 結構包含要繪製之專案的相關資訊，以及所需的繪圖類型。

### <a name="remarks"></a>備註

主控描繪按鈕具有 BS_OWNERDRAW 樣式集。 覆寫這個成員函式，以針對主控描繪的物件來執行繪圖 `CButton` 。 應用程式應該在成員函式終止之前，還原為 *lpDrawItemStruct* 中提供的顯示內容選取的所有圖形裝置介面 (GDI) 物件。

另請參閱 [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) 樣式值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CButton#3](../../mfc/reference/codesnippet/cpp/cbutton-class_3.cpp)]

## <a name="cbuttongetbitmap"></a><a name="getbitmap"></a> CButton：： GetBitmap

呼叫這個成員函式，以取得與按鈕相關聯之點陣圖（先前以 [SetBitmap](#setbitmap)設定）的控制碼。

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>傳回值

點陣圖的控制碼。 如果之前未指定任何點陣圖，則為 Null。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

## <a name="cbuttongetbuttonstyle"></a><a name="getbuttonstyle"></a> CButton：： GetButtonStyle

抓取按鈕控制項樣式的相關資訊。

```
UINT GetButtonStyle() const;
```

### <a name="return-value"></a>傳回值

傳回這個物件的按鈕樣式 `CButton` 。 此函數只會傳回 [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) 的樣式值，不會傳回任何其他視窗樣式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

## <a name="cbuttongetcheck"></a><a name="getcheck"></a> CButton：： GetCheck

抓取選項按鈕或核取方塊的檢查狀態。

```
int GetCheck() const;
```

### <a name="return-value"></a>傳回值

使用 BS_AUTOCHECKBOX、BS_AUTORADIOBUTTON、BS_AUTO3STATE、BS_CHECKBOX、BS_RADIOBUTTON 或 BS_3STATE 樣式所建立之按鈕控制項的傳回值是下列其中一個值：

|值|意義|
|-----------|-------------|
|BST_UNCHECKED|按鈕狀態為未核取。|
|BST_CHECKED|按鈕狀態為已核取。|
|BST_INDETERMINATE|按鈕狀態是不定的 (只有在按鈕具有 BS_3STATE 或 BS_AUTO3STATE 樣式) 時才適用。|

如果按鈕具有任何其他樣式，則傳回值為 BST_UNCHECKED。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

## <a name="cbuttongetcursor"></a><a name="getcursor"></a> CButton：： GetCursor

呼叫這個成員函式，以取得與按鈕相關聯的資料指標（先前以 [SetCursor](#setcursor)設定）的控制碼。

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>傳回值

資料指標影像的控制碼。 如果之前未指定任何資料指標，則為 Null。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

## <a name="cbuttongeticon"></a><a name="geticon"></a> CButton：： GetIcon

呼叫這個成員函式，以取得與按鈕相關聯之圖示的控制碼，先前以 [SetIcon](#seticon)設定。

```
HICON GetIcon() const;
```

### <a name="return-value"></a>傳回值

圖示的控制代碼。 如果先前未指定任何圖示，則為 Null。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

## <a name="cbuttongetidealsize"></a><a name="getidealsize"></a> CButton：： GetIdealSize

抓取按鈕控制項的理想大小。

```
BOOL GetIdealSize(SIZE* psize);
```

### <a name="parameters"></a>參數

*psize*<br/>
按鈕目前大小的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式會模擬 BCM_GETIDEALSIZE 訊息的功能，如 Windows SDK 的 [按鈕](/windows/win32/controls/buttons) 區段中所述。

## <a name="cbuttongetimagelist"></a><a name="getimagelist"></a> CButton：： GetImageList

呼叫這個方法，從按鈕控制項取得影像清單。

```
BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>參數

*pbuttonImagelist*<br/>
物件影像清單的指標 `CButton` 。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式會模擬 BCM_GETIMAGELIST 訊息的功能，如 Windows SDK 的 [按鈕](/windows/win32/controls/buttons) 區段中所述。

## <a name="cbuttongetnote"></a><a name="getnote"></a> CButton：： GetNote

抓取與目前命令連結控制項相關聯的備註文字。

```
CString GetNote() const;

BOOL GetNote(
    LPTSTR lpszNote,
    UINT* cchNote) const;
```

### <a name="parameters"></a>參數

*lpszNote*\
擴展緩衝區的指標，呼叫端負責配置和解除配置。 如果傳回值為 TRUE，緩衝區會包含與目前命令連結控制項相關聯的附注文字;否則，緩衝區會維持不變。

*cchNote*\
[in，out]不帶正負號整數變數的指標。 當呼叫這個方法時，變數會包含 *lpszNote* 參數所指定的緩衝區大小。 當此方法傳回時，如果傳回值為 TRUE，則變數會包含與目前命令連結控制項相關聯的附注大小。 如果傳回值為 FALSE，則變數包含包含附注所需的緩衝區大小。

### <a name="return-value"></a>傳回值

在第一個多載中，包含與目前命令連結控制項相關聯之附注文字的 [CString](../../atl-mfc-shared/using-cstring.md) 物件。

-或-

在第二個多載中，如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

此方法只能搭配按鈕樣式是 BS_COMMANDLINK 或 BS_DEFCOMMANDLINK 的控制項使用。

這個方法會傳送 [BCM_GETNOTE](/windows/win32/Controls/bcm-getnote) 的訊息，如 Windows SDK 中所述。

## <a name="cbuttongetnotelength"></a><a name="getnotelength"></a> CButton：： GetNoteLength

抓取目前命令連結控制項的附注文字長度。

```
UINT GetNoteLength() const;
```

### <a name="return-value"></a>傳回值

目前命令連結控制項的附注文字長度（以16位 Unicode 字元為單位）。

### <a name="remarks"></a>備註

此方法只能搭配按鈕樣式是 BS_COMMANDLINK 或 BS_DEFCOMMANDLINK 的控制項使用。

這個方法會傳送 [BCM_GETNOTELENGTH](/windows/win32/Controls/bcm-getnotelength) 的訊息，如 Windows SDK 中所述。

## <a name="cbuttongetsplitglyph"></a><a name="getsplitglyph"></a> CButton：： GetSplitGlyph

抓取與目前分割按鈕控制項相關聯的圖像。

```
TCHAR GetSplitGlyph() const;
```

### <a name="return-value"></a>傳回值

與目前分割按鈕控制項相關聯的圖像字元。

### <a name="remarks"></a>備註

圖像是特定字型中字元的實體標記法。 例如，分割按鈕控制項可能會以 Unicode 勾號字元的字元 (U + 2713) 裝飾。

此方法只能搭配按鈕樣式是 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 的控制項使用。

這個方法會將 `mask` [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) 結構的成員初始化為 BCSIF_GLYPH 旗標，然後在 Windows SDK 所述的 [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) 訊息中傳送該結構。 當訊息函式傳回時，這個方法會從結構的 `himlGlyph` 成員抓取圖像。

## <a name="cbuttongetsplitimagelist"></a><a name="getsplitimagelist"></a> CButton：： GetSplitImageList

抓取目前分割按鈕控制項的 [影像清單](../../mfc/reference/cimagelist-class.md) 。

```
CImageList* GetSplitImageList() const;
```

### <a name="return-value"></a>傳回值

[CImageList](../../mfc/reference/cimagelist-class.md)物件的指標。

### <a name="remarks"></a>備註

此方法只能搭配按鈕樣式是 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 的控制項使用。

這個方法會將 `mask` [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) 結構的成員初始化為 BCSIF_IMAGE 旗標，然後在 Windows SDK 所述的 [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) 訊息中傳送該結構。 當訊息函數傳回時，這個方法會從結構的成員抓取影像清單 `himlGlyph` 。

## <a name="cbuttongetsplitinfo"></a><a name="getsplitinfo"></a> CButton：： GetSplitInfo

抓取決定 Windows 如何繪製目前分割按鈕控制項的參數。

```
BOOL GetSplitInfo(PBUTTON_SPLITINFO pInfo) const;
```

### <a name="parameters"></a>參數

*pInfo*\
擴展 [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) 結構的指標，此結構會接收目前分割按鈕控制項的相關資訊。 呼叫端負責配置結構。

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

此方法只能搭配按鈕樣式是 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 的控制項使用。

這個方法會傳送 [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) 的訊息，如 Windows SDK 中所述。

## <a name="cbuttongetsplitsize"></a><a name="getsplitsize"></a> CButton：： GetSplitSize

抓取目前分割按鈕控制項之下拉式元件的周框。

```
BOOL GetSplitSize(LPSIZE pSize) const;
```

### <a name="parameters"></a>參數

*pSize*\
擴展接收矩形描述的 [大小](/windows/win32/api/windef/ns-windef-size) 結構指標。

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

此方法只能搭配按鈕樣式是 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 的控制項使用。

展開分割按鈕控制項時，它可以顯示下拉式元件，例如清單控制項或分頁控制項。 這個方法會抓取包含下拉式元件的周框。

這個方法會將 `mask` [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) 結構的成員初始化為 BCSIF_SIZE 旗標，然後在 Windows SDK 所述的 [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) 訊息中傳送該結構。 當訊息函式傳回時，這個方法會從結構的成員中抓取周框 `size` 。

## <a name="cbuttongetsplitstyle"></a><a name="getsplitstyle"></a> CButton：： GetSplitStyle

抓取定義目前分割按鈕控制項的分割按鈕樣式。

```
UINT GetSplitStyle() const;
```

### <a name="return-value"></a>傳回值

分割按鈕樣式的位元組合。 如需詳細資訊，請參閱 `uSplitStyle` [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) 結構的成員。

### <a name="remarks"></a>備註

此方法只能搭配按鈕樣式是 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 的控制項使用。

分割按鈕樣式會指定視窗用來繪製分割按鈕圖示的對齊、外觀比例和圖形格式。

這個方法會將 `mask` [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) 結構的成員初始化為 BCSIF_STYLE 旗標，然後在 Windows SDK 所述的 [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) 訊息中傳送該結構。 當訊息函式傳回時，這個方法會從結構的成員中抓取分割按鈕的樣式 `uSplitStyle` 。

## <a name="cbuttongetstate"></a><a name="getstate"></a> CButton：： >getstate

抓取按鈕控制項的狀態。

```
UINT GetState() const;
```

### <a name="return-value"></a>傳回值

位欄位，包含表示按鈕控制項目前狀態的值組合。 下表列出可能的值。

|按鈕狀態|值|描述|
|------------------|-----------|-----------------|
|BST_UNCHECKED|0x0000|初始狀態。|
|BST_CHECKED|0x0001|按鈕控制項已核取。|
|BST_INDETERMINATE|0x0002|只有當按鈕控制項有三個狀態) 時，才可能 (狀態為不定。|
|BST_PUSHED|0x0004|已按下按鈕控制項。|
|BST_FOCUS|0x0008|按鈕控制項具有焦點。|

### <a name="remarks"></a>備註

具有 [BS_3STATE] 或 [BS_AUTO3STATE] 按鈕樣式的按鈕控制項，會建立一個具有名為 [不定] 狀態之第三個狀態的核取方塊。 [不定] 狀態表示未核取或取消核取此核取方塊。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

## <a name="cbuttongettextmargin"></a><a name="gettextmargin"></a> CButton：： GetTextMargin

呼叫這個方法以取得物件的文字邊界 `CButton` 。

```
BOOL GetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>參數

*pmargin*<br/>
物件的文字邊界指標 `CButton` 。

### <a name="return-value"></a>傳回值

傳回文字邊界。

### <a name="remarks"></a>備註

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式會模擬 BCM_GETTEXTMARGIN 訊息的功能，如 Windows SDK 的 [按鈕](/windows/win32/controls/buttons) 區段中所述。

## <a name="cbuttonsetbitmap"></a><a name="setbitmap"></a> CButton：： SetBitmap

呼叫這個成員函式，將新的點陣圖與按鈕產生關聯。

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>參數

*hBitmap*<br/>
點陣圖的控制碼。

### <a name="return-value"></a>傳回值

先前與按鈕相關聯之點陣圖的控制碼。

### <a name="remarks"></a>備註

點陣圖會自動放在按鈕的臉部上，預設為置中。 如果點陣圖對按鈕而言太大，則會在任一側裁剪。 您可以選擇其他對齊選項，包括下列各項：

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

不同于 [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)（每個按鈕使用四個位圖）， `SetBitmap` 每個按鈕只會使用一個點陣圖。 按下按鈕時，點陣圖會向下和向下移至右邊。

您必須負責在完成時釋放點陣圖。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

## <a name="cbuttonsetbuttonstyle"></a><a name="setbuttonstyle"></a> CButton：： SetButtonStyle

變更按鈕的樣式。

```cpp
void SetButtonStyle(
    UINT nStyle,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>參數

*nStyle*<br/>
指定 [按鈕樣式](../../mfc/reference/styles-used-by-mfc.md#button-styles)。

*bRedraw*<br/>
指定是否要重繪按鈕。 非零值會重繪按鈕。 0值不會重繪按鈕。 預設會重新繪製按鈕。

### <a name="remarks"></a>備註

使用成員函式 `GetButtonStyle` 來取出按鈕樣式。 [完整] 按鈕樣式的低序位字是按鈕專屬的樣式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

## <a name="cbuttonsetcheck"></a><a name="setcheck"></a> CButton：： SetCheck

設定或重設選項按鈕或核取方塊的檢查狀態。

```cpp
void SetCheck(int nCheck);
```

### <a name="parameters"></a>參數

*n*<br/>
指定檢查狀態。 此參數可以是下列其中一項：

|值|意義|
|-----------|-------------|
|BST_UNCHECKED|將按鈕狀態設定為未核取。|
|BST_CHECKED|將按鈕狀態設定為 [已檢查]。|
|BST_INDETERMINATE|將按鈕狀態設定為 [不定]。 只有當按鈕有 BS_3STATE 或 BS_AUTO3STATE 樣式時，才能使用這個值。|

### <a name="remarks"></a>備註

此成員函式對按鈕沒有作用。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

## <a name="cbuttonsetcursor"></a><a name="setcursor"></a> CButton：： SetCursor

呼叫這個成員函式，將新的資料指標與按鈕產生關聯。

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>參數

*hCursor*<br/>
資料指標的控制碼。

### <a name="return-value"></a>傳回值

先前與按鈕相關聯之資料指標的控制碼。

### <a name="remarks"></a>備註

游標會自動放在按鈕的臉部上，預設為置中。 如果資料指標對按鈕而言太大，則會在任一側裁剪。 您可以選擇其他對齊選項，包括下列各項：

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

不同于 [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)（每個按鈕使用四個位圖）， `SetCursor` 每個按鈕只會使用一個資料指標。 按下按鈕時，游標會顯示為向下和向下移至右邊。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

## <a name="cbuttonsetdropdownstate"></a><a name="setdropdownstate"></a> CButton：： SetDropDownState

設定目前分割按鈕控制項的下拉式狀態。

```
BOOL SetDropDownState(BOOL fDropDown);
```

### <a name="parameters"></a>參數

*fDropDown*\
在TRUE 表示設定 BST_DROPDOWNPUSHED 狀態;否則為 FALSE。

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

分割按鈕控制項有 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 的樣式，並包含按鈕和右邊的下拉箭號。 如需詳細資訊，請參閱 [按鈕樣式](/windows/win32/Controls/button-styles)。 通常，當使用者按一下下拉式箭號時，就會設定下拉式清單狀態。 您可以使用這個方法，以程式設計方式設定控制項的下拉式清單狀態。 下拉箭號會以陰影繪製以表示狀態。

這個方法會傳送 [BCM_SETDROPDOWNSTATE](/windows/win32/Controls/bcm-setdropdownstate) 的訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義用來以程式設計方式存取分割按鈕控制項的變數（ *m_splitButton*）。 下列範例會使用這個變數。

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>範例

下列程式碼範例會設定分割按鈕控制項的狀態，以指出下拉箭號已被推送。

[!code-cpp[NVC_MFC_CButton_s1#6](../../mfc/reference/codesnippet/cpp/cbutton-class_11.cpp)]

## <a name="cbuttonsetelevationrequired"></a><a name="setelevationrequired"></a> CButton：： SetElevationRequired

將目前按鈕控制項的狀態設定為 `elevation required` ，讓控制項顯示更高的安全性圖示是必要的。

```
BOOL SetElevationRequired(BOOL fElevationRequired);
```

### <a name="parameters"></a>參數

*fElevationRequired*\
在TRUE 表示設定 `elevation required` 狀態，否則為 FALSE。

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

如果按鈕或命令連結控制項需要較高的安全性許可權來執行動作，請將控制項設定為 [ `elevation required` 狀態]。 接著，Windows 會在控制項上顯示 (UAC) 盾牌圖示的 [使用者帳戶控制]。 如需詳細資訊，請參閱[使用者帳戶控制](/windows/win32/uxguide/winenv-uac)。

這個方法會傳送 [BCM_SETSHIELD](/windows/win32/Controls/bcm-setshield) 的訊息，如 Windows SDK 中所述。

## <a name="cbuttonseticon"></a><a name="seticon"></a> CButton：： SetIcon

呼叫這個成員函式，將新的圖示與按鈕產生關聯。

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>參數

*hIcon*<br/>
圖示的控制碼。

### <a name="return-value"></a>傳回值

先前與按鈕相關聯之圖示的控制碼。

### <a name="remarks"></a>備註

圖示會自動放在按鈕的臉部上，預設為置中。 如果圖示對按鈕而言太大，則會在任一側裁剪。 您可以選擇其他對齊選項，包括下列各項：

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

不同于 [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)（每個按鈕使用四個位圖）， `SetIcon` 每個按鈕只會使用一個圖示。 按下按鈕時，圖示會向下和向下移到右邊。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

## <a name="cbuttonsetimagelist"></a><a name="setimagelist"></a> CButton：： SetImageList

呼叫這個方法來設定物件的影像清單 `CButton` 。

```
BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>參數

*pbuttonImagelist*<br/>
新影像清單的指標。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

此成員函式會模擬 BCM_SETIMAGELIST 訊息的功能，如 Windows SDK 的 [按鈕](/windows/win32/controls/buttons) 區段中所述。

## <a name="cbuttonsetnote"></a><a name="setnote"></a> CButton：： SetNote

設定目前命令連結控制項的附注文字。

```
BOOL SetNote(LPCTSTR lpszNote);
```

### <a name="parameters"></a>參數

*lpszNote*\
在設定為命令連結控制項備註文字的 Unicode 字串指標。

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

此方法只能搭配按鈕樣式是 BS_COMMANDLINK 或 BS_DEFCOMMANDLINK 的控制項使用。

這個方法會傳送 [BCM_SETNOTE](/windows/win32/Controls/bcm-setnote) 的訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義用來以程式設計方式存取命令連結控制項的變數（ *m_cmdLink*）。 下列範例會使用這個變數。

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>範例

下列程式碼範例會設定命令連結控制項的附注文字。

[!code-cpp[NVC_MFC_CButton_s1#7](../../mfc/reference/codesnippet/cpp/cbutton-class_12.cpp)]

## <a name="cbuttonsetsplitglyph"></a><a name="setsplitglyph"></a> CButton：： SetSplitGlyph

將指定的圖像與目前的分割按鈕控制項產生關聯。

```
BOOL SetSplitGlyph(TCHAR chGlyph);
```

### <a name="parameters"></a>參數

*chGlyph*\
在字元，指定用來做為分割按鈕下拉式箭號的圖像。

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

此方法只能搭配具有按鈕樣式 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 的控制項使用。

圖像是特定字型中字元的實體標記法。 *ChGlyph*參數不會用來做為圖像，而是用來從一組系統定義的字元中選取一個圖像。 預設的下拉箭號字元是由字元 ' 6 ' 所指定，類似于 Unicode 字元黑色右下角三角形 (U + 25BC) 。

這個方法 `mask` 會使用 BCSIF_GLYPH 旗標和具有 chGlyph 參數的成員來初始化[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)結構的成員 `himlGlyph` ，然後在 Windows SDK 所述的[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)訊息中傳送該結構。 *chGlyph*

## <a name="cbuttonsetsplitimagelist"></a><a name="setsplitimagelist"></a> CButton：： SetSplitImageList

將 [影像清單](../../mfc/reference/cimagelist-class.md) 與目前的分割按鈕控制項產生關聯。

```
BOOL SetSplitImageList(CImageList* pSplitImageList);
```

### <a name="parameters"></a>參數

*pSplitImageList*\
在要指派給目前分割按鈕控制項之 [CImageList](../../mfc/reference/cimagelist-class.md) 物件的指標。

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

此方法只能搭配按鈕樣式是 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 的控制項使用。

這個方法 `mask` 會使用 BCSIF_IMAGE 旗標和具有 pSplitImageList 參數的成員來初始化[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)結構的成員 `himlGlyph` ，然後在 Windows SDK 所述的[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)訊息中傳送該結構。 *pSplitImageList*

## <a name="cbuttonsetsplitinfo"></a><a name="setsplitinfo"></a> CButton：： SetSplitInfo

指定決定 Windows 如何繪製目前分割按鈕控制項的參數。

```
BOOL SetSplitInfo(PBUTTON_SPLITINFO pInfo);
```

### <a name="parameters"></a>參數

*pInfo*\
在 [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) 結構的指標，此結構會定義目前的分割按鈕控制項。

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

此方法只能搭配按鈕樣式是 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 的控制項使用。

這個方法會傳送 [BCM_SETSPLITINFO](/windows/win32/Controls/bcm-setsplitinfo) 的訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例 `m_splitButton` 會定義用來以程式設計方式存取分割按鈕控制項的變數。

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>範例

下列程式碼範例會變更用於分割按鈕下拉式箭號的圖像。 此範例會針對預設的向下三角形圖像，取代向上指標的三角形圖像。 顯示的圖像取決於您在結構的成員中指定的字元 `himlGlyph` `BUTTON_SPLITINFO` 。 向下指向的三角形圖像是以字元 ' 6 ' 指定，而向上三角形字元是由字元 ' 5 ' 所指定。 如需比較，請參閱便利性方法 [CButton：： SetSplitGlyph](#setsplitglyph)。

[!code-cpp[NVC_MFC_CButton_s1#4](../../mfc/reference/codesnippet/cpp/cbutton-class_13.cpp)]

## <a name="cbuttonsetsplitsize"></a><a name="setsplitsize"></a> CButton：： SetSplitSize

設定目前分割按鈕控制項之下拉式元件的周框。

```
BOOL SetSplitSize(LPSIZE pSize);
```

### <a name="parameters"></a>參數

*pSize*\
在描述周框的 [大小](/windows/win32/api/windef/ns-windef-size) 結構指標。

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

此方法只能搭配按鈕樣式是 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 的控制項使用。

展開分割按鈕控制項時，它可以顯示下拉式元件，例如清單控制項或分頁控制項。 這個方法會指定包含下拉式元件之周框的大小。

這個方法 `mask` 會使用 BCSIF_SIZE 旗標和具有 pSize 參數的成員來初始化[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)結構的成員 `size` ，然後在 Windows SDK 所述的[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)訊息中傳送該結構。 *pSize*

### <a name="example"></a>範例

下列程式碼範例 `m_splitButton` 會定義用來以程式設計方式存取分割按鈕控制項的變數。 下列範例會使用這個變數。

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>範例

下列程式碼範例會將分割按鈕下拉式箭號的大小加倍。

[!code-cpp[NVC_MFC_CButton_s1#5](../../mfc/reference/codesnippet/cpp/cbutton-class_14.cpp)]

## <a name="cbuttonsetsplitstyle"></a><a name="setsplitstyle"></a> CButton：： SetSplitStyle

設定目前分割按鈕控制項的樣式。

```
BOOL SetSplitStyle(UINT uSplitStyle);
```

### <a name="parameters"></a>參數

*uSplitStyle*\
在分割按鈕樣式的位元組合。 如需詳細資訊，請參閱 `uSplitStyle` [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) 結構的成員。

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

此方法只能搭配按鈕樣式是 BS_SPLITBUTTON 或 BS_DEFSPLITBUTTON 的控制項使用。

分割按鈕樣式會指定視窗用來繪製分割按鈕圖示的對齊、外觀比例和圖形格式。 如需詳細資訊，請參閱 `uSplitStyle` [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) 結構的成員。

這個方法 `mask` 會使用 BCSIF_STYLE 旗標和具有 uSplitStyle 參數的成員來初始化[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)結構的成員 `uSplitStyle` ，然後在 Windows SDK 所述的[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)訊息中傳送該結構。 *uSplitStyle*

### <a name="example"></a>範例

下列程式碼範例 `m_splitButton` 會定義用來以程式設計方式存取分割按鈕控制項的變數。

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>範例

下列程式碼範例會設定分割按鈕下拉式箭號的樣式。 BCSS_ALIGNLEFT 樣式會顯示按鈕左邊的箭號，而 BCSS_STRETCH 樣式會在您調整按鈕大小時，保留下拉箭號的比例。

[!code-cpp[NVC_MFC_CButton_s1#3](../../mfc/reference/codesnippet/cpp/cbutton-class_15.cpp)]

## <a name="cbuttonsetstate"></a><a name="setstate"></a> CButton：： SetState

設定是否要反白顯示按鈕控制項。

```cpp
void SetState(BOOL bHighlight);
```

### <a name="parameters"></a>參數

*bHighlight*<br/>
指定是否要反白顯示按鈕。 非零值會反白顯示按鈕;0值會移除任何反白顯示。

### <a name="remarks"></a>備註

反白顯示會影響 button 控制項的外部。 它不會影響選項按鈕或核取方塊的核取狀態。

當使用者按一下並按住滑鼠左鍵時，會自動反白顯示按鈕控制項。 當使用者放開滑鼠按鍵時，就會移除反白顯示。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

## <a name="cbuttonsettextmargin"></a><a name="settextmargin"></a> CButton：： SetTextMargin

呼叫這個方法來設定物件的文字邊界 `CButton` 。

```
BOOL SetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>參數

*pmargin*<br/>
新文字邊界的指標。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

此成員函式會模擬 BCM_SETTEXTMARGIN 訊息的功能，如 Windows SDK 的 [按鈕](/windows/win32/controls/buttons) 區段中所述。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[CComboBox 類別](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit 類別](../../mfc/reference/cedit-class.md)<br/>
[CListBox 類別](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar 類別](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic 類別](../../mfc/reference/cstatic-class.md)<br/>
[CBitmapButton 類別](../../mfc/reference/cbitmapbutton-class.md)<br/>
[CDialog 類別](../../mfc/reference/cdialog-class.md)
