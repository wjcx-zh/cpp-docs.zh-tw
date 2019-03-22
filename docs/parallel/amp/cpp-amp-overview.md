---
title: C++ AMP 概觀
ms.date: 11/19/2018
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, requirements
- C++ Accelerated Massive Parallelism, architecture
- C++ AMP
- C++ Accelerated Massive Parallelism, overview
- C++ Accelerated Massive Parallelism
ms.assetid: 9e593b06-6e3c-43e9-8bae-6d89efdd39fc
ms.openlocfilehash: a4bd8546ba551ee37b9c03b5965a4079a3bd9f98
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2019
ms.locfileid: "58328879"
---
# <a name="c-amp-overview"></a>C++ AMP 概觀

C + + Accelerated Massive Parallelism (c + + AMP) 會利用在獨立圖形顯示卡上的圖形處理單元 (GPU) 等資料平行硬體來加速 c + + 程式碼的執行。 藉由使用 c + + AMP，您可以撰寫多維資料演算法，以便利用異質硬體上的平行處理加速執行。 C++ AMP 程式設計模型包含多維陣列、索引、記憶體傳輸、並排顯示和數學函式庫。 您可以使用 c + + AMP 語言擴充功能來控制資料如何從 CPU 移至 GPU 和上一步，以便您可以改善效能。

## <a name="system-requirements"></a>系統需求

- Windows 7 或更新版本

- Windows Server 2008 R2 或更新版本

- DirectX 11 功能層級 11.0 或更新版本的硬體

- 在軟體模擬器上偵錯，Windows 8 或 Windows Server 2012 是必要的。 如需在硬體上偵錯，您必須安裝圖形卡的驅動程式。 如需詳細資訊，請參閱 <<c0> [ 偵錯 GPU 程式碼](/visualstudio/debugger/debugging-gpu-code)。

- 注意:ARM64 上目前不支援 P。

## <a name="introduction"></a>簡介

下列兩個範例說明 c + + AMP 的主要元件。 假設您想要新增的兩個一維陣列的對應項目。 例如，您可能想要新增`{1, 2, 3, 4, 5}`並`{6, 7, 8, 9, 10}`若要取得`{7, 9, 11, 13, 15}`。 不使用 c + + AMP，您可以撰寫下列程式碼，將數字相加並顯示結果。

```cpp
#include <iostream>

void StandardMethod() {

    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5];

    for (int idx = 0; idx < 5; idx++)
    {
        sumCPP[idx] = aCPP[idx] + bCPP[idx];
    }

    for (int idx = 0; idx < 5; idx++)
    {
        std::cout << sumCPP[idx] << "\n";
    }
}
```

重要的部分的程式碼如下所示：

- 資料：資料是由三個陣列所組成。 所有具有相同陣序 (1) 和長度 (5)。

- 反覆項目:第一個`for`迴圈提供一個機制，以逐一查看陣列中的項目。 您想要執行以計算總和的程式碼包含在第一個`for`區塊。

- 索引：`idx`變數存取陣列的個別項目。

使用 c + + AMP，您還是可以改為撰寫下列程式碼。

```cpp
#include <amp.h>
#include <iostream>
using namespace concurrency;

const int size = 5;

void CppAmpMethod() {
    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[size];

    // Create C++ AMP objects.
    array_view<const int, 1> a(size, aCPP);
    array_view<const int, 1> b(size, bCPP);
    array_view<int, 1> sum(size, sumCPP);
    sum.discard_data();

    parallel_for_each(
        // Define the compute domain, which is the set of threads that are created.
        sum.extent,
        // Define the code to run on each thread on the accelerator.
        [=](index<1> idx) restrict(amp) {
            sum[idx] = a[idx] + b[idx];
        }
    );

    // Print the results. The expected output is "7, 9, 11, 13, 15".
    for (int i = 0; i < size; i++) {
        std::cout << sum[i] << "\n";
    }
}
```

相同的基本項目存在，但是會使用 c + + AMP 建構：

- 資料：您可以使用 c + + 陣列建構三個 c + + AMP [array_view](../../parallel/amp/reference/array-view-class.md)物件。 提供四個值來建構`array_view`物件： 資料值、 陣序規範、 項目類型和長度`array_view`每個維度中的物件。 陣序和型別會當做型別參數傳遞。 做為建構函式參數傳遞的資料和長度。 在此範例中，會傳遞至建構函式的 c + + 陣列是一維的。 順位和長度用來建構中的資料的矩形`array_view`物件和值來填滿此陣列的資料。 執行階段程式庫也包含[array 類別](../../parallel/amp/reference/array-class.md)，其具有類似的介面`array_view`類別，並將在本文稍後討論。

- 反覆項目:[Parallel_for_each 函式 (c + + AMP)](reference/concurrency-namespace-functions-amp.md#parallel_for_each)提供一個機制，以逐一查看的資料項目，或*計算網域*。 在此範例中，指定 compute domain `sum.extent`。 您想要執行的程式碼包含在 lambda 運算式中，或是*核心功能*。 `restrict(amp)`指示中使用 c + + AMP 可以加速 c + + 語言的子集。

- 索引：[編製索引類別](../../parallel/amp/reference/index-class.md)變數`idx`，來比對的陣序的其中一個的陣序規範宣告`array_view`物件。 使用索引，您可以存取的個別項目`array_view`物件。

## <a name="shaping-and-indexing-data-index-and-extent"></a>定形和索引的資料： 索引和範圍

您必須定義資料值，並宣告資料的形式，才能執行核心程式碼。 所有資料都已都定義為陣列 (rectangle)，以及您可以定義陣列具有任何陣序 （維度數目）。 資料可以是任何維度中的任何大小。

### <a name="index-class"></a>index 類別

[編製索引類別](../../parallel/amp/reference/index-class.md)中指定位置`array`或`array_view`藉由將從每個維度中的原點的位移封裝成一個物件的物件。 當您存取陣列中的位置時，會傳遞給`index`物件的索引運算子， `[]`，而不是整數索引清單。 您可以使用，以存取每個維度中的項目[array:: operator （) 運算子](reference/array-class.md#operator_call)或[array_view::operator() 運算子](reference/array-view-class.md#operator_call)。

下列範例會建立一維索引，指定第三個項目中的一維`array_view`物件。 索引用來列印中的第三個項目`array_view`物件。 輸出會是 3。

```cpp
int aCPP[] = {1, 2, 3, 4, 5};
array_view<int, 1> a(5, aCPP);

index<1> idx(2);

std::cout << a[idx] << "\n";
// Output: 3
```

下列範例會建立二維索引指定的項目，其中資料列 = 1 且資料行 = 2 中的二維`array_view`物件。 中的第一個參數`index`建構函式是資料列元件，而第二個參數是欄位元件。 輸出為 6。

```cpp
int aCPP[] = {1, 2, 3, 4, 5, 6};
array_view<int, 2> a(2, 3, aCPP);

index<2> idx(1, 2);

std::cout <<a[idx] << "\n";
// Output: 6
```

下列範例會建立立體索引指定的項目，其中深度 = 0 時，資料列 = 1，且資料行 = 3 中的三維`array_view`物件。 請注意第一個參數是深度元件，第二個參數是資料列元件，而第三個參數是欄位元件。 輸出為 8。

```cpp
int aCPP[] = {
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12,
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12};

array_view<int, 3> a(2, 3, 4, aCPP);

// Specifies the element at 3, 1, 0.
index<3> idx(0, 1, 3);

std::cout << a[idx] << "\n";
// Output: 8
```

### <a name="extent-class"></a>extent 類別

[Extent 類別](../../parallel/amp/reference/extent-class.md)的每個維度中指定的資料長度`array`或`array_view`物件。 您可以建立一個範圍，並使用它來建立`array`或`array_view`物件。 您也可以擷取現有的範圍`array`或`array_view`物件。 下列範例會列印在每個維度的範圍長度`array_view`物件。

```cpp
int aCPP[] = {
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12,
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12};
// There are 3 rows and 4 columns, and the depth is two.
array_view<int, 3> a(2, 3, 4, aCPP);

std::cout << "The number of columns is " << a.extent[2] << "\n";
std::cout << "The number of rows is " << a.extent[1] << "\n";
std::cout << "The depth is " << a.extent[0] << "\n";
std::cout << "Length in most significant dimension is " << a.extent[0] << "\n";
```

下列範例會建立`array_view`具有相同的物件為上述範例中，但此範例中的物件會使用維度`extent`物件，而非使用中的明確參數`array_view`建構函式。

```cpp
int aCPP[] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24};
extent<3> e(2, 3, 4);

array_view<int, 3> a(e, aCPP);

std::cout << "The number of columns is " << a.extent[2] << "\n";
std::cout << "The number of rows is " << a.extent[1] << "\n";
std::cout << "The depth is " << a.extent[0] << "\n";
```

## <a name="moving-data-to-the-accelerator-array-and-arrayview"></a>將資料移至加速器： 陣列和 array_view

執行階段程式庫中定義兩個用來將資料移至加速器的資料容器。 它們[array 類別](../../parallel/amp/reference/array-class.md)並[array_view 類別](../../parallel/amp/reference/array-view-class.md)。 `array`類別是在建構物件時，會建立資料的深層複本的容器類別。 `array_view`類別是核心功能存取資料時，會將資料複製的包裝函式類別。 當來源裝置上所需的資料時將資料複製回來。

### <a name="array-class"></a>array 類別

當`array`建構物件，如果您使用建構函式，其中包含資料集的指標，將會建立在加速器上的資料的深層複本。 核心函式會修改加速器上的複本。 核心函式執行完成時，您必須將資料複製回到來源資料結構。 下列範例會將向量中的每個項目乘以 10。 核心功能完成之後，`vector conversion operator`用來將資料複製回向量物件。

```cpp
std::vector<int> data(5);

for (int count = 0; count <5; count++)
{
    data[count] = count;
}

array<int, 1> a(5, data.begin(), data.end());

parallel_for_each(
    a.extent,
    [=, &a](index<1> idx) restrict(amp) {
        a[idx] = a[idx]* 10;
    });

data = a;
for (int i = 0; i < 5; i++)
{
    std::cout << data[i] << "\n";
}
```

### <a name="arrayview-class"></a>array_view 類別

`array_view`有幾乎相同的成員`array`類別，不過基礎行為並不相同。 資料傳遞至`array_view`建構函式不會複寫在 GPU 上，與`array`建構函式。 相反地，將資料複製到加速器，核心函式執行時。 因此，如果您建立兩個`array_view`物件，使用相同的資料，同時`array_view`物件參考相同的記憶體空間。 當您這樣做時，您必須同步處理任何多執行緒的存取。 使用的主要優點`array_view`類別是必要時才會移動資料。

### <a name="comparison-of-array-and-arrayview"></a>陣列和 array_view 比較

下表摘要說明相似之處和之間的差異`array`和`array_view`類別。

|描述|array 類別|array_view 類別|
|-----------------|-----------------|-----------------------|
|當陣序規範已決定時|在編譯時期。|在編譯時期。|
|當範圍已決定|在執行階段。|在執行階段。|
|圖形|矩形。|矩形。|
|資料存放區|是資料容器。|是資料包裝函式。|
|複製|在定義明確和深層複製。|核心功能存取時隱含複本。|
|資料擷取|藉由複製陣列資料回到 CPU 執行緒上的物件。|直接存取`array_view`物件，或藉由呼叫[array_view:: synchronize 方法](reference/array-view-class.md#synchronize)才能繼續存取原始容器上的資料。|

### <a name="shared-memory-with-array-and-arrayview"></a>使用 array 和 array_view 共用的記憶體

共用的記憶體是可由 CPU 和加速器存取的記憶體。 使用共用記憶體排除或大幅降低的 CPU 和加速器之間複製資料的額外負荷。 雖然共用記憶體，其 CPU 和加速器，無法並行存取，而且會產生未定義的行為。

`array` 物件可用來指定關聯的加速器支援共用記憶體的使用更細微的控制。 加速器是否支援共用的記憶體取決於加速器[supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory)屬性，會傳回 **，則為 true**當支援共用的記憶體。 如果支援共用的記憶體，則預設值[access_type 列舉](reference/concurrency-namespace-enums-amp.md#access_type)記憶體配置在加速器上的由`default_cpu_access_type`屬性。 根據預設，`array`並`array_view`物件採用相同`access_type`主要關聯`accelerator`。

藉由設定[array:: cpu_access_type 資料成員](reference/array-class.md#cpu_access_type)屬性`array`明確，您可以進行細部控制使用透過共用記憶體時，以便您可以最佳化的硬體效能的應用程式特性，根據計算核心的記憶體存取模式。 `array_view`會反映相同`cpu_access_type`作為`array`它相關聯; 或者，如果 array_view 建構不具資料來源，其`access_type`會反映第一個使其配置儲存體的環境。 也就是說，如果它第一次存取主機 (CPU)，則其行為就如同透過 CPU 資料來源和共用建立`access_type`的`accelerator_view`藉由擷取關聯; 不過，如果是第一次存取`accelerator_view`，則其行為就如同它是透過建立`array`上，建立`accelerator_view`，並共用`array`的`access_type`。

下列程式碼範例示範如何判斷預設加速器是否支援共用的記憶體，並接著會建立數個具有不同 cpu_access_type 組態的陣列。

```cpp
#include <amp.h>
#include <iostream>

using namespace Concurrency;

int main()
{
    accelerator acc = accelerator(accelerator::default_accelerator);

    // Early out if the default accelerator doesn’t support shared memory.
    if (!acc.supports_cpu_shared_memory)
    {
        std::cout << "The default accelerator does not support shared memory" << std::endl;
        return 1;
    }

    // Override the default CPU access type.
    acc.default_cpu_access_type = access_type_read_write

    // Create an accelerator_view from the default accelerator. The
    // accelerator_view inherits its default_cpu_access_type from acc.
    accelerator_view acc_v = acc.default_view;

    // Create an extent object to size the arrays.
    extent<1> ex(10);

    // Input array that can be written on the CPU.
    array<int, 1> arr_w(ex, acc_v, access_type_write);

    // Output array that can be read on the CPU.
    array<int, 1> arr_r(ex, acc_v, access_type_read);

    // Read-write array that can be both written to and read from on the CPU.
    array<int, 1> arr_rw(ex, acc_v, access_type_read_write);
}
```

## <a name="executing-code-over-data-parallelforeach"></a>資料上執行程式碼： parallel_for_each

[Parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each)函式會定義您想要對中的資料在加速器上執行的程式碼`array`或`array_view`物件。 請考慮下列程式碼從本主題簡介。

```cpp
#include <amp.h>
#include <iostream>
using namespace concurrency;

void AddArrays() {
    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5] = {0, 0, 0, 0, 0};

    array_view<int, 1> a(5, aCPP);
    array_view<int, 1> b(5, bCPP);
    array_view<int, 1> sum(5, sumCPP);

    parallel_for_each(
        sum.extent,
        [=](index<1> idx) restrict(amp)
        {
            sum[idx] = a[idx] + b[idx];
        }
    );

    for (int i = 0; i < 5; i++) {
        std::cout << sum[i] << "\n";
    }
}
```

`parallel_for_each`方法會採用兩個引數，計算網域和 lambda 運算式。

*計算網域*是`extent`物件或`tiled_extent`定義一組的執行緒就能建立平行執行的物件。 計算網域中的每個項目會產生一個執行緒。 在此情況下，`extent`物件是一維陣列，且具有五個項目。 因此，五個執行緒會啟動。

*Lambda 運算式*定義每個執行緒上執行的程式碼。 擷取子句`[=]`，指定 lambda 運算式主體不存取所有擷取的變數值，在此情況下所`a`， `b`，和`sum`。 在此範例中，參數清單會建立一維`index`名為變數`idx`。 值`idx[0]`0 中的第一個執行緒，並增加每個後續的執行緒的一個。 `restrict(amp)`指示中使用 c + + AMP 可以加速 c + + 語言的子集。  具有限制修飾詞的函式的限制詳述於[限制 (c + + AMP)](../../cpp/restrict-cpp-amp.md)。 如需詳細資訊，請參閱， [Lambda 運算式語法](../../cpp/lambda-expression-syntax.md)。

Lambda 運算式可以包含執行的程式碼，或它可以呼叫個別核心功能。 核心函式必須包含`restrict(amp)`修飾詞。 下列範例相當於上述範例中，但它會呼叫個別核心功能。

```cpp
#include <amp.h>
#include <iostream>
using namespace concurrency;

void AddElements(
    index<1> idx,
    array_view<int, 1> sum,
    array_view<int, 1> a,
    array_view<int, 1> b) restrict(amp) {
    sum[idx] = a[idx] + b[idx];
}

void AddArraysWithFunction() {

    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5] = {0, 0, 0, 0, 0};

    array_view<int, 1> a(5, aCPP);
    array_view<int, 1> b(5, bCPP);
    array_view<int, 1> sum(5, sumCPP);

    parallel_for_each(
        sum.extent,
        [=](index<1> idx) restrict(amp) {
            AddElements(idx, sum, a, b);
        }
    );

    for (int i = 0; i < 5; i++) {
        std::cout << sum[i] << "\n";
    }
}
```

## <a name="accelerating-code-tiles-and-barriers"></a>加速程式碼：並排和屏障

您可以使用並排顯示，以獲得額外的加速。 並排顯示會將執行緒分成相等的矩形子集或*圖格*。 您決定您的資料集和您撰寫程式碼的演算法為基礎的適當並排顯示大小。 對於每個執行緒中，您可以存取*全域*相對於整個資料元素的位置`array`或是`array_view`及存取權*本機*相對於 tile 的位置。 使用區域索引值可簡化您的程式碼，因為您不必撰寫程式碼至本機的索引值從全域轉譯。 若要使用並排，呼叫[extent:: tile 方法](reference/extent-class.md#tile)中之計算網域`parallel_for_each`方法，並使用[tiled_index](../../parallel/amp/reference/tiled-index-class.md) lambda 運算式中的物件。

在一般的應用程式中，tile 中的項目相關以某種方式，而且程式碼必須存取和追蹤的值 圖格。 使用[tile_static 關鍵字](../../cpp/tile-static-keyword.md)關鍵字和[tile_barrier:: wait 方法](reference/tile-barrier-class.md#wait)為了達成此目的。 具有變數**tile_static**關鍵字具有範圍跨整個 tile，和每個 tile 建立變數的執行個體。 您必須處理變數的並排-執行緒存取的同步處理。 [Tile_barrier:: wait 方法](reference/tile-barrier-class.md#wait)會停止執行目前的執行緒，直到 tile 中的所有執行緒都到達呼叫至`tile_barrier::wait`。 因此您也可以使用跨磚累積值**tile_static**變數。 然後您可以完成任何需要存取所有值的計算。

下圖代表以磚排列的資料取樣的二維陣列。

![並排範圍中的值的索引](../../parallel/amp/media/camptiledgridexample.png "並排顯示範圍中的索引值")

下列程式碼範例會使用上圖中的取樣資料。 程式碼會並排顯示中值的平均值取代磚中的每個值。

```cpp
// Sample data:
int sampledata[] = {
    2, 2, 9, 7, 1, 4,
    4, 4, 8, 8, 3, 4,
    1, 5, 1, 2, 5, 2,
    6, 8, 3, 2, 7, 2};

// The tiles:
// 2 2    9 7    1 4
// 4 4    8 8    3 4
//
// 1 5    1 2    5 2
// 6 8    3 2    7 2

// Averages:
int averagedata[] = {
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
};

array_view<int, 2> sample(4, 6, sampledata);

array_view<int, 2> average(4, 6, averagedata);

parallel_for_each(
    // Create threads for sample.extent and divide the extent into 2 x 2 tiles.
    sample.extent.tile<2,2>(),
        [=](tiled_index<2,2> idx) restrict(amp) {
        // Create a 2 x 2 array to hold the values in this tile.
        tile_static int nums[2][2];

        // Copy the values for the tile into the 2 x 2 array.
        nums[idx.local[1]][idx.local[0]] = sample[idx.global];

        // When all the threads have executed and the 2 x 2 array is complete, find the average.
        idx.barrier.wait();
        int sum = nums[0][0] + nums[0][1] + nums[1][0] + nums[1][1];

        // Copy the average into the array_view.
        average[idx.global] = sum / 4;
    });

for (int i = 0; i <4; i++) {
    for (int j = 0; j <6; j++) {
        std::cout << average(i,j) << " ";
    }
    std::cout << "\n";
}

// Output:
// 3 3 8 8 3 3
// 3 3 8 8 3 3
// 5 5 2 2 4 4
// 5 5 2 2 4 4
```

## <a name="math-libraries"></a>數學程式庫

C + + AMP 包含兩個數學程式庫。 中的雙精確度程式庫[concurrency:: precise_math 命名空間](../../parallel/amp/reference/concurrency-precise-math-namespace.md)支援雙精確度函式。 它也提供支援單精確度函式中，雖然仍需要的硬體上的雙精確度支援。 其符合[C99 規格 (ISO/IEC 9899)](http://go.microsoft.com/fwlink/p/?linkid=225887)。 加速器必須支援完整雙精確度。 您可以判斷它是否會藉由檢查的值[accelerator:: supports_double_precision 資料成員](reference/accelerator-class.md#supports_double_precision)。 Fast math 程式庫，請在[concurrency:: fast_math 命名空間](../../parallel/amp/reference/concurrency-fast-math-namespace.md)，包含另一組數學函式。 這些函式僅支援`float`運算元，更快速地執行，但精確度不如雙精確度數學程式庫中。 函式內\<amp_math.h > 標頭檔與所有使用宣告`restrict(amp)`。 中的函式\<cmath> > 標頭檔匯入至兩者`fast_math`和`precise_math`命名空間。 **限制**關鍵字用來區別\<cmath> > 版本和 c + + AMP 版本。 下列程式碼會計算使用快速方法，是計算網域中每個值的基底 10 對數。

```cpp
#include <amp.h>
#include <amp_math.h>
#include <iostream>
using namespace concurrency;

void MathExample() {

    double numbers[] = { 1.0, 10.0, 60.0, 100.0, 600.0, 1000.0 };
    array_view<double, 1> logs(6, numbers);

    parallel_for_each(
        logs.extent,
        [=] (index<1> idx) restrict(amp) {
            logs[idx] = concurrency::fast_math::log10(logs[idx]);
        }
    );

    for (int i = 0; i < 6; i++) {
        std::cout << logs[i] << "\n";
    }
}
```

## <a name="graphics-library"></a>圖形文件庫

C + + AMP 包含針對加速圖形程式設計所設計的圖形程式庫。 此文件庫只適用於支援原生繪圖功能的裝置。 方法會在[concurrency:: graphics 命名空間](../../parallel/amp/reference/concurrency-graphics-namespace.md)且包含在\<amp_graphics.h > 標頭檔。 圖形程式庫的主要元件如下：

- [texture 類別](../../parallel/amp/reference/texture-class.md):您可以使用紋理類別從記憶體中或從檔案建立紋理。 紋理類似陣列，因為它們包含資料，而且這些介面類似於指派和複製建構 c + + 標準程式庫中的容器。 如需詳細資訊，請參閱 [C++ 標準程式庫容器](../../standard-library/stl-containers.md)。 樣板參數`texture`類別是項目型別和陣序規範。 順位可以是 1、 2 或 3。 項目類型可以是一種短向量類型在本文稍後所述。

- [writeonly_texture_view 類別](../../parallel/amp/reference/writeonly-texture-view-class.md):提供所有材質的唯寫存取。

- 短向量庫：定義短向量類型，長度為 2、 3 和 4 為基礎的一組**int**， `uint`， **float**， **double**， [norm](../../parallel/amp/reference/norm-class.md)，或[unorm](../../parallel/amp/reference/unorm-class.md)。

## <a name="universal-windows-platform-uwp-apps"></a>通用 Windows 平台 (UWP) 應用程式

像其他 c + + 程式庫中，您可以使用 c + + AMP 的 UWP app 中。 這些文章說明如何在應用程式中包含 c + + AMP 程式碼，使用 c + +、 C#、 Visual Basic 或 JavaScript 所建立：

- [在 UWP 應用程式中使用 C++ AMP](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)

- [逐步解說：C + + 建立基本 Windows 執行階段元件，然後從 JavaScript 呼叫該](http://go.microsoft.com/fwlink/p/?linkid=249077)

- [Bing Maps Trip Optimizer、 JavaScript 和 c + + 中的 Windows 市集應用程式](http://go.microsoft.com/fwlink/p/?linkid=249078)

- [如何使用 C# 中使用 Windows 執行階段從 c + + AMP](http://go.microsoft.com/fwlink/p/?linkid=249080)

- [如何使用 c + + AMP，從 C#](http://go.microsoft.com/fwlink/p/?linkid=249081)

- [從 Managed 程式碼呼叫原生函式](../../dotnet/calling-native-functions-from-managed-code.md)

## <a name="c-amp-and-concurrency-visualizer"></a>C + + AMP 和並行視覺化檢視

並行視覺化檢視支援分析 c + + AMP 程式碼的效能。 這些文章將說明這些功能：

- [GPU 活動圖](/visualstudio/profiling/gpu-activity-graph)

- [GPU 活動 (分頁)](/visualstudio/profiling/gpu-activity-paging)

- [GPU 活動 (這個處理序)](/visualstudio/profiling/gpu-activity-this-process)

- [GPU 活動 (其他處理序)](/visualstudio/profiling/gpu-activity-other-processes)

- [通道 (執行緒檢視)](/visualstudio/profiling/channels-threads-view)

- [使用並行視覺化檢視分析 c + + AMP 程式碼](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/03/09/analyzing-c-amp-code-with-the-concurrency-visualizer/)

## <a name="performance-recommendations"></a>效能建議

模數和除法的不帶正負號的整數有效能明顯優於模數和除法的帶正負號的整數。 我們建議您使用盡可能不帶正負號的整數。

## <a name="see-also"></a>另請參閱

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Lambda 運算式語法](../../cpp/lambda-expression-syntax.md)<br/>
[參考 (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[機器碼部落格中的平行程式設計](http://go.microsoft.com/fwlink/p/?linkid=238472)
