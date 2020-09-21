---
title: CMFCMenuButton 類別
ms.date: 07/15/2019
f1_keywords:
- CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton::CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton::PreTranslateMessage
- AFXMENUBUTTON/CMFCMenuButton::SizeToContent
- AFXMENUBUTTON/CMFCMenuButton::m_bOSMenu
- AFXMENUBUTTON/CMFCMenuButton::m_bRightArrow
- AFXMENUBUTTON/CMFCMenuButton::m_bStayPressed
- AFXMENUBUTTON/CMFCMenuButton::m_hMenu
- AFXMENUBUTTON/CMFCMenuButton::m_nMenuResult
- AFXMENUBUTTON/CMFCMenuButton::m_bDefaultClick
helpviewer_keywords:
- CMFCMenuButton [MFC], CMFCMenuButton
- CMFCMenuButton [MFC], PreTranslateMessage
- CMFCMenuButton [MFC], SizeToContent
- CMFCMenuButton [MFC], m_bOSMenu
- CMFCMenuButton [MFC], m_bRightArrow
- CMFCMenuButton [MFC], m_bStayPressed
- CMFCMenuButton [MFC], m_hMenu
- CMFCMenuButton [MFC], m_nMenuResult
- CMFCMenuButton [MFC], m_bDefaultClick
ms.assetid: 53d3d459-1e5a-47c5-8b7f-2e61f6af5187
ms.openlocfilehash: 2f8ef341d7f460ed6b0ec23cb8a490842eb67cbc
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743265"
---
# <a name="cmfcmenubutton-class"></a>CMFCMenuButton 類別

顯示快顯功能表和報告使用者功能表選取的按鈕。

## <a name="syntax"></a>語法

```
class CMFCMenuButton : public CMFCButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCMenuButton：： CMFCMenuButton](#cmfcmenubutton)|建構 `CMFCMenuButton` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCMenuButton::PreTranslateMessage](#pretranslatemessage)|由架構呼叫以在分派訊息之前轉譯視窗訊息。 (覆寫 `CMFCButton::PreTranslateMessage`。)|
|[CMFCMenuButton：： System.windows.window.sizetocontent](#sizetocontent)|根據按鈕的文字和影像大小來變更按鈕的大小。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMFCMenuButton：： m_bOSMenu](#m_bosmenu)|指定是否要顯示預設系統快顯功能表，或使用 [CCoNtextMenuManager：： trackpopupmenu 讓](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu)。|
|[CMFCMenuButton：： m_bRightArrow](#m_brightarrow)|指定快顯功能表是否會顯示在按鈕的下方或右邊。|
|[CMFCMenuButton：： m_bStayPressed](#m_bstaypressed)|指定功能表按鈕是否會在使用者放開按鈕之後變更其狀態。|
|[CMFCMenuButton：： m_hMenu](#m_hmenu)|附加的 Windows 功能表的控制碼。|
|[CMFCMenuButton：： m_nMenuResult](#m_nmenuresult)|指出使用者從快顯功能表中選取之專案的識別碼。|
|[CMFCMenuButton：： m_bDefaultClick](#m_bdefaultclick)| 允許預設 (按鈕文字/影像) 處理。|

## <a name="remarks"></a>備註

`CMFCMenuButton`類別衍生自[CMFCButton 類別](../../mfc/reference/cmfcbutton-class.md)，而後者又衍生自[CButton 類別](../../mfc/reference/cbutton-class.md)。 因此，您可以使用 `CMFCMenuButton` 程式碼中的相同方式來使用 `CButton` 。

當您建立時 `CMFCMenuButton` ，您必須將控制碼傳遞給相關聯的快顯功能表。 接下來，呼叫函數 `CMFCMenuButton::SizeToContent` 。 `CMFCMenuButton::SizeToContent` 檢查按鈕大小是否足以包含箭號，指向顯示快顯視窗的位置，也就是按鈕的下方或右邊。

## <a name="example"></a>範例

下列範例示範如何設定附加至按鈕的功能表控制碼、根據按鈕的文字和影像大小調整按鈕的大小，以及設定架構所顯示的快顯功能表。 此程式碼片段是 [新控制項範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#38](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#39](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)

## <a name="requirements"></a>規格需求

**標頭：** afxmenubutton。h

## <a name="cmfcmenubuttoncmfcmenubutton"></a><a name="cmfcmenubutton"></a> CMFCMenuButton：： CMFCMenuButton

建立新的 [CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md) 物件。

```
CMFCMenuButton();
```

## <a name="cmfcmenubuttonm_bosmenu"></a><a name="m_bosmenu"></a> CMFCMenuButton：： m_bOSMenu

布林成員變數，指出架構所顯示的快顯功能表。

```
BOOL m_bOSMenu;
```

### <a name="remarks"></a>備註

如果 `m_bOSMenu` 為 TRUE，架構會呼叫 `TrackPopupMenu` 這個物件的繼承方法。 否則，架構會呼叫 [CCoNtextMenuManager：： trackpopupmenu 讓](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu)。

## <a name="cmfcmenubuttonm_brightarrow"></a><a name="m_brightarrow"></a> CMFCMenuButton：： m_bRightArrow

指出快顯功能表位置的布林成員變數。

```
BOOL m_bRightArrow;
```

### <a name="remarks"></a>備註

當使用者按下功能表按鈕時，應用程式會顯示快顯功能表。 架構會顯示快顯功能表，其位於按鈕的旁邊或右邊。 按鈕也有一個小箭號，指出快顯功能表出現的位置。 若 `m_bRightArrow` 為 TRUE，則架構會顯示按鈕右邊的快顯功能表。 否則，它會在按鈕下方顯示快顯功能表。

## <a name="cmfcmenubuttonm_bstaypressed"></a><a name="m_bstaypressed"></a> CMFCMenuButton：： m_bStayPressed

布林成員變數，指出當使用者在快顯功能表中進行選取時，是否要按下功能表按鈕。

```
BOOL m_bStayPressed;
```

### <a name="remarks"></a>備註

如果 `m_bStayPressed` 成員為 FALSE，當使用者按一下按鈕時，就不會按下功能表按鈕。 在此情況下，架構只會顯示快顯功能表。

如果 `m_bStayPressed` 成員為 TRUE，當使用者按一下按鈕時，就會按下功能表按鈕。 在使用者關閉快顯功能表之前，您可以進行選取或取消，以保持按下狀態。

## <a name="cmfcmenubuttonm_hmenu"></a><a name="m_hmenu"></a> CMFCMenuButton：： m_hMenu

附加功能表的控制碼。

```
HMENU m_hMenu;
```

### <a name="remarks"></a>備註

當使用者按一下功能表按鈕時，架構會顯示這個成員變數所指出的功能表。

## <a name="cmfcmenubuttonm_nmenuresult"></a><a name="m_nmenuresult"></a> CMFCMenuButton：： m_nMenuResult

整數，指出使用者從快顯功能表中選取的專案。

```
int m_nMenuResult;
```

### <a name="remarks"></a>備註

如果使用者取消功能表而未進行選取或發生錯誤，則此成員變數的值為零。

## <a name="cmfcmenubuttonm_bdefaultclick"></a><a name="m_bdefaultclick"></a> CMFCMenuButton：： m_bDefaultClick

允許預設處理按鈕上的文字或影像。

```
BOOL  m_bDefaultClick;
```

### <a name="remarks"></a>備註

將 m_bDefaultClick 設定為 false，會在您按一下按鈕上的任何位置時，讓按鈕顯示功能表。

## <a name="cmfcmenubuttonpretranslatemessage"></a><a name="pretranslatemessage"></a> CMFCMenuButton：:P reTranslateMessage

由架構呼叫以在分派訊息之前轉譯視窗訊息。

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>參數

*pMsg*<br/>
在指向包含要處理之訊息的 [MSG](/windows/win32/api/winuser/ns-winuser-msg) 結構。

### <a name="return-value"></a>傳回值

如果訊息已轉譯且不應分派，則為非零;如果訊息未轉譯且應該分派，則為0。

### <a name="remarks"></a>備註

## <a name="cmfcmenubuttonsizetocontent"></a><a name="sizetocontent"></a> CMFCMenuButton：： System.windows.window.sizetocontent

根據按鈕的文字大小和影像大小，變更按鈕的大小。

```
virtual CSize SizeToContent(BOOL bCalcOnly = FALSE);
```

### <a name="parameters"></a>參數

*bCalcOnly*<br/>
在布林值參數，指出這個方法是否調整按鈕的大小。

### <a name="return-value"></a>傳回值

[CSize](../../atl-mfc-shared/reference/csize-class.md)物件，指定按鈕的新大小。

### <a name="remarks"></a>備註

如果您呼叫此函式，且 *bCalcOnly* 為 TRUE，則 `SizeToContent` 只會計算按鈕的新大小。

會計算按鈕的新大小，以符合按鈕文字、影像和箭號。 此架構也會將水準邊緣的10圖元預先定義邊界加上垂直邊緣的5圖元。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCButton 類別](../../mfc/reference/cmfcbutton-class.md)
