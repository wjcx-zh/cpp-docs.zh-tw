---
title: CSnapInItemImpl 類別
ms.date: 11/04/2016
f1_keywords:
- CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl::CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl::AddMenuItems
- ATLSNAP/ATL::CSnapInItemImpl::Command
- ATLSNAP/ATL::CSnapInItemImpl::CreatePropertyPages
- ATLSNAP/ATL::CSnapInItemImpl::FillData
- ATLSNAP/ATL::CSnapInItemImpl::GetResultPaneInfo
- ATLSNAP/ATL::CSnapInItemImpl::GetResultViewType
- ATLSNAP/ATL::CSnapInItemImpl::GetScopePaneInfo
- ATLSNAP/ATL::CSnapInItemImpl::Notify
- ATLSNAP/ATL::CSnapInItemImpl::QueryPagesFor
- ATLSNAP/ATL::CSnapInItemImpl::SetMenuInsertionFlags
- ATLSNAP/ATL::CSnapInItemImpl::SetToolbarButtonInfo
- ATLSNAP/ATL::CSnapInItemImpl::UpdateMenuState
- ATLSNAP/ATL::CSnapInItemImpl::UpdateToolbarButton
- ATLSNAP/ATL::CSnapInItemImpl::m_bstrDisplayName
- ATLSNAP/ATL::CSnapInItemImpl::m_resultDataItem
- ATLSNAP/ATL::CSnapInItemImpl::m_scopeDataItem
helpviewer_keywords:
- snap-ins, data items
- snap-ins, ATL support for
- CSnapInItemImpl class
- snap-ins
ms.assetid: 52caefbd-9eae-49b0-add2-d55524271aa7
ms.openlocfilehash: 27f3e8a17a9538a72a6592177a88a9b415b1a27c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62277704"
---
# <a name="csnapinitemimpl-class"></a>CSnapInItemImpl 類別

這個類別提供方法實作的嵌入式管理單元節點物件。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
template <class T, BOOL bIsExtension = FALSE>
class ATL_NO_VTABLE CSnapInItemImpl : public CSnapInItem
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類別，衍生自`CSnapInItemImpl`。

*bIsExtension*<br/>
如果物件是嵌入式管理單元延伸;，則為 TRUE。否則為 FALSE。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CSnapInItemImpl::CSnapInItemImpl](#csnapinitemimpl)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSnapInItemImpl::AddMenuItems](#addmenuitems)|將功能表項目加入至內容功能表中。|
|[CSnapInItemImpl::Command](#command)|選取自訂功能表項目時，請呼叫主控台。|
|[CSnapInItemImpl::CreatePropertyPages](#createpropertypages)|將頁面新增至嵌入式管理單元的屬性工作表。|
|[CSnapInItemImpl::FillData](#filldata)|嵌入式管理單元物件複製資訊到指定的資料流。|
|[CSnapInItemImpl::GetResultPaneInfo](#getresultpaneinfo)|擷取`RESULTDATAITEM`嵌入式管理單元的結構。|
|[CSnapInItemImpl::GetResultViewType](#getresultviewtype)|決定使用 [結果] 窗格的檢視類型。|
|[CSnapInItemImpl::GetScopePaneInfo](#getscopepaneinfo)|擷取`SCOPEDATAITEM`嵌入式管理單元的結構。|
|[CSnapInItemImpl::Notify](#notify)|由通知嵌入式管理單元中的使用者所採取的動作的主控台呼叫。|
|[CSnapInItemImpl::QueryPagesFor](#querypagesfor)|呼叫以嵌入式管理單元的節點是否支援屬性頁。|
|[CSnapInItemImpl::SetMenuInsertionFlags](#setmenuinsertionflags)|修改嵌入式管理單元物件的功能表插入旗標。|
|[CSnapInItemImpl::SetToolbarButtonInfo](#settoolbarbuttoninfo)|設定指定的工具列按鈕的資訊。|
|[CSnapInItemImpl::UpdateMenuState](#updatemenustate)|更新操作功能表項目的狀態。|
|[CSnapInItemImpl::UpdateToolbarButton](#updatetoolbarbutton)|更新指定的工具列按鈕的狀態。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CSnapInItemImpl::m_bstrDisplayName](#m_bstrdisplayname)|嵌入式管理單元物件的名稱。|
|[CSnapInItemImpl::m_resultDataItem](#m_resultdataitem)|Windows`RESULTDATAITEM`所使用的結構`CSnapInItemImpl`物件。|
|[CSnapInItemImpl::m_scopeDataItem](#m_scopedataitem)|Windows`SCOPEDATAITEM`所使用的結構`CSnapInItemImpl`物件。|

## <a name="remarks"></a>備註

`CSnapInItemImpl` 提供基本的實作嵌入式管理單元節點物件，例如加入功能表項目和工具列，並轉送至適當的處理常式函式的嵌入式管理單元 節點的命令。 這些功能會使用數個不同的介面實作，並將型別對應。 預設實作會處理傳送至節點物件，判斷正確的衍生類別的執行個體，然後再將訊息轉送至正確的執行個體的通知。

## <a name="inheritance-hierarchy"></a>繼承階層

`CSnapInItem`

`CSnapInItemImpl`

## <a name="requirements"></a>需求

**標頭：** atlsnap.h

##  <a name="addmenuitems"></a>  CSnapInItemImpl::AddMenuItems

這個方法會實作 Win32 函式[IExtendContextMenu::AddMenuItems](/windows/desktop/api/mmc/nf-mmc-iextendcontextmenu-addmenuitems)。

```
AddMenuItems(
    LPCONTEXTMENUCALLBACK piCallback,
    long* pInsertionAllowed,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>參數

*piCallback*<br/>
[in]指標`IContextMenuCallback`，可以加入快顯功能表中的項目。

*pInsertionAllowed*<br/>
[in、 out]識別 Microsoft Management Console MMC 定義功能表項目插入點可用。 這可以是下列旗標的組合：

- 可以在操作功能表的頂端插入 CCM_INSERTIONALLOWED_TOP 項目。

- 建立新的子功能表中，可以插入 CCM_INSERTIONALLOWED_NEW 項目。

- [工作] 子功能表中可插入 CCM_INSERTIONALLOWED_TASK 項目。

- [結果] 窗格內容功能表中的 [檢視] 子功能表或工具列的 [檢視] 功能表中，可以插入 CCM_INSERTIONALLOWED_VIEW 項目。

*type*<br/>
[in]指定物件的型別。 它可以包含下列值之一：

- 範圍窗格內容的 CCT_SCOPE 資料物件。

- 結果窗格內容的 CCT_RESULT 資料物件。

- CCT_SNAPIN_MANAGER 資料管理員 嵌入式管理單元中的內容物件。

- CCT_UNINITIALIZED 資料物件都有無效的類型。

##  <a name="command"></a>  CSnapInItemImpl::Command

這個方法會實作 Win32 函式[IExtendContextMenu::Command](/windows/desktop/api/mmc/nf-mmc-iextendcontextmenu-command)。

```
Command(long lCommandID, DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>參數

*lCommandID*<br/>
[in]指定功能表項目的命令識別項。

*type*<br/>
[in]指定物件的型別。 它可以包含下列值之一：

- 範圍窗格內容的 CCT_SCOPE 資料物件。

- 結果窗格內容的 CCT_RESULT 資料物件。

- CCT_SNAPIN_MANAGER 資料管理員 嵌入式管理單元中的內容物件。

- CCT_UNINITIALIZED 資料物件都有無效的類型。

##  <a name="createpropertypages"></a>  CSnapInItemImpl::CreatePropertyPages

這個方法會實作 Win32 函式[IExtendPropertySheet::CreatePropertyPages](/windows/desktop/api/mmc/nn-mmc-iextendpropertysheet2)。

```
CreatePropertyPages(
    LPPROPERTYSHEETCALLBACK lpProvider,
    long handle,
    IUnknown* pUnk,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>參數

*lpProvider*<br/>
[in]指標`IPropertySheetCallback`介面。

*handle*<br/>
[in]指定用來將 MMCN_PROPERTY_CHANGE 通知訊息傳送至適當的資料類別的控制代碼。

*pUnk*<br/>
[in]指標`IExtendPropertySheet`包含該節點的內容資訊的物件上的介面。

*type*<br/>
[in]指定物件的型別。 它可以包含下列值之一：

- 範圍窗格內容的 CCT_SCOPE 資料物件。

- 結果窗格內容的 CCT_RESULT 資料物件。

- CCT_SNAPIN_MANAGER 資料管理員 嵌入式管理單元中的內容物件。

- CCT_UNINITIALIZED 資料物件都有無效的類型。

##  <a name="csnapinitemimpl"></a>  CSnapInItemImpl::CSnapInItemImpl

建構 `CSnapInItemImpl` 物件。

```
CSnapInItemImpl();
```

##  <a name="filldata"></a>  CSnapInItemImpl::FillData

您可以呼叫此函式擷取項目的資訊。

```
FillData(CLIPFORMAT cf, LPSTREAM pStream);
```

### <a name="parameters"></a>參數

*cf*<br/>
[in]剪貼簿格式 （文字、 豐富的文字或 rtf 文字與 OLE 項目）。

*pStream*<br/>
[in]包含的物件資料的資料流指標。

### <a name="remarks"></a>備註

若要正確實作此函式，將正確的資訊複製到資料流 (*pStream*)，這取決於所指出的剪貼簿格式*cf*。

##  <a name="getresultviewtype"></a>  CSnapInItemImpl::GetResultViewType

呼叫此函式可擷取的嵌入式管理單元物件的 [結果] 窗格的檢視類型。

```
GetResultViewType(
    LPOLESTR* ppViewType,
    long* pViewOptions);
```

### <a name="parameters"></a>參數

*ppViewType*<br/>
[out]傳回的檢視類型的位址指標。

*pViewOptions*<br/>
[out]提供選項，指定所擁有的嵌入式管理單元主控台 MMC_VIEW_OPTIONS 列舉型別指標。 這個值可以是下列其中一項：

- MMC_VIEW_OPTIONS_NOLISTVIEWS = 0x00000001 會告訴主控台，以避免呈現中的標準清單檢視選項**檢視**功能表。 可讓嵌入式管理單元只在結果檢視 窗格中顯示它自己的自訂檢視。 這是定義在這個階段的唯一選項旗標。

- MMC_VIEW_OPTIONS_NONE = 0 允許預設檢視選項。

##  <a name="getscopepaneinfo"></a>  CSnapInItemImpl::GetScopePaneInfo

呼叫此函式可擷取`SCOPEDATAITEM`嵌入式管理單元的結構。

```
GetScopePaneInfo (SCOPEDATAITEM* pScopeDataItem);
```

### <a name="parameters"></a>參數

*pScopeDataItem*<br/>
[out]指標`SCOPEDATAITEM`結構`CSnapInItemImpl`物件。

##  <a name="getresultpaneinfo"></a>  CSnapInItemImpl::GetResultPaneInfo

呼叫此函式可擷取`RESULTDATAITEM`嵌入式管理單元的結構。

```
GetResultPaneInfo (RESULTDATAITEM* pResultDataItem);
```

### <a name="parameters"></a>參數

*pResultDataItem*<br/>
[out]指標`RESULTDATAITEM`結構`CSnapInItemImpl`物件。

##  <a name="m_bstrdisplayname"></a>  CSnapInItemImpl::m_bstrDisplayName

包含節點的項目所顯示的字串。

```
CComBSTR m_bstrDisplayName;
```

##  <a name="m_scopedataitem"></a>  CSnapInItemImpl::m_scopeDataItem

`SCOPEDATAITEM`嵌入式管理單元中的資料物件的結構。

```
SCOPEDATAITEM m_scopeDataItem;
```

##  <a name="m_resultdataitem"></a>  CSnapInItemImpl::m_resultDataItem

[RESULTDATAITEM](/windows/desktop/api/mmc/ns-mmc-resultdataitem)嵌入式管理單元中的資料物件的結構。

```
RESULTDATAITEM m_resultDataItem;
```

##  <a name="notify"></a>  CSnapInItemImpl::Notify

當嵌入式管理單元的物件有作用時，由使用者呼叫。

```
STDMETHOD(Notify)(
    MMC_NOTIFY_TYPE event,
    long arg,
    long param,
    IComponentData* pComponentData,
    IComponent* pComponent,
    DATA_OBJECT_TYPES type) = 0;
```

### <a name="parameters"></a>參數

*event*<br/>
[in]識別使用者所採取的動作。 下列通知則可能會：

- MMCN_ACTIVATE 傳送時視窗正被啟動和停用。

- MMCN_ADD_IMAGES 傳送將影像新增至 [結果] 窗格。

- 當使用者按一下其中一個工具列按鈕時，就會傳送 MMCN_BTN_CLICK。

- 當使用者按下滑鼠按鈕在清單檢視項目上的時，就會傳送 MMCN_CLICK。

- 當使用者按兩下滑鼠按鈕在清單檢視項目上的時，就會傳送 MMCN_DBLCLICK。

- MMCN_DELETE 傳送至通知嵌入式管理單元的物件應該刪除。

- MMCN_EXPAND 傳送時的資料夾，就必須加以擴大或縮減。

- MMCN_MINIMIZED 傳送時的視窗最小化或最大化。

- MMCN_PROPERTY_CHANGE 傳送通知的嵌入式管理單元物件的檢視即將變更的嵌入式管理單元物件。

- 當嵌入式管理單元必須刪除它加入指定的節點下的整個樹狀子目錄時，就會傳送 MMCN_REMOVE_CHILDREN。

- MMCN_RENAME 會傳送第一次重新命名的查詢和第二次執行重新命名。

- 當選取範圍或結果的 [檢視] 窗格中的項目時，就會傳送 MMCN_SELECT。

- 選取或取消選取第一次的範圍項目時，就會傳送 MMCN_SHOW。

- 當嵌入式管理單元可以更新所有的檢視表發生變更時，就會傳送 MMCN_VIEW_CHANGE。

*arg*<br/>
[in]通知類型而定。

*param*<br/>
[in]通知類型而定。

*pComponentData*<br/>
[out]物件，實作的指標`IComponentData`。 這個參數是 NULL，如果通知不會從正在轉送`IComponentData::Notify`。

*pComponent*<br/>
[out]實作的物件指標`IComponent`。 這個參數是 NULL，如果通知不會從正在轉送`IComponent::Notify`。

*type*<br/>
[in]指定物件的型別。 它可以包含下列值之一：

- 範圍窗格內容的 CCT_SCOPE 資料物件。

- 結果窗格內容的 CCT_RESULT 資料物件。

- CCT_SNAPIN_MANAGER 資料管理員 嵌入式管理單元中的內容物件。

- CCT_UNINITIALIZED 資料物件都有無效的類型。

##  <a name="querypagesfor"></a>  CSnapInItemImpl::QueryPagesFor

呼叫以嵌入式管理單元的節點是否支援屬性頁。

```
QueryPagesFor(DATA_OBJECT_TYPES type);
```

##  <a name="setmenuinsertionflags"></a>  CSnapInItemImpl::SetMenuInsertionFlags

呼叫此函式可修改的功能表插入旗標，指定*pInsertionAllowed*，嵌入式管理單元的物件。

```
void SetMenuInsertionFlags(
    bool bBeforeInsertion,
    long* pInsertionAllowed);
```

### <a name="parameters"></a>參數

*bBeforeInsertion*<br/>
[in]如果項目加入至內容功能表; 之前，應該呼叫此函式，非零值。否則為 0。

*pInsertionAllowed*<br/>
[in、 out]識別 Microsoft Management Console MMC 定義功能表項目插入點可用。 這可以是下列旗標的組合：

- 可以在操作功能表的頂端插入 CCM_INSERTIONALLOWED_TOP 項目。

- 建立新的子功能表中，可以插入 CCM_INSERTIONALLOWED_NEW 項目。

- [工作] 子功能表中可插入 CCM_INSERTIONALLOWED_TASK 項目。

- [結果] 窗格內容功能表中的 [檢視] 子功能表或工具列的 [檢視] 功能表中，可以插入 CCM_INSERTIONALLOWED_VIEW 項目。

### <a name="remarks"></a>備註

如果您正在開發一個主要的嵌入式管理單元，您可以重設任何插入旗標，這種限制使用協力廠商延伸模組可以加入的功能表項目類型。 比方說，主要的嵌入式管理單元可以清除 CCM_INSERTIONALLOWED_NEW 旗標，以防止擴充功能加入自己建立新的功能表項目。

您不應該嘗試設定位元*pInsertionAllowed* ，原先已清除。 MMC 的未來版本可能會使用目前未定義，所以您不應變更目前未定義的位元的位元。

##  <a name="settoolbarbuttoninfo"></a>  CSnapInItemImpl::SetToolbarButtonInfo

呼叫此函式來建立工具列之前修改嵌入式管理單元物件的任何工具列按鈕樣式。

```
void SetToolbarButtonInfo(
    UINT id,
    BYTE* fsState,
    BYTE* fsType);
```

### <a name="parameters"></a>參數

*id*<br/>
[in]若要設定的工具列按鈕的識別碼。

*fsState*<br/>
[in]按鈕的狀態旗標。 可以是下列其中一個或多個項目：

- TBSTATE_CHECKED 按鈕 TBSTYLE_CHECKED 樣式，並按下。

- TBSTATE_ENABLED 按鈕接受使用者輸入。 沒有此狀態的按鈕不接受使用者輸入，並會變為灰色。

- TBSTATE_HIDDEN 按鈕看不到，且無法接收使用者輸入。

- TBSTATE_INDETERMINATE 按鈕會變為灰色。

- TBSTATE_PRESSED 按鈕已按下。

- TBSTATE_WRAP 的分行符號會遵循 按鈕。 按鈕也必須擁有 TBSTATE_ENABLED。

*fsType*<br/>
[in]按鈕的狀態旗標。 可以是下列其中一個或多個項目：

- TBSTYLE_BUTTON 建立標準按鈕。

- TBSTYLE_CHECK 建立按鈕來切換使用已按下和未按下狀態每次使用者按下它。 處於已按下狀態時，按鈕會有不同的背景色彩。

- TBSTYLE_CHECKGROUP 建立直到按下群組中的另一個按鈕，按下保持核取按鈕。

- TBSTYLE_GROUP 建立直到群組中的另一個按鈕按下按鈕處於已按下。

- TBSTYLE_SEP 建立分隔符號，提供按鈕群組之間有小型的間隙。 具有此樣式的按鈕不會接收使用者輸入。

##  <a name="updatemenustate"></a>  CSnapInItemImpl::UpdateMenuState

呼叫此函式可修改的功能表項目之前插入物件 嵌入式管理單元中的操作功能表。

```
void UpdateMenuState(
    UINT id,
    LPTSTR pBuf,
    UINT* flags);
```

### <a name="parameters"></a>參數

*id*<br/>
[in]設定功能表項目的識別碼。

*pBuf*<br/>
[in]若要更新之功能表項目字串的指標。

*flags*<br/>
[in]指定新的狀態旗標。 這可以是下列旗標的組合：

- MF_POPUP 指定這是快顯功能表中的子功能表。 功能表項目、 插入點，以及進一步子功能表可能會加入至這個子功能表使用其`lCommandID`做為其`IInsertionPointID`。

- MF_BITMAP 並 MF_OWNERDRAW 這些旗標不允許會導致傳回值 E_INVALIDARG。

- MF_SEPARATOR 繪製水平分隔線。 只有`IContextMenuProvider`允許加入 MF_SEPARATOR 組功能表項目。

- MF_CHECKED 會放在功能表項目旁邊的核取記號。

- MF_DISABLED 停用的功能表項目，因此不會選取它，但此旗標不會不 gray 它。

- MF_ENABLED 啟用功能表項目，讓它可被選取，從其呈現灰色的狀態還原。

- MF_GRAYED 停用功能表項目，讓它，因此無法選取。

- 功能表列的旗標 MF_MENUBREAK 相同 MF_MENUBARBREAK 函式。 下拉式選單 子功能表，或快顯功能表中，新的資料行是從舊的資料行以分隔的垂直線條。

- MF_MENUBREAK 將項目置於新行 （適用於功能表列） 或新的資料行 （適用於下拉式選單 子功能表或快顯功能表中） 而不分隔資料行。

- MF_UNCHECKED 並不會在項目 （預設值） 旁邊的核取記號。

下列群組的旗標不能同時使用：

- MF_DISABLED、 MF_ENABLED 和 MF_GRAYED。

- MF_MENUBARBREAK 和 MF_MENUBREAK。

- MF_CHECKED 和 MF_UNCHECKED。

##  <a name="updatetoolbarbutton"></a>  CSnapInItemImpl::UpdateToolbarButton

呼叫此函式可在顯示之前，修改工具列按鈕，在嵌入式管理單元物件。

```
BOOL UpdateToolbarButton(UINT id, BYTE fsState);
```

### <a name="parameters"></a>參數

*id*<br/>
指定工具列按鈕的按鈕 ID，更新。

*fsState*<br/>
指定的工具列按鈕的狀態。 如果要設定此狀態，則傳回 TRUE。 這可以是下列旗標的組合：

- 已啟用 按鈕會接受使用者輸入。 沒有此狀態的按鈕不接受使用者輸入，並會變為灰色。

- 檢查 按鈕已核取的樣式，並按下。

- 隱藏按鈕看不到，且無法接收使用者輸入。

- 不定的按鈕會變為灰色。

- BUTTONPRESSED 按鈕已按下。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
