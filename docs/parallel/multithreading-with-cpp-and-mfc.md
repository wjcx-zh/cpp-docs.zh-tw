---
title: "使用 C++ 和 MFC 進行多執行緒處理 | Microsoft Docs"
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
  - "CWinThread 類別, 目的"
  - "MFC [C++], 多執行緒"
  - "多執行緒 [C++], MFC"
  - "同步 [C++], 多執行緒"
  - "同步類別 [C++]"
  - "執行緒 [C++], MFC"
  - "執行緒 [MFC]"
  - "執行緒 [MFC], 關於執行緒"
  - "使用者介面執行緒 [C++]"
  - "背景工作執行緒 [C++]"
ms.assetid: 979605f8-3988-44b5-ac9c-b8cce7fcce14
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 C++ 和 MFC 進行多執行緒處理
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft Foundation Class \(MFC\) 程式庫提供多執行緒應用程式 \(Multithreaded Application\) 的支援。  這個主題會描述處理序和執行緒，以及多執行緒的 MFC 方法。  
  
 處理序是應用程式的執行個體。  例如，當您在 \[記事本\] 圖示上按兩下時，您會啟動執行記事本的處理序。  
  
 執行緒是在處理序內的執行路徑。  當您啟動記事本時，作業系統會建立處理序並且開始執行該處理序的主執行緒。  當這個執行緒結束時，處理序也會結束。  這個主要執行緒是藉由啟始程式碼 \(Startup Code\) 以函式位址的形式提供給作業系統。  通常，它是提供的 **main** 或 `WinMain` 函式的位址。  
  
 如果想要的話，您可以在應用程式裡建立額外的執行緒。  當您不想讓使用者等候時，您可能想要利用這種方式來處理背景或維護工作。  MFC 應用程式中所有的執行緒都由 [CWinThread](../mfc/reference/cwinthread-class.md) 物件來表示。  在大多數的情況下，您甚至不需要明確的建立這些物件，而以呼叫為您建立 `CWinThread` 物件的架構 Helper 函式 [AfxBeginThread](../Topic/AfxBeginThread.md) 來代替。  
  
 MFC 會分辨兩種類型的執行緒：使用者介面執行緒和背景工作執行緒 \(Worker Thread\)。  使用者介面執行緒通常是用來處理使用者輸入並回應使用者所產生的事件和訊息。  背景工作執行緒通常是用來完成不需要使用者輸入的工作，例如重新計算。  Win32 API 不能分辨執行緒的類型；它只需要知道執行緒的開始位址，就可以開始執行執行緒。  MFC 會在使用者介面中，為事件提供訊息幫浦 \(Message Pump\)，藉此特別處理使用者介面執行緒。  `CWinApp` 是使用者介面執行緒物件的範例，因為它衍生自 `CWinThread` 並處理使用者所產生的事件和訊息。  
  
 在一個以上的執行緒可能要存取相同物件的情況中，應該要特別注意。  [多執行緒：程式設計提示](../parallel/multithreading-programming-tips.md)說明您可用來處理在這些情況中可能發生的問題的技術。  [多執行緒：如何使用同步類別](../parallel/multithreading-how-to-use-the-synchronization-classes.md)說明如何使用可用來同步處理從多重執行緒到單一物件之存取的類別。  
  
 因為您必須確定一次不能有一個以上的執行緒存取物件，所以撰寫和偵錯多執行緒程式設計會相當複雜並難以處理。  多執行緒主題沒有教授多執行緒程式設計的基本概念，只有教授如何在您的多執行緒程式中使用 MFC。  在 Visual C\+\+ 裡的多執行緒 MFC 範例會示範幾種 MFC 沒有包含的多執行緒加入功能 \(Adding Functionality\) 和 Win32 API，不過它們只是做為起點。  
  
 如需作業系統如何處理處理序和執行緒的詳細資訊，請參閱 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] 中的[處理序和執行緒](http://msdn.microsoft.com/library/windows/desktop/ms684841)。  
  
 如需 MFC 多執行緒支援的詳細資訊，請參閱下列主題：  
  
-   [多執行緒：建立使用者介面執行緒](../parallel/multithreading-creating-user-interface-threads.md)  
  
-   [多執行緒：建立背景工作執行緒](../parallel/multithreading-creating-worker-threads.md)  
  
-   [多執行緒：如何使用同步類別](../parallel/multithreading-how-to-use-the-synchronization-classes.md)  
  
-   [多執行緒：結束執行緒](../parallel/multithreading-terminating-threads.md)  
  
-   [多執行緒：程式設計提示](../parallel/multithreading-programming-tips.md)  
  
-   [多執行緒：何時使用同步類別](../parallel/multithreading-when-to-use-the-synchronization-classes.md)  
  
## 請參閱  
 [舊版程式碼的多執行緒支援 \(Visual C\+\+\)](../parallel/multithreading-support-for-older-code-visual-cpp.md)