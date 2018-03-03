---
title: "逐步解說： 偵錯 c + + AMP 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- debugging, C++ Accelerated Massive Parallelism
- C++ AMP, debugging
- C++ Accelerated Massive Parallelism, debugging
- debugging, C++ AMP
ms.assetid: 40e92ecc-f6ba-411c-960c-b3047b854fb5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8cfc12a238ccaff90fa7c22e8a67d8e10d0796e6
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="walkthrough-debugging-a-c-amp-application"></a>逐步解說：偵錯 C++ AMP 應用程式
本主題示範如何使用 c + + Accelerated Massive Parallelism (c + + AMP) 若要善用圖形處理單元 (GPU) 的應用程式進行偵錯。 它會使用平行縮減程式，有個加總整數的大型陣列。 這個逐步解說將說明下列工作：  
  
-   正在啟動 GPU 偵錯工具。  
  
-   檢查 [GPU 執行緒] 視窗中的 GPU 執行緒。  
  
-   使用平行堆疊 視窗可以同時發現多個 GPU 執行緒的呼叫堆疊。  
  
-   使用 [平行監看式] 視窗來檢查跨多個執行緒的單一運算式中的值，在相同的時間。  
  
-   加上旗標、 凍結、 解除凍結，和群組 GPU 執行緒。  
  
-   在程式碼中執行所有執行緒的磚至特定位置。  
  
## <a name="prerequisites"></a>必要條件  
 開始本逐步解說之前：  
  
-   讀取[c + + AMP 概觀](../../parallel/amp/cpp-amp-overview.md)。  
  
-   請確定該行文字編輯器中顯示的數字。 如需詳細資訊，請參閱[How to： 在編輯器中顯示行號](/visualstudio/ide/reference/how-to-display-line-numbers-in-the-editor)。  
  
-   請確定您執行[!INCLUDE[win8](../../build/reference/includes/win8_md.md)]或[!INCLUDE[winserver8](../../build/reference/includes/winserver8_md.md)]以支援在軟體模擬器上偵錯。  
  
 [!INCLUDE[note_settings_general](../../mfc/includes/note_settings_general_md.md)]  
  
### <a name="to-create-the-sample-project"></a>建立範例專案  
  
1.  啟動 Visual Studio。  
  
2.  在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。  
  
3.  在下**已安裝**在範本窗格中，選擇  **Visual c + +**。  
  
4.  選擇**Win32 主控台應用程式**，型別`AMPMapReduce`中**名稱**方塊，然後再選擇**確定** 按鈕。  
  
5.  選擇 [下一步] 按鈕。  
  
6.  清除**先行編譯標頭**核取方塊，，然後選擇 [**完成**] 按鈕。  
  
7.  在**方案總管 中**，從專案刪除 stdafx.h、 targetver.h 和 stdafx.cpp。  
  
8.  開啟 AMPMapReduce.cpp 並將其內容取代下列程式碼。  
  
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
        printf("sum: %s\n", passed  "Passed!" : "Failed!");   
  
        getchar();  
  
        return 0;  
    }  
  
 ```  
  
9. 在功能表列上，依序選擇 [檔案] 和 [全部儲存]。  
  
10. 在**方案總管] 中**，開啟捷徑功能表**AMPMapReduce**，然後選擇 [**屬性**。  
  
11. 在**屬性頁**對話方塊的 **組態屬性**，選擇**C/c + +**，**先行編譯標頭**。  
  
12. 如**先行編譯標頭**屬性選取**未使用先行編譯標頭**，然後選擇 [ **[確定]** ] 按鈕。  
  
13. 在功能表列上，選擇 [建置] 、[建置方案] 。  
  
## <a name="debugging-the-cpu-code"></a>偵錯 CPU 程式碼  
 在此程序，您將使用本機 Windows 偵錯工具，並確定在此應用程式的 CPU 程式碼正確。 在此會特別有趣的應用程式的 CPU 程式碼的區段是`for`迴圈`reduction_sum_gpu_kernel`函式。 它可控制樹狀結構為基礎平行減少 GPU 上執行。  
  
### <a name="to-debug-the-cpu-code"></a>若要偵錯的 CPU 程式碼  
  
1.  在**方案總管] 中**，開啟捷徑功能表**AMPMapReduce**，然後選擇 [**屬性**。  
  
2.  在**屬性頁**對話方塊的 **組態屬性**，選擇**偵錯**。 確認**本機 Windows 偵錯工具**中選取**偵錯工具啟動**清單。  
  
3.  傳回程式碼編輯器。  
  
4.  圖 （大約行 67 行 70） 中顯示的程式碼行上設定中斷點。  
  
     ![CPU 中斷點](../../parallel/amp/media/campcpubreakpoints.png "campcpubreakpoints")  
CPU 中斷點  
  
5.  在功能表列上，選擇 [偵錯]、[開始偵錯]。  
  
6.  在**區域變數**視窗中，觀察到的值`stride_size`在列 70 中斷點為止。  
  
7.  在功能表列上，選擇 [偵錯]、[停止偵錯]。  
  
## <a name="debugging-the-gpu-code"></a>偵錯 GPU 程式碼  
 本節說明如何偵錯 GPU 程式碼，也就是包含的程式碼中`sum_kernel_tiled`函式。 GPU 程式碼會以平行方式計算總和的每個 「 區塊 」 的整數。  
  
### <a name="to-debug-the-gpu-code"></a>若要偵錯 GPU 程式碼  
  
1.  在**方案總管] 中**，開啟捷徑功能表**AMPMapReduce**，然後選擇 [**屬性**。  
  
2.  在**屬性頁**對話方塊的 **組態屬性**，選擇**偵錯**。  
  
3.  在**偵錯工具啟動**清單中，選取**本機 Windows 偵錯工具**。  
  
4.  在**偵錯工具類型**清單中，選取**僅限 GPU**。  
  
5.  選擇 [確定]  按鈕。  
  
6.  在行 30、 設定中斷點，在下圖所示。  
  
     ![GPU 中斷點](../../parallel/amp/media/campgpubreakpoints.png "campgpubreakpoints")  
GPU 中斷點  
  
7.  在功能表列上，選擇 [偵錯]、[開始偵錯]。 在 GPU 偵錯，因為在 CPU 上執行這些程式碼行時，不會執行行 67 和 70 的 CPU 程式碼中的中斷點。  
  
### <a name="to-use-the-gpu-threads-window"></a>若要使用 [GPU 執行緒] 視窗  
  
1.  若要開啟 GPU 執行緒 視窗中的，功能表列上選擇 **偵錯**， **Windows**， **GPU 執行緒**。  
  
     您可以檢查狀態會顯示 GPU 執行緒 視窗中的 GPU 執行緒。  
  
2.  停駐在 Visual Studio 底部 [GPU 執行緒] 視窗。 選擇**展開執行緒切換** 按鈕以顯示 tile 和執行緒的文字方塊。 下圖所示，[GPU 執行緒] 視窗會顯示作用中和已封鎖的 GPU 執行緒的總數。  
  
     ![GPU 執行緒 視窗，顯示 4 個使用中執行緒](../../parallel/amp/media/campc.png "campc")  
[GPU 執行緒] 視窗  
  
     有 313 配置給這項計算的磚。 每個圖格包含 32 個執行緒。 由於本機 GPU 偵錯發生在軟體模擬器上，有四個作用中的 GPU 執行緒。 四個執行緒同時執行指令，然後移一起至下一個指令。  
  
     在 [GPU 執行緒] 視窗中，有四個 GPU 執行緒使用中和 28 的 GPU 執行緒封鎖在[tile_barrier:: wait](reference/tile-barrier-class.md#wait)第 21 行定義在陳述式 (`t_idx.barrier.wait();`)。 所有 32 的 GPU 執行緒屬於第一個磚， `tile[0]`。 箭號會指向包含目前執行緒的資料列。 若要切換至不同的執行緒，請使用下列方法之一：  

  
    -   在切換至 GPU 執行緒 視窗中的執行緒列中，開啟捷徑功能表並選擇 **切換至執行緒**。 如果資料列都代表一個以上的執行緒，您將切換至執行緒座標根據第一個執行緒。  
  
    -   在對應的文字方塊中輸入 tile 和執行緒的執行緒的值，然後選擇**切換執行緒** 按鈕。  
  
     [呼叫堆疊] 視窗會顯示目前的 GPU 執行緒的呼叫堆疊。  
  
### <a name="to-use-the-parallel-stacks-window"></a>若要使用平行堆疊 視窗  
  
1.  若要開啟 [平行堆疊] 視窗中的，功能表列上，選擇**偵錯**， **Windows**，**平行堆疊**。  
  
     您可以使用 [平行堆疊] 視窗，同時檢查多個 GPU 執行緒的堆疊框架。  
  
2.  停駐 平行堆疊 視窗底部的 Visual Studio。  
  
3.  請確定**執行緒**在左上角的清單中選取。 在下圖中，平行堆疊 視窗會顯示呼叫堆疊已取得焦點的檢視您在 GPU 執行緒 視窗中看到 GPU 執行緒。  
  
     ![平行堆疊 視窗，顯示 4 個使用中執行緒](../../parallel/amp/media/campd.png "campd")  
[平行堆疊] 視窗  
  
     32 個執行緒發生從`_kernel_stub`中的 lambda 陳述式`parallel_for_each`函式呼叫，然後在`sum_kernel_tiled`函式，其中平行減少，就會發生。 28 超出 32 個執行緒已進入[tile_barrier:: wait](reference/tile-barrier-class.md#wait)陳述式並維持在列 22，已封鎖，而其他 4 個執行緒仍在作用中`sum_kernel_tiled`函式在列 30。  

  
     您可以檢查平行堆疊 視窗中的豐富資料提示方塊中的 GPU 執行緒 視窗中可用的 GPU 執行緒屬性。 若要這樣做，請將滑鼠指標的堆疊框架上**sum_kernel_tiled**。 下圖顯示資料提示方塊。  
  
     ![平行堆疊 視窗的 DataTip](../../parallel/amp/media/campe.png "campe")  
GPU 執行緒資料提示方塊  
  
     如需有關 [平行堆疊] 視窗的詳細資訊，請參閱[使用平行堆疊視窗](/visualstudio/debugger/using-the-parallel-stacks-window)。  
  
### <a name="to-use-the-parallel-watch-window"></a>若要使用平行監看式視窗  
  
1.  若要開啟 平行監看式視窗中的，功能表列上選擇**偵錯**， **Windows**，**平行監看式**，**平行監看式 1**。  
  
     您可以使用 [平行監看式] 視窗來檢查運算式的值跨多個執行緒。  
  
2.  [平行監看式 1] 視窗停駐於 Visual Studio 底部。 [平行監看式] 視窗的資料表中有 32 個資料列。 每一個都對應到出現在 GPU 執行緒 視窗和平行堆疊 視窗中的 GPU 執行緒。 現在，您可以輸入您想要檢查所有 32 的 GPU 執行緒其值的運算式。  
  
3.  選取**加入監看式**資料行標頭，請輸入`localIdx`，然後選擇 Enter 鍵。  
  
4.  選取**加入監看式**一次資料行標頭中，輸入`globalIdx`，然後選擇 Enter 鍵。  
  
5.  選取**加入監看式**一次資料行標頭中，輸入`localA[localIdx[0]]`，然後選擇 Enter 鍵。  
  
     您可以選取其對應的資料行標頭來排序所指定的運算式。  
  
     選取**localA [localIdx [0]]**欄標題來排序資料行。 下圖顯示依排序的結果**localA [localIdx [0]]**。  
  
     ![已排序的結果與平行監看式視窗](../../parallel/amp/media/campf.png "campf")  
 排序結果  
  
     您可以選擇 [Excel] 按鈕，然後選擇 [平行監看式] 視窗中的內容將匯出至 Excel**在 Excel 中開啟**。 如果您有在開發電腦上安裝 Excel 時，這會開啟 Excel 工作表，包含的內容。  
  
6.  [平行監看式] 視窗右上角，在沒有篩選器控制項可讓您使用布林運算式來篩選的內容。 Enter`localA[localIdx[0]] > 20000`篩選控制項文字方塊方塊，然後選擇 Enter 鍵。  
  
     此視窗現在包含只所在的執行緒`localA[localIdx[0]]`值大於 20000。 內容仍然依照`localA[localIdx[0]]`資料行，也就是您稍早執行的排序動作。  
  
## <a name="flagging-gpu-threads"></a>GPU 執行緒加上旗標  
 您可以標示特定 GPU 執行緒加上這些旗標 [GPU 執行緒] 視窗、 [平行監看式] 視窗中或 [平行堆疊] 視窗中的資料提示方塊中。 如果 [GPU 執行緒] 視窗中的資料列包含一個以上的執行緒，該資料列加上旗標旗標所包含的資料列中的所有執行緒。  
  
### <a name="to-flag-gpu-threads"></a>GPU 執行緒加上旗標  
  
1.  選取**[執行緒]**資料行標頭來排序的磚索引和執行緒索引的 [平行監看式 1] 視窗中。  
  
2.  在功能表列上選擇 **偵錯**，**繼續**，因而導致四個執行緒，皆為作用中下一個屏障 （定義在一行 32 AMPMapReduce.cpp） 的進度。  
  
3.  選擇包含四個執行緒，且現在使用的資料列左側的旗標符號。  
  
     下圖顯示四個作用中已標幟的執行緒在 [GPU 執行緒] 視窗中。  
  
     ![已標幟的執行緒，[GPU 執行緒] 視窗](../../parallel/amp/media/campg.png "campg")  
[GPU 執行緒] 視窗中正在活動的執行緒  
  
     [平行監看式] 視窗和 [平行堆疊] 視窗的這兩個資料提示方塊表示已標幟的執行緒。  
  
4.  如果您想要專注您加上旗標的四個執行緒上，您可以選擇在 GPU 執行緒、 平行監看式 和 平行堆疊視窗中顯示已標幟的執行緒。  
  
     選擇 僅顯示已標幟按鈕在任何 windows 或在**偵錯位置**工具列。 下圖顯示 [僅顯示已標幟] 按鈕上**偵錯位置**工具列。  
  
     ![偵錯位置工具列，以僅顯示有旗標圖示](../../parallel/amp/media/camph.png "camph")  
[僅顯示已標幟的項目] 按鈕  
  
     現在 [GPU 執行緒、 平行監看式] 和 [平行堆疊] 視窗會顯示已標幟的執行緒。  
  
## <a name="freezing-and-thawing-gpu-threads"></a>凍結和解除凍結 GPU 執行緒  
 您可以凍結 （暫止） 和解除凍結 （繼續） 從 GPU 執行緒 視窗或 平行監看式 視窗的 GPU 執行緒。 您可以凍結和解除凍結 CPU 執行緒相同的方式;如需資訊，請參閱[How to： 使用執行緒視窗](/visualstudio/debugger/how-to-use-the-threads-window)。  
  
### <a name="to-freeze-and-thaw-gpu-threads"></a>若要凍結和解除凍結 GPU 執行緒  
  
1.  選擇**僅顯示已標幟** 按鈕以顯示所有執行緒。  
  
2.  在功能表列上選擇 **偵錯**，**繼續**。  
  
3.  開啟作用中的資料列的捷徑功能表，然後選擇**凍結**。  
  
     [GPU 執行緒] 視窗的下圖會顯示所有的四個執行緒已遭到凍結。  
  
     ![GPU 執行緒視窗顯示已凍結的執行緒](../../parallel/amp/media/campk.png "campk")  
[GPU 執行緒] 視窗中已凍結的執行緒  
  
     同樣地，[平行監看式] 視窗會顯示所有的四個執行緒已遭到凍結。  
  
4.  在功能表列上選擇 **偵錯**，**繼續**允許四個 GPU 執行緒進展超過屏障在列 22 和到達中斷點在列 30。 [GPU 執行緒] 視窗會顯示四個先前已凍結的執行緒，保持凍結和作用中狀態。  
  
5.  在功能表列上選擇 **偵錯**，**繼續**。  
  
6.  從 [平行監看式] 視窗中，您可以也解除凍結個別或多個 GPU 執行緒。  
  
### <a name="to-group-gpu-threads"></a>若要群組 GPU 執行緒  
  
1.  其中一個執行緒中的捷徑功能表上**GPU 執行緒**視窗中，選擇**Group By**，**位址**。  
  
     在 [GPU 執行緒] 視窗中的執行緒會分組位址。 位址對應到每個執行緒群組所在的反組譯碼中的指示。 24 執行緒位於行 22 其中[tile_barrier:: wait 方法](reference/tile-barrier-class.md#wait)執行。 12 執行緒都可以在列 32 屏障的指示。 四個這些執行緒會加上旗標。 8 個執行緒會在行 30 的中斷點處。 四個這些執行緒會凍結。 下圖顯示在 [GPU 執行緒] 視窗中的群組的執行緒。  

  
     ![依位址分組的 GPU 執行緒 視窗與執行緒](../../parallel/amp/media/campl.png "campl")  
[GPU 執行緒] 視窗中的群組的執行緒  
  
2.  您也可以執行**Group By**作業開啟資料格的 [平行監看式] 視窗的捷徑功能表選擇**Group By**，然後選擇您要如何對應的功能表項目若要群組執行緒。  
  
## <a name="running-all-threads-to-a-specific-location-in-code"></a>執行程式碼中的特定位置的所有執行緒  
 所有執行緒在給定的磚中都執行使用包含游標的那一行**都執行目前磚至游標處**。  
  
### <a name="to-run-all-threads-to-the-location-marked-by-the-cursor"></a>若要執行所有執行緒資料指標所標記的位置  
  
1.  在已凍結的執行緒的捷徑功能表，選擇 **解除凍結**。  
  
2.  在程式碼編輯器中，將游標放在一行 30。  
  
3.  程式碼編輯器的捷徑功能表，選擇 **執行目前磚至游標處**。  
  
     24 先前已封鎖在第 21 行在屏障的執行緒已進入列 32。 這會顯示在**GPU 執行緒**視窗。  
  
## <a name="see-also"></a>請參閱  
 [C + + AMP 概觀](../../parallel/amp/cpp-amp-overview.md)   
 [偵錯 GPU 程式碼](/visualstudio/debugger/debugging-gpu-code)   
 [如何： 使用 GPU 執行緒視窗](/visualstudio/debugger/how-to-use-the-gpu-threads-window)   
 [如何： 使用平行監看式視窗](/visualstudio/debugger/how-to-use-the-parallel-watch-window)   
 [分析 c + + AMP 程式碼，使用 並行視覺化檢視](http://go.microsoft.com/fwlink/p/?linkid=253987&clcid=0x409)

