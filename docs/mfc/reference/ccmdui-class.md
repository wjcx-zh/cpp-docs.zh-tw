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
ms.openlocfilehash: 42aec2937cd81ebbb50482321b8deae001723d3a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418822"
---
# <a name="ccmdui-class"></a>CCmdUI 類別

只能在 `CCmdTarget`衍生類別中的 `ON_UPDATE_COMMAND_UI` 處理常式內使用。

## <a name="syntax"></a>語法

```
class CCmdUI
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CCmdUI：： ContinueRouting](#continuerouting)|告訴命令路由機制，繼續將目前的訊息路由傳送至處理常式鏈。|
|[CCmdUI：： Enable](#enable)|啟用或停用此命令的使用者介面專案。|
|[CCmdUI：： SetCheck](#setcheck)|設定此命令之使用者介面專案的檢查狀態。|
|[CCmdUI：： SetRadio](#setradio)|如同 `SetCheck` 成員函式，但會在選項按鈕群組上運作。|
|[CCmdUI：： SetText](#settext)|設定此命令之使用者介面專案的文字。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CCmdUI：： m_nID](#m_nid)|使用者介面物件的識別碼。|
|[CCmdUI：： m_nIndex](#m_nindex)|使用者介面物件的索引。|
|[CCmdUI：： m_pMenu](#m_pmenu)|指向 `CCmdUI` 物件所代表的功能表。|
|[CCmdUI：： m_pOther](#m_pother)|指向傳送通知的視窗物件。|
|[CCmdUI：： m_pSubMenu](#m_psubmenu)|指向 `CCmdUI` 物件所代表的包含子功能表。|

## <a name="remarks"></a>備註

`CCmdUI` 沒有基類。

當您應用程式的使用者提取功能表時，每個功能表項目都必須知道它應該顯示為 [已啟用] 或 [已停用]。 功能表命令的目標會藉由執行 ON_UPDATE_COMMAND_UI 處理常式來提供這項資訊。 針對應用程式中的每個命令使用者介面物件，使用 [[類別] [Wizard]](mfc-class-wizard.md)或 [**屬性**] 視窗（在**類別檢視**中），為每個處理常式建立訊息對應專案和函式原型。

當功能表向下提取時，架構會搜尋並呼叫每個 ON_UPDATE_COMMAND_UI 處理常式，每個處理常式都會呼叫 `CCmdUI` 的成員函式，例如 `Enable` 和 `Check`，然後架構會適當地顯示每個功能表項目。

功能表項目可以取代為控制列按鈕或其他命令使用者介面物件，而不需要變更 `ON_UPDATE_COMMAND_UI` 處理常式內的程式碼。

下表摘要說明 `CCmdUI`的成員函式在各種命令使用者介面專案上的效果。

|使用者介面專案|啟用|SetCheck|SetRadio|SetText|
|--------------------------|------------|--------------|--------------|-------------|
|功能表項目|啟用或停用|檢查或取消核取|使用點檢查|設定專案文字|
|工具列按鈕|啟用或停用|選取、取消選擇或不確定|與 `SetCheck` 相同|(不適用)|
|狀態列窗格|讓文字變成可見或不可見|設定快顯或一般框線|與 `SetCheck` 相同|設定窗格文字|
|`CDialogBar` 中的 [一般] 按鈕|啟用或停用|[檢查或取消選取] 核取方塊|與 `SetCheck` 相同|設定按鈕文字|
|`CDialogBar` 中的一般控制項|啟用或停用|(不適用)|(不適用)|設定視窗文字|

如需使用此類別的詳細資訊，請參閱[如何更新使用者介面物件](../../mfc/how-to-update-user-interface-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

`CCmdUI`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="continuerouting"></a>CCmdUI：： ContinueRouting

呼叫此成員函式，以告知命令路由機制繼續將目前的訊息路由傳送至處理常式鏈。

```
void ContinueRouting();
```

### <a name="remarks"></a>備註

這是應該與傳回 FALSE 的 ON_COMMAND_EX 處理常式搭配使用的 advanced 成員函式。 如需詳細資訊，請參閱[技術提示 6](../../mfc/tn006-message-maps.md)。

##  <a name="enable"></a>CCmdUI：： Enable

呼叫這個成員函式，以啟用或停用此命令的使用者介面專案。

```
virtual void Enable(BOOL bOn = TRUE);
```

### <a name="parameters"></a>參數

*bOn*<br/>
TRUE 表示啟用此專案，FALSE 則會停用它。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#46](../../mfc/codesnippet/cpp/ccmdui-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#47](../../mfc/codesnippet/cpp/ccmdui-class_2.cpp)]

##  <a name="m_nid"></a>CCmdUI：： m_nID

`CCmdUI` 物件所表示之功能表項目、工具列按鈕或其他使用者介面物件的識別碼。

```
UINT m_nID;
```

##  <a name="m_nindex"></a>CCmdUI：： m_nIndex

由 `CCmdUI` 物件表示的功能表項目、工具列按鈕或其他使用者介面物件的索引。

```
UINT m_nIndex;
```

##  <a name="m_pmenu"></a>CCmdUI：： m_pMenu

`CCmdUI` 物件所表示之功能表的指標（屬於 `CMenu` 類型）。

```
CMenu* m_pMenu;
```

### <a name="remarks"></a>備註

如果專案不是功能表，則為 Null。

##  <a name="m_psubmenu"></a>CCmdUI：： m_pSubMenu

`CCmdUI` 物件所代表之包含子功能表的指標（屬於 `CMenu` 類型）。

```
CMenu* m_pSubMenu;
```

### <a name="remarks"></a>備註

如果專案不是功能表，則為 Null。 如果子功能表是快顯視窗， *m_nID*包含快顯功能表中第一個專案的識別碼。 如需詳細資訊，請參閱[技術附注 21](../../mfc/tn021-command-and-message-routing.md)。

##  <a name="m_pother"></a>CCmdUI：： m_pOther

傳送通知的視窗物件（如工具或狀態列）的指標（類型 `CWnd`）。

```
CWnd* m_pOther;
```

### <a name="remarks"></a>備註

如果專案是功能表或非 `CWnd` 物件，則為 Null。

##  <a name="setcheck"></a>CCmdUI：： SetCheck

呼叫這個成員函式，將此命令的使用者介面專案設定為適當的檢查狀態。

```
virtual void SetCheck(int nCheck = 1);
```

### <a name="parameters"></a>參數

*nCheck*<br/>
指定要設定的檢查狀態。 如果為0，則取消選中;如果是1，則會檢查;如果為2，則設定不定。

### <a name="remarks"></a>備註

這個成員函式適用于功能表項目和工具列按鈕。 [不定] 狀態只適用于工具列按鈕。

##  <a name="setradio"></a>CCmdUI：： SetRadio

呼叫這個成員函式，將此命令的使用者介面專案設定為適當的檢查狀態。

```
virtual void SetRadio(BOOL bOn = TRUE);
```

### <a name="parameters"></a>參數

*bOn*<br/>
TRUE 表示啟用此專案;否則為 FALSE。

### <a name="remarks"></a>備註

這個成員函式的運作方式類似 `SetCheck`，不同之處在于它會在做為單選群組一部分的使用者介面專案上運作。 取消核取群組中的其他專案並不會自動進行，除非專案本身會維護單選群組的行為。

##  <a name="settext"></a>CCmdUI：： SetText

呼叫這個成員函式可設定此命令之使用者介面專案的文字。

```
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

*lpszText*<br/>
文字字串的指標。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#48](../../mfc/codesnippet/cpp/ccmdui-class_3.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 MDI](../../overview/visual-cpp-samples.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget 類別](../../mfc/reference/ccmdtarget-class.md)
