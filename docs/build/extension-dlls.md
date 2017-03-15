---
title: "擴充 DLL | Microsoft Docs"
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
  - "afxdll"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AFXDLL 程式庫"
  - "DLL [C++], 擴充功能"
  - "擴充 DLL [C++]"
  - "擴充 DLL [C++], 關於擴充 DLL"
  - "記憶體 [C++], DLL"
  - "MFC DLL [C++], 擴充 DLL"
  - "MFC 擴充 DLL [C++]"
  - "資源共用 [C++]"
  - "共用的 DLL 版本 [C++]"
  - "共用資源 [C++]"
ms.assetid: f69ac3d4-e474-4b1c-87a1-6738843a135c
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 擴充 DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 擴充 DLL 通常是實作衍生自現有 MFC 程式庫類別的重複使用類別之 DLL。  
  
 MFC 擴充 DLL 有下列功能和需求：  
  
-   用戶端可執行檔必須是在 **\_AFXDLL** 已定義的情況下編譯之 MFC 應用程式。  
  
-   擴充 DLL 也可以由動態連結至 MFC 的標準 DLL 來使用。  
  
-   擴充 DLL 應該以定義的 `_AFXEXT` 來編譯。  這會強迫定義 **\_AFXDLL**，並確保會從 MFC 標頭檔 \(Header File\) 提取適當的宣告。  這也確保在建置 DLL 時，**AFX\_EXT\_CLASS** 會定義為 **\_\_declspec\(dllexport\)** \(如果您使用這個巨集來宣告擴充 DLL 的類別，就會需要此動作\)。  
  
-   擴充 DLL 不應該對於衍生自 `CWinApp` 的類別執行個體化，但是應該要根據用戶端應用程式 \(或 DLL\) 來提供這個物件。  
  
-   然而，擴充 DLL 應該提供 `DllMain` 函式，而且在那裡執行任何所需的初始化。  
  
 擴充 DLL 是使用 MFC 的動態連結程式庫版本 \(也稱為 MFC 的共用版本\) 所建置的。  只有以 MFC 的共用版本所建置的 MFC 可執行檔 \(應用程式或標準 DLL\) 可以使用擴充 DLL。  用戶端應用程式和擴充 DLL 必須使用相同的 MFCx0.DLL 版本。  使用擴充 DLL，您可以從 MFC 衍生新的自訂類別，然後將這個 MFC 的擴充版本提供給呼叫您 DLL 的應用程式。  
  
 擴充 DLL 也可以用來在應用程式和 DLL 之間傳遞 MFC 衍生物件。  與傳遞物件關聯的成員函式存在於建立物件的模組裡。  因為使用共用的 MFC DLL 版本時會適當地匯出這些函式，所以您可以在應用程式和它所載入的擴充 DLL 之間自由地傳遞 MFC 或 MFC 衍生物件指標。  
  
 MFC 擴充 DLL 使用 MFC 共用版本的方式與應用程式使用 MFC 共用 DLL 版本相同，但仍有一些需要考慮的地方：  
  
-   沒有 `CWinApp` 衍生物件。  這個 DLL 必須與用戶端應用程式的 `CWinApp` 衍生物件一起使用。  這是說用戶端應用程式擁有主要的訊息幫浦、閒置 \(Idle\) 迴圈等等。  
  
-   它會在其 `DllMain` 函式呼叫 `AfxInitExtensionModule`。  應該要檢查這個函式的傳回值。  如果 `AfxInitExtensionModule` 傳回零值，您的 `DllMain` 函式便會傳回 0。  
  
-   如果擴充 DLL 要將 `CRuntimeClass` 物件或資源匯出至應用程式，則會在初始化時建立 **CDynLinkLibrary** 物件。  
  
 4.0 版之前的 MFC 會稱這類型的 DLL 為 AFXDLL。  AFXDLL 可以參考到建置 DLL 時所定義的 **\_AFXDLL** 前置處理器 \(Preprocessor\) 符號。  
  
 MFC 共用版本的匯入程式庫是根據 [MFC DLL 命名慣例](../build/naming-conventions-for-mfc-dlls.md)中描述的慣例來命名。  Visual C\+\+ 提供 MFC DLL 的預先建置版本，加上您可以使用並且與您的應用程式一起散佈的許多非 MFC DLL。  這些資訊都記錄在 Redist.txt 中，此檔案安裝於 Program Files\\Microsoft Visual Studio 資料夾。  
  
 如果您是使用 .def 檔匯出，請將下列程式碼置於標頭檔的開頭和結尾：  
  
```  
#undef AFX_DATA  
#define AFX_DATA AFX_EXT_DATA  
// <body of your header file>  
#undef AFX_DATA  
#define AFX_DATA  
```  
  
 這四行程式碼會確保您的程式碼正確地編譯為擴充 DLL。  遺漏這四行可能會導致 DLL 不正確編譯或連結。  
  
 如果您需要在 MFC DLL 往返傳遞 MFC 或 MFC 衍生物件指標，這個 DLL 就必須是擴充 DLL。  與傳遞物件關聯的成員函式存在於建立物件的模組裡。  因為使用共用的 MFC DLL 版本時會適當地匯出這些函式，所以您可以在應用程式和它所載入的擴充 DLL 之間自由地傳遞 MFC 或 MFC 衍生物件指標。  
  
 由於 C\+\+ 函式名稱改變 \(Name Mangling\) 和匯出問題，擴充 DLL 的匯出清單在相同 DLL 和不同平台之 DLL 的偵錯版本和正式版本之間可能會不同。  正式版本的 MFCx0.DLL 有大約 2,000 個匯出的進入點；偵錯版本的 MFCx0D.DLL 有大約 3,000 個匯出的進入點。  
  
## 記憶體管理  
 載入至用戶端應用程式位址空間的 MFCx0.dll 和所有的擴充 DLL，會使用相同的記憶體配置器 \(Allocator\)、資源載入以及其他的 MFC 全域狀態，就如同在同一個應用程式中一樣。  因為非 MFC DLL 程式庫和標準 DLL 所做的正好相反，並且讓每個 DLL 配置在它自己的記憶體集區之外，這是很重要的。  
  
 如果擴充 DLL 會配置記憶體，則該記憶體便可以自由地與其他應用程式配置的物件相互摻雜。  同時，如果動態連結至 MFC 的應用程式損毀，作業系統的保護會維持共用 DLL 之其他 MFC 應用程式的完整性。  
  
 同樣的，其他的全域 MFC 狀態 \(例如要載入資源的目前可執行檔\)，也會在用戶端應用程式和所有 MFC 擴充 DLL 之間以及 MFCx0.dll 本身中共用。  
  
## 共用資源和類別  
 匯出資源是經由資源清單來完成。  每個應用程式都會包含 **CDynLinkLibrary** 物件的單一連結清單。  尋找資源時，大多數載入資源的標準 MFC 實作會先在目前資源模組 \(`AfxGetResourceHandle`\) 搜尋，並在找不到資源時，瀏覽 **CDynLinkLibrary** 物件的清單來嘗試載入要求的資源。  
  
 瀏覽清單時會出現速度略微緩慢和需要管理資源 ID 範圍等缺點。  優點是連結至數個擴充 DLL 的用戶端應用程式可以使用任何 DLL 提供的資源，而不需要指定 DLL 執行個體控制代碼 \(Instance Handle\)。  `AfxFindResourceHandle` 是 API，用來逐一查看資源清單以尋找指定的符合項目。  這個 API 會使用到資源的名稱、類型，並傳回第一次發現時 \(或 NULL\) 的資源控制代碼。  
  
 如果您不要瀏覽清單，並且只要從特定地方載入資源，使用 `AfxGetResourceHandle` 和 `AfxSetResourceHandle` 函式來儲存舊的控制代碼，並且設定新控制代碼。  請確定在傳回用戶端應用程式之前要還原舊的資源控制代碼。  如需使用這種方法來明確載入功能表的範例，請參閱 MFC 範例 [DLLHUSK](http://msdn.microsoft.com/zh-tw/dfcaa6ff-b8e2-4efd-8100-ee3650071f90) 中的 Testdll2.cpp。  
  
 MFC 物件動態建立給定的 MFC 名稱會很相似。  MFC 物件還原序列化 \(Deserialization\) 機制必須登錄所有 `CRuntimeClass` 物件，這樣它就可以動態建立根據先前儲存的所需 C\+\+ 物件型別來進行重建。  
  
 在 MFC [DLLHUSK](http://msdn.microsoft.com/zh-tw/dfcaa6ff-b8e2-4efd-8100-ee3650071f90) 範例的例子裡，此清單看起來會像這樣：  
  
```  
head ->   DLLHUSK.EXE   - or -   DLLHUSK.EXE  
               |                      |  
          TESTDLL2.DLL           TESTDLL2.DLL  
               |                      |  
          TESTDLL1.DLL           TESTDLL1.DLL  
               |                      |  
           MFCOxxD.DLL                |  
               |                      |  
           MFCDxxD.DLL                |  
               |                      |  
            MFCxxD.DLL            MFCxx.DLL  
```  
  
 其中 *xx* 是版本號碼；例如，42 表示 4.2 版。  
  
 MFCxx.dll 通常是在資源和類別清單的最後面。  MFCxx.dll 包含所有的標準 MFC 資源，包括所有標準命令 ID 的提示字串 \(Prompt String\)。  將其置於清單的最後面，可以讓 DLL 和用戶端應用程式不具有自己的標準 MFC 資源複本，而是依賴 MFCxx.dll 的共用資源。  
  
 將所有 DLL 的資源和類別名稱合併到用戶端應用程式的命名空間，會產生向您要求注意指定的 ID 或名稱的缺點。  
  
 [DLLHUSK](http://msdn.microsoft.com/zh-tw/dfcaa6ff-b8e2-4efd-8100-ee3650071f90) 範例會使用多個標頭檔來管理共用資源命名空間。  
  
 如果您的 MFC 擴充 DLL 必須為每一個應用程式維護其他資料，您可以由 **CDynLinkLibrary** 衍生新類別，並且使用 `DllMain` 來建立。  該 DLL 會在執行時檢查 **CDynLinkLibrary** 物件目前的應用程式清單，找出特殊擴充 DLL 的物件。  
  
### 您想要執行甚麼工作？  
  
-   [初始化擴充 DLL](../build/initializing-extension-dlls.md)  
  
### 您還想知道關於哪些方面的詳細資訊？  
  
-   [使用共用資源檔的提示](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)  
  
-   [MFC 的 DLL 版本](../mfc/tn033-dll-version-of-mfc.md)  
  
-   [靜態連結至 MFC 的標準 DLL](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [動態連結至 MFC 的標準 DLL](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [在標準 DLL 中使用資料庫、OLE 和通訊端擴充 DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
## 請參閱  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)