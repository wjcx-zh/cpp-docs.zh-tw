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
ms.openlocfilehash: 2629f243f3db3b8fabbd87ee0a211380ac3d45a2
ms.sourcegitcommit: 093f49b8b69daf86661adc125b1d2d7b1f0e0650
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2020
ms.locfileid: "89427721"
---
# <a name="c-amp-overview"></a>C++ AMP 概觀

C++ Accelerated Massive Parallelism (C++ AMP) 利用資料平行的硬體（例如圖形處理單元）來加速 c + + 程式碼的執行，而不需要在離散的圖形配接器上使用 GPU (。 藉由使用 C++ AMP，您可以撰寫多維度資料演算法的程式碼，讓您可以在異類硬體上使用平行處理來加速執行。 C++ AMP 程式設計模型包含多維陣列、索引、記憶體傳輸、並排顯示和數學函式庫。 您可以使用 C++ AMP 語言延伸模組，來控制如何將資料從 CPU 移回 GPU 並返回，以便您可以改善效能。

## <a name="system-requirements"></a>系統需求

- Windows 7 或更新版本

- Windows Server 2008 R2 或更新版本

- DirectX 11 功能等級11.0 或更新版本的硬體

- 若要在軟體模擬器上進行偵錯工具，則需要 Windows 8 或 Windows Server 2012。 如需在硬體上偵錯，您必須安裝圖形卡的驅動程式。 如需詳細資訊，請參閱將 [GPU 程式碼進行調試](/visualstudio/debugger/debugging-gpu-code)程式。

- 注意： ARM64 目前不支援 AMP。

## <a name="introduction"></a>簡介

下列兩個範例說明 C++ AMP 的主要元件。 假設您想要加入 2 1 維度陣列的對應元素。 例如，您可能想要加入 `{1, 2, 3, 4, 5}` 並 `{6, 7, 8, 9, 10}` 取得 `{7, 9, 11, 13, 15}` 。 若未使用 C++ AMP，您可以撰寫下列程式碼來加入數位並顯示結果。

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

程式碼的重要部分如下：

- 資料：資料包含三個數組。 全都具有相同的等級 (一個) 且長度 (五個) 。

- 反復專案：第一個 **`for`** 迴圈會提供一種機制，以逐一查看陣列中的元素。 您要用來計算總和的程式碼會包含在第一個區塊中 **`for`** 。

- Index： `idx` 變數會存取陣列的個別元素。

使用 C++ AMP，您可能會改為撰寫下列程式碼。

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

存在相同的基本元素，但使用 C++ AMP 的結構：

- 資料：您可以使用 c + + 陣列來建立三個 C++ AMP [array_view](../../parallel/amp/reference/array-view-class.md) 物件。 您可以提供四個值來建立 `array_view` 物件：資料值、排名、元素類型，以及 `array_view` 每個維度中物件的長度。 Rank 和 type 會以型別參數傳遞。 資料和長度會以函式參數的形式傳遞。 在此範例中，傳遞至函式的 c + + 陣列是一維的。 順位和長度用來在物件中建立資料的矩形圖形 `array_view` ，而且資料值會用來填滿陣列。 執行時間程式庫也包含 [陣列類別](../../parallel/amp/reference/array-class.md)，其介面類別似于 `array_view` 類別，稍後將在本文中討論。

- 反復專案： [parallel_for_each 函式 (C++ AMP) ](reference/concurrency-namespace-functions-amp.md#parallel_for_each) 提供逐一查看資料元素或 *計算網域*的機制。 在此範例中，計算網域是由指定 `sum.extent` 。 您要執行的程式碼包含在 lambda 運算式或 *核心函數*中。 `restrict(amp)`表示只使用 C++ AMP 可以加速的 c + + 語言子集。

- Index： [索引類別](../../parallel/amp/reference/index-class.md) 變數（）是以一陣序來宣告， `idx` 以符合物件的順位 `array_view` 。 您可以使用索引來存取物件的個別元素 `array_view` 。

## <a name="shaping-and-indexing-data-index-and-extent"></a>塑造和編制索引資料：索引和範圍

您必須定義資料值，並宣告資料的形狀，才能執行核心程式代碼。 所有資料都會定義為數組 (矩形) ，而且您可以定義陣列，以) 的維度數目 (數目。 資料可以是任何維度中的任何大小。

### <a name="index-class"></a>index 類別

[Index 類別](../../parallel/amp/reference/index-class.md)會將 `array` `array_view` 每個維度中來源的位移封裝成一個物件，藉此指定或物件中的位置。 當您存取陣列中的位置時，會將 `index` 物件傳遞至索引運算子， `[]` 而不是整數索引的清單。 您可以使用 [array：： operator ( # A1 運算子](reference/array-class.md#operator_call) 或 [array_view：： Operator ( # A3 運算子](reference/array-view-class.md#operator_call)，來存取每個維度中的元素。

下列範例會建立一維索引，以指定一維物件中的第三個元素 `array_view` 。 索引是用來列印物件中的第三個元素 `array_view` 。 輸出為3。

```cpp
int aCPP[] = {1, 2, 3, 4, 5};
array_view<int, 1> a(5, aCPP);

index<1> idx(2);

std::cout << a[idx] << "\n";
// Output: 3
```

下列範例會建立二維索引，以指定在二維物件中資料列 = 1 和資料行 = 2 的元素 `array_view` 。 函式中的第一個參數 `index` 是資料列元件，而第二個參數是資料行元件。 輸出為6。

```cpp
int aCPP[] = {1, 2, 3, 4, 5, 6};
array_view<int, 2> a(2, 3, aCPP);

index<2> idx(1, 2);

std::cout <<a[idx] << "\n";
// Output: 6
```

下列範例會建立三維索引，以指定在三維物件中，depth = 0、row = 1 和 column = 3 的元素 `array_view` 。 請注意，第一個參數是深度元件，第二個參數是資料列元件，而第三個參數是資料行元件。 輸出為8。

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

[範圍類別](../../parallel/amp/reference/extent-class.md)會指定或物件之每個維度中的資料長度 `array` `array_view` 。 您可以建立範圍，並用它來建立 `array` 或 `array_view` 物件。 您也可以取出現有或物件的範圍 `array` `array_view` 。 下列範例會列印物件的每個維度中的範圍長度 `array_view` 。

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

下列範例會建立一個 `array_view` 物件，該物件與上一個範例中的物件具有相同的維度，但這個範例會使用 `extent` 物件，而不是使用函式中的明確參數 `array_view` 。

```cpp
int aCPP[] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24};
extent<3> e(2, 3, 4);

array_view<int, 3> a(e, aCPP);

std::cout << "The number of columns is " << a.extent[2] << "\n";
std::cout << "The number of rows is " << a.extent[1] << "\n";
std::cout << "The depth is " << a.extent[0] << "\n";
```

## <a name="moving-data-to-the-accelerator-array-and-array_view"></a>將資料移至加速器：陣列和 array_view

用來將資料移至加速器的兩個數據容器會定義在執行時間程式庫中。 它們是 [陣列類別](../../parallel/amp/reference/array-class.md) 和 [array_view 類別](../../parallel/amp/reference/array-view-class.md)。 `array`類別是一個容器類別，可在建立物件時，建立資料的深層複本。 `array_view`類別是一種包裝函式類別，可在核心函數存取資料時複製資料。 當來源裝置需要資料時，就會將資料複製回來。

### <a name="array-class"></a>array 類別

當 `array` 建立物件時，如果您使用包含資料集指標的函式，就會在加速器上建立資料的深層複製。 核心函數會修改加速器上的複本。 當核心函數的執行完成時，您必須將資料複製回源資料結構。 下列範例會將向量中的每個元素乘以10。 核心函數完成之後， `vector conversion operator` 會使用將資料複製回 vector 物件。

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

### <a name="array_view-class"></a>array_view 類別

`array_view`具有與類別幾乎相同的成員 `array` ，但基礎行為不同。 傳遞至函式的資料 `array_view` 不會在 GPU 上複寫，因為它是使用函式 `array` 。 相反地，在執行核心函數時，資料會複製到加速器。 因此，如果您建立兩個 `array_view` 使用相同資料的物件，則這兩個 `array_view` 物件都會參考相同的記憶體空間。 當您這樣做時，您必須同步處理任何多執行緒存取。 使用類別的主要優點 `array_view` 是只在必要時才移動資料。

### <a name="comparison-of-array-and-array_view"></a>陣列和 array_view 的比較

下表摘要說明和類別之間的相似性和 `array` 差異 `array_view` 。

|說明|array 類別|array_view 類別|
|-----------------|-----------------|-----------------------|
|當排名決定時|在編譯時期。|在編譯時期。|
|判斷範圍時|在執行時間。|在執行時間。|
|形狀|矩形。|矩形。|
|資料儲存體|是資料容器。|是資料包裝函式。|
|複製|定義時的明確和深層複製。|當核心函數存取時的隱含複本。|
|資料抓取|藉由將陣列資料複製回 CPU 執行緒上的物件。|藉由直接存取 `array_view` 物件，或藉由呼叫 [array_view：： synchronize 方法](reference/array-view-class.md#synchronize) 來繼續存取原始容器上的資料。|

### <a name="shared-memory-with-array-and-array_view"></a>具有陣列和 array_view 的共用記憶體

共用記憶體是 CPU 和加速器可存取的記憶體。 使用共用記憶體可消除或大幅降低在 CPU 與加速器之間複製資料的額外負荷。 雖然記憶體是共用的，但 CPU 和加速器無法同時存取，而這樣做會造成未定義的行為。

`array` 如果相關聯的加速器支援共用記憶體，則可以使用物件來指定其使用方式的精細控制。 加速器是否支援共用記憶體是由加速器的 [supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory) 屬性所決定，而這會 **`true`** 在支援共用記憶體時傳回。 如果支援共用記憶體，則加速器上記憶體配置的預設 [Access_type 列舉](reference/concurrency-namespace-enums-amp.md#access_type) 是由屬性所決定 `default_cpu_access_type` 。 依預設， `array` 和 `array_view` 物件會採用與 `access_type` 主要相關聯的相同 `accelerator` 。

藉由明確地設定的 [array：： Cpu_access_type 資料成員](reference/array-class.md#cpu_access_type) 屬性 `array` ，您可以對共用記憶體的使用方式進行細微的控制，讓您可以根據其計算核心的記憶體存取模式，將硬體效能特性的應用程式優化。 與其 `array_view` `cpu_access_type` 相關聯的反映方式相同 `array` ; 或者，如果在不使用資料來源的情況下建立 array_view，則會 `access_type` 反映第一個導致它配置儲存體的環境。 也就是說，如果第一次是由主機 (CPU) 所存取，則它的行為就像是在 CPU 資料來源上建立的，而且會共用的 `access_type` `accelerator_view` 關聯。不過，如果是第一次存取，則 `accelerator_view` 它的行為就像是 `array` 在上建立的， `accelerator_view` 並共用的 `array` `access_type` 。

下列程式碼範例示範如何判斷預設加速器是否支援共用記憶體，然後建立數個具有不同 cpu_access_type 設定的陣列。

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

## <a name="executing-code-over-data-parallel_for_each"></a>對資料執行程式碼： parallel_for_each

[Parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each)函式會根據或物件中的資料，定義您想要在加速器上執行的程式碼 `array` `array_view` 。 請考慮本主題簡介中的下列程式碼。

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

此 `parallel_for_each` 方法會採用兩個引數，也就是計算網域和 lambda 運算式。

*計算網域*是 `extent` 物件或 `tiled_extent` 物件，可定義要為平行執行所建立的執行緒集。 計算網域中的每個元素都會產生一個執行緒。 在此情況下， `extent` 物件為一維，並有五個元素。 因此，會啟動五個執行緒。

*Lambda 運算式*會定義要在每個執行緒上執行的程式碼。 Capture 子句 `[=]` 會指定 lambda 運算式的主體會以傳值方式存取所有已捕捉的變數，在此案例中為 `a` 、 `b` 和 `sum` 。 在此範例中，參數清單會建立名為的一維 `index` 變數 `idx` 。 `idx[0]`第一個執行緒中的值為0，並在每個後續執行緒中增加一個。 `restrict(amp)`表示只使用 C++ AMP 可以加速的 c + + 語言子集。  限制修飾詞之函式的限制描述于 [限制 (C++ AMP) ](../../cpp/restrict-cpp-amp.md)。 如需詳細資訊，請參閱 [Lambda 運算式語法](../../cpp/lambda-expression-syntax.md)。

Lambda 運算式可包含要執行的程式碼，或可呼叫個別的核心函式。 核心函數必須包含修飾詞 `restrict(amp)` 。 下列範例相當於前一個範例，但它會呼叫個別的核心函式。

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

## <a name="accelerating-code-tiles-and-barriers"></a>加速程式碼：磚和阻礙

您可以使用並排圖來增加加速。 磚會將執行緒分成相等的矩形子集或 *圖*格。 您可以根據您的資料集和您要編碼的演算法來決定適當的磚大小。 您可以針對每個執行緒，存取資料元素的 *全域* 位置（相對於整個或）， `array` 並存取相對於磚的 `array_view` *本機* 位置。 使用本機索引值可簡化您的程式碼，因為您不需要撰寫程式碼來將索引值從全域轉譯為本機。 若要使用並排顯示，請在方法的計算網域上呼叫 [範圍：：磚方法](reference/extent-class.md#tile) `parallel_for_each` ，並在 lambda 運算式中使用 [tiled_index](../../parallel/amp/reference/tiled-index-class.md) 物件。

在一般應用程式中，磚中的元素會以某種方式相關聯，而且程式碼必須在磚上存取和追蹤值。 使用 [Tile_static 關鍵字](../../cpp/tile-static-keyword.md) 關鍵字和 [tile_barrier：： wait 方法](reference/tile-barrier-class.md#wait) 來完成此動作。 具有 **tile_static** 關鍵字的變數具有橫跨整個磚的範圍，且會為每個磚建立變數的實例。 您必須處理對變數進行磚執行緒存取的同步處理。 [Tile_barrier：： Wait 方法](reference/tile-barrier-class.md#wait)會停止執行目前的執行緒，直到磚中的所有線程都已到達的呼叫為止 `tile_barrier::wait` 。 因此，您可以使用 **tile_static** 變數來累積磚上的值。 然後，您可以完成任何需要存取所有值的計算。

下圖表示以圖格排列之取樣資料的二維陣列。

![並排顯示範圍中的索引值](../../parallel/amp/media/camptiledgridexample.png "並排顯示範圍中的索引值")

下列程式碼範例會使用上圖中的取樣資料。 此程式碼會將磚中的每個值取代為圖格中值的平均值。

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

C++ AMP 包含兩個數學程式庫。 [Concurrency：:p Recise_math 命名空間](../../parallel/amp/reference/concurrency-precise-math-namespace.md)中的雙精確度程式庫提供雙精確度函數的支援。 它也提供單精確度函式的支援，但仍需要雙精確度的硬體支援。 它符合 [ (ISO/IEC 9899) 的 C99 規格 ](https://go.microsoft.com/fwlink/p/?linkid=225887)。 加速器必須支援完整的雙精確度。 您可以藉由檢查 [快速鍵：： Supports_double_precision 資料成員](reference/accelerator-class.md#supports_double_precision)的值來判斷是否已完成。 [Concurrency：： Fast_math 命名空間](../../parallel/amp/reference/concurrency-fast-math-namespace.md)中的 fast math library 包含另一組數學函數。 這些函式只支援 **`float`** 運算元、執行速度更快，但不像雙精確度數學程式庫中的精確。 這些函式會包含在 \<amp_math.h> 標頭檔中，且會使用宣告 `restrict(amp)` 。 標頭檔中的函式 \<cmath> 會匯入至 `fast_math` 和 `precise_math` 命名空間。 **`restrict`** 關鍵字是用來區別 \<cmath> 版本和 C++ AMP 版本。 下列程式碼會使用計算網域中每個值的快速方法來計算以10為底數的對數。

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
            logs[idx] = concurrency::fast_math::log10(numbers[idx]);
        }
    );

    for (int i = 0; i < 6; i++) {
        std::cout << logs[i] << "\n";
    }
}
```

## <a name="graphics-library"></a>圖形程式庫

C++ AMP 包含設計用於加速圖形程式設計的圖形程式庫。 此程式庫只會在支援原生圖形功能的裝置上使用。 這些方法位於 [Concurrency：： Graphics 命名空間](../../parallel/amp/reference/concurrency-graphics-namespace.md) 中，並包含在 \<amp_graphics.h> 標頭檔中。 圖形程式庫的主要元件如下：

- [材質類別](../../parallel/amp/reference/texture-class.md)：您可以使用材質類別，從記憶體或檔案建立紋理。 紋理類似陣列，因為它們包含資料，而且類似于 c + + 標準程式庫中的容器與指派和複製結構相關。 如需詳細資訊，請參閱 [C++ 標準程式庫容器](../../standard-library/stl-containers.md)。 類別的範本參數 `texture` 是專案類型和等級。 排名可以是1、2或3。 元素類型可以是本文稍後描述的其中一個簡短向量類型。

- [Writeonly_texture_view 類別](../../parallel/amp/reference/writeonly-texture-view-class.md)：提供任何材質的僅限寫入存取權。

- 短向量程式庫：定義一組長度為2、3和4且以 **`int`** 、、 `uint` **`float`** 、 **`double`** 、 [標準](../../parallel/amp/reference/norm-class.md)或 [unorm](../../parallel/amp/reference/unorm-class.md)為基礎的短向量類型。

## <a name="universal-windows-platform-uwp-apps"></a>通用 Windows 平台 (UWP) 應用程式

如同其他 c + + 程式庫，您可以在 UWP 應用程式中使用 C++ AMP。 這些文章說明如何在使用 c + +、c #、Visual Basic 或 JavaScript 所建立的應用程式中包含 C++ AMP 程式碼：

- [在 UWP 應用程式中使用 C++ AMP](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)

- [逐步解說：在 c + + 中建立基本的 Windows 執行階段元件，然後從 JavaScript 呼叫它](https://go.microsoft.com/fwlink/p/?linkid=249077)

- [Bing 地圖服務路線優化程式，JavaScript 和 c + + 中的視窗存放區應用程式](https://go.microsoft.com/fwlink/p/?linkid=249078)

- [如何使用 Windows 執行階段從 c # 使用 C++ AMP](https://devblogs.microsoft.com/pfxteam/how-to-use-c-amp-from-c-using-winrt/)

- [如何使用 C 的 C++ AMP#](https://devblogs.microsoft.com/pfxteam/how-to-use-c-amp-from-c/)

- [從 Managed 程式碼呼叫原生函式](../../dotnet/calling-native-functions-from-managed-code.md)

## <a name="c-amp-and-concurrency-visualizer"></a>C++ AMP 和並行視覺化

並行視覺化套裝程式括支援分析 C++ AMP 程式碼的效能。 這些文章會說明這些功能：

- [GPU 活動圖](/visualstudio/profiling/gpu-activity-graph)

- [GPU 活動 (分頁)](/visualstudio/profiling/gpu-activity-paging)

- [GPU 活動 (這個處理序)](/visualstudio/profiling/gpu-activity-this-process)

- [GPU 活動 (其他處理序)](/visualstudio/profiling/gpu-activity-other-processes)

- [通道 (執行緒檢視)](/visualstudio/profiling/channels-threads-view)

- [使用平行存取視覺化程式分析 C++ AMP 程式碼](/archive/blogs/nativeconcurrency/analyzing-c-amp-code-with-the-concurrency-visualizer)

## <a name="performance-recommendations"></a>效能建議

不帶正負號整數的模數和除法比帶正負號整數的模數和除法有顯著的效能。 建議您盡可能使用不帶正負號的整數。

## <a name="see-also"></a>另請參閱

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Lambda 運算式語法](../../cpp/lambda-expression-syntax.md)<br/>
[參考 (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[原生程式碼中的平行程式設計](/archive/blogs/nativeconcurrency/)
