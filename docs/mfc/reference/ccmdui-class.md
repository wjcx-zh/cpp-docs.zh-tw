---
title: CCmdUI 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 288dbaa5bb3c0d7f1731d996e6f4b1daed93d14e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411367"
---
# <a name="ccmdui-class"></a>CCmdUI 類別

只有在使用`ON_UPDATE_COMMAND_UI`中的處理常式`CCmdTarget`-衍生的類別。

## <a name="syntax"></a>語法

```
class CCmdUI
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CCmdUI::ContinueRouting](#continuerouting)|會告知命令路由機制繼續路由處理常式鏈結中向下目前的訊息。|
|[CCmdUI::Enable](#enable)|啟用或停用此命令的使用者介面項目。|
|[CCmdUI::SetCheck](#setcheck)|設定核取狀態，此命令的使用者介面項目。|
|[CCmdUI::SetRadio](#setradio)|例如`SetCheck`成員函式，但會作選項群組。|
|[CCmdUI::SetText](#settext)|設定使用者介面項目，此命令的文字。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CCmdUI::m_nID](#m_nid)|使用者介面物件的識別碼。|
|[CCmdUI::m_nIndex](#m_nindex)|使用者介面物件的索引。|
|[CCmdUI::m_pMenu](#m_pmenu)|指向由功能表`CCmdUI`物件。|
|[CCmdUI::m_pOther](#m_pother)|要傳送通知給視窗物件的點。|
|[CCmdUI::m_pSubMenu](#m_psubmenu)|指向包含所代表的子功能表`CCmdUI`物件。|

## <a name="remarks"></a>備註

`CCmdUI` 沒有基底類別。

當您的應用程式的使用者需要提取功能表中，每個功能表項目需要知道是否應該顯示為已啟用或停用。 功能表命令的目標會提供這項資訊藉由實作 ON_UPDATE_COMMAND_UI 處理常式。 針對每個命令的使用者介面物件，在您的應用程式中，使用 [屬性] 視窗來建立訊息對應項目和函式原型，每個處理常式。

當功能表提取時，架構搜尋，並呼叫每個 ON_UPDATE_COMMAND_UI 處理常式時，每個處理常式會呼叫`CCmdUI`成員函式，如`Enable`和`Check`，framework 然後適當地顯示每個功能表項目。

功能表項目可以取代與控制列按鈕或其他命令的使用者介面物件，而不需要變更中的程式碼`ON_UPDATE_COMMAND_UI`處理常式。

下表摘要說明影響`CCmdUI`的成員函式具有各個命令使用者介面項目。

|使用者介面項目|啟用|SetCheck|SetRadio|SetText|
|--------------------------|------------|--------------|--------------|-------------|
|Menu item|啟用或停用|檢查或取消核取|使用點的檢查|設定項目文字|
|工具列按鈕|啟用或停用|選取、 取消選取，或不確定|與 `SetCheck` 相同|（不適用）|
|狀態列窗格|讓文字可見或不可見|設定顯或一般框線|與 `SetCheck` 相同|設定窗格中的文字|
|在一般的按鈕 `CDialogBar`|啟用或停用|檢查或取消核取方塊|與 `SetCheck` 相同|設定按鈕文字|
|在正常的程式控制 `CDialogBar`|啟用或停用|（不適用）|（不適用）|設定視窗的文字|

如需使用這個類別的詳細資訊，請參閱 <<c0> [ 如何更新使用者介面物件](../../mfc/how-to-update-user-interface-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`CCmdUI`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="continuerouting"></a>  CCmdUI::ContinueRouting

呼叫此成員函式，來告訴命令路由機制，以繼續路由處理常式鏈結中向下目前的訊息。

```
void ContinueRouting();
```

### <a name="remarks"></a>備註

這是進階的成員函式，應該會傳回 FALSE 的 ON_COMMAND_EX 處理常式搭配使用。 如需詳細資訊，請參閱 <<c0> [ 技術的附註 6](../../mfc/tn006-message-maps.md)。

##  <a name="enable"></a>  CCmdUI::Enable

呼叫此成員函式可啟用或停用此命令的使用者介面項目。

```
virtual void Enable(BOOL bOn = TRUE);
```

### <a name="parameters"></a>參數

*bOn*<br/>
如果為 true，則在啟用項目，FALSE 來停用它。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#46](../../mfc/codesnippet/cpp/ccmdui-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#47](../../mfc/codesnippet/cpp/ccmdui-class_2.cpp)]

##  <a name="m_nid"></a>  CCmdUI::m_nID

功能表項目、 工具列按鈕或由其他使用者介面物件的識別碼`CCmdUI`物件。

```
UINT m_nID;
```

##  <a name="m_nindex"></a>  CCmdUI::m_nIndex

功能表項目、 工具列按鈕或由其他使用者介面物件的索引`CCmdUI`物件。

```
UINT m_nIndex;
```

##  <a name="m_pmenu"></a>  CCmdUI::m_pMenu

指標 (的`CMenu`型別) 所表示的功能表`CCmdUI`物件。

```
CMenu* m_pMenu;
```

### <a name="remarks"></a>備註

如果不是一個功能表項目，則為 NULL。

##  <a name="m_psubmenu"></a>  CCmdUI::m_pSubMenu

指標 (的`CMenu`類型) 來包含所代表的子功能表`CCmdUI`物件。

```
CMenu* m_pSubMenu;
```

### <a name="remarks"></a>備註

如果不是一個功能表項目，則為 NULL。 如果子功能表中的快顯視窗中， *m_nID*包含快顯功能表中的第一個項目識別碼。 如需詳細資訊，請參閱 <<c0> [ 技術提示 21](../../mfc/tn021-command-and-message-routing.md)。

##  <a name="m_pother"></a>  CCmdUI::m_pOther

指標 (型別`CWnd`) 視窗物件，例如工具或 [狀態] 列中，傳送通知。

```
CWnd* m_pOther;
```

### <a name="remarks"></a>備註

如果項目是功能表或非 NULL`CWnd`物件。

##  <a name="setcheck"></a>  CCmdUI::SetCheck

呼叫此成員函式，將此命令的使用者介面項目設定為適當的核取狀態。

```
virtual void SetCheck(int nCheck = 1);
```

### <a name="parameters"></a>參數

*n*<br/>
指定設定的核取狀態。 如果取消核取 0，;如果 1，檢查;，和 2，如果設定為不定。

### <a name="remarks"></a>備註

此成員函式適用於功能表項目和工具列按鈕。 不定狀態僅適用於工具列按鈕。

##  <a name="setradio"></a>  CCmdUI::SetRadio

呼叫此成員函式，將此命令的使用者介面項目設定為適當的核取狀態。

```
virtual void SetRadio(BOOL bOn = TRUE);
```

### <a name="parameters"></a>參數

*bOn*<br/>
TRUE 表示啟用項目;否則為 FALSE。

### <a name="remarks"></a>備註

這個成員函式`SetCheck`，只不過它作做為選項群組一部分的使用者介面項目。 取消核取 在群組中的其他項目不會自動除非項目本身維護選項群組行為。

##  <a name="settext"></a>  CCmdUI::SetText

呼叫此成員函式設定的使用者介面項目，此命令的文字。

```
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

*lpszText*<br/>
文字字串的指標。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#48](../../mfc/codesnippet/cpp/ccmdui-class_3.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 MDI](../../visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)
