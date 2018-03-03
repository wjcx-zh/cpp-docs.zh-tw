---
title: "閒置迴圈處理 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC, background processing
- PeekMessage method [MFC], elsewhere than message loop
- PeekMessage method [MFC]
- MFC, messages
- messages [MFC], loops
- OnIdle method [MFC]
- processing [MFC], background
- idle loop processing [MFC]
- idle processing [MFC]
- threading [MFC], alternatives to multithreading
- processing, during idle loop
- processing [MFC]
- background processing [MFC]
ms.assetid: 5c7c46c1-6107-4304-895f-480983bb1e44
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: baabba60ffaf886b7a34acfbff5b923a4495fa1b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="idle-loop-processing"></a>閒置迴圈處理
許多應用程式會「在背景」進行耗時的處理。 有時候會因為效能考量而使用多執行緒進行此類工作。 執行緒會涉及額外的開發負荷，因此不建議如 MFC 會閒置時間工作等簡單的工作[OnIdle](../mfc/reference/cwinthread-class.md#onidle)函式。 本文會著重於閒置處理的部分。 如需多執行緒處理，請參閱[多執行緒主題](../parallel/multithreading-support-for-older-code-visual-cpp.md)。  
  
 某些種類的背景處理適合在使用者與應用程式沒有互動的期間完成。 在針對 Microsoft Windows 作業系統所開發的應用程式中，應用程式可以藉由將耗時的處理序分割成許多小片段來執行閒置時間處理。 每個片段之後，應用程式會產生執行控制項來使用 Windows [PeekMessage](http://msdn.microsoft.com/library/windows/desktop/ms644943)迴圈。  
  
 本文說明兩種可在應用程式中進行閒置處理的方式：  
  
-   使用**PeekMessage** MFC 的主要訊息迴圈中。  
  
-   將另一個**PeekMessage**迴圈應用程式中的其他地方。  
  
##  <a name="_core_peekmessage_in_the_mfc_message_loop"></a>MFC 訊息迴圈中的 PeekMessage  
 使用 MFC 開發的應用程式中，主要訊息迴圈中`CWinThread`類別包含呼叫的訊息迴圈[PeekMessage](http://msdn.microsoft.com/library/windows/desktop/ms644943) Win32 API。 這個迴圈也會在各個訊息之間呼叫 `OnIdle` 的 `CWinThread` 成員函式。 應用程式可以藉由覆寫 `OnIdle` 函式，在閒置時間處理這些訊息。  
  
> [!NOTE]
>  **執行**， `OnIdle`，和其他成員函式現在是類別的成員`CWinThread`而不是類別的`CWinApp`。 `CWinApp` 衍生自 `CWinThread`。  
  
 如需執行閒置處理的詳細資訊，請參閱[OnIdle](../mfc/reference/cwinthread-class.md#onidle)中*MFC 參考*。  
  
##  <a name="_core_peekmessage_elsewhere_in_your_application"></a>您的應用程式中其他位置的 PeekMessage  
 在應用程式中執行閒置處理的另一種方法包含將訊息迴圈內嵌在您的某個函式中。 這個訊息迴圈是非常類似於 MFC 的主要訊息迴圈，位於[cwinthread:: Run](../mfc/reference/cwinthread-class.md#run)。 這表示在使用 MFC 開發的應用程式中，這類迴圈必須執行許多和主要訊息迴圈相同的函式。 下列程式碼片段說明如何撰寫與 MFC 相容的訊息迴圈：  
  
 [!code-cpp[NVC_MFCDocView#8](../mfc/codesnippet/cpp/idle-loop-processing_1.cpp)]  
  
 這個嵌入在函式中的程式碼，會在需要執行閒置處理時執行迴圈。 在該迴圈內的巢狀的迴圈重複呼叫**PeekMessage**。 只要該呼叫傳回非零的值，迴圈就會呼叫 `CWinThread::PumpMessage` 執行一般訊息轉譯和分派。 雖然 `PumpMessage` 並未記載，但您可以檢查 Visual C++ 安裝的 \atlmfc\src\mfc 目錄中，ThrdCore.Cpp 檔案的原始程式碼。  
  
 一旦內部迴圈結束，外部迴圈便會搭配一個或多個對 `OnIdle` 的呼叫以執行閒置處理。 第一次呼叫是供 MFC 使用。 您可以建立其他對 `OnIdle` 的呼叫，以完成您的背景工作。  
  
 如需執行閒置處理的詳細資訊，請參閱[OnIdle](../mfc/reference/cwinthread-class.md#onidle) MFC 程式庫參考中。  
  
## <a name="see-also"></a>請參閱  
 [一般 MFC 主題](../mfc/general-mfc-topics.md)

