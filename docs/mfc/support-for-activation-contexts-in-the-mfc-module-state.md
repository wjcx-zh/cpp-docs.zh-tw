---
title: "MFC 模組狀態的啟用內容支援 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- activation contexts [MFC]
- activation contexts [MFC], MFC support
ms.assetid: 1e49eea9-3620-46dd-bc5f-d664749567c7
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 41aa0987a6fad48e57544ebbdd708d60c000382e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="support-for-activation-contexts-in-the-mfc-module-state"></a>MFC 模組狀態的啟用內容支援
MFC 會使用由使用者模組所提供的資訊清單資源來建立啟用內容。 如需如何建立啟用內容的詳細資訊，請參閱下列主題：  
  
-   [啟用內容](http://msdn.microsoft.com/library/aa374153)  
  
-   [應用程式資訊清單](http://msdn.microsoft.com/library/aa374191)  
  
-   [組件資訊清單](http://msdn.microsoft.com/library/aa374219)  
  
## <a name="remarks"></a>備註  
 當讀取這些 Windows SDK 主題，請注意，MFC 啟用內容機制類似 Windows SDK 啟用內容，不同之處在於 MFC 不會使用 Windows SDK 啟用內容 API。  
  
 MFC 應用程式、 使用者 Dll 和 MFC 擴充 Dll 中的啟用內容是以下列方式運作：  
  
-   MFC 應用程式會使用其資訊清單資源的資源 ID 1。 在這種情況下，MFC 不建立它的啟用內容，而是使用預設的應用程式內容。  
  
-   MFC 使用者 DLL 會使用它們的資訊清單資源的資源 ID 2。 在這裡，MFC 會為每個使用者 DLL 建立啟用內容，因此，不同的使用者 DLL 可以使用相同程式庫 (例如，通用控制項程式庫) 的不同版本。  
  
-   MFC 擴充 DLL 依賴其裝載應用程式或使用者 DLL 來建立它們的啟用內容。  
  
 雖然可以使用下所述的程序修改啟用內容狀態[使用啟用內容 API](http://msdn.microsoft.com/library/aa376620)，使用 MFC 啟用內容機制有助於進行開發以 DLL 為基礎的外掛程式架構並不容易 （或無法） 之前和外部的外掛程式來個別呼叫之後，手動切換啟動狀態。  
  
 啟用內容中建立[AfxWinInit](../mfc/reference/application-information-and-management.md#afxwininit)。 其會在 `AFX_MODULE_STATE` 解構函式被終結。 啟用內容控制代碼保留在 `AFX_MODULE_STATE` 中。 (`AFX_MODULE_STATE`述[AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)。)  
  
 [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state)巨集啟用和停用的啟用內容。 `AFX_MANAGE_STATE` 可針對 MFC 靜態程式庫及 MFC DLL 來啟用，如此便可讓 MFC 程式碼在使用者 DLL 選取的適當啟用內容中執行。  
  
## <a name="see-also"></a>請參閱  
 [啟用內容](http://msdn.microsoft.com/library/aa374153)   
 [應用程式資訊清單](http://msdn.microsoft.com/library/aa374191)   
 [組件資訊清單](http://msdn.microsoft.com/library/aa374219)   
 [AfxWinInit](../mfc/reference/application-information-and-management.md#afxwininit)   
 [AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate)   
 [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state)

