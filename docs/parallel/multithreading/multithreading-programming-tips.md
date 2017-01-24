---
title: "多執行緒：程式設計提示 | Microsoft Docs"
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
  - "存取控制 [C++], 多執行緒"
  - "通訊 [C++], 執行緒之間"
  - "關鍵區段 [C++]"
  - "控制代碼對應 [C++]"
  - "多執行緒 [C++], 程式設計提示"
  - "非 MFC 執行緒 [C++]"
  - "物件 [C++], 多個執行緒和"
  - "程式設計 [C++], 多執行緒"
  - "同步 [C++], 多執行緒"
  - "執行緒 [C++], 最佳作法"
  - "執行緒 [MFC], 程式設計提示"
  - "疑難排解 [C++], 多執行緒"
  - "Windows 控制代碼對應 [C++]"
ms.assetid: ad14cc70-c91c-4c24-942f-13a75e58bf8a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 多執行緒：程式設計提示
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

多執行緒應用程式在存取資料時需要比單一執行緒應用程式更加小心。  因為在多重執行緒應用程式中執行的多重、獨立路徑會同時使用，演算法、資料或兩者都必須知道同一時間可能會有一個以上的執行緒在使用資料。  這個主題會說明在使用 Microsoft Foundation Class \(MFC\) 程式庫進行多執行緒應用程式的程式設計時，用來避免可能問題的各種技術。  
  
-   [從多個執行緒存取物件](#_core_accessing_objects_from_multiple_threads)  
  
-   [從非 MFC 執行緒存取 MFC 物件](#_core_accessing_mfc_objects_from_non.2d.mfc_threads)  
  
-   [Windows 處理常式對應](#_core_windows_handle_maps)  
  
-   [執行緒之間的通訊](#_core_communicating_between_threads)  
  
##  <a name="_core_accessing_objects_from_multiple_threads"></a> 從多個執行緒存取物件  
 由於大小和效能因素，MFC 物件在物件層級上不是安全執行緒，只有在類別層級上才是。  這表示您可以擁有兩個操作兩個不同的 `CString` 物件之分開的執行緒，而不是兩個操作相同的 `CString` 物件的執行緒。  如果您一定要擁有操作相同的物件的多個執行緒，請使用適當的 Win32 同步作業機制 \(例如，關鍵區段\) 來保護這種存取。  如需關鍵區段 \(Critical Section\) 和其他相關物件的詳細資訊，請參閱 [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)] 中的[同步處理](http://msdn.microsoft.com/library/windows/desktop/ms686353)。  
  
 類別程式庫在內部使用關鍵區段來保護全域資料結構，例如偵錯記憶體配置所使用的資料結構。  
  
##  <a name="_core_accessing_mfc_objects_from_non.2d.mfc_threads"></a> 從非 MFC 執行緒存取 MFC 物件  
 如果您擁有不是使用 [CWinThread](../../mfc/reference/cwinthread-class.md) 物件來建立執行緒的多執行緒應用程式，您不能從該執行緒存取其他的 MFC 物件。  換句話說，如果您要從輔助執行緒存取任何的 MFC 物件，就必須使用在[多執行緒：建立使用者介面執行緒](../../parallel/multithreading-creating-user-interface-threads.md)或[多執行緒：建立背景工作執行緒](../../parallel/multithreading-creating-worker-threads.md)中所說明的其中一個方法來建立該執行緒。  這些方法是唯一允許類別程式庫初始化處理多執行緒應用程式必要的內部變數之方法。  
  
##  <a name="_core_windows_handle_maps"></a> Windows 處理常式對應  
 根據一般規則，執行緒只能存取它所建立的 MFC 物件。  這是因為暫時和永久 Windows 處理常式對應是保存在執行緒區域儲存中，以協助維持不被多重執行緒同時存取。  例如，背景工作執行緒不能執行計算，然後呼叫文件的 `UpdateAllViews` 成員函式，修改包含新資料的檢視之視窗。  這根本不會有影響，因為從 `CWnd` 物件到 `HWND` 的對應對主執行緒而言是區域性的。  這表示一個執行緒可能擁有從 Windows 處理常式到 C\+\+ 物件的對應，但是另一個執行緒可能將相同的處理常式對應到不同的 C\+\+ 物件。  在一個執行緒中所作的變更不會反映在另一個執行緒中。  
  
 有許多的方法可以避免這種問題。  第一種是將個別的處理常式 \(例如 `HWND`\) 而不是 C\+\+ 物件傳送到背景工作執行緒。  然後背景工作執行緒藉著呼叫適當的 `FromHandle` 成員函式，將這些物件加入至其暫時的對應。  您也可以藉著呼叫 **Attach** 將物件加入至執行緒的永久對應，然而只有在您保證物件會比執行緒存在更久時才可這麼做。  
  
 另一個方法是建立對應到您的背景工作執行緒將會執行之不同工作的新使用者定義訊息，並使用 **::PostMessage** 將這些訊息張貼在應用程式的主視窗。  這種通訊方法類似於兩個不同應用程式的轉換，除了兩個執行緒是在相同的位址空間中執行。  
  
 如需處理常式對應的詳細資訊，請參閱[技術提示 3](../../mfc/tn003-mapping-of-windows-handles-to-objects.md)。  如需執行緒區域儲存區的詳細資訊，請參閱 [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)] 中的[執行緒區域儲存區](http://msdn.microsoft.com/library/windows/desktop/ms686749)和[使用執行緒區域儲存區](http://msdn.microsoft.com/library/windows/desktop/ms686991)。  
  
##  <a name="_core_communicating_between_threads"></a> 執行緒之間的通訊  
 MFC 提供許多類別，這些類別允許執行緒同步物件的存取，以維護執行緒安全性。  在[多執行緒：如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)和[多執行緒：何時使用同步類別](../../parallel/multithreading-when-to-use-the-synchronization-classes.md)中說明了這些類別的用法。  如需這些物件的詳細資訊，請參閱在 [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)] 中的[同步處理](http://msdn.microsoft.com/library/windows/desktop/ms686353)。  
  
## 請參閱  
 [使用 C\+\+ 和 MFC 進行多執行緒處理](../../parallel/multithreading-with-cpp-and-mfc.md)