---
title: 逐步解說：進行 AMP C++應用程式的偵錯工具
ms.date: 04/23/2019
helpviewer_keywords:
- debugging, C++ Accelerated Massive Parallelism
- C++ AMP, debugging
- C++ Accelerated Massive Parallelism, debugging
- debugging, C++ AMP
ms.assetid: 40e92ecc-f6ba-411c-960c-b3047b854fb5
ms.openlocfilehash: 0c9fb5588cfd44c83d8fe72c7c4aede0fedab672
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "69631590"
---
# <a name="walkthrough-debugging-a-c-amp-application"></a>逐步解說：進行 AMP C++應用程式的偵錯工具

本主題示範如何使用C++加速的大規模平行處理原則（C++ AMP），來對應用程式進行 debug，以利用圖形處理器（GPU）。 它會使用平行縮減程式來增加大量整數陣列的總和。 這個逐步解說將說明下列工作：

- 啟動 GPU 偵錯工具。

- 在 [GPU 執行緒] 視窗中檢查 GPU 執行緒。

- 使用 [**平行堆疊**] 視窗同時觀察多個 GPU 執行緒的呼叫堆疊。

- 使用 [**平行監看**式] 視窗，在多個執行緒上同時檢查單一運算式的值。

- 標記、凍結、解除凍結和分組 GPU 執行緒。

- 以程式碼中的特定位置執行磚的所有線程。

## <a name="prerequisites"></a>必要條件

開始進行本逐步解說之前：

- 閱讀[ C++ AMP 總覽](../../parallel/amp/cpp-amp-overview.md)。

- 請確定行號顯示在文字編輯器中。 如需詳細資訊，請參閱[如何：在編輯器](/visualstudio/ide/reference/how-to-display-line-numbers-in-the-editor)中顯示行號。

- 請確定您至少執行 Windows 8 或 Windows Server 2012，以支援軟體模擬器上的偵錯工具。 

[!INCLUDE[note_settings_general](../../mfc/includes/note_settings_general_md.md)]

### <a name="to-create-the-sample-project"></a>建立範例專案

建立專案的指示會根據您使用的 Visual Studio 版本而有所不同。 請確定您已在此頁面的左上方選取正確的版本。

::: moniker range="vs-2019"

### <a name="to-create-the-sample-project-in-visual-studio-2019"></a>若要在 Visual Studio 2019 中建立範例專案

1. 在功能表列上，選擇 [檔案] > [新增] > [專案]，以開啟 [建立新專案] 對話方塊。

1. 在對話方塊頂端，將 [語言] 設定為 **C++** ，將 [平台] 設定為 **Windows**，並將 [專案類型] 設定為**主控台**。 

1. 從專案類型的篩選清單中，選擇 [主控台應用程式]，然後選擇 [下一步]。 在下一頁的 [名稱] 方塊中輸入 `AMPMapReduce` 以指定專案名稱，並依照需要指定專案位置。

   ![將專案命名為](../../build/media/mathclient-project-name-2019.png "將專案命名為")

1. 選擇 [建立] 按鈕以建立用戶端專案。

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-the-sample-project-in-visual-studio-2017-or-visual-studio-2015"></a>若要在 Visual Studio 2017 或 Visual Studio 2015 中建立範例專案

1. 啟動 Visual Studio。

1. 在功能表列上，選擇 [檔案] > [新增] > [專案]。

1. 在 [**已安裝**] 的 [範本] 窗格中，選擇 [**視覺效果C++** ]

1. 選擇 [ **Win32 主控台應用程式**]，在 [ `AMPMapReduce` **名稱**] 方塊中輸入，然後選擇 [**確定]** 按鈕。

1. 選擇 [下一步] 按鈕。

1. 清除 [先行**編譯頭**檔] 核取方塊，然後選擇 [**完成]** 按鈕。

1. 在**方案總管**中，從專案中刪除*stdafx.h*、 *targetver.h*和*stdafx.h。*

::: moniker-end

下一個主題：

8. 開啟 AMPMapReduce，並將其內容取代為下列程式碼。

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

9. 在功能表列上，依序選擇 [檔案] > [全部儲存]。

10. 在**方案總管**中，開啟**AMPMapReduce**的快捷方式功能表，然後選擇 [**屬性**]。

11. 在 [**屬性頁**] 對話方塊的 [設定**屬性**] 下，選擇 [ **CC++/**  > 先行**編譯頭**檔]。

12. 針對 [先行**編譯頭**檔] 屬性，選取 [**不使用先行編譯頭**檔]，然後選擇 [**確定]** 按鈕。

13. 在功能表列上選擇 [建置] > [建置解決方案]。

## <a name="debugging-the-cpu-code"></a>對 CPU 程式碼進行偵錯工具

在此程式中，您將使用本機 Windows 偵錯工具來確保此應用程式中的 CPU 代碼正確。 此應用程式中的 CPU 代碼區段特別有趣，是函式`for` `reduction_sum_gpu_kernel`中的迴圈。 它會控制在 GPU 上執行的樹狀結構平行縮減。

### <a name="to-debug-the-cpu-code"></a>若要對 CPU 程式碼進行偵錯工具

1. 在**方案總管**中，開啟**AMPMapReduce**的快捷方式功能表，然後選擇 [**屬性**]。

2. 在 [**屬性頁**] 對話方塊的 [設定**屬性**] 下，選擇 [**調試**]。 確認已在偵錯工具中選取 [**本機 Windows 偵錯工具**]**以啟動**清單。

3. 返回程式**代碼編輯器**。

4. 在下圖所示的程式程式碼上設定中斷點（大約行67行70）。

   ![CPU 中斷點](../../parallel/amp/media/campcpubreakpoints.png "CPU 中斷點") <br/>
   CPU 中斷點

5. 在功能表列上，依序選擇 [偵錯] > [開始偵錯]。

6. 在 [**區域變數**] 視窗中，觀察的`stride_size`值，直到到達位於第70行的中斷點。

7. 在功能表列上，依序選擇 [偵錯] > [停止偵錯]。

## <a name="debugging-the-gpu-code"></a>對 GPU 程式碼進行偵錯工具

本節說明如何將 GPU 程式碼（也就是包含在函式中`sum_kernel_tiled`的程式碼）加以調試。 GPU 程式碼會以平行方式計算每個「區塊」的整數總和。

### <a name="to-debug-the-gpu-code"></a>若要對 GPU 程式碼進行偵錯工具

1. 在**方案總管**中，開啟**AMPMapReduce**的快捷方式功能表，然後選擇 [**屬性**]。

2. 在 [**屬性頁**] 對話方塊的 [設定**屬性**] 下，選擇 [**調試**]。

3. 在 [要啟動的偵錯工具] 清單中，選取 [本機 Windows 偵錯工具]。

4. 在 [**偵錯工具類型**] 清單中，確認已選取 [**自動**]。

    **Auto**是預設值。 在 Windows 10 之前，**只有 GPU**是必要的值，而不是**Auto**。

5. 選擇 [確定] 按鈕。

6. 在第30行設定中斷點，如下圖所示。

   ![GPU 中斷點](../../parallel/amp/media/campgpubreakpoints.png "GPU 中斷點") <br/>
   GPU 中斷點

7. 在功能表列上，依序選擇 [偵錯] > [開始偵錯]。 在 GPU 偵錯工具期間，CPU 程式67代碼中的中斷點不會執行70，因為這些程式程式碼會在 CPU 上執行。

### <a name="to-use-the-gpu-threads-window"></a>使用 GPU 執行緒視窗

1. 若要開啟 [ **GPU 執行緒**] 視窗，請在功能表列上選擇 [**調試** >  **Windows**  >  **GPU 執行緒**]。

   您可以在出現的 [ **Gpu 執行緒**] 視窗中，檢查 gpu 執行緒的狀態。

2. 將 [ **GPU 執行緒**] 視窗停駐在 Visual Studio 的底部。 選擇 [**展開執行緒切換**] 按鈕，以顯示 [磚] 和 [執行緒] 文字方塊。 [ **GPU 執行緒**] 視窗會顯示作用中和已封鎖的 GPU 執行緒總數，如下圖所示。

   ![具有4個使用中線程的 GPU 執行緒視窗](../../parallel/amp/media/campc.png "具有4個使用中線程的 GPU 執行緒視窗") <br/>
   [GPU 執行緒] 視窗

   有313個磚配置給此計算。 每個磚都包含32個執行緒。 由於本機 GPU 偵錯工具是在軟體模擬器上進行，因此有四個作用中的 GPU 執行緒。 四個執行緒會同時執行指示，然後將它們一起移至下一個指令。

   在 [ **GPU 執行緒**] 視窗中，有四個作用中的 gpu 執行緒，以及28個在大約第21行（`t_idx.barrier.wait();`）所定義的[tile_barrier：： wait](reference/tile-barrier-class.md#wait)語句封鎖的 gpu 執行緒。 所有 32 GPU 執行緒都屬於第一個磚`tile[0]`。 箭號指向包含目前線程的資料列。 若要切換至不同的執行緒，請使用下列其中一種方法：

    - 在 [ **GPU 執行緒**] 視窗中要切換的執行緒資料列中，開啟快捷方式功能表，然後選擇 [**切換至執行緒**]。 如果資料列代表一個以上的執行緒，您就會根據執行緒座標切換到第一個執行緒。

    - 在對應的文字方塊中輸入執行緒的磚和執行緒值，然後選擇 [**切換執行緒**] 按鈕。

   [**呼叫堆疊**] 視窗會顯示目前 GPU 執行緒的呼叫堆疊。

### <a name="to-use-the-parallel-stacks-window"></a>使用平行堆疊視窗

1. 若要開啟 [**平行堆疊**] 視窗，請在功能表列上選擇 [**調試** >  **Windows**  > **平行堆疊**]。

   您可以使用 [**平行堆疊**] 視窗，同時檢查多個 GPU 執行緒的堆疊框架。

2. 將 [**平行堆疊**] 視窗停駐在 Visual Studio 的底部。

3. 請確定在左上角的清單中已選取 [**執行緒**]。 在下圖中，[**平行堆疊**] 視窗會針對您在 [ **gpu 執行緒**] 視窗中看到的 gpu 執行緒，顯示以呼叫堆疊為主的觀點。

   ![具有4個使用中線程的平行堆疊視窗](../../parallel/amp/media/campd.png "具有4個使用中線程的平行堆疊視窗") <br/>
   [平行堆疊] 視窗

   32執行緒已從`_kernel_stub`函式`sum_kernel_tiled`呼叫`parallel_for_each`中的 lambda 語句進入，然後指向函式，以進行平行縮減。 32執行緒中有28個已移至[tile_barrier：： wait](reference/tile-barrier-class.md#wait)語句，並在第22行繼續封鎖，而其他4個執行緒在函式`sum_kernel_tiled`的第30行保持作用中狀態。

   您可以在 [**平行堆疊**] 視窗的豐富資料提示方塊中，檢查 [ **gpu 執行緒**] 視窗中可用的 gpu 執行緒屬性。 若要這麼做，請將滑鼠指標停留在**sum_kernel_tiled**的堆疊框架上。 下圖顯示資料提示。

   [![平行堆疊] 視窗的資料提示][(../../parallel/amp/media/campe.png "平行堆疊] 視窗的資料提示") <br/>
   GPU 執行緒資料提示

   如需 [**平行堆疊**] 視窗的詳細資訊，請參閱[使用平行堆疊視窗](/visualstudio/debugger/using-the-parallel-stacks-window)。

### <a name="to-use-the-parallel-watch-window"></a>若要使用 Parallel 監看式視窗

1. 若要開啟 [**平行監看**式] 視窗，請在功能表列上選擇 [ **Debug**  >  **Windows**  >  **parallel watch**  >  **Parallel watch 1**]。

   您可以使用 [**平行監看**式] 視窗，跨多個執行緒檢查運算式的值。

2. 將 [**平行監看式 1** ] 視窗停駐在 Visual Studio 的底部。 [**平行監看**式] 視窗的資料表中有32個數據列。 每個都對應到出現在 [GPU 執行緒] 視窗和 [**平行堆疊**] 視窗中的 gpu 執行緒。 現在，您可以輸入您想要在所有 32 GPU 執行緒上檢查其值的運算式。

3. 選取 [**新增監看式]** 欄`localIdx`標題，輸入，然後選擇**enter**鍵。

4. 再次選取 [**新增監看式]** 資料`globalIdx`行標題，輸入，然後選擇**Enter**鍵。

5. 再次選取 [**新增監看式]** 資料`localA[localIdx[0]]`行標題，輸入，然後選擇**Enter**鍵。

   您可以依指定的運算式排序，方法是選取其對應的資料行標題。

   選取**localA [localIdx [0]]** 資料行標題，以排序資料行。 下圖顯示依**localA [localIdx [0]]** 排序的結果。

   ![具有排序結果的平行監看式視窗](../../parallel/amp/media/campf.png "具有排序結果的平行監看式視窗") <br/>
   排序結果

   您可以選擇 [ **Excel** ] 按鈕，然後選擇 [**在 excel 中開啟**]，將 [**平行監看**式] 視窗中的內容匯出至 Excel。 如果您的開發電腦上已安裝 Excel，這會開啟包含內容的 Excel 工作表。

6. 在 [**平行監看**式] 視窗的右上角，有一個篩選控制項可供您使用布林運算式來篩選內容。 在`localA[localIdx[0]] > 20000` [篩選控制項] 文字方塊中輸入，然後選擇**enter**鍵。

   此視窗現在只包含`localA[localIdx[0]]`值大於20000的執行緒。 內容仍會依`localA[localIdx[0]]`資料行排序，這是您稍早執行的排序動作。

## <a name="flagging-gpu-threads"></a>標記 GPU 執行緒

您可以在 [ **Gpu 執行緒**] 視窗、[**平行監看**式] 視窗或 [**平行堆疊**] 視窗中的資料提示方塊中，標記特定的 GPU 執行緒。 如果 [GPU 執行緒] 視窗中的資料列包含一個以上的執行緒，則會將該資料列標示為包含在該資料列中的所有線程。

### <a name="to-flag-gpu-threads"></a>為 GPU 執行緒加上旗標

1. 選取 [**平行監看式 1** ] 視窗中的 **[執行緒]** 資料行標頭，依磚索引和執行緒索引進行排序。

2. 在功能表列上，選擇 [ **Debug**  >  **Continue**]，這會使四個作用中的執行緒進行下一個屏障（定義于 AMPMapReduce 的第32行）。

3. 選擇包含四個目前作用中線程的資料列左側的旗標符號。

   下圖顯示 [ **GPU 執行緒**] 視窗中的四個已加上旗標的執行緒。

   ![具有旗標之執行緒的 GPU 執行緒視窗](../../parallel/amp/media/campg.png "具有旗標之執行緒的 GPU 執行緒視窗") <br/>
   [GPU 執行緒] 視窗中正在活動的執行緒

   [平行**堆疊**] 視窗的 [**平行監看**式] 視窗和 [資料提示] 都會指出標示的執行緒。

4. 如果您想要將焦點放在您標示的四個執行緒上，您可以選擇在 [ **GPU 執行緒**]、[**平行監看式]** 和 [**平行堆疊**] 視窗中顯示，只有加上旗標的執行緒。

   選擇任何視窗或 [**調試位置**] 工具列上的 [**僅顯示標示**為旗標] 按鈕。 下圖顯示 [**調試位置**] 工具列上的 [**僅顯示標示**為旗標] 按鈕。

   ![具有僅顯示加上旗標圖示的 [調試位置] 工具列](../../parallel/amp/media/camph.png "具有僅顯示加上旗標圖示的 [調試位置] 工具列") <br/>
   **僅顯示標記**的按鈕

   現在 [ **GPU 執行緒**]、[**平行監看式]** 和 [**平行堆疊**] 視窗只會顯示旗標的執行緒。

## <a name="freezing-and-thawing-gpu-threads"></a>凍結和解除凍結 GPU 執行緒

您可以從 [ **GPU 執行緒**] 視窗或 [**平行監看**式] 視窗凍結（暫止）和解除凍結（繼續） gpu 執行緒。 您可以用相同的方式凍結和解凍 CPU 執行緒;如需相關資訊[，請參閱如何：使用 [執行緒]](/visualstudio/debugger/how-to-use-the-threads-window)視窗。

### <a name="to-freeze-and-thaw-gpu-threads"></a>若要凍結和解除凍結 GPU 執行緒

1. 選擇 [**顯示旗標**] 按鈕，以顯示所有的執行緒。

2. 在功能表列上，選擇 [ **Debug**  >  **Continue**]。

3. 開啟現用資料列的快捷方式功能表，然後選擇 [**凍結**]。

   [ **GPU 執行緒**] 視窗的下圖顯示所有四個執行緒都已凍結。

   ![顯示已凍結執行緒的 GPU 執行緒視窗](../../parallel/amp/media/campk.png "顯示已凍結執行緒的 GPU 執行緒視窗") <br/>
   [ **GPU 執行緒**] 視窗中的凍結執行緒

   同樣地，[**平行監看**式] 視窗會顯示所有四個執行緒都已凍結。

4. 在功能表列上，選擇 [ **Debug**  >  **Continue** ]，讓接下來的四個 GPU 執行緒在第22行的屏障之後進行，並到達第30行的中斷點。 [ **GPU 執行緒**] 視窗會顯示先前已凍結的四個執行緒會保持凍結狀態且處於作用中狀態。

5. 在功能表列上，選擇 [ **Debug**]、[ **Continue**]。

6. 在 [**平行監看**式] 視窗中，您也可以解除凍結個別或多個 GPU 執行緒。

### <a name="to-group-gpu-threads"></a>群組 GPU 執行緒

1. 在 [ **GPU 執行緒**] 視窗中的其中一個執行緒的快捷方式功能表上，選擇 [**群組依據**]、[**位址**]。

   [ **GPU 執行緒**] 視窗中的執行緒會依位址分組。 此位址會對應至每個執行緒群組所在的反組解碼指令。 24個執行緒在[tile_barrier：： Wait 方法](reference/tile-barrier-class.md#wait)執行所在的第22行。 12執行緒位於第32行的屏障指示。 其中四個執行緒會加上旗標。 8個執行緒位於第30行的中斷點。 其中四個執行緒已凍結。 下圖顯示 [ **GPU 執行緒**] 視窗中的群組執行緒。

   [ ![GPU 執行緒] 視窗，其中包含依位址分組的執行緒][ (../../parallel/amp/media/campl.png "GPU 執行緒] 視窗，其中包含依位址分組的執行緒") <br/>
   [ **GPU 執行緒**] 視窗中的群組執行緒

2. 您也可以開啟 [**平行監看**式] 視窗中資料格的快捷方式功能表，選擇 [**分組依據**]，然後選擇對應至您要分組執行緒之方式的功能表項目，以執行 [**群組依據**] 作業。

## <a name="running-all-threads-to-a-specific-location-in-code"></a>執行程式碼中的特定位置的所有線程

您可以使用 [**執行目前的磚至游標處**]，在指定的磚中，將所有線程執行到包含游標的那一行。

### <a name="to-run-all-threads-to-the-location-marked-by-the-cursor"></a>若要對資料指標所標記的位置執行所有線程

1. 在凍結執行緒的快捷方式功能表上，選擇 [**解除凍結**]。

2. 在 [程式**代碼編輯器**] 中，將游標放在第30行。

3. 在程式**代碼編輯器**的快捷方式功能表上，選擇 [**執行目前的磚至游標處**]。

   先前在第21行的屏障封鎖的24個執行緒已進入第32行。 這會顯示在 [ **GPU 執行緒**] 視窗中。

## <a name="see-also"></a>另請參閱

[C++ AMP 概觀](../../parallel/amp/cpp-amp-overview.md)<br/>
[偵錯 GPU 程式碼](/visualstudio/debugger/debugging-gpu-code)<br/>
[如何：使用 GPU 執行緒視窗](/visualstudio/debugger/how-to-use-the-gpu-threads-window)<br/>
[如何：使用平行監看式視窗](/visualstudio/debugger/how-to-use-the-parallel-watch-window)<br/>
[使用C++並行視覺化來分析 AMP 程式碼](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/03/09/analyzing-c-amp-code-with-the-concurrency-visualizer/)
