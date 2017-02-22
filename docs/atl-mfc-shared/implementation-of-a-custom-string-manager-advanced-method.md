---
title: "Implementation of a Custom String Manager (Advanced Method) | Microsoft Docs"
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
  - "IAtlStringMgr class, 使用"
ms.assetid: 64ab7da9-47c1-4c4a-9cd7-4cc37e7f3f57
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Implementation of a Custom String Manager (Advanced Method)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在特定情況下，您可能會想要實作不僅變更堆積是用來配置記憶體的自訂字串處理常式。  在這種情況下，您必須手動實作 [IAtlStringMgr](../atl-mfc-shared/reference/iatlstringmgr-class.md) 介面做為您的自訂字串處理常式。  
  
 若要這樣做，請注意連接管理其字串資料的 [CStringT](../atl-mfc-shared/reference/cstringt-class.md) 使用 HOW TO 首先是很重要的。  `CStringT` 每一個執行個體都有指標 [CStringData](../atl-mfc-shared/reference/cstringdata-class.md) 結構。  這個可變長度的結構包含有關資料的重要資訊 \(例如長度\)，以及字串的實際字元資料。  每個自訂字串管理員負責配置和釋放這些結構應用 `CStringT`要求。  
  
 `CStringData` 結構包含四個欄位:  
  
-   [pStringMgr](../Topic/CStringData::pStringMgr.md) 所用的 `IAtlStringMgr` 介面的這個欄位按處理這個字串資料。  當 `CStringT` 需要重新配置或釋放字串緩衝區它呼叫重新配置或釋放這個介面的方法，傳遞做為 `CStringData` 結構做為參數。  當配置在字串處理常式中 `CStringData` 結構，您必須將這個欄位指向自訂字串處理常式。  
  
-   [nDataLength](../Topic/CStringData::nDataLength.md) 這個欄位包含不同之處在於結束的 null 緩衝區儲存字串的目前邏輯長度。  在字串的長度變更時，`CStringT` 更新這個欄位。  當配置 `CStringData` 結構時，您的字串處理常式必須設定這個欄位為零。  當重新 `CStringData` 結構時，您的自訂字串處理常式必須離開此欄位未變更。  
  
-   [nAllocLength](../Topic/CStringData::nAllocLength.md) 這個欄位會包含在這個字串緩衝區可以儲存，而不用重新指定字元的最大數目 \(除了結束的 null\)。  每當 `CStringT` 需要加入字串，其邏輯長度會先檢查這個欄位會決定在緩衝區空間不足。  如果檢查失敗， `CStringT` 對您的重新配置緩衝區的自訂字串處理常式中。  當配置或重新 `CStringData` 結構，您必須將欄位加入至 **nChars** 參數需要至少字元的數目。 [IAtlStringMgr::Allocate](../Topic/IAtlStringMgr::Allocate.md) 或 [IAtlStringMgr::Reallocate](../Topic/IAtlStringMgr::Reallocate.md)。  如果小於要求在緩衝區的更多空間，您可以將這個值反映的實際可用的空間。  在中，則它必須呼叫回字串處理常式重新配置緩衝區之前，這可讓 `CStringT` 成長字串填滿整個配置的空間。  
  
-   [nRefs](../Topic/CStringData::nRefs.md) 這個欄位包含字串緩衝區的目前參考計數。  如果值為，則 `CStringT` 單一執行個體使用緩衝區。  此外，這個執行個體允許讀取和修改緩衝區的內容。  如果值大於一， `CStringT` 多個執行個體可以使用緩衝區。  由於字元緩衝區是共用的， `CStringT` 執行個體只能讀取緩衝區的內容。  若要修改內容， `CStringT` 先製作緩衝區。  如果的值是負數， `CStringT` ，只有一個執行個體使用緩衝區。  在這種情況下，緩衝區會被視為已鎖定。  當 `CStringT` 執行個體不使用時鎖定的緩衝區 `CStringT` 其他執行個體可能會共用緩衝區。  不過，這些執行個體在作業內容之前建立緩衝區的複本。  此外，使用鎖定的緩衝區的 `CStringT` 執行個體不會嘗試共用其他執行個體 `CStringT` 緩衝區指派給它。  在這種情況下， `CStringT` 執行個體複製到另一個字串寫入鎖定的緩衝區。  
  
     當配置 `CStringData` 結構，您必須將  欄位會反映出共用時的型別允許該緩衝區。  對於大部分的實作，將此值設定為一。  這允許共用行為通常的複本在寫入。  不過，在中，如果您的資料處理常式不支援共用字串緩衝區，請將這個欄位為鎖定的狀態。  這會強制 `CStringT` 用於配置它 `CStringT` 執行個體才會使用這個緩衝區。  
  
## 請參閱  
 [Memory Management with CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)