---
title: "使用磚 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: acb86a86-2b7f-43f1-8fcf-bcc79b21d9a8
caps.latest.revision: 18
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用磚
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可以使用 tile 最大化應用程式的加速效果。  使用 tile 可將執行緒分成由相同矩形構成的子集或多個*tile*。  如果您使用適當的磚大小和並排顯示演算法，就可以從 C\+\+ AMP 程式碼得到更多的加速效果。  磚的基本元件如下：  
  
-   `tile_static` 變數。  tile 的主要優點是從 `tile_static` 存取權限獲得效能。  在 `tile_static` 記憶體中存取資料顯然會比在全域空間 \(`array` 或 `array_view` 物件\) 中存取還要快速。  `tile_static` 變數的執行個體會為每個 Tile 建立，而且 Tile 中的所有執行緒都可以存取該變數。  在典型的並排顯示演算法中，資料從全域記憶體複製到 `tile_static` 記憶體一次，然後再從 `tile_static` 記憶體存取數次。  
  
-   [tile\_barrier::wait 方法](../Topic/tile_barrier::wait%20Method.md).  對 `tile_barrier::wait` 的呼叫會暫止目前執行緒的執行，直到同一個 Tile 中的所有執行緒都到達對 `tile_barrier::wait` 的呼叫為止。  除了一個執行緒在呼叫 `tile_barrier::wait` 後，同一 tile 中的所有執行緒也呼叫它以前，該執行緒不會執行以外，您無法保證各執行緒的執行順序。  這意味您可以透過使用 `tile_barrier::wait` 方法，按 tile 逐個執行工作 \(而非以逐條執行緒為基礎執行工作\)。  典型的 Tile 劃分演算法具有在呼叫 `tile_barrer::wait` 後初始化整個 Tile 的 `tile_static` 記憶體的程式碼。  `tile_barrier::wait` 隨後的程式碼包含需要存取所有 `tile_static` 值的計算。  
  
-   區域與全域索引。  您可以存取相對於整個 `array_view` 或 `array` 物件的執行緒索引值和相對於 tile 的索引值。  使用本機索引可以讓您的程式碼易於閱讀及偵錯。  通常，您會使用區域索引存取 `tile_static` 變數，全域索引存取 `array` 和 `array_view` 變數。  
  
-   [tiled\_extent 類別](../../parallel/amp/reference/tiled-extent-class.md) 和 [tiled\_index 類別](../../parallel/amp/reference/tiled-index-class.md)。  在呼叫 `parallel_for_each` 時，您應使用 `tiled_extent` 物件，而非 `extent` 物件。  在呼叫 `parallel_for_each` 時，您應使用 `tiled_index` 物件，而非 `index` 物件。  
  
 若要使用 tile 劃分，演算法必須將計算網域分割成數個 tile ，然後複製 tile 資料到 `tile_static` 變數以獲得較快的存取速度。  
  
## 全域、Tile 和區域索引範例  
 下圖表示以 2x3 並排排列的 8x9 資料矩陣。  
  
 ![分成 2x3 並排矩陣的 8x9 矩陣](../../parallel/amp/media/usingtilesmatrix.png "UsingTilesMatrix")  
  
 下列範例會顯示此並排矩陣的全域、並排以及區域索引。  `array_view` 物件是使用屬於類型 `Description` 的項目建立的。  `Description` 保留此矩陣中元素的全域、並排以及區域索引。  呼叫 `parallel_for_each` 中的程式碼會設定每個項目的全域、並排以及區域索引的值。  輸出會顯示在 `Description` 結構中的值。  
  
```cpp  
  
#include <iostream>  
#include <iomanip>  
#include <Windows.h>  
#include <amp.h>  
using namespace concurrency;  
  
const int ROWS = 8;  
const int COLS = 9;  
  
// tileRow and tileColumn specify the tile that each thread is in.  
// globalRow and globalColumn specify the location of the thread in the array_view.  
// localRow and localColumn specify the location of the thread relative to the tile.  
struct Description {  
    int value;  
    int tileRow;  
    int tileColumn;  
    int globalRow;  
    int globalColumn;  
    int localRow;  
    int localColumn;  
};  
  
// A helper function for formatting the output.  
void SetConsoleColor(int color) {  
    int colorValue = (color == 0) ? 4 : 2;  
    SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), colorValue);  
}  
  
// A helper function for formatting the output.  
void SetConsoleSize(int height, int width) {  
    COORD coord; coord.X = width; coord.Y = height;  
    SetConsoleScreenBufferSize(GetStdHandle(STD_OUTPUT_HANDLE), coord);  
    SMALL_RECT* rect = new SMALL_RECT();  
    rect->Left = 0; rect->Top = 0; rect->Right = width; rect->Bottom = height;  
    SetConsoleWindowInfo(GetStdHandle(STD_OUTPUT_HANDLE), true, rect);  
}  
  
// This method creates an 8x9 matrix of Description structures. In the call to parallel_for_each, the structure is updated   
// with tile, global, and local indices.  
void TilingDescription() {  
    // Create 72 (8x9) Description structures.  
    std::vector<Description> descs;  
    for (int i = 0; i < ROWS * COLS; i++) {  
        Description d = {i, 0, 0, 0, 0, 0, 0};  
        descs.push_back(d);  
    }  
  
    // Create an array_view from the Description structures.  
    extent<2> matrix(ROWS, COLS);  
    array_view<Description, 2> descriptions(matrix, descs);  
  
    // Update each Description with the tile, global, and local indices.  
    parallel_for_each(descriptions.extent.tile< 2, 3>(),  
         [=] (tiled_index< 2, 3> t_idx) restrict(amp)   
    {  
        descriptions[t_idx].globalRow = t_idx.global[0];  
        descriptions[t_idx].globalColumn = t_idx.global[1];  
        descriptions[t_idx].tileRow = t_idx.tile[0];  
        descriptions[t_idx].tileColumn = t_idx.tile[1];  
        descriptions[t_idx].localRow = t_idx.local[0];  
        descriptions[t_idx].localColumn= t_idx.local[1];  
    });  
  
    // Print out the Description structure for each element in the matrix.  
    // Tiles are displayed in red and green to distinguish them from each other.  
    SetConsoleSize(100, 150);  
    for (int row = 0; row < ROWS; row++) {  
        for (int column = 0; column < COLS; column++) {  
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);  
            std::cout << "Value: " << std::setw(2) << descriptions(row, column).value << "      ";  
        }  
        std::cout << "\n";  
  
        for (int column = 0; column < COLS; column++) {  
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);  
            std::cout << "Tile:   " << "(" << descriptions(row, column).tileRow << "," << descriptions(row, column).tileColumn << ")  ";  
        }  
        std::cout << "\n";  
  
        for (int column = 0; column < COLS; column++) {  
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);  
            std::cout << "Global: " << "(" << descriptions(row, column).globalRow << "," << descriptions(row, column).globalColumn << ")  ";  
        }  
        std::cout << "\n";  
  
        for (int column = 0; column < COLS; column++) {  
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);  
            std::cout << "Local:  " << "(" << descriptions(row, column).localRow << "," << descriptions(row, column).localColumn << ")  ";  
        }  
        std::cout << "\n";  
        std::cout << "\n";  
    }  
}  
  
void main() {  
    TilingDescription();  
    char wait;  
    std::cin >> wait;  
}  
  
```  
  
 此範例的主要目的是定義 `array_view` 物件和`parallel_for_each` 的呼叫。  
  
1.  會將`Description` 結構向量複製到 8x9 的 `array_view` 物件。  
  
2.  以 `tiled_extent` 做為 compute domain 呼叫 `parallel_for_each` 方法。  透過呼叫 `descriptions` 變數的 `extent::tile()` 方法建立 `tiled_extent` 物件。  `extent::tile()` 呼叫的類型參數 `<2,3>`，表示建立 2x3 的 tile。  因此，8x9 矩陣會拼貼成 12 個 tile、四個資料列和三個資料行。  
  
3.  使用 `tiled_index<2,3>` 物件 \(`t_idx`\) 做為索引呼叫 `parallel_for_each` 方法。  索引的類型參數 \(`t_idx`\) 必須符合 compute domain 的類型參數 \(`descriptions.extent.tile< 2, 3>()`\)。  
  
4.  執行每個執行緒執行時，索引 `t_idx` 會傳回執行緒是處於哪一個 tile 的資訊 \(`tiled_index::tile`屬性\)，以及執行緒於 tile 中的位置 \(`tiled_index::local` 屬性\)。  
  
## tile 同步處理 – tile\_static 和 tile\_barrier::wait  
 前一個範例說明 tile 的版面配置和索引，但本身並不是很實用。當 tile 劃分整合至演算法中並使用 `tile_static` 變數時才會變得實用。  因為 Tile 中的所有執行緒都可以存取 `tile_static` 變數，所以 `tile_barrier::wait` 的呼叫是用來同步處理對 `tile_static` 變數的存取。  雖然 Tile 中的所有執行緒都可以存取 `tile_static` 變數，但是不保證執行緒在 Tile 中的執行順序。  下列範例示範如何使用 `tile_static` 變數和 `tile_barrier::wait` 方法來計算每個磚的平均值。  以下是了解範例的重點：  
  
1.  rawData 會儲存在 8x8 矩陣裡。  
  
2.  tile 大小為 2x2。  這會使用 `array` 物件建立 4x4 方格的 tile ，且平均值可以儲存於 4x4 的矩陣中。  您只能在 AMP 限制的函式中擷取有限的類型。  `array` 類別是其中一個。  
  
3.  因為 `array`、 `array_view`、 `extent`和 `tiled_index` 的類型參數必須是常數值，所以矩陣大小和取樣大小是由 `#define` 陳述式定義。  您也可以使用 `const int static` 宣告。  還有一個好處就是，您可以輕易地變更取樣大小來計算 4x4 Tile 的平均值。  
  
4.  每個 Tile 都會宣告浮點值的 `tile_static` 2x2 陣列。  雖然宣告位於每個執行緒的程式碼執行路徑上，仍然只會為矩陣中的每個 Tile 建立一個陣列。  
  
5.  有一個程式行可將每個 tile 中的值複製到 `tile_static` 陣列。  對於每個執行緒，當值複製到陣列之後，執行緒會因呼叫 `tile_barrier::wait` 而停止執行。  
  
6.  tile 中所有的執行緒都到達 barrier 後，可以計算平均。  因為程式碼會針對每個執行緒執行，所以會有 `if` 陳述式只計算一個執行緒的平均值。  此平均值會儲存在平均值變數中。  屏障是磚控制計算的必要結構，就像您可能會使用 `for` 迴圈。  
  
7.  因為 `averages` 中的資料是 `array` 物件，所以複製回主機。  本範例會使用向量轉換運算子。  
  
8.  在完成的範例中，您可以將 SAMPLESIZE 變更為 4，程式碼將可正確執行，而不需進行任何其他變更。  
  
```cpp  
  
#include <iostream>  
#include <amp.h>  
using namespace concurrency;  
  
#define SAMPLESIZE 2  
#define MATRIXSIZE 8  
void SamplingExample() {  
  
    // Create data and array_view for the matrix.  
    std::vector<float> rawData;  
    for (int i = 0; i < MATRIXSIZE * MATRIXSIZE; i++) {  
        rawData.push_back((float)i);  
    }  
    extent<2> dataExtent(MATRIXSIZE, MATRIXSIZE);  
    array_view<float, 2> matrix(dataExtent, rawData);  
  
    // Create the array for the averages.  
    // There is one element in the output for each tile in the data.  
    std::vector<float> outputData;  
    int outputSize = MATRIXSIZE / SAMPLESIZE;  
    for (int j = 0; j < outputSize * outputSize; j++) {  
        outputData.push_back((float)0);  
    }  
    extent<2> outputExtent(MATRIXSIZE / SAMPLESIZE, MATRIXSIZE / SAMPLESIZE);  
    array<float, 2> averages(outputExtent, outputData.begin(), outputData.end());  
  
    // Use tiles that are SAMPLESIZE x SAMPLESIZE.  
    // Find the average of the values in each tile.  
    // The only reference-type variable you can pass into the parallel_for_each call  
    // is a concurrency::array.  
    parallel_for_each(matrix.extent.tile<SAMPLESIZE, SAMPLESIZE>(),  
         [=, &averages] (tiled_index<SAMPLESIZE, SAMPLESIZE> t_idx) restrict(amp)   
    {  
        // Copy the values of the tile into a tile-sized array.  
        tile_static float tileValues[SAMPLESIZE][SAMPLESIZE];  
        tileValues[t_idx.local[0]][t_idx.local[1]] = matrix[t_idx];  
  
        // Wait for the tile-sized array to load before you calculate the average.  
        t_idx.barrier.wait();  
  
        // If you remove the if statement, then the calculation executes for every  
        // thread in the tile, and makes the same assignment to averages each time.  
        if (t_idx.local[0] == 0 && t_idx.local[1] == 0) {  
            for (int trow = 0; trow < SAMPLESIZE; trow++) {  
                for (int tcol = 0; tcol < SAMPLESIZE; tcol++) {  
                    averages(t_idx.tile[0],t_idx.tile[1]) += tileValues[trow][tcol];  
                }  
            }  
            averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE * SAMPLESIZE);  
        }  
    });  
  
    // Print out the results.  
    // You cannot access the values in averages directly. You must copy them  
    // back to a CPU variable.  
    outputData = averages;  
    for (int row = 0; row < outputSize; row++) {  
        for (int col = 0; col < outputSize; col++) {  
            std::cout << outputData[row*outputSize + col] << " ";  
        }  
        std::cout << "\n";  
    }  
    // Output for SAMPLESSIZE = 2 is:  
    //  4.5  6.5  8.5 10.5  
    // 20.5 22.5 24.5 26.5  
    // 36.5 38.5 40.5 42.5  
    // 52.5 54.5 56.5 58.5  
  
    // Output for SAMPLESIZE = 4 is:  
    // 13.5 17.5  
    // 45.5 49.5  
}  
  
int main() {  
    SamplingExample();  
}  
  
```  
  
## 競爭情形  
 您可能會想要建立一個名為的 `total` 的變數 `tile_static`，並針對每個執行緒遞增該變數，如下所示：  
  
```cpp  
  
// Do not do this.  
tile_static float total;  
total += matrix[t_idx];  
t_idx.barrier.wait();  
averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE * SAMPLESIZE);  
  
```  
  
 這個方法的第一個問題是，`tile_static` 變數不能有初始設定式。  第二個問題是，因為 tile 中的所有執行緒都有`total`變數的存取權限，且它們沒有特定的順序，所以對於該變數的指定構成了競爭條件。  您可以撰寫演算法，只允許一個執行緒存取每個障礙物的總和，如下列範例所示。  儘管如此，本解決方案不具有延伸性。  
  
```cpp  
  
// Do not do this.  
tile_static float total;  
if (t_idx.local[0] == 0 && t_idx.local[1] == 0) {  
    total = matrix[t_idx];  
}  
t_idx.barrier.wait();  
  
if (t_idx.local[0] == 0 && t_idx.local[1] == 1) {  
    total += matrix[t_idx];  
}  
t_idx.barrier.wait();  
  
// etc.  
  
```  
  
## 記憶體柵欄  
 有兩種記憶體存取方式，全域記憶體存取和 `tile_static` 記憶體存取，必須同步處理。  `concurrency::array` 物件只會配置全域記憶體。  `concurrency::array_view` 可以參考全域記憶體、`tile_static` 記憶體或兩者都參考，視其建構方式而定。記憶體有兩種，必須同步處理:  
  
-   全域記憶體  
  
-   `tile_static`  
  
 「*記憶體圍欄*」\(Memory Fence\) 會確保執行緒 Tile 中的其他執行緒也可以存取記憶體，並根據程式的順序執行記憶體存取。  若要確保這一點，編譯器和處理器不得重新排列圍欄間的讀寫順序。  在 C\+\+ AMP 中，記憶體柵欄是藉由呼叫下列其中一個方法建立：  
  
-   [tile\_barrier::wait 方法](../Topic/tile_barrier::wait%20Method.md): 建立在全域以及 `tile_static` 記憶體周圍的圍欄。  
  
-   [tile\_barrier::wait\_with\_all\_memory\_fence 方法](../Topic/tile_barrier::wait_with_all_memory_fence%20Method.md): 建立在全域以及 `tile_static` 記憶體周圍的圍欄。  
  
-   [tile\_barrier::wait\_with\_global\_memory\_fence 方法](../Topic/tile_barrier::wait_with_global_memory_fence%20Method.md): 建立只在全域記憶體周圍的圍欄。  
  
-   [tile\_barrier::wait\_with\_tile\_static\_memory\_fence 方法](../Topic/tile_barrier::wait_with_tile_static_memory_fence%20Method.md): 建立只在 `tile_static` 記憶體周圍的圍欄。  
  
 呼叫您所需要的特定圍欄可以改善應用程式的效能。  屏障類型會影響編譯器和硬體如何重新排列陳述式。  例如，如果您使用全域記憶體圍欄，因其僅適用於全域記憶體存取，所以編譯器和硬體可能重新排列在圍欄兩側的 `tile_static` 變數的讀寫順序。  
  
 在下一個範例中，屏障會同步將 `tile_static` 變數寫入至 `tileValues` 的作業。  在此範例中，將改為呼叫 `tile_barrier::wait_with_tile_static_memory_fence`，而不會呼叫 `tile_barrier::wait`。  
  
```cpp  
  
// Using a tile_static memory fence.  
parallel_for_each(matrix.extent.tile<SAMPLESIZE, SAMPLESIZE>(),  
     [=, &averages] (tiled_index<SAMPLESIZE, SAMPLESIZE> t_idx) restrict(amp)   
{  
    // Copy the values of the tile into a tile-sized array.  
    tile_static float tileValues[SAMPLESIZE][SAMPLESIZE];  
    tileValues[t_idx.local[0]][t_idx.local[1]] = matrix[t_idx];  
  
    // Wait for the tile-sized array to load before calculating the average.  
    t_idx.barrier.wait_with_tile_static_memory_fence();  
  
    // If you remove the if statement, then the calculation executes for every  
    // thread in the tile, and makes the same assignment to averages each time.  
    if (t_idx.local[0] == 0 && t_idx.local[1] == 0) {  
        for (int trow = 0; trow < SAMPLESIZE; trow++) {  
            for (int tcol = 0; tcol < SAMPLESIZE; tcol++) {  
                averages(t_idx.tile[0],t_idx.tile[1]) += tileValues[trow][tcol];  
            }  
        }  
        averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE * SAMPLESIZE);  
    }  
});  
  
```  
  
## 請參閱  
 [C\+\+ AMP \(C\+\+ Accelerated Massive Parallelism\)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [tile\_static 關鍵字](../../cpp/tile-static-keyword.md)