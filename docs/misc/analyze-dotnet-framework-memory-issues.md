---
title: "分析 .NET Framework 記憶體問題 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.diagnostics.managedmemoryanalysis"
ms.assetid: 43341928-9930-48cf-a57f-ddcc3984b787
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "susanno"
manager: "douge"
---
# 分析 .NET Framework 記憶體問題
使用 Visual Studio Managed 記憶體分析器，找出 .NET Framework 程式碼中記憶體流失和記憶體使用沒有效率的問題。  目標程式碼的最小 .NET Framework 版本是 .NET Framework 4.5。  
  
 記憶體分析工具分析會分析*「包含堆積資料的傾印檔案」*\(Dump File With Heap Data\) 中的資訊，堆積資料是應用程式記憶體中的物件複本。  您可以從 Visual Studio IDE 或透過其他系統工具收集傾印檔案 \(.dmp\)。  
  
-   您可以分析一份快照，了解物件類型對於記憶體使用的相對影響，並找出應用程式中記憶體使用沒有效率的程式碼。  
  
-   您也可以比較 \(*「差異比對」*\(Diff\)\) 應用程式的兩個快照，找出造成記憶體使用量隨著時間逐漸增加的程式碼部分。  
  
 如需 Managed 記憶體分析器的逐步解說，請參閱 Visual Studio ALM \+ Team Foundation Server 部落格上的[在生產環境中使用 Visual Studio 2013 診斷 .NET 記憶體問題](http://blogs.msdn.com/b/visualstudioalm/archive/2013/06/20/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production.aspx) \(英文\)。  
  
##  <a name="BKMK_Contents"></a> 內容  
 [.NET Framework 應用程式中的記憶體使用情況](#BKMK_Memory_use_in__NET_Framework_apps)  
  
 [識別應用程式中的記憶體問題](#BKMK_Identify_a_memory_issue_in_an_app)  
  
 [收集記憶體快照](#BKMK_Collect_memory_snapshots)  
  
 [分析記憶體使用情況](#BKMK_Analyze_memory_use)  
  
##  <a name="BKMK_Memory_use_in__NET_Framework_apps"></a> .NET Framework 應用程式中的記憶體使用情況  
 .NET Framework 是記憶體回收執行階段，因此在大多數應用程式中，記憶體使用情況不會構成問題。  但在長時間執行的應用程式 \(例如 Web 服務和應用程式\) 及記憶體數量有限的裝置中，記憶體中累積的物件會對應用程式及應用程式執行所在的裝置造成效能影響。  如果記憶體回收行程太常執行，或者強制作業系統在 RAM 和磁碟之間移動記憶體，則會過度使用記憶體，而導致應用程式和資源所在的電腦記憶體不足。  在最糟的情況下，應用程式可能會損毀並出現「記憶體不足」的例外狀況。  
  
 .NET*「Managed 堆積」*\(Managed Heap\) 是應用程式建立之參考物件儲存所在的虛擬記憶體區域。  物件的存留期是由記憶體回收行程 \(GC\) 所管理。  記憶體回收行程使用參考來追蹤佔用記憶體區塊的物件。  當系統建立物件並指派給變數時，便會建立參考。  一個物件可以有多個參考。  例如，您可以將物件加入至類別、集合或其他資料結構，或者將物件指派給第二個變數，來建立物件的其他參考。  還有一個較不常見的建立參考方式，那就是由某個物件將處理常式加入至另一個物件的事件。  在此情況下，第二個物件會保留第一個物件的參考，直到明確移除處理常式或終結第二個物件為止。  
  
 GC 針對每個應用程式維護一個參考樹狀目錄，以追蹤應用程式參考的物件。  *「參考樹狀目錄」*\(Reference Tree\) 有一組根目錄，其中包含全域和靜態物件，以及相關聯的執行緒堆疊和動態具現化的物件。  如果某個物件至少有一個參考該物件的父物件，則該物件是根目錄。  只有應用程式中沒有其他物件或變數參考該物件時，GC 才能回收該物件的記憶體。  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [內容](#BKMK_Contents)  
  
##  <a name="BKMK_Identify_a_memory_issue_in_an_app"></a> 識別應用程式中的記憶體問題  
 應用程式效能是記憶體問題的最明顯徵兆，特別是效能隨著時間逐漸降低時。  如果您的應用程式執行期間有其他應用程式的效能降低，也表示發生記憶體問題。  如果您懷疑發生記憶體問題，請使用工作管理員或 [Windows 效能監視器](http://technet.microsoft.com/library/cc749249.aspx)等工具進一步調查。  例如，尋找您無法解釋的記憶體大小總計成長量，當做記憶體流失的可能來源：  
  
 ![資源監視器中一致的記憶體成長](../misc/media/mngdmem_resourcemanagerconsistentgrowth.png "MNGDMEM\_ResourceManagerConsistentGrowth")  
  
 您也可能注意到那些遠超出您所認為程式碼應該使用的記憶體量增量，這可能指出某個程序的記憶體使用沒有效率：  
  
 ![資源管理員中記憶體爆增](../misc/media/mngdmem_resourcemanagerspikes.png "MNGDMEM\_ResourceManagerSpikes")  
  
##  <a name="BKMK_Collect_memory_snapshots"></a> 收集記憶體快照  
 記憶體分析工具會分析包含堆積資訊之*「傾印檔案」*\(Dump File\) 中的資訊。  您可以在 Visual Studio 中建立傾印檔案，也可以使用從 [Windows Sysinternals](http://technet.microsoft.com/sysinternals) 取得的 [ProcDump](http://technet.microsoft.com/sysinternals/dd996900.aspx) 等工具。  請參閱 Visual Studio Debugger 團隊部落格上的[什麼是傾印，如何建立一個傾印？](http://blogs.msdn.com/b/debugger/archive/2009/12/30/what-is-a-dump-and-how-do-i-create-one.aspx) \(英文\)。  
  
> [!NOTE]
>  大多數工具都可以收集含有或不含堆積記憶體資料的傾印資訊。  Visual Studio 記憶體分析器需要完整的堆積資訊。  
  
 **從 Visual Studio 收集傾印**  
  
1.  您可以建立從 Visual Studio 專案啟動之處理序的傾印檔案，也可以將偵錯工具附加至執行中的處理序。  請參閱[附加至執行中處理序](../Topic/Attach%20to%20Running%20Processes%20with%20the%20Visual%20Studio%20Debugger.md)。  
  
2.  停止執行。  當您選擇 \[偵錯\] 功能表上的 \[全部中斷\] 時，或者發生例外狀況或到達中斷點時，偵錯工具會停止。  
  
3.  在 \[偵錯\] 功能表上，選擇 \[另存傾印\]。  在 \[另存傾印\] 對話方塊中指定位置，並確定在 \[存檔類型\] 清單中選取 \[包含堆積的小型傾印\] \(預設值\)。  
  
 **比較兩個記憶體快照**  
  
 若要分析應用程式的記憶體使用成長量，請從一個應用程式執行個體收集兩個傾印檔案。  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [內容](#BKMK_Contents)  
  
##  <a name="BKMK_Analyze_memory_use"></a> 分析記憶體使用情況  
 [篩選物件清單](#BKMK_Filter_the_list_of_objects) **&#124;** [分析一份快照中的記憶體資料](#BKMK_Analyze_memory_data_in_from_a_single_snapshot) **&#124;** [比較兩個記憶體快照](#BKMK_Compare_two_memory_snapshots)  
  
 若要分析傾印檔案以找出記憶體使用問題：  
  
1.  在 Visual Studio 中，依序選擇 \[檔案\]、\[開啟舊檔\]，然後指定傾印檔案。  
  
2.  在 \[小型傾印檔案摘要\] 頁面上，選擇 \[偵錯 Managed 記憶體\]。  
  
     ![傾印檔案摘要頁面](../misc/media/mngdmem_dumpfilesummary.png "MNGDMEM\_DumpFileSummary")  
  
 記憶體分析器會啟動偵錯工作階段以分析檔案，並在 \[堆積檢視\] 頁面中顯示結果：  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [內容](#BKMK_Contents)  
  
###  <a name="BKMK_Filter_the_list_of_objects"></a> 篩選物件清單  
 根據預設，記憶體分析器會篩選記憶體快照中的物件清單，只顯示使用者程式碼的類型和執行個體，並且只顯示內含大小總計超過堆積大小總計之臨界值百分比的類型。  您可以在 \[檢視設定\] 清單中變更下列選項：  
  
|||  
|-|-|  
|**啟用 Just My Code**|Just My Code 隱藏最常見的系統物件，只在清單中顯示您建立的類型。<br /><br /> 您也可以在 Visual Studio 的 \[選項\] 對話方塊中，設定 \[Just My Code\] 選項。  在 \[**偵錯**\] 功能表上選擇 \[**選項和設定**\]。  在 \[偵錯\]\/\[一般\] 索引標籤中，選擇或清除 \[Just My Code\]。|  
|**摺疊小物件**|\[摺疊小物件\] 隱藏內含大小總計小於堆積大小總計 0.5% 的所有類型。|  
  
 您也可以在 \[搜尋\] 方塊中輸入字串，來篩選類型清單。  此清單只會顯示其名稱包含字串的類型。  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [內容](#BKMK_Contents)  
  
###  <a name="BKMK_Analyze_memory_data_in_from_a_single_snapshot"></a> 分析一份快照中的記憶體資料  
 Visual Studio 啟動新的偵錯工作階段以分析檔案，並在 \[堆積檢視\] 視窗中顯示記憶體資料。  
  
 ![&#91;物件類型&#93; 清單](../misc/media/dbg_mma_objecttypelist.png "DBG\_MMA\_ObjectTypeList")  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [內容](#BKMK_Contents)  
  
#### 物件類型資料表  
 上方資料表列出保留在記憶體中之物件的類型。  
  
-   \[計數\] 顯示快照中類型執行個體的數目。  
  
-   \[大小 \(位元組\)\] 是所有類型執行個體的大小，但不包含該類型參考之物件的大小。  此  
  
-   \[內含大小 \(位元組\)\] 包含參考的物件大小。  
  
 您可以選擇 \[**物件類型**\] 資料行中的執行個體圖示 \(![&#91;物件類型&#93; 資料行中的執行個體圖示](../misc/media/dbg_mma_instancesicon.png "DBG\_MMA\_InstancesIcon")\)，以檢視該類型執行個體的清單。  
  
#### 執行個體資料表  
 ![執行個體資料表](../misc/media/dbg_mma_instancestable.png "DBG\_MMA\_InstancesTable")  
  
-   \[執行個體\] 是物件的記憶體位置，可做為物件的物件識別項。  
  
-   \[值\] 顯示實值類型的實際值。  您可以將滑鼠指標停留在參考類型的名稱上，以在資料提示中檢視其資料值。  
  
     ![資料提示中的執行個體值](../misc/media/dbg_mma_instancevaluesindatatip.png "DBG\_MMA\_InstanceValuesInDataTip")  
  
-   \[大小 \(位元組\)\] 是物件的大小，但不包含該物件參考之其他物件的大小。  此  
  
-   \[內含大小 \(位元組\)\] 包含參考的物件大小。  
  
 根據預設，類型和執行個體會依 \[內含大小 \(位元組\)\] 排序。  選擇清單中的資料行標頭可變更排序次序。  
  
#### 根的路徑  
  
-   針對從 \[物件類型\] 資料表中選取的類型，\[根的路徑\] 資料表會顯示唯一的類型階層架構，指向該類型之所有物件的根物件，並顯示階層架構中該類型上方之類型參考的數目。  
  
-   針對從類型執行個體中選取的物件，\[根的路徑\] 會顯示參考該執行個體之實際物件的圖表。  您可以將滑鼠指標停留在物件的名稱上，以在資料提示中檢視其資料值。  
  
#### 參考的類型\/參考的物件  
  
-   針對從 \[物件類型\] 資料表中選取的類型，\[參考的類型\] 索引標籤會顯示所選類型的所有物件持有之參考類型的大小和數目。  
  
-   針對選取的類型執行個體，\[參考的物件\] 會顯示所選執行個體持有的物件。  您可以將滑鼠指標停留在名稱上，以在資料提示中檢視其資料值。  
  
 **循環參考**  
  
 第一個物件可參考第二個物件，而第二個物件對第一個物件有直接或間接參考。  當記憶體分析器遇到這種情況時，它會停止展開參考路徑並將 \[偵測到循環\] 註釋加入至第一個物件的清單中，然後停止。  
  
 **根類型**  
  
 記憶體分析器會將註釋加入至根物件，以描述持有的參考類型：  
  
|註釋|描述|  
|--------|--------|  
|\[靜態變數\] `VariableName`|靜態變數。  `VariableName` 是變數的名稱。|  
|**完成項控制代碼**|完成項佇列中的參考|  
|**區域變數**|區域變數。|  
|**強式控制代碼**|物件控制代碼資料表中的強式參考控制代碼。|  
|**非同步  固定控制代碼**|物件控制代碼資料表中的非同步固定物件。|  
|**相依控制代碼**|物件控制代碼資料表中的相依物件。|  
|**固定控制代碼**|物件控制代碼資料表中的固定強式參考。|  
|**RefCount 控制代碼**|物件控制代碼資料表中的參考計數物件。|  
|**SizedRef 控制代碼**|強式控制代碼，保留記憶體回收時集體關閉之所有物件和根物件的估計大小。|  
|**固定的區域變數**|固定的區域變數。|  
  
###  <a name="BKMK_Compare_two_memory_snapshots"></a> 比較兩個記憶體快照  
 您可以比較一個處理序的兩個傾印檔案，以找出可能造成記憶體流失的物件。  收集第一個 \(較早的\) 檔案到收集第二個 \(較晚的\) 檔案的間隔應該夠長，才能輕鬆看出造成記憶體流失之物件數目的成長量。  若要比較兩個檔案：  
  
1.  開啟第二個傾印檔案，然後在 \[小型傾印檔案摘要\] 頁面上，選擇 \[偵錯 Managed 記憶體\]。  
  
2.  在記憶體分析報告頁面上，開啟 \[選取基準\] 清單，然後選擇 \[瀏覽\] 以指定第一個傾印檔案。  
  
 分析器會在報告的上窗格中加入資料行，以顯示這些類型的 \[計數\]、\[大小\] 和 \[內含大小\] 與先前快照中對應值之間的差異。  
  
 ![型別清單中的差異比對資料行](../misc/media/mngdmem_diffcolumns.png "MNGDMEM\_DiffColumns")  
  
 \[參考計數差異\] 資料行也會加入至 \[根的路徑\] 資料表。  
  
 ![回到頁首](../misc/media/pcs_backtotop.png "PCS\_BackToTop") [內容](#BKMK_Contents)  
  
## 請參閱  
 [VS ALM TFS 部落格：在生產環境中使用 Visual Studio 2013 診斷 .NET 記憶體問題](http://blogs.msdn.com/b/visualstudioalm/archive/2013/06/20/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production.aspx)   
 [Channel 9 &#124; Visual Studio TV &#124; Managed 記憶體分析](http://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Managed-Memory-Analysis)   
 [Channel 9 &#124; Visual Studio 工具箱 &#124; Visual Studio 2013 中的 Managed 記憶體分析](http://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Managed-Memory-Analysis-in-Visual-Studio-2013)