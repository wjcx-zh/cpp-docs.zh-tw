---
title: "CFixedStringT： 範例的自訂字串管理員 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CFixedStringT class, using a custom string manager
ms.assetid: 1cf11fd7-51b8-4b94-87af-02bc25f47dd6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7164d2313f5610d1d7e56f5449c81ea9e2282981
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cfixedstringt-example-of-a-custom-string-manager"></a>CFixedStringT： 範例的自訂字串管理員
ATL 程式庫實作類別所使用的自訂字串管理員的其中一個範例[CFixedStringT](../atl-mfc-shared/reference/cfixedstringt-class.md)，稱為**CFixedStringMgr**。 `CFixedStringT`衍生自[CStringT](../atl-mfc-shared/reference/cstringt-class.md)並實作一部分配置其字元資料字串`CFixedStringT`物件本身為字串所指定的長度小於**t_nChars**樣板參數的`CFixedStringT`。 使用此方法時，不需要字串堆積，除非字串的長度超過固定緩衝區的大小。 因為`CFixedStringT`不一定不使用的堆積來配置其字串資料，它不能使用**CAtlStringMgr**做為其字串管理員。 它會使用自訂字串管理員 (**CFixedStringMgr**)，它會實作[IAtlStringMgr](../atl-mfc-shared/reference/iatlstringmgr-class.md)介面。 這個介面會討論[實作的自訂字串管理員 （進階方法）](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)。  
  
 建構函式**CFixedStringMgr**接受三個參數：  
  
-   **pData:**指標固定的`CStringData`要使用的結構。  
  
-   **nChars:**最大字元數`CStringData`結構可以保存。  
  
-   **pMgr:**指標`IAtlStringMgr`介面的 「 備份字串 manager 」。  
  
 建構函式儲存值`pData`和**pMgr**中它們各自的成員變數 (`m_pData`和**m_pMgr**)。 然後，它會設定為零，可用的長度等於最大的大小固定的緩衝區，並為-1 的參考計數的緩衝區的長度。 參考計數值，指出緩衝區已鎖定，並使用此執行個體**CFixedStringMgr**字串經理。  
  
 將緩衝區標示為已鎖定可防止其他`CStringT`緊緩衝區的共用的參考的執行個體。 如果有其他`CStringT`共用它是可行的所包含之緩衝區的緩衝區所允許的執行個體`CFixedStringT`其他字串仍所使用緩衝區時被刪除。  
  
 **CFixedStringMgr**是以完整的實作`IAtlStringMgr`介面。 會分別討論每個方法的實作。  
  
## <a name="implementation-of-cfixedstringmgrallocate"></a>CFixedStringMgr::Allocate 的實作  
 實作**CFixedStringMgr::Allocate**字串的要求的大小是否小於或等於固定緩衝區的大小會先檢查 (儲存在`m_pData`成員)。 如果固定的緩衝區不夠大**CFixedStringMgr**鎖定固定的緩衝區長度為零。 字串長度不會成長得超過的固定的緩衝區大小為`CStringT`不會重新配置緩衝區。  
  
 如果字串的要求的大小大於固定緩衝區**CFixedStringMgr**要求轉送給字串備份管理員。 備份字串管理員會假設配置堆積中的緩衝區。 不過，再傳回此緩衝區**CFixedStringMgr**鎖定緩衝區，並以指標取代緩衝區的字串管理員指標**CFixedStringMgr**物件。 這可確保嘗試重新配置或釋放緩衝區`CStringT`就會呼叫**CFixedStringMgr**。  
  
## <a name="implementation-of-cfixedstringmgrreallocate"></a>CFixedStringMgr::ReAllocate 的實作  
 實作**CFixedStringMgr::ReAllocate**非常類似於它的實作**配置**。  
  
 如果要重新配置的緩衝區是固定的緩衝區，要求的緩衝區大小小於固定緩衝區不會進行配置。 不過，如果要重新配置的緩衝區不是固定的緩衝區，它必須是以備份管理員所配置的緩衝區。 在此情況下備份管理員用來重新配置的緩衝區。  
  
 如果要重新配置的緩衝區是固定的緩衝區，而且新的緩衝區大小太大而無法容納固定緩衝區， **CFixedStringMgr**會配置新緩衝區使用的備份管理員。 然後會將固定緩衝區的內容複製到新的緩衝區。  
  
## <a name="implementation-of-cfixedstringmgrfree"></a>CFixedStringMgr::Free 的實作  
 實作**CFixedStringMgr::Free**遵循相同的模式為**配置**和`ReAllocate`。 如果要釋放的緩衝區是固定的緩衝區，方法會將它設定為零長度的鎖定緩衝區。 如果要釋放的緩衝區已備份管理員，以配置**CFixedStringMgr**使用備份管理員將它釋放。  
  
## <a name="implementation-of-cfixedstringmgrclone"></a>CFixedStringMgr::Clone 的實作  
 實作**CFixedStringMgr::Clone**永遠備份管理員傳回的指標而**CFixedStringMgr**本身。 這是因為每個執行個體**CFixedStringMgr**只能是單一執行個體相關聯`CStringT`。 任何其他執行個體`CStringT`嘗試進行複製，管理員應該取得備份管理員改為。 這是因為備份管理員支援共用。  
  
## <a name="implementation-of-cfixedstringmgrgetnilstring"></a>CFixedStringMgr::GetNilString 的實作  
 實作**CFixedStringMgr::GetNilString**傳回固定的緩衝區。 因為一對一的對應**CFixedStringMgr**和`CStringT`，指定的執行個體`CStringT`永遠不會使用多個緩衝區，一次。 因此，nil 字串和實際字串緩衝區永遠不需要在相同的時間。  
  
 固定的緩衝區不在使用中，每當**CFixedStringMgr**可確保它長度為零初始化。 這可讓它要做為 nil 的字串。 另外，`nAllocLength`的固定緩衝區成員一定會設定為完整的固定緩衝區大小。 這表示`CStringT`所能成長的字串，而不需呼叫[IAtlStringMgr::Reallocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#reallocate)即使 nil 的字串。  
  
## <a name="requirements"></a>需求  
 **標頭：** cstringt.h  
  
## <a name="see-also"></a>請參閱  
 [使用 CStringT 管理記憶體](../atl-mfc-shared/memory-management-with-cstringt.md)

