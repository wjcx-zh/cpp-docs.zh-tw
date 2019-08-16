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
ms.openlocfilehash: a9ebcf8827d79a9613ce14251d361dd607aa6af3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496553"
---
# <a name="csnapinitemimpl-class"></a>CSnapInItemImpl 類別

這個類別會提供用來執行嵌入式管理單元節點物件的方法。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class T, BOOL bIsExtension = FALSE>
class ATL_NO_VTABLE CSnapInItemImpl : public CSnapInItem
```

#### <a name="parameters"></a>參數

*T*<br/>
衍生自`CSnapInItemImpl`的類別。

*bIsExtension*<br/>
如果物件是嵌入式管理單元擴充功能, 則為 TRUE;否則為 FALSE。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CSnapInItemImpl::CSnapInItemImpl](#csnapinitemimpl)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CSnapInItemImpl::AddMenuItems](#addmenuitems)|將功能表項目新增至內容功能表。|
|[CSnapInItemImpl::Command](#command)|當選取自訂功能表項目時, 由主控台呼叫。|
|[CSnapInItemImpl::CreatePropertyPages](#createpropertypages)|將頁面新增至嵌入式管理單元的屬性工作表。|
|[CSnapInItemImpl::FillData](#filldata)|將嵌入式管理單元物件上的資訊複製到指定的資料流程。|
|[CSnapInItemImpl::GetResultPaneInfo](#getresultpaneinfo)|抓取嵌入式管理單元的結構。`RESULTDATAITEM`|
|[CSnapInItemImpl::GetResultViewType](#getresultviewtype)|決定 [結果] 窗格所使用的檢視類型。|
|[CSnapInItemImpl::GetScopePaneInfo](#getscopepaneinfo)|抓取嵌入式管理單元的結構。`SCOPEDATAITEM`|
|[CSnapInItemImpl::Notify](#notify)|由主控台呼叫, 以通知嵌入式管理單元使用者所採取的動作。|
|[CSnapInItemImpl::QueryPagesFor](#querypagesfor)|呼叫以查看嵌入式管理單元節點是否支援屬性頁。|
|[CSnapInItemImpl::SetMenuInsertionFlags](#setmenuinsertionflags)|修改嵌入式管理單元物件的功能表插入旗標。|
|[CSnapInItemImpl::SetToolbarButtonInfo](#settoolbarbuttoninfo)|設定指定之工具列按鈕的資訊。|
|[CSnapInItemImpl::UpdateMenuState](#updatemenustate)|更新內容功能表項目的狀態。|
|[CSnapInItemImpl::UpdateToolbarButton](#updatetoolbarbutton)|更新指定之工具列按鈕的狀態。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CSnapInItemImpl::m_bstrDisplayName](#m_bstrdisplayname)|嵌入式管理單元物件的名稱。|
|[CSnapInItemImpl::m_resultDataItem](#m_resultdataitem)|`CSnapInItemImpl`物件所`RESULTDATAITEM`使用的 Windows 結構。|
|[CSnapInItemImpl::m_scopeDataItem](#m_scopedataitem)|`CSnapInItemImpl`物件所`SCOPEDATAITEM`使用的 Windows 結構。|

## <a name="remarks"></a>備註

`CSnapInItemImpl`提供嵌入式管理單元節點物件的基本執行方式, 例如新增功能表項目和工具列, 以及將嵌入式管理單元節點的命令轉送至適當的處理常式函式。 這些功能是使用數個不同的介面和對應類型來執行。 預設的執行會藉由判斷衍生類別的正確實例, 然後將訊息轉送至正確的實例, 來處理傳送至 node 物件的通知。

## <a name="inheritance-hierarchy"></a>繼承階層

`CSnapInItem`

`CSnapInItemImpl`

## <a name="requirements"></a>需求

**標頭:** atlsnap。h

##  <a name="addmenuitems"></a>CSnapInItemImpl:: AddMenuItems

這個方法會執行 Win32 函數[IExtendCoNtextMenu:: AddMenuItems](/windows/win32/api/mmc/nf-mmc-iextendcontextmenu-addmenuitems)。

```
AddMenuItems(
    LPCONTEXTMENUCALLBACK piCallback,
    long* pInsertionAllowed,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>參數

*piCallback*<br/>
在的指標, 可將專案新增至內容功能表。 `IContextMenuCallback`

*pInsertionAllowed*<br/>
[in、out]識別可使用的 Microsoft Management Console (MMC) 定義的功能表項目插入點。 這可以是下列旗標的組合:

- CCM_INSERTIONALLOWED_TOP 專案可以插入內容功能表的頂端。

- CCM_INSERTIONALLOWED_NEW 專案可以插入 [建立新的] 子功能表中。

- CCM_INSERTIONALLOWED_TASK 專案可以插入 [工作] 子功能表中。

- CCM_INSERTIONALLOWED_VIEW 專案可以插入 [工具列視圖] 功能表或 [結果] 窗格內容功能表的 [視圖] 子功能表中。

*type*<br/>
在指定物件的類型。 它可以有下列其中一個值:

- 範圍窗格內容的 CCT_SCOPE 資料物件。

- 結果窗格內容的 CCT_RESULT 資料物件。

- 嵌入式管理單元管理員內容的 CCT_SNAPIN_MANAGER 資料物件。

- CCT_UNINITIALIZED 資料物件具有不正確類型。

##  <a name="command"></a>CSnapInItemImpl:: Command

這個方法會實作用 Win32 函數[IExtendCoNtextMenu:: Command](/windows/win32/api/mmc/nf-mmc-iextendcontextmenu-command)。

```
Command(long lCommandID, DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>參數

*lCommandID*<br/>
在指定功能表項目的命令識別碼。

*type*<br/>
在指定物件的類型。 它可以有下列其中一個值:

- 範圍窗格內容的 CCT_SCOPE 資料物件。

- 結果窗格內容的 CCT_RESULT 資料物件。

- 嵌入式管理單元管理員內容的 CCT_SNAPIN_MANAGER 資料物件。

- CCT_UNINITIALIZED 資料物件具有不正確類型。

##  <a name="createpropertypages"></a>CSnapInItemImpl::CreatePropertyPages

這個方法會執行 Win32 函數[IExtendPropertySheet:: CreatePropertyPages](/windows/win32/api/mmc/nn-mmc-iextendpropertysheet2)。

```
CreatePropertyPages(
    LPPROPERTYSHEETCALLBACK lpProvider,
    long handle,
    IUnknown* pUnk,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>參數

*lpProvider*<br/>
在介面的`IPropertySheetCallback`指標。

*圖*<br/>
在指定用來將 MMCN_PROPERTY_CHANGE 通知訊息路由傳送至適當資料類別的控制碼。

*pUnk*<br/>
在物件上介面的指標, 其中包含節點的相關內容資訊。 `IExtendPropertySheet`

*type*<br/>
在指定物件的類型。 它可以有下列其中一個值:

- 範圍窗格內容的 CCT_SCOPE 資料物件。

- 結果窗格內容的 CCT_RESULT 資料物件。

- 嵌入式管理單元管理員內容的 CCT_SNAPIN_MANAGER 資料物件。

- CCT_UNINITIALIZED 資料物件具有不正確類型。

##  <a name="csnapinitemimpl"></a>CSnapInItemImpl::CSnapInItemImpl

建構 `CSnapInItemImpl` 物件。

```
CSnapInItemImpl();
```

##  <a name="filldata"></a>CSnapInItemImpl::FillData

呼叫此函式可取得專案的相關資訊。

```
FillData(CLIPFORMAT cf, LPSTREAM pStream);
```

### <a name="parameters"></a>參數

*cf*<br/>
在剪貼簿的格式 (文字、rtf 文字或 rtf 文字)。

*pStream*<br/>
在包含物件資料之資料流程的指標。

### <a name="remarks"></a>備註

若要正確地執行此函式, 請根據*cf*所指示的剪貼簿格式, 將正確的資訊複製到資料流程 (*pStream*)。

##  <a name="getresultviewtype"></a>CSnapInItemImpl::GetResultViewType

呼叫此函式可抓取嵌入式管理單元物件之結果窗格的檢視類型。

```
GetResultViewType(
    LPOLESTR* ppViewType,
    long* pViewOptions);
```

### <a name="parameters"></a>參數

*ppViewType*<br/>
脫銷傳回之檢視類型的位址指標。

*pViewOptions*<br/>
脫銷MMC_VIEW_OPTIONS 列舉的指標, 它會為主控台提供擁有的嵌入式管理單元所指定的選項。 此值可以是下列其中一項:

- MMC_VIEW_OPTIONS_NOLISTVIEWS = 0x00000001 告訴主控台避免在 [ **VIEW** ] 功能表中呈現標準清單視圖選項。 允許嵌入式管理單元只在 [結果] 視圖窗格中顯示自己的自訂視圖。 這是目前唯一定義的選項旗標。

- MMC_VIEW_OPTIONS_NONE = 0 允許預設的 VIEW 選項。

##  <a name="getscopepaneinfo"></a>CSnapInItemImpl::GetScopePaneInfo

呼叫此函式可取出`SCOPEDATAITEM`嵌入式管理單元的結構。

```
GetScopePaneInfo (SCOPEDATAITEM* pScopeDataItem);
```

### <a name="parameters"></a>參數

*pScopeDataItem*<br/>
脫銷`SCOPEDATAITEM`物件結構`CSnapInItemImpl`的指標。

##  <a name="getresultpaneinfo"></a>CSnapInItemImpl::GetResultPaneInfo

呼叫此函式可取出`RESULTDATAITEM`嵌入式管理單元的結構。

```
GetResultPaneInfo (RESULTDATAITEM* pResultDataItem);
```

### <a name="parameters"></a>參數

*pResultDataItem*<br/>
脫銷`RESULTDATAITEM`物件結構`CSnapInItemImpl`的指標。

##  <a name="m_bstrdisplayname"></a>CSnapInItemImpl::m_bstrDisplayName

包含為節點專案顯示的字串。

```
CComBSTR m_bstrDisplayName;
```

##  <a name="m_scopedataitem"></a>CSnapInItemImpl::m_scopeDataItem

嵌入式`SCOPEDATAITEM`管理單中繼資料物件的結構。

```
SCOPEDATAITEM m_scopeDataItem;
```

##  <a name="m_resultdataitem"></a>CSnapInItemImpl::m_resultDataItem

嵌入式管理單中繼資料物件的[RESULTDATAITEM](/windows/win32/api/mmc/ns-mmc-resultdataitem)結構。

```
RESULTDATAITEM m_resultDataItem;
```

##  <a name="notify"></a>CSnapInItemImpl:: Notify

當使用者對嵌入式管理單元物件進行動作時呼叫。

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
在識別使用者所採取的動作。 可能的通知如下:

- 當視窗正在啟動並停用時, 會傳送 MMCN_ACTI加值稅E。

- MMCN_ADD_IMAGES 傳送 以將影像新增至 結果 窗格。

- MMCN_BTN_CLICK 會在使用者按一下其中一個工具列按鈕時傳送。

- 當使用者按一下清單視圖專案上的滑鼠按鍵時, 就會傳送 MMCN_CLICK。

- 當使用者按兩下清單視圖專案上的滑鼠按鍵時, 就會傳送 MMCN_DBLCLICK。

- MMCN_DELETE 已傳送 通知嵌入式管理單元, 應刪除物件。

- MMCN_EXPAND 在資料夾需要展開或收縮時傳送。

- 當視窗最小化或最大化時, 所傳送的 MMCN_MINIMIZED。

- MMCN_PROPERTY_CHANGE 傳送, 以通知嵌入式管理單元物件的視圖即將變更的嵌入式管理單元物件。

- 當嵌入式管理單元必須刪除它在指定節點底下新增的整個子樹時, 就會傳送 MMCN_REMOVE_CHILDREN。

- 第一次傳送 MMCN_RENAME 來查詢重新命名, 第二次是進行重新命名。

- 選取 [範圍] 或 [結果] 視圖窗格中的專案時所傳送的 MMCN_SELECT。

- 第一次選取或取消選取範圍專案時, 所傳送的 MMCN_SHOW。

- 當嵌入式管理單元可以在發生變更時更新所有的視圖時, 會傳送 MMCN_VIEW_CHANGE。

*arg*<br/>
在視通知類型而定。

*param*<br/>
在視通知類型而定。

*pComponentData*<br/>
脫銷執行`IComponentData`之物件的指標。 如果未從`IComponentData::Notify`轉送通知, 這個參數會是 Null。

*pComponent*<br/>
脫銷執行之物件`IComponent`的指標。 如果未從`IComponent::Notify`轉送通知, 這個參數會是 Null。

*type*<br/>
在指定物件的類型。 它可以有下列其中一個值:

- 範圍窗格內容的 CCT_SCOPE 資料物件。

- 結果窗格內容的 CCT_RESULT 資料物件。

- 嵌入式管理單元管理員內容的 CCT_SNAPIN_MANAGER 資料物件。

- CCT_UNINITIALIZED 資料物件具有不正確類型。

##  <a name="querypagesfor"></a>CSnapInItemImpl::QueryPagesFor

呼叫以查看嵌入式管理單元節點是否支援屬性頁。

```
QueryPagesFor(DATA_OBJECT_TYPES type);
```

##  <a name="setmenuinsertionflags"></a>CSnapInItemImpl::SetMenuInsertionFlags

呼叫此函式可針對嵌入式管理單元物件修改*pInsertionAllowed*所指定的功能表插入旗標。

```
void SetMenuInsertionFlags(
    bool bBeforeInsertion,
    long* pInsertionAllowed);
```

### <a name="parameters"></a>參數

*bBeforeInsertion*<br/>
在如果應該在將專案新增至內容功能表之前呼叫函式, 則為非零。否則為0。

*pInsertionAllowed*<br/>
[in、out]識別可使用的 Microsoft Management Console (MMC) 定義的功能表項目插入點。 這可以是下列旗標的組合:

- CCM_INSERTIONALLOWED_TOP 專案可以插入內容功能表的頂端。

- CCM_INSERTIONALLOWED_NEW 專案可以插入 [建立新的] 子功能表中。

- CCM_INSERTIONALLOWED_TASK 專案可以插入 [工作] 子功能表中。

- CCM_INSERTIONALLOWED_VIEW 專案可以插入 [工具列視圖] 功能表或 [結果] 窗格內容功能表的 [視圖] 子功能表中。

### <a name="remarks"></a>備註

如果您正在開發主要嵌入式管理單元, 您可以重設任何插入旗標, 以限制協力廠商擴充功能可以加入的功能表項目類型。 例如, 主要嵌入式管理單元可以清除 CCM_INSERTIONALLOWED_NEW 旗標, 以防止延伸模組新增自己的 [建立新的] 功能表項目。

您不應該嘗試在原本已清除的*pInsertionAllowed*中設定位。 未來的 MMC 版本可能會使用目前未定義的 bits, 因此您不應該變更目前未定義的位。

##  <a name="settoolbarbuttoninfo"></a>CSnapInItemImpl::SetToolbarButtonInfo

呼叫此函式可在建立工具列之前, 修改嵌入式管理單元物件的任何工具列按鈕樣式。

```
void SetToolbarButtonInfo(
    UINT id,
    BYTE* fsState,
    BYTE* fsType);
```

### <a name="parameters"></a>參數

*id*<br/>
在要設定之工具列按鈕的識別碼。

*fsState*<br/>
在按鈕的狀態旗標。 可以是下列一或多個:

- TBSTATE_CHECKED 按鈕具有 TBSTYLE_CHECKED 樣式, 並已按下。

- TBSTATE_ENABLED 按鈕會接受使用者輸入。 沒有此狀態的按鈕不接受使用者輸入, 且呈現灰色。

- TBSTATE_HIDDEN 按鈕不可見, 且無法接收使用者輸入。

- TBSTATE_INDETERMINATE 按鈕會呈現灰色。

- TBSTATE_PRESSED 按鈕已按下。

- 在按鈕後面 TBSTATE_WRAP 分行符號。 此按鈕也必須有 TBSTATE_ENABLED。

*fsType*<br/>
在按鈕的狀態旗標。 可以是下列一或多個:

- TBSTYLE_BUTTON 會建立標準的 [推播] 按鈕。

- TBSTYLE_CHECK 會建立一個按鈕, 在每次使用者按一下時, 切換已按下和未按下的狀態。 當按鈕處於已按下的狀態時, 其背景色彩會不同。

- TBSTYLE_CHECKGROUP 會建立一個勾選的核取按鈕, 直到按下群組中的另一個按鈕為止。

- TBSTYLE_GROUP 會建立一個按鈕, 讓它持續按下, 直到按下群組中的另一個按鈕為止。

- TBSTYLE_SEP 會建立分隔符號, 並在按鈕群組之間提供小間隙。 具有此樣式的按鈕不會接收使用者輸入。

##  <a name="updatemenustate"></a>CSnapInItemImpl::UpdateMenuState

呼叫此函式可在將功能表項目插入嵌入式管理單元物件的操作功能表之前, 加以修改。

```
void UpdateMenuState(
    UINT id,
    LPTSTR pBuf,
    UINT* flags);
```

### <a name="parameters"></a>參數

*id*<br/>
在要設定之功能表項目的識別碼。

*pBuf*<br/>
在要更新之功能表項目的字串指標。

*flags*<br/>
在指定新的狀態旗標。 這可以是下列旗標的組合:

- MF_POPUP 指定這是內容功能表中的子功能表。 功能表項目、插入點和其他子功能表可能會使用其`lCommandID`做為其`IInsertionPointID`新增至這個子功能表。

- 不允許 MF_BITMAP 和 MF_OWNERDRAW 這些旗標, 並會產生 E_INVALIDARG 的傳回值。

- MF_SEPARATOR 繪製水準分隔線。 僅`IContextMenuProvider`允許加入具有 MF_SEPARATOR 集的功能表項目。

- MF_CHECKED 會在功能表項目旁邊放置一個核取記號。

- MF_DISABLED 會停用功能表項目, 因此無法選取它, 但旗標不會將它變成灰色。

- MF_ENABLED 會啟用功能表項目, 讓它可以選取, 並從灰色的狀態還原。

- MF_GRAYED 會停用功能表項目, 讓, 使其無法選取。

- MF_MENUBARBREAK 的功能與功能表列的 MF_MENUBREAK 旗標相同。 針對下拉式功能表、子功能表或快捷方式功能表, 新的資料行會與舊的資料行分隔。

- MF_MENUBREAK 會將專案放在新的一行 (適用于功能表列) 或新的欄位 (用於下拉式功能表、子功能表或快顯功能表), 而不需要分隔資料行。

- MF_UNCHECKED 不會在專案旁放置核取記號 (預設值)。

下列旗標群組不能同時使用:

- MF_DISABLED、MF_ENABLED 和 MF_GRAYED。

- MF_MENUBARBREAK 和 MF_MENUBREAK。

- MF_CHECKED 和 MF_UNCHECKED。

##  <a name="updatetoolbarbutton"></a>CSnapInItemImpl::UpdateToolbarButton

呼叫此函式以修改嵌入式管理單元物件的工具列按鈕, 然後再顯示它。

```
BOOL UpdateToolbarButton(UINT id, BYTE fsState);
```

### <a name="parameters"></a>參數

*id*<br/>
指定要更新之工具列按鈕的按鈕識別碼。

*fsState*<br/>
指定工具列按鈕狀態。 如果要設定此狀態, 則傳回 TRUE。 這可以是下列旗標的組合:

- [已啟用] 按鈕可接受使用者輸入。 沒有此狀態的按鈕不接受使用者輸入, 且呈現灰色。

- 核取按鈕具有核取的樣式, 並按下。

- 隱藏的按鈕不會顯示, 且無法接收使用者輸入。

- 不確定按鈕會呈現灰色。

- BUTTONPRESSED 按鈕已按下。

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)
