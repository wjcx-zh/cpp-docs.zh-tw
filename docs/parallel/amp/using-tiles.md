---
title: 使用磚 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: acb86a86-2b7f-43f1-8fcf-bcc79b21d9a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4e3d1e37562e9e14bbbeda5a01198358b4615d3c
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="using-tiles"></a>使用磚
若要最大化的加速應用程式，您可以使用並排顯示。 並排顯示執行緒分成相等矩形的子集或*磚*。 如果您使用適當的並排顯示大小和並排顯示的演算法，您可以從 c + + AMP 程式碼來取得更多的加速。 並排顯示的基本元件如下：  
  
- `tile_static` 變數。 並排顯示的主要優點是獲得的效能`tile_static`存取。 中的資料存取`tile_static`記憶體可能比在全域空間資料的存取權快很多 (`array`或`array_view`物件)。 執行個體`tile_static`變數會建立每個圖格，並在磚中的所有執行緒都有變數的存取權。 典型的並排顯示演算法在資料複製到`tile_static`一次從全域記憶體的記憶體，然後從存取多次`tile_static`記憶體。  
  
- [tile_barrier:: wait 方法](reference/tile-barrier-class.md#wait)。 呼叫`tile_barrier::wait`暫停執行目前執行緒，直到所有相同的磚中的執行緒到達的呼叫`tile_barrier::wait`。 您無法保證在中執行的執行緒，只有該磚中的沒有任何執行緒會執行過的呼叫順序`tile_barrier::wait`之前的所有執行緒已達到呼叫。 這表示，使用`tile_barrier::wait`方法，您可以並排顯示的圖格為基礎而非執行緒的執行緒上執行工作。 典型的並排顯示演算法具有程式碼以初始化`tile_static`整個磚記憶體後面呼叫`tile_barrer::wait`。 下列程式碼`tile_barrier::wait`包含需要存取所有的計算`tile_static`值。  

  
-   本機和全域編製索引。 您可以存取的執行緒，相對於整個索引`array_view`或`array`物件和相對於磚索引。 使用本機的索引，可讓您的程式碼容易閱讀及偵錯。 一般而言，您可以使用本機的索引，以存取`tile_static`變數和全域索引來存取`array`和`array_view`變數。  
  
- [tiled_extent 類別](../../parallel/amp/reference/tiled-extent-class.md)和[tiled_index 類別](../../parallel/amp/reference/tiled-index-class.md)。 您使用`tiled_extent`物件而非`extent`物件存放至`parallel_for_each`呼叫。 您使用`tiled_index`物件而非`index`物件存放至`parallel_for_each`呼叫。  
  
 若要善用並排顯示，您的演算法必須分割成磚的 計算網域，然後磚將資料複製到`tile_static`更快速存取的變數。  
  
## <a name="example-of-global-tile-and-local-indices"></a>範例中的全域、 磚和本機索引  
 下圖表示 8 x 9 矩陣的排列 2 x 3 磚中的資料。  
  
 ![8&#45;由&#45;9 矩陣分成 2&#45;由&#45;3 磚](../../parallel/amp/media/usingtilesmatrix.png "usingtilesmatrix")  
  
 下列範例會顯示 [全域] 磚，並本機索引這個並排矩陣。 `array_view`物件由使用類型的項目建立`Description`。 `Description`保存全域磚，並在矩陣中項目的本機索引。 呼叫中的程式碼`parallel_for_each`設定的全域值、 圖格及本機索引的每個項目。 輸出會顯示在值`Description`結構。  
  
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
    int colorValue = (color == 0)  4 : 2;  
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
  
 此範例的主要工作是定義中的`array_view`物件並呼叫`parallel_for_each`。  
  
1.  向量的`Description`結構會複製到 8 x 9`array_view`物件。  
  
2.  `parallel_for_each`方法呼叫`tiled_extent`物件做為計算網域。 `tiled_extent`物件由呼叫`extent::tile()`方法`descriptions`變數。 若要呼叫的型別參數`extent::tile()`， `<2,3>`，指定建立的磚 2 x 3。 因此，8 x 9 矩陣會並排顯示，到 12 的圖格、 四個資料列和三個資料行。  
  
3.  `parallel_for_each`方法會呼叫使用`tiled_index<2,3>`物件 (`t_idx`) 做為索引。 索引的型別參數 (`t_idx`) 必須符合此計算網域中的型別參數 (`descriptions.extent.tile< 2, 3>()`)。  
  
4.  每個執行緒執行時，索引`t_idx`傳回資訊，關於哪個方塊執行緒中 (`tiled_index::tile`屬性) 和執行緒的區塊中的位置 (`tiled_index::local`屬性)。  
  
## <a name="tile-synchronizationtilestatic-and-tilebarrierwait"></a>並排顯示同步處理，tile_static 和 tile_barrier:: wait  
 前一個範例說明的磚配置和索引，但不是本身非常有用。  並排顯示的圖格都不可或缺的演算法和攻擊會很有用`tile_static`變數。 因為在磚中的所有執行緒存取`tile_static`變數，呼叫`tile_barrier::wait`可用以同步存取`tile_static`變數。 雖然所有磚中的執行緒可以存取`tile_static`變數，沒有任何保證的順序的磚中的執行緒執行。 下列範例示範如何使用`tile_static`變數和`tile_barrier::wait`方法來計算每個圖格的平均值。 以下是要了解範例的索引鍵：  
  
1.  RawData 會儲存在 8 x 8 矩陣。  
  
2.  並排顯示大小為 2 x 2。 這會建立 4 x 4 方格的磚，而平均可以透過使用儲存在一個 4x4 矩陣`array`物件。 有有限的數目的型別，您可以擷取在 AMP 限制函式的參考。 `array`類別是其中一個。  
  
3.  此矩陣的大小和取樣大小定義使用`#define`陳述式，因為類型參數，以`array`， `array_view`， `extent`，和`tiled_index`必須是常數值。 您也可以使用`const int static`宣告。 另一個好處是，它只是一般變更範例大小來計算平均超過 4 x 4 磚。  
  
4.  A`tile_static`浮點值 2 x 2 陣列宣告每個圖格。 雖然宣告是在每個執行緒的程式碼路徑中，只有一個陣列建立每個圖格矩陣中。  
  
5.  沒有將值複製到每個磚中的程式碼行`tile_static`陣列。 每個執行緒，值會複製到陣列之後, 在執行緒上的執行會停止由於呼叫`tile_barrier::wait`。  
  
6.  當所有磚中的執行緒已經到達屏障時，就可以計算平均值。 因為每個執行緒中執行的程式碼，所以`if`只計算平均在一個執行緒上的陳述式。 平均值會儲存在平均值變數。 屏障是本質上的磚，來控制計算的建構，就像您可能會使用`for`迴圈。  
  
7.  中的資料`averages`變數，因為它是`array`物件，必須重新複製到主機。 這個範例會使用向量轉換運算子。  
  
8.  在完整的範例中，您可以變更 SAMPLESIZE 4 而且不進行任何其他變更正確執行的程式碼。  
  
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
  
## <a name="race-conditions"></a>追蹤條件  
 它可能會想要建立`tile_static`名為變數`total`且遞增量為該變數的每個執行緒，像這樣：  
  
```cpp  
// Do not do this.  
tile_static float total;  
total += matrix[t_idx];  
t_idx.barrier.wait();

averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE* SAMPLESIZE);

 
```  
  
 這個方法的第一個問題在於`tile_static`變數不能有初始設定式。 第二個問題的原因是競爭條件上指派給`total`，原因是所有的磚中的執行緒不依特定順序將變數的存取權。 您可以程式設計的演算法，只允許一個執行緒存取的總計，在每個障礙，如下所示。 不過，此方案不是可延伸。  
  
```cpp  
// Do not do this.  
tile_static float total;  
if (t_idx.local[0] == 0&& t_idx.local[1] == 0) {  
    total = matrix[t_idx];  
}  
t_idx.barrier.wait();

 
if (t_idx.local[0] == 0&& t_idx.local[1] == 1) {  
    total += matrix[t_idx];  
}  
t_idx.barrier.wait();

 
// etc.  
 
```  
  
## <a name="memory-fences"></a>記憶體柵欄  
 有兩種類型的記憶體存取必須同步處理-全域記憶體存取和`tile_static`記憶體存取。 A`concurrency::array`物件配置全域記憶體。 A`concurrency::array_view`可以參考全域記憶體，`tile_static`記憶體，或兩者，根據建構方式。  有兩種類型的必須同步處理的記憶體：  
  
-   全域記憶體  
  
- `tile_static`  
  
 A*記憶體圍欄*可確保存取可供執行緒磚中的其他執行緒的記憶體和記憶體存取會根據程式的順序執行。 若要確保這種情況，編譯器和處理器並不重新排序讀取和寫入跨範圍。 在 c + + AMP 記憶體範圍的建立方式的其中一種方法的呼叫：  
  

- [tile_barrier:: wait 方法](reference/tile-barrier-class.md#wait)： 建立全域兩者周圍的範圍和`tile_static`記憶體。  
  
- [tile_barrier:: wait_with_all_memory_fence 方法](reference/tile-barrier-class.md#wait_with_all_memory_fence)： 建立全域兩者周圍的範圍和`tile_static`記憶體。  
  
- [tile_barrier:: wait_with_global_memory_fence 方法](reference/tile-barrier-class.md#wait_with_global_memory_fence)： 建立全域記憶體周圍的範圍。  
  
- [tile_barrier:: wait_with_tile_static_memory_fence 方法](reference/tile-barrier-class.md#wait_with_tile_static_memory_fence)： 建立唯一周圍範圍`tile_static`記憶體。  

  
 呼叫特定範圍，您需要可以改善您的應用程式的效能。 屏障類型會影響如何在編譯器和硬體重新排列陳述式。 例如，如果您使用全域記憶體範圍，它會套用為全域記憶體存取，因此，編譯器和硬體可能會重新排列讀取並寫入`tile_static`兩側的範圍變數。  
  
 在下一個範例中，屏障同步處理寫入`tileValues`、`tile_static`變數。 在此範例中，`tile_barrier::wait_with_tile_static_memory_fence`呼叫而不是`tile_barrier::wait`。  
  
```cpp  
// Using a tile_static memory fence.  
parallel_for_each(matrix.extent.tile<SAMPLESIZE, SAMPLESIZE>(),  
 [=, &averages] (tiled_index<SAMPLESIZE, SAMPLESIZE> t_idx) restrict(amp)   
{ *// Copy the values of the tile into a tile-sized array.  
    tile_static float tileValues[SAMPLESIZE][SAMPLESIZE];  
    tileValues[t_idx.local[0]][t_idx.local[1]] = matrix[t_idx];  
 *// Wait for the tile-sized array to load before calculating the average.  
    t_idx.barrier.wait_with_tile_static_memory_fence();

 *// If you remove the if statement, then the calculation executes for every *// thread in the tile, and makes the same assignment to averages each time.  
    if (t_idx.local[0] == 0&& t_idx.local[1] == 0) {  
    for (int trow = 0; trow <SAMPLESIZE; trow++) {  
    for (int tcol = 0; tcol <SAMPLESIZE; tcol++) {  
    averages(t_idx.tile[0],t_idx.tile[1]) += tileValues[trow][tcol];  
 }  
 }  
    averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE* SAMPLESIZE);

 }  
});

 
```  
  
## <a name="see-also"></a>另請參閱  
 [C + + AMP (c + + Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [tile_static 關鍵字](../../cpp/tile-static-keyword.md)

