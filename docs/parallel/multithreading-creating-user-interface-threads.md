---
title: "多執行緒：建立使用者介面執行緒 | Microsoft Docs"
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
  - "CREATE_SUSPENDED"
  - "SECURITY_ATTRIBUTES"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "多執行緒 [C++], 使用者介面執行緒"
  - "執行緒 [C++], 建立執行緒"
  - "執行緒 [C++], 使用者介面執行緒"
  - "執行緒 [MFC], 使用者介面執行緒"
  - "使用者介面執行緒 [C++]"
ms.assetid: 446925c1-db59-46ea-ae5b-d5ae5d5b91d8
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 多執行緒：建立使用者介面執行緒
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用者介面執行緒通常用來處理使用者輸入和回應與執行緒沒有關係之執行應用程式其他部分的使用者事件。  主要的應用程式執行緒 \(在 `CWinApp` 衍生類別中提供\) 已經為您建立並且啟動。  這個主題說明建立額外使用者介面執行緒的必須步驟。  
  
 建立使用者介面執行緒時您必須要做的第一件事，是從 [CWinThread](../mfc/reference/cwinthread-class.md) 衍生類別。  您必須使用 [DECLARE\_DYNCREATE](../Topic/DECLARE_DYNCREATE.md) 和 [IMPLEMENT\_DYNCREATE](../Topic/IMPLEMENT_DYNCREATE.md) 巨集來宣告和實作這個類別。  這個類別必須覆寫一些函式，而且還可以覆寫其他的函式。  這些函式和它們的功能會在下表中說明。  
  
### 在建立使用者介面執行緒時要覆寫的函式  
  
|功能|用途|  
|--------|--------|  
|[ExitInstance](../Topic/CWinThread::ExitInstance.md)|執行緒結束時會執行清除。  通常覆寫。|  
|[InitInstance](../Topic/CWinThread::InitInstance.md)|執行執行緒執行個體 \(Instance\) 初始化。  必須被覆寫。|  
|[OnIdle](../Topic/CWinThread::OnIdle.md)|執行執行緒特定的閒置 \(Idle\) 時間處理。  通常不覆寫。|  
|[PreTranslateMessage](../Topic/CWinThread::PreTranslateMessage.md)|在訊息分派到 **TranslateMessage** 和 **DispatchMessage** 之前篩選它們。  通常不覆寫。|  
|[ProcessWndProcException](../Topic/CWinThread::ProcessWndProcException.md)|攔截由執行緒的訊息和命令列處理常式所擲回的未處理例外狀況。  通常不覆寫。|  
|[執行](../Topic/CWinThread::Run.md)|執行緒的控制函式。  包含訊息幫浦 \(Message Pump\)。  幾乎不覆寫。|  
  
 MFC 提供兩種 `AfxBeginThread` 參數多載版本：只能建立背景工作執行緒的版本，以及可以建立使用者介面執行緒或背景工作執行緒的版本。  若要啟動您的使用介面執行緒，請呼叫第二種多載 [AfxBeginThread](../Topic/AfxBeginThread.md)，並提供下列資訊：  
  
-   衍生自 `CWinThread` 之類別的 [RUNTIME\_CLASS](../Topic/RUNTIME_CLASS.md)。  
  
-   \(選擇項\) 想要的優先權等級。  預設值是一般優先權。  如需可用的優先權層級，請參閱 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] 中的 [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277)。  
  
-   \(選擇項\) 想要的執行緒堆疊大小。  預設為與建立的執行緒堆疊大小相同。  
  
-   \(選擇項\) **CREATE\_SUSPENDED** 如果您要將執行緒建立在暫停狀態。  預設值為 0，或是正常啟動執行緒。  
  
-   \(選擇項\) 想要的安全屬性。  預設為與父執行緒相同的存取。  如需這個安全資訊格式的詳細資訊，請參閱 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] 中的 [SECURITY\_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560)。  
  
 `AfxBeginThread` 會為您做大部分的工作。  它會為您的類別建立新物件，用您所提供的資訊將它初始化，並且呼叫 [CWinThread::CreateThread](../Topic/CWinThread::CreateThread.md) 來開始執行執行緒。  整個程序都會進行檢查，確保建立的任何部分萬一失敗時，所有物件都會適當地解除配置。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [多執行緒：結束執行緒](../parallel/multithreading-terminating-threads.md)  
  
-   [多執行緒：建立背景工作執行緒](../parallel/multithreading-creating-worker-threads.md)  
  
-   [\<caps:sentence id\="tgt49" sentenceid\="d446961ca833a037f83b141ec4859428" class\="tgtSentence"\>處理序和執行緒\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms684841)  
  
## 請參閱  
 [使用 C\+\+ 和 MFC 進行多執行緒處理](../parallel/multithreading-with-cpp-and-mfc.md)