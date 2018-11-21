---
title: 使用磚
ms.date: 11/19/2018
ms.assetid: acb86a86-2b7f-43f1-8fcf-bcc79b21d9a8
ms.openlocfilehash: ede62c80a83b5f5fc1d691bf52dde67140e68246
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176090"
---
# <a name="using-tiles"></a>使用磚

若要最大化您的應用程式加速，您可以使用並排顯示。 並排顯示會將執行緒分成相等的矩形子集或*圖格*。 如果您使用適當的並排顯示大小和並排顯示的演算法，您可以從您的 c + + AMP 程式碼來取得更多的加速效果。 並排顯示的基本元件如下：

- `tile_static` 變數。 並排顯示的主要優點是獲得的效能`tile_static`存取。 中的資料的存取權`tile_static`記憶體可以大幅快於存取全域空間中的資料 (`array`或`array_view`物件)。 執行個體`tile_static`變數是每個 tile 建立，且 tile 中的所有執行緒存取的變數。 在典型的並排顯示演算法中，資料會複製到`tile_static`一次從全域記憶體的記憶體，然後從存取多次`tile_static`記憶體。

- [tile_barrier:: wait 方法](reference/tile-barrier-class.md#wait)。 呼叫`tile_barrier::wait`會暫停執行目前的執行緒，直到所有的同一個 tile 中的執行緒到達呼叫`tile_barrier::wait`。 您不能保證執行緒將執行，只有該 tile 中的任何執行緒會執行過的呼叫順序`tile_barrier::wait`之前的所有執行緒到達呼叫。 這表示，使用`tile_barrier::wait`方法中，您可以執行工作圖格的圖格為基礎，而不是由執行緒為基礎。 典型的 tile 劃分演算法具有程式碼來初始化`tile_static`呼叫後面接著將整個圖格的記憶體`tile_barrer::wait`。 程式碼所示`tile_barrier::wait`包含需要存取所有的計算`tile_static`值。

- 本機和全域編製索引。 您具有存取權的執行緒，相對於整個索引`array_view`或`array`物件和相對於 tile 的索引。 使用本機索引可以讓您的程式碼容易閱讀及偵錯。 一般而言，您可以使用區域索引存取`tile_static`變數和全域索引存取`array`和`array_view`變數。

- [tiled_extent 類別](../../parallel/amp/reference/tiled-extent-class.md)並[tiled_index 類別](../../parallel/amp/reference/tiled-index-class.md)。 您使用`tiled_extent`物件而非`extent`物件中`parallel_for_each`呼叫。 您使用`tiled_index`物件而非`index`物件中`parallel_for_each`呼叫。

若要充分利用的並排顯示，演算法必須將計算網域分割為圖格，然後複製 tile 資料到`tile_static`以利快速存取的變數。

## <a name="example-of-global-tile-and-local-indices"></a>範例中的全域、 並排以及區域索引

下圖顯示資料以 2x3 並排排列的 8x9 的矩陣。

![8&#45;所&#45;9 矩陣分成 2&#45;所&#45;3 的圖格](../../parallel/amp/media/usingtilesmatrix.png "8&#45;的&#45;9 矩陣分成 2&#45;的&#45;3 的圖格")

下列範例會顯示 [全域] 圖格和區域的索引，此並排矩陣。 `array_view`物件使用類型的項目來建立`Description`。 `Description`保存的全域、 並排以及區域索引的矩陣中的項目。 呼叫中的程式碼`parallel_for_each`設定的全域值、 圖格，以及區域索引的每個項目。 輸出會顯示在值`Description`結構。

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
    COORD coord;

    coord.X = width;
    coord.Y = height;
    SetConsoleScreenBufferSize(GetStdHandle(STD_OUTPUT_HANDLE), coord);

    SMALL_RECT* rect = new SMALL_RECT();
    rect->Left = 0;
    rect->Top = 0;
    rect->Right = width;
    rect->Bottom = height;
    SetConsoleWindowInfo(GetStdHandle(STD_OUTPUT_HANDLE), true, rect);
}

// This method creates an 8x9 matrix of Description structures.
// In the call to parallel_for_each, the structure is updated
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

此範例的主要工作是定義中的`array_view`物件和呼叫`parallel_for_each`。

1. 向量`Description`結構會複製到 8x9`array_view`物件。

2. `parallel_for_each`方法呼叫`tiled_extent`為 compute domain 的物件。 `tiled_extent`物件由呼叫`extent::tile()`方法`descriptions`變數。 若要呼叫的型別參數`extent::tile()`， `<2,3>`，指定了建立 2x3 並排。 因此，8x9 矩陣會拼貼成 12 個 tile、 四個資料列和三個資料行。

3. `parallel_for_each`方法透過呼叫`tiled_index<2,3>`物件 (`t_idx`) 做為索引。 索引的類型參數 (`t_idx`) 必須符合 compute domain 的類型參數 (`descriptions.extent.tile< 2, 3>()`)。

4. 每個執行緒執行時，索引`t_idx`傳回執行緒是處於哪一個 tile 的資訊 (`tiled_index::tile`屬性)，以及執行緒於 tile 的位置 (`tiled_index::local`屬性)。

## <a name="tile-synchronizationtilestatic-and-tilebarrierwait"></a>Tile 同步處理，tile_static 和 tile_barrier:: wait

前一個範例說明的磚配置和索引，但不是本身很有幫助。  並排顯示演算法中並不可或缺的圖格，都很實用`tile_static`變數。 因為 tile 中的所有執行緒都有存取權`tile_static`變數，呼叫`tile_barrier::wait`用來同步存取`tile_static`變數。 雖然所有的磚中的執行緒可以存取`tile_static`變數沒有執行緒 tile 中的執行，不保證的順序。 下列範例示範如何使用`tile_static`變數和`tile_barrier::wait`方法來計算每個磚的平均值。 以下是要了解範例的索引鍵：

1. RawData 會儲存在 8x8 矩陣。

2. 並排顯示大小為 2x2。 這會建立 4x4 方格的 tile 和平均值可以儲存在 4 x 4 矩陣，使用`array`物件。 有只在有限的類型，您可以擷取在 AMP 限定函式的參考。 `array`類別是其中一個。

3. 您可以使用定義的矩陣大小和取樣大小`#define`陳述式，因為類型參數，以`array`， `array_view`， `extent`，和`tiled_index`必須是常數值。 您也可以使用`const int static`宣告。 另一個好處，很輕易地變更取樣大小來計算平均超過 4x4 tile。

4. A`tile_static`浮點值 2x2 陣列宣告每個圖格。 雖然宣告位於每個執行緒的程式碼路徑，在矩陣中的每個圖格會建立只有一個陣列。

5. 沒有將值複製到每個圖格中的程式碼行`tile_static`陣列。 對於每個執行緒中，值會複製到陣列之後, 在執行緒上停止執行因為呼叫`tile_barrier::wait`。

6. 當所有的 tile 中執行緒都到達 barrier 後時，就可以計算平均。 每個執行緒執行的程式碼，因為沒有`if`陳述式只計算一個執行緒的平均值。 此平均值會儲存在平均值變數中。 屏障是必要結構控制計算的圖格，就像您可能會使用`for`迴圈。

7. 中的資料`averages`變數，因為它是`array`物件，必須重新複製到主機。 此範例會使用向量轉換運算子。

8. 在完整的範例中，您可以將 SAMPLESIZE 變更為 4，而不需要任何其他變更正確執行的程式碼。

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

它可能會想要建立`tile_static`名為變數`total`且遞增量為該變數的每個執行緒，就像這樣：

```cpp
// Do not do this.
tile_static float total;
total += matrix[t_idx];
t_idx.barrier.wait();

averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE* SAMPLESIZE);
```

此方法的第一個問題在於`tile_static`變數不能有初始設定式。 第二個問題是在指派給是競爭狀況`total`，因為 tile 中執行緒的所有不依特定順序取得變數的存取。 您可以撰寫演算法，只允許一個執行緒存取每個障礙物，總計，如下所示。 不過，此方案不是可延伸的。

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

有兩種類型的記憶體存取必須同步處理，全域記憶體存取和`tile_static`記憶體存取。 A`concurrency::array`物件配置只在全域記憶體。 A`concurrency::array_view`可以參考全域記憶體、`tile_static`記憶體，或兩者，根據其建構方式。  有兩種類型的記憶體必須同步處理：

- 全域記憶體

- `tile_static`

A*記憶體柵欄*可確保存取可供其他執行緒 tile 中執行緒，該記憶體和記憶體存取根據依照程式順序執行。 若要確保這種情況，編譯器和處理器不得重新排列讀取和寫入之間的範圍。 在 c + + AMP 中記憶體柵欄被建立的其中一種方法的呼叫：

- [tile_barrier:: wait 方法](reference/tile-barrier-class.md#wait)： 建立周圍的圍欄的全域和`tile_static`記憶體。

- [tile_barrier:: wait_with_all_memory_fence 方法](reference/tile-barrier-class.md#wait_with_all_memory_fence)： 建立周圍的圍欄的全域和`tile_static`記憶體。

- [tile_barrier:: wait_with_global_memory_fence 方法](reference/tile-barrier-class.md#wait_with_global_memory_fence)： 建立只在全域記憶體周圍的圍欄。

- [tile_barrier:: wait_with_tile_static_memory_fence 方法](reference/tile-barrier-class.md#wait_with_tile_static_memory_fence)： 建立唯一周圍的圍欄`tile_static`記憶體。

呼叫特定範圍，您需要可以改善您的應用程式的效能。 屏障類型會影響如何在編譯器和硬體重新排列陳述式。 例如，如果您使用的全域記憶體圍欄，它適用於全域記憶體存取，因此，編譯器和硬體可能重新排列讀取並寫入`tile_static`圍欄兩側的變數。

在下一個範例中，屏障會同步寫入`tileValues`、`tile_static`變數。 在此範例中，`tile_barrier::wait_with_tile_static_memory_fence`而不是呼叫`tile_barrier::wait`。

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

    // If you remove the if statement, then the calculation executes
    // for every thread in the tile, and makes the same assignment to
    // averages each time.
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

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[tile_static 關鍵字](../../cpp/tile-static-keyword.md)
