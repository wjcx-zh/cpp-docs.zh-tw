---
title: CContextMenuManager 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager::CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager::AddMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuById
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuByName
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuNames
- AFXCONTEXTMENUMANAGER/CContextMenuManager::LoadState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::ResetState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::SaveState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::SetDontCloseActiveMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::ShowPopupMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::TrackPopupMenu
dev_langs:
- C++
helpviewer_keywords:
- CContextMenuManager [MFC], CContextMenuManager
- CContextMenuManager [MFC], AddMenu
- CContextMenuManager [MFC], GetMenuById
- CContextMenuManager [MFC], GetMenuByName
- CContextMenuManager [MFC], GetMenuNames
- CContextMenuManager [MFC], LoadState
- CContextMenuManager [MFC], ResetState
- CContextMenuManager [MFC], SaveState
- CContextMenuManager [MFC], SetDontCloseActiveMenu
- CContextMenuManager [MFC], ShowPopupMenu
- CContextMenuManager [MFC], TrackPopupMenu
ms.assetid: 1de20640-243c-47e1-85de-1baa4153bc83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9407c98183fa923a58ca2939e8c534cd56dc8ef7
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954617"
---
# <a name="ccontextmenumanager-class"></a>CContextMenuManager 類別
`CContextMenuManager`物件管理捷徑功能表，也稱為內容功能表。  
  
## <a name="syntax"></a>語法  
  
```  
class CContextMenuManager : public CObject  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CContextMenuManager::CContextMenuManager](#ccontextmenumanager)|建構 `CContextMenuManager` 物件。|  
|`CContextMenuManager::~CContextMenuManager`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CContextMenuManager::AddMenu](#addmenu)|加入新的快顯功能表。|  
|[CContextMenuManager::GetMenuById](#getmenubyid)|傳回與提供的資源識別碼相關聯的功能表的控制代碼|  
|[CContextMenuManager::GetMenuByName](#getmenubyname)|傳回符合所提供的功能表名稱的功能表的控制代碼。|  
|[CContextMenuManager::GetMenuNames](#getmenunames)|傳回的功能表名稱的清單。|  
|[CContextMenuManager::LoadState](#loadstate)|載入儲存在 Windows 登錄中的快顯功能表。|  
|[CContextMenuManager::ResetState](#resetstate)|清除的快顯功能表，從內容功能表管理員。|  
|[CContextMenuManager::SaveState](#savestate)|將 Windows 登錄中的快顯功能表。|  
|[CContextMenuManager::SetDontCloseActiveMenu](#setdontcloseactivemenu)|控制項是否`CContextMenuManager`時它會顯示新的快顯功能表關閉使用中的快顯功能表。|  
|[CContextMenuManager::ShowPopupMenu](#showpopupmenu)|顯示指定的快顯功能表。|  
|[CContextMenuManager::TrackPopupMenu](#trackpopupmenu)|顯示指定的快顯功能表。 傳回選取的功能表命令的索引。|  
  
## <a name="remarks"></a>備註  
 `CContextMenuManager` 管理捷徑功能表，並確定它們有一致的外觀。  
  
 您不應建立`CContextMenuManager`手動物件。 您的應用程式的架構建立`CContextMenuManager`物件。 不過，您應該呼叫[CWinAppEx::InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager)初始化您的應用程式的時間。 初始化 「 內容管理員 」 之後, 使用的方法[CWinAppEx::GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager)取得您的應用程式的內容管理員的指標。  
  
 您可以在執行階段建立快顯功能表，藉由呼叫`AddMenu`。 如果您想要顯示的功能表第一個接收使用者輸入的情況下，呼叫`ShowPopupMenu`。 `TrackPopupMenu` 您想要建立功能表，並等候使用者輸入時使用。 `TrackPopupMenu` 如果使用者已結束，而不選取任何項目會傳回選取的命令則為 0 索引。  
  
 `CContextMenuManager`也可以儲存及載入至 Windows 登錄其狀態。  
  
## <a name="example"></a>範例  
 下列範例示範如何加入功能表`CContextMenuManager`物件，以及如何不關閉使用中的快顯功能表時`CContextMenuManager`物件就會顯示新的快顯功能表。 此程式碼片段是部分[自訂網頁範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_CustomPages#4](../../mfc/reference/codesnippet/cpp/ccontextmenumanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CContextMenuManager`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcontextmenumanager.h  
  
##  <a name="addmenu"></a>  CContextMenuManager::AddMenu  
 加入新的快顯功能表來[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)。  
  
```  
BOOL AddMenu(
    UINT uiMenuNameResId,  
    UINT uiMenuResId);

 
BOOL AddMenu(
    LPCTSTR lpszName,  
    UINT uiMenuResId);
```  
  
### <a name="parameters"></a>參數  
 [in]*uiMenuNameResId*  
 包含新的功能表名稱的字串資源識別碼。  
  
 [in]*uiMenuResId*  
 功能表上的資源 id。  
  
 [in]*lpszName*  
 包含新的功能表名稱的字串。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果該方法成功。0，表示方法失敗。  
  
### <a name="remarks"></a>備註  
 如果這個方法會失敗*uiMenuResId*無效，或者如果具有相同名稱的另一個功能表已存在於中`CContextMenuManager`。  
  
##  <a name="ccontextmenumanager"></a>  CContextMenuManager::CContextMenuManager  
 建構[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)物件。  
  
```  
CContextMenuManager();
```  
  
### <a name="remarks"></a>備註  
 在大部分情況下，您不應建立`CContextMenuManager`手動。 您的應用程式的架構建立`CContextMenuManager`物件。 您應該呼叫[CWinAppEx::InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager)您的應用程式初始化期間。 若要取得內容管理員的指標，呼叫[CWinAppEx::GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager)。  
  
##  <a name="getmenubyid"></a>  CContextMenuManager::GetMenuById  
 傳回與指定的資源識別碼相關聯的功能表的控制代碼  
  
```  
HMENU GetMenuById(UINT nMenuResId) const;  
```  
  
### <a name="parameters"></a>參數  
 [in]*nMenuResId*  
 功能表資源識別碼。  
  
### <a name="return-value"></a>傳回值  
 相關的功能表的控制代碼或`NULL`找不到功能表時。  
  
##  <a name="getmenubyname"></a>  CContextMenuManager::GetMenuByName  
 傳回特定的功能表的控制代碼。  
  
```  
HMENU GetMenuByName(
    LPCTSTR lpszName,  
    UINT* puiOrigResID = NULL) const;  
```  
  
### <a name="parameters"></a>參數  
 [in]*lpszName*  
 包含要擷取的功能表名稱的字串。  
  
 [out]*puiOrigResID*  
 `UINT` 的指標。 這個參數會包含指定的功能表中，資源識別碼，如果找到。  
  
### <a name="return-value"></a>傳回值  
 所指定的名稱相符的功能表的控制代碼*lpszName*。 `NULL` 如果沒有呼叫功能表*lpszName*。  
  
### <a name="remarks"></a>備註  
 如果此方法找到符合的功能表*lpszName*，`GetMenuByName`參數中儲存功能表資源 ID *puiOrigResID*。  
  
##  <a name="getmenunames"></a>  CContextMenuManager::GetMenuNames  
 傳回的功能表名稱加入至清單[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)。  
  
```  
void GetMenuNames(CStringList& listOfNames) const;  
```  
  
### <a name="parameters"></a>參數  
 [out]*listOfNames*  
 若要參考[CStringList](../../mfc/reference/cstringlist-class.md)參數。 這個方法會寫入此參數中的功能表名稱的清單。  
  
##  <a name="loadstate"></a>  CContextMenuManager::LoadState  
 載入與相關聯的資訊[CContextMenuManager 類別](../../mfc/reference/ccontextmenumanager-class.md)從 Windows 登錄。  
  
```  
virtual BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in]*lpszProfileName*  
 字串，包含相對路徑的登錄機碼。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果方法成功。否則便是 0。  
  
### <a name="remarks"></a>備註  
 *LpszProfileName*參數不是絕對路徑的登錄項目。 它是相對的路徑加入至您的應用程式的預設登錄機碼的結尾。 若要取得或設定預設的登錄機碼，使用方法[CWinAppEx::GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase)和[CWinAppEx::SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase)分別。  
  
 使用方法[CContextMenuManager::SaveState](#savestate)登錄中儲存的快顯功能表。  
  
##  <a name="resetstate"></a>  CContextMenuManager::ResetState  
 清除所有項目相關聯的捷徑功能表[CContextMenuManager 類別](../../mfc/reference/ccontextmenumanager-class.md)。  
  
```  
virtual BOOL ResetState();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果方法成功。`FALSE`如果發生失敗。  
  
### <a name="remarks"></a>備註  
 這個方法會清除快顯功能表，並將其從移除`CContextMenuManager`。  
  
##  <a name="savestate"></a>  CContextMenuManager::SaveState  
 將相關聯的資訊儲存[CContextMenuManager 類別](../../mfc/reference/ccontextmenumanager-class.md)至 Windows 登錄。  
  
```  
virtual BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in]*lpszProfileName*  
 字串，包含相對路徑的登錄機碼。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果方法成功。否則便是 0。  
  
### <a name="remarks"></a>備註  
 *LpszProfileName*參數不是絕對路徑的登錄項目。 它是相對的路徑加入至您的應用程式的預設登錄機碼的結尾。 若要取得或設定預設的登錄機碼，使用方法[CWinAppEx::GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase)和[CWinAppEx::SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase)分別。  
  
 使用方法[CContextMenuManager::LoadState](#loadstate)從登錄載入的快顯功能表。  
  
##  <a name="setdontcloseactivemenu"></a>  CContextMenuManager::SetDontCloseActiveMenu  
 控制項是否[CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)時它會顯示新的快顯功能表關閉使用中的快顯功能表。  
  
```  
void SetDontCloseActiveMenu (BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in]*bSet*  
 布林值參數可控制是否要關閉使用中的快顯功能表。 值為`TRUE`指出未關閉使用中的快顯功能表。 `FALSE` 表示已關閉使用中的快顯功能表。  
  
### <a name="remarks"></a>備註  
 根據預設，`CContextMenuManager`關閉使用中的快顯功能表。  
  
##  <a name="showpopupmenu"></a>  CContextMenuManager::ShowPopupMenu  
 顯示指定的快顯功能表。  
  
```  
virtual BOOL ShowPopupMenu(
    UINT uiMenuResId,  
    int x,  
    int y,  
    CWnd* pWndOwner,  
    BOOL bOwnMessage = FALSE,  
    BOOL bRightAlign = FALSE);

 
virtual CMFCPopupMenu* ShowPopupMenu(
    HMENU hmenuPopup,  
    int x,  
    int y,  
    CWnd* pWndOwner,  
    BOOL bOwnMessage = FALSE,  
    BOOL bAutoDestroy = TRUE,  
    BOOL bRightAlign = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in]*uiMenuResId*  
 這個方法會顯示的功能表資源識別碼。  
  
 [in]*x*  
 在水平位移的用戶端座標中的捷徑功能表時。  
  
 [in]*y*  
 垂直位移用戶端座標中的捷徑功能表  
  
 [in]*pWndOwner*  
 快顯功能表的父視窗指標。  
  
 [in]*bOwnMessage*  
 表示訊息會路由傳送的布林參數。 如果*bOwnMessage*是`FALSE`，標準 MFC 路由可用於。 否則， *pWndOwner*接收訊息。  
  
 [in]*hmenuPopup*  
 這個方法會顯示功能表的控制代碼。  
  
 [in]*bAutoDestroy*  
 布林值參數，指出是否會自動終結功能表。  
  
 [in]*bRightAlign*  
 布林值參數，指出功能表項目對齊的方式。 如果*bRightAlign*是`TRUE`，是由右至左讀取順序為靠右對齊。  
  
### <a name="return-value"></a>傳回值  
 第一個方法多載會傳回非零，如果該方法成功; 顯示的功能表否則便是 0。 第二個方法多載將指標傳回至[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)如果正確，否則為要顯示的捷徑功能表`NULL`。  
  
### <a name="remarks"></a>備註  
 這個方法類似方法[CContextMenuManager::TrackPopupMenu](#trackpopupmenu)在於這兩種方法顯示的捷徑功能表。 不過，`TrackPopupMenu`傳回選取的功能表命令的索引。  
  
 如果參數*bAutoDestroy*是`FALSE`，您必須以手動方式呼叫繼承`DestroyMenu`方法，以釋放記憶體資源。 預設實作`ShowPopupMenu`不使用參數*bAutoDestroy*。 軟體係以供日後使用，或自訂類別衍生自`CContextMenuManager`類別。  
  
##  <a name="trackpopupmenu"></a>  CContextMenuManager::TrackPopupMenu  
 顯示指定的捷徑功能表，並傳回所選的捷徑功能表命令的索引。  
  
```  
virtual UINT TrackPopupMenu(
    HMENU hmenuPopup,  
    int x,  
    int y,  
    CWnd* pWndOwner,  
    BOOL bRightAlign = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in]*hmenuPopup*  
 這個方法會顯示快顯功能表的控制代碼。  
  
 [in]*x*  
 在水平位移的用戶端座標中的捷徑功能表時。  
  
 [in]*y*  
 垂直位移的用戶端座標中的捷徑功能表。  
  
 [in]*pWndOwner*  
 快顯功能表的父視窗指標。  
  
 [in]*bRightAlign*  
 布林值參數，指出功能表項目對齊的方式。 如果*bRightAlign*是`TRUE`，是由右至左讀取順序為靠右對齊。 如果*bRightAlign*是`FALSE`，功能表是靠左對齊，以由左至右的讀取順序。  
  
### <a name="return-value"></a>傳回值  
 使用者選擇; 的命令功能表命令識別碼0，如果使用者關閉但不選取功能表命令的捷徑功能表。  
  
### <a name="remarks"></a>備註  
 此方法做為強制回應的呼叫，顯示快顯功能表。 在使用者關閉快顯功能表，或選取命令之前，應用程式將不會繼續為下列一行程式碼中。 您可以使用顯示快顯功能表的替代方法是[CContextMenuManager::ShowPopupMenu](#showpopupmenu)。 該方法不是強制回應的呼叫，而且不會傳回選取的命令識別碼。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)
