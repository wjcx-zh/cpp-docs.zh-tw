---
title: 逐步解說：矩陣乘法
ms.date: 04/23/2019
ms.assetid: 61172e8b-da71-4200-a462-ff3a908ab0cf
ms.openlocfilehash: a84383aa02b3f8300774e18ba2b27655d07b72ae
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075713"
---
# <a name="walkthrough-matrix-multiplication"></a>逐步解說：矩陣乘法

此逐步解說示範如何使用C++ AMP 來加速矩陣乘法的執行。 呈現兩種演算法，其中一個不會並排顯示，另一種則是平鋪。

## <a name="prerequisites"></a>Prerequisites

開始之前：

- 閱讀[ C++ AMP 總覽](../../parallel/amp/cpp-amp-overview.md)。

- [使用磚](../../parallel/amp/using-tiles.md)閱讀。

- 請確定您至少執行 Windows 7 或 Windows Server 2008 R2。

### <a name="to-create-the-project"></a>若要建立專案

建立新專案的指示會根據您已安裝的 Visual Studio 版本而有所不同。 請確定您在左上角將版本選取器設定為正確的版本。

::: moniker range="vs-2019"

### <a name="to-create-the-project-in-visual-studio-2019"></a>若要在 Visual Studio 2019 中建立專案

1. 在功能表列上 **，選擇 [** 檔案] > [**新增**>**專案**]，開啟 [**建立新的專案**] 對話方塊。

1. 在對話方塊頂端，將 [語言] 設定為 **C++** ，將 [平台] 設定為 **Windows**，並將 [專案類型] 設定為**主控台**。

1. 從篩選過的專案類型清單中，選擇 [**空白專案**]，然後選擇 **[下一步]** 。 在下一個頁面的 [**名稱**] 方塊中，輸入*MatrixMultiply*以指定專案的名稱，並視需要指定專案位置。

   ![新的主控台應用程式](../../build/media/mathclient-project-name-2019.png "新的主控台應用程式")

1. 選擇 [建立] 按鈕以建立用戶端專案。

1. 在**方案總管**中，開啟 [**原始**程式檔] 的快捷方式功能表，然後選擇 [**加入**>**新專案**]。

1. 在 [**加入新專案**] 對話方塊中，選取 **C++ [檔案（.cpp）** ]，在 [**名稱**] 方塊中輸入*MatrixMultiply* ，然後選擇 [**新增**] 按鈕。

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-project-in-visual-studio-2017-or-2015"></a>若要在 Visual Studio 2017 或2015中建立專案

1. 在 Visual Studio 的功能表列上 **，選擇 [** 檔案] [檔案] [>**新增**>**專案**]。

1. 在 [**已安裝**] 的 [範本] 窗格中，選取 [ **Visual C++** ]。

1. 選取 [**空專案**]，在 [**名稱**] 方塊中輸入*MatrixMultiply* ，然後選擇 [**確定]** 按鈕。

1. 選擇 [下一步] 按鈕。

1. 在**方案總管**中，開啟 [**原始**程式檔] 的快捷方式功能表，然後選擇 [**加入**>**新專案**]。

1. 在 [**加入新專案**] 對話方塊中，選取 **C++ [檔案（.cpp）** ]，在 [**名稱**] 方塊中輸入*MatrixMultiply* ，然後選擇 [**新增**] 按鈕。

::: moniker-end

## <a name="multiplication-without-tiling"></a>不並排的乘法

在本節中，請考慮兩個矩陣 A 和 B 的乘法，其定義如下：

![3&#45;x&#45;2 矩陣 A](../../parallel/amp/media/campmatrixanontiled.png "3&#45;x&#45;2 矩陣 A")

![2&#45;x&#45;3 矩陣 B](../../parallel/amp/media/campmatrixbnontiled.png "2&#45;x&#45;3 矩陣 B")

是 3 x 2 的矩陣，而 B 是 2 x 3 的矩陣。 將 A 乘以 B 的乘積為下列3到3個矩陣。 產品的計算方式是將的資料列乘以元素的 B 元素的資料行。

![3&#45;x&#45;3 產品矩陣](../../parallel/amp/media/campmatrixproductnontiled.png "3&#45;x&#45;3 產品矩陣")

### <a name="to-multiply-without-using-c-amp"></a>若要相乘而C++不使用 AMP

1. 開啟 MatrixMultiply，並使用下列程式碼來取代現有的程式碼。

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

   int main() {
       MultiplyWithOutAMP();
       getchar();
   }
   ```

   演算法是矩陣乘法定義的直接執行。 它不會使用任何平行或執行緒演算法來減少計算時間。

1. 在功能表列上，依序選擇 [檔案] > [全部儲存]。

1. 選擇**F5**鍵盤快速鍵以開始進行偵錯工具，並確認輸出正確。

1. 選擇**Enter**以結束應用程式。

### <a name="to-multiply-by-using-c-amp"></a>使用C++ AMP 乘以

1. 在 MatrixMultiply 中，將下列程式碼加入 `main` 方法前面。

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

   AMP 程式碼類似于非 AMP 程式碼。 對 `parallel_for_each` 的呼叫會針對 `product.extent`中的每個元素啟動一個執行緒，並取代資料列和資料行的 `for` 迴圈。 資料列和資料行的資料格值可在 `idx`中取得。 您可以使用 `[]` 運算子和索引變數，或是 `()` 運算子和資料列和資料行變數，來存取 `array_view` 物件的元素。 此範例會示範這兩種方法。 `array_view::synchronize` 方法會將 `product` 變數的值複製回 `productMatrix` 變數。

1. 在 MatrixMultiply 的頂端新增下列 `include` 和 `using` 語句。

   ```cpp
   #include <amp.h>
   using namespace concurrency;
   ```

1. 修改 `main` 方法以呼叫 `MultiplyWithAMP` 方法。

   ```cpp
   int main() {
       MultiplyWithOutAMP();
       MultiplyWithAMP();
       getchar();
   }
   ```

1. 按下**Ctrl**+**F5**鍵盤快速鍵，以開始進行偵錯工具，並驗證輸出是否正確。

1. 按**空格鍵**結束應用程式。

## <a name="multiplication-with-tiling"></a>與並排平相乘

「並排顯示」是一種將資料分割成相等大小子集的技術，也就是所謂的磚。 當您使用並排時，三件事會改變。

- 您可以建立 `tile_static` 變數。 存取 `tile_static` 空間中的資料，速度可能會比存取全域空間中的資料快許多倍。 系統會為每個磚建立 `tile_static` 變數的實例，而磚中的所有線程都可以存取該變數。 並排的主要優點是因為 `tile_static` 存取而提升效能。

- 您可以呼叫[tile_barrier：： wait](reference/tile-barrier-class.md#wait)方法，在指定的程式程式碼停止一個磚中的所有線程。 您無法保證執行緒執行的順序，只有一個磚中的所有線程都會在 `tile_barrier::wait` 的呼叫停止，然後再繼續執行。

- 您可以存取相對於整個 `array_view` 物件的執行緒索引，以及相對於磚的索引。 藉由使用本機索引，您可以讓程式碼更容易讀取和 debug。

若要利用矩陣乘法的並排顯示，演算法必須將矩陣分割成磚，然後將磚資料複製到 `tile_static` 變數中，以加快存取的速度。 在此範例中，矩陣會分割成大小相同的 submatrices。 藉由將 submatrices 乘以來找到產品。 此範例中的兩個矩陣和其產品如下：

![4&#45;x&#45;4 矩陣 A](../../parallel/amp/media/campmatrixatiled.png "4&#45;x&#45;4 矩陣 A")

![4&#45;x&#45;4 矩陣 B](../../parallel/amp/media/campmatrixbtiled.png "4&#45;x&#45;4 矩陣 B")

![4&#45;x&#45;4 產品矩陣](../../parallel/amp/media/campmatrixproducttiled.png "4&#45;x&#45;4 產品矩陣")

矩陣會分割成四個2x2 矩陣，其定義如下：

![4&#45;x&#45;4 矩陣，分割成&#45;&#45;2 個子矩陣&#45;](../../parallel/amp/media/campmatrixapartitioned.png "4&#45;x&#45;4 矩陣，分割成&#45;&#45;2 個子矩陣&#45;")

![4&#45;x&#45;4 矩陣 B 分割成&#45;&#45;2 個子矩陣&#45;](../../parallel/amp/media/campmatrixbpartitioned.png "4&#45;x&#45;4 矩陣 B 分割成&#45;&#45;2 個子矩陣&#45;")

A 和 B 的產品現在可以撰寫和計算，如下所示：

![4&#45;x&#45;4 矩陣 A B 分割成&#45;&#45;2 個子矩陣&#45;](../../parallel/amp/media/campmatrixproductpartitioned.png "4&#45;x&#45;4 矩陣 A B 分割成&#45;&#45;2 個子矩陣&#45;")

因為矩陣 `a` 至 `h` 是2x2 矩陣，所以所有產品和其總和也都是2x2 矩陣。 此外，A 和 B 的乘積也會如預期般出現4x4 矩陣。 若要快速檢查演算法，請在產品的第一個資料列、第一個資料行中計算元素的值。 在此範例中，這會是第一個資料列中的元素值，以及 `ae + bg`的第一個資料行。 您只需要計算第一個資料行、`ae` 的第一個資料列，以及每個詞彙的 `bg`。 `ae` 的該值 `(1 * 1) + (2 * 5) = 11`。 `bg` 的值為 `(3 * 1) + (4 * 5) = 23`。 最終的值是 `11 + 23 = 34`，這是正確的。

若要執行此演算法，程式碼：

- 使用 `tiled_extent` 物件，而不是 `parallel_for_each` 呼叫中的 `extent` 物件。

- 使用 `tiled_index` 物件，而不是 `parallel_for_each` 呼叫中的 `index` 物件。

- 建立 `tile_static` 變數來保存 submatrices。

- 使用 `tile_barrier::wait` 方法來停止執行緒，以計算 submatrices 的產品。

### <a name="to-multiply-by-using-amp-and-tiling"></a>使用 AMP 和並排的方式乘以

1. 在 MatrixMultiply 中，將下列程式碼加入 `main` 方法前面。

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

   這個範例與不進行並排的範例截然不同。 程式碼會使用這些概念步驟：
   1. 將圖格 [0，0] 的 `a` 的元素複製到 `locA`。 將圖格 [0，0] 的 `b` 的元素複製到 `locB`。 請注意，`product` 已並排顯示，而不是 `a` 和 `b`。 因此，您可以使用全域索引來存取 `a, b`，並 `product`。 `tile_barrier::wait` 的呼叫是必要的。 它會停止磚中的所有線程，直到 `locA` 和 `locB` 都填滿為止。

   1. 將 `locA` 和 `locB` 相乘，並將結果放在 `product`中。

   1. 將圖格 [0，1] 的 `a` 的元素複製到 `locA`。 將圖格 [1，0] 的 `b` 的元素複製到 `locB`。

   1. 將 `locA` 和 `locB` 相乘，並將它們加入至已在 `product`中的結果。

   1. 磚 [0，0] 的乘法已完成。

   1. 針對其他四個磚重複上述步驟。 沒有特別針對磚的編制索引，而且執行緒可以依任何循序執行。 當每個執行緒執行時，會適當地為每個磚建立 `tile_static` 變數，而呼叫 `tile_barrier::wait` 會控制程式流程。

   1. 當您仔細檢查演算法時，請注意每個 submatrix 都會載入到 `tile_static` 記憶體兩次。 該資料傳輸需要一些時間。 不過，一旦資料位於 `tile_static` 記憶體中，存取資料的速度就會更快。 因為計算產品需要重複存取 submatrices 中的值，所以會有整體的效能提升。 針對每個演算法，需要進行實驗以找出最佳的演算法和磚大小。

   在非 AMP 和非磚範例中，會從全域記憶體存取 A 和 B 的每個元素四次，以計算產品。 在圖格範例中，每個專案都會從全域記憶體存取兩次，而從 `tile_static` 記憶體取四次。 這不是顯著的效能提升。 不過，如果 A 和 B 是1024x1024 矩陣，而磚大小是16，則會有顯著的效能提升。 在此情況下，每個元素只會複製到 `tile_static` 記憶體16次，並從 `tile_static` 記憶體1024次存取。

1. 修改 main 方法以呼叫 `MultiplyWithTiling` 方法，如下所示。

   ```cpp
   int main() {
       MultiplyWithOutAMP();
       MultiplyWithAMP();
       MultiplyWithTiling();
       getchar();
   }
   ```

1. 按下**Ctrl**+**F5**鍵盤快速鍵，以開始進行偵錯工具，並驗證輸出是否正確。

1. 按**空格鍵**以結束應用程式。

## <a name="see-also"></a>另請參閱

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[逐步解說：偵錯 C++ AMP 應用程式](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)
