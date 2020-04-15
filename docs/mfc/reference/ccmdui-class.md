---
title: CCmdUI 類別
ms.date: 09/06/2019
f1_keywords:
- CCmdUI
- AFXWIN/CCmdUI
- AFXWIN/CCmdUI::ContinueRouting
- AFXWIN/CCmdUI::Enable
- AFXWIN/CCmdUI::SetCheck
- AFXWIN/CCmdUI::SetRadio
- AFXWIN/CCmdUI::SetText
- AFXWIN/CCmdUI::m_nID
- AFXWIN/CCmdUI::m_nIndex
- AFXWIN/CCmdUI::m_pMenu
- AFXWIN/CCmdUI::m_pOther
- AFXWIN/CCmdUI::m_pSubMenu
helpviewer_keywords:
- CCmdUI [MFC], ContinueRouting
- CCmdUI [MFC], Enable
- CCmdUI [MFC], SetCheck
- CCmdUI [MFC], SetRadio
- CCmdUI [MFC], SetText
- CCmdUI [MFC], m_nID
- CCmdUI [MFC], m_nIndex
- CCmdUI [MFC], m_pMenu
- CCmdUI [MFC], m_pOther
- CCmdUI [MFC], m_pSubMenu
ms.assetid: 04eaaaf5-f510-48ab-b425-94665ba24766
ms.openlocfilehash: 5f411890575c07e471b02c423aa42ec5bf51ac0a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352280"
---
# <a name="ccmdui-class"></a>CCmdUI 類別

僅在`ON_UPDATE_COMMAND_UI``CCmdTarget`派生類中的處理程式中使用。

## <a name="syntax"></a>語法

```
class CCmdUI
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CCmdUI::繼續路由](#continuerouting)|告訴命令路由機制繼續將當前消息路由到處理程序鏈中。|
|[CmDUI:啟用](#enable)|啟用或禁用此命令的用戶介面項。|
|[CmdUI::設定檢查](#setcheck)|設定此命令的用戶介面項的檢查狀態。|
|[CmdUI::SetRadio](#setradio)|與成員`SetCheck`函數一樣,但在無線電組上運行。|
|[CmdUI::設定文字](#settext)|設定此指令的用戶介面項的文本。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CCmdUI::m_nID](#m_nid)|使用者介面物件的 ID。|
|[CCmdUI::m_nIndex](#m_nindex)|用戶介面物件的索引。|
|[CmDUI::m_pMenu](#m_pmenu)|指向物件表示的`CCmdUI`功能表。|
|[CmDUI::m_pOther](#m_pother)|指向發送通知的視窗物件。|
|[CmdUI::m_pSubMenu](#m_psubmenu)|指向由物件表示的`CCmdUI`包含的子功能表。|

## <a name="remarks"></a>備註

`CCmdUI`沒有基類。

當應用程式的使用者拉下功能表時,每個功能表項需要知道它是應該顯示為已啟用還是禁用。 功能表命令的目標通過實現ON_UPDATE_COMMAND_UI處理程式來提供此資訊。 對於應用程式中的每個命令使用者介面物件,請使用[類嚮導](mfc-class-wizard.md)或**屬性**視窗(**類視圖**中)為每個處理程式創建消息映射條目和函數原型。

當菜單拉下時,框架搜索並調用每個ON_UPDATE_COMMAND_UI處理程式,每個處理程式調用`CCmdUI`成員函數,`Enable`如`Check`和 ,然後框架適當地顯示每個功能表項。

功能表項可以替換為控制欄按鈕或其他命令使用者介面物件,而無需更改處理程式中`ON_UPDATE_COMMAND_UI`的代碼。

下表總結了成員函數對各種命令`CCmdUI`用戶介面項的影響。

|使用者介面專案|啟用|設定檢查|SetRadio|設定文字|
|--------------------------|------------|--------------|--------------|-------------|
|功能表項目|開啟或關閉|檢查或取消檢查|使用點進行檢查|設定項目文字|
|工具列按鈕|開啟或關閉|選擇、取消選擇或不確定|與 `SetCheck` 相同|(不適用)|
|狀態列窗格|使文字可見或不可見|設定彈出邊框或正常框框|與 `SetCheck` 相同|設定窗格文字|
|中法線按鈕`CDialogBar`|開啟或關閉|勾選或取消選取的選擇的欄位|與 `SetCheck` 相同|設定按鈕文字|
|中的正常控制`CDialogBar`|開啟或關閉|(不適用)|(不適用)|設定視窗文字|

有關此類使用的詳細資訊,請參閱[如何更新使用者介面物件](../../mfc/how-to-update-user-interface-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CCmdUI`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="ccmduicontinuerouting"></a><a name="continuerouting"></a>CCmdUI::繼續路由

調用此成員函數告訴命令路由機制繼續將當前消息路由到處理程序鏈中。

```
void ContinueRouting();
```

### <a name="remarks"></a>備註

這是一個高級成員函數,應與返回 FALSE 的ON_COMMAND_EX處理程式結合使用。 有關詳細資訊,請參閱[技術說明 6](../../mfc/tn006-message-maps.md)。

## <a name="ccmduienable"></a><a name="enable"></a>CmDUI:啟用

呼叫此成員函數以啟用或禁用此命令的用戶介面項。

```
virtual void Enable(BOOL bOn = TRUE);
```

### <a name="parameters"></a>參數

*邦*<br/>
TRUE 啟用該專案,FALSE 將其禁用。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#46](../../mfc/codesnippet/cpp/ccmdui-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#47](../../mfc/codesnippet/cpp/ccmdui-class_2.cpp)]

## <a name="ccmduim_nid"></a><a name="m_nid"></a>CCmdUI::m_nID

選單項、工具列按鈕或`CCmdUI`物件表示的其他使用者介面對象的 ID。

```
UINT m_nID;
```

## <a name="ccmduim_nindex"></a><a name="m_nindex"></a>CCmdUI::m_nIndex

功能表項、工具列按鈕或`CCmdUI`物件表示的其他使用者介面物件的索引。

```
UINT m_nIndex;
```

## <a name="ccmduim_pmenu"></a><a name="m_pmenu"></a>CmDUI::m_pMenu

指向物件表示`CMenu`的功能表`CCmdUI`的指標(類型)。

```
CMenu* m_pMenu;
```

### <a name="remarks"></a>備註

如果專案不是功能表,則為 NULL。

## <a name="ccmduim_psubmenu"></a><a name="m_psubmenu"></a>CmdUI::m_pSubMenu

指向由物件`CMenu`表示的包含子功能表`CCmdUI`的指標(類型)。

```
CMenu* m_pSubMenu;
```

### <a name="remarks"></a>備註

如果專案不是功能表,則為 NULL。 如果子功能表是彈出視窗 *,m_nID*包含彈出式功能表中第一項的 ID。 有關詳細資訊,請參閱[技術說明 21](../../mfc/tn021-command-and-message-routing.md)。

## <a name="ccmduim_pother"></a><a name="m_pother"></a>CmDUI::m_pOther

指向視窗物件的指標`CWnd`(類型 )(如工具或狀態列)發送通知。

```
CWnd* m_pOther;
```

### <a name="remarks"></a>備註

如果項目是功能表或非`CWnd`物件,則 NULL。

## <a name="ccmduisetcheck"></a><a name="setcheck"></a>CmdUI::設定檢查

調用此成員函數以將此命令的用戶介面項設置為相應的檢查狀態。

```
virtual void SetCheck(int nCheck = 1);
```

### <a name="parameters"></a>參數

*N檢查*<br/>
指定要設置的檢查狀態。 如果為 0,則取消選中;如果為 0,則取消選中。如果為 1,則進行檢查;如果為 2,則設置不確定。

### <a name="remarks"></a>備註

此成員函數適用於功能表項和工具列按鈕。 不確定狀態僅適用於工具列按鈕。

## <a name="ccmduisetradio"></a><a name="setradio"></a>CmdUI::SetRadio

調用此成員函數以將此命令的用戶介面項設置為相應的檢查狀態。

```
virtual void SetRadio(BOOL bOn = TRUE);
```

### <a name="parameters"></a>參數

*邦*<br/>
TRUE 以啟用專案;否則 FALSE。

### <a name="remarks"></a>備註

此成員函數的操作方式`SetCheck`與類似,只不過它操作作為無線電組的一部分的用戶介面項。 除非項本身維護無線電組行為,否則取消選中組中的其他項不是自動的。

## <a name="ccmduisettext"></a><a name="settext"></a>CmdUI::設定文字

呼叫此成員函數以設定此命令的用戶介面項的文本。

```
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

*lpszText*<br/>
指向文字字串的指標。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#48](../../mfc/codesnippet/cpp/ccmdui-class_3.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 樣品 MDI](../../overview/visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)
