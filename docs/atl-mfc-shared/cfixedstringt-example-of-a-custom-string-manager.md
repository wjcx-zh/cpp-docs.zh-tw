---
title: "CFixedStringT: Example of a Custom String Manager | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFixedStringT class, using a custom string manager"
ms.assetid: 1cf11fd7-51b8-4b94-87af-02bc25f47dd6
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# CFixedStringT: Example of a Custom String Manager
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL 程式庫的實作類別使用的自訂字串處理常式的範例， [CFixedStringT](../atl-mfc-shared/reference/cfixedstringt-class.md)呼叫 **CFixedStringMgr**。  `CFixedStringT`[CStringT](../atl-mfc-shared/reference/cstringt-class.md) 從衍生並實作來配置它的字元資料做為物件 `CFixedStringT` 字串的一部分，只要字串比較 `CFixedStringT`**t\_nChars** 樣板參數指定的長度是更少。  這個方法，為，除非字串的長度 \(以固定的緩衝區的大小之外，增加字串完全不需要堆積。  由於 `CFixedStringT` 並非一定會使用一個堆積配置其字串資料，就無法使用 **CAtlStringMgr** 做為它的資料處理常式。  它會使用自訂字串處理常式 \(**CFixedStringMgr**\)， [IAtlStringMgr](../atl-mfc-shared/reference/iatlstringmgr-class.md) 實作介面。  這個介面會 [自訂字串處理常式 \(進階方法\) 的實作。](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md)討論。  
  
 **CFixedStringMgr** 的建構函式接受三個參數:  
  
-   要使用的固定 `CStringData` 結構的**pData:** 指標。  
  
-   **nChars:** `CStringData` 結構可以容納的最大字元數。  
  
-   為「備份字串處理常式的 `IAtlStringMgr` 介面的**pMgr:** 指標」。  
  
 建構函式在各自的成員變數儲存 `pData` 和 **pMgr** 的值 \(`m_pData` 和 **m\_pMgr**\)。  然後調整緩衝區的長度為零，可用的長度等於 Pin 緩衝區的最大大小和參考計數為– 1。  參考計數值表示緩衝區鎖定和 **CFixedStringMgr** 使用執行個體做為字串處理常式。  
  
 標記緩衝區的鎖定會防止其他 `CStringT` 執行個體至緩衝區的共用的參考。  如果其他 `CStringT` 執行個體允許共用緩衝區對於 `CFixedStringT` 中的緩衝區可能會刪除，而其他字串仍使用緩衝區時。  
  
 **CFixedStringMgr** 是 `IAtlStringMgr` 介面的完整實作。  每個方法的實作分開討論。  
  
## CFixedStringMgr::Allocate 的實作。  
 **CFixedStringMgr::Allocate** 的實作會先檢查資料的要求大小是否小於或等於 Pin 緩衝區的大小 \(儲存在 `m_pData` 成員\)。  如果固定緩衝區夠大， **CFixedStringMgr** 鎖定具有長度的固定緩衝區中的零。  只要字串長度不在固定的緩衝區以外的大小增加， `CStringT` 不需要重新配置緩衝區。  
  
 如果字串的要求大小大於固定緩衝區中 **CFixedStringMgr** 會將要求轉送至待命字串處理常式。  備份字串處理常式假設是從堆積配置緩衝區。  不過，在返回這個緩衝區之前 **CFixedStringMgr** 鎖定緩衝區並以指標取代緩衝區的資料處理常式指標 **CFixedStringMgr** 物件。  這可確保嘗試 `CStringT` 重新配置或釋放緩衝區將呼叫 **CFixedStringMgr**。  
  
## CFixedStringMgr::ReAllocate 的實作。  
 **CFixedStringMgr::ReAllocate** 的實作非常類似於其 **Allocate**的實作。  
  
 如果重新配置緩衝區是固定的緩衝區，並要求的緩衝區大小小於固定緩衝區中，配置未完成。  不過，在中，如果重新配置緩衝區不固定的緩衝區，它必須是緩衝區配置與這個備份處理常式。  在這個案例中這個備份管理員用來重新配置緩衝區。  
  
 如果重新配置緩衝區是固定的緩衝區，而且新的緩衝區大小太大而無法在固定緩衝區中適合，使用這個備份處理常式， **CFixedStringMgr** 配置新的緩衝區。  Pin 緩衝區的內容隨後會複製到新的緩衝區。  
  
## CFixedStringMgr::Free 的實作。  
 **CFixedStringMgr::Free** 的實作遵循模式和 **Allocate** 和 `ReAllocate`相同。  如果已釋放的緩衝區是固定的緩衝區，方法會將其設定為零長度的鎖定的緩衝區。  如果已釋放的緩衝區配置了這個備份處理常式中，使用  **CFixedStringMgr** 備份管理員釋放它。  
  
## CFixedStringMgr::Clone 的實作。  
 **CFixedStringMgr::Clone** 的實作一定會傳回指標給這個備份處理常式而不是 **CFixedStringMgr** 。  **CFixedStringMgr** ，因為每個執行個體只能與 `CStringT`，單一執行個體時發生。  嘗試 `CStringT` 任何其他執行個體複製該管理員應該備份取得這個處理常式。  這是因為，共用的備份管理員支援。  
  
## CFixedStringMgr::GetNilString 的實作。  
 **CFixedStringMgr::GetNilString** 的實作會傳回 Pin 緩衝區。  由於 **CFixedStringMgr** 和 `CStringT`一對一的對應關係， `CStringT` 特定執行個體一次從未使用一個以上的緩衝區。  因此，零字串和真正的字串緩衝區同時永遠不需要。  
  
 每當 Pin 緩衝區不在使用中， **CFixedStringMgr** 確定它使用長度為零。  這可讓它使用為零的字串。  因為增加了紅利，固定緩衝區中的 `nAllocLength` 成員永遠設定為固定緩衝區中的完整大小。  即使為零的字串表示 `CStringT` 可能發生長度的字串，但不呼叫， [IAtlStringMgr::Reallocate](../Topic/IAtlStringMgr::Reallocate.md)。  
  
## 需求  
 **Header:** cstringt.h  
  
## 請參閱  
 [Memory Management with CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)