---
title: "匯出 DLL 函式進入點 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- exporting DLLs [MFC], functions
- MFC, managing state data
- state management [MFC], exported DLLs
ms.assetid: 3268666e-d24b-44f2-80e8-7c80f73b93ca
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 28ded528d584e98b704b5f2d8e6e0a379a6a11a3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="exported-dll-function-entry-points"></a>匯出的 DLL 函式進入點
DLL 的匯出函式，使用[AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state)巨集來維護適當的全域狀態時從 DLL 模組切換到呼叫應用程式的 DLL。  
  
 呼叫時，這個巨集會將 `pModuleState` (`AFX_MODULE_STATE` 結構的指標，其中包含模組的全域資料) 設定為函式所包含範圍其餘部分的有效模組狀態。 離開包含巨集的範圍之後，會自動還原前一個有效的模組狀態。  
  
 此切換達成方式是建構的執行個體**AFX_MODULE_STATE**堆疊上的類別。 在其建構函式中，這個類別會取得目前模組狀態的指標，並將其儲存在成員變數中，然後再將 `pModuleState` 設定為新的有效模組狀態。 在其解構函式中，這個類別會將儲存在其成員變數中的指標還原成有效的模組狀態。  
  
 如果您有匯出函式 (例如在 DLL 中啟動對話方塊)，則您必須將下列程式碼加入至函式的開頭：  
  
 [!code-cpp[NVC_MFCConnectionPoints#6](../mfc/codesnippet/cpp/exported-dll-function-entry-points_1.cpp)]  
  
 這會將目前的模組狀態與從傳回的狀態[AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)到目前的範圍結束為止。  
  
 如果沒有使用 `AFX_MANAGE_STATE` 巨集，就會發生在 DLL 中使用資源的問題。 根據預設，MFC 會使用主應用程式的資源控制代碼來載入資源範本。 這個範本實際上會儲存在 DLL 中。 其根本原因是 MFC 的模組狀態資訊並未由 `AFX_MANAGE_STATE` 巨集交換。 資源控制代碼是從 MFC 的模組狀態復原。 由於未切換模組狀態而導致使用錯誤的資源控制代碼。  
  
 `AFX_MANAGE_STATE` 不需要將每個函式放在 DLL 中。 例如，`InitInstance` 可以由應用程式中的 MFC 程式碼呼叫，而不需使用 `AFX_MANAGE_STATE`，因為 MFC 會在 `InitInstance` 之前將模組狀態自動位移，然後在 `InitInstance` 傳回之後再將其切換回來。 相同的情況也適用於所有訊息對應處理常式。 MFC 的標準 Dll 實際上具有特殊的主視窗程序，會自動切換模組狀態，再傳送訊息。  
  
## <a name="see-also"></a>請參閱  
 [管理 MFC 模組的狀態資料](../mfc/managing-the-state-data-of-mfc-modules.md)

