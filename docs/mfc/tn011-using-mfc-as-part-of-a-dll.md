---
title: "TN011：將 MFC 當成 DLL 的一部分來使用 | Microsoft Docs"
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
  - "vc.mfc.dll"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_USRDLL 符號"
  - "DLL [C++], 連結"
  - "MFC DLL [C++], 將標準 DLL 連結至 MFC"
  - "TN011"
  - "USRDLL, 編譯器參數"
ms.assetid: 76753e9c-59dc-40f6-b6a7-f6bb9a7c4190
caps.latest.revision: 20
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN011：將 MFC 當成 DLL 的一部分來使用
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

說明標準 DLL，可以讓您將 MFC 程式庫當成 Windows 動態連結程式庫來使用。  它假設您熟悉 Windows DLL 和如何建置它們。  如需 MFC 擴充 DLL 的資訊，您可以建立擴充功能加入至 MFC 程式庫，請參閱 [MFC DLL 版本](../mfc/tn033-dll-version-of-mfc.md)。  
  
## DLL 介面  
 泛型 DLL 假設應用程式和 DLL 之間的介面在像 C 的函式指定或明確匯出類別。  MFC 類別介面無法匯出。  
  
 如果 DLL 和應用程式要使用 MFC，具有一個要使用 MFC 程式庫的共用版本或對靜態與程式庫的複寫連線。  應用程式和 DLL 可能都使用其中一個 MFC 程式庫的標準版本。  
  
 標準 DLL 有下列幾項優點:  
  
-   使用 DLL 的應用程式不使用 MFC，而且不需要是 Visual C\+\+ 應用程式。  
  
-   靜態連結至 MFC 的標準 DLL， DLL 的大小只取決於使用和介面的 MFC 和 C 執行階段常式。  
  
-   動態連結至 MFC 的標準 DLL，在記憶體中節省從使用 MFC 的共用版本可以是很重要的。  不過，您必須發出共用 DLL、Mfc*\<version\>*.dll 和 Msvvcrt 與您的 DLL 的*\<version\>*.dll，。  
  
-   DLL 設計是獨立類別如何實作。  您的 DLL 設計只匯出至您要的 API。  因此，，如果實作變更，標準 DLL 有效。  
  
-   標準 DLL，因此，如果 DLL 和應用程式使用 MFC 靜態連結至 MFC，沒有比 DLL 想要反之亦然 MFC 不同版本或應用程式的問題。  因為 MFC 程式庫以靜態方式連結至每個 DLL 或 EXE，沒有關於版本的問題您有。  
  
## API限制  
 一些 MFC 功能並不適用於 DLL 版本，或由於技術限制，或是因為應用程式通常會提供這些服務。  MFC 版本，不適用於的函式是 `CWinApp::SetDialogBkColor`。  
  
## 建置 DLL  
 當必須定義編譯標準 DLL 使用 MFC，符號的 `_USRDLL` 和 `_WINDLL` 時靜態連結。  也必須編譯您的 DLL 程式碼與下列編譯器參數:  
  
-   **\/D\_WINDLL** 表示編譯為 DLL  
  
-   **\/D\_USRDLL** 指定您建置標準 DLL  
  
 在動態編譯標準 DLL 該連結至 MFC 時，您也必須定義這些符號和使用這些編譯器參數。  此外，必須定義符號則為 `_AFXDLL` ，而且必須編譯您的程式碼與 DLL:  
  
-   **\/D\_AFXDLL** 指定建置該規則的 DLL 動態連結至 MFC  
  
 必須明確地匯出介面 \(API\) 應用程式和 DLL 之間。  我們建議您定義介面是低頻寬，並且只使用 C 介面，則可以。  直接 C 介面比更複雜的 C\+\+ 類別容易維護。  
  
 將 API 以 C 和 C\+\+ 檔案包含不同的標題。  如需範例查看 MFC 進階概念 [DLLScreenCap](../top/visual-cpp-samples.md) 範例的標題 ScreenCap.h。  您要匯出的函式，請輸入到模組定義檔 \(.DEF\) 的 `EXPORTS` 部分或包括在您的函式定義的 `__declspec(dllexport)` 。  使用 `__declspec(dllimport)` 匯入這些函式匯入用戶端可執行檔。  
  
 您必須在動態連結至 MFC 的標準 DLL 的匯出函式的開頭加入 `AFX_MANAGE_STATE` 巨集。  這個巨集目前模組狀態設定為 DLL 的狀態。  透過使用這個巨集，將下行程式碼加入由 DLL 匯出的函式開頭來完成：  
  
 `AFX_MANAGE_STATE(AfxGetStaticModuleState( ))`  
  
## WinMain\-\> DllMain  
 MFC 程式庫定義標準 Win32 `DllMain` 進入點初始化您的 [CWinApp](../mfc/reference/cwinapp-class.md) 衍生物件加入位於一般 MFC 應用程式。  像在一般 MFC 應用程式一樣，將所有 DLL 特定的初始化置於 [InitInstance](../Topic/CWinApp::InitInstance.md) 成員函式裡。  
  
 請注意因為應用程式擁有主要訊息幫浦，所以 [CWinApp::Run](../Topic/CWinApp::Run.md) 機制不適用於 DLL。  如果 DLL 顯示非強制回應的對話方塊或者是有它自己的主框架視窗，應用程式的主要訊息幫浦就必須呼叫將會呼叫 [CWinApp::PreTranslateMessage](../Topic/CWinApp::PreTranslateMessage.md) 的 DLL 匯出常式。  
  
 請參閱 DLLScreenCap 範例觀看這個函式的使用範例。  
  
 在卸載 DLL 之前，MFC 提供的 `DllMain` 函式會從`CWinApp`  衍生您自己的類別的 [CWinApp::ExitInstance](../Topic/CWinApp::ExitInstance.md) 方法。  
  
## 連接您的 DLL  
 靜態連結至 MFC 的標準 DLL，您必須連結您的 DLL Nafxcwd.lib 或 Nafxcw.lib 和使用 C 執行階段具名 Libcmt.lib 的版本。  這些程式庫是預先建立，而且可以透過指定它們安裝，當您執行 Visual C\+\+ 設定時。  
  
## 程式碼範例  
 如需完整的範例的 MFC 進階概念 DLLScreenCap 範例程式。  請注意幾個有趣的是在這個範例如下:  
  
-   DLL 的編譯器旗標和這些應用程式是不同的。  
  
-   連結行和 .DEF 檔的 DLL 和那些應用程式的不同。  
  
-   使用 DLL 的應用程式不需要在 C\+\+。  
  
-   應用程式和由 C 或 C\+\+ 可和匯出與 DLLScreenCap.def 的 DLL 之間的介面是應用程式開發介面。  
  
 在該規則的 DLL 定義靜態連結至 MFC 的範例說明了應用程式開發介面。  在此範例中，宣告在 C\+\+ 使用者的 `extern "C" { }` 區塊內。  這有數種好處。  第一，它能夠讓非 C\+\+ 用戶端應用程式也可以使用您的 DLL API。  第二，它降低了 DLL 虛耗的空間，因為 C\+\+ 名稱損壞無法套用至已匯出的名稱。  最後，它讓您更容易明確地加入至 .DEF 檔案 \(以便用於依序數匯出\)，而不需要擔心 C\+\+ 名稱損壞。  
  
```  
#ifdef __cplusplus  
extern "C" {  
#endif  /* __cplusplus */  
  
struct TracerData  
{  
    BOOL    bEnabled;  
    UINT    flags;  
};  
  
BOOL PromptTraceFlags(TracerData FAR* lpData);  
  
#ifdef __cplusplus  
}  
#endif  
```  
  
 應用程式開發介面使用的結構從 MFC 類別在應用程式開發介面標頭不是衍生自和定義。  這會減少介面的複雜 DLL 和應用程式之間的並使 DLL 可以由 C 程式。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)