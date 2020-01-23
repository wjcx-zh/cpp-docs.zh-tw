---
title: 使用磚
ms.date: 11/19/2018
ms.assetid: acb86a86-2b7f-43f1-8fcf-bcc79b21d9a8
ms.openlocfilehash: 6c935134e033d12fc140c8d377ef59d0b47265fc
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518253"
---
# <a name="using-tiles"></a>使用磚

您可以使用並排來最大化應用程式的加速。 並排顯示會將執行緒分割成相等的矩形子集或*磚*。 如果您使用適當的磚大小和並排顯示演算法，您可以從 AMP 程式C++代碼取得更多的加速。 並排平的基本元件如下：

- `tile_static` 變數。 並排的主要優點是 `tile_static` 存取的效能提升。 存取 `tile_static` 記憶體中的資料，可能會比存取全域空間（`array` 或 `array_view` 物件）中的資料快很多。 系統會為每個磚建立 `tile_static` 變數的實例，而磚中的所有線程都可以存取該變數。 在一般的磚化演算法中，資料會從全域記憶體複製到 `tile_static` 記憶體，然後從 `tile_static` 記憶體中存取多次。

- [tile_barrier：： Wait 方法](reference/tile-barrier-class.md#wait)。 呼叫 `tile_barrier::wait` 會暫停執行目前的執行緒，直到相同磚中的所有線程都到達 `tile_barrier::wait`的呼叫為止。 您無法保證執行緒在中執行的順序，只有磚中的任何執行緒都不會在 `tile_barrier::wait` 的呼叫之後執行，直到所有線程都已達到呼叫為止。 這表示，藉由使用 `tile_barrier::wait` 方法，您可以依磚逐一執行工作，而不是逐執行緒。 一般的並排顯示演算法具有程式碼，可初始化整個磚的 `tile_static` 記憶體，然後再呼叫 `tile_barrer::wait`。 後面的程式碼 `tile_barrier::wait` 包含需要存取所有 `tile_static` 值的計算。

- 本機和全域索引。 您可以存取相對於整個 `array_view` 或 `array` 物件的執行緒索引，以及相對於磚的索引。 使用本機索引可以讓您的程式碼更容易讀取和 debug。 一般而言，您會使用本機索引來存取 `tile_static` 變數，以及用來存取 `array` 和 `array_view` 變數的全域索引。

- [Tiled_extent 類別](../../parallel/amp/reference/tiled-extent-class.md)和[tiled_index 類別](../../parallel/amp/reference/tiled-index-class.md)。 您可以使用 `tiled_extent` 物件，而不是 `parallel_for_each` 呼叫中的 `extent` 物件。 您可以使用 `tiled_index` 物件，而不是 `parallel_for_each` 呼叫中的 `index` 物件。

若要利用並排顯示，您的演算法必須將計算網域分割成磚，然後將磚資料複製到 `tile_static` 變數中，以加快存取的速度。

## <a name="example-of-global-tile-and-local-indices"></a>全域、磚和本機索引的範例

下圖代表在2x3 磚中排列之資料的8x9 矩陣。

![8&#45;x&#45;9 矩陣分為 2&#45;x&#45;3 個磚](../../parallel/amp/media/usingtilesmatrix.png "8&#45;x&#45;9 矩陣分為 2&#45;x&#45;3 個磚")

下列範例會顯示此磚矩陣的全域、磚和本機索引。 `array_view` 物件是使用 `Description`類型的元素所建立。 `Description` 會保存矩陣中元素的全域、磚和本機索引。 呼叫中的程式碼 `parallel_for_each` 會設定每個元素的全域、磚和本機索引的值。 輸出會顯示 `Description` 結構中的值。

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

int main() {
    TilingDescription();
    char wait;
    std::cin >> wait;
}
```

範例的主要工作是在 `array_view` 物件的定義中，以及呼叫 `parallel_for_each`。

1. `Description` 結構的向量會複製到 8x9 `array_view` 物件中。

2. 使用 `tiled_extent` 物件當做計算網域來呼叫 `parallel_for_each` 方法。 `tiled_extent` 物件是藉由呼叫 `descriptions` 變數的 `extent::tile()` 方法來建立。 `extent::tile()`的呼叫型別參數，`<2,3>`指定建立2x3 磚。 因此，8x9 矩陣會分割成12個磚、四個數據列和三個數據行。

3. 使用 `tiled_index<2,3>` 物件（`t_idx`）做為索引來呼叫 `parallel_for_each` 方法。 索引的類型參數（`t_idx`）必須符合計算網域（`descriptions.extent.tile< 2, 3>()`）的類型參數。

4. 當執行每個執行緒時，索引 `t_idx` 會傳回執行緒所在的磚（`tiled_index::tile` 屬性）和磚（`tiled_index::local` 屬性）中線程位置的相關資訊。

## <a name="tile-synchronizationtile_static-and-tile_barrierwait"></a>磚同步處理-tile_static 和 tile_barrier：： wait

上一個範例說明磚配置和索引，但它本身並不太實用。  當磚是演算法的整數，並利用 `tile_static` 變數時，並排顯示會變得很有用。 因為磚中的所有線程都具有 `tile_static` 變數的存取權，所以會使用 `tile_barrier::wait` 的呼叫來同步處理對 `tile_static` 變數的存取。 雖然磚中的所有線程都具有 `tile_static` 變數的存取權，但在磚中不一定要執行執行緒。 下列範例顯示如何使用 `tile_static` 變數和 `tile_barrier::wait` 方法來計算每個磚的平均值。 以下是瞭解範例的關鍵：

1. RawData 會儲存在8x8 矩陣中。

2. 磚大小為2x2。 這會建立磚的4x4 方格，而且平均值可以使用 `array` 物件儲存在4x4 矩陣中。 只有有限數量的類型，您可以在 AMP 限制函式中以傳址方式來捕捉。 `array` 類別是其中一種。

3. 矩陣大小和樣本大小是使用 `#define` 語句來定義，因為 `array`、`array_view`、`extent`和 `tiled_index` 的型別參數必須是常數值。 您也可以使用 `const int static` 宣告。 另一個好處是，變更樣本大小以計算4x4 磚的平均值是很簡單的。

4. 會針對每個磚宣告浮點值的 `tile_static` 2x2 陣列。 雖然宣告是在每個執行緒的程式碼路徑中，但只會針對矩陣中的每個磚建立一個陣列。

5. 有一行程式碼可將每個磚中的值複製到 `tile_static` 陣列。 針對每個執行緒，將值複製到陣列之後，執行緒上的執行會因為呼叫 `tile_barrier::wait`而停止。

6. 當磚中的所有線程都已達到屏障時，就可以計算出平均值。 因為程式碼會針對每個執行緒執行，所以只會有一個 `if` 語句來計算一個執行緒上的平均值。 平均值會儲存在平均值變數中。 屏障基本上是依磚控制計算的結構，就像您使用 `for` 迴圈一樣。

7. `averages` 變數中的資料，因為它是 `array` 物件，所以必須複製回主機。 這個範例會使用向量轉換運算子。

8. 在完整的範例中，您可以將 SAMPLESIZE 變更為4，而程式碼會正確執行，而不需要任何其他變更。

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

建立名為 `total` 的 `tile_static` 變數，並為每個執行緒遞增該變數，可能會很吸引人，如下所示：

```cpp
// Do not do this.
tile_static float total;
total += matrix[t_idx];
t_idx.barrier.wait();

averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE* SAMPLESIZE);
```

這種方法的第一個問題是 `tile_static` 變數不能有初始化運算式。 第二個問題是，`total`指派的競爭條件，因為磚中的所有線程都有權存取變數，而不是特定的順序。 您可以將演算法的程式設計成隻允許一個執行緒存取每個屏障的總計，如下所示。 不過，此解決方案不是可擴充的。

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

## <a name="memory-fences"></a>記憶體時限

有兩種必須同步處理的記憶體存取：全域記憶體存取和 `tile_static` 記憶體存取。 `concurrency::array` 物件只會配置全域記憶體。 `concurrency::array_view` 可以參考全域記憶體、`tile_static` 記憶體或兩者，視其結構而定。  有兩種類型的記憶體必須進行同步處理：

- 全域記憶體

- `tile_static`

*記憶體隔離*可確保執行緒磚中的其他執行緒可以使用記憶體存取，而且會根據程式循序執行記憶體存取。 為了確保這一點，編譯器和處理器不會重新排列整個範圍中的讀取和寫入。 在C++ AMP 中，記憶體隔離是透過呼叫下列其中一個方法來建立：

- [tile_barrier：： Wait 方法](reference/tile-barrier-class.md#wait)：建立全域和 `tile_static` 記憶體周圍的範圍。

- [tile_barrier：： Wait_with_all_memory_fence 方法](reference/tile-barrier-class.md#wait_with_all_memory_fence)：建立全域和 `tile_static` 記憶體周圍的範圍。

- [tile_barrier：： Wait_with_global_memory_fence 方法](reference/tile-barrier-class.md#wait_with_global_memory_fence)：只會在全域記憶體周圍建立一個範圍。

- [tile_barrier：： Wait_with_tile_static_memory_fence 方法](reference/tile-barrier-class.md#wait_with_tile_static_memory_fence)：只會針對 `tile_static` 記憶體建立一個範圍。

呼叫您所需的特定範圍，可以改善應用程式的效能。 屏障類型會影響編譯器和硬體重新排序語句的方式。 例如，如果您使用全域記憶體的範圍，它只會套用到全域記憶體存取，因此編譯器和硬體可能會將讀取和寫入重新排列至範圍兩邊的 `tile_static` 變數。

在下一個範例中，屏障會同步處理寫入至 `tileValues`（`tile_static` 變數）。 在此範例中，會呼叫 `tile_barrier::wait_with_tile_static_memory_fence`，而不是 `tile_barrier::wait`。

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

## <a name="see-also"></a>請參閱

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[tile_static 關鍵字](../../cpp/tile-static-keyword.md)
