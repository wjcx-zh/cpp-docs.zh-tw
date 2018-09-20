---
title: 逐步解說： 矩陣乘法 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 61172e8b-da71-4200-a462-ff3a908ab0cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d10ab2a6243af5b6e70cb86d3d54ca291a5b9173
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446123"
---
# <a name="walkthrough-matrix-multiplication"></a>逐步解說：矩陣乘法

此逐步解說示範如何使用 c + + AMP 來加速執行矩陣乘法。 會顯示兩種演算法，另一個則沒有並排顯示，一個用於並排顯示。

## <a name="prerequisites"></a>必要條件

在開始之前：

- 讀取[c + + AMP 概觀](../../parallel/amp/cpp-amp-overview.md)。

- 讀取[使用磚](../../parallel/amp/using-tiles.md)。

- 請確定您的電腦上安裝的 Windows 7、 Windows 8、 Windows Server 2008 R2 或 Windows Server 2012。

### <a name="to-create-the-project"></a>若要建立專案

1. 在 Visual Studio 中的功能表列上選擇 **檔案** > **新增** > **專案**。

2. 底下**已安裝**在 [範本] 窗格中，選取**Visual c + +**。

3. 選取**空專案**，輸入`MatrixMultiply`中**名稱** 方塊中，然後選擇**確定** 按鈕。

4. 選擇 [下一步] 按鈕。

5. 中**方案總管**，開啟捷徑功能表**原始程式檔**，然後選擇**新增** > **新項目**。

6. 在 **加入新項目**對話方塊中，選取**c + + 檔 (.cpp)**，輸入`MatrixMultiply.cpp`中**名稱** 方塊中，然後選擇 **新增**按鈕。

## <a name="multiplication-without-tiling"></a>乘法，而不需要並排顯示

在本節中，請考慮 A 和 B，且會定義，如下所示的兩個矩陣相乘︰

![3&#45;的&#45;2 的矩陣](../../parallel/amp/media/campmatrixanontiled.png "campmatrixanontiled")

![2&#45;的&#45;3 的矩陣](../../parallel/amp/media/campmatrixbnontiled.png "campmatrixbnontiled")

A 是 3-2 矩陣，而 B 是 2-3 的矩陣。 由 B 相乘的乘積是下列 3-3 矩陣。 產品是計算方式是乘的 B 項的資料行的資料列。

![3&#45;的&#45;3 的矩陣](../../parallel/amp/media/campmatrixproductnontiled.png "campmatrixproductnontiled")

### <a name="to-multiply-without-using-c-amp"></a>要相乘，而不使用 c + + AMP

1. 開啟 MatrixMultiply.cpp，並使用下列的程式碼取代現有的程式碼。

```cpp
#include <iostream>

void MultiplyWithOutAMP() {
    int aMatrix[3][2] = {{1, 4}, {2, 5}, {3, 6}};
    int bMatrix[2][3] = {{7, 8, 9}, {10, 11, 12}};
    int product[3][3] = {{0, 0, 0}, {0, 0, 0}, {0, 0, 0}};

    for (int row = 0; row < 3; row++) {
        for (int col = 0; col < 3; col++) {
            // Multiply the row of A by the column of B to get the row, column of product.
            for (int inner = 0; inner < 2; inner++) {
                product[row][col] += aMatrix[row][inner] * bMatrix[inner][col];
            }
            std::cout << product[row][col] << "  ";
        }
        std::cout << "\n";
    }
}

void main() {
    MultiplyWithOutAMP();
    getchar();
}
```

    The algorithm is a straightforward implementation of the definition of matrix multiplication. It does not use any parallel or threaded algorithms to reduce the computation time.

2. 在功能表列上，依序選擇 [檔案] > [全部儲存]。

3. 選擇**F5**開始偵錯，並確認輸出正確無誤的鍵盤快速鍵。

4. 選擇**Enter**結束應用程式。

### <a name="to-multiply-by-using-c-amp"></a>若要將乘以使用 c + + AMP

1. 在 MatrixMultiply.cpp，新增下列程式碼，再`main`方法。

```cpp
void MultiplyWithAMP() {
    int aMatrix[] = { 1, 4, 2, 5, 3, 6 };
    int bMatrix[] = { 7, 8, 9, 10, 11, 12 };
    int productMatrix[] = { 0, 0, 0, 0, 0, 0, 0, 0, 0 };

    array_view<int, 2> a(3, 2, aMatrix);

    array_view<int, 2> b(2, 3, bMatrix);

    array_view<int, 2> product(3, 3, productMatrix);

    parallel_for_each(product.extent,
        [=] (index<2> idx) restrict(amp) {
            int row = idx[0];
            int col = idx[1];
            for (int inner = 0; inner <2; inner++) {
                product[idx] += a(row, inner)* b(inner, col);
            }
        });

    product.synchronize();

    for (int row = 0; row <3; row++) {
        for (int col = 0; col <3; col++) {
            //std::cout << productMatrix[row*3 + col] << "  ";
            std::cout << product(row, col) << "  ";
        }
        std::cout << "\n";
    }
}
```

    The AMP code resembles the non-AMP code. The call to `parallel_for_each` starts one thread for each element in `product.extent`, and replaces the `for` loops for row and column. The value of the cell at the row and column is available in `idx`. You can access the elements of an `array_view` object by using either the `[]` operator and an index variable, or the `()` operator and the row and column variables. The example demonstrates both methods. The `array_view::synchronize` method copies the values of the `product` variable back to the `productMatrix` variable.

2. 新增下列`include`和`using`MatrixMultiply.cpp 頂端的陳述式。

```cpp
#include <amp.h>
using namespace concurrency;
```

3. 修改`main`方法來呼叫`MultiplyWithAMP`方法。

```cpp
void main() {
    MultiplyWithOutAMP();
    MultiplyWithAMP();
    getchar();
}
```

4. 選擇**Ctrl**+**F5**開始偵錯，並確認輸出正確無誤的鍵盤快速鍵。

5. 選擇**空格鍵**結束應用程式。

## <a name="multiplication-with-tiling"></a>乘法與並排顯示

並排顯示是您資料的資料分割為大小相等的子集，稱為磚的技術。 三個項目變更時使用並排顯示。

- 您可以建立`tile_static`變數。 中的資料存取`tile_static`空間可以是許多倍比在全域空間資料的存取權。 執行個體`tile_static`變數是每個 tile 建立，且 tile 中的所有執行緒存取的變數。 並排顯示的主要優點是提升的效能，因為`tile_static`存取。

- 您可以呼叫[tile_barrier:: wait](reference/tile-barrier-class.md#wait)停止所有指定一行程式碼的一個 tile 中執行緒的方法。 您無法保證的順序，執行緒將只能在執行中，所有一個 tile 中的執行緒將會停止在對`tile_barrier::wait`它們繼續執行之前。

- 您具有存取權的執行緒，相對於整個索引`array_view`物件和相對於 tile 的索引。 藉由使用本機的索引，您可以讓您的程式碼容易閱讀及偵錯。

若要利用並排顯示中的矩陣相乘，演算法必須分割成磚的 矩陣，然後複製 tile 資料到`tile_static`以利快速存取的變數。 在此範例中，矩陣會分割成相同大小的 submatrices。 找不到乘以 submatrices 的產品。 兩個矩陣和他們的產品，在此範例如下：

![4&#45;的&#45;4 矩陣](../../parallel/amp/media/campmatrixatiled.png "campmatrixatiled")

![4&#45;的&#45;4 矩陣](../../parallel/amp/media/campmatrixbtiled.png "campmatrixbtiled")

![4&#45;的&#45;4 矩陣](../../parallel/amp/media/campmatrixproducttiled.png "campmatrixproducttiled")

矩陣會分割成四個 2 x 2 矩陣，定義如下：

![4&#45;的&#45;分割成 2 的 4 矩陣&#45;的&#45;2 sub&#45;矩陣](../../parallel/amp/media/campmatrixapartitioned.png "campmatrixapartitioned")

![4&#45;的&#45;分割成 2 的 4 矩陣&#45;的&#45;2 sub&#45;矩陣](../../parallel/amp/media/campmatrixbpartitioned.png "campmatrixbpartitioned")

產品的 A 和 B 可以寫入和計算，如下所示：

![4&#45;的&#45;分割成 2 的 4 矩陣&#45;的&#45;2 sub&#45;矩陣](../../parallel/amp/media/campmatrixproductpartitioned.png "campmatrixproductpartitioned")

因為矩陣`a`透過`h`為 2x2 矩陣的所有產品，而且它們的總和也 2x2 矩陣。 它也會遵循 A * B 是 4 x 4 矩陣，如預期般運作。 若要快速檢查演算法，計算的第一個資料列中的項目，產品中的第一個資料行的值。 在範例中，這會是元素的值中的第一個資料列和第一個資料行`ae + bg`。 您只需要計算的第一個資料行、 第一個資料列`ae`和`bg`每個詞彙。 該值`ae`是`1*1 + 2*5 = 11`。 值`bg`是`3*1 + 4*5 = 23`。 最終的值會是`11 + 23 = 34`，這是正確。

若要實作這個演算法，將程式碼：

- 會使用`tiled_extent`物件而非`extent`物件中`parallel_for_each`呼叫。

- 會使用`tiled_index`物件而非`index`物件中`parallel_for_each`呼叫。

- 建立`tile_static`變數來保存 submatrices。

- 使用`tile_barrier::wait`停止 submatrices 之產品為計算執行緒的方法。

### <a name="to-multiply-by-using-amp-and-tiling"></a>若要將乘以使用 AMP 和並排顯示

1. 在 MatrixMultiply.cpp，新增下列程式碼，再`main`方法。

```cpp
void MultiplyWithTiling() {
    // The tile size is 2.
    static const int TS = 2;

    // The raw data.
    int aMatrix[] = { 1, 2, 3, 4, 5, 6, 7, 8, 1, 2, 3, 4, 5, 6, 7, 8 };
    int bMatrix[] = { 1, 2, 3, 4, 5, 6, 7, 8, 1, 2, 3, 4, 5, 6, 7, 8 };
    int productMatrix[] = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };

    // Create the array_view objects.
    array_view<int, 2> a(4, 4, aMatrix);
    array_view<int, 2> b(4, 4, bMatrix);
    array_view<int, 2> product(4, 4, productMatrix);

    // Call parallel_for_each by using 2x2 tiles.
    parallel_for_each(product.extent.tile<TS, TS>(),
        [=] (tiled_index<TS, TS> t_idx) restrict(amp)
        {
            // Get the location of the thread relative to the tile (row, col)
            // and the entire array_view (rowGlobal, colGlobal).
            int row = t_idx.local[0];
            int col = t_idx.local[1];
            int rowGlobal = t_idx.global[0];
            int colGlobal = t_idx.global[1];
            int sum = 0;

            // Given a 4x4 matrix and a 2x2 tile size, this loop executes twice for each thread.
            // For the first tile and the first loop, it copies a into locA and e into locB.
            // For the first tile and the second loop, it copies b into locA and g into locB.
            for (int i = 0; i < 4; i += TS) {
                tile_static int locA[TS][TS];
                tile_static int locB[TS][TS];
                locA[row][col] = a(rowGlobal, col + i);
                locB[row][col] = b(row + i, colGlobal);
                // The threads in the tile all wait here until locA and locB are filled.
                t_idx.barrier.wait();

                // Return the product for the thread. The sum is retained across
                // both iterations of the loop, in effect adding the two products
                // together, for example, a*e.
                for (int k = 0; k < TS; k++) {
                    sum += locA[row][k] * locB[k][col];
                }

                // All threads must wait until the sums are calculated. If any threads
                // moved ahead, the values in locA and locB would change.
                t_idx.barrier.wait();
                // Now go on to the next iteration of the loop.
            }

            // After both iterations of the loop, copy the sum to the product variable by using the global location.
            product[t_idx.global] = sum;
        });

    // Copy the contents of product back to the productMatrix variable.
    product.synchronize();

    for (int row = 0; row <4; row++) {
        for (int col = 0; col <4; col++) {
            // The results are available from both the product and productMatrix variables.
            //std::cout << productMatrix[row*3 + col] << "  ";
            std::cout << product(row, col) << "  ";
        }
        std::cout << "\n";
    }
}
```

    This example is significantly different than the example without tiling. The code uses these conceptual steps:

    1. 複製的圖格 [0，0] 的項目`a`成`locA`。 複製的圖格 [0，0] 的項目`b`成`locB`。 請注意，`product`並排顯示，不`a`和`b`。 因此，您使用全域索引來存取`a, b`，和`product`。 若要呼叫`tile_barrier::wait`是不可或缺的。 它會先停止所有的磚中的執行緒，等到`locA`和`locB`填滿。

    2. 乘`locA`並`locB`並將結果放在`product`。

    3. 複製的圖格 [0，1] 的項目`a`成`locA`。 複製的圖格 [1，0] 的項目`b`成`locB`。

    4. 乘`locA`並`locB`並將其新增至結果對於已處於`product`。

    5. 完成 [0，0] 磚的乘法運算。

    6. 針對其他四個圖格重複。 沒有任何編製索引專為圖格，執行緒可以執行以任何順序。 當每個執行緒執行時，`tile_static`變數會適當地建立每個圖格和呼叫`tile_barrier::wait`控制程式流程。

    7. 當您仔細檢查的演算法，請注意，載入每個 submatrix`tile_static`記憶體兩次。 資料傳輸會花費的時間。 不過，一旦資料位於`tile_static`記憶體資料的存取權會更快。 計算產品需要重複的存取 submatrices 中的值，因為沒有整體的效能改善。 每個演算法，測試，才能尋找最佳的演算法和並排顯示大小而定。

         在非 AMP 和非並排顯示範例中，A 的每個項目，且 B 從來計算產品的全域記憶體存取四次。 在圖格範例中，每個項目來存取兩次從全域記憶體以及四次`tile_static`記憶體。 這不是效能大幅提高。 不過，如果 A 和 B 是 1024 x 1024 矩陣和圖格大小是 16，會有顯著的效能提升。 在此情況下，每個項目會複製到`tile_static`記憶體只有 16 倍，並從存取`tile_static`1024年倍的記憶體。

2. 修改主要的方法，以呼叫`MultiplyWithTiling`方法，如所示。

```cpp
void main() {
    MultiplyWithOutAMP();
    MultiplyWithAMP();
    MultiplyWithTiling();
    getchar();
}
```

3. 選擇**Ctrl**+**F5**開始偵錯，並確認輸出正確無誤的鍵盤快速鍵。

4. 選擇**空間**列結束應用程式。

## <a name="see-also"></a>另請參閱

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[逐步解說：偵錯 C++ AMP 應用程式](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)