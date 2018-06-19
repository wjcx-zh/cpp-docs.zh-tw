---
title: CBaseTabbedPane 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CBaseTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane::AddTab
- AFXBASETABBEDPANE/CBaseTabbedPane::AllowDestroyEmptyTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane::ApplyRestoredTabInfo
- AFXBASETABBEDPANE/CBaseTabbedPane::CanFloat
- AFXBASETABBEDPANE/CBaseTabbedPane::CanSetCaptionTextToTabName
- AFXBASETABBEDPANE/CBaseTabbedPane::ConvertToTabbedDocument
- AFXBASETABBEDPANE/CBaseTabbedPane::DetachPane
- AFXBASETABBEDPANE/CBaseTabbedPane::EnableSetCaptionTextToTabName
- AFXBASETABBEDPANE/CBaseTabbedPane::FillDefaultTabsOrderArray
- AFXBASETABBEDPANE/CBaseTabbedPane::FindBarByTabNumber
- AFXBASETABBEDPANE/CBaseTabbedPane::FindPaneByID
- AFXBASETABBEDPANE/CBaseTabbedPane::FloatTab
- AFXBASETABBEDPANE/CBaseTabbedPane::GetDefaultTabsOrder
- AFXBASETABBEDPANE/CBaseTabbedPane::GetFirstVisibleTab
- AFXBASETABBEDPANE/CBaseTabbedPane::GetMinSize
- AFXBASETABBEDPANE/CBaseTabbedPane::GetPaneIcon
- AFXBASETABBEDPANE/CBaseTabbedPane::GetPaneList
- AFXBASETABBEDPANE/CBaseTabbedPane::GetTabArea
- AFXBASETABBEDPANE/CBaseTabbedPane::GetTabsNum
- AFXBASETABBEDPANE/CBaseTabbedPane::GetUnderlyingWindow
- AFXBASETABBEDPANE/CBaseTabbedPane::GetVisibleTabsNum
- AFXBASETABBEDPANE/CBaseTabbedPane::HasAutoHideMode
- AFXBASETABBEDPANE/CBaseTabbedPane::IsHideSingleTab
- AFXBASETABBEDPANE/CBaseTabbedPane::RecalcLayout
- AFXBASETABBEDPANE/CBaseTabbedPane::RemovePane
- AFXBASETABBEDPANE/CBaseTabbedPane::SetAutoDestroy
- AFXBASETABBEDPANE/CBaseTabbedPane::SetAutoHideMode
- AFXBASETABBEDPANE/CBaseTabbedPane::ShowTab
dev_langs:
- C++
helpviewer_keywords:
- CBaseTabbedPane [MFC], AddTab
- CBaseTabbedPane [MFC], AllowDestroyEmptyTabbedPane
- CBaseTabbedPane [MFC], ApplyRestoredTabInfo
- CBaseTabbedPane [MFC], CanFloat
- CBaseTabbedPane [MFC], CanSetCaptionTextToTabName
- CBaseTabbedPane [MFC], ConvertToTabbedDocument
- CBaseTabbedPane [MFC], DetachPane
- CBaseTabbedPane [MFC], EnableSetCaptionTextToTabName
- CBaseTabbedPane [MFC], FillDefaultTabsOrderArray
- CBaseTabbedPane [MFC], FindBarByTabNumber
- CBaseTabbedPane [MFC], FindPaneByID
- CBaseTabbedPane [MFC], FloatTab
- CBaseTabbedPane [MFC], GetDefaultTabsOrder
- CBaseTabbedPane [MFC], GetFirstVisibleTab
- CBaseTabbedPane [MFC], GetMinSize
- CBaseTabbedPane [MFC], GetPaneIcon
- CBaseTabbedPane [MFC], GetPaneList
- CBaseTabbedPane [MFC], GetTabArea
- CBaseTabbedPane [MFC], GetTabsNum
- CBaseTabbedPane [MFC], GetUnderlyingWindow
- CBaseTabbedPane [MFC], GetVisibleTabsNum
- CBaseTabbedPane [MFC], HasAutoHideMode
- CBaseTabbedPane [MFC], IsHideSingleTab
- CBaseTabbedPane [MFC], RecalcLayout
- CBaseTabbedPane [MFC], RemovePane
- CBaseTabbedPane [MFC], SetAutoDestroy
- CBaseTabbedPane [MFC], SetAutoHideMode
- CBaseTabbedPane [MFC], ShowTab
ms.assetid: f22c0080-5b29-4a0a-8f74-8f0a4cd2dbcf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d628758f19c36112bf896e11c97df3e1f92cbc47
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355947"
---
# <a name="cbasetabbedpane-class"></a>CBaseTabbedPane 類別
擴充 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) 的功能，以支援建立索引標籤式視窗。  
  
## <a name="syntax"></a>語法  
  
```  
class CBaseTabbedPane : public CDockablePane  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|`CBaseTabbedPane::CBaseTabbedPane`|預設建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Cbasetabbedpane:: Addtab](#addtab)|將新的索引標籤加入至索引標籤式窗格。|  
|[CBaseTabbedPane::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|指定是否可以終結空的索引標籤式的窗格。|  
|[CBaseTabbedPane::ApplyRestoredTabInfo](#applyrestoredtabinfo)|適用於載入登錄中，從索引標籤式窗格的索引標籤設定。|  
|[CBaseTabbedPane::CanFloat](#canfloat)|決定是否可以浮動窗格。 (覆寫[CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)。)|  
|[CBaseTabbedPane::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|決定索引標籤式窗格的標題是否應該為作用中的索引標籤會顯示相同的文字。|  
|[CBaseTabbedPane::ConvertToTabbedDocument](#converttotabbeddocument)|(覆寫[CDockablePane::ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument)。)|  
|[Cbasetabbedpane:: Detachpane](#detachpane)|將 MDI 索引標籤式文件中的一個或多個可停駐窗格。|  
|[CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)|啟用或停用索引標籤式窗格的 [作用中] 索引標籤上的標籤文字與同步處理標題文字的能力。|  
|[CBaseTabbedPane::FillDefaultTabsOrderArray](#filldefaulttabsorderarray)|還原 [內部] 索引標籤順序設為預設狀態。|  
|[CBaseTabbedPane::FindBarByTabNumber](#findbarbytabnumber)|傳回位於索引標籤時以零為起始的索引所識別的索引標籤的窗格。|  
|||  
|[CBaseTabbedPane::FindPaneByID](#findpanebyid)|傳回窗格識別碼所識別的窗格|  
|[Cbasetabbedpane:: Floattab](#floattab)|讓窗格浮動，但僅限於窗格目前位於可卸離的索引標籤時。|  
|[CBaseTabbedPane::GetDefaultTabsOrder](#getdefaulttabsorder)|傳回在窗格中的索引標籤的預設順序。|  
|[CBaseTabbedPane::GetFirstVisibleTab](#getfirstvisibletab)|擷取第一個顯示索引標籤的指標。|  
|[CBaseTabbedPane::GetMinSize](#getminsize)|擷取最小允許大小的窗格。 (覆寫[CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize)。)|  
|[CBaseTabbedPane::GetPaneIcon](#getpaneicon)|傳回窗格圖示的控制代碼。 (覆寫[CBasePane::GetPaneIcon](../../mfc/reference/cbasepane-class.md#getpaneicon)。)|  
|[CBaseTabbedPane::GetPaneList](#getpanelist)|在索引標籤式窗格中，會傳回一份包含窗格。|  
|[CBaseTabbedPane::GetTabArea](#gettabarea)|傳回的頂端和底部的索引標籤區域的週框矩形。|  
|[CBaseTabbedPane::GetTabsNum](#gettabsnum)|傳回在索引標籤 視窗中的索引標籤的計數。|  
|[CBaseTabbedPane::GetUnderlyingWindow](#getunderlyingwindow)|取得基礎 （包裝） 索引標籤視窗。|  
|[CBaseTabbedPane::GetVisibleTabsNum](#getvisibletabsnum)|傳回顯示索引標籤的計數。|  
|[Cbasetabbedpane:: Hasautohidemode](#hasautohidemode)|決定索引標籤式的窗格是否可以切換為自動隱藏模式。|  
|[CBaseTabbedPane::IsHideSingleTab](#ishidesingletab)|決定索引標籤式的窗格是否會取消隱藏如果只有一個索引標籤會顯示。|  
|`CBaseTabbedPane::LoadSiblingPaneIDs`|在序列化期間，在內部使用。|  
|[CBaseTabbedPane::RecalcLayout](#recalclayout)|重新計算窗格的配置資訊。 (覆寫[cpane:: Recalclayout](../../mfc/reference/cpane-class.md#recalclayout)。)|  
|[CBaseTabbedPane::RemovePane](#removepane)|從索引標籤式窗格中移除窗格。|  
|`CBaseTabbedPane::SaveSiblingBarIDs`|在序列化期間，在內部使用。|  
|`CBaseTabbedPane::Serialize`|(覆寫[cdockablepane:: Serialize](http://msdn.microsoft.com/en-us/09787e59-e446-4e76-894b-206d303dcfd6)。)|  
|`CBaseTabbedPane::SerializeTabWindow`|在序列化期間，在內部使用。|  
|[CBaseTabbedPane::SetAutoDestroy](#setautodestroy)|判斷是否會自動終結索引標籤式的控制列。|  
|[CBaseTabbedPane::SetAutoHideMode](#setautohidemode)|停駐窗格之間顯示的切換按鈕和 自動隱藏模式。 (覆寫[CDockablePane::SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode)。)|  
|[CBaseTabbedPane::ShowTab](#showtab)|顯示或隱藏 索引標籤。|  
  
## <a name="remarks"></a>備註  
 這個類別是抽象類別，而且無法具現化。 它會實作通用於所有類型的索引標籤式窗格的服務。  
  
 目前的程式庫包含兩個衍生的索引標籤式的窗格的類別： [CTabbedPane 類別](../../mfc/reference/ctabbedpane-class.md)和[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)。  
  
 A`CBaseTabbedPane`物件會包裝的指標[CMFCBaseTabCtrl 類別](../../mfc/reference/cmfcbasetabctrl-class.md)物件。 [CMFCBaseTabCtrl 類別](../../mfc/reference/cmfcbasetabctrl-class.md)就會變成索引標籤式窗格中的子視窗。  
  
 如需如何建立索引標籤式的窗格的詳細資訊，請參閱[CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)， [CTabbedPane 類別](../../mfc/reference/ctabbedpane-class.md)，和[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 `CBaseTabbedPane`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxBaseTabbedPane.h  
  
##  <a name="addtab"></a>  Cbasetabbedpane:: Addtab  
 將新的索引標籤加入至索引標籤式窗格。  
  
```  
virtual BOOL AddTab(
    CWnd* pNewBar,  
    BOOL bVisible = TRUE,  
    BOOL bSetActive = TRUE,  
    BOOL bDetachable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in][out] `pNewBar`  
 若要加入窗格指標。 此指標可能會變成無效之後呼叫這個方法。 如需詳細資訊，請參閱＜備註＞一節。  
  
 [輸入] `bVisible`  
 `TRUE` 若要顯示 [] 索引標籤。否則， `FALSE`。  
  
 [輸入] `bSetActive`  
 `TRUE` 讓 [] 索引標籤作用中的索引標籤。否則， `FALSE`。  
  
 [輸入] `bDetachable`  
 `TRUE` 要中斷連結; 索引標籤否則， `FALSE`。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果已成功加入成為的索引標籤的窗格，且未損毀處理序中。 `FALSE` 如果要加入的窗格是類型的物件`CBaseTabbedPane`。 如需詳細資訊，請參閱＜備註＞一節。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法，以加入為新的索引標籤上的索引標籤式窗格的窗格。 如果`pNewBar`指向型別的物件`CBaseTabbedPane`，其所有的索引標籤會複製到索引標籤式窗格，然後`pNewBar`終結。 因此，`pNewBar`會變成無效的指標，因此不應使用。  
  
##  <a name="allowdestroyemptytabbedpane"></a>  CBaseTabbedPane::AllowDestroyEmptyTabbedPane  
 指定是否可以終結空的索引標籤式的窗格。  
  
```  
virtual BOOL AllowDestroyEmptyTabbedPane() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果可以終結空的索引標籤式的窗格。否則， `FALSE`。 預設實作一定會傳回`TRUE`。  
  
### <a name="remarks"></a>備註  
 如果也將被銷毀不允許空白的索引標籤式的窗格，架構會改為隱藏窗格。  
  
##  <a name="applyrestoredtabinfo"></a>  CBaseTabbedPane::ApplyRestoredTabInfo  
 從登錄載入索引標籤的設定，並將其套用至索引標籤式窗格。  
  
```  
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bUseTabIndexes`  
 由架構內部使用這個參數。  
  
### <a name="remarks"></a>備註  
 這個方法是由架構呼叫，當您重新載入專案從登錄的銜接狀態資訊。 方法會取得定位順序和索引標籤式窗格的索引標籤名稱的資訊。  
  
##  <a name="canfloat"></a>  CBaseTabbedPane::CanFloat  
 指定是否可以浮動索引標籤式的窗格。  
  
```  
virtual BOOL CanFloat() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果可以浮動窗格;，否則， `FALSE`。  
  
##  <a name="cansetcaptiontexttotabname"></a>  CBaseTabbedPane::CanSetCaptionTextToTabName  
 決定索引標籤式窗格的標題是否應該為作用中的索引標籤會顯示相同的文字。  
  
```  
virtual BOOL CanSetCaptionTextToTabName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果索引標籤式窗格的標題文字設定為使用中的索引標籤; 的文字否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 方法用來決定文字來顯示索引標籤式的窗格標題重複的項目上的作用中的索引標籤的標籤。您可以啟用或停用此功能藉由呼叫[CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)。  
  
##  <a name="converttotabbeddocument"></a>  CBaseTabbedPane::ConvertToTabbedDocument  
 將 MDI 索引標籤式文件中的一個或多個可停駐窗格。  
  
```  
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bActiveTabOnly`  
 當您轉換的索引標籤式的窗格時，指定`TRUE`轉換使用中索引標籤。指定`FALSE`轉換在窗格中的所有索引標籤。  
  
##  <a name="detachpane"></a>  Cbasetabbedpane:: Detachpane  
 中斷連結從索引標籤式窗格的窗格。  
  
```  
virtual BOOL DetachPane(
    CWnd* pBar,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pBar`  
 若要卸離 窗格的指標。  
  
 [輸入] `bHide`  
 布林值參數，指定卸離之後，架構是否隱藏窗格。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果架構已成功中斷連結 窗格中。`FALSE`如果`pBar`是`NULL`或參考到不在索引標籤式窗格的窗格。  
  
### <a name="remarks"></a>備註  
 架構會盡可能浮動中斷連結的窗格。 如需詳細資訊，請參閱[CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)。  
  
##  <a name="enablesetcaptiontexttotabname"></a>  CBaseTabbedPane::EnableSetCaptionTextToTabName  
 啟用或停用索引標籤式窗格的 [作用中] 索引標籤上的標籤文字與同步處理標題文字的能力。  
  
```  
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bEnable`  
 `TRUE` 與使用中索引標籤標題; 同步處理的索引標籤式的窗格的標題否則， `FALSE`。  
  
##  <a name="filldefaulttabsorderarray"></a>  CBaseTabbedPane::FillDefaultTabsOrderArray  
 還原 [內部] 索引標籤順序設為預設狀態。  
  
```  
void FillDefaultTabsOrderArray();
```  
  
### <a name="remarks"></a>備註  
 架構會將 outlook 功能區還原為初始狀態時，會呼叫這個方法。  
  
##  <a name="findpanebyid"></a>  CBaseTabbedPane::FindPaneByID  
 傳回窗格之識別碼所識別的窗格  
  
```  
virtual CWnd* FindPaneByID(UINT uBarID);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `uBarID`  
 指定要尋找窗格的識別碼。  
  
### <a name="return-value"></a>傳回值  
 指向的窗格中，如果找不到它。否則， `NULL`。  
  
### <a name="remarks"></a>備註  
 這個方法會比較在窗格中的所有索引標籤，並傳回具有所指定的識別碼`uBarID`參數。  
  
##  <a name="findbarbytabnumber"></a>  CBaseTabbedPane::FindBarByTabNumber  
 傳回位於索引標籤的窗格。  
  
```  
virtual CWnd* FindBarByTabNumber(
    int nTabNum,  
    BOOL bGetWrappedBar = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nTabNum`  
 指定要擷取的索引標籤的以零為起始的索引。  
  
 [輸入] `bGetWrappedBar`  
 `TRUE` 要傳回而不是本身; 窗格 窗格的 基礎 （包裝） 視窗否則`FALSE`。 這只適用於衍生自窗格[CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)。  
  
### <a name="return-value"></a>傳回值  
 如果找到 [] 窗格中，則會傳回要搜尋的窗格中的有效指標;否則， `NULL`。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以擷取所指定的索引標籤中的窗格`nTabNum`參數。  
  
##  <a name="floattab"></a>  Cbasetabbedpane:: Floattab  
 讓窗格浮動，但僅限於窗格目前位於可卸離的索引標籤時。  
  
```  
virtual BOOL FloatTab(
    CWnd* pBar,  
    int nTabID,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in][out] `pBar`  
 Float 窗格指標。  
  
 [輸入] `nTabID`  
 指定 float 索引標籤的以零為起始的索引。  
  
 [輸入] `dockMethod`  
 指定要用來讓窗格浮動方法。 如需詳細資訊，請參閱＜備註＞一節。  
  
 [輸入] `bHide`  
 `TRUE` 若要隱藏窗格之前浮點數;否則， `FALSE`。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果窗格浮動;否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以浮動窗格目前位於可卸離索引標籤。  
  
 如果您想要以程式設計的方式卸離 窗格，指定`DM_SHOW`如`dockMethod`參數。 如果您想要浮動窗格，其中它浮動先前的相同位置中，指定`DM_DBL_CLICK`為`dockMethod`參數。  
  
##  <a name="getdefaulttabsorder"></a>  CBaseTabbedPane::GetDefaultTabsOrder  
 傳回在窗格中的索引標籤的預設順序。  
  
```  
const CArray<int,int>& GetDefaultTabsOrder();
```  
  
### <a name="return-value"></a>傳回值  
 A`CArray`物件，指定在窗格中的索引標籤的預設順序。  
  
### <a name="remarks"></a>備註  
 Outlook 功能區會重設為初始狀態時，架構會呼叫這個方法。  
  
##  <a name="getfirstvisibletab"></a>  CBaseTabbedPane::GetFirstVisibleTab  
 擷取第一個顯示索引標籤的指標。  
  
```  
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `iTabNum`  
 整數的參考。 這個方法會寫入第一個顯示索引標籤的以零為起始的索引至這個參數，則為-1 如果未顯示索引標籤上找到。  
  
### <a name="return-value"></a>傳回值  
 如果成功，第一個顯示索引標籤; 的指標否則， `NULL`。  
  
##  <a name="getminsize"></a>  CBaseTabbedPane::GetMinSize  
 擷取最小允許大小的窗格。  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `size`  
 A`CSize`填滿允許大小的最小的物件。  
  
### <a name="remarks"></a>備註  
 是否在作用中的最小的窗格大小一致的處理 ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize))，`size`填滿允許的作用中的索引標籤大小的最小。否則，`size`填滿的傳回值[CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize)。  
  
##  <a name="getpaneicon"></a>  CBaseTabbedPane::GetPaneIcon  
 擷取最小允許大小的窗格。  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `size`  
 A`CSize`填滿允許大小的最小的物件。  
  
### <a name="remarks"></a>備註  
 是否在作用中的最小的窗格大小一致的處理 ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize))，`size`填滿允許的作用中的索引標籤大小的最小。否則，`size`填滿的傳回值[CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize)。  
  
##  <a name="getpanelist"></a>  CBaseTabbedPane::GetPaneList  
 在索引標籤式窗格中，會傳回一份包含窗格。  
  
```  
virtual void GetPaneList(
    CObList& lst,  
    CRuntimeClass* pRTCFilter = NULL);
```  
  
### <a name="parameters"></a>參數  
 [輸出] `lst`  
 A`CObList`填入索引標籤式窗格中所包含的窗格。  
  
 [輸入] `pRTCFilter`  
 如果不是`NULL`，傳回的清單包含屬於指定的執行階段類別的窗格。  
  
##  <a name="gettabarea"></a>  CBaseTabbedPane::GetTabArea  
 傳回的頂端和底部的索引標籤區域的週框矩形。  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const = 0;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `rectTabAreaTop`  
 接收上方的索引標籤區域的螢幕座標。  
  
 [輸出] `rectTabAreaBottom`  
 接收較低的索引標籤區域的螢幕座標。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來判斷上限和下限 索引標籤區域的螢幕座標中的週框矩形。  
  
##  <a name="gettabsnum"></a>  CBaseTabbedPane::GetTabsNum  
 傳回在索引標籤 視窗中的索引標籤的計數。  
  
```  
virtual int GetTabsNum() const;  
```  
  
### <a name="return-value"></a>傳回值  
 索引標籤式窗格中的索引標籤數目。  
  
##  <a name="getunderlyingwindow"></a>  CBaseTabbedPane::GetUnderlyingWindow  
 取得基礎 （包裝） 索引標籤視窗。  
  
```  
virtual CMFCBaseTabCtrl* GetUnderlyingWindow();
```  
  
### <a name="return-value"></a>傳回值  
 基礎的索引標籤視窗的指標。  
  
##  <a name="getvisibletabsnum"></a>  CBaseTabbedPane::GetVisibleTabsNum  
 傳回可見索引標籤的計數。  
  
```  
virtual int GetVisibleTabsNum() const;  
```  
  
### <a name="return-value"></a>傳回值  
 可見索引標籤，將會大於或等於零的數字。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以判斷可見索引標籤的索引標籤式窗格數目。  
  
##  <a name="hasautohidemode"></a>  Cbasetabbedpane:: Hasautohidemode  
 決定索引標籤式窗格是否可切換為自動隱藏模式。  
  
```  
virtual BOOL HasAutoHideMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果窗格可以切換為自動隱藏模式。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 已停用自動隱藏模式，沒有 pin 碼 按鈕會顯示在索引標籤式的窗格的標題。  
  
##  <a name="ishidesingletab"></a>  CBaseTabbedPane::IsHideSingleTab  
 決定索引標籤式的窗格是否會取消隱藏如果只有一個索引標籤會顯示。  
  
```  
virtual BOOL IsHideSingleTab() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果只有一個可見的索引標籤; 時未顯示索引標籤視窗否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 如果未顯示 窗格，因為只有一個索引標籤已開啟，您可以呼叫這個方法來判斷索引標籤式的窗格是否正常運作。  
  
##  <a name="removepane"></a>  CBaseTabbedPane::RemovePane  
 從索引標籤式窗格中移除窗格。  
  
```  
virtual BOOL RemovePane(CWnd* pBar);
```  
  
### <a name="parameters"></a>參數  
 [in][out] `pBar`  
 若要從索引標籤式窗格移除窗格指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果成功移除窗格從索引標籤式窗格，和索引標籤式的窗格是否仍然有效。 `FALSE` 如果已移除最後一個窗格從索引標籤式窗格，而且即將終結索引標籤式的窗格。 如果傳回值是`FALSE`，任何不使用索引標籤式的窗格。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以移除所指定的窗格`pBar`參數從索引標籤式窗格。  
  
##  <a name="setautodestroy"></a>  CBaseTabbedPane::SetAutoDestroy  
 判斷是否會自動終結索引標籤式的控制列。  
  
```  
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bAutoDestroy`  
 `TRUE` 如果以動態方式建立索引標籤式的窗格，而且您不會控制其存留期。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 設定自動終結模式`TRUE`如果您以動態方式建立索引標籤式的窗格，而且您不會控制其存留期。 如果自動終結模式是`TRUE`，會自動終結索引標籤式的窗格，架構。  
  
##  <a name="showtab"></a>  CBaseTabbedPane::ShowTab  
 顯示或隱藏 索引標籤。  
  
```  
virtual BOOL ShowTab(
    CWnd* pBar,  
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pBar`  
 若要顯示或隱藏窗格指標。  
  
 [輸入] `bShow`  
 `TRUE` 若要顯示窗格。`FALSE`隱藏窗格。  
  
 [輸入] `bDelay`  
 `TRUE` 若要延遲的調整 索引標籤的版面配置。否則， `FALSE`。  
  
 [輸入] `bActivate`  
 `TRUE` 讓 [] 索引標籤作用中的索引標籤。否則， `FALSE`。  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果 [] 索引標籤已顯示或隱藏可順利啟動。，否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 當您呼叫這個方法時，一個窗格是顯示或隱藏，根據的值`bShow`參數。 如果您隱藏索引標籤，而且它是最後一個可見的索引標籤，在 [基礎] 視窗中，會隱藏索引標籤式的窗格。 如果有先前沒有索引標籤可見時，您就會顯示索引標籤，會顯示索引標籤式的窗格。  
  
##  <a name="recalclayout"></a>  CBaseTabbedPane::RecalcLayout  
 重新計算窗格的配置資訊。  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>備註  
 如果窗格浮動窗格，則這個方法會通知架構，以調整窗格的迷你框架的目前大小的大小。  
  
 如果窗格停駐，這個方法沒有任何作用。  
  
##  <a name="setautohidemode"></a>  CBaseTabbedPane::SetAutoHideMode  
 設定自動隱藏模式，可以中斷連結的索引標籤式窗格的窗格。  
  
```  
virtual CMFCAutoHideToolBar* SetAutoHideMode(
    BOOL bMode,  
    DWORD dwAlignment,  
    CMFCAutoHideToolBar* pCurrAutoHideBar = NULL,  
    BOOL bUseTimer = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bMode`  
 `TRUE` 若要啟用自動隱藏模式。`FALSE`啟用一般停駐的模式。  
  
 [輸入] `dwAlignment`  
 指定要建立 [自動隱藏] 窗格的對齊方式。 如需可能值的清單，請參閱[CPane::MoveByAlignment](../../mfc/reference/cpane-class.md#movebyalignment)。  
  
 [in][out] `pCurrAutoHideBar`  
 目前的自動隱藏工具列指標。 可以是`NULL`。  
  
 [輸入] `bUseTimer`  
 指定是否要使用的自動隱藏效果，當使用者切換窗格為 自動隱藏模式，或是立即隱藏窗格。  
  
### <a name="return-value"></a>傳回值  
 自動隱藏工具列切換自動隱藏模式時所建立的指標或`NULL`如果建立沒有工具列。  
  
### <a name="remarks"></a>備註  
 當使用者選擇 [固定] 按鈕，切換為自動隱藏模式或一般停駐模式的索引標籤式的窗格，架構會呼叫這個方法。  
  
 每個中斷連結的窗格，在索引標籤式窗格中設定自動隱藏模式。 非中斷連結的窗格會被忽略。 如需詳細資訊，請參閱[:: Enabletabdetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach)。  
  
 呼叫這個方法來以程式設計方式切換到 自動隱藏模式的索引標籤式的窗格。 必須停駐於主框架視窗窗格 ( [CDockablePane::GetDefaultPaneDivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider)必須傳回的有效指標[CPaneDivider](../../mfc/reference/cpanedivider-class.md))。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)
