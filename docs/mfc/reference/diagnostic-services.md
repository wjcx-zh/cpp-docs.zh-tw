---
title: "診斷服務 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "診斷, 診斷函式和變數"
  - "診斷, 診斷服務"
  - "診斷, 一般 MFC 的清單"
  - "診斷函式和變數"
  - "診斷巨集"
  - "診斷巨集, 一般 MFC 的清單"
  - "診斷服務"
  - "診斷, 診斷函式和變數"
  - "診斷, 診斷服務"
  - "診斷, 一般 MFC 的清單"
  - "一般診斷函式和變數"
  - "MFC 中的一般診斷巨集"
  - "MFC, 診斷服務"
  - "MFC 中的物件診斷函式"
  - "服務, 診斷"
ms.assetid: 8d78454f-9fae-49c2-88c9-d3fabd5393e8
caps.latest.revision: 20
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 診斷服務
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

MFC 程式庫提供許多診斷服務，可讓您更輕鬆地對程式進行偵錯。 這些診斷服務包含巨集和全域函式，可讓您追蹤程式的記憶體配置、在執行階段傾印物件的內容，以及在執行階段列印偵錯訊息。 診斷服務的巨集和全域函式可分為下列分類：  
  
-   一般診斷巨集  
  
-   一般診斷函式和變數  
  
-   物件診斷函式  
  
 這些巨集和函式都可以在 MFC 的偵錯和發行版本中，供所有衍生自 `CObject` 的類別使用。 不過，在發行版本中只能使用 `DEBUG_NEW` 和 **VERIFY**。  
  
 在偵錯程式庫中，所有配置的記憶體區塊都會以一系列「保護位元組」\(Guard Byte\) 來提供支援。 如果這些位元組受到錯誤記憶體寫入的干擾，則診斷常式可能會回報問題。 如果您在實作檔中包含此行：  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/CPP/diagnostic-services_1.cpp)]  
  
 則所有對 **new** 的呼叫都會儲存發生記憶體配置的檔案名稱和行號。[CMemoryState::DumpAllObjectsSince](../Topic/CMemoryState::DumpAllObjectsSince.md) 函式會顯示這項額外的資訊，讓您找出記憶體流失的問題。 如需診斷輸出的其他資訊，另請參閱 [CDumpContext](../../mfc/reference/cdumpcontext-class.md) 類別。  
  
 此外，C 執行階段程式庫也支援一組可用來偵錯應用程式的診斷函式。 如需詳細資訊，請參閱＜執行階段程式庫參考＞中的[偵錯常式](../../c-runtime-library/debug-routines.md)。  
  
### MFC 一般診斷巨集  
  
|||  
|-|-|  
|[ASSERT](../Topic/ASSERT%20\(MFC\).md)|如果指定的運算式在程式庫的偵錯版本中評估為 **FALSE**，則會列印訊息，再中止程式。|  
|[ASSERT\_KINDOF](../Topic/ASSERT_KINDOF.md)|測試某物件是屬於指定類別，還是屬於該類別的衍生類別。|  
|[ASSERT\_VALID](../Topic/ASSERT_VALID.md)|藉由呼叫物件的 `AssertValid` 成員函式來測試其內部有效性，通常會覆寫自 `CObject`。|  
|[DEBUG\_NEW](../Topic/DEBUG_NEW.md)|提供偵錯模式中所有物件配置的檔案名稱和行號，以協助找出記憶體流失的問題。|  
|[DEBUG\_ONLY](../Topic/DEBUG_ONLY.md)|類似於 **ASSERT**，但不會測試運算式的值；適用於只能在偵錯模式中執行的程式碼。|  
|[TRACE](../Topic/TRACE.md)|提供此程式庫之偵錯版本中類似 `printf` 的功能。|  
|[VERIFY](../Topic/VERIFY.md)|類似於 **ASSERT**，但不僅會評估此程式庫之發行版本中的運算式，也會評估偵錯版本中的運算式。|  
  
### MFC 一般診斷變數和函式  
  
|||  
|-|-|  
|[afxDump](../Topic/afxDump%20\(CDumpContext%20in%20MFC\).md)|全域變數，可將 [CDumpContext](../../mfc/reference/cdumpcontext-class.md) 資訊傳送至偵錯工具輸出視窗或偵錯終端機。|  
|[afxMemDF](../Topic/afxMemDF.md)|全域變數，可控制偵錯記憶體配置器的行為。|  
|[AfxCheckError](../Topic/AfxCheckError.md)|全域變數，可用來測試所傳遞的 **SCODE** 以查看其是否為錯誤；如果是，則擲回適當的錯誤。|  
|[AfxCheckMemory](../Topic/AfxCheckMemory.md)|檢查目前配置之所有記憶體的完整性。|  
|[AfxDump](../Topic/AfxDump%20\(MFC\).md)|如果在偵錯工具中呼叫，則會一面進行偵錯，一面傾印物件的狀態。|  
|[AfxDumpStack](../Topic/AfxDumpStack.md)|產生目前堆疊的映像。 這個函式一律會以靜態方式連結。|  
|[AfxEnableMemoryLeakDump](../Topic/AfxEnableMemoryLeakDump.md)|啟用記憶體流失傾印。|  
|[AfxEnableMemoryTracking](../Topic/AfxEnableMemoryTracking.md)|開啟和關閉記憶體追蹤。|  
|[AfxIsMemoryBlock](../Topic/AfxIsMemoryBlock.md)|確認已適當地配置記憶體區塊。|  
|[AfxIsValidAddress](../Topic/AfxIsValidAddress.md)|確認記憶體位址範圍落在程式的範圍內。|  
|[AfxIsValidString](../Topic/AfxIsValidString.md)|判斷字串指標是否有效。|  
|[AfxSetAllocHook](../Topic/AfxSetAllocHook.md)|允許對每個記憶體配置呼叫函式。|  
  
### MFC 物件診斷函式  
  
|||  
|-|-|  
|[AfxDoForAllClasses](../Topic/AfxDoForAllClasses.md)|針對所有可支援執行階段類型檢查的 `CObject` 衍生類別執行指定的函式。|  
|[AfxDoForAllObjects](../Topic/AfxDoForAllObjects.md)|針對所有已透過 **new** 來配置的 `CObject` 衍生物件執行指定函式。|  
  
## 請參閱  
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)