---
title: "CBaseTabbedPane 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
- CBaseTabbedPane class
ms.assetid: f22c0080-5b29-4a0a-8f74-8f0a4cd2dbcf
caps.latest.revision: 26
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: b72804dd8b2ca2253caff4cebf5b0631ae6040c6
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cbasetabbedpane-class"></a>CBaseTabbedPane 類別
擴充功能的[CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)支援建立索引標籤式視窗。  
  
## <a name="syntax"></a>語法  
  
```  
class CBaseTabbedPane : public CDockablePane  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|`CBaseTabbedPane::CBaseTabbedPane`|預設建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CBaseTabbedPane::AddTab](#addtab)|將新的索引標籤加入至索引標籤式窗格。|  
|[CBaseTabbedPane::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|指定是否可以終結空白的索引標籤式的窗格。|  
|[CBaseTabbedPane::ApplyRestoredTabInfo](#applyrestoredtabinfo)|適用於載入登錄中，從索引標籤式窗格的索引標籤設定。|  
|[CBaseTabbedPane::CanFloat](#canfloat)|判斷是否可以浮動窗格。 (覆寫[CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)。)|  
|[CBaseTabbedPane::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|決定索引標籤式窗格的標題是否應該為作用中的索引標籤會顯示相同的文字。|  
|[CBaseTabbedPane::ConvertToTabbedDocument](#converttotabbeddocument)|(覆寫[CDockablePane::ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument)。)|  
|[CBaseTabbedPane::DetachPane](#detachpane)|MDI 索引標籤式文件會將一或多個可停駐窗格。|  
|[CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)|啟用或停用索引標籤式窗格能力同步處理與作用中的索引標籤上的標籤文字的標題文字。|  
|[CBaseTabbedPane::FillDefaultTabsOrderArray](#filldefaulttabsorderarray)|還原 [內部] 索引標籤順序設為預設狀態。|  
|[CBaseTabbedPane::FindBarByTabNumber](#findbarbytabnumber)|傳回 [] 索引標籤由以零為起始的索引時，位於索引標籤的窗格。|  
|||  
|[CBaseTabbedPane::FindPaneByID](#findpanebyid)|傳回窗格識別碼所識別的窗格|  
|[CBaseTabbedPane::FloatTab](#floattab)|讓窗格浮動，但僅限於窗格目前位於可卸離的索引標籤時。|  
|[CBaseTabbedPane::GetDefaultTabsOrder](#getdefaulttabsorder)|傳回在窗格中的索引標籤的預設順序。|  
|[CBaseTabbedPane::GetFirstVisibleTab](#getfirstvisibletab)|擷取第一個顯示索引標籤的指標。|  
|[CBaseTabbedPane::GetMinSize](#getminsize)|擷取的最小允許大小的窗格。 (覆寫[CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize)。)|  
|[CBaseTabbedPane::GetPaneIcon](#getpaneicon)|傳回窗格圖示的控制代碼。 (覆寫[CBasePane::GetPaneIcon](../../mfc/reference/cbasepane-class.md#getpaneicon)。)|  
|[CBaseTabbedPane::GetPaneList](#getpanelist)|傳回包含窗格的清單中的索引標籤式窗格。|  
|[CBaseTabbedPane::GetTabArea](#gettabarea)|傳回的週框矩形的頂端和底端的索引標籤區域。|  
|[CBaseTabbedPane::GetTabsNum](#gettabsnum)|傳回索引標籤 視窗中。|  
|[CBaseTabbedPane::GetUnderlyingWindow](#getunderlyingwindow)|取得基礎 （包裝） 索引標籤視窗。|  
|[CBaseTabbedPane::GetVisibleTabsNum](#getvisibletabsnum)|傳回顯示索引標籤的計數。|  
|[CBaseTabbedPane::HasAutoHideMode](#hasautohidemode)|判斷是否可以將索引標籤式的窗格切換到 自動隱藏模式。|  
|[CBaseTabbedPane::IsHideSingleTab](#ishidesingletab)|決定是否隱藏如果只有一個索引標籤會顯示索引標籤式的窗格。|  
|`CBaseTabbedPane::LoadSiblingPaneIDs`|在序列化期間，在內部使用。|  
|[CBaseTabbedPane::RecalcLayout](#recalclayout)|重新計算配置資訊窗格。 (覆寫[CPane::RecalcLayout](../../mfc/reference/cpane-class.md#recalclayout)。)|  
|[CBaseTabbedPane::RemovePane](#removepane)|移除索引標籤式窗格的窗格。|  
|`CBaseTabbedPane::SaveSiblingBarIDs`|在序列化期間，在內部使用。|  
|`CBaseTabbedPane::Serialize`|(覆寫[CDockablePane::Serialize](http://msdn.microsoft.com/en-us/09787e59-e446-4e76-894b-206d303dcfd6)。)|  
|`CBaseTabbedPane::SerializeTabWindow`|在序列化期間，在內部使用。|  
|[CBaseTabbedPane::SetAutoDestroy](#setautodestroy)|判斷是否會自動終結索引標籤式的控制列。|  
|[CBaseTabbedPane::SetAutoHideMode](#setautohidemode)|切換停駐窗格之間顯示和 自動隱藏模式。 (覆寫[CDockablePane::SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode)。)|  
|[CBaseTabbedPane::ShowTab](#showtab)|顯示或隱藏 索引標籤。|  
  
## <a name="remarks"></a>備註  
 這個類別是抽象類別，而且無法具現化。 它會實作通用於所有類型的索引標籤式窗格的服務。  
  
 目前，此程式庫包含兩個衍生的索引標籤式的窗格類別︰ [CTabbedPane 類別](../../mfc/reference/ctabbedpane-class.md)和[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)。  
  
 A`CBaseTabbedPane`物件包裝指標[CMFCBaseTabCtrl 類別](../../mfc/reference/cmfcbasetabctrl-class.md)物件。 [CMFCBaseTabCtrl 類別](../../mfc/reference/cmfcbasetabctrl-class.md)便成為索引標籤式窗格中的子視窗。  
  
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
 **標頭︰** afxBaseTabbedPane.h  
  
##  <a name="addtab"></a>CBaseTabbedPane::AddTab  
 將新的索引標籤加入至索引標籤式窗格。  
  
```  
virtual BOOL AddTab(
    CWnd* pNewBar,  
    BOOL bVisible = TRUE,  
    BOOL bSetActive = TRUE,  
    BOOL bDetachable = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in][out]`pNewBar`  
 窗格來新增指標。 之後呼叫這個方法，這個指標可能會變成無效。 如需詳細資訊，請參閱＜備註＞一節。  
  
 [in] `bVisible`  
 `TRUE`若要顯示 [] 索引標籤。否則， `FALSE`。  
  
 [in] `bSetActive`  
 `TRUE`讓 [] 索引標籤作用中的索引標籤。否則， `FALSE`。  
  
 [in] `bDetachable`  
 `TRUE`讓 [] 索引標籤可分開。否則， `FALSE`。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果窗格已成功加入成為的索引標籤，並不會終結程序中。 `FALSE`如果要加入的窗格是型別的物件`CBaseTabbedPane`。 如需詳細資訊，請參閱＜備註＞一節。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來加入成為索引標籤式窗格上的新索引標籤的窗格。 如果`pNewBar`類型的物件會指向`CBaseTabbedPane`，其所有的索引標籤都會複製到索引標籤式窗格，然後`pNewBar`損毀。 因此，`pNewBar`會變成無效的指標，而不應使用。  
  
##  <a name="allowdestroyemptytabbedpane"></a>CBaseTabbedPane::AllowDestroyEmptyTabbedPane  
 指定是否可以終結空白的索引標籤式的窗格。  
  
```  
virtual BOOL AllowDestroyEmptyTabbedPane() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果可以終結空白的索引標籤式的窗格。否則， `FALSE`。 預設實作一定會傳回`TRUE`。  
  
### <a name="remarks"></a>備註  
 如果不允許空白的索引標籤式的窗格會終結，架構會改為隱藏的窗格。  
  
##  <a name="applyrestoredtabinfo"></a>CBaseTabbedPane::ApplyRestoredTabInfo  
 從登錄載入設定 索引標籤，並套用至索引標籤式窗格。  
  
```  
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bUseTabIndexes`  
 由架構在內部使用這個參數。  
  
### <a name="remarks"></a>備註  
 當您重新載入專案從登錄的銜接狀態資訊時，架構會呼叫這個方法。 方法會取得定位順序和索引標籤式窗格的索引標籤名稱的資訊。  
  
##  <a name="canfloat"></a>CBaseTabbedPane::CanFloat  
 指定是否可以浮動索引標籤式的窗格。  
  
```  
virtual BOOL CanFloat() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果可以浮動窗格。，否則， `FALSE`。  
  
##  <a name="cansetcaptiontexttotabname"></a>CBaseTabbedPane::CanSetCaptionTextToTabName  
 決定索引標籤式窗格的標題是否應該為作用中的索引標籤會顯示相同的文字。  
  
```  
virtual BOOL CanSetCaptionTextToTabName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果索引標籤式窗格的標題文字設為 [作用中] 索引標籤; 文字否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 方法用來決定文字顯示在索引標籤式的窗格標題重複的項目上使用中 索引標籤的標籤。 您可以啟用或停用此功能，藉由呼叫[CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)。  
  
##  <a name="converttotabbeddocument"></a>CBaseTabbedPane::ConvertToTabbedDocument  
 MDI 索引標籤式文件會將一或多個可停駐窗格。  
  
```  
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bActiveTabOnly`  
 當您轉換索引標籤式的窗格時，指定`TRUE`轉換作用中索引標籤。 指定`FALSE`轉換在窗格中的所有索引標籤。  
  
##  <a name="detachpane"></a>CBaseTabbedPane::DetachPane  
 中斷連結的索引標籤式窗格的窗格。  
  
```  
virtual BOOL DetachPane(
    CWnd* pBar,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `pBar`  
 若要卸離 窗格的指標。  
  
 [in] `bHide`  
 布林值參數，指定卸離之後，架構是否隱藏的窗格。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果架構順利卸離 窗格中。`FALSE`如果`pBar`是`NULL`或參考到不在索引標籤式窗格的窗格。  
  
### <a name="remarks"></a>備註  
 架構會盡可能浮動卸離 窗格。 如需詳細資訊，請參閱[CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)。  
  
##  <a name="enablesetcaptiontexttotabname"></a>CBaseTabbedPane::EnableSetCaptionTextToTabName  
 啟用或停用索引標籤式窗格能力同步處理與作用中的索引標籤上的標籤文字的標題文字。  
  
```  
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```  
  
### <a name="parameters"></a>參數  
 [in] `bEnable`  
 `TRUE`作用中索引標籤的標題; 與同步處理的索引標籤式的窗格標題否則， `FALSE`。  
  
##  <a name="filldefaulttabsorderarray"></a>CBaseTabbedPane::FillDefaultTabsOrderArray  
 還原 [內部] 索引標籤順序設為預設狀態。  
  
```  
void FillDefaultTabsOrderArray();
```  
  
### <a name="remarks"></a>備註  
 架構會將 outlook 功能區還原為初始狀態時，會呼叫這個方法。  
  
##  <a name="findpanebyid"></a>CBaseTabbedPane::FindPaneByID  
 傳回一個窗格窗格識別碼識別。  
  
```  
virtual CWnd* FindPaneByID(UINT uBarID);
```  
  
### <a name="parameters"></a>參數  
 [in] `uBarID`  
 指定要尋找窗格的識別碼。  
  
### <a name="return-value"></a>傳回值  
 變數的指標，窗格中，如果找到了。否則， `NULL`。  
  
### <a name="remarks"></a>備註  
 這個方法會比較在窗格中的所有索引標籤，並傳回具有所指定的識別碼`uBarID`參數。  
  
##  <a name="findbarbytabnumber"></a>CBaseTabbedPane::FindBarByTabNumber  
 傳回位於索引標籤的窗格。  
  
```  
virtual CWnd* FindBarByTabNumber(
    int nTabNum,  
    BOOL bGetWrappedBar = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `nTabNum`  
 指定要擷取之索引標籤以零為起始的索引。  
  
 [in] `bGetWrappedBar`  
 `TRUE`傳回而不是本身; 窗格 窗格的基礎 （包裝） 視窗否則`FALSE`。 這只適用於衍生自窗格[CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)。  
  
### <a name="return-value"></a>傳回值  
 如果找到窗格中，則會傳回要搜尋的窗格中的有效指標;否則， `NULL`。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來擷取位於指定索引標籤的窗格`nTabNum`參數。  
  
##  <a name="floattab"></a>CBaseTabbedPane::FloatTab  
 讓窗格浮動，但僅限於窗格目前位於可卸離的索引標籤時。  
  
```  
virtual BOOL FloatTab(
    CWnd* pBar,  
    int nTabID,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in][out]`pBar`  
 Float 窗格指標。  
  
 [in] `nTabID`  
 指定為 float 索引標籤的以零為起始的索引。  
  
 [in] `dockMethod`  
 指定要用來進行的窗格中的浮點數的方法。 如需詳細資訊，請參閱＜備註＞一節。  
  
 [in] `bHide`  
 `TRUE`若要隱藏窗格之前浮點數。否則， `FALSE`。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果浮動窗格。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以浮動窗格目前位於可拆式索引標籤。  
  
 如果您想要以程式設計的方式卸離 窗格中，指定`DM_SHOW`的`dockMethod`參數。 如果您想要浮動在相同的位置它其中先前浮動窗格中，指定`DM_DBL_CLICK`為`dockMethod`參數。  
  
##  <a name="getdefaulttabsorder"></a>CBaseTabbedPane::GetDefaultTabsOrder  
 傳回在窗格中的索引標籤的預設順序。  
  
```  
const CArray<int,int>& GetDefaultTabsOrder();
```  
  
### <a name="return-value"></a>傳回值  
 A`CArray`物件，指定在窗格中的索引標籤的預設順序。  
  
### <a name="remarks"></a>備註  
 Outlook 功能區重設為初始狀態時，架構會呼叫這個方法。  
  
##  <a name="getfirstvisibletab"></a>CBaseTabbedPane::GetFirstVisibleTab  
 擷取第一個顯示索引標籤的指標。  
  
```  
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```  
  
### <a name="parameters"></a>參數  
 [in] `iTabNum`  
 整數的參考。 此方法將第一個顯示索引標籤的以零起始的索引寫入這個參數，則為-1 如果沒有顯示索引標籤上找到。  
  
### <a name="return-value"></a>傳回值  
 如果成功，指向第一個顯示索引標籤。否則， `NULL`。  
  
##  <a name="getminsize"></a>CBaseTabbedPane::GetMinSize  
 擷取的最小允許大小的窗格。  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `size`  
 A`CSize`填滿允許大小的最小的物件。  
  
### <a name="remarks"></a>備註  
 如果作用中的最小窗格大小一致的處理 ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize))，`size`填滿允許的作用中的索引標籤的大小最小值。 否則，`size`填滿的傳回值[CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize)。  
  
##  <a name="getpaneicon"></a>CBaseTabbedPane::GetPaneIcon  
 擷取的最小允許大小的窗格。  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `size`  
 A`CSize`填滿允許大小的最小的物件。  
  
### <a name="remarks"></a>備註  
 如果作用中的最小窗格大小一致的處理 ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize))，`size`填滿允許的作用中的索引標籤的大小最小值。 否則，`size`填滿的傳回值[CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize)。  
  
##  <a name="getpanelist"></a>CBaseTabbedPane::GetPaneList  
 傳回包含窗格的清單中的索引標籤式窗格。  
  
```  
virtual void GetPaneList(
    CObList& lst,  
    CRuntimeClass* pRTCFilter = NULL);
```  
  
### <a name="parameters"></a>參數  
 [輸出] `lst`  
 A`CObList`窗格包含在索引標籤式窗格中會填入。  
  
 [in] `pRTCFilter`  
 如果不是`NULL`，傳回的清單包含屬於指定的執行階段類別的窗格。  
  
##  <a name="gettabarea"></a>CBaseTabbedPane::GetTabArea  
 傳回的週框矩形的頂端和底端的索引標籤區域。  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const = 0;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `rectTabAreaTop`  
 接收的上方的索引標籤區域的螢幕座標。  
  
 [輸出] `rectTabAreaBottom`  
 接收的較低的索引標籤區域的螢幕座標。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來決定的上限和下限 索引標籤區域的螢幕座標中的週框矩形。  
  
##  <a name="gettabsnum"></a>CBaseTabbedPane::GetTabsNum  
 傳回索引標籤 視窗中。  
  
```  
virtual int GetTabsNum() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在索引標籤式窗格中的標籤數目。  
  
##  <a name="getunderlyingwindow"></a>CBaseTabbedPane::GetUnderlyingWindow  
 取得基礎 （包裝） 索引標籤視窗。  
  
```  
virtual CMFCBaseTabCtrl* GetUnderlyingWindow();
```  
  
### <a name="return-value"></a>傳回值  
 基礎的索引標籤視窗的指標。  
  
##  <a name="getvisibletabsnum"></a>CBaseTabbedPane::GetVisibleTabsNum  
 傳回顯示索引標籤的計數。  
  
```  
virtual int GetVisibleTabsNum() const;  
```  
  
### <a name="return-value"></a>傳回值  
 顯示索引標籤，將會大於或等於零的數字。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法來判斷索引標籤式窗格中顯示的標籤數目。  
  
##  <a name="hasautohidemode"></a>CBaseTabbedPane::HasAutoHideMode  
 決定索引標籤式窗格是否可切換為自動隱藏模式。  
  
```  
virtual BOOL HasAutoHideMode() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果窗格可以切換為 自動隱藏模式;否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 如果停用自動隱藏模式時，沒有 pin 碼 按鈕會顯示在索引標籤式的窗格的標題。  
  
##  <a name="ishidesingletab"></a>CBaseTabbedPane::IsHideSingleTab  
 決定是否隱藏如果只有一個索引標籤會顯示索引標籤式的窗格。  
  
```  
virtual BOOL IsHideSingleTab() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果只有一個可見的索引標籤; 時，不會顯示 索引標籤視窗否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 如果未顯示窗格中，因為只有一個索引標籤已開啟，您可以呼叫這個方法來判斷索引標籤式的窗格是否正常運作。  
  
##  <a name="removepane"></a>CBaseTabbedPane::RemovePane  
 移除索引標籤式窗格的窗格。  
  
```  
virtual BOOL RemovePane(CWnd* pBar);
```  
  
### <a name="parameters"></a>參數  
 [in][out]`pBar`  
 若要移除的索引標籤式窗格的窗格指標。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果成功移除窗格從索引標籤式窗格，和索引標籤式的窗格是否仍然有效。 `FALSE`如果已移除的最後一個窗格從索引標籤式的窗格和索引標籤式的窗格，是即將終結。 如果傳回值是`FALSE`，就比較不使用索引標籤式的窗格。  
  
### <a name="remarks"></a>備註  
 呼叫此方法以移除所指定的窗格`pBar`索引標籤式窗格中的參數。  
  
##  <a name="setautodestroy"></a>CBaseTabbedPane::SetAutoDestroy  
 判斷是否會自動終結索引標籤式的控制列。  
  
```  
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bAutoDestroy`  
 `TRUE`如果以動態方式建立索引標籤式的窗格，而且您不想要控制其存留期。否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 設定自動終結模式`TRUE`如果動態建立索引標籤式的窗格，而且您不想要控制其存留期。 如果自動終結模式是`TRUE`，索引標籤式的窗格將會自動終結架構。  
  
##  <a name="showtab"></a>CBaseTabbedPane::ShowTab  
 顯示或隱藏 索引標籤。  
  
```  
virtual BOOL ShowTab(
    CWnd* pBar,  
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>參數  
 [in] `pBar`  
 若要顯示或隱藏窗格指標。  
  
 [in] `bShow`  
 `TRUE`若要顯示窗格。`FALSE`隱藏窗格。  
  
 [in] `bDelay`  
 `TRUE`若要延遲的調整 索引標籤的版面配置。否則， `FALSE`。  
  
 [in] `bActivate`  
 `TRUE`讓 [] 索引標籤作用中的索引標籤。否則， `FALSE`。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果 [] 索引標籤已顯示或隱藏可順利啟動。，否則， `FALSE`。  
  
### <a name="remarks"></a>備註  
 當您呼叫這個方法時，窗格可以顯示或隱藏，根據的值`bShow`參數。 如果您隱藏 索引標籤，而且它是最後一個可見的索引標籤，在 基礎 視窗中，會隱藏索引標籤式的窗格。 如果有先前未索引標籤顯示時，您就會顯示索引標籤，會顯示索引標籤式的窗格。  
  
##  <a name="recalclayout"></a>CBaseTabbedPane::RecalcLayout  
 重新計算配置資訊窗格。  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>備註  
 如果浮動窗格，這個方法會通知架構，來調整窗格的迷你框架目前大小的大小。  
  
 如果停駐窗格中，這個方法沒有作用。  
  
##  <a name="setautohidemode"></a>CBaseTabbedPane::SetAutoHideMode  
 在索引標籤式窗格的分離式窗格的設定自動隱藏模式。  
  
```  
virtual CMFCAutoHideToolBar* SetAutoHideMode(
    BOOL bMode,  
    DWORD dwAlignment,  
    CMFCAutoHideToolBar* pCurrAutoHideBar = NULL,  
    BOOL bUseTimer = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bMode`  
 `TRUE`若要啟用自動隱藏模式;`FALSE`來啟用規則的停駐模式。  
  
 [in] `dwAlignment`  
 指定要建立 [自動隱藏] 窗格的對齊方式。 如需可能的值，請參閱[CPane::MoveByAlignment](../../mfc/reference/cpane-class.md#movebyalignment)。  
  
 [in][out]`pCurrAutoHideBar`  
 目前的自動隱藏工具列指標。 可以是`NULL`。  
  
 [in] `bUseTimer`  
 指定是否要在使用者切換窗格為 自動隱藏模式時，使用自動隱藏效果，或是立即隱藏窗格。  
  
### <a name="return-value"></a>傳回值  
 自動隱藏工具列切換為 自動隱藏模式時所建立的指標或`NULL`如果不建立任何工具列。  
  
### <a name="remarks"></a>備註  
 在使用者選擇自動隱藏模式或標準停駐模式切換索引標籤式的窗格的 [固定] 按鈕時，架構會呼叫這個方法。  
  
 自動隱藏模式設定為每個索引標籤式窗格中的分離式窗格。 非可分開的窗格會被忽略。 如需詳細資訊，請參閱[CMFCBaseTabCtrl::EnableTabDetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach)。  
  
 呼叫這個方法來以程式設計方式切換到 自動隱藏模式的索引標籤式的窗格。 窗格必須可停駐於主框架視窗 ( [CDockablePane::GetDefaultPaneDivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider)必須傳回有效指標[CPaneDivider](../../mfc/reference/cpanedivider-class.md))。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)

