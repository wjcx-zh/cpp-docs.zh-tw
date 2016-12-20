---
title: "逐步解說：偵錯 C++ AMP 應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "偵錯，C++ Accelerated Massive Parallelism"
  - "C++ AMP，偵錯"
  - "C++ Accelerated Massive Parallelism，偵錯"
  - "偵錯，C++ AMP"
ms.assetid: 40e92ecc-f6ba-411c-960c-b3047b854fb5
caps.latest.revision: 35
caps.handback.revision: 34
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 逐步解說：偵錯 C++ AMP 應用程式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主題示範如何使用 C\+\+ Accelerated Massive Parallelism \(C\+\+ AMP\)來利用圖形處理器 \(GPU\) 進行偵錯應用程式。  它會使用平行降低程式來加總大型陣列的整數。  這個逐步解說將說明下列工作：  
  
-   啟動 GPU 偵錯工具。  
  
-   檢查 GPU 執行緒 視窗中的執行緒。  
  
-   使用平行堆疊視窗同時觀察多重 GPU 執行緒的呼叫堆疊。  
  
-   若要在多個執行緒之間檢查單一運算式的值請使用平行監看式視窗。  
  
-   標幟、 凍結、 解除凍結，和群組 GPU 執行緒。  
  
-   針對程式碼的特定區域執行所有執行緒。  
  
## 必要條件  
 請在啟動前瀏覽這個說明：  
  
-   讀取 [C\+\+ AMP 概觀](../../parallel/amp/cpp-amp-overview.md)。  
  
-   行數將會顯示在文字編輯器中。  如需詳細資訊，請參閱[如何：顯示編輯器中的行號](../Topic/How%20to:%20Display%20Line%20Numbers%20in%20the%20Editor.md)。  
  
-   請確定您執行 [!INCLUDE[win8](../../build/includes/win8_md.md)] 或 [!INCLUDE[winserver8](../../build/includes/winserver8_md.md)] 支援軟體模擬器的偵錯。  
  
 [!INCLUDE[note_settings_general](../../mfc/includes/note_settings_general_md.md)]  
  
### 建立範例專案  
  
1.  啟動 Visual Studio。  
  
2.  在功能表列上，選擇 \[**檔案**\]、\[**新增**\]、\[**專案**\]。  
  
3.  在範本窗格中選擇 \[**已安裝**\]，接著選擇 \[**Visual C\+\+**\]。  
  
4.  選擇 **Win32 主控台應用程式**，輸入 `AMPMapReduce` 在**名稱** 方塊中，然後再選擇 **確定** 按鈕。  
  
5.  選擇 \[**下一步**\] 按鈕。  
  
6.  清除**先行編譯標頭** 核取方塊，然後再選擇 **完成** 按鈕。  
  
7.  在**方案總管中**，從專案刪除 stdafx.h、 targetver.h 和 stdafx.cpp。  
  
8.  開啟 AMPMapReduce.cpp，將它的內容取代成下列程式碼。  
  
    ```cpp  
  
    // AMPMapReduce.cpp defines the entry point for the program.  
    // The program performs a parallel-sum reduction that computes the sum of an array of integers.   
  
    #include <stdio.h>  
    #include <tchar.h>  
    #include <amp.h>  
  
    const int BLOCK_DIM = 32;  
  
    using namespace concurrency;  
  
    void sum_kernel_tiled(tiled_index<BLOCK_DIM> t_idx, array<int, 1> &A, int stride_size) restrict(amp)  
    {  
        tile_static int localA[BLOCK_DIM];  
  
        index<1> globalIdx = t_idx.global * stride_size;  
        index<1> localIdx = t_idx.local;  
  
        localA[localIdx[0]] =  A[globalIdx];  
  
        t_idx.barrier.wait();  
  
        // Aggregate all elements in one tile into the first element.  
        for (int i = BLOCK_DIM / 2; i > 0; i /= 2)   
        {  
            if (localIdx[0] < i)   
            {  
  
                localA[localIdx[0]] += localA[localIdx[0] + i];  
            }  
  
            t_idx.barrier.wait();  
        }  
  
        if (localIdx[0] == 0)  
        {  
            A[globalIdx] = localA[0];  
        }  
    }  
  
    int size_after_padding(int n)  
    {  
        // The extent might have to be slightly bigger than num_stride to   
        // be evenly divisible by BLOCK_DIM. You can do this by padding with zeros.  
        // The calculation to do this is BLOCK_DIM * ceil(n / BLOCK_DIM)  
        return ((n - 1) / BLOCK_DIM + 1) * BLOCK_DIM;  
    }  
  
    int reduction_sum_gpu_kernel(array<int, 1> input)   
    {  
        int len = input.extent[0];  
  
        //Tree-based reduction control that uses the CPU.  
        for (int stride_size = 1; stride_size < len; stride_size *= BLOCK_DIM)   
        {  
            // Number of useful values in the array, given the current  
            // stride size.  
            int num_strides = len / stride_size;    
  
            extent<1> e(size_after_padding(num_strides));  
  
            // The sum kernel that uses the GPU.  
            parallel_for_each(extent<1>(e).tile<BLOCK_DIM>(), [&input, stride_size] (tiled_index<BLOCK_DIM> idx) restrict(amp)  
            {  
                sum_kernel_tiled(idx, input, stride_size);  
            });  
        }  
  
        array_view<int, 1> output = input.section(extent<1>(1));  
        return output[0];  
    }  
  
    int cpu_sum(const std::vector<int> &arr) {  
        int sum = 0;  
        for (size_t i = 0; i < arr.size(); i++) {  
            sum += arr[i];  
        }  
        return sum;  
    }  
  
    std::vector<int> rand_vector(unsigned int size) {  
        srand(2011);  
  
        std::vector<int> vec(size);  
        for (size_t i = 0; i < size; i++) {  
            vec[i] = rand();  
        }  
        return vec;  
    }  
  
    array<int, 1> vector_to_array(const std::vector<int> &vec) {  
        array<int, 1> arr(vec.size());  
        copy(vec.begin(), vec.end(), arr);  
        return arr;  
    }  
  
    int _tmain(int argc, _TCHAR* argv[])  
    {  
        std::vector<int> vec = rand_vector(10000);  
        array<int, 1> arr = vector_to_array(vec);  
  
        int expected = cpu_sum(vec);  
        int actual = reduction_sum_gpu_kernel(arr);  
  
        bool passed = (expected == actual);  
        if (!passed) {  
            printf("Actual (GPU): %d, Expected (CPU): %d", actual, expected);  
        }  
        printf("sum: %s\n", passed ? "Passed!" : "Failed!");   
  
        getchar();  
  
        return 0;  
    }  
  
    ```  
  
9. 在功能表列上，選擇 \[**檔案**\]、\[**全部儲存**\]。  
  
10. 在**方案總管中**，開啟快顯功能表的  **AMPMapReduce**，然後選擇 **屬性**。  
  
11. 在**屬性頁** 對話方塊的 **組態屬性**，選擇 **C\/C\+\+**， **先行編譯標頭**。  
  
12. 欲修改**先行編譯標頭** 屬性，請選取 **未使用先行編譯標頭檔**，然後選擇  **\[確定\]** 按鈕。  
  
13. 在功能表列上，選擇 \[**建置**\]、\[**建置方案**\]。  
  
## 偵錯 CPU 程式碼  
 在此程序，您將使用本機的 Windows 偵錯工具，以確定這個應用程式中的 CPU 程式碼正確。  特別有趣的是這個應用程式 CPU 程式碼的區段為`for`迴圈，在`reduction_sum_gpu_kernel`函式中。  在 GPU 上執行，可控制減少樹狀結構式平行 。  
  
### 要偵錯的 CPU 程式碼  
  
1.  在**方案總管中**，開啟快顯功能表的  **AMPMapReduce**，然後選擇 **屬性**。  
  
2.  在**屬性頁** 對話方塊的 **組態屬性**，選擇 **偵錯**。  請確認**本機 Windows 偵錯工具** 中已選取 **偵錯工具啟動**清單。  
  
3.  傳回程式碼編輯器。  
  
4.  下圖 \(大約行 67 行 70\) 所示的程式碼的行上設定中斷點。  
  
     ![CPU 中斷點](../../parallel/amp/media/campcpubreakpoints.png "CampCpuBreakpoints")  
CPU 中斷點  
  
5.  在功能表列上，選擇 \[**偵錯**\]、\[**開始偵錯**\]。  
  
6.  在**區域變數** 視窗中，尋找值為`stride_size`直到行 70 中斷點為止。  
  
7.  在功能表列上，選擇 \[**偵錯**\]、\[**停止偵錯**\]。  
  
## 偵錯 GPU 程式碼  
 本章節示範如何偵錯 GPU 程式碼，也就是包含在`sum_kernel_tiled`函式中的程式碼。  GPU 程式碼可平行計算整數，如"區塊"中的總和。  
  
### 若要偵錯的 GPU 程式碼  
  
1.  在**方案總管中**，開啟快顯功能表的  **AMPMapReduce**，然後選擇 **屬性**。  
  
2.  在**屬性頁** 對話方塊的 **組態屬性**，選擇 **偵錯**。  
  
3.  在 \[**要啟動的偵錯工具**\] 清單中，選取 \[**本機 Windows 偵錯工具**\]。  
  
4.  在 \[**偵錯工具類型**\] 清單中，選取 \[**僅限 GPU**\]。  
  
5.  選擇 \[**確定**\] 按鈕。  
  
6.  下圖所示，請在列 30 設定中斷點。  
  
     ![GPU 中斷點](../../parallel/amp/media/campgpubreakpoints.png "CampGpuBreakpoints")  
GPU 中斷點  
  
7.  在功能表列上，選擇 \[**偵錯**\]、\[**開始偵錯**\]。  行數 67 與 70 的 CPU 程式碼中的中斷點在 GPU 偵錯期間不會執行，因為 CPU 將會執行這些程式碼。  
  
### 若要使用 \[GPU 執行緒\] 視窗  
  
1.  若要開啟 \[GPU 執行緒\] 視窗，在功能表列中，選擇 **偵錯**，**視窗**，**GPU 執行緒**。  
  
     在 \[GPU 執行緒\] 視窗中，您可以檢閱 GPU 執行緒狀態。  
  
2.  停駐 GPU 執行緒視窗在 Visual Studio 的下方。  選擇 \[**展開執行緒切換**\] 按鈕以顯示 tile 和執行緒文字方塊。  GPU 執行緒 視窗中顯示使用中和已封鎖的 GPU 執行緒的總數，如下圖所示。  
  
     ![&#91;GPU 執行緒&#93; 視窗，顯示 4 個活動中執行緒](../../parallel/amp/media/campc.png "CampC")  
\[GPU 執行緒\] 視窗  
  
     有 313 區塊配置給這項計算。  每個區塊都包含 32 個執行緒。  因為在本機的軟體模擬器進行 GPU 偵錯，則會有四個作用中的 GPU 執行緒。  四個執行緒同時執行的指令，然後同時繼續下一個指令。  
  
     在 GPU 執行緒視窗、第 21 行 \(`t_idx.barrier.wait();`\)附近所定義 [tile\_barrier::wait](../Topic/tile_barrier::wait%20Method.md) 陳述式中有4個執行中、 28個被阻擋的GPU 執行緒。  所有 32 個 GPU 執行緒隸屬於第一個 tile，`tile[0]`。  箭頭指向的資料列，其中包含目前的執行緒。  若要切換到另一個執行緒，請使用下列方法之一：  
  
    -   在列中的執行緒切換至 \[GPU 執行緒\] 視窗中，開啟快顯功能表，然後選擇**切換至執行緒**。  如果資料列代表一個以上的執行緒，您會切換至第一個執行緒根據執行緒座標。  
  
    -   輸入執行緒的值到對應的 \[文字\] 方塊，然後選擇 **切換執行緒** 按鈕。  
  
     呼叫堆疊 視窗會顯示目前的 GPU 執行緒的呼叫堆疊。  
  
### 若要使用平行堆疊視窗  
  
1.  若要開啟 \[平行堆疊\] 視窗，在功能表列中，選擇 **偵錯**，**視窗**，**平行堆疊**。  
  
     您可以使用平行堆疊視窗，同時檢查多個 GPU 執行緒的堆疊框架。  
  
2.  在 Visual Studio 的底部停駐平行堆疊視窗。  
  
3.  請確定**執行緒**在左上角清單中被選取。  如下列圖例，您在 \[GPU 執行緒\] 視窗中會看到 GPU 執行緒的呼叫堆疊顯示於平行堆疊視窗中。  
  
     ![&#91;平行堆疊&#93; 視窗，顯示 4 個活動中執行緒](../../parallel/amp/media/campd.png "CampD")  
\[平行堆疊\] 視窗  
  
     32 個執行緒不同名稱儲存變更從`_kernel_stub`到 lambda 陳述式中透過`parallel_for_each`函式呼叫，並執行`sum_kernel_tiled`函式，減少平行的發生。在 32 個執行緒中的 28 個已進行至 [tile\_barrier::wait](../Topic/tile_barrier::wait%20Method.md) 陳述式，並會一直維持封鎖在行 22，而其他 4 個執行緒仍持續進行於`sum_kernel_tiled`在行 30 的函式。  
  
     您可以檢視可用的執行緒屬性在\[GPU 執行緒\] 視窗中，在豐富的資料型提示方塊中。  若要執行這項操作，將滑鼠指標停留在堆疊框架的 **sum\_kernel\_tiled**。  下圖顯示資料提示方塊。  
  
     ![&#91;平行堆疊&#93; 視窗的 DataTip](../../parallel/amp/media/campe.png "CampE")  
GPU 執行緒資料提示方塊  
  
     如需有關 \[平行堆疊\] 視窗的詳細資訊，請參閱[使用平行堆疊視窗](../Topic/Using%20the%20Parallel%20Stacks%20Window.md)。  
  
### 若要使用平行監看式視窗  
  
1.  若要開啟 \[平行監看式\] 視窗，在 \[功能表列\] 中，選擇 **偵錯**，**視窗**，**平行監看式**，**平行監看式 1**。  
  
     您可以使用 \[平行監看式\] 視窗來跨多重執行緒檢查運算式的值。  
  
2.  將 \[平行監看式 1\] 視窗停駐 Visual Studio 的底部。  在 \[平行監看式\] 視窗中有 32 個資料列。  分別對應到 出現在\[GPU 執行緒平行堆疊\] 視窗和 \[GPU 執行緒\] 視窗中的GPU執行緒。  現在，您可以輸入運算是來檢查所有 32 GPU 執行緒之中的哪一個的值。  
  
3.  選取 **新增監看式** 資料行行首中，輸入  `localIdx`，然後選擇 \[Enter\] 鍵。  
  
4.  選取  **新增監看式** 一次的資料行行首，輸入  `globalIdx`，然後選擇 \[Enter\] 鍵。  
  
5.  選取 **新增監看式** 一次的資料行行首，輸入  `localA [localIdx [0]]`，然後選擇 \[Enter\] 鍵。  
  
     您可以藉由選取其相對應的資料行行首排序指定的運算式。  
  
     選取  **localA \[localIdx \[0\]\]** 資料行行首來排序資料行。  下圖顯示由 **localA \[localIdx \[0\]\]**排序方式的結果。  
  
     ![&#91;平行監看式&#93; 視窗，顯示已排序的結果](../../parallel/amp/media/campf.png "CampF")  
 排序結果  
  
     可以藉由選擇 \[Excel\] 按鈕，然後選取 \[將平行監看式\] 視窗中的內容匯出至 Excel，接著選擇 **在 Excel 中開啟**。  如果您在開發電腦上安裝 Excel，這會開啟 Excel 工作表包含的內容。  
  
6.  在 \[平行監看式\] 視窗的右上角，沒有可供您使用的布林運算式來篩選內容篩選器控制項。  在篩選條件控制文字方塊中請輸入 `localA [localIdx [0]] >  20000`，然後選擇 \[Enter\] 鍵。  
  
     \[視窗\] 現在只包含執行緒的`localA[localIdx[0]]`值大於 20000。  內容仍會按照`localA[localIdx[0]]`資料行排序，也就是您稍早執行的排序動作。  
  
## 標幟 GPU 執行緒  
 您可以標示特定的 GPU 執行緒於 \[GPU 執行緒\] 視窗中、 \[平行監看式\] 視窗中或在 \[平行堆疊\] 視窗中的資料提示方塊中。  如果 \[GPU 執行緒\] 視窗中的資料列包含一個以上的執行緒，標示該資料列旗標的列中包含所有執行緒。  
  
### 若要加上旗標於 GPU 執行緒  
  
1.  選取  **\[執行緒\]** 資料行行首來排序 tile 索引和執行緒索引的 \[平行監看式 1\] 視窗中。  
  
2.  在功能表列上，選擇 **偵錯**， **繼續**，而導致四個執行緒進行到下一次 \(在 AMPMapReduce.cpp 32 行定義\) 的防護機制。  
  
3.  選擇包含四個目前作用中的執行緒的資料列左邊的旗標符號。  
  
     下圖顯示 \[GPU 執行緒\] 視窗中的四個作用中加上旗標的執行緒。  
  
     ![包含已標幟執行緒的 &#91;GPU 執行緒&#93; 視窗](../../parallel/amp/media/campg.png "CampG")  
\[GPU 執行緒\] 視窗中正在活動的執行緒  
  
     \[平行監看式\] 視窗和視窗的 \[平行堆疊\] 資料提示方塊兩者皆可指出加上旗標的執行緒。  
  
4.  如果您想要把焦點放在已標幟的四個執行緒上，您可以選擇在 GPU 執行緒、 平行監看式和平行堆疊視窗中顯示加上旗標的執行緒。  
  
     請選擇僅顯示加上旗標按鈕上任何的視窗或**偵錯位置**工具列。  下圖顯示 \[僅顯示加上旗標\] 按鈕，在**偵錯位置**工具列。  
  
     ![偵錯位置工具列，包含僅顯示已標幟的項目圖示](../../parallel/amp/media/camph.png "CampH")  
\[僅顯示已標幟的項目\] 按鈕  
  
     現在 \[GPU 執行緒\]、 \[平行監看式\] 和 \[平行堆疊\] 視窗會顯示加上旗標的執行緒。  
  
## 凍結和解除凍結 GPU 執行緒  
 您可以從 \[GPU 執行緒\] 視窗或 \[平行監看式\] 視窗凍結 \(暫停\) 和解除凍結 \(繼續\) GPU 執行緒。  您可以以相同的方式凍結及解除凍結 CPU 執行緒。 如需資訊，請參閱[如何：使用執行緒視窗](../Topic/How%20to:%20Use%20the%20Threads%20Window.md)。  
  
### 若要凍結及解除凍結 GPU 執行緒  
  
1.  選擇**僅顯示加上旗標** \] 按鈕以顯示所有執行緒。  
  
2.  在功能表列上，選擇 **偵錯**， **繼續**。  
  
3.  開啟使用中的資料列的快顯功能表，然後選擇**凍結**。  
  
     \[GPU 執行緒\] 視窗中的下方將顯示四個執行緒已凍結。  
  
     ![顯示已凍結之執行緒的 &#91;GPU 執行緒&#93; 視窗](../../parallel/amp/media/campk.png "CampK")  
\[GPU 執行緒\] 視窗中已凍結的執行緒  
  
     同樣地，\[平行監看式\] 視窗會顯示四個執行緒都已凍結。  
  
4.  在功能表列上，選擇 **偵錯**， **繼續**好讓四個 GPU 執行緒障礙繼續在行 22 的進度，並到達在 30 列的中斷點。  \[GPU 執行緒\] 視窗會顯示四個先前凍結的執行緒保持已凍結和作用中狀態。  
  
5.  在功能表列上，選擇 **偵錯**， **繼續**。  
  
6.  從 \[平行監看式\] 視窗中，您也可以解除個別或多重 GPU 執行緒。  
  
### 群組 GPU 往來執行緒  
  
1.  快顯功能表上的其中一個執行緒在 **GPU 執行緒** 視窗中，選擇  **Group By**， **位址**。  
  
     \[GPU 執行緒\] 視窗中的執行緒會依 \[位址\] 來分組。  位址對應到中每個已鎖定執行緒群的反組譯碼。24 的執行緒都在行 22 其中[tile\_barrier::wait 方法](../Topic/tile_barrier::wait%20Method.md)會執行。12 的執行緒是在第 32 行屏障的指令。  四個這些執行緒被設定旗標。  八個執行緒會在中斷點行 30。  四個執行緒會凍結。  下圖顯示 \[GPU 執行緒\] 視窗中群組的執行緒。  
  
     ![&#91;GPU 執行緒&#93; 視窗，顯示依 &#91;位址&#93; 分組的執行緒](../../parallel/amp/media/campl.png "CampL")  
群組 \[GPU 執行緒\] 視窗中的執行緒  
  
2.  您也可以執行 **Group By** 作業，藉由開啟快顯功能表的平行監看式\] 視窗中，資料格來選擇 **Group By**，然後再選擇 \[功能表項目\] 根據於您要分組執行緒的方式。  
  
## 執行程式碼特定位置中的所有執行緒  
 您可以執行在指定的 tile 中的所有執行緒包含游標的那一行藉由執行 \[**執行目前 Tile 至游標處**\]。  
  
### 若要以資料指標所標示的位置執行的所有執行緒  
  
1.  在已凍結的執行緒的快顯功能表中選擇**解除凍結**。  
  
2.  在程式碼編輯器中，將游標移動至列 30。  
  
3.  在快顯功能表的 \[程式碼編輯器\] 中，選擇 **執行目前區塊至游標處**。  
  
     先前已封鎖在第 21 行的阻礙的 24 個執行緒已經進行到 32 行。  這會顯示在 **GPU 執行緒**視窗。  
  
## 請參閱  
 [C\+\+ AMP 概觀](../../parallel/amp/cpp-amp-overview.md)   
 [偵錯 GPU 程式碼](../Topic/Debugging%20GPU%20Code.md)   
 [如何：使用 GPU 執行緒視窗](../Topic/How%20to:%20Use%20the%20GPU%20Threads%20Window.md)   
 [如何：使用平行監看式視窗](../Topic/How%20to:%20Use%20the%20Parallel%20Watch%20Window.md)   
 [使用 Concurrency Visualizer 分析 C\+\+ AMP 程式碼](http://go.microsoft.com/fwlink/?LinkID=253987&clcid=0x409)