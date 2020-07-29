---
title: 使用磚
ms.date: 11/19/2018
ms.assetid: acb86a86-2b7f-43f1-8fcf-bcc79b21d9a8
ms.openlocfilehash: edef9154b0c4da6f53c8ac40ee84e55e9b38a9b7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228462"
---
# <a name="using-tiles"></a>使用磚

您可以使用並排來最大化應用程式的加速。 並排顯示會將執行緒分割成相等的矩形子集或*磚*。 如果您使用適當的磚大小和並排顯示演算法，您可以從 C++ AMP 程式碼取得更多加速。 並排平的基本元件如下：

- `tile_static`變數. 並排的主要優點是存取的效能提升 `tile_static` 。 存取記憶體中的資料可能 `tile_static` 會比存取全域空間（ `array` 或物件）中的資料快得多 `array_view` 。 `tile_static`系統會為每個磚建立變數的實例，而磚中的所有線程都可以存取該變數。 在一般的並排顯示演算法中，資料會 `tile_static` 從全域記憶體複製到記憶體一次，然後從記憶體中存取許多次 `tile_static` 。

- [tile_barrier：： Wait 方法](reference/tile-barrier-class.md#wait)。 呼叫會 `tile_barrier::wait` 暫停執行目前的執行緒，直到相同磚中的所有線程都到達對的呼叫為止 `tile_barrier::wait` 。 您無法保證執行緒執行的順序，只有在 `tile_barrier::wait` 所有線程都已到達呼叫之前，磚中的任何執行緒都不會在呼叫之後執行。 這表示，藉由使用 `tile_barrier::wait` 方法，您可以依磚逐一執行工作，而不是逐執行緒。 一般的並排顯示演算法具有程式碼，可初始化 `tile_static` 整個磚的記憶體，然後再呼叫 `tile_barrier::wait` 。 後面的程式碼 `tile_barrier::wait` 包含需要存取所有值的計算 `tile_static` 。

- 本機和全域索引。 您可以存取相對於整個或物件的執行緒索引 `array_view` `array` ，以及相對於磚的索引。 使用本機索引可以讓您的程式碼更容易讀取和 debug。 一般而言，您會使用本機索引來存取 `tile_static` 變數，並使用全域索引來存取 `array` 和 `array_view` 變數。

- [Tiled_extent 類別](../../parallel/amp/reference/tiled-extent-class.md)和[tiled_index 類別](../../parallel/amp/reference/tiled-index-class.md)。 您在 `tiled_extent` 呼叫中使用物件，而不是 `extent` 物件 `parallel_for_each` 。 您在 `tiled_index` 呼叫中使用物件，而不是 `index` 物件 `parallel_for_each` 。

若要利用並排顯示，您的演算法必須將計算網域分割成磚，然後將磚資料複製到變數中， `tile_static` 以加快存取的速度。

## <a name="example-of-global-tile-and-local-indices"></a>全域、磚和本機索引的範例

下圖代表在2x3 磚中排列之資料的8x9 矩陣。

![&#45;9 矩陣的 8&#45;依&#45;3 個磚分成2個&#45;](../../parallel/amp/media/usingtilesmatrix.png "&#45;9 矩陣的 8&#45;依&#45;3 個磚分成2個&#45;")

下列範例會顯示此磚矩陣的全域、磚和本機索引。 `array_view`物件是使用類型的元素所建立 `Description` 。 會 `Description` 保存矩陣中元素的全域、磚和本機索引。 呼叫中的程式碼，可 `parallel_for_each` 設定每個專案的全域、磚和本機索引的值。 輸出會顯示結構中的值 `Description` 。

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

此範例的主要工作是在物件的定義中 `array_view` ，以及對的呼叫 `parallel_for_each` 。

1. 結構的向量 `Description` 會複製到8x9 物件中 `array_view` 。

2. `parallel_for_each`使用 `tiled_extent` 物件當做計算網域來呼叫方法。 `tiled_extent`物件的建立方式是呼叫 `extent::tile()` 變數的方法 `descriptions` 。 呼叫的型別參數 `extent::tile()` ， `<2,3>` 會指定要建立2x3 磚。 因此，8x9 矩陣會分割成12個磚、四個數據列和三個數據行。

3. `parallel_for_each`使用 `tiled_index<2,3>` 物件（ `t_idx` ）做為索引來呼叫方法。 索引的類型參數（ `t_idx` ）必須符合計算網域的類型參數（ `descriptions.extent.tile< 2, 3>()` ）。

4. 當執行每個執行緒時，索引會傳回 `t_idx` 執行緒所在的磚（ `tiled_index::tile` 屬性）和磚（屬性）內之執行緒位置的相關資訊 `tiled_index::local` 。

## <a name="tile-synchronizationtile_static-and-tile_barrierwait"></a>磚同步處理-tile_static 和 tile_barrier：： wait

上一個範例說明磚配置和索引，但它本身並不太實用。  磚在演算法和惡意探索變數的整數時，會變得很有用 `tile_static` 。 因為磚中的所有線程都有變數的存取權 `tile_static` ，所以 `tile_barrier::wait` 會使用的呼叫來同步處理對變數的存取 `tile_static` 。 雖然磚中的所有線程都具有變數的存取權 `tile_static` ，但在磚中不一定要執行執行緒。 下列範例顯示如何使用 `tile_static` 變數和 `tile_barrier::wait` 方法來計算每個磚的平均值。 以下是瞭解範例的關鍵：

1. RawData 會儲存在8x8 矩陣中。

2. 磚大小為2x2。 這會建立磚的4x4 方格，而且平均值可以使用物件儲存在4x4 矩陣中 `array` 。 只有有限數量的類型，您可以在 AMP 限制函式中以傳址方式來捕捉。 `array`類別是其中一個。

3. 矩陣大小和樣本大小是使用語句來定義 `#define` ，因為 `array` 、、和的型別 `array_view` 參數 `extent` `tiled_index` 必須是常數值。 您也可以使用宣告 `const int static` 。 另一個好處是，變更樣本大小以計算4x4 磚的平均值是很簡單的。

4. `tile_static`會針對每個磚宣告 float 值的2x2 陣列。 雖然宣告是在每個執行緒的程式碼路徑中，但只會針對矩陣中的每個磚建立一個陣列。

5. 有一行程式碼可將每個磚中的值複製到 `tile_static` 陣列。 針對每個執行緒，將值複製到陣列之後，執行緒上的執行會因為呼叫而停止 `tile_barrier::wait` 。

6. 當磚中的所有線程都已達到屏障時，就可以計算出平均值。 因為程式碼會針對每個執行緒執行，所以 `if` 只會有一個語句來計算一個執行緒上的平均值。 平均值會儲存在平均值變數中。 屏障基本上是依磚控制計算的結構，就像您使用 **`for`** 迴圈一樣。

7. 變數中的資料 `averages` ，因為它是 `array` 物件，所以必須複製回主機。 這個範例會使用向量轉換運算子。

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
    // Output for SAMPLESIZE = 2 is:
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

建立 `tile_static` 名為的變數， `total` 並為每個執行緒遞增該變數，可能會很吸引人，如下所示：

```cpp
// Do not do this.
tile_static float total;
total += matrix[t_idx];
t_idx.barrier.wait();

averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE* SAMPLESIZE);
```

此方法的第一個問題是 `tile_static` 變數不能有初始化運算式。 第二個問題是指派給的競爭條件 `total` ，因為磚中的所有線程都有權存取變數，而不是特定的順序。 您可以將演算法的程式設計成隻允許一個執行緒存取每個屏障的總計，如下所示。 不過，此解決方案不是可擴充的。

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

有兩種必須同步處理的記憶體存取：全域記憶體存取和 `tile_static` 記憶體存取。 `concurrency::array`物件只會配置全域記憶體。 `concurrency::array_view`可以參考全域記憶體、 `tile_static` 記憶體或兩者，視其結構而定。  有兩種類型的記憶體必須進行同步處理：

- 全域記憶體

- `tile_static`

*記憶體隔離*可確保執行緒磚中的其他執行緒可以使用記憶體存取，而且會根據程式循序執行記憶體存取。 為了確保這一點，編譯器和處理器不會重新排列整個範圍中的讀取和寫入。 在 C++ AMP 中，會透過呼叫下列其中一個方法來建立記憶體隔離：

- [tile_barrier：： Wait 方法](reference/tile-barrier-class.md#wait)：建立全域和記憶體周圍的範圍 `tile_static` 。

- [tile_barrier：： Wait_with_all_memory_fence 方法](reference/tile-barrier-class.md#wait_with_all_memory_fence)：建立全域和記憶體周圍的範圍 `tile_static` 。

- [tile_barrier：： Wait_with_global_memory_fence 方法](reference/tile-barrier-class.md#wait_with_global_memory_fence)：只會在全域記憶體周圍建立一個範圍。

- [tile_barrier：： Wait_with_tile_static_memory_fence 方法](reference/tile-barrier-class.md#wait_with_tile_static_memory_fence)：只會在記憶體周圍建立一個範圍 `tile_static` 。

呼叫您所需的特定範圍，可以改善應用程式的效能。 屏障類型會影響編譯器和硬體重新排序語句的方式。 例如，如果您使用全域記憶體的範圍，它只會套用到全域記憶體存取，因此編譯器和硬體可能會將讀取和寫入重新排列至範圍 `tile_static` 兩邊的變數。

在下一個範例中，屏障會同步處理對 `tileValues` 變數的寫入 `tile_static` 。 在此範例中， `tile_barrier::wait_with_tile_static_memory_fence` 會呼叫，而不是 `tile_barrier::wait` 。

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
