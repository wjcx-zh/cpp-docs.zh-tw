---
title: "多執行緒：何時使用同步類別 | Microsoft Docs"
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
  - "受控制資源的存取 [C++]"
  - "多執行緒 [C++], 同步類別"
  - "資源 [C++], 多執行緒"
  - "同步 [C++], 多執行緒"
  - "同步存取類別 [C++]"
  - "同步類別 [C++]"
  - "執行緒 [C++], 同步"
  - "執行緒 [MFC], 同步類別"
ms.assetid: 4914f54e-68ac-438f-93c9-c013455a657e
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 多執行緒：何時使用同步類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

MFC 所提供的多執行緒類別可以分成兩類：同步物件 \([CSyncObject](../../mfc/reference/csyncobject-class.md)、[CSemaphore](../../mfc/reference/csemaphore-class.md)、[CMutex](../../mfc/reference/cmutex-class.md)、[CCriticalSection](../../mfc/reference/ccriticalsection-class.md) 和 [CEvent](../../mfc/reference/cevent-class.md)\) 以及同步存取物件 \([CMultiLock](../../mfc/reference/cmultilock-class.md) 和 [CSingleLock](../../mfc/reference/csinglelock-class.md)\)。  
  
 必須控制對資源的存取以確定資源完整性的時候，就會用到同步類別。  同步存取類別用來取得這些受控制資源的存取。  本主題說明何時使用每一個類別。  
  
 若要決定應該使用哪一個同步類別，請檢視下列一系列的問題：  
  
1.  應用程式必須等候事情發生之後才能存取資源嗎 \(例如，資料必須先從通訊連接埠接收之後才能寫入至檔案\)？  
  
     如果是，請使用 `CEvent`。  
  
2.  相同應用程式內可以有一個以上的執行緒同時存取這個資源嗎 \(例如，您的應用程式允許最多五個視窗具有相同的文件上的檢視\)？  
  
     如果是，請使用 `CSemaphore`。  
  
3.  可以有一個以上的應用程式使用這個資源嗎 \(例如，資源在 DLL 中\)？  
  
     如果是，使用 `CMutex`。  
  
     如果不是，使用 `CCriticalSection`。  
  
 **CSyncObject** 絕對不會直接使用。  它是其他四個同步類別的基底類別。  
  
## 範例 1：使用三個同步類別  
 例如，取得維護帳戶之連結串列的應用程式。  這個帳戶最多允許在不同視窗中查看三個帳戶，但一次只能有一個可以被更新。  當更新帳戶時，更新的資料會經由網路傳送到資料保存。  
  
 這個範例使用全部三種同步類別。  因為同一時間它允許檢查最多三個帳戶，它使用 `CSemaphore` 來限制三個檢視物件的存取。  嘗試檢視第四個帳戶時，應用程式會等候前三個視窗其中之一關閉，否則便會失敗。  帳戶被更新時，應用程式使用 `CCriticalSection` 來確定一次只更新一個帳戶。  更新成功之後，會發送訊號到 `CEvent`，以釋放等候被發送信號之事件的執行緒。  這個執行緒會將新資料傳送到資料保存。  
  
## 範例 2：使用同步存取類別  
 選擇要使用哪一個同步存取類別則更加簡單。  如果您的應用程式只考慮單一控制資源的存取，請使用 `CSingleLock`。  如果它需要存取許多受控制資源中的一種，請使用 `CMultiLock`。  範例 1 中可能會使用 `CSingleLock`，因為在每個情況中的任何特定時間內只需要一種資源。  
  
 如需如何使用同步類別的詳細資訊，請參閱[多執行緒：如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  如需同步處理的詳細資訊，請參閱 [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)] 中的[同步處理](http://msdn.microsoft.com/library/windows/desktop/ms686353)。  如需 MFC 多執行緒支援的詳細資訊，請參閱[使用 C\+\+ 和 MFC 進行多執行緒處理](../../parallel/multithreading-with-cpp-and-mfc.md)。  
  
## 請參閱  
 [使用 C\+\+ 和 MFC 進行多執行緒處理](../../parallel/multithreading-with-cpp-and-mfc.md)