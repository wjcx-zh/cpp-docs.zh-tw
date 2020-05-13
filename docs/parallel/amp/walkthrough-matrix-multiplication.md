---
title: 逐步解說：矩陣乘法
ms.date: 04/23/2019
ms.assetid: 61172e8b-da71-4200-a462-ff3a908ab0cf
ms.openlocfilehash: f30f8dc235bf0e76c342bea26a35bcbb36cfa237
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366804"
---
# <a name="walkthrough-matrix-multiplication"></a>逐步解說：矩陣乘法

此分步演練演示了如何使用C++ AMP加速執行矩陣乘法。 提出了兩種演演演算法,一種不平鋪,一種不平鋪。

## <a name="prerequisites"></a>Prerequisites

開始之前：

- 閱讀[C++ AMP 概述](../../parallel/amp/cpp-amp-overview.md)。

- [使用磁貼](../../parallel/amp/using-tiles.md)讀取 。

- 請確保您至少運行的是 Windows 7 或 Windows 伺服器 2008 R2。

### <a name="to-create-the-project"></a>若要建立專案

創建新項目的說明因已安裝的 Visual Studio 版本而異。 要查看您首選版本的 Visual Studio 的文件,請使用**版本**選擇器控制項。 它位於此頁面的目錄頂部。

::: moniker range="vs-2019"

### <a name="to-create-the-project-in-visual-studio-2019"></a>在視覺工作室 2019 中建立專案

1. 在功能表列上，選擇 [檔案]** [新增]** > ** [專案]** > ****，以開啟 [建立新專案]**** 對話方塊。

1. 在對話方塊頂端，將 [語言]**** 設定為 **C++**，將 [平台]**** 設定為 **Windows**，並將 [專案類型]**** 設定為**主控台**。

1. 從篩選的項目類型清單中,選擇 **「空專案」,** 然後選擇 **「下一步**」 。 在下一頁中,在 **「名稱」** 框中輸入*MatrixMultiply*以指定專案的名稱,並根據需要指定專案位置。

   ![新的主控台應用程式](../../build/media/mathclient-project-name-2019.png "新的主控台應用程式")

1. 選擇 [建立]**** 按鈕以建立用戶端專案。

1. 在**解決方案資源管理員**中,打開**源檔案的**快捷方式功能表,然後選擇**Add**>「**添加新項**」。

1. 在「**新增新項目」** 對話框中,選擇**C++檔 (.cpp)**,在 **「名稱」** 框中輸入*Matrixmultiply.cpp,* 然後選擇 **「 添加**」按鈕。

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-project-in-visual-studio-2017-or-2015"></a>在 Visual Studio 2017 或 2015 建立專案

1. 在 Visual Studio 的選單欄上,選擇 **「檔案**>**新專案**>**」 。**

1. 在樣本窗格中 **「安裝」** 下,選擇 **「可視C++**」。。

1. 選擇 **"空專案**",在 **"名稱"** 框中輸入*矩陣乘法*,然後選擇 **"確定**"按鈕。

1. 選擇 [下一步]**** 按鈕。

1. 在**解決方案資源管理員**中,打開**源檔案的**快捷方式功能表,然後選擇**Add**>「**添加新項**」。

1. 在「**新增新項目」** 對話框中,選擇**C++檔 (.cpp)**,在 **「名稱」** 框中輸入*Matrixmultiply.cpp,* 然後選擇 **「 添加**」按鈕。

::: moniker-end

## <a name="multiplication-without-tiling"></a>不平鋪的乘法

在本節中,請考慮兩個矩陣 A 和 B 的乘法,它們的定義如下:

![3&#45;由&#45;2 矩陣 A](../../parallel/amp/media/campmatrixanontiled.png "3&#45;由&#45;2 矩陣 A")

![2&#45;矩阵 B&#45;](../../parallel/amp/media/campmatrixbnontiled.png "2&#45;矩阵 B&#45;")

A 是 3×2 矩陣,B 為 2×3 矩陣。 將 A 乘以 B 的乘積為以下 3×3 矩陣。 通過乘以 A 元素的列來計算產品。

![3&#45;3 個產品矩陣&#45;](../../parallel/amp/media/campmatrixproductnontiled.png "3&#45;3 個產品矩陣&#45;")

### <a name="to-multiply-without-using-c-amp"></a>不使用C++ AMP 相乘

1. 打開矩陣乘法.cpp 並使用以下代碼替換現有代碼。

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

   該演演演算法是矩陣乘法定義的一個直接實現。 它不使用任何並行或線程演演演算法來減少計算時間。

1. 在選單列上,選擇 **「全部儲存檔** > **Save All**」。

1. 選擇**F5**鍵盤快捷鍵以開始除錯並驗證輸出是否正確。

1. 選擇 **「輸入」** 以離開應用程式。

### <a name="to-multiply-by-using-c-amp"></a>使用C++ AMP 相乘

1. 在 Matrixmultiply.cpp 中`main`,在方法之前添加以下代碼。

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

   AMP 代碼類似於非 AMP 代碼。 呼叫`parallel_for_each`為`product.extent`中的每個元素啟動一個線程,並替換`for`行 和列的迴圈。 行和列中的儲存格的值在中`idx`可用。 可以使用`[]`運算子和索引變數或`()`運算子`array_view`以及行和列變數訪問物件的元素。 該示例演示了這兩種方法。 此方法`array_view::synchronize``product`將變數的值複製回變數`productMatrix`。

1. 在 Matrixmultiply.cpp 的頂部添加`include`以下`using`內容和語句。

   ```cpp
   #include <amp.h>
   using namespace concurrency;
   ```

1. 變更方法`main`以呼叫`MultiplyWithAMP`方法 。

   ```cpp
   int main() {
       MultiplyWithOutAMP();
       MultiplyWithAMP();
       getchar();
   }
   ```

1. 按**Ctrl**+**F5**鍵盤快速鍵開始調試並驗證輸出是否正確。

1. 按**空格鍵**退出應用程式。

## <a name="multiplication-with-tiling"></a>平鋪乘法

平鋪是一種將數據劃分為大小相等的子集(稱為切片)的技術。 使用平鋪時,有三件事會改變。

- 您可以創建`tile_static`變數。 在空間中`tile_static`訪問數據的速度可能比訪問全域空間中的數據快很多倍。 為每個磁貼創建`tile_static`變數的實例,並且磁貼中的所有線程都有權訪問該變數。 平鋪的主要好處是由於訪問而`tile_static`獲得性能。

- 您可以調用[tile_barrier::wait](reference/tile-barrier-class.md#wait)方法,以在指定的代碼行上停止一個磁貼中的所有線程。 您無法保證線程將運行的順序,只有一個磁貼中的所有線程在繼續執行之前在調用`tile_barrier::wait`時停止。

- 您可以存取線程相對於`array_view`整個 物件的索引和相對於磁貼的索引。 通過使用本地索引,可以使代碼更易於讀取和調試。

為了利用矩陣乘法中的平鋪,演演演算法必須將矩陣分區到切片中,然後將切片數據複製到`tile_static`變數中 ,以便更快地訪問。 在此示例中,矩陣被劃分為大小相等的子矩陣。 通過乘以子矩陣找到產品。 此範例中的兩個矩陣及其產品是:

![4&#45;由&#45;4 矩陣 A](../../parallel/amp/media/campmatrixatiled.png "4&#45;由&#45;4 矩陣 A")

![4&#45;由&#45;4 矩陣 B](../../parallel/amp/media/campmatrixbtiled.png "4&#45;由&#45;4 矩陣 B")

![4&#45;由&#45;4 個產品矩陣](../../parallel/amp/media/campmatrixproducttiled.png "4&#45;由&#45;4 個產品矩陣")

矩陣被劃分為四個 2x2 矩陣,定義如下:

![4&#45;由&#45;4 矩陣 A 分區為 2&#45;由&#45;子&#45;矩阵](../../parallel/amp/media/campmatrixapartitioned.png "4&#45;由&#45;4 矩陣 A 分區為 2&#45;由&#45;子&#45;矩阵")

![4&#45;由&#45;4 矩陣 B 分區為 2&#45;,由&#45;2 子&#45;矩陣](../../parallel/amp/media/campmatrixbpartitioned.png "4&#45;由&#45;4 矩陣 B 分區為 2&#45;,由&#45;2 子&#45;矩陣")

A 和 B 的積數現在可以編寫和計算如下:

![4&#45;由&#45;4 矩陣 A B 分區為 2&#45;由&#45;2 子&#45;矩阵](../../parallel/amp/media/campmatrixproductpartitioned.png "4&#45;由&#45;4 矩陣 A B 分區為 2&#45;由&#45;2 子&#45;矩阵")

由於矩陣`a``h`為 2x2 矩陣,因此所有產品和總和也是 2x2 矩陣。 因此,A 和 B 的乘積是 4x4 矩陣,正如預期的那樣。 要快速檢查演演演算法,請計算第一行中元素的值,在產品中的第一列。 在此範例中,這將是元素在的第一行和第一列中`ae + bg`的元素的值。 您只需要計算每個術語的第一列、第一行`ae``bg`與 。 值為`ae``(1 * 1) + (2 * 5) = 11`。 `bg` 的值為 `(3 * 1) + (4 * 5) = 23`。 最終值為`11 + 23 = 34`,這是正確的。

要實現此演算法,代碼:

- 使用`tiled_extent`物件而不是調用中`extent``parallel_for_each`的物件。

- 使用`tiled_index`物件而不是調用中`index``parallel_for_each`的物件。

- 建立`tile_static`變數以保存子矩陣。

- 使用`tile_barrier::wait`方法停止用於計算子矩陣的產品的線程。

### <a name="to-multiply-by-using-amp-and-tiling"></a>使用 AMP 和平鋪進行乘以

1. 在 Matrixmultiply.cpp 中`main`,在方法之前添加以下代碼。

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

   此示例與不平鋪的範例明顯不同。 程式碼使用以下概念步驟:
   1. 將 的磁貼`a`[0,0]`locA`的元素 複製到 中。 將 的磁貼`b`[0,0]`locB`的元素 複製到 中。 請注意,`product`請注意已平鋪`a``b`, 而不是與 。 因此,您可以使用全域索引來存取`a, b`與`product`。 調用`tile_barrier::wait`至關重要。 它停止磁貼中的所有線程,直到填充`locA``locB`和填充。

   1. 乘`locA``locB`以並將結果`product`放入 中。

   1. 將 的磁貼[0,1]`a`的元素`locA`複製到 中。 將 的磁貼`b`[1,0]`locB`的元素 複製到 中。

   1. 相`locA`乘`locB`並新增它們到 中`product`已有的結果 。

   1. 切片[0,0] 的乘法已完成。

   1. 對其他四個磁貼重複上述步驟。 沒有專門針對切片的索引,線程可以按任何順序執行。 當每個線程執行時,`tile_static`將為每個磁貼適當地創建變數,並相應地呼叫控制`tile_barrier::wait`程式流。

   1. 仔細檢查演演演算法時,請注意每個子矩陣都載入到`tile_static`記憶體中 兩次。 數據傳輸確實需要時間。 但是,一旦數據進入記憶體`tile_static`中,對數據的訪問就會更快。 由於計算產品需要重複存取子矩陣中的值,因此性能會提高。 對於每個演演演算法,需要實驗才能找到最佳演演演算法和切片大小。

   在非 AMP 和非切片範例中,A 和 B 的每個元素從全域記憶體中訪問四次以計算產品。 在磁貼示例中,每個元素從全域記憶體訪問兩次,從`tile_static`記憶體訪問四次。 這不是顯著的性能提升。 但是,如果 A 和 B 是 1024x1024 矩陣,並且切片大小為 16,則性能會顯著提高。 在這種情況下,每個元素將只複製到`tile_static`記憶體 16 次,`tile_static`並從 記憶體訪問 1024 次。

1. 修改主方法以調用`MultiplyWithTiling`方法,如圖所示。

   ```cpp
   int main() {
       MultiplyWithOutAMP();
       MultiplyWithAMP();
       MultiplyWithTiling();
       getchar();
   }
   ```

1. 按**Ctrl**+**F5**鍵盤快速鍵開始調試並驗證輸出是否正確。

1. 按**空格**鍵退出應用程式。

## <a name="see-also"></a>另請參閱

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[逐步解說：偵錯 C++ AMP 應用程式](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)
