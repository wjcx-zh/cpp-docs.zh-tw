---
title: "匯出的 DLL 函式進入點 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "匯出 DLL, 函式"
  - "MFC, 管理狀態資料"
  - "狀態管理, 匯出的 DLL"
ms.assetid: 3268666e-d24b-44f2-80e8-7c80f73b93ca
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 匯出的 DLL 函式進入點
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如需 DLL 的匯出函式轉換成時，從 DLL 模組加入至呼叫的應用程式的 DLL 時，請使用 [AFX\_MANAGE\_STATE](../Topic/AFX_MANAGE_STATE.md) 巨集維護適當的全域狀態。  
  
 呼叫時，這個巨集合 `pModuleState`，其中包含全域資料為模組的 `AFX_MODULE_STATE` 結構的指標，做為函式的包含範圍的其餘部分的有效的模組狀態。  當離開包含巨集的範圍之後，前一個有效的模組狀態會自動還原。  
  
 這個切換藉由建構執行個體在堆疊上 **AFX\_MODULE\_STATE** 類別來達成。  在它的建構函式，這個類別在成員變數取得指標目前模組狀態並儲存它，然後將 `pModuleState` 做為新有效的模組狀態。  在其解構函式，這個類別會還原其成員變數儲存的指標做為有效的模組狀態。  
  
 如果您有輸出函式，例如啟動 DLL 中的對話方塊的話，您必須將下列程式碼加入至函式的開頭:  
  
 [!code-cpp[NVC_MFCConnectionPoints#6](../mfc/codesnippet/CPP/exported-dll-function-entry-points_1.cpp)]  
  
 這個互換直到從目前範圍結尾的 [AfxGetStaticModuleState](../Topic/AfxGetStaticModuleState.md) 傳回的這個狀態的目前模組狀態。  
  
 如果沒有使用，資源的問題在 DLL 會發生 `AFX_MANAGE_STATE` 巨集。  根據預設， MFC 會使用主應用程式的資源控制代碼載入資源範本。  這個範本在 DLL 實際儲存。  原因是 MFC 模組狀態資訊由 `AFX_MANAGE_STATE` 巨集交換。  資源控制代碼從 MFC 模組狀態復原。  造成錯誤的資源控制代碼不使用交換模組狀態。  
  
 `AFX_MANAGE_STATE` 不需要將每個函式放在 DLL 。  例如， `InitInstance` 可以由應用程式的 MFC 程式碼呼叫，而不使用 `AFX_MANAGE_STATE` ，因為 MFC 在 `InitInstance` 然後參數之前自動將模組狀態， `InitInstance` 傳回之後。  這也適用於所有訊息對應的處理常式。  標準 DLL 實際上會在傳送任何訊息之前自動切換至模組狀態的特殊主視窗程序。  
  
## 請參閱  
 [管理 MFC 模組的狀態資料](../mfc/managing-the-state-data-of-mfc-modules.md)