---
title: C + + AMP 概觀 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, requirements
- C++ Accelerated Massive Parallelism, architecture
- C++ AMP
- C++ Accelerated Massive Parallelism, overview
- C++ Accelerated Massive Parallelism
ms.assetid: 9e593b06-6e3c-43e9-8bae-6d89efdd39fc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f8de31ab9009a84c04e594837a0c4fbf30758fea
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694624"
---
# <a name="c-amp-overview"></a>C++ AMP 概觀
C + + Accelerated Massive Parallelism (c + + AMP) 藉由運用在獨立圖形顯示卡的圖形處理單元 (GPU) 之類的資料平行硬體加速執行 c + + 程式碼。 藉由使用 c + + AMP，您可以撰寫多維度資料的演算法，因此可加快執行異質硬體上使用平行處理原則。 C++ AMP 程式設計模型包含多維陣列、索引、記憶體傳輸、並排顯示和數學函式庫。 您可以使用 c + + AMP 語言擴充功能來控制資料如何將 cpu 移到 GPU 上, 一步，這樣可以改善效能。  
  
## <a name="system-requirements"></a>系統需求  
  
- [!INCLUDE[win7](../../build/includes/win7_md.md)]、[!INCLUDE[win8](../../build/reference/includes/win8_md.md)]、[!INCLUDE[winsvr08_r2](../../parallel/amp/includes/winsvr08_r2_md.md)] 或 [!INCLUDE[winserver8](../../build/reference/includes/winserver8_md.md)]  
  
-   DirectX 11 功能層級 11.0 或更新版本的硬體  
  
-   在軟體模擬器上偵錯[!INCLUDE[win8](../../build/reference/includes/win8_md.md)]或[!INCLUDE[winserver8](../../build/reference/includes/winserver8_md.md)]需要。 如需在硬體上偵錯，您必須安裝圖形卡的驅動程式。 如需詳細資訊，請參閱[偵錯 GPU 程式碼](/visualstudio/debugger/debugging-gpu-code)。  
  
## <a name="introduction"></a>簡介  
 下列兩個範例會說明 c + + AMP 的主要元件。 假設您想要加入兩個一維陣列的對應元素。 例如，您可能想要新增`{1, 2, 3, 4, 5}`和`{6, 7, 8, 9, 10}`取得`{7, 9, 11, 13, 15}`。 不使用 c + + AMP，您可以撰寫下列程式碼，將數字相加並顯示結果。  
  
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
  
 重要的部分程式碼如下所示：  
  
-   資料： 資料包含三個陣列。 所有具有相同的陣序 （一） 和 (5) 的長度。  
  
-   反覆項目： 第一個`for`迴圈提供一個機制，逐一查看陣列中的項目。 在第一個包含您想要計算總和所執行的程式碼`for`區塊。  
  
-   Index:`idx`變數存取個別元素的陣列。  
  
 使用 c + + AMP，您就可以撰寫下列程式碼改為。  
  
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
  
-   資料： 您可使用 c + + 陣列建構三個 c + + AMP [array_view](../../parallel/amp/reference/array-view-class.md)物件。 提供四個值，以建構`array_view`物件： 資料值、 順位、 項目類型和長度`array_view`每個維度中的物件。 順位和型別會當做型別參數傳遞。 長度與資料會當做建構函式參數傳遞。 在此範例中，傳遞至建構函式的 c + + 陣列是一維的。 順位和長度會用來建構矩形的圖形中的資料`array_view`物件和資料值用來填滿此陣列。 執行階段程式庫也包含[array 類別](../../parallel/amp/reference/array-class.md)，其具有類似的介面`array_view`類別，並將在本文稍後討論。  
  
-   反覆項目： [parallel_for_each 函式 (c + + AMP)](reference/concurrency-namespace-functions-amp.md#parallel_for_each)提供一個機制，逐一查看的資料元素，或*計算網域*。 在此範例中，所指定運算網域`sum.extent`。 在 lambda 運算式中，包含您想要執行的程式碼或*核心函式*。 `restrict(amp)`表示中使用 c + + AMP 可以加速之 c + + 語言的子集。  
  
-   Index: [index 類別](../../parallel/amp/reference/index-class.md)變數`idx`，宣告一個符合的陣序的陣序規範`array_view`物件。 使用索引時，您可以存取的個別項目`array_view`物件。  
  
## <a name="shaping-and-indexing-data-index-and-extent"></a>成形及索引的資料： 索引和範圍  
 您必須定義的資料值，並宣告資料的形式，您可以執行核心程式碼。 所有資料都定義為陣列 （矩形），而且您可以定義任何的陣序 （維度數目） 的陣列。 資料可以是任何在任何維度的大小。  
  
### <a name="index-class"></a>index 類別  
 [Index 類別](../../parallel/amp/reference/index-class.md)指定的位置中`array`或`array_view`藉由從每個維度中的原點位移封裝到一個物件的物件。 當您存取陣列中的位置時，您傳遞`index`物件的索引運算子， `[]`，而不是整數索引的清單。 您可以使用，以存取每個維度中的項目[陣列:: operator （) 運算子](reference/array-class.md#operator_call)或[array_view::operator() 運算子](reference/array-view-class.md#operator_call)。  
  
 下列範例會建立指定第三個項目在一維的一維索引`array_view`物件。 索引用來列印中的第三個項目`array_view`物件。 輸出會是 3。  
  
```cpp  
int aCPP[] = {1, 2, 3, 4, 5};  
array_view<int, 1> a(5, aCPP);

index<1> idx(2);

std::cout << a[idx] << "\n";    
// Output: 3  
```  
  
 下列範例會建立指定的項目二維索引位置的資料列 = 1 且資料行 = 2 在二維`array_view`物件。 中的第一個參數`index`建構函式為資料列元件，而且第二個參數是資料行的元件。 輸出為 6。  
  
```cpp  
int aCPP[] = {1, 2, 3, 4, 5, 6};  
array_view<int, 2> a(2, 3, aCPP);  
  
index<2> idx(1, 2);  
  
std::cout <<a[idx] << "\n";    
// Output: 6  
```  
  
 下列範例會建立三維的索引指定的項目，其中深度 = 0 時，資料列 = 1，且資料行 = 3 中的三維`array_view`物件。 請注意，第一個參數是深度元件、 將第二個參數是資料列的元件，而第三個參數是資料行的元件。 輸出為 8。  
  
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
 [Extent 類別](../../parallel/amp/reference/extent-class.md)的每個維度中指定的資料長度`array`或`array_view`物件。 您可以建立一個範圍，並使用它來建立`array`或`array_view`物件。 您也可以擷取現有範圍`array`或`array_view`物件。 下列範例會列印每個維度之範圍的長度`array_view`物件。  
  
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
  
 下列範例會建立`array_view`物件具有相同維度為上述範例中，但此範例中的物件會使用`extent`物件，而非使用中的明確參數`array_view`建構函式。  
  
```cpp  
int aCPP[] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24};  
extent<3> e(2, 3, 4);

array_view<int, 3> a(e, aCPP);

std::cout << "The number of columns is " << a.extent[2] << "\n";  
std::cout << "The number of rows is " << a.extent[1] << "\n";  
std::cout << "The depth is " << a.extent[0] << "\n";  
```  
  
## <a name="moving-data-to-the-accelerator-array-and-arrayview"></a>將資料移至快速鍵： array_view 和陣列  
 執行階段程式庫中定義用來將資料移至快速鍵的兩個資料容器。 它們是[array 類別](../../parallel/amp/reference/array-class.md)和[array_view 類別](../../parallel/amp/reference/array-view-class.md)。 `array`類別是容器類別物件建構時所建立之資料的深層複本。 `array_view`類別是核心函式來存取資料時，會將資料複製的包裝函式類別。 時，來源裝置上所需的資料的資料複製回。  
  
### <a name="array-class"></a>array 類別  
 當`array`建構物件，如果您使用建構函式，其中包含指向資料集的加速器上建立資料的深層複本。 核心函式會修改上對應的複本。 核心函式執行完成時，您必須將資料複製回來源資料結構。 下列範例會乘以 10 向量中的每個項目。 核心功能完成之後，`vector conversion operator`用來將資料複製回向量物件。  
  
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
 `array_view`有幾乎相同的成員`array`類別，但基礎行為不相同。 資料傳遞至`array_view`建構函式不會複寫 gpu 和`array`建構函式。 相反地，將資料複製到快速鍵，核心函式執行時。 因此，如果您建立兩個`array_view`物件使用相同的資料，同時`array_view`物件參考相同的記憶體空間。 當您這樣做時，您必須同步處理的任何多執行緒的存取。 使用的主要優點`array_view`類別是需要時，才會移動資料。  
  
### <a name="comparison-of-array-and-arrayview"></a>陣列和 array_view 的比較  
 下表摘要說明相似之處並之間的差異`array`和`array_view`類別。  
  
|描述|array 類別|array_view 類別|  
|-----------------|-----------------|-----------------------|  
|次序是由決定|在編譯時間。|在編譯時間。|  
|範圍是由決定|在執行階段。|在執行階段。|  
|圖形|矩形。|矩形。|  
|資料存放區|是資料容器。|是資料包裝函數。|  
|複製|在定義的明確和深層複本。|隱含核心函式存取時的複本。|  
|擷取資料|將陣列資料複製回到 CPU 執行緒上的物件。|直接存取的`array_view`物件，或藉由呼叫[array_view:: synchronize 方法](reference/array-view-class.md#synchronize)可以繼續存取原始的容器上的資料。|  
  
### <a name="shared-memory-with-array-and-arrayview"></a>Array_view 與陣列的共用的記憶體  
 共用的記憶體是可以存取的 CPU 和快速鍵。 使用共用記憶體排除，或會大幅降低 CPU 與對應鍵之間複製資料的額外負荷。 雖然共用記憶體時，不能存取同時 CPU 和快速鍵，而且這樣做會導致未定義的行為。  
  
 `array` 物件可以用來指定共用記憶體的使用更細微的控制，如果相關聯的快速鍵支援它。 快速鍵是否支援共用的記憶體由 accelerator [supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory)屬性，它會傳回`true`支援共用的記憶體時。 支援共用的記憶體，則為預設[access_type 列舉](reference/concurrency-namespace-enums-amp.md#access_type)記憶體加速器上的配置由`default_cpu_access_type`屬性。 根據預設，`array`和`array_view`物件需要在同一個`access_type`為相關聯的主要`accelerator`。  
  
 藉由設定[array:: cpu_access_type 資料成員](reference/array-class.md#cpu_access_type)屬性`array`明確，您可以更細緻的練習控制透過如何共用記憶體的使用，讓您可以最佳化的硬體效能的應用程式特性，根據其計算核心的記憶體存取模式。 `array_view`反映相同`cpu_access_type`為`array`與其相關聯或 array_view 建構不具資料來源，其`access_type`會反映第一次會使配置存放集區的環境。 亦即，如果主機 (CPU) 的第一次存取它，然後它會假設它所建立的 CPU 資料來源與共用`access_type`的`accelerator_view`擷取相關聯; 不過，如果是第一次存取`accelerator_view`，則它的行為會如同建立容錯移轉`array`上，建立`accelerator_view`並共用`array`的`access_type`。  
  
 下列程式碼範例示範如何判斷是否預設加速器支援共用的記憶體，並接著會建立具有不同 cpu_access_type 組態的數個陣列。  
  
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
  
## <a name="executing-code-over-data-parallelforeach"></a>資料上執行的程式碼： parallel_for_each  
 [Parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each)函式定義您想要在對中的資料加速器上執行的程式碼`array`或`array_view`物件。 請考慮本主題簡介中的下列程式碼。  
  
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
  
 *計算網域*是`extent`物件或`tiled_extent`物件，定義要建立平行執行的執行緒集。 此計算網域中的每個項目會產生一個執行緒。 在此情況下，`extent`是一維物件，而且具有五個項目。 因此，五個執行緒已啟動。  
  
 *Lambda 運算式*定義每個執行緒上執行的程式碼。 Capture 子句， `[=]`，指定 lambda 運算式主體不存取所有擷取的變數值，在此情況下是由`a`， `b`，和`sum`。 在此範例中，參數清單會建立一維`index`名為變數`idx`。 值`idx[0]`為 0 中的第一個執行緒，而增加一個在每個後續的執行緒。 `restrict(amp)`表示中使用 c + + AMP 可以加速之 c + + 語言的子集。  具有限制修飾詞的函式的限制詳述於[限制 (c + + AMP)](../../cpp/restrict-cpp-amp.md)。 如需詳細資訊，請參閱， [Lambda 運算式語法](../../cpp/lambda-expression-syntax.md)。  
  
 Lambda 運算式可以包含要執行的程式碼，或它可以呼叫個別的核心函式。 核心函式必須包含`restrict(amp)`修飾詞。 下列範例是相當於上述範例中，但它會呼叫不同的核心函式。  
  
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
  
## <a name="accelerating-code-tiles-and-barriers"></a>加速程式碼： 磚和障礙  

 您可以利用其他加速並排顯示。 並排顯示執行緒分成相等矩形的子集或*磚*。 您決定您的資料集以及您在撰寫程式碼的演算法為根據適當的並排顯示大小。 您可以在每個執行緒存取*全域*相對於整體資料元素的位置`array`或`array_view`存取和*本機*相對於方塊的位置。 使用本機的索引值可簡化您的程式碼，因為您不需要撰寫程式碼轉譯為本機的索引值從全域。 若要使用並排顯示，請呼叫[extent:: tile 方法](reference/extent-class.md#tile)計算網域中上`parallel_for_each`方法，並使用[tiled_index](../../parallel/amp/reference/tiled-index-class.md) lambda 運算式中的物件。  
  
 在一般的應用程式，在磚中的項目彼此相關以某種方式，而且的程式碼存取，並持續追蹤跨圖格的值。 使用[tile_static 關鍵字](../../cpp/tile-static-keyword.md)關鍵字和[tile_barrier:: wait 方法](reference/tile-barrier-class.md#wait)完成這項作業。 變數，其中包含`tile_static`關鍵字跨越整個磚中，具有的範圍，而且每個圖格建立變數的執行個體。 您必須處理同步處理圖格執行緒變數的存取權。 [Tile_barrier:: wait 方法](reference/tile-barrier-class.md#wait)停止目前執行緒的執行，直到在磚中的所有執行緒已都達到呼叫`tile_barrier::wait`。 所以您也可以使用跨磚累積值`tile_static`變數。 然後您可以完成任何需要存取的所有值的計算。  

  
 下圖代表取樣排列磚中的資料的二維陣列。  
  
 ![索引中並排顯示的範圍值](../../parallel/amp/media/camptiledgridexample.png "camptiledgridexample")  
  
 下列程式碼範例會使用上圖中的取樣資料。 程式碼取代磚中值的平均每個磚中的值。  
  
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
 C + + AMP 包含兩個數學程式庫。 中的雙精確度程式庫[concurrency:: precise_math 命名空間](../../parallel/amp/reference/concurrency-precise-math-namespace.md)提供支援的雙精確度函式。 它也提供支援單精確度函式，雖然雙精度支援的硬體上仍需要。 它符合[C99 規格 (ISO/IEC 9899)](http://go.microsoft.com/fwlink/p/?linkid=225887)。 加速器必須支援完整的雙精確度。 您可以判斷它是否會檢查的值[accelerator:: supports_double_precision 資料成員](reference/accelerator-class.md#supports_double_precision)。 快速數學程式庫，請在[concurrency:: fast_math 命名空間](../../parallel/amp/reference/concurrency-fast-math-namespace.md)，包含另一組的數學函式。 這些函式僅支援`float`運算元，更快速地執行，但不精確的雙精確度數學程式庫中。 函式都包含在\<amp_math.h > 標頭檔和所有的宣告與`restrict(amp)`。 中的函式\<h > 標頭檔匯入同時`fast_math`和`precise_math`命名空間。 `restrict`關鍵字用來區別\<cmath > 版本和 c + + AMP 版本。 下列程式碼會計算使用快速方法，在計算網域中每個值的基底 10 對數。  

  
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
 C + + AMP 包括圖形程式庫是設計來加速圖形程式設計。 此文件庫只適用於支援原生圖形功能的裝置。 方法會進入[concurrency:: graphics 命名空間](../../parallel/amp/reference/concurrency-graphics-namespace.md)，而且包含在\<amp_graphics.h > 標頭檔。 圖形文件庫的關鍵元件如下：  
  
- [texture 類別](../../parallel/amp/reference/texture-class.md)： 您可以使用紋理類別來建立紋理，從記憶體或檔案。 紋理類似陣列，因為其包含的資料，而且這些介面類似於 c + + 標準程式庫指派和複製建構中的容器。 如需詳細資訊，請參閱 [C++ 標準程式庫容器](../../standard-library/stl-containers.md)。 範本參數`texture`類別為項目類型和陣序規範。 順位可以是 1、 2 或 3。 項目類型可以是其中一個會在本文稍後所述的短向量類型。  
  
- [writeonly_texture_view 類別](../../parallel/amp/reference/writeonly-texture-view-class.md)： 提供任何紋理的唯寫存取。  
  
- [短向量庫](http://msdn.microsoft.com/en-us/4c4f5bed-c396-493b-a238-c347563f645f)： 定義一組的長度為 2、 3 和 4 為基礎的短向量類型`int`， `uint`， `float`， `double`， [norm](../../parallel/amp/reference/norm-class.md)，或[unorm](../../parallel/amp/reference/unorm-class.md).  
  
## <a name="universal-windows-platform-uwp-apps"></a>通用 Windows 平台 (UWP) 應用程式  
 類似其他 c + + 程式庫中，您可以使用 c + + AMP UWP 應用程式中。 這些文章說明如何在應用程式包含 c + + AMP 程式碼所建立的 c + +、 C#、 Visual Basic 或 JavaScript 使用：  
  
- [在 UWP 應用程式中使用 C++ AMP](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)  
  
- [逐步解說： 以 c + + 建立基本 Windows 執行階段元件，然後從 JavaScript 呼叫該](http://go.microsoft.com/fwlink/p/?linkid=249077)  
  
- [Bing 地圖服務路線最佳化程式的 JavaScript 和 c + + 中的 Windows 市集應用程式](http://go.microsoft.com/fwlink/p/?linkid=249078)  
  
- [如何使用 c + + AMP 從 C# 使用 Windows 執行階段](http://go.microsoft.com/fwlink/p/?linkid=249080)  
  
- [如何使用 c + + AMP 從 C#](http://go.microsoft.com/fwlink/p/?linkid=249081)  
  
- [從 Managed 程式碼呼叫原生函式](../../dotnet/calling-native-functions-from-managed-code.md)  
  
## <a name="c-amp-and-concurrency-visualizer"></a>C + + AMP 和並行視覺化檢視  
 並行視覺化檢視包含支援分析 c + + AMP 程式碼的效能。 這些文件說明這些功能：  
  
- [GPU 活動圖](/visualstudio/profiling/gpu-activity-graph)  
  
- [GPU 活動 (分頁)](/visualstudio/profiling/gpu-activity-paging)  
  
- [GPU 活動 (這個處理序)](/visualstudio/profiling/gpu-activity-this-process)  
  
- [GPU 活動 (其他處理序)](/visualstudio/profiling/gpu-activity-other-processes)  
  
- [通道 (執行緒檢視)](/visualstudio/profiling/channels-threads-view)  
  
- [分析 c + + AMP 程式碼，使用 並行視覺化檢視](http://go.microsoft.com/fwlink/p/?linkid=253987&clcid=0x409)  
  
## <a name="performance-recommendations"></a>效能建議  
 模數和不帶正負號整數的除法有效能明顯優於模數和帶正負號整數的除法。 我們建議您使用盡可能不帶正負號的整數。  
  
## <a name="see-also"></a>另請參閱  
 [C + + AMP (c + + Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [Lambda 運算式語法](../../cpp/lambda-expression-syntax.md)   
 [參考 (c + + AMP)](../../parallel/amp/reference/reference-cpp-amp.md)   
 [機器碼部落格中的平行程式設計](http://go.microsoft.com/fwlink/p/?linkid=238472)
