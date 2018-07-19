---
title: CJumpList 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0c4090ebfa432f1d8b7f05942a6b1af68b75d270
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37337888"
---
# <a name="cjumplist-class"></a>CJumpList 類別
A`CJumpList`是當您以滑鼠右鍵按一下工作列中的圖示時所顯示的捷徑清單。  
  
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
|[CJumpList::AbortList](#abortlist)|中止清單構成交易，而不需要認可。|  
|[CJumpList::AddDestination](#adddestination)|多載。 將目的地加入至清單。|  
|[CJumpList::AddKnownCategory](#addknowncategory)|將一個已知的類別附加至清單。|  
|[CJumpList::AddTask](#addtask)|多載。 將項目加入至標準工作分類。|  
|[CJumpList::AddTasks](#addtasks)|將項目加入至標準工作分類。|  
|[CJumpList::AddTaskSeparator](#addtaskseparator)|新增工作之間的分隔符號。|  
|[CJumpList::ClearAll](#clearall)|移除所有的工作和已加入至目前的執行個體的目的地`CJumpList`為止。|  
|[CJumpList::ClearAllDestinations](#clearalldestinations)|移除已新增至目前的執行個體的所有目的地`CJumpList`為止。|  
|[CJumpList::CommitList](#commitlist)|結束清單構成交易並認可報告的清單相關聯的儲存區 （在此情況下登錄。）|  
|[CJumpList::GetDestinationList](#getdestinationlist)|擷取目的地清單的介面指標。|  
|[CJumpList::GetMaxSlots](#getmaxslots)|擷取的項目，包括分類標頭可以在呼叫應用程式的 [目的地] 功能表中顯示的數目上限。|  
|[CJumpList::GetRemovedItems](#getremoveditems)|傳回陣列，表示項目移除目的地。|  
|[CJumpList::InitializeList](#initializelist)|開始清單構成交易。|  
|[CJumpList::SetAppID](#setappid)|設定應用程式使用者模型識別碼，將會建置的清單。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CJumpList](../../mfc/reference/cjumplist-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxadv.h  
  
##  <a name="_dtorcjumplist"></a>  CJumpList:: ~ CJumpList  
 終結 `CJumpList` 物件。  
  
```  
~CJumpList();
```  
  
##  <a name="abortlist"></a>  CJumpList::AbortList  
 中止清單構成交易，而不需要認可。  
  
```  
void AbortList();
```  
  
### <a name="remarks"></a>備註  
 呼叫這個方法有相同的效果終結`CJumpList`而不需呼叫`CommitList`。  
  
##  <a name="adddestination"></a>  CJumpList::AddDestination  
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
 *lpcszCategoryName*  
 指定的類別名稱。 如果指定的分類不存在，它會建立它。  
  
 *strDestinationPath*  
 指定目的地檔案的路徑。  
  
 *strCategoryName*  
 指定的類別名稱。 如果指定的分類不存在，它會建立它。  
  
 *pShellItem*  
 指定代表要加入目的地殼層項目。  
  
 *pShellLink*  
 指定殼層連結，以代表要加入的目的地。  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 執行個體`CJumpList`在內部會累積新增的目的地，然後認可在`CommitList`。  
  
##  <a name="addknowncategory"></a>  CJumpList::AddKnownCategory  
 將一個已知的類別附加至清單。  
  
```  
BOOL AddKnownCategory(KNOWNDESTCATEGORY category);
```  
  
### <a name="parameters"></a>參數  
 *category*  
 指定已知的類別類型。 可以是 KDC_RECENT 或 KDC_KNOWN。  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 已知的分類為 經常與最近類別，我們將會自動計算每個應用程式，它會利用`SHAddToRecentDocs`（或間接使用它時，殼層會呼叫它的應用程式代表，在某些情況下）。  
  
##  <a name="addtask"></a>  CJumpList::AddTask  
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
 *strTargetExecutablePath*  
 指定的目標工作路徑。  
  
 *strCommandLineArgs*  
 指定 strTargetExecutablePath 所指定的可執行檔的命令列引數。  
  
 *strTitle*  
 將會顯示在 [目的地] 清單中的工作名稱。  
  
 *strIconLocation*  
 將標題和之目的地清單中顯示的圖示的位置。  
  
 *iIconIndex*  
 圖示的索引。  
  
 *pShellLink*  
 表示要加入的工作的 shell 連結。  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 執行個體`CJumpList`累積指定的工作，並將它們新增至目的地清單期間`CommitList`。 工作項目會出現在底部的 應用程式的 目的地 功能表的類別。 當它在 UI 中填滿時，此類別的優先順序高於所有其他類別。  
  
##  <a name="addtasks"></a>  CJumpList::AddTasks  
 將項目加入至標準工作分類。  
  
```  
BOOL AddTasks(IObjectArray* pObjectCollection);
```  
  
### <a name="parameters"></a>參數  
 *pObjectCollection*  
 要加入的工作集合。  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 CJumpList 的執行個體累積指定的工作，並將它們新增至目的地清單期間`CommitList`。 工作項目會出現在底部的 應用程式的 目的地 功能表的類別。 當它在 UI 中填滿時，此類別的優先順序高於所有其他類別。  
  
##  <a name="addtaskseparator"></a>  CJumpList::AddTaskSeparator  
 新增工作之間的分隔符號。  
  
```  
BOOL AddTaskSeparator();
```  
  
### <a name="return-value"></a>傳回值  
 非零值，如果成功，如果不是 0。  
  
##  <a name="cjumplist"></a>  CJumpList::CJumpList  
 建構 `CJumpList` 物件。  
  
```  
CJumpList(BOOL bAutoCommit = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *bAutoCommit*  
 如果此參數為 FALSE 時不會解構函式中自動認可清單。  
  
##  <a name="clearall"></a>  CJumpList::ClearAll  
 移除所有的工作和已加入至目前的執行個體的目的地`CJumpList`為止。  
  
```  
void ClearAll();
```  
  
### <a name="remarks"></a>備註  
 這個方法會清除並釋放所有的資料和內部介面。  
  
##  <a name="clearalldestinations"></a>  CJumpList::ClearAllDestinations  
 移除已新增至目前的執行個體的 CJumpList 到目前為止的所有目的地。  
  
```  
void ClearAllDestinations();
```  
  
### <a name="remarks"></a>備註  
 如果您要移除所有目的地中已加入到目前為止的目的地清單建置目前的工作階段，並再次新增其他目的地，請呼叫此函式。 如果內部`ICustomDestinationList`已初始化，它就保持運作。  
  
##  <a name="commitlist"></a>  CJumpList::CommitList  
 結束清單構成交易，並認可至相關聯的存放區 （在此情況下登錄） 的報告的清單。  
  
```  
BOOL CommitList();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 Commit 就是不可部分完成的。 如果認可失敗，則會傳回錯誤。  當`CommitList`呼叫時，目前已移除的項目清單將會清除。 呼叫這個方法，使它並沒有使用中的清單建置交易，會重設物件。 若要更新的清單中，`BeginList`需要被呼叫一次。  
  
##  <a name="getdestinationlist"></a>  CJumpList::GetDestinationList  
 擷取目的地清單的介面指標。  
  
```  
ICustomDestinationList* GetDestinationList();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 如果捷徑清單尚未初始化，或已認可或中止，則傳回的值會是 NULL。  
  
##  <a name="getmaxslots"></a>  CJumpList::GetMaxSlots  
 擷取的項目，包括分類標頭可以在呼叫應用程式的 [目的地] 功能表中顯示的數目上限。  
  
```  
UINT GetMaxSlots() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 應用程式可能只會報告許多項目和合併到此值的分類標頭。 如果呼叫`AppendCategory`， `AppendKnownCategory`，或`AddUserTasks`超過此數字，它們將會傳回失敗。  
  
##  <a name="getremoveditems"></a>  CJumpList::GetRemovedItems  
 傳回陣列，表示項目移除目的地。  
  
```  
IObjectArray* GetRemovedItems();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 移除的目的地的捷徑清單初始化期間擷取。 產生新的 [目的地] 清單，當應用程式應該先處理已移除的目的地清單中，清除已移除的清單的列舉值所傳回的任何項目其追蹤資料。 如果應用程式會嘗試提供已只會移除在目前呼叫的交易中的項目`BeginList`啟動，重新新增該項目方法呼叫將會失敗，以確保應用程式會採用已移除的清單。  
  
##  <a name="initializelist"></a>  CJumpList::InitializeList  
 開始清單構成交易。  
  
```  
BOOL InitializeList();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 您不需要明確地呼叫這個方法，除非您想要擷取的指標`ICustomDestinationList`使用`GetDestinationList`，使用的可用插槽數目`GetMaxSlots`，或使用移除的項目清單`GetRemovedItems`。  
  
##  <a name="setappid"></a>  CJumpList::SetAppID  
 設定應用程式使用者模型識別碼，將會建置的清單。  
  
```  
void SetAppID(LPCTSTR strAppID);
```  
  
### <a name="parameters"></a>參數  
 *strAppID*  
 字串，指定應用程式使用者模型識別碼。  
  
## <a name="see-also"></a>另請參閱  
 [類別](../../mfc/reference/mfc-classes.md)
