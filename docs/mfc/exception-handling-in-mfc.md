---
title: "MFC 中的例外狀況處理 | Microsoft Docs"
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
  - "異常程式執行 [C++]"
  - "封存例外狀況 [C++]"
  - "判斷提示 [C++], 使用例外狀況的時機"
  - "Automation [C++], 例外狀況"
  - "C++ 例外狀況處理, 啟用"
  - "C++ 例外狀況處理, MFC 應用程式"
  - "C++ 例外狀況處理, 類型"
  - "類別庫 [C++], 例外狀況支援"
  - "DAO [C++], 例外狀況"
  - "資料庫例外狀況 [C++]"
  - "錯誤處理 [C++], 例外狀況和"
  - "錯誤 [C++], 判斷提示偵測到的"
  - "例外狀況處理 [C++], MFC"
  - "例外狀況巨集 [C++]"
  - "例外狀況 [C++], MFC 巨集和 C++ 關鍵字比較"
  - "函式呼叫, 結果"
  - "關鍵字 [C++], 例外狀況處理"
  - "巨集 [C++], 例外狀況處理"
  - "巨集 [C++], MFC 例外狀況巨集"
  - "記憶體 [C++], 記憶體不足例外狀況"
  - "MFC [C++], 例外狀況"
  - "ODBC 例外狀況 [C++]"
  - "OLE 例外狀況 [C++], MFC 例外狀況處理"
  - "記憶體不足例外狀況 [C++]"
  - "預先定義的例外狀況 [C++]"
  - "不支援的服務要求"
  - "資源配置例外狀況"
  - "資源 [C++], 配置"
  - "序列化 [C++], 例外狀況"
  - "Windows [C++], 資源配置例外狀況"
ms.assetid: 0926627d-2ba7-44a6-babe-d851a4a2517c
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# MFC 中的例外狀況處理
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明 MFC 中可用的例外狀況處理機制。  兩種可用機制：  
  
-   C\+\+ 例外狀況，可用在 MFC 3.0 版和以後的版本  
  
-   MFC 例外狀況巨集，可用在 MFC 1.0 版和以後的版本  
  
 如果您正在使用 MFC撰寫新的應用程式，您應該使用 C\+\+ 機制。  您可以使用這個以巨集的機制，如果您的現有應用程式已經使用該機制廣泛。  
  
 您可以立即轉換現有的程式碼使用 C\+\+ 例外狀況而非 MFC 例外狀況巨集。  將您的程式碼和方針的優點這麼做的在文件 [例外狀況：從 MFC 例外狀況巨集轉換](../mfc/exceptions-converting-from-mfc-exception-macros.md)中說明。  
  
 使用 MFC 例外狀況巨集，如果已開發了應用程式，您仍然可以使用這些巨集以現有的程式碼，同時又使用了， C\+\+ 例外狀況是您的新程式碼時。  這篇文章 [例外狀況：3.0 版例外狀況巨集的變更](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md) 給這麼做的方針。  
  
> [!NOTE]
>  若要啟用 C\+\+ 例外狀況處理程式碼，選取啟用程式碼產生網頁的 C\+\+ 例外狀況在專案的 [屬性頁](../ide/property-pages-visual-cpp.md) 對話方塊的 C\/C\+\+ 資料夾或使用 \/GX 編譯器選項。  預設值為 \/GX \)，停用例外狀況處理。  
  
 本章節涵蓋下列主題：  
  
-   [使用例外狀況的時機](#_core_when_to_use_exceptions)  
  
-   [MFC 例外狀況支援](#_core_mfc_exception_support)  
  
-   [如需例外狀況的進一步閱讀](#_core_further_reading_about_exceptions)  
  
##  <a name="_core_when_to_use_exceptions"></a> 使用例外狀況的時機  
 當函式在程式執行期間，呼叫結果的三種可能發生:正常執行、錯誤執行或例外狀況執行。  每個分類如下。  
  
-   正常執行。  
  
     函式可提供較快的執行並傳回。  有些函式傳回的結果程式碼給呼叫端，表示函式的結果。  可能的結果碼為函式確實地定義和表示函式的可能結果的範圍。  結果碼表示成功或失敗或甚至表示正常範圍需要的失敗的特定型別。  例如，檔案狀態函式可傳回程式碼指示檔案不存在。  請注意不使用這個詞彙「錯誤碼」，因為結果程式碼代表許多預期結果之一。  
  
-   錯誤執行  
  
     呼叫端在不適當的內容會在傳遞引數的某些錯誤對函式或呼叫函式。  這種情況會造成錯誤，且在程式開發過程中判斷提示偵測到它。\(如需聲明的詳細資訊，請參閱[C\/C\+\+ 判斷提示](../Topic/C-C++%20Assertions.md)。\)  
  
-   異常執行  
  
     例外狀況執行在程式控制之外的條件，例如記憶體不足或發生 I\/O 錯誤，會影響函式結果的情況。  應該由攔截和擲回的例外狀況處理異常情況。  
  
 使用例外狀況的例外狀況執行特別適合。  
  
##  <a name="_core_mfc_exception_support"></a> MFC 例外狀況支援  
 如果直接使用 C\+\+ 例外狀況或使用 MFC 例外狀況巨集，您將使用 [CException Class](../mfc/reference/cexception-class.md) 或 `CException`\-可能擲回由架構或由您的應用程式的衍生物件。  
  
 下表顯示MFC所提供的預先定義例外狀況。  
  
|例外狀況類別|意義|  
|------------|--------|  
|[CMemoryException Class](../mfc/reference/cmemoryexception-class.md)|記憶體不足。|  
|[CFileException Class](../mfc/reference/cfileexception-class.md)|檔案的案例|  
|[CArchiveException Class](../mfc/reference/carchiveexception-class.md)|封存\/序列化例外狀況。|  
|[CNotSupportedException Class](../mfc/reference/cnotsupportedexception-class.md)|要求的回應不支援的服務。|  
|[CResourceException Class](../mfc/reference/cresourceexception-class.md)|Windows 資源配置例外狀況。|  
|[CDaoException Class](../mfc/reference/cdaoexception-class.md)|資料庫例外狀況 \(DAO 類別\)|  
|[CDBException Class](../mfc/reference/cdbexception-class.md)|資料庫例外狀況 \(ODBC 類別\)|  
|[COleException Class](../mfc/reference/coleexception-class.md)|OLE 例外狀況|  
|[COleDispatchException Class](../mfc/reference/coledispatchexception-class.md)|分派 \(自動\) 例外狀況。|  
|[CUserException Class](../mfc/reference/cuserexception-class.md)|警告擁有訊息方塊的使用者的例外狀況，然後擲回泛型 [CException Class](../mfc/reference/cexception-class.md)|  
  
> [!NOTE]
>  MFC 支援 C\+\+ 例外狀況和 MFC 例外狀況巨集。  MFC 不直接支援 Windows NT 結構化例外狀況處理常式 \(SEH\)，如 [結構化例外處理](http://msdn.microsoft.com/library/windows/desktop/ms680657)所述。  
  
##  <a name="_core_further_reading_about_exceptions"></a> 如需例外狀況的進一步閱讀  
 使用例外狀況處理， MFC 程式庫下列文章說明：  
  
-   [例外狀況：攔截及刪除例外狀況](../mfc/exceptions-catching-and-deleting-exceptions.md)  
  
-   [例外狀況：檢查例外狀況內容](../mfc/exceptions-examining-exception-contents.md)  
  
-   [例外狀況：釋放例外狀況中的物件](../mfc/exceptions-freeing-objects-in-exceptions.md)  
  
-   [例外狀況：從您自己的函式擲回例外狀況](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)  
  
-   [例外狀況：資料庫例外狀況](../mfc/exceptions-database-exceptions.md)  
  
-   [例外狀況：OLE 例外狀況](../mfc/exceptions-ole-exceptions.md)  
  
 下列文章 MFC 例外狀況巨集與 C\+\+ 例外狀況關鍵字比較並說明如何以符合您的程式碼：  
  
-   [例外狀況：3.0 版例外狀況巨集的變更](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)  
  
-   [例外狀況：從 MFC 例外狀況巨集轉換](../mfc/exceptions-converting-from-mfc-exception-macros.md)  
  
-   [例外狀況：使用 MFC 巨集和 C\+\+ 例外狀況](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)  
  
## 請參閱  
 [C\+\+ 例外狀況處理](../cpp/cpp-exception-handling.md)   
 [如何？：建立您的自訂例外狀況類別？](http://go.microsoft.com/fwlink/?LinkId=128045)