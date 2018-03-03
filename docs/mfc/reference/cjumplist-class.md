---
title: "CJumpList 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CJumpList
- AFXADV/CJumpList
- AFXADV/CJumpList::CJumpList
- AFXADV/CJumpList::AbortList
- AFXADV/CJumpList::AddDestination
- AFXADV/CJumpList::AddKnownCategory
- AFXADV/CJumpList::AddTask
- AFXADV/CJumpList::AddTasks
- AFXADV/CJumpList::AddTaskSeparator
- AFXADV/CJumpList::ClearAll
- AFXADV/CJumpList::ClearAllDestinations
- AFXADV/CJumpList::CommitList
- AFXADV/CJumpList::GetDestinationList
- AFXADV/CJumpList::GetMaxSlots
- AFXADV/CJumpList::GetRemovedItems
- AFXADV/CJumpList::InitializeList
- AFXADV/CJumpList::SetAppID
dev_langs:
- C++
helpviewer_keywords:
- CJumpList [MFC], CJumpList
- CJumpList [MFC], AbortList
- CJumpList [MFC], AddDestination
- CJumpList [MFC], AddKnownCategory
- CJumpList [MFC], AddTask
- CJumpList [MFC], AddTasks
- CJumpList [MFC], AddTaskSeparator
- CJumpList [MFC], ClearAll
- CJumpList [MFC], ClearAllDestinations
- CJumpList [MFC], CommitList
- CJumpList [MFC], GetDestinationList
- CJumpList [MFC], GetMaxSlots
- CJumpList [MFC], GetRemovedItems
- CJumpList [MFC], InitializeList
- CJumpList [MFC], SetAppID
ms.assetid: d364d27e-f512-4b12-9872-c2a17c78ab1f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 11b28199155c0ac3bd90cda8fb830ea6f8894dde
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cjumplist-class"></a>CJumpList 類別
A`CJumpList`是當您以滑鼠右鍵按一下工作列中的圖示時所顯示的快速鍵的清單。  
  
## <a name="syntax"></a>語法  
  
```  
class CJumpList;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CJumpList::CJumpList](#cjumplist)|建構 `CJumpList` 物件。|  
|[CJumpList:: ~ CJumpList](#cjumplist__~cjumplist)|終結 `CJumpList` 物件。|  
  
|名稱|描述|  
|----------|-----------------|  
|[CJumpList::AbortList](#abortlist)|中止清單建置交易不認可。|  
|[CJumpList::AddDestination](#adddestination)|多載。 將目的地加入至清單。|  
|[CJumpList::AddKnownCategory](#addknowncategory)|將已知的類別附加至清單。|  
|[CJumpList::AddTask](#addtask)|多載。 將項目加入至標準工作分類。|  
|[CJumpList::AddTasks](#addtasks)|將項目加入至標準工作分類。|  
|[CJumpList::AddTaskSeparator](#addtaskseparator)|新增工作之間的分隔符號。|  
|[CJumpList::ClearAll](#clearall)|移除所有的工作和已新增至目前的執行個體的目的地`CJumpList`為止。|  
|[CJumpList::ClearAllDestinations](#clearalldestinations)|移除已加入至目前的執行個體的所有目的地`CJumpList`為止。|  
|[CJumpList::CommitList](#commitlist)|結束清單建立異動時，便認可報告的清單相關聯的存放區 （在此情況下登錄。）|  
|[CJumpList::GetDestinationList](#getdestinationlist)|擷取目的地清單的介面指標。|  
|[CJumpList::GetMaxSlots](#getmaxslots)|擷取項目，包括可以在呼叫應用程式的 [目的地] 功能表中顯示的類別標頭的最大數目。|  
|[CJumpList::GetRemovedItems](#getremoveditems)|傳回陣列，表示項目移除的目的地。|  
|[CJumpList::InitializeList](#initializelist)|開始清單建立交易。|  
|[CJumpList::SetAppID](#setappid)|設定應用程式使用者模型識別碼，將建置的清單。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CJumpList](../../mfc/reference/cjumplist-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxadv.h  
  
##  <a name="_dtorcjumplist"></a>CJumpList:: ~ CJumpList  
 終結 `CJumpList` 物件。  
  
```  
~CJumpList();
```  
  
##  <a name="abortlist"></a>CJumpList::AbortList  
 中止清單建置交易不認可。  
  
```  
void AbortList();
```  
  
### <a name="remarks"></a>備註  
 呼叫這個方法有相同的效果終結`CJumpList`而不需呼叫`CommitList`。  
  
##  <a name="adddestination"></a>CJumpList::AddDestination  
 將目的地加入至清單。  
  
```  
BOOL AddDestination(
    LPCTSTR lpcszCategoryName,  
    LPCTSTR strDestinationPath);

 
BOOL AddDestination(
    LPCTSTR strCategoryName,  
    IShellItem* pShellItem);

 
BOOL AddDestination(
    LPCTSTR strCategoryName,  
    IShellLink* pShellLink);
```  
  
### <a name="parameters"></a>參數  
 `lpcszCategoryName`  
 指定類別名稱。 如果指定的類別目錄不存在，則會建立。  
  
 `strDestinationPath`  
 指定目的地檔案的路徑。  
  
 `strCategoryName`  
 指定類別名稱。 如果指定的類別目錄不存在，則會建立。  
  
 `pShellItem`  
 指定代表要加入目的地 Shell 項目。  
  
 `pShellLink`  
 指定代表要加入目的地的殼層連結。  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 執行個體`CJumpList`在內部會加入的目的地，然後認可在`CommitList`。  
  
##  <a name="addknowncategory"></a>CJumpList::AddKnownCategory  
 將已知的類別附加至清單。  
  
```  
BOOL AddKnownCategory(KNOWNDESTCATEGORY category);
```  
  
### <a name="parameters"></a>參數  
 `category`  
 指定已知的類別類型。 可以是`KDC_RECENT`，或`KDC_KNOWN`。  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 知道類別是經常和最近分類，我們將會自動計算每個應用程式，它會利用`SHAddToRecentDocs`（或間接使用它殼層會呼叫應用程式的身分，在某些情況下）。  
  
##  <a name="addtask"></a>CJumpList::AddTask  
 將項目加入至標準工作分類。  
  
```  
BOOL AddTask(
    LPCTSTR strTargetExecutablePath,  
    LPCTSTR strCommandLineArgs,  
    LPCTSTR strTitle,  
    LPCTSTR strIconLocation,  
    int iIconIndex);  
  
BOOL AddTask(IShellLink* pShellLink);
```  
  
### <a name="parameters"></a>參數  
 `strTargetExecutablePath`  
 指定目標工作路徑。  
  
 `strCommandLineArgs`  
 指定可執行檔 strTargetExecutablePath 所指定的命令列引數。  
  
 `strTitle`  
 將目的地清單中顯示的工作名稱。  
  
 `strIconLocation`  
 將標題以及之目的地清單中顯示的圖示的位置。  
  
 `iIconIndex`  
 圖示索引。  
  
 `pShellLink`  
 介面表示要加入工作的連結。  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 執行個體`CJumpList`累積指定的工作，並將它們新增至目的地清單期間`CommitList`。 工作項目會出現在應用程式的目的地功能表底部的類別。 此類別會優先於所有的其他類別，在 UI 中填滿時。  
  
##  <a name="addtasks"></a>CJumpList::AddTasks  
 將項目加入至標準工作分類。  
  
```  
BOOL AddTasks(IObjectArray* pObjectCollection);
```  
  
### <a name="parameters"></a>參數  
 `pObjectCollection`  
 要加入之工作集合。  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 CJumpList 的執行個體累加指定的工作，並將它們加入至目的地清單期間`CommitList`。 工作項目會出現在應用程式的目的地功能表底部的類別。 此類別會優先於所有的其他類別，在 UI 中填滿時。  
  
##  <a name="addtaskseparator"></a>CJumpList::AddTaskSeparator  
 新增工作之間的分隔符號。  
  
```  
BOOL AddTaskSeparator();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為非零如果不是 0。  
  
##  <a name="cjumplist"></a>CJumpList::CJumpList  
 建構 `CJumpList` 物件。  
  
```  
CJumpList(BOOL bAutoCommit = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `bAutoCommit`  
 如果這個參數是 FALSE 清單不會自動認可解構函式中。  
  
##  <a name="clearall"></a>CJumpList::ClearAll  
 移除所有的工作和已新增至目前的執行個體的目的地`CJumpList`為止。  
  
```  
void ClearAll();
```  
  
### <a name="remarks"></a>備註  
 這個方法會清除並釋放所有資料和內部介面。  
  
##  <a name="clearalldestinations"></a>CJumpList::ClearAllDestinations  
 移除已加入至目前的執行個體的 CJumpList 到目前為止的所有目的地。  
  
```  
void ClearAllDestinations();
```  
  
### <a name="remarks"></a>備註  
 如果您要移除所有目的地，已加入到目前為止的目的地清單建置目前的工作階段，並再次新增其他目的地，請呼叫此函式。 如果內部`ICustomDestinationList`已初始化，它會保持運作。  
  
##  <a name="commitlist"></a>CJumpList::CommitList  
 結束清單建立交易，並認可至相關聯的存放區 （在此情況下登錄） 的報告的清單。  
  
```  
BOOL CommitList();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 Commit 就是不可部分完成的。 如果認可失敗，則會傳回錯誤。  當`CommitList`呼叫時，目前已移除的項目清單將會清除。 呼叫這個方法，使它並沒有使用中的清單建立交易，會重設物件。 若要更新的清單，`BeginList`需要被呼叫一次。  
  
##  <a name="getdestinationlist"></a>CJumpList::GetDestinationList  
 擷取目的地清單的介面指標。  
  
```  
ICustomDestinationList* GetDestinationList();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 如果跳躍清單尚未初始化，或已認可或中止，傳回的值將是`NULL`。  
  
##  <a name="getmaxslots"></a>CJumpList::GetMaxSlots  
 擷取項目，包括可以在呼叫應用程式的 [目的地] 功能表中顯示的類別標頭的最大數目。  
  
```  
UINT GetMaxSlots() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 應用程式可能只會報告項目和類別標頭結合到此值的數的字。 如果呼叫`AppendCategory`， `AppendKnownCategory`，或`AddUserTasks`超過此數目，它們將會傳回失敗。  
  
##  <a name="getremoveditems"></a>CJumpList::GetRemovedItems  
 傳回陣列，表示項目移除的目的地。  
  
```  
IObjectArray* GetRemovedItems();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 移除的目的地的跳躍清單初始設定期間擷取。 時產生新的目的地清單時，應用程式都必須先處理移除的目的地清單中，清除其追蹤資料，傳回已移除的清單的列舉值的任何項目。 如果應用程式會嘗試提供項目只在目前呼叫在交易中移除`BeginList`啟動，重新新增該項目在方法呼叫將會失敗，以確保應用程式會尊重移除的清單。  
  
##  <a name="initializelist"></a>CJumpList::InitializeList  
 開始清單建立交易。  
  
```  
BOOL InitializeList();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 您不需要呼叫這個方法，除非您想要擷取的指標`ICustomDestinationList`使用`GetDestinationList`，使用的可用插槽數目`GetMaxSlots`，或移除的項目使用的清單`GetRemovedItems`。  
  
##  <a name="setappid"></a>CJumpList::SetAppID  
 設定應用程式使用者模型識別碼，將建置的清單。  
  
```  
void SetAppID(LPCTSTR strAppID);
```  
  
### <a name="parameters"></a>參數  
 `strAppID`  
 字串，指定應用程式使用者模型識別碼。  
  
## <a name="see-also"></a>請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
