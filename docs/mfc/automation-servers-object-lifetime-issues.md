---
title: "Automation 伺服程式：物件存留期問題 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Automation 伺服程式, 物件存留期"
  - "存留期, Automation 伺服程式"
  - "物件 [C++], 存留期"
  - "伺服器, Automation 的存留期"
ms.assetid: 342baacf-4015-4a0e-be2f-321424f1cb43
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Automation 伺服程式：物件存留期問題
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當 Automation 用戶端建立或啟動 OLE 項目時，伺服器透過用戶端傳遞指標給該物件。  用戶端藉由呼叫 OLE 函式 [IUnknown::AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) 建立對物件的參考。  這個參考直到用戶端呼叫 [IUnknown::Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) 為止都會是有效的。\(以 MFC 程式庫的 OLE 類別撰寫的用戶端應用程式不需要建立這些呼叫；架構也是如此\)。這個 OLE 系統和伺服器可能會建立對物件的參考。  只要物件的外部參考仍然有效，伺服器不應終結物件。  
  
 架構會維護一個內部計數，計算衍生自 [CCmdTarget](../mfc/reference/ccmdtarget-class.md) 的任何伺服器物件的參考之數目。  當 Automation 用戶端或其他實體加入或釋放對物件的參考時，這個計數會更新。  
  
 當參考計數變成 0 時，架構會呼叫虛擬函式 [CCmdTarget::OnFinalRelease](../Topic/CCmdTarget::OnFinalRelease.md)。  這個函式的預設實作會呼叫 **delete** 運算子刪除這個物件。  
  
 當外部用戶端擁有對應用程式物件的參考時，MFC 程式庫會為控制應用程式行為提供額外的功能。  除了維護對每個物件的參考計數，伺服器會維護使用中物件的全域計數。  全域函式 [AfxOleLockApp](../Topic/AfxOleLockApp.md) 和 [AfxOleUnlockApp](../Topic/AfxOleUnlockApp.md) 函式會更新應用程式中使用中物件的計數。  如果這個計數為零，當使用者從系統功能表選取關閉或匯出檔案功能表時，應用程式不會結束。  相反地，應用程式的主視窗會被隱藏 \(但不會被終結\)，直到所有暫止的用戶端要求已經完成。  通常， `AfxOleLockApp` 和 `AfxOleUnlockApp` 會分別由支援 Automation 的類別之建構和解構函式呼叫。  
  
 當用戶端仍然永有對物件的參考時，有些情況會強制終止伺服器。  例如，伺服器根據的一個資源變成無法使用，造成伺服器遇到錯誤。  使用者也可以關閉包含有其他應用程式具有參考的物件之伺服器文件。  
  
 在 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)] 中，請參閱 `IUnknown::AddRef` 和 `IUnknown::Release`。  
  
## 請參閱  
 [Automation 伺服程式](../mfc/automation-servers.md)   
 [AfxOleCanExitApp](../Topic/AfxOleCanExitApp.md)