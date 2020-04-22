---
title: 快照項目類別
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
ms.openlocfilehash: 04eeba0239789b9f3220b7bfece3eb41dc7f2826
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746422"
---
# <a name="csnapinitemimpl-class"></a>快照項目類別

此類提供了實現入網節點物件的方法。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template <class T, BOOL bIsExtension = FALSE>
class ATL_NO_VTABLE CSnapInItemImpl : public CSnapInItem
```

#### <a name="parameters"></a>參數

*T*<br/>
您的類,派生自`CSnapInItemImpl`。

*bIs 擴充*<br/>
如果對像是卡入擴展,則為 TRUE;如果對像是卡入擴展。否則 FALSE。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[快照專案::卡內普內專案](#csnapinitemimpl)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[快照專案::添加功能表項](#addmenuitems)|將功能表項添加到上下文菜單。|
|[快照專案::命令](#command)|選擇自定義功能表項時,控制台調用。|
|[快照項目::建立屬性頁](#createpropertypages)|將頁面添加到管理單元的屬性表。|
|[快照項目::填充資料](#filldata)|將管理單元物件上的資訊複製到指定的流中。|
|[快照項目::取得結果窗格資訊](#getresultpaneinfo)|檢索卡入`RESULTDATAITEM`的結構。|
|[快照項目::取得結果檢視類型](#getresultviewtype)|確定結果窗格使用的檢視類型。|
|[快照專案::獲取ScopePane資訊](#getscopepaneinfo)|檢索卡入`SCOPEDATAITEM`的結構。|
|[快照專案::通知](#notify)|由控制台調用以通知用戶執行的操作的卡入。|
|[快照項目::查詢頁面](#querypagesfor)|已調用以查看管理單元節點是否支援屬性頁。|
|[快照項目::設定Menu插入標記](#setmenuinsertionflags)|修改插入物件的功能表插入標誌。|
|[快照專案::設定工具列按鈕資訊](#settoolbarbuttoninfo)|設置指定工具列按鈕的資訊。|
|[快照專案::更新功能表狀態](#updatemenustate)|更新上下文菜單項的狀態。|
|[快照專案::更新工具列按鈕](#updatetoolbarbutton)|更新指定工具列按鈕的狀態。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[快照專案::m_bstrDisplayName](#m_bstrdisplayname)|卡入物件的名稱。|
|[快照專案::m_resultDataItem](#m_resultdataitem)|`CSnapInItemImpl`物件使用的 Windows`RESULTDATAITEM`結構。|
|[快照專案::m_scopeDataItem](#m_scopedataitem)|`CSnapInItemImpl`物件使用的 Windows`SCOPEDATAITEM`結構。|

## <a name="remarks"></a>備註

`CSnapInItemImpl`為入卡節點物件提供了基本實現,例如添加功能表項和工具列,以及將入卡節點的命令轉發到相應的處理程式函數。 這些要素使用幾個不同的介面和映射類型實現。 預設實現通過確定派生類的正確實例,然後將消息轉發到正確的實例來處理發送到節點物件的通知。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CSnapInItem`

`CSnapInItemImpl`

## <a name="requirements"></a>需求

**標題:** atlsnap.h

## <a name="csnapinitemimpladdmenuitems"></a><a name="addmenuitems"></a>快照專案::添加功能表項

此方法實現 Win32 函數[IExtendContextMenu::addMenuitem](/windows/win32/api/mmc/nf-mmc-iextendcontextmenu-addmenuitems)。

```
AddMenuItems(
    LPCONTEXTMENUCALLBACK piCallback,
    long* pInsertionAllowed,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>參數

*皮卡背*<br/>
[在]指向`IContextMenuCallback`可以向上下文菜單添加項的 的指標。

*p 允許插入*<br/>
[進出]標識可以使用的 Microsoft 管理主控台 (MMC) 定義的選單項插入點。 這可以是以下旗標的組合:

- CCM_INSERTIONALLOWED_TOP項可以插入到上下文菜單的頂部。

- CCM_INSERTIONALLOWED_NEW項可以插入到"創建新"子功能表中。

- CCM_INSERTIONALLOWED_TASK項可以插入到任務子功能表中。

- CCM_INSERTIONALLOWED_VIEW項可以插入工具列檢視功能表或結果窗格上下文菜單的「查看子功能表」。

*type*<br/>
[在]指定物件的類型。 其值可以是下列其中一個值：

- CCT_SCOPE範圍窗格上下文的數據物件。

- CCT_RESULT結果窗格上下文的數據物件。

- CCT_SNAPIN_MANAGER用於管理單元上下文的數據物件。

- CCT_UNINITIALIZED資料物件的類型無效。

## <a name="csnapinitemimplcommand"></a><a name="command"></a>快照專案::命令

此方法實現 Win32 函數[IExtendContextMenu::指令](/windows/win32/api/mmc/nf-mmc-iextendcontextmenu-command)。

```
Command(long lCommandID, DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>參數

*lCommandID*<br/>
[在]指定選單的命令識別碼。

*type*<br/>
[在]指定物件的類型。 其值可以是下列其中一個值：

- CCT_SCOPE範圍窗格上下文的數據物件。

- CCT_RESULT結果窗格上下文的數據物件。

- CCT_SNAPIN_MANAGER用於管理單元上下文的數據物件。

- CCT_UNINITIALIZED資料物件的類型無效。

## <a name="csnapinitemimplcreatepropertypages"></a><a name="createpropertypages"></a>快照項目::建立屬性頁

此方法實現 Win32 函數[IExtend 屬性表::建立屬性頁](/windows/win32/api/mmc/nn-mmc-iextendpropertysheet2)。

```
CreatePropertyPages(
    LPPROPERTYSHEETCALLBACK lpProvider,
    long handle,
    IUnknown* pUnk,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>參數

*lpProvider*<br/>
[在]指向介面的`IPropertySheetCallback`指標。

*處理*<br/>
[在]指定用於將MMCN_PROPERTY_CHANGE通知消息路由到相應數據類的句柄。

*龐克*<br/>
[在]指向物件上的`IExtendPropertySheet`介面的指標,該介面包含有關節點的上下文資訊。

*type*<br/>
[在]指定物件的類型。 其值可以是下列其中一個值：

- CCT_SCOPE範圍窗格上下文的數據物件。

- CCT_RESULT結果窗格上下文的數據物件。

- CCT_SNAPIN_MANAGER用於管理單元上下文的數據物件。

- CCT_UNINITIALIZED資料物件的類型無效。

## <a name="csnapinitemimplcsnapinitemimpl"></a><a name="csnapinitemimpl"></a>快照專案::卡內普內專案

建構 `CSnapInItemImpl` 物件。

```
CSnapInItemImpl();
```

## <a name="csnapinitemimplfilldata"></a><a name="filldata"></a>快照項目::填充資料

調用此函數是為了檢索有關項的資訊。

```
FillData(CLIPFORMAT cf, LPSTREAM pStream);
```

### <a name="parameters"></a>參數

*cf*<br/>
[在]剪貼簿的格式(文字、富文字或帶有 OLE 項的富文本)。

*pStream*<br/>
[在]指向包含對象數據的流的指標。

### <a name="remarks"></a>備註

要正確實現此功能,請根據*cf*指示的剪貼簿格式將正確的資訊複製到流 *(pStream)* 中。

## <a name="csnapinitemimplgetresultviewtype"></a><a name="getresultviewtype"></a>快照項目::取得結果檢視類型

調用此函數以檢索管理單元對象的結果窗格的檢視類型。

```
GetResultViewType(
    LPOLESTR* ppViewType,
    long* pViewOptions);
```

### <a name="parameters"></a>參數

*ppView類型*<br/>
[出]指向返回檢視類型的位址。

*p 檢視選項*<br/>
[出]指向MMC_VIEW_OPTIONS枚舉的指標,該枚舉為主控台提供由所屬管理單元指定的選項。 這個值可以是下列其中一個值：

- MMC_VIEW_OPTIONS_NOLISTVIEWS = 0x0000001 告訴主控台不要在 **「檢視」** 選單中顯示標準清單視圖選項。 允許管理單元僅在結果視窗格中顯示其自己的自訂檢視。 這是此時定義的唯一選項標誌。

- MMC_VIEW_OPTIONS_NONE = 0 允許預設檢視選項。

## <a name="csnapinitemimplgetscopepaneinfo"></a><a name="getscopepaneinfo"></a>快照專案::獲取ScopePane資訊

調用此函數以檢索管理`SCOPEDATAITEM`單元的結構。

```
GetScopePaneInfo (SCOPEDATAITEM* pScopeDataItem);
```

### <a name="parameters"></a>參數

*pScope 資料專案*<br/>
[出]指向物件`SCOPEDATAITEM`結構`CSnapInItemImpl`的指標。

## <a name="csnapinitemimplgetresultpaneinfo"></a><a name="getresultpaneinfo"></a>快照項目::取得結果窗格資訊

調用此函數以檢索管理`RESULTDATAITEM`單元的結構。

```
GetResultPaneInfo (RESULTDATAITEM* pResultDataItem);
```

### <a name="parameters"></a>參數

*pResult 資料項目*<br/>
[出]指向物件`RESULTDATAITEM`結構`CSnapInItemImpl`的指標。

## <a name="csnapinitemimplm_bstrdisplayname"></a><a name="m_bstrdisplayname"></a>快照專案::m_bstrDisplayName

包含為節點項顯示的字串。

```
CComBSTR m_bstrDisplayName;
```

## <a name="csnapinitemimplm_scopedataitem"></a><a name="m_scopedataitem"></a>快照專案::m_scopeDataItem

卡`SCOPEDATAITEM`入數據對象的結構。

```
SCOPEDATAITEM m_scopeDataItem;
```

## <a name="csnapinitemimplm_resultdataitem"></a><a name="m_resultdataitem"></a>快照專案::m_resultDataItem

入卡資料物件的[RESULTDATAITEM](/windows/win32/api/mmc/ns-mmc-resultdataitem)結構。

```
RESULTDATAITEM m_resultDataItem;
```

## <a name="csnapinitemimplnotify"></a><a name="notify"></a>快照專案::通知

當使用者對卡入物件執行操作時調用。

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
[在]標識用戶執行的操作。 以下通知是可能的:

- MMCN_ACTIVATE啟動和停用視窗時已發送。

- MMCN_ADD_IMAGES已發送以將圖像添加到結果窗格。

- MMCN_BTN_CLICK當用戶按一下其中一個工具列按鈕時已發送。

- MMCN_CLICK當用戶按一下清單檢視專案上的滑鼠按鈕時已發送。

- 當用戶雙擊清單檢視專案上的滑鼠按鈕時,MMCN_DBLCLICK已發送。

- MMCN_DELETE已發送通知管理單元該物件應刪除。

- MMCN_EXPAND資料夾需要展開或收縮時已發送。

- MMCN_MINIMIZED視窗最小化或最大化時發送。

- MMCN_PROPERTY_CHANGE已發送通知卡入物件,即卡入對象的檢視即將更改。

- MMCN_REMOVE_CHILDREN當管理單元必須刪除它在指定節點下方添加的整個子樹時,已發送。

- MMCN_RENAME 首次發送用於查詢重命名,第二次進行重命名。

- MMCN_SELECT在選擇範圍或結果視窗格中的項時已發送。

- MMCN_SHOW首次選擇或取消選擇示波器項時已發送。

- MMCN_VIEW_CHANGE在發生更改時,當管理單元可以更新所有視圖時,已發送。

*精 氨 酸*<br/>
[在]取決於通知類型。

*參數*<br/>
[在]取決於通知類型。

*P 元件資料*<br/>
[出]指向實現`IComponentData`的物件的指標。 如果未從`IComponentData::Notify`轉發通知,則此參數為 NULL。

*P 元件*<br/>
[出]指向實現`IComponent`的物件的指標。 如果未從`IComponent::Notify`轉發通知,則此參數為 NULL。

*type*<br/>
[在]指定物件的類型。 其值可以是下列其中一個值：

- CCT_SCOPE範圍窗格上下文的數據物件。

- CCT_RESULT結果窗格上下文的數據物件。

- CCT_SNAPIN_MANAGER用於管理單元上下文的數據物件。

- CCT_UNINITIALIZED資料物件的類型無效。

## <a name="csnapinitemimplquerypagesfor"></a><a name="querypagesfor"></a>快照項目::查詢頁面

已調用以查看管理單元節點是否支援屬性頁。

```
QueryPagesFor(DATA_OBJECT_TYPES type);
```

## <a name="csnapinitemimplsetmenuinsertionflags"></a><a name="setmenuinsertionflags"></a>快照項目::設定Menu插入標記

呼叫此函數以修改插入物件(由*p插入允許*)指定的選單插入標誌。

```cpp
void SetMenuInsertionFlags(
    bool bBeforeInsertion,
    long* pInsertionAllowed);
```

### <a name="parameters"></a>參數

*b 插入前*<br/>
[在]在將項添加到上下文菜單之前調用函數時,應不為零;否則 0。

*p 允許插入*<br/>
[進出]標識可以使用的 Microsoft 管理主控台 (MMC) 定義的選單項插入點。 這可以是以下旗標的組合:

- CCM_INSERTIONALLOWED_TOP項可以插入到上下文菜單的頂部。

- CCM_INSERTIONALLOWED_NEW項可以插入到"創建新"子功能表中。

- CCM_INSERTIONALLOWED_TASK項可以插入到任務子功能表中。

- CCM_INSERTIONALLOWED_VIEW項可以插入工具列檢視功能表或結果窗格上下文菜單的「查看子功能表」。

### <a name="remarks"></a>備註

如果要開發主插入,可以重置任何插入標誌,以限制第三方擴展可以添加的菜單項類型。 例如,主管理單元可以清除CCM_INSERTIONALLOWED_NEW標誌,以防止擴展添加自己的"創建新"功能表項。

不應嘗試在 p*插入中*設定最初清除的位。 MMC 的未來版本可能使用當前未定義的位,因此不應更改當前未定義的位。

## <a name="csnapinitemimplsettoolbarbuttoninfo"></a><a name="settoolbarbuttoninfo"></a>快照專案::設定工具列按鈕資訊

呼叫此函數以在創建工具列之前修改卡入物件的任何工具列按鈕樣式。

```cpp
void SetToolbarButtonInfo(
    UINT id,
    BYTE* fsState,
    BYTE* fsType);
```

### <a name="parameters"></a>參數

*id*<br/>
[在]要設置的工具列按鈕的 ID。

*fsState*<br/>
[在]按鈕的狀態標誌。 可以是以下一種或多項:

- TBSTATE_CHECKED 按鈕具有TBSTYLE_CHECKED樣式,正在按下。

- TBSTATE_ENABLED 該按鈕接受用戶輸入。 沒有此狀態的按鈕不接受使用者輸入,並且為灰色。

- TBSTATE_HIDDEN 該按鈕不可見,無法接收用戶輸入。

- TBSTATE_INDETERMINATE 該按鈕為灰色。

- TBSTATE_PRESSED 按下按鈕。

- TBSTATE_WRAP按鈕後面的換行符。 該按鈕還必須具有TBSTATE_ENABLED。

*fsType*<br/>
[在]按鈕的狀態標誌。 可以是以下一種或多項:

- TBSTYLE_BUTTON 創建標準按鈕。

- TBSTYLE_CHECK 創建一個按鈕,每次使用者按下狀態和非按下狀態之間切換。 當按鈕處於按下狀態時,其背景顏色不同。

- TBSTYLE_CHECKGROUP 創建一個檢查按鈕,直到按下組中的另一個按鈕。

- TBSTYLE_GROUP 創建一個按鈕,直到按下組中的另一個按鈕。

- TBSTYLE_SEP 創建分隔符,在按鈕組之間提供一個小間隙。 具有此樣式的按鈕不會接收使用者輸入。

## <a name="csnapinitemimplupdatemenustate"></a><a name="updatemenustate"></a>快照專案::更新功能表狀態

調用此函數以在菜單項插入到卡入物件的上下文菜單之前對其進行修改。

```cpp
void UpdateMenuState(
    UINT id,
    LPTSTR pBuf,
    UINT* flags);
```

### <a name="parameters"></a>參數

*id*<br/>
[在]要設置的功能表項的 ID。

*普布夫*<br/>
[在]要更新的功能表項的字串的指標。

*flags*<br/>
[在]指定新的狀態標誌。 這可以是以下旗標的組合:

- MF_POPUP指定這是上下文菜單中的子菜單。 功能表項、插入點和進一步子功能表可以使用其`lCommandID``IInsertionPointID`作為添加到此子功能表。

- MF_BITMAP和MF_OWNERDRAW這些標誌是不允許的,並且將導致返回值E_INVALIDARG。

- MF_SEPARATOR繪製水準分界線。 只允許`IContextMenuProvider`添加設置MF_SEPARATOR功能表項。

- MF_CHECKED在菜單項旁邊放置複選標記。

- MF_DISABLED禁用功能表項,因此無法選擇,但標誌不會將其灰暗。

- MF_ENABLED 啟用功能表項以便可以選擇,將其從灰狀態還原。

- MF_GRAYED禁用功能表項,使其變灰,使其無法選擇。

- MF_MENUBARBREAK 功能與功能表欄的MF_MENUBREAK標誌相同。 對於下拉菜單、子功能表或快捷功能表,新列由垂直線與舊列分隔。

- MF_MENUBREAK將專案放在新行(功能表欄)或新列(對於下拉菜單、子功能表或快捷功能表)中,而不分隔列。

- MF_UNCHECKED不會在項目旁邊放置複選標記(預設值)。

以下旗標列不能使用:

- MF_DISABLED、MF_ENABLED和MF_GRAYED。

- MF_MENUBARBREAK和MF_MENUBREAK。

- MF_CHECKED和MF_UNCHECKED。

## <a name="csnapinitemimplupdatetoolbarbutton"></a><a name="updatetoolbarbutton"></a>快照專案::更新工具列按鈕

呼叫此函數以在顯示卡入物件之前修改該按鈕的工具列按鈕。

```
BOOL UpdateToolbarButton(UINT id, BYTE fsState);
```

### <a name="parameters"></a>參數

*id*<br/>
指定要更新的工具列按鈕的按鈕 ID。

*fsState*<br/>
指定工具列按鈕狀態。 如果要設置此狀態,則返回 TRUE。 這可以是以下旗標的組合:

- 啟用 該按鈕接受用戶輸入。 沒有此狀態的按鈕不接受使用者輸入,並且為灰色。

- 正在按下的「檢查」按鈕具有「檢查」樣式。

- 隱藏 這個按鈕不可見,無法接收使用者輸入。

- 不確定 按鈕為灰色。

- 按鈕按下按鈕。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
