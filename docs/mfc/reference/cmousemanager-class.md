---
title: "CMouseManager 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMouseManager
dev_langs:
- C++
helpviewer_keywords:
- CMouseManager class
ms.assetid: a4d05017-4e44-4a40-8b57-4ece0de20481
caps.latest.revision: 26
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 7ba50f976f6cf9d6b701e39304c50507cfa34cc5
ms.lasthandoff: 02/24/2017

---
# <a name="cmousemanager-class"></a>CMouseManager 類別
允許將不同的命令與特定使用者[CView](../../mfc/reference/cview-class.md)當使用者按兩下該檢視內的物件。  
  
## <a name="syntax"></a>語法  
  
```  
class CMouseManager : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMouseManager::AddView](#addview)|新增`CView`物件傳遞給**自訂**對話方塊。 **自訂**對話方塊可讓使用者按兩下關聯命令，針對每個列出的檢視。|  
|[CMouseManager::GetViewDblClickCommand](#getviewdblclickcommand)|傳回使用者按兩下內提供的檢視時，所執行的命令。|  
|[CMouseManager::GetViewIconId](#getviewiconid)|傳回提供的檢視識別碼相關聯的圖示|  
|[CMouseManager::GetViewIdByName](#getviewidbyname)|傳回與提供的檢視名稱相關聯的檢視識別碼。|  
|[CMouseManager::GetViewNames](#getviewnames)|擷取所有新增的檢視名稱的清單。|  
|[CMouseManager::LoadState](#loadstate)|載入`CMouseManager`狀態從 Windows 登錄。|  
|[CMouseManager::SaveState](#savestate)|寫入`CMouseManager`狀態寫入 Windows 登錄。|  
|[CMouseManager::SetCommandForDblClk](#setcommandfordblclk)|將提供的命令和提供的檢視相關聯。|  
  
## <a name="remarks"></a>備註  
 `CMouseManager`類別會維護一堆`CView`物件。 每個檢視被識別依名稱和 id。 這些檢視會顯示在**自訂**對話方塊。 使用者可以變更與透過任何檢視相關聯的命令**自訂**對話方塊。 當使用者按兩下該檢視中，會執行相關聯的命令。 若要支援此功能從程式碼撰寫的觀點來看，您必須處理`WM_LBUTTONDBLCLK`訊息並呼叫[CWinAppEx::OnViewDoubleClick](../../mfc/reference/cwinappex-class.md#onviewdoubleclick)函式中的程式碼`CView`物件...  
  
 您不應該建立`CMouseManager`手動物件。 它將建立應用程式的架構。 它也會終結自動當使用者結束應用程式。 若要取得您的應用程式滑鼠管理員的指標，呼叫[CWinAppEx::GetMouseManager](../../mfc/reference/cwinappex-class.md#getmousemanager)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMouseManager`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxmousemanager.h  
  
##  <a name="a-nameaddviewa--cmousemanageraddview"></a><a name="addview"></a>CMouseManager::AddView  
 註冊[CView](../../mfc/reference/cview-class.md)物件[CMouseManager 類別](../../mfc/reference/cmousemanager-class.md)以支援自訂的滑鼠行為。  
  
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
 [in] `iViewId`  
 檢視識別碼。  
  
 [in] `uiViewNameResId`  
 資源字串的 ID 參考檢視名稱。  
  
 [in] `uiIconId`  
 檢視圖示識別碼。  
  
 [in] `iId`  
 檢視識別碼。  
  
 [in] `lpszViewName`  
 檢視名稱。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 為了支援滑鼠自訂行為，檢視必須向`CMouseManager`物件。 任何物件衍生自`CView`類別可以使用滑鼠管理員註冊。 字串和檢視表相關聯的圖示會顯示在**滑鼠** 索引標籤的**自訂**對話方塊。  
  
 建立和維護檢視識別碼，例如，程式設計師負責`iViewId`和`iId`。  
  
 如需如何提供自訂的滑鼠行為的詳細資訊，請參閱[鍵盤和滑鼠自訂](../../mfc/keyboard-and-mouse-customization.md)。  
  
### <a name="example"></a>範例  
 下列範例示範如何擷取變數的指標，`CMouseManager`物件使用`CWinAppEx::GetMouseManager`方法和`AddView`方法中的`CMouseManager`類別。 此程式碼片段是一部分[狀態集合範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_StateCollection #&4;](../../mfc/reference/codesnippet/cpp/cmousemanager-class_1.cpp)]  
  
##  <a name="a-namegetviewdblclickcommanda--cmousemanagergetviewdblclickcommand"></a><a name="getviewdblclickcommand"></a>CMouseManager::GetViewDblClickCommand  
 傳回使用者按兩下內提供的檢視時，所執行的命令。  
  
```  
UINT GetViewDblClickCommand(int iId) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `iId`  
 檢視識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果檢視命令，與相關聯的命令識別項否則為 0。  
  
##  <a name="a-namegetviewiconida--cmousemanagergetviewiconid"></a><a name="getviewiconid"></a>CMouseManager::GetViewIconId  
 擷取與檢視識別碼相關聯的圖示  
  
```  
UINT GetViewIconId(int iViewId) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `iViewId`  
 檢視識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功，圖示資源識別碼否則為 0。  
  
### <a name="remarks"></a>備註  
 如果檢視未使用第一次註冊，這個方法將會失敗[CMouseManager::AddView](#addview)。  
  
##  <a name="a-namegetviewidbynamea--cmousemanagergetviewidbyname"></a><a name="getviewidbyname"></a>CMouseManager::GetViewIdByName  
 擷取與檢視表名稱相關聯的檢視識別碼。  
  
```  
int GetViewIdByName(LPCTSTR lpszName) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszName`  
 檢視名稱。  
  
### <a name="return-value"></a>傳回值  
 如果成功則檢視表識別碼否則為 0。  
  
### <a name="remarks"></a>備註  
 這個方法會透過使用註冊的檢視搜尋[CMouseManager::AddView](#addview)。  
  
##  <a name="a-namegetviewnamesa--cmousemanagergetviewnames"></a><a name="getviewnames"></a>CMouseManager::GetViewNames  
 擷取所有已註冊的檢視名稱的清單。  
  
```  
void GetViewNames(CStringList& listOfNames) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `listOfNames`  
 參考`CStringList`物件。  
  
### <a name="remarks"></a>備註  
 這個方法會填入參數`listOfNames`使用註冊的所有檢視的名稱與[CMouseManager::AddView](#addview)。  
  
##  <a name="a-nameloadstatea--cmousemanagerloadstate"></a><a name="loadstate"></a>CMouseManager::LoadState  
 載入的狀態[CMouseManager 類別](../../mfc/reference/cmousemanager-class.md)登錄中。  
  
```  
BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszProfileName`  
 登錄機碼的路徑。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 從登錄載入狀態資訊會包含已註冊的檢視，檢視識別碼和相關聯的命令。 如果參數`lpszProfileName`是`NULL`，此函式載入`CMouseManager`所控制的預設登錄位置中的資料[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)。  
  
 在大部分情況下，您不需要直接呼叫此函式。 它稱為工作區初始化程序的一部分。 如需工作區初始化程序的詳細資訊，請參閱[CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate)。  
  
##  <a name="a-namesavestatea--cmousemanagersavestate"></a><a name="savestate"></a>CMouseManager::SaveState  
 寫入的狀態[CMouseManager 類別](../../mfc/reference/cmousemanager-class.md)登錄。  
  
```  
BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszProfileName`  
 登錄機碼的路徑。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 寫入登錄的狀態資訊包括所有已註冊的檢視，檢視識別碼和相關聯的命令。 如果參數`lpszProfileName`是`NULL`，此函數會寫入`CMouseManager`所控制的預設登錄位置的資料[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)。  
  
 在大部分情況下，您不需要直接呼叫此函式。 它稱為工作區序列化程序的一部分。 如需工作區序列化程序的詳細資訊，請參閱[CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate)。  
  
##  <a name="a-namesetcommandfordblclka--cmousemanagersetcommandfordblclk"></a><a name="setcommandfordblclk"></a>CMouseManager::SetCommandForDblClk  
 自訂命令關聯至第一次向滑鼠管理員的檢視。  
  
```  
void SetCommandForDblClk(
    int iViewId,  
    UINT uiCmd);
```  
  
### <a name="parameters"></a>參數  
 [in] `iViewId`  
 檢視識別項。  
  
 [in] `uiCmd`  
 命令識別碼。  
  
### <a name="remarks"></a>備註  
 若要將自訂命令相關聯的檢視，您必須先註冊檢視使用[CMouseManager::AddView](#addview)。 `AddView`方法需要檢視識別項做為輸入參數。 一旦您註冊的檢視，您可以呼叫`CMouseManager::SetCommandForDblClk`與相同檢視識別碼輸入參數提供給`AddView`。 此後，當使用者按兩下滑鼠已註冊的檢視中，應用程式將執行命令以`uiCmd.`以支援自訂的滑鼠行為，您也需要來自訂滑鼠管理員註冊的檢視。 如需自訂滑鼠行為的詳細資訊，請參閱 [鍵盤和滑鼠自訂]--brokenlink-(.../ 滑鼠-和-鍵盤-customization.md）。  
  
 如果`uiCmd`設為 0，指定的檢視已不再與命令相關聯。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [Cwinappex 衍生類別](../../mfc/reference/cwinappex-class.md)   
 [鍵盤和滑鼠自訂](../../mfc/keyboard-and-mouse-customization.md)




