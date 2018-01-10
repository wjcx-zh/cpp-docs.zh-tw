---
title: "改善時間關鍵程式碼的秘訣 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- _lsearch function
- qsort function
- background tasks
- standard sort routines
- clock cycle losses
- code, time-critical
- memory [C++], monitoring usage
- execution, speed improvements
- local heap performance
- optimization [C++], time-critical code
- performance [C++], time-critical code
- threading [C++], performance
- cache [C++], hits and misses
- linear search performance
- page faults
- best practices, time-critical code
- searching [C++], improving performance
- sorting data, improving performance
- threading [C++], best practices
- threading [C++], background tasks
- lists, sorting
- bsearch function
- MFC [C++], performance
- sort routines
- programs [C++], performance
- _lfind function
- heap allocation, time-critical code performance
ms.assetid: 3e95a8cc-6239-48d1-9d6d-feb701eccb54
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 23ca6fc8c18a7f2f2013ffdeabd70a7eb9fb0057
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="tips-for-improving-time-critical-code"></a>改善時間關鍵程式碼的秘訣
撰寫快速的程式碼需要瞭解應用程式的所有層面，以及它如何與系統互動。 本主題建議一些較明顯程式設計技巧的替代選擇，以協助您確定程式碼中時間關鍵的部分效能令人滿意。  
  
 總而言之，改善時間關鍵程式碼需要您：  
  
-   知道程式的哪些部分必須快速。  
  
-   知道程式碼的大小和速度。  
  
-   知道新功能的成本。  
  
-   知道完成工作所需的最少工作。  
  
 若要收集程式碼效能的資訊，您可以使用效能監視器 (perfmon.exe)。  
  
## <a name="sections-in-this-article"></a>本文內容：  
  
-   [快取遺漏和分頁錯誤](#_core_cache_hits_and_page_faults)  
  
-   [排序和搜尋](#_core_sorting_and_searching)  
  
-   [MFC 和類別庫](#_core_mfc_and_class_libraries)  
  
-   [共用程式庫](#vcovrsharedlibraries)  
  
-   [堆積](#_core_heaps)  
  
-   [執行緒](#_core_threads)  
  
-   [小工作集](#_core_small_working_set)  
  
##  <a name="_core_cache_hits_and_page_faults"></a>快取遺漏和分頁錯誤  
 遺漏的快取命中 (在內部和外部快取) 以及分頁錯誤 (前往次要存放裝置取得程式指示和資料) 會減慢程式的效能。  
  
 CPU 快取命中可能耗費程式 10 20 個時脈週期。 外部快取命中可能耗費 20-40 個時脈週期。 分頁錯誤可能耗費一百萬個時脈週期 (假設是每秒可處理 5 億個指示的處理器，以及一次分頁錯誤要 2 毫秒)。 因此，撰寫減少遺漏快取命中和分頁錯誤數目的程式碼，對程式執行而言最有利。  
  
 緩慢程式的一個原因是它們的分頁錯誤或快取遺漏經常多過於必要。 要避免此點，很重要的是要使用具有良好參考位置的資料結構，這意味著將相關的東西放在一起。 有時候看起來很棒的資料結構因為參考位置惡劣而最後變得嚇人，而有時候相反的情況也成立。 以下是兩個範例：  
  
-   動態配置的連結清單可能會降低程式效能，因為當您搜尋項目或周遊清單到盡頭時，每個略過的連結都可能遺漏快取，或造成分頁錯誤。 以簡單陣列為基礎的清單實作可能實際上快速許多，因為有較佳的快取和較少的分頁錯誤 — 甚至是考慮到陣列會比較難成長的事實，它仍然可能比較快。  
  
-   使用動態配置連結清單的雜湊表可能會降低效能。 藉由擴充，使用動態配置連結清單存放內容的雜湊表效能可能實質較差。 事實上，在最後的分析中，在陣列進行簡單的線性搜尋可能實際上較快 (視情況而定)。 以陣列為基礎的雜湊表 (所謂的「閉合雜湊」) 是經常被忽略的實作，它的效能經常都很卓越。  
  
##  <a name="_core_sorting_and_searching"></a>排序和搜尋  
 排序與許多一般作業相比，本質就很耗時。 避免不必要的減緩，最好的方式就是避免在關鍵時刻進行排序。 您可以：  
  
-   延遲的效能關鍵的時間排序。  
  
-   在較早、 非效能關鍵的時間來排序資料。  
  
-   只針對真正需要排序的資料部分進行排序。  
  
 有時候，您可以使用排序過的順序建置清單。 請小心，因為如果您需要以排序順序插入資料，可能需要較複雜的資料結構，而其具有不良的參考位置，導致快取遺漏和分頁錯誤。 沒有方法可適用於所有情況。 請嘗試數種方法，並測量差異。  
  
 下面是一些排序的一般祕訣：  
  
-   使用庫存排序讓 Bug 減到最少。  
  
-   您可以事先進行以減少排序複雜度的任何工作都是值得的。 如果瀏覽過資料一遍可以簡化比較，並將排序從 O(n log n) 減到 O(n)，您將幾乎確定領先。  
  
-   請思考排序演算法的參考位置和您預期它執行的資料。  
  
 搜尋的替代選擇比排序少。 如果搜尋時間很重要，二進位搜尋或雜湊表查閱幾乎永遠是最佳選擇，但就像排序一樣，您必須將位置牢記在心。 對於小陣列進行線性搜尋，可能會比對於具有許多指標導致分頁錯誤或快取遺漏的資料結構進行二進位搜尋來得快。  
  
##  <a name="_core_mfc_and_class_libraries"></a>MFC 和類別庫  
 Microsoft Foundation Class (MFC) 可大幅簡化程式碼的撰寫。 在撰寫時間關鍵的程式碼時，您應該注意在部分類別中固有的額外負荷。 請檢查您的時間關鍵程式碼所使用的 MFC 程式碼，查看它是否符合您的效能要求。 下列清單顯示您應該注意的 MFC 類別和函式：  
  
-   `CString`MFC 呼叫 C 執行階段程式庫配置的記憶體[CString](../../atl-mfc-shared/reference/cstringt-class.md)動態。 一般而言，`CString` 效率和任何其他動態配置的字串一樣。 如同任何動態配置的字串，它也有動態配置和釋放的額外負荷。 堆疊上的簡單 `char` 陣列便經常可以達到相同的目的，且更快速。 請不要使用 `CString` 來存放常數字串。 請改用 `const char *`。 您對 `CString` 物件執行的任何作業都有一些額外負荷。 使用執行階段程式庫[字串函數](../../c-runtime-library/string-manipulation-crt.md)可能更快。  
  
-   `CArray`A [CArray](../../mfc/reference/carray-class.md)提供彈性，不是一般的陣列，但您的程式可能不需要它。 如果您知道陣列的特定限制，可以改用全域固定陣列。 如果使用 `CArray`，請使用 `CArray::SetSize` 來建立其大小，並指定當需要重新配置時，它成長的項目個數。 否則，加入項目可能會導致您的陣列經常重新配置和複製，這樣沒有效率，且可能導致記憶體片段化。 另外也請注意，如果您在陣列中插入項目，`CArray` 會將後續項目移入記憶體，而可能需要加大陣列。 這些動作可能導致快取遺漏和分頁錯誤。 如果您瀏覽過 MFC 使用的程式碼，可能會發現您可以撰寫更專屬於您情節的程式碼，以改善效能。 例如，由於 `CArray` 是一個範本，您可能會針對特定類型提供 `CArray` 特製化。  
  
-   `CList`[CList](../../mfc/reference/clist-class.md)是雙向連結的清單中，所以插入項目是快速在頭、 尾以及的已知位置 (`POSITION`) 清單中。 不過，以值或索引來查閱項目需要進行循序搜尋，如果清單很長便可能速度緩慢。 如果您的程式碼不需要雙向連結清單，可以重新考慮是否使用 `CList`。 使用單向連結清單可以節省針對所有作業更新額外指標的額外負荷，以及該指標的記憶體。 額外記憶體不太好，它是另一個可能出現快取遺漏或分頁錯誤的機會。  
  
-   `IsKindOf`此函式可以產生許多呼叫，並存取大量的記憶體不同的資料區域中，導致參考位置不佳。 它適用於偵錯組建 (例如在 ASSERT 呼叫中)，但在發行組建裡請試著避免用它。  
  
-   `PreTranslateMessage`使用`PreTranslateMessage`當特定視窗的樹狀結構需要不同的鍵盤快速鍵，或當您必須將訊息處理，在訊息幫浦內插入。 `PreTranslateMessage` 會修改 MFC 分派訊息。 如果您覆寫 `PreTranslateMessage`，請只在需要的層級上進行。 例如，如果您只對送到特定檢視之子系的訊息有興趣，就不必覆寫 `CMainFrame::PreTranslateMessage`。 請改成覆寫檢視類別的 `PreTranslateMessage`。  
  
     請不要使用 `PreTranslateMessage` 處理送往任何視窗的任何訊息，而避開正常的分派路徑。 使用[視窗程序](../../mfc/registering-window-classes.md)和 MFC 訊息對應用於此用途。  
  
-   `OnIdle`閒置事件可能會發生在您不希望，例如`WM_KEYDOWN`和`WM_KEYUP`事件。 計時器可能是觸發程式碼更有效率的方式。 請不要藉由產生假訊息或一律從覆寫 `OnIdle` 傳回 `TRUE`，強制重複呼叫 `OnIdle`，這會永遠不允許您的執行緒睡眠。 同樣地，計時器或個別執行緒可能較適合。  
  
##  <a name="vcovrsharedlibraries"></a>共用程式庫  
 重複使用程式碼是合理的。 不過，如果您即將使用別人的程式碼，則應該確定您完全知道在效能對您很關鍵的情況下，它做些什麼事。 瞭解此點的最好方式就是逐步執行原始程式碼，或是使用例如 PView 或效能監視器的工具來進行測量。  
  
##  <a name="_core_heaps"></a>堆積  
 請謹慎使用多個堆積。 以 `HeapCreate` 和 `HeapAlloc` 建立的額外堆積讓您能管理然後處置相關的配置集合。 請不要認可過多記憶體。 如果您使用多個堆積，請特別注意一開始認可的記憶體數量。  
  
 若不用多個堆積，您可以使用 Helper 函式作為程式碼與預設堆積之間的介面。 Helper 函式有助於自訂配置策略，可以改善應用程式的效能。 例如，如果您經常執行小型配置，可能會想將這些配置集中在預設堆積的一個部分。 您可以配置大區塊的記憶體，然後使用 Helper 函式從該區塊再配置出來。 這麼做的話，您便不會有具有未使用記憶體的額外堆積，因為配置將來自預設堆積。  
  
 不過在某些情況下，使用預設堆積可能減少參考位置。 請使用處理序檢視器、Spy++ 或效能監視器，來測量在堆積之間移動物件的效果。  
  
 測量您的堆積，您便可以解釋堆積上的每次配置。 使用 C 執行階段[偵錯堆積常式](/visualstudio/debugger/crt-debug-heap-details)至檢查點和傾印堆積。 您可以將輸出讀取到例如 Microsoft Excel 的試算表格式，並使用樞紐分析表來檢視結果。 請注意配置的總數、大小和分佈。 將這些與工作集的大小進行比較。 另外也請查看相關大小之物件的群集。  
  
 您也可以使用效能計數器來監控記憶體使用量。  
  
##  <a name="_core_threads"></a> 執行緒  
 對於背景工作，有效的事件閒置處理可能比使用執行緒更快。 在單一執行緒程式中比較容易瞭解參考位置。  
  
 有一項不錯的準則是，唯有在您封鎖的作業系統通知是背景工作的根源時才使用執行緒。 執行緒是這類案例中的最佳解決方案，因為封鎖事件的主要執行緒並不實際。  
  
 執行緒也會造成通訊問題。 您必須使用訊息清單或是藉由配置並使用共用記憶體，來管理執行緒之間的通訊連結。 管理通訊連結通常需要同步處理，以避免競爭情況和死結問題。 這種複雜性很有可能輕易地便演變成 Bug 和效能問題。  
  
 如需詳細資訊，請參閱[閒置迴圈處理](../../mfc/idle-loop-processing.md)和[多執行緒](../../parallel/multithreading-support-for-older-code-visual-cpp.md)。  
  
##  <a name="_core_small_working_set"></a>小工作集  
 較小的工作集表示參考位置較佳、較少分頁錯誤，且會有較多的快取命中。 處理序工作集是作業系統直接提供來測量參考位置的最接近度量。  
  
-   若要設定工作集上限和下限，使用[SetProcessWorkingSetSize](http://msdn.microsoft.com/library/windows/desktop/ms683226.aspx)。  
  
-   若要取得工作集上限和下限，請使用[GetProcessWorkingSetSize](http://msdn.microsoft.com/library/windows/desktop/ms686234.aspx)。  
  
-   若要檢視工作集的大小，請使用 Spy++。  
  
## <a name="see-also"></a>請參閱  
 [最佳化程式碼](../../build/reference/optimizing-your-code.md)