---
title: "CWinApp：應用程式類別 | Microsoft Docs"
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
  - "CWinApp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "應用程式類別"
  - "CWinApp 類別, CWinThread"
  - "CWinApp 類別, 多執行緒"
  - "CWinApp 類別, WinMain"
  - "CWinThread 類別, 和 CWinApp"
  - "InitApplication 方法"
  - "MFC [C++], WinMain 和"
  - "WinMain 方法"
  - "WinMain 方法, 在 MFC 中"
ms.assetid: 935822bb-d463-481b-a5f6-9719d68ed1d5
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CWinApp：應用程式類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 MFC 中的主要應用程式類別封裝應用程式的初始化、執行和終止對 Windows 作業系統的。  在架構中建立的應用程式必須具有衍生自 [CWinApp](../mfc/reference/cwinapp-class.md)的類別只能有一個物件。  在建立視窗之前，建構這個物件。  
  
 `CWinApp` ，衍生自 `CWinThread`表示主執行緒應用程式中，可能有一或多個執行緒。  在 MFC 版本， **Run**、 `InitInstance`、 `ExitInstance`和 `OnIdle` 成員函式實際上是 `CWinThread`類別。  這些函式會在這個位置，就如同 `CWinApp` 成員，因為這個討論相關物件的角色，應用程式物件而不是主執行緒。  
  
> [!NOTE]
>  您的應用程式類別撰寫要執行應用程式的主執行緒。  使用 Win32 API 函式，您也可以建立執行次要執行緒。  這些執行緒可以使用 MFC 程式庫。  如需詳細資訊，請參閱 [多線程](../parallel/multithreading-support-for-older-code-visual-cpp.md)。  
  
 與 Windows 作業系統的程式，您的架構應用程式具有 `WinMain` 函式。  在架構應用程式，不過，您不會寫入 `WinMain`。  當應用程式啟動時，類別庫提供再呼叫。  `WinMain` 執行標準的服務，例如註冊視窗類別。  然後它會呼叫應用程式物件的成員函式來初始化和執行應用程式。\(您可以透過覆寫 `CWinApp` 成員的自訂 `WinMain` 函式呼叫 `WinMain` \)。  
  
 若要初始化應用程式， `WinMain` 呼叫應用程式物件的 `InitApplication` 和 `InitInstance` 成員函式。  若要執行應用程式的訊息迴圈， `WinMain` **Run** 呼叫成員函式。  在終止時， `WinMain` 呼叫應用程式物件的 `ExitInstance` 成員函式。  
  
> [!NOTE]
>  在 MFC 程式庫與 Visual C\+\+ 提供的這個文件指示項目 **bold** 的顯示名稱。  在 `monospaced` 型別的名稱表示項目建立或覆寫。  
  
## 請參閱  
 [一般 MFC 主題](../mfc/general-mfc-topics.md)   
 [CWinApp 和 MFC 應用程式精靈](../mfc/cwinapp-and-the-mfc-application-wizard.md)   
 [可覆寫的 CWinApp 成員函式](../mfc/overridable-cwinapp-member-functions.md)   
 [特殊 CWinApp 服務](../mfc/special-cwinapp-services.md)