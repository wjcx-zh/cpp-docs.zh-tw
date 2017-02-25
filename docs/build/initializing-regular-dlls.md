---
title: "初始化標準 DLL | Microsoft Docs"
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
  - "DLL [C++], 規則性"
  - "初始化 DLL"
  - "標準 DLL [C++], 初始化"
ms.assetid: f1f091d1-bb91-468a-94f4-3c554657b8fc
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 初始化標準 DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

因為標準 DLL 有 `CWinApp` 物件，所以它們應該在和 MFC 應用程式的相同位置執行其初始化和終止工作：即在 DLL 的 `CWinApp` 衍生類別之 `InitInstance` 和 **ExitInstance** 成員函式。  因為 MFC 會提供由 **PROCESS\_ATTACH** 和 **PROCESS\_DETACH** 的 **\_DllMainCRTStartup** 呼叫的 `DllMain` 函式，所以您應該不用撰寫自己的 `DllMain` 函式。  MFC 提供的 `DllMain` 函式會在您的 DLL 載入時呼叫 `InitInstance`，並在卸載 DLL 之前呼叫 `ExitInstance`。  
  
 標準 DLL 會在其 `InitInstance` 函式裡呼叫 [TlsAlloc](http://msdn.microsoft.com/library/windows/desktop/ms686801) 和 [TlsGetValue](http://msdn.microsoft.com/library/windows/desktop/ms686812) 來儲存多個執行緒。  這些函式允許 DLL 儲存執行緒特定的資料。  
  
 在動態連結至 MFC 的標準 DLL 中，如果您分別使用任何 MFC OLE、MFC 資料庫 \(或 DAO\) 或 MFC 通訊端 \(Socket\) 支援，則會自動連結 MFC 偵錯擴充 DLL MFCOxxD.dll、MFCDxxD.dll 和 MFCNxxD.dll \(xx 是版本編號\)。  您必須為每個用於標準 DLL 的 `CWinApp::InitInstance` 中的 DLL 呼叫下列預先定義初始化函式其中之一。  
  
|MFC 支援的類型|要呼叫的初始化函式|  
|---------------|---------------|  
|MFC OLE \(MFCOxxD.dll\)|`AfxOleInitModule`|  
|MFC 資料庫 \(MFCDxxD.dll\)|`AfxDbInitModule`|  
|MFC 通訊端 \(MFCNxxD.dll\)|`AfxNetInitModule`|  
  
## 您想要執行甚麼工作？  
  
-   [初始化擴充 DLL](../build/initializing-extension-dlls.md)  
  
-   [初始化非 MFC DLL](../build/initializing-non-mfc-dlls.md)  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [C 執行階段程式庫行為和 \_DllMainCRTStartup](../build/run-time-library-behavior.md)  
  
-   [在標準 DLL 中使用資料庫、OLE 和通訊端擴充 DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [\<caps:sentence id\="tgt22" sentenceid\="704731be78a1b2b43311fed62656e454" class\="tgtSentence"\>處理序和執行緒 \(Windows SDK\)\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms684841)  
  
-   [執行緒區域儲存區包裝函式 \(MFC 技術提示 58\)](../mfc/tn058-mfc-module-state-implementation.md)  
  
## 請參閱  
 [初始化 DLL](../build/initializing-a-dll.md)