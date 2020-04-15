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
ms.openlocfilehash: 929fc1c8166f249fe3babc724b2c0bcd9cb99676
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369676"
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
|[CMFC選單按鈕:CMFC選單按鈕](#cmfcmenubutton)|建構 `CMFCMenuButton` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCMenuButton::PreTranslateMessage](#pretranslatemessage)|由框架調用,在發送視窗消息之前進行轉換。 (覆寫 `CMFCButton::PreTranslateMessage`。)|
|[CMFCMenu按鈕::大小到內容](#sizetocontent)|根據按鈕的文本和圖像大小更改按鈕的大小。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMFC選單按鈕::m_bOSMenu](#m_bosmenu)|指定顯示預設系統彈出選單還是使用[CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu)。|
|[CMFC功能表按鈕::m_bRightArrow](#m_brightarrow)|指定彈出功能表是顯示在按鈕的下方還是右側。|
|[CMFC選單按鈕:m_bStayPressed](#m_bstaypressed)|指定功能表按鈕在使用者釋放按鈕后是否更改其狀態。|
|[CMFC選單按鈕:m_hMenu](#m_hmenu)|附加 Windows 功能表的句柄。|
|[CMFC選單按鈕::m_nMenuResult](#m_nmenuresult)|指示用戶從彈出式功能表中選擇的項的標識碼。|
|[CMFC功能表按鈕::m_bDefaultClick](#m_bdefaultclick)| 允許預設(按鈕文本/圖像)處理。|

## <a name="remarks"></a>備註

類別`CMFCMenuButton`的 cTTTTTButton,[而 CMFCButton 類別](../../mfc/reference/cmfcbutton-class.md)則派生自[CButton 類別](../../mfc/reference/cbutton-class.md)。 因此,您可以在程式碼中`CMFCMenuButton`使用與`CButton`使用相同的方式使用 。

創建`CMFCMenuButton`時 ,必須將句柄傳遞到關聯的彈出式功能表。 接下來,呼叫函數`CMFCMenuButton::SizeToContent`。 `CMFCMenuButton::SizeToContent`檢查按鈕大小是否足以包含指向彈出視窗顯示位置的箭頭,即按鈕下方或右側。

## <a name="example"></a>範例

下面的範例展示如何設定附加到按鈕的選單的句柄,根據按鈕的文本和圖像大小調整按鈕的大小,以及設置框架顯示的彈出式功能表。 此代碼段是[「新控制件」範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#38](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#39](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)

## <a name="requirements"></a>需求

**標題:** afxmenu按鈕.h

## <a name="cmfcmenubuttoncmfcmenubutton"></a><a name="cmfcmenubutton"></a>CMFC選單按鈕:CMFC選單按鈕

建構新的[CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)物件。

```
CMFCMenuButton();
```

## <a name="cmfcmenubuttonm_bosmenu"></a><a name="m_bosmenu"></a>CMFC選單按鈕::m_bOSMenu

一個布爾成員變數,指示框架顯示的彈出功能表。

```
BOOL m_bOSMenu;
```

### <a name="remarks"></a>備註

如果`m_bOSMenu`為 TRUE,則框架將`TrackPopupMenu`調用 此物件的繼承方法。 否則,框架將調用[CContextMenuManager::追蹤彈出選單](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu)。

## <a name="cmfcmenubuttonm_brightarrow"></a><a name="m_brightarrow"></a>CMFC功能表按鈕::m_bRightArrow

指示彈出功能表位置的布爾成員變數。

```
BOOL m_bRightArrow;
```

### <a name="remarks"></a>備註

當使用者按下功能表按鈕時,應用程式將顯示一個彈出式功能表。 框架將在按鈕下方或按鈕右側顯示彈出式功能表。 該按鈕還有一個小箭頭,指示彈出功能表的顯示位置。 如果`m_bRightArrow`為 TRUE,則框架將顯示按鈕右側的彈出式功能表。 否則,它會在按鈕下顯示彈出式功能表。

## <a name="cmfcmenubuttonm_bstaypressed"></a><a name="m_bstaypressed"></a>CMFC選單按鈕:m_bStayPressed

Boolean 成員變數,指示用戶從彈出式功能表中進行選擇時選單按鈕是否顯示按下。

```
BOOL m_bStayPressed;
```

### <a name="remarks"></a>備註

如果`m_bStayPressed`成員為 FALSE,則當使用單擊該按鈕時,功能表按鈕不會按下。 在這種情況下,框架僅顯示彈出式功能表。

如果`m_bStayPressed`成員為 TRUE,則當用戶按下該按鈕時,將按下選單按鈕。 它保持按下,直到使用者關閉彈出功能表後,通過選擇或取消。

## <a name="cmfcmenubuttonm_hmenu"></a><a name="m_hmenu"></a>CMFC選單按鈕:m_hMenu

附加功能表的句柄。

```
HMENU m_hMenu;
```

### <a name="remarks"></a>備註

當用戶單擊功能表按鈕時,框架將顯示此成員變數指示的菜單。

## <a name="cmfcmenubuttonm_nmenuresult"></a><a name="m_nmenuresult"></a>CMFC選單按鈕::m_nMenuResult

指示用戶從彈出式功能表中選擇哪個項的整數。

```
int m_nMenuResult;
```

### <a name="remarks"></a>備註

如果使用者取消功能表而不進行選擇或發生錯誤,則此成員變數的值為零。

## <a name="cmfcmenubuttonm_bdefaultclick"></a><a name="m_bdefaultclick"></a>CMFC功能表按鈕::m_bDefaultClick

允許默認處理按鈕上的文本或圖像。

```
BOOL  m_bDefaultClick;
```

### <a name="remarks"></a>備註

將m_bDefaultClick設定為 false 會導致按鈕在按一下按鈕上的任意位置時顯示選單。

## <a name="cmfcmenubuttonm_nmenuresult"></a><a name="m_nmenuresult"></a>CMFC選單按鈕::m_nMenuResult

指示用戶從彈出式功能表中選擇哪個項的整數。

```
int m_nMenuResult;
```

### <a name="remarks"></a>備註

## <a name="cmfcmenubuttonpretranslatemessage"></a><a name="pretranslatemessage"></a>CMFCMenu按鈕::P重新翻譯訊息

由框架調用,在發送視窗消息之前進行轉換。

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>參數

*pMsg*<br/>
[在]指向包含要處理的消息的[MSG](/windows/win32/api/winuser/ns-winuser-msg)結構。

### <a name="return-value"></a>傳回值

如果郵件已翻譯且不應發送,則非零;0 如果郵件未翻譯,則應調度。

### <a name="remarks"></a>備註

## <a name="cmfcmenubuttonsizetocontent"></a><a name="sizetocontent"></a>CMFCMenu按鈕::大小到內容

根據按鈕的文字大小和圖像大小更改按鈕的大小。

```
virtual CSize SizeToContent(BOOL bCalcOnly = FALSE);
```

### <a name="parameters"></a>參數

*bCalcOnly*<br/>
[在]一個布爾參數,指示此方法是否調整按鈕的大小。

### <a name="return-value"></a>傳回值

指定按鈕新[大小的 CSize](../../atl-mfc-shared/reference/csize-class.md)物件。

### <a name="remarks"></a>備註

如果調用此函數,並且*bCalcOnly*為`SizeToContent`TRUE,則僅計算按鈕的新大小。

計算按鈕的新大小以適合按鈕文本、圖像和箭頭。 框架還增加了預定義的邊距為 10 像素的水平邊和 5 像素的垂直邊。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCButton 類別](../../mfc/reference/cmfcbutton-class.md)
