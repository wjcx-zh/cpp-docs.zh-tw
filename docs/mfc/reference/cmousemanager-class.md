---
title: "CMouseManager 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMouseManager
- AFXMOUSEMANAGER/CMouseManager
- AFXMOUSEMANAGER/CMouseManager::AddView
- AFXMOUSEMANAGER/CMouseManager::GetViewDblClickCommand
- AFXMOUSEMANAGER/CMouseManager::GetViewIconId
- AFXMOUSEMANAGER/CMouseManager::GetViewIdByName
- AFXMOUSEMANAGER/CMouseManager::GetViewNames
- AFXMOUSEMANAGER/CMouseManager::LoadState
- AFXMOUSEMANAGER/CMouseManager::SaveState
- AFXMOUSEMANAGER/CMouseManager::SetCommandForDblClk
dev_langs:
- C++
helpviewer_keywords:
- CMouseManager [MFC], AddView
- CMouseManager [MFC], GetViewDblClickCommand
- CMouseManager [MFC], GetViewIconId
- CMouseManager [MFC], GetViewIdByName
- CMouseManager [MFC], GetViewNames
- CMouseManager [MFC], LoadState
- CMouseManager [MFC], SaveState
- CMouseManager [MFC], SetCommandForDblClk
ms.assetid: a4d05017-4e44-4a40-8b57-4ece0de20481
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7d019bedd63e7b7700ec91309c9ccaa0a41bf1ed
ms.sourcegitcommit: 185e11ab93af56ffc650fe42fb5ccdf1683e3847
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2018
---
# <a name="cmousemanager-class"></a>CMouseManager 類別
可讓不同的命令與特定使用者[CView](../../mfc/reference/cview-class.md)當使用者在該檢視內部按兩下時物件。  
  
## <a name="syntax"></a>語法  
  
```  
class CMouseManager : public CObject  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMouseManager::AddView](#addview)|新增`CView`物件**自訂** 對話方塊。 **自訂** 對話方塊可讓使用者按兩下關聯的每個列出檢視的命令。|  
|[CMouseManager::GetViewDblClickCommand](#getviewdblclickcommand)|傳回使用者在提供的檢視內部按兩下時所執行的命令。|  
|[CMouseManager::GetViewIconId](#getviewiconid)|傳回與提供的檢視識別碼相關聯的圖示|  
|[CMouseManager::GetViewIdByName](#getviewidbyname)|傳回與提供的檢視名稱相關聯的檢視表識別碼。|  
|[CMouseManager::GetViewNames](#getviewnames)|擷取所有加入的檢視名稱的清單。|  
|[CMouseManager::LoadState](#loadstate)|載入`CMouseManager`從 Windows 登錄狀態。|  
|[CMouseManager::SaveState](#savestate)|寫入`CMouseManager`狀態寫入 Windows 登錄。|  
|[CMouseManager::SetCommandForDblClk](#setcommandfordblclk)|將提供的命令和提供的檢視產生關聯。|  
  
## <a name="remarks"></a>備註  
 `CMouseManager`類別會維護的集合`CView`物件。 每個檢視被識別依名稱和 id。 這些檢視會顯示在**自訂** 對話方塊。 使用者可以變更與透過任何檢視相關聯的命令**自訂** 對話方塊。 當使用者按兩下該檢視中，會執行相關聯的命令。 若要支援此作業從程式碼撰寫的觀點來看，您必須處理`WM_LBUTTONDBLCLK`訊息並呼叫[CWinAppEx::OnViewDoubleClick](../../mfc/reference/cwinappex-class.md#onviewdoubleclick)函式，該程式碼中的`CView`物件...  
  
 您不應建立`CMouseManager`手動物件。 它會建立由應用程式的架構。 它也會終結自動當使用者結束應用程式。 若要取得的指標至滑鼠管理員，您的應用程式，呼叫[CWinAppEx::GetMouseManager](../../mfc/reference/cwinappex-class.md#getmousemanager)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMouseManager`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxmousemanager.h  
  
##  <a name="addview"></a>CMouseManager::AddView  
 註冊[CView](../../mfc/reference/cview-class.md)物件[CMouseManager 類別](../../mfc/reference/cmousemanager-class.md)以支援自訂滑鼠行為。  
  
```  
BOOL AddView(
    int iViewId,  
    UINT uiViewNameResId,  
    UINT uiIconId = 0);

 
BOOL AddView(
    int iId,  
    LPCTSTR lpszViewName,  
    UINT uiIconId = 0);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `iViewId`  
 檢視識別碼。  
  
 [輸入] `uiViewNameResId`  
 資源字串 ID 所參考的檢視名稱。  
  
 [輸入] `uiIconId`  
 檢視圖示識別碼。  
  
 [輸入] `iId`  
 檢視識別碼。  
  
 [輸入] `lpszViewName`  
 檢視名稱。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 若要支援自訂滑鼠行為，以檢視必須註冊`CMouseManager`物件。 任何物件衍生自`CView`類別可以使用滑鼠管理員註冊。 字串和與檢視相關聯的圖示會顯示在**滑鼠** 索引標籤**自訂** 對話方塊。  
  
 建立和維護檢視識別碼，例如程式設計人員負責`iViewId`和`iId`。  
  
 如需如何提供自訂的滑鼠行為的詳細資訊，請參閱[鍵盤和滑鼠自訂](../../mfc/keyboard-and-mouse-customization.md)。  
  
### <a name="example"></a>範例  
 下列範例示範如何擷取指標`CMouseManager`物件使用`CWinAppEx::GetMouseManager`方法和`AddView`方法中的`CMouseManager`類別。 此程式碼片段是部分[狀態集合範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_StateCollection#4](../../mfc/reference/codesnippet/cpp/cmousemanager-class_1.cpp)]  
  
##  <a name="getviewdblclickcommand"></a>  CMouseManager::GetViewDblClickCommand  
 傳回使用者在提供的檢視內部按兩下時所執行的命令。  
  
```  
UINT GetViewDblClickCommand(int iId) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸入] `iId`  
 檢視識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果檢視是相關聯的命令; 命令識別碼否則便是 0。  
  
##  <a name="getviewiconid"></a>  CMouseManager::GetViewIconId  
 擷取與檢視識別碼相關聯的圖示  
  
```  
UINT GetViewIconId(int iViewId) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸入] `iViewId`  
 檢視識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功; 圖示資源識別項否則便是 0。  
  
### <a name="remarks"></a>備註  
 這個方法將會失敗，如果檢視未使用第一次登錄[CMouseManager::AddView](#addview)。  
  
##  <a name="getviewidbyname"></a>  CMouseManager::GetViewIdByName  
 擷取與檢視名稱相關聯的檢視表識別碼。  
  
```  
int GetViewIdByName(LPCTSTR lpszName) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszName`  
 檢視名稱。  
  
### <a name="return-value"></a>傳回值  
 如果成功; 檢視表識別碼否則便是 0。  
  
### <a name="remarks"></a>備註  
 這個方法會搜尋透過檢視來使用註冊[CMouseManager::AddView](#addview)。  
  
##  <a name="getviewnames"></a>  CMouseManager::GetViewNames  
 擷取所有已註冊的檢視名稱的清單。  
  
```  
void GetViewNames(CStringList& listOfNames) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `listOfNames`  
 若要參考`CStringList`物件。  
  
### <a name="remarks"></a>備註  
 這個方法會填入參數`listOfNames`使用註冊的所有檢視的名稱取代[CMouseManager::AddView](#addview)。  
  
##  <a name="loadstate"></a>  CMouseManager::LoadState  
 載入的狀態[CMouseManager 類別](../../mfc/reference/cmousemanager-class.md)從登錄。  
  
```  
BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszProfileName`  
 登錄機碼的路徑。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 從登錄載入狀態資訊會包含已註冊的檢視、 檢視識別碼和相關聯的命令。 如果參數`lpszProfileName`是`NULL`，此函式載入`CMouseManager`所控制的預設登錄位置中的資料[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)。  
  
 在大部分情況下，您不必直接呼叫此函式。 它稱為工作區初始化程序的一部分。 如需工作區初始化程序的詳細資訊，請參閱[CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate)。  
  
##  <a name="savestate"></a>  CMouseManager::SaveState  
 寫入的狀態[CMouseManager 類別](../../mfc/reference/cmousemanager-class.md)登錄。  
  
```  
BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszProfileName`  
 登錄機碼的路徑。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 寫入登錄的狀態資訊會包含所有已註冊的檢視、 檢視識別碼和相關聯的命令。 如果參數`lpszProfileName`是`NULL`，此函式會寫入`CMouseManager`資料所控制的預設登錄位置[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)。  
  
 在大部分情況下，您不必直接呼叫此函式。 它稱為工作區序列化程序的一部分。 如需工作區序列化程序的詳細資訊，請參閱[CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate)。  
  
##  <a name="setcommandfordblclk"></a>  CMouseManager::SetCommandForDblClk  
 將自訂命令與第一次向滑鼠管理員的檢視產生關聯。  
  
```  
void SetCommandForDblClk(
    int iViewId,  
    UINT uiCmd);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `iViewId`  
 檢視識別項。  
  
 [輸入] `uiCmd`  
 命令識別項。  
  
### <a name="remarks"></a>備註  
 若要將自訂命令產生關聯的檢視，您必須先註冊檢視使用[CMouseManager::AddView](#addview)。 `AddView`方法需要檢視識別項做為輸入參數。 一旦您註冊的檢視，您可以呼叫`CMouseManager::SetCommandForDblClk`具有相同檢視識別項之輸入參數提供給`AddView`。 此後，當使用者按兩下滑鼠中已註冊的檢視時，應用程式將執行命令所指示`uiCmd.`以支援自訂滑鼠行為，您也需要自訂向 滑鼠管理員檢視。 如需自訂滑鼠行為的詳細資訊，請參閱[鍵盤和滑鼠自訂](../keyboard-and-mouse-customization.md)。  
  
 如果`uiCmd`設為 0，指定的檢視已不再與命令相關聯。  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)   
 [鍵盤和滑鼠自訂](../../mfc/keyboard-and-mouse-customization.md)



