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
ms.openlocfilehash: d7c23cbda0a5af4dc3fa6b2d9f59497acc9bf5ff
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505202"
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
|[CMFCMenuButton:: CMFCMenuButton](#cmfcmenubutton)|建構 `CMFCMenuButton` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCMenuButton::PreTranslateMessage](#pretranslatemessage)|由架構呼叫以在分派之前轉譯視窗訊息。 (覆寫 `CMFCButton::PreTranslateMessage`。)|
|[CMFCMenuButton::SizeToContent](#sizetocontent)|根據按鈕的文字和影像大小變更其大小。|

### <a name="data-members"></a>資料成員

|名稱|說明|
|----------|-----------------|
|[CMFCMenuButton::m_bOSMenu](#m_bosmenu)|指定是否要顯示預設的系統快顯功能表, 或使用[CCoNtextMenuManager:: trackpopupmenu 讓](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu)。|
|[CMFCMenuButton::m_bRightArrow](#m_brightarrow)|指定快顯功能表是否會出現在按鈕的下方或右邊。|
|[CMFCMenuButton::m_bStayPressed](#m_bstaypressed)|指定在使用者放開按鈕之後, 功能表按鈕是否會變更其狀態。|
|[CMFCMenuButton::m_hMenu](#m_hmenu)|附加的 Windows 功能表的控制碼。|
|[CMFCMenuButton::m_nMenuResult](#m_nmenuresult)|表示使用者在快顯功能表中選取之專案的識別碼。|
|[CMFCMenuButton::m_bDefaultClick](#m_bdefaultclick)| 允許預設值 (在按鈕文字/影像上) 處理。|

## <a name="remarks"></a>備註

類別衍生自[CMFCButton 類別](../../mfc/reference/cmfcbutton-class.md), 而後者又衍生自[CButton 類別。](../../mfc/reference/cbutton-class.md) `CMFCMenuButton` 因此, 您可以在`CMFCMenuButton`程式碼中使用, 方法與使用`CButton`的方式相同。

當您建立`CMFCMenuButton`時, 您必須將控制碼傳入相關聯的快顯功能表。 接下來, 呼叫`CMFCMenuButton::SizeToContent`函式。 `CMFCMenuButton::SizeToContent`檢查按鈕大小是否足以包含指向快顯視窗顯示位置的箭號, 也就是在按鈕的下方或右邊。

## <a name="example"></a>範例

下列範例示範如何設定附加至按鈕之功能表的控制碼、根據按鈕的文字和影像大小來調整按鈕的大小, 以及設定架構所顯示的快顯功能表。 此程式碼片段是[新控制項範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#38](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#39](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)

## <a name="requirements"></a>需求

**標頭:** afxmenubutton。h

##  <a name="cmfcmenubutton"></a>CMFCMenuButton:: CMFCMenuButton

構造新的[CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)物件。

```
CMFCMenuButton();
```

##  <a name="m_bosmenu"></a>CMFCMenuButton:: m_bOSMenu

布林成員變數, 指出架構顯示的快顯功能表。

```
BOOL m_bOSMenu;
```

### <a name="remarks"></a>備註

如果`m_bOSMenu`為 TRUE, 則架構會呼叫這個`TrackPopupMenu`物件的繼承方法。 否則, 架構會呼叫[CCoNtextMenuManager:: trackpopupmenu 讓](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu)。

##  <a name="m_brightarrow"></a>CMFCMenuButton:: m_bRightArrow

指出快顯功能表位置的布林成員變數。

```
BOOL m_bRightArrow;
```

### <a name="remarks"></a>備註

當使用者按下功能表按鈕時, 應用程式會顯示快顯功能表。 此架構會在按鈕下方或按鈕右邊顯示快顯功能表。 此按鈕也有一個小箭號, 指出快顯功能表的顯示位置。 如果`m_bRightArrow`為 TRUE, 則架構會顯示按鈕右邊的快顯功能表。 否則, 它會顯示按鈕底下的快顯功能表。

##  <a name="m_bstaypressed"></a>CMFCMenuButton:: m_bStayPressed

布林成員變數, 指出當使用者從快顯功能表進行選取時, 是否按下 [功能表] 按鈕。

```
BOOL m_bStayPressed;
```

### <a name="remarks"></a>備註

`m_bStayPressed`如果成員為 FALSE, 則當使用者按一下按鈕時, 不會按下功能表按鈕。 在此情況下, 架構只會顯示快顯功能表。

`m_bStayPressed`如果成員為 TRUE, 則當使用者按一下按鈕時, 就會按下功能表按鈕。 在使用者關閉快顯功能表 (藉由進行選取或取消) 之前, 會保持按下狀態。

##  <a name="m_hmenu"></a>CMFCMenuButton:: m_hMenu

附加功能表的控制碼。

```
HMENU m_hMenu;
```

### <a name="remarks"></a>備註

當使用者按一下功能表按鈕時, 架構會顯示此成員變數所指定的功能表。

##  <a name="m_nmenuresult"></a>CMFCMenuButton:: m_nMenuResult

整數, 表示使用者從快顯功能表選取的專案。

```
int m_nMenuResult;
```

### <a name="remarks"></a>備註

如果使用者取消功能表而未進行選取, 或發生錯誤, 這個成員變數的值就是零。

##  <a name="m_bdefaultclick"></a>CMFCMenuButton:: m_bDefaultClick

允許在按鈕上預設處理文字或影像。

```
BOOL  m_bDefaultClick;
```

### <a name="remarks"></a>備註

將 m_bDefaultClick 設定為 false, 會在您按一下按鈕上的任何位置時, 讓按鈕顯示功能表。

##  <a name="m_nmenuresult"></a>CMFCMenuButton:: m_nMenuResult

整數, 表示使用者從快顯功能表選取的專案。

```
int m_nMenuResult;
```

### <a name="remarks"></a>備註

##  <a name="pretranslatemessage"></a>CMFCMenuButton::P reTranslateMessage

由架構呼叫以在分派之前轉譯視窗訊息。

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>參數

*pMsg*<br/>
在指向包含要處理之訊息的[MSG](/windows/win32/api/winuser/ns-winuser-msg)結構。

### <a name="return-value"></a>傳回值

如果訊息已轉譯而不應分派, 則為非零值;如果訊息未轉譯且應分派, 則為0。

### <a name="remarks"></a>備註

##  <a name="sizetocontent"></a>CMFCMenuButton:: System.windows.window.sizetocontent

根據按鈕的文字大小和影像大小, 變更其大小。

```
virtual CSize SizeToContent(BOOL bCalcOnly = FALSE);
```

### <a name="parameters"></a>參數

*bCalcOnly*<br/>
在布林值參數, 指出這個方法是否會調整按鈕的大小。

### <a name="return-value"></a>傳回值

[CSize](../../atl-mfc-shared/reference/csize-class.md)物件, 指定按鈕的新大小。

### <a name="remarks"></a>備註

如果您呼叫此函式, 且*bCalcOnly*為`SizeToContent` TRUE, 則只會計算按鈕的新大小。

會計算按鈕的新大小, 以符合按鈕文字、影像和箭號。 此架構也會針對水準邊緣加上10圖元的預先定義邊界, 並針對垂直邊緣加入5圖元。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCButton 類別](../../mfc/reference/cmfcbutton-class.md)
