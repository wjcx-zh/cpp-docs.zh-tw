---
title: CSnapInItemImpl 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- snap-ins, data items
- snap-ins, ATL support for
- CSnapInItemImpl class
- snap-ins
ms.assetid: 52caefbd-9eae-49b0-add2-d55524271aa7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 759917497f06f80cde97f4e1bba9f3711add94a8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="csnapinitemimpl-class"></a>CSnapInItemImpl 類別
這個類別會提供實作的嵌入式管理單元節點物件的方法。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template <class T, BOOL bIsExtension = FALSE>  
class ATL_NO_VTABLE CSnapInItemImpl : public CSnapInItem
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`CSnapInItemImpl`。  
  
 *bIsExtension*  
 **TRUE**如果物件是嵌入式管理單元擴充功能; 否則**FALSE**。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CSnapInItemImpl::CSnapInItemImpl](#csnapinitemimpl)|建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CSnapInItemImpl::AddMenuItems](#addmenuitems)|將功能表項目加入至內容功能表。|  
|[CSnapInItemImpl::Command](#command)|選取自訂功能表項目時，請呼叫主控台。|  
|[CSnapInItemImpl::CreatePropertyPages](#createpropertypages)|將頁面新增至嵌入式管理單元的屬性工作表。|  
|[CSnapInItemImpl::FillData](#filldata)|嵌入式管理單元的物件複製資訊到指定的資料流。|  
|[CSnapInItemImpl::GetResultPaneInfo](#getresultpaneinfo)|擷取**RESULTDATAITEM**嵌入式管理單元的結構。|  
|[CSnapInItemImpl::GetResultViewType](#getresultviewtype)|決定檢視結果 窗格所使用的型別。|  
|[CSnapInItemImpl::GetScopePaneInfo](#getscopepaneinfo)|擷取**SCOPEDATAITEM**嵌入式管理單元的結構。|  
|[CSnapInItemImpl::Notify](#notify)|呼叫以通知嵌入式管理單元的使用者所採取的動作主控台。|  
|[CSnapInItemImpl::QueryPagesFor](#querypagesfor)|呼叫以嵌入式管理單元的節點是否支援屬性頁。|  
|[CSnapInItemImpl::SetMenuInsertionFlags](#setmenuinsertionflags)|修改嵌入式管理單元物件的功能表插入旗標。|  
|[CSnapInItemImpl::SetToolbarButtonInfo](#settoolbarbuttoninfo)|設定指定的工具列按鈕的資訊。|  
|[CSnapInItemImpl::UpdateMenuState](#updatemenustate)|更新操作功能表項目的狀態。|  
|[CSnapInItemImpl::UpdateToolbarButton](#updatetoolbarbutton)|更新指定的工具列按鈕的狀態。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CSnapInItemImpl::m_bstrDisplayName](#m_bstrdisplayname)|嵌入式管理單元之物件的名稱。|  
|[CSnapInItemImpl::m_resultDataItem](#m_resultdataitem)|Windows **RESULTDATAITEM**所使用的結構`CSnapInItemImpl`物件。|  
|[CSnapInItemImpl::m_scopeDataItem](#m_scopedataitem)|Windows **SCOPEDATAITEM**所使用的結構`CSnapInItemImpl`物件。|  
  
## <a name="remarks"></a>備註  
 `CSnapInItemImpl` 提供基本實作嵌入式管理單元節點物件，例如加入功能表項目和工具列，以及轉送至適當的處理常式函式的嵌入式管理單元 節點的命令。 這些功能會使用數個不同的介面實作，並將型別對應。 預設實作會處理由判斷正確的執行個體的衍生類別，並再轉送到正確的執行個體訊息傳送至節點物件的通知。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CSnapInItem`  
  
 `CSnapInItemImpl`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlsnap.h  
  
##  <a name="addmenuitems"></a>  CSnapInItemImpl::AddMenuItems  
 這個方法會實作的 Win32 函式[IExtendContextMenu::AddMenuItems](http://msdn.microsoft.com/library/aa814841)。  
  
```
AddMenuItems(  
    LPCONTEXTMENUCALLBACK piCallback,
    long* pInsertionAllowed,
    DATA_OBJECT_TYPES type);
```  
  
### <a name="parameters"></a>參數  
 *piCallback*  
 [in]指標**IContextMenuCallback** ，可以將項目加入至內容功能表。  
  
 `pInsertionAllowed`  
 [in、 out]識別 Microsoft Management Console MMC 定義功能表項目插入點可用。 這可以是下列旗標的組合：  
  
- **CCM_INSERTIONALLOWED_TOP**可以在內容功能表的頂端插入項目。  
  
- **CCM_INSERTIONALLOWED_NEW**可以建立新的子功能表中插入項目。  
  
- **CCM_INSERTIONALLOWED_TASK**可以插入 [工作] 子功能表中的項目。  
  
- **CCM_INSERTIONALLOWED_VIEW**可以在結果窗格的內容功能表中的 [檢視] 子功能表或工具列的 [檢視] 功能表中，插入項目。  
  
 `type`  
 [in]指定物件的類型。 它可以包含下列值之一：  
  
- **CCT_SCOPE**範圍窗格之內容的資料物件。  
  
- **CCT_RESULT**結果窗格之內容的資料物件。  
  
- **CCT_SNAPIN_MANAGER**管理員 嵌入式管理單元中之內容的資料物件。  
  
- **CCT_UNINITIALIZED**資料物件都有無效的類型。  
  
##  <a name="command"></a>  CSnapInItemImpl::Command  
 這個方法會實作的 Win32 函式[IExtendContextMenu::Command](http://msdn.microsoft.com/library/aa814842)。  
  
```
Command(long lCommandID, DATA_OBJECT_TYPES type);
```  
  
### <a name="parameters"></a>參數  
 *lCommandID*  
 [in]指定功能表項目的命令識別碼。  
  
 `type`  
 [in]指定物件的類型。 它可以包含下列值之一：  
  
- **CCT_SCOPE**範圍窗格之內容的資料物件。  
  
- **CCT_RESULT**結果窗格之內容的資料物件。  
  
- **CCT_SNAPIN_MANAGER**管理員 嵌入式管理單元中之內容的資料物件。  
  
- **CCT_UNINITIALIZED**資料物件都有無效的類型。  
  
##  <a name="createpropertypages"></a>  CSnapInItemImpl::CreatePropertyPages  
 這個方法會實作的 Win32 函式[IExtendPropertySheet::CreatePropertyPages](http://msdn.microsoft.com/library/aa814846)。  
  
```
CreatePropertyPages(  
    LPPROPERTYSHEETCALLBACK lpProvider,
    long handle,
    IUnknown* pUnk,
    DATA_OBJECT_TYPES type);
```  
  
### <a name="parameters"></a>參數  
 *lpProvider*  
 [in]指標**IPropertySheetCallback**介面。  
  
 *控制代碼*  
 [in]指定的控制代碼，用來路由**MMCN_PROPERTY_CHANGE**通知訊息至適當的資料類別。  
  
 *pUnk*  
 [in]指標**IExtendPropertySheet**包含內容節點的相關資訊的物件上的介面。  
  
 `type`  
 [in]指定物件的類型。 它可以包含下列值之一：  
  
- **CCT_SCOPE**範圍窗格之內容的資料物件。  
  
- **CCT_RESULT**結果窗格之內容的資料物件。  
  
- **CCT_SNAPIN_MANAGER**管理員 嵌入式管理單元中之內容的資料物件。  
  
- **CCT_UNINITIALIZED**資料物件都有無效的類型。  
  
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
 `cf`  
 [in]剪貼簿格式 （文字、 豐富的文字或 rtf 文字與 OLE 項目）。  
  
 `pStream`  
 [in]包含的物件資料的資料流指標。  
  
### <a name="remarks"></a>備註  
 若要正確實作此函式，將正確的資訊複製到資料流 ( `pStream`)，取決於所指出的剪貼簿格式`cf`。  
  
##  <a name="getresultviewtype"></a>  CSnapInItemImpl::GetResultViewType  
 呼叫此函式可擷取的嵌入式管理單元之物件的 [結果] 窗格的檢視類型。  
  
```
GetResultViewType(
    LPOLESTR* ppViewType,
    long* pViewOptions);
```  
  
### <a name="parameters"></a>參數  
 *ppViewType*  
 [out]傳回的檢視類型的位址指標。  
  
 *pViewOptions*  
 [out]指標**MMC_VIEW_OPTIONS**列舉型別，提供選項指定的擁有者的嵌入式管理單元主控台。 這個值可以是下列其中一項：  
  
- **MMC_VIEW_OPTIONS_NOLISTVIEWS** = 0x00000001 告訴主控台，以避免呈現標準的清單中的檢視選擇**檢視**功能表。 可讓嵌入式管理單元只在結果檢視 窗格中顯示它自己的自訂檢視。 這是定義在這個階段的唯一選項旗標。  
  
- **MMC_VIEW_OPTIONS_NONE** = 0 允許預設的檢視選項。  
  
##  <a name="getscopepaneinfo"></a>  CSnapInItemImpl::GetScopePaneInfo  
 呼叫此函式可擷取**SCOPEDATAITEM**嵌入式管理單元的結構。  
  
```
GetScopePaneInfo (SCOPEDATAITEM* pScopeDataItem);
```  
  
### <a name="parameters"></a>參數  
 *pScopeDataItem*  
 [out]指標**SCOPEDATAITEM**結構`CSnapInItemImpl`物件。  
  
##  <a name="getresultpaneinfo"></a>  CSnapInItemImpl::GetResultPaneInfo  
 呼叫此函式可擷取**RESULTDATAITEM**嵌入式管理單元的結構。  
  
```
GetResultPaneInfo (RESULTDATAITEM* pResultDataItem);
```  
  
### <a name="parameters"></a>參數  
 *pResultDataItem*  
 [out]指標**RESULTDATAITEM**結構`CSnapInItemImpl`物件。  
  
##  <a name="m_bstrdisplayname"></a>  CSnapInItemImpl::m_bstrDisplayName  
 包含節點的項目所顯示的字串。  
  
```
CComBSTR m_bstrDisplayName;
```  
  
##  <a name="m_scopedataitem"></a>  CSnapInItemImpl::m_scopeDataItem  
 `SCOPEDATAITEM`嵌入式管理單元資料物件的結構。  
  
```
SCOPEDATAITEM m_scopeDataItem;
```  
  
##  <a name="m_resultdataitem"></a>  CSnapInItemImpl::m_resultDataItem  
 [RESULTDATAITEM](http://msdn.microsoft.com/library/aa815165)嵌入式管理單元資料物件的結構。  
  
```
RESULTDATAITEM m_resultDataItem;
```  
  
##  <a name="notify"></a>  CSnapInItemImpl::Notify  
 當使用者起嵌入式管理單元的物件時呼叫。  
  
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
 `event`  
 [in]識別使用者所採取的動作。 下列通知則可能會：  
  
- **MMCN_ACTIVATE** Sent 當視窗是要啟用和停用。  
  
- **MMCN_ADD_IMAGES**傳送至將影像加入至 [結果] 窗格。  
  
- **MMCN_BTN_CLICK**當使用者按一下其中一個工具列按鈕時傳送。  
  
- **MMCN_CLICK**當使用者按一下滑鼠按鈕在清單檢視項目上的時傳送。  
  
- **MMCN_DBLCLICK**當使用者按兩下滑鼠按鈕在清單檢視項目上的時傳送。  
  
- **MMCN_DELETE**傳送通知的嵌入式管理單元的物件應該刪除。  
  
- **MMCN_EXPAND**資料夾需要展開或收縮時傳送。  
  
- **MMCN_MINIMIZED** Sent 當視窗是在最小化或最大化。  
  
- **MMCN_PROPERTY_CHANGE**通知即將變更嵌入式管理單元物件檢視的嵌入式管理單元物件傳送。  
  
- **MMCN_REMOVE_CHILDREN**嵌入式管理單元必須刪除它加入指定的節點下的整個樹狀子目錄時傳送。  
  
- **MMCN_RENAME**傳送第一次重新命名的查詢和第二次執行重新命名。  
  
- **MMCN_SELECT**傳送選取範圍或結果檢視 窗格中的項目時。  
  
- **MMCN_SHOW**時範圍項目是選取或取消選取第一次傳送。  
  
- **MMCN_VIEW_CHANGE**時嵌入式管理單元可以更新所有的檢視表發生變更時傳送。  
  
 `arg`  
 [in]通知類型而定。  
  
 `param`  
 [in]通知類型而定。  
  
 *pComponentData*  
 [out]指標物件實作**IComponentData**。 這個參數是**NULL**如果通知未從轉寄**IComponentData::Notify**。  
  
 *pComponent*  
 [out]實作的物件的指標**IComponent**。 這個參數是**NULL**如果通知未從轉寄**IComponent::Notify**。  
  
 `type`  
 [in]指定物件的類型。 它可以包含下列值之一：  
  
- **CCT_SCOPE**範圍窗格之內容的資料物件。  
  
- **CCT_RESULT**結果窗格之內容的資料物件。  
  
- **CCT_SNAPIN_MANAGER**管理員 嵌入式管理單元中之內容的資料物件。  
  
- **CCT_UNINITIALIZED**資料物件都有無效的類型。  
  
##  <a name="querypagesfor"></a>  CSnapInItemImpl::QueryPagesFor  
 呼叫以嵌入式管理單元的節點是否支援屬性頁。  
  
```
QueryPagesFor(DATA_OBJECT_TYPES type);
```  
  
##  <a name="setmenuinsertionflags"></a>  CSnapInItemImpl::SetMenuInsertionFlags  
 呼叫此函式可修改的功能表插入旗標，指定`pInsertionAllowed`，嵌入式管理單元的物件。  
  
```
void SetMenuInsertionFlags(  
    bool bBeforeInsertion,
    long* pInsertionAllowed);
```  
  
### <a name="parameters"></a>參數  
 *bBeforeInsertion*  
 [in]為非零，如果項目加入至內容功能表; 之前，應該呼叫此函式否則便是 0。  
  
 `pInsertionAllowed`  
 [in、 out]識別 Microsoft Management Console MMC 定義功能表項目插入點可用。 這可以是下列旗標的組合：  
  
- **CCM_INSERTIONALLOWED_TOP**可以在內容功能表的頂端插入項目。  
  
- **CCM_INSERTIONALLOWED_NEW**可以建立新的子功能表中插入項目。  
  
- **CCM_INSERTIONALLOWED_TASK**可以插入 [工作] 子功能表中的項目。  
  
- **CCM_INSERTIONALLOWED_VIEW**可以在結果窗格的內容功能表中的 [檢視] 子功能表或工具列的 [檢視] 功能表中，插入項目。  
  
### <a name="remarks"></a>備註  
 如果您正在開發的主要的嵌入式管理單元，您就可以將任何這種限制的第三方擴充功能可以加入功能表項目類型的插入旗標重設。 例如，主要的嵌入式管理單元可以清除**CCM_INSERTIONALLOWED_NEW**旗標，以防止加入自己建立新的功能表項目延伸。  
  
 您不應嘗試設定的位元`pInsertionAllowed`，原先已清除。 MMC 的未來版本可能會使用目前未定義，所以您不應變更目前未定義的位元的位元。  
  
##  <a name="settoolbarbuttoninfo"></a>  CSnapInItemImpl::SetToolbarButtonInfo  
 呼叫此函式可修改任何工具列按鈕樣式，將嵌入式管理單元物件的建立工具列之前。  
  
```
void SetToolbarButtonInfo(  
    UINT id,
    BYTE* fsState,
    BYTE* fsType);
```  
  
### <a name="parameters"></a>參數  
 `id`  
 [in]工具列按鈕，以設定識別碼。  
  
 `fsState`  
 [in]按鈕的狀態旗標。 可以是下列一或多個項目：  
  
- `TBSTATE_CHECKED` 按鈕的**TBSTYLE_CHECKED**樣式，並按下。  
  
- `TBSTATE_ENABLED` [] 按鈕，接受使用者輸入。 沒有此狀態的按鈕不接受使用者輸入，並會變成灰色。  
  
- `TBSTATE_HIDDEN` 按鈕看不到，並無法接收使用者輸入。  
  
- `TBSTATE_INDETERMINATE` 按鈕會變成灰色。  
  
- `TBSTATE_PRESSED` 按鈕已按下。  
  
- `TBSTATE_WRAP` 分行符號會遵循 [] 按鈕。 按鈕還必須`TBSTATE_ENABLED`。  
  
 *fsType*  
 [in]按鈕的狀態旗標。 可以是下列一或多個項目：  
  
- `TBSTYLE_BUTTON` 建立標準的按鈕。  
  
- `TBSTYLE_CHECK` 建立按下的按鍵和 not 按下狀態每次使用者按一下切換按鈕。 按下狀態時，按鈕會有不同的背景色彩。  
  
- `TBSTYLE_CHECKGROUP` 建立核取按鈕保持已按下群組中的另一個按鈕按下為止。  
  
- `TBSTYLE_GROUP` 建立直到按下群組中的另一個按鈕是處於已按下按鈕。  
  
- `TBSTYLE_SEP` 建立提供小的缺口按鈕群組之間的分隔符號。 具有此樣式的按鈕不會接收使用者輸入。  
  
##  <a name="updatemenustate"></a>  CSnapInItemImpl::UpdateMenuState  
 呼叫此函式可修改的功能表項目之前插入的嵌入式管理單元物件的內容功能表。  
  
```
void UpdateMenuState(  
    UINT id,
    LPTSTR pBuf,
    UINT* flags);
```  
  
### <a name="parameters"></a>參數  
 `id`  
 [in]若要設定功能表項目的識別碼。  
  
 `pBuf`  
 [in]要更新功能表項目的字串指標。  
  
 `flags`  
 [in]指定新的狀態旗標。 這可以是下列旗標的組合：  
  
- **MF_POPUP**指定內容功能表中的子功能表。 功能表項目、 插入點，以及進一步的子功能表可能會加入至這個子功能表使用其**lCommandID**做為其**IInsertionPointID**。  
  
- **MF_BITMAP**和`MF_OWNERDRAW`不允許使用這些旗標，而會傳回值`E_INVALIDARG`。  
  
- **MF_SEPARATOR**繪製水平分隔線。 只有**IContextMenuProvider**允許加入功能表項目**MF_SEPARATOR**設定。  
  
- **MF_CHECKED**功能表項目旁的核取記號。  
  
- **MF_DISABLED**停用功能表項目，因此無法選取它，但是旗標不會不停用它。  
  
- `MF_ENABLED` 可讓功能表項目，因此也可以選取，會從其呈現灰色的狀態還原。  
  
- **MF_GRAYED**停用功能表項目，因此不會選取對於它。  
  
- **MF_MENUBARBREAK**函數一樣**MF_MENUBREAK**功能表列的旗標。 下拉功能表、 子功能表，或快顯功能表中，新的資料行是舊的資料行被分隔垂直線條。  
  
- **MF_MENUBREAK**將項目放在新行 （適用於功能表列） 或新的資料行 （適用於下拉功能表、 子功能表或快顯功能表） 而不分隔資料行中。  
  
- **MF_UNCHECKED**並不會在項目 （預設值） 旁邊的核取記號。  
  
 不能同時使用旗標的下列群組：  
  
- **MF_DISABLED**， `MF_ENABLED`，和**MF_GRAYED**。  
  
- **MF_MENUBARBREAK**和**MF_MENUBREAK**。  
  
- **MF_CHECKED**和**MF_UNCHECKED**。  
  
##  <a name="updatetoolbarbutton"></a>  CSnapInItemImpl::UpdateToolbarButton  
 呼叫此函式可修改工具列按鈕，將嵌入式管理單元物件的顯示之前。  
  
```
BOOL UpdateToolbarButton(UINT id, BYTE fsState);
```  
  
### <a name="parameters"></a>參數  
 `id`  
 指定工具列按鈕的按鈕 ID，更新。  
  
 `fsState`  
 指定的工具列按鈕的狀態。 如果要設定此狀態，則傳回**TRUE**。 這可以是下列旗標的組合：  
  
- **啟用**按鈕接受使用者輸入。 沒有此狀態的按鈕不接受使用者輸入，並會變成灰色。  
  
- **檢查**按鈕具有**檢查**樣式，並按下。  
  
- **隱藏**按鈕是不可見的無法接收使用者輸入。  
  
- **不定**按鈕會變成灰色。  
  
- **BUTTONPRESSED**按鈕按下。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
