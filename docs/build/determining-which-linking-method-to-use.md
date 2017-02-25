---
title: "決定要使用哪一個連結方法 | Microsoft Docs"
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
  - "明確連結 [C++]"
  - "隱含連結 [C++]"
ms.assetid: 6b6d3fec-4711-4a30-af5b-354b965ecaec
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 決定要使用哪一個連結方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

有兩種連結的類型：隱含連結 \(Implicit Linking\) 和明確連結 \(Explicit Linking\)。  
  
## 隱含連結  
 應用程式程式碼在呼叫匯出 DLL 函式時，會發生[隱含連結](../build/linking-implicitly.md)。  DLL 函式呼叫會在編譯或組譯呼叫可執行檔的原始程式碼時，在物件程式碼產生外部函式參考。  若要解析這種外部參考，應用程式必須連結 DLL 製造者所提供的匯入程式庫 \(.lib 檔\)。  
  
 匯入程式庫包含的程式碼只會載入 DLL 並實作 DLL 函式的呼叫。  若是在匯入程式庫裡發現外部函式，連結器便會被通知該函式的程式碼是在 DLL 裡。  為了解析 DLL 的外部參考，連結器會僅將資訊加入會在處理序啟動時告訴系統哪裡可取得 DLL 程式碼的可執行檔。  
  
 系統在啟動包含動態連結參考的程式時，會使用程式可執行檔裡的資訊來找出所需的 DLL。  如果找不到 DLL，該系統就會終止處理序，並且顯示報告錯誤的對話方塊。  否則，系統會將 DLL 模組對應到處理序的位址空間。  
  
 任一 DLL 出現進入點 \(Entry Point\) 函式 \(用於初始化和終止程式碼\) 時，作業系統就會呼叫函式。  一個傳遞至進入點函式的參數指定程式碼將會指示該 DLL 是連結至處理序。  如果進入點函式沒有傳回 TRUE，系統會中止處理序並且報告錯誤。  
  
 最後，系統會修改處理序的可執行程式碼，以便提供 DLL 函式的開始位址。  
  
 就像其他程式程式碼，DLL 程式碼會在處理序啟動時對應到處理序的位址空間，而且只有在需要時才會載入記憶體。  因此，在先前版本的 Windows 中 .def 檔用來控制載入的 **PRELOAD** 和 **LOADONCALL** 程式碼屬性 \(Attribute\)，就再也沒有意義。  
  
## 明確連結  
 因為隱含連結是最容易使用的連結方法，因此大多數的應用程式都會使用它。  但是有時也必須使用[明確連結](../build/linking-explicitly.md)。  下列是使用明確連結的常見原因：  
  
-   應用程式一直要等到執行階段時才會知道其將載入的 DLL 名稱。  例如，應用程式可能需要從組態檔取得 DLL 和匯出函式的名稱。  
  
-   如果處理序啟動時找不到 DLL，作業系統便會終止使用隱含連結的處理序。  此時並不會終止使用明確連結的處理序，且可以嘗試從錯誤復原。  例如，處理序將錯誤告知使用者，並且讓使用者指定 DLL 的另一個路徑。  
  
-   如果處理序所連結的任何 DLL 出現失敗的 `DllMain` 函式，也會終止使用隱含連結的處理序。  此時並不會終止使用明確連結的處理序。  
  
-   隱含連結至許多 DLL 的應用程式啟動可能會很緩慢，因為 Windows 在載入應用程式時會載入所有的 DLL。  若要改善啟動效能，應用程式可以在載入後立即隱含地連結至所需的 DLL，等候在需要時再明確地連結至其他的 DLL。  
  
-   明確連結可以減少應用程式連結匯入程式庫的需要。  如果 DLL 的變更造成匯出序數變更，就不需要重新連結使用明確連結的應用程式 \(假設它們是以函式的名稱而不是序數值呼叫 **GetProcAddress**\)，但是使用隱含連結的應用程式必須重新連結新匯入程式庫。  
  
 下列是明確連結要小心的兩個危險區域：  
  
-   如果 DLL 有 `DllMain` 進入點函式，作業系統就會呼叫稱為 **LoadLibrary** 執行緒內容中的函式。  如果 DLL 已經連結至處理序，就不會呼叫進入點函式，因為先前 **LoadLibrary** 的呼叫並沒有包含 **FreeLibrary** 函式的對應呼叫。  如果 DLL 是使用 `DllMain` 函式來執行處理序中每個執行緒的初始化，明確連結便可能會發生問題，因為當呼叫 **LoadLibrary** \(或 `AfxLoadLibrary`\) 時，並不會初始化現存的執行緒。  
  
-   如果 DLL 將靜態範圍資料宣告成 **\_\_declspec\(thread\)**，便可能會在明確連結時造成保護錯誤。  DLL 以 **LoadLibrary** 載入之後，這份資料會在每次受程式碼參考時造成保護錯誤 \(靜態範圍資料包括全域和區域靜態項目\)。因此，當您建立 DLL 時，您應該避免使用執行緒區域儲存區 \(Thread Local Storage\)，或告知 DLL 使用者潛在的風險 \(以免他們嘗試動態載入\)。  
  
## 您想要執行甚麼工作？  
  
-   [隱含連結](../build/linking-implicitly.md)  
  
-   [明確連結](../build/linking-explicitly.md)  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [Windows 用來找出 DLL 的搜尋路徑](../build/search-path-used-by-windows-to-locate-a-dll.md)  
  
-   [LoadLibrary 和 AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
  
-   [GetProcAddress](../build/getprocaddress.md)  
  
-   [FreeLibrary 和 AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md)  
  
-   [\<caps:sentence id\="tgt47" sentenceid\="8081a197f9413cac12a30b57c2612af5" class\="tgtSentence"\>在動態連結程式庫中使用執行緒區域儲存區 \(Windows SDK\)\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms686997)  
  
## 請參閱  
 [將可執行檔連結至 DLL](../build/linking-an-executable-to-a-dll.md)