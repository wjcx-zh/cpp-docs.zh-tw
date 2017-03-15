---
title: "平行演算法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "平行演算法 [並行執行階段]"
ms.assetid: 045dca7b-4d73-4558-a44c-383b88a28473
caps.latest.revision: 36
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 36
---
# 平行演算法
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

平行模式程式庫 (PPL) 提供同時資料集合執行工作的演算法。 這些演算法類似標準範本程式庫 (STL) 提供。  
  
 平行演算法被由並行執行階段中的現有功能。 例如， [concurrency:: parallel_for](../Topic/parallel_for%20Function.md) 演算法會使用 [structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) 物件執行的平行迴圈反覆項目。  `parallel_for` 演算法的資料分割使用可用的運算資源數目而以最佳方式。  
  
##  <a name="a-nametopa-sections"></a><a name="top"></a> 區段  
  
- [Parallel_for 演算法](#parallel_for)  
  
- [Parallel_for_each 演算法](#parallel_for_each)  
  
- [Parallel_invoke 演算法](#parallel_invoke)  
  
- [Parallel_transform 和 parallel_reduce 演算法](#parallel_transform_reduce)  
  
    - [Parallel_transform 演算法](#parallel_transform)  
  
    - [Parallel_reduce 演算法](#parallel_reduce)  
  
    - [範例︰ 執行對應和簡化以平行方式](#map_reduce_example)  
  
- [分割工作](#partitions)  
  
- [平行排序](#parallel_sorting)  
  
    - [選擇排序演算法](#choose_sort)  
  
##  <a name="a-nameparallelfora-the-parallelfor-algorithm"></a><a name="parallel_for"></a> Parallel_for 演算法  
  [Concurrency:: parallel_for](../Topic/parallel_for%20Function.md) 演算法以平行方式重複執行相同的工作。 這些工作是由反覆項目值的參數化。 這個演算法時，就不會共用資源，在該迴圈的反覆項目之間的迴圈主體。  
  
  `parallel_for` 演算法分割工作以平行執行的最佳方式。 它會使用工作竊取演算法和範圍竊取工作負載不平衡時，將這些資料分割之間取得平衡。 迴圈反覆項目會以合作方式封鎖，執行階段會轉散發反覆項目的範圍，顯示指派給其他執行緒或處理器目前的執行緒。 同樣地，當執行緒完成一系列反覆項目，執行階段會轉散發該執行緒來自其他執行緒的工作。  `parallel_for` 演算法也支援 *巢狀平行處理原則*。 當一個平行迴圈包含另一個平行迴圈時，執行階段會協調之間迴圈主體，以有效率的方式，平行執行的處理資源。  
  
  `parallel_for` 演算法都有數個多載的版本。 第一個版本會接受以開始值、 結束值，以及工作函式 （lambda 運算式、 函式物件或函式指標）。 第二個版本會開始值、 結束值、 值的步驟中，並將工作函式。 此函式的第一個版本做間距值為 1。 剩餘的版本會以 partitioner 物件，可讓您指定如何 `parallel_for` 應該分割在執行緒之間的範圍。 一節將詳細說明 partitioner [分割工作](#partitions) 本文件中。  
  
 您可以將許多轉換 `for` 迴圈，以使用 `parallel_for`。 不過， `parallel_for` 演算法不同於 `for` 陳述式如下︰  
  
-    `parallel_for` 演算法 `parallel_for` 不會以預先決定的順序執行這些工作。  
  
-    `parallel_for` 演算法不支援任意的終止條件。  `parallel_for` 演算法就會停止，當目前的反覆項目變數的值是小於 `last`。  
  
-    `_Index_type` 型別參數必須是整數類資料類型。 此整數類資料類型可以是帶正負號或不帶正負號。  
  
-   迴圈反覆項目必須是向前。  `parallel_for` 演算法就會擲回例外狀況型別 [std::invalid_argument](../../standard-library/invalid-argument-class.md) 如果 `_Step` 參數設為小於 1。  
  
-   例外狀況處理機制 `parallel_for` 演算法不同於 `for` 迴圈。 如果平行迴圈主體中同時發生多個例外狀況，執行階段會傳播給呼叫的執行緒的例外狀況的其中之一 `parallel_for`。 此外，當一個迴圈反覆運算擲回例外狀況，執行階段不會立即停止整體的迴圈。 相反地，迴圈會處於已取消的狀態和執行階段會捨棄任何尚未開始的工作。 如需例外狀況處理和平行演算法的詳細資訊，請參閱 [例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。  
  
 雖然 `parallel_for` 演算法不支援任意的終止條件，您可以使用取消來停止所有的工作。 如需取消的詳細資訊，請參閱 [取消](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation_in_the_ppl)。  
  
> [!NOTE]
>  從負載平衡和支援的功能，例如取消作業的結果可能不克服優點迴圈主體中平行執行排程的成本，尤其是迴圈主體時相當小。 您可以在平行迴圈中使用分割器來減少這項額外工作。 如需詳細資訊，請參閱 [分割工作](#partitions) 稍後在本文件中。  
  
### <a name="example"></a>範例  
 下列範例顯示的基本結構 `parallel_for` 演算法。 這個範例會列印至主控台的範圍 [1，5]，以平行方式在每個值。  
  
 [!code-cpp[concrt-parallel-for-structure#1](../../parallel/concrt/codesnippet/CPP/parallel-algorithms_1.cpp)]  
  
 這個範例會產生下列輸出的範例︰  
  
```Output  
1 2 4 3 5  
```  
  
 因為 `parallel_for` 演算法會在每個項目，以平行方式運作，值列印至主控台的順序而異。  
  
 如需完整的範例使用 `parallel_for` 演算法，請參閱 [How to︰ 撰寫 parallel_for 迴圈](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)。  
  
 [[靠上](#top)]  
  
##  <a name="a-nameparallelforeacha-the-parallelforeach-algorithm"></a><a name="parallel_for_each"></a> Parallel_for_each 演算法  
  [Concurrency:: parallel_for_each](../Topic/parallel_for_each%20Function.md) 演算法會反覆的容器，例如提供的 STL、 以平行方式執行工作。 它會使用相同的資料分割邏輯， `parallel_for` 演算法使用。  
  
  `parallel_for_each` 演算法類似 STL [std:: for_each](../Topic/for_each.md) 演算法，但 `parallel_for_each` 演算法會並行執行的工作。 像其他平行演算法， `parallel_for_each` 不會以特定順序執行這些工作。  
  
 雖然 `parallel_for_each` 演算法適用於正向迭代器和隨機存取迭代器，就會執行更隨機存取迭代器。  
  
### <a name="example"></a>範例  
 下列範例顯示的基本結構 `parallel_for_each` 演算法。 此範例會列印到主控台中的每個值 [array](../../standard-library/array-class-stl.md) 平行的物件。  
  
 [!code-cpp[concrt-parallel-for-each-structure#1](../../parallel/concrt/codesnippet/CPP/parallel-algorithms_2.cpp)]  
  
 這個範例會產生下列輸出的範例︰  
  
```Output  
4 5 1 2 3  
```  
  
 因為 `parallel_for_each` 演算法會在每個項目，以平行方式運作，值列印至主控台的順序而異。  
  
 如需完整的範例使用 `parallel_for_each` 演算法，請參閱 [How to︰ 撰寫 parallel_for_each 迴圈](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)。  
  
 [[靠上](#top)]  
  
##  <a name="a-nameparallelinvokea-the-parallelinvoke-algorithm"></a><a name="parallel_invoke"></a> Parallel_invoke 演算法  
  [Concurrency:: parallel_invoke](../Topic/parallel_invoke%20Function.md) 演算法以平行方式執行的一組工作。 它不會傳回每個工作完成為止。 當您想要同時執行數個獨立的工作，這個演算法是很有用。  
  
  `parallel_invoke` 演算法會做為其參數一系列的工作函式 （lambda 函式、 函式物件或函式指標）。  `parallel_invoke` 演算法多載之後可採取之間兩個和十個參數。 您傳遞給每個函式 `parallel_invoke` 必須接受零個參數。  
  
 像其他平行演算法， `parallel_invoke` 不會以特定順序執行這些工作。 本主題 [工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md) 說明如何 `parallel_invoke` 演算法與相關工作和工作群組。  
  
### <a name="example"></a>範例  
 下列範例顯示的基本結構 `parallel_invoke` 演算法。 這個範例會同時呼叫 `twice` 三個區域變數的函式，並列印到主控台的結果。  
  
 [!code-cpp[concrt-parallel-invoke-structure#1](../../parallel/concrt/codesnippet/CPP/parallel-algorithms_3.cpp)]  
  
 這個範例會產生下列輸出：  
  
```Output  
108 11.2 HelloHello  
```  
  
 如需使用的完整範例 `parallel_invoke` 演算法，請參閱 [如何︰ 使用 parallel_invoke 撰寫平行排序常式](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md) 和 [How to︰ 使用 parallel_invoke 執行平行作業](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)。  
  
 [[靠上](#top)]  
  
##  <a name="a-nameparalleltransformreducea-the-paralleltransform-and-parallelreduce-algorithms"></a><a name="parallel_transform_reduce"></a> Parallel_transform 和 parallel_reduce 演算法  
  [Parallel_transform](../Topic/parallel_transform%20Function.md) 和 [concurrency::parallel_reduce](../Topic/parallel_reduce%20Function.md) 的演算法為 STL 演算法的平行版本 [std::transform](../Topic/transform.md) 和 [std::accumulate](../Topic/accumulate.md), 分別。 並行執行階段版本表現 STL 版本，不同之處在於平行地執行，因為不會決定作業的順序。 當您使用一組夠大，無法取得效能與延展性優點平行處理時，請使用這些演算法。  
  
> [!IMPORTANT]
>   `parallel_transform` 和 `parallel_reduce` 演算法支援只有隨機存取、 雙向、 和正向迭代器，因為這些迭代器產生穩定的記憶體位址。 此外，這些迭代器必須產生非`const` 左值。  
  
###  <a name="a-nameparalleltransforma-the-paralleltransform-algorithm"></a><a name="parallel_transform"></a> Parallel_transform 演算法  
 您可以使用 `parallel transform` 演算法來執行許多資料平行處理作業。 例如，您可以：  
  
-   調整亮度的映像，並執行其他映像處理作業。  
  
-   加總或採取積之間兩個向量，並在向量上執行其他數字的計算。  
  
-   執行 3d 光跡追蹤，其中每個反覆項目指的是一個必須轉譯的像素。  
  
 下列範例顯示用來呼叫的基本結構 `parallel_transform` 演算法。 此範例執行否定運算標準的每個項目::[向量](../../standard-library/vector-class.md) 兩種方式的物件。 第一種方式使用 lambda 運算式。 第二種方式使用 [std::negate](../../standard-library/negate-struct.md), ，衍生自 [std::unary_function](../../standard-library/unary-function-struct.md)。  
  
 [!code-cpp[concrt-basic-parallel-transform#1](../../parallel/concrt/codesnippet/CPP/parallel-algorithms_4.cpp)]  
  
> [!WARNING]
>  這個範例示範基本的用法 `parallel_transform`。 因為工作函式不會執行大量的工作，在此範例中不應該大幅提高效能。  
  
  `parallel_transform` 演算法都有兩個多載。 第一個多載會採用一個輸入的範圍以及一元函式。 一元函式可以是 lambda 運算式採用一個引數、 函式物件或型別衍生自 `unary_function`。 第二個多載會採用兩個輸入的範圍和二元函式。 二元函式可以是 lambda 運算式採用兩個引數、 函式物件或型別衍生自 [std::binary_function](../../standard-library/binary-function-struct.md)。 下列範例會說明這些差異。  
  
 [!code-cpp[concrt-parallel-transform-vectors#2](../../parallel/concrt/codesnippet/CPP/parallel-algorithms_5.cpp)]  
  
> [!IMPORTANT]
>  您提供的輸出迭代器 `parallel_transform` 必須完全重疊輸入迭代器，或根本不重疊。 此演算法的行為是未指定，如果部分重疊的輸入和輸出迭代器。  
  
###  <a name="a-nameparallelreducea-the-parallelreduce-algorithm"></a><a name="parallel_reduce"></a> Parallel_reduce 演算法  
  `parallel_reduce` 演算法時，您必須符合關聯屬性的作業序列。 （此演算法不需要交換屬性）。以下是一些您可以使用執行的作業 `parallel_reduce`:  
  
-   將矩陣，以產生一個矩陣的序列。  
  
-   向量乘以矩陣，以產生向量的序列。  
  
-   計算序列中的字串長度。  
  
-   將清單項目，例如字串、 結合成一個項目。  
  
 下列基本範例示範如何使用 `parallel_reduce` 演算法來結合成一個字串序列的字串。 範例如同 `parallel_transform`, ，效能提升不會在這個基本範例。  
  
 [!code-cpp[concrt-basic-parallel-reduce#1](../../parallel/concrt/codesnippet/CPP/parallel-algorithms_6.cpp)]  
  
 在許多情況下，您可以將 `parallel_reduce` 簡略的使用 `parallel_for_each` 演算法搭配 [concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) 類別。  
  
###  <a name="a-namemapreduceexamplea-example-performing-map-and-reduce-in-parallel"></a><a name="map_reduce_example"></a> 範例︰ 執行對應和簡化以平行方式  
 A *對應* 作業適用於每個值序列中的函式。 A *減少* 作業會結合為一個值序列的項目。 您可以使用 Standard Template Library (STL) [std::transform](../Topic/transform.md)[std::accumulate](../Topic/accumulate.md) 類別來執行對應和縮減作業。 不過，對於許多的問題，您可以使用 `parallel_transform` 以平行方式執行 「 對應 」 作業的演算法和 `parallel_reduce` 演算法以平行方式執行縮小作業。  
  
 下列範例會比較循序和平行計算質數的數字的總和所花費的時間。 在對應階段轉換非質數值 0，並減少階段總和的值。  
  
 [!code-cpp[concrt-parallel-map-reduce-sum-of-primes#1](../../parallel/concrt/codesnippet/CPP/parallel-algorithms_7.cpp)]  
  
 如需其他範例會執行對應和減少作業以平行方式，請參閱 [How to︰ 執行對應和減少作業以平行方式](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)。  
  
 [[靠上](#top)]  
  
##  <a name="a-namepartitionsa-partitioning-work"></a><a name="partitions"></a> 分割工作  
 必要的步驟是要平行處理的資料來源上的作業， *分割* 到多個執行緒可以並行存取的多個區段的來源。 分割器指定的平行演算法分割在執行緒之間的範圍的方式。 如本文先前所述，PPL 會使用預設的資料分割建立初始的工作負載，然後使用工作竊取演算法和範圍竊取工作負載不平衡時，將這些資料分割之間取得平衡的機制。 例如，一個迴圈反覆項目完成一系列反覆項目，執行階段會轉散發該執行緒來自其他執行緒工作。 不過，某些情況下，您可能想要指定不同的資料分割機制比較適合您的問題。  
  
  `parallel_for`, ，`parallel_for_each`, ，和 `parallel_transform` 演算法提供採取額外的參數的多載的版本 `_Partitioner`。 這個參數會定義會將工時分割器類型。 以下是 PPL 會定義的 partitioner 種類︰  
  
 [concurrency::affinity_partitioner](../../parallel/concrt/reference/affinity-partitioner-class.md)  
 將測試分成工作固定數目的範圍 （通常可用來執行迴圈的背景工作執行緒的數目）。 這個分割器型別類似 `static_partitioner`, ，但工作者執行緒的對應範圍的方式藉此改善快取親和性。 此分割器類型可以改善效能，透過多次 （例如在迴圈中迴圈中） 相同的資料集執行迴圈後的資料放在快取中。 此分割器未完全參與取消。 它也不會使用合作式封鎖的語意 （semantics），並因此不能與具有正向的相依性的平行迴圈。  
  
 [concurrency::auto_partitioner](../../parallel/concrt/reference/auto-partitioner-class.md)  
 將測試分成工作範圍 （通常可用來執行迴圈的背景工作執行緒的數目） 的初始數目。 執行階段預設會使用這個型別時不會呼叫多載採用平行演算法 `_Partitioner` 參數。 每個範圍可分成子範圍，並藉此啟用負載平衡發生。 一系列工作完成時，執行階段會轉散發該執行緒的工作與其他執行緒的子範圍。 如果您的工作負載不在其中一個其他類別或您需要完整的支援取消或合作式封鎖，請使用此 partitioner。  
  
 [concurrency::simple_partitioner](../../parallel/concrt/reference/simple-partitioner-class.md)  
 將測試分成工作範圍，每個範圍都至少指定的區塊大小所指定的反覆項目數目。 這個分割器型別參與負載平衡。不過，執行階段不會將範圍分成子範圍。 針對每一個背景工作，執行階段會檢查是否有取消並執行之後進行負載平衡 `_Chunk_size` 完成反覆項目。  
  
 [concurrency::static_partitioner](../../parallel/concrt/reference/static-partitioner-class.md)  
 將測試分成工作固定數目的範圍 （通常可用來執行迴圈的背景工作執行緒的數目）。 此分割器類型可以改善效能，因為它不會使用工作竊取，因此會有較少的額外負荷。 當平行迴圈的每個反覆項目會固定和統一大量的工作，而且您不需要支援取消或轉送合作式封鎖時，請使用此分割器類型。  
  
> [!WARNING]
>   `parallel_for_each` 和 `parallel_transform` 演算法都支援使用隨機存取迭代器的容器 (例如 std::[向量](../../standard-library/vector-class.md)) 的靜態、 簡單、 和親和性的 partitioner。 使用雙向和正向迭代器的容器將會產生編譯時期錯誤。 預設 partitioner， `auto_partitioner`, ，支援所有三種迭代器類型。  
  
 一般而言，這些 partitioner 的使用方式相同，除了 `affinity_partitioner`。 大部分的 partitioner 類型不會維護狀態，並不會修改執行階段。 因此您可以建立這些 partitioner 物件呼叫位置，如下列範例所示。  
  
 [!code-cpp[concrt-static-partitioner#1](../../parallel/concrt/codesnippet/CPP/parallel-algorithms_8.cpp)]  
  
 不過，您必須傳遞 `affinity_partitioner` 物件做為非`const`, ，左值參考，以便演算法才能儲存狀態供未來重複使用的迴圈。 下列範例是以平行方式多次執行相同作業的資料集的基本應用程式。 使用 `affinity_partitioner` 可以改善效能，因為陣列可能放入快取。  
  
 [!code-cpp[concrt-affinity-partitioner#1](../../parallel/concrt/codesnippet/CPP/parallel-algorithms_9.cpp)]  
  
> [!CAUTION]
>  當您修改現有的程式碼所使用的合作式封鎖語意 （semantics） 使用時請特別小心 `static_partitioner` 或 `affinity_partitioner`。 這些分割器型別不使用負載平衡或竊取範圍，並可以改變應用程式的行為。  
  
 若要判斷是否要在任何給定的情況下使用 partitioner，最好是實驗，並測量具代表性的載入與電腦設定] 下完成作業所需的時間。 例如，靜態分割可能會有幾個核心，在多核心電腦上提供顯著的加速效果，但它可能會導致速度變慢，有相當多核心的電腦上。  
  
 [[靠上](#top)]  
  
##  <a name="a-nameparallelsortinga-parallel-sorting"></a><a name="parallel_sorting"></a> 平行排序  
 PPL 提供三種排序演算法︰ [concurrency:: parallel_sort](../Topic/parallel_sort%20Function.md), ，[concurrency:: parallel_buffered_sort](../Topic/parallel_buffered_sort%20Function.md), ，和 [concurrency:: parallel_radixsort](../Topic/parallel_radixsort%20Function.md)。 當您有可以受益於平行正在排序的資料集，這些排序演算法很有用。 特別是，以平行方式排序適合當您有大型資料集，或當您使用高度耗費比較作業來排序資料。 每種演算法來排序在位置的項目。  
  
  `parallel_sort` 和 `parallel_buffered_sort` 演算法就是這兩個比較為基礎的演算法。 也就是它們來比較項目值。  `parallel_sort` 演算法並無額外的記憶體需求，以及適用於一般用途的排序。  `parallel_buffered_sort` 演算法可以執行優於 `parallel_sort`, ，但它需要 o （n） 空間。  
  
  `parallel_radixsort` 演算法是以雜湊為基礎。 也就是說，它會使用整數索引鍵排序項目。 藉由使用索引鍵，此演算法可以直接計算而不是使用比較項目的目的地。 像 `parallel_buffered_sort`, ，此演算法必須 o （n） 空間。  
  
 下表摘要說明三個平行排序演算法的重要屬性。  
  
|演算法|描述|排序的機制|排序穩定性|記憶體需求|時間複雜性|迭代器存取|  
|---------------|-----------------|-----------------------|--------------------|-------------------------|---------------------|---------------------|  
|`parallel_sort`|一般用途比較為基礎的排序。|比較為基礎 （遞增）|不穩定|無|O((N/P)log(N/P) + 2N((P-1)/P))|隨機|  
|`parallel_buffered_sort`|速度一般用途比較為基礎的 sort 需要 o （n） 空間。|比較為基礎 （遞增）|不穩定|需要額外的 o （n） 空間|O((N/P)log(N))|隨機|  
|`parallel_radixsort`|整數索引鍵為基礎的 sort 需要 o （n） 空間。|雜湊式|穩定|需要額外的 o （n） 空間|O(N/P)|隨機|  
  
 下圖更以圖形方式顯示三個平行排序演算法的重要屬性。  
  
 ![排序演算法的比較](../../parallel/concrt/media/concrt_parallel_sorting.png "concrt_parallel_sorting")  
  
 這些平行排序演算法遵循的規則的取消及例外狀況處理。 如需取消作業和並行執行階段中的例外狀況處理的詳細資訊，請參閱 [取消平行演算法](../../parallel/concrt/cancellation-in-the-ppl.md#algorithms) 和 [例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。  
  
> [!TIP]
>  這些平行排序演算法支援移動語意。 您可以定義移動指派運算子，以便更有效率地發生的交換作業。 如需有關移動語意和移動指派運算子的詳細資訊，請參閱 [右值參考宣告子︰ & （& s)](../../cpp/rvalue-reference-declarator-amp-amp.md), ，和 [移動建構函式和移動指派運算子 （c + +）](../../cpp/move-constructors-and-move-assignment-operators-cpp.md)。 如果您未提供的移動指派運算子或交換函式，排序演算法會使用複製建構函式。  
  
 下列基本範例示範如何使用 `parallel_sort` 排序 `vector` 的 `int` 值。 根據預設， `parallel_sort` 使用 [concurrency:: message](../../standard-library/less-struct.md) 來比較值。  
  
 [!code-cpp[concrt-basic-parallel-sort#1](../../parallel/concrt/codesnippet/CPP/parallel-algorithms_10.cpp)]  
  
 這個範例示範如何提供自訂比較函式。 它會使用 [std::complex::real](../Topic/complex::real.md) 方法來排序 [std::complex \< double>](../../standard-library/complex-class.md) 值依遞增順序。  
  
 [!code-cpp[concrt-basic-parallel-sort#2](../../parallel/concrt/codesnippet/CPP/parallel-algorithms_11.cpp)]  
  
 這個範例示範如何提供雜湊函式 `parallel_radixsort` 演算法。 本範例排序 3d 點。 點會根據參考點的距離為何排序。  
  
 [!code-cpp[concrt-parallel-sort-points#1](../../parallel/concrt/codesnippet/CPP/parallel-algorithms_12.cpp)]  
  
 舉例來說，此範例會使用相對較小的資料集。 您可以增加試驗大型資料集的效能改進向量的初始大小。  
  
 此範例使用 lambda 運算式做為雜湊函式。 您也可以使用其中一個內建實作的 std::[雜湊類別](../../standard-library/hash-class.md) 或定義您自己的特製化。 您也可以使用自訂的雜湊函式物件，此範例中所示︰  
  
 [!code-cpp[concrt-parallel-sort-points#2](../../parallel/concrt/codesnippet/CPP/parallel-algorithms_13.cpp)]  
  
 [!code-cpp[concrt-parallel-sort-points#3](../../parallel/concrt/codesnippet/CPP/parallel-algorithms_14.cpp)]  
  
 雜湊函式必須傳回整數型別 ([std::is_integral::value](../../standard-library/is-integral-class.md) 必須 `true`)。 此整數類資料類型必須轉換成輸入 `size_t`。  
  
###  <a name="a-namechoosesorta-choosing-a-sorting-algorithm"></a><a name="choose_sort"></a> 選擇排序演算法  
 在許多情況下， `parallel_sort` 提供速度和記憶體的效能的最佳平衡。 不過，當您放大您的資料集、 可用的處理器數目或您的比較函式的複雜性 `parallel_buffered_sort` 或 `parallel_radixsort` 更好。 決定要在任何給定的案例中使用的排序演算法的最佳方式是實驗和量值排序 [代表性電腦設定] 下的典型資料需要多久。 當您選擇排序策略時，請記住下列指導方針。  
  
-   資料集的大小。 本文件 *小* 資料集包含少於 1000 名的項目 *媒體* 10000 與 100000 項目，包含的資料集和 *大型* 資料集包含 100000 個以上的項目。  
  
-   您的比較函式或雜湊函式執行的工作量。  
  
-   可用的運算資源數量。  
  
-   資料集的特性。 例如，用於幾乎已排序的資料，但也不是完全未排序的資料，可能會執行一種演算法。  
  
-   區塊大小。 選擇性 `_Chunk_size` 引數會指定當演算法切換從平行序列的排序實作，它細分為較小的工作單位的整體排序。 例如，如果您提供 512，演算法會切換成序列實作時的工作單元包含 512 或更少的項目。 序列的實作可以改善整體效能，因為它不需要以平行方式處理資料的額外負荷。  
  
 它可能不值得排序小型的資料集，以平行方式，即使您有大量可用的運算資源，或您的比較函式或雜湊函式會執行相當大量的工作。 您可以使用 [ivector<t](../Topic/sort.md) 排序小型資料集的函式。 (`parallel_sort` 和 `parallel_buffered_sort` 呼叫 `sort` 時指定的區塊大小大於資料集; 不過， `parallel_buffered_sort` 必須配置 o （n） 空間，可能需要額外的時間，因為鎖定爭用或記憶體配置。)  
  
 如果您必須節省記憶體，或您的記憶體配置器受限於鎖定爭用的情況，使用 `parallel_sort` 來排序的中小型資料集。 `parallel_sort` 不需要額外空間;其他演算法需要 o （n） 空間。  
  
 使用 `parallel_buffered_sort` 來排序中小型資料集，然後當您的應用程式符合其他 o （n） 空間需求。 `parallel_buffered_sort` 您有大量的運算資源或昂貴的比較函式或雜湊函式時，可以是特別有用。  
  
 使用 `parallel_radixsort` 來排序大型資料集，然後當您的應用程式符合其他 o （n） 空間需求。 `parallel_radixsort` 相等比較作業時更耗費資源，或這兩種作業時耗費資源，可以是特別有用。  
  
> [!CAUTION]
>  實作良好的雜湊函式，您需要知道資料集範圍，以及如何在資料集中的每個項目轉換成對應的不帶正負號值。 因為雜湊作業處理不帶正負號的值，考慮不同的排序方法，如果無法產生不帶正負號的雜湊值。  
  
 下列範例會比較的效能 `sort`, ，`parallel_sort`, ，`parallel_buffered_sort`, ，和 `parallel_radixsort` 針對相同的大量的隨機資料。  
  
 [!code-cpp[concrt-choosing-parallel-sort#1](../../parallel/concrt/codesnippet/CPP/parallel-algorithms_15.cpp)]  
  
 在此範例中，假設是在排序期間配置 o （n） 空間可接受， `parallel_radixsort` 在此電腦設定上此資料集上執行效能最好。  
  
 [[靠上](#top)]  
  
## <a name="related-topics"></a>相關主題  
  
|標題|說明|  
|-----------|-----------------|  
|[如何︰ 撰寫 parallel_for 迴圈](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)|示範如何使用 `parallel_for` 執行矩陣相乘演算法。|  
|[如何︰ 撰寫 parallel_for_each 迴圈](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)|示範如何使用 `parallel_for_each` 演算法來計算中質數的計數 [array](../../standard-library/array-class-stl.md) 平行的物件。|  
|[如何︰ 使用 parallel_invoke 撰寫平行排序常式](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|顯示如何使用 `parallel_invoke` 演算法，以改善 bitonic 排序演算法的效能。|  
|[如何︰ 使用 parallel_invoke 執行平行作業](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|顯示如何使用 `parallel_invoke` 演算法，以改善在共用資料來源上執行多個作業的程式效能。|  
|[如何︰ 執行對應和減少平行作業](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|示範如何使用 `parallel_transform` 和 `parallel_reduce` 演算法來執行對應和縮減作業來計算檔案中單字的出現次數。|  
|[平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|說明 PPL 提供命令式程式設計模型，可提升延展性和方便使用性開發並存應用程式。|  
|[取消](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation_in_the_ppl)|說明 PPL、 如何取消平行工作，以及如何判斷工作群組已取消時取消的角色。|  
|[例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|說明的並行執行階段例外狀況處理的角色。|  
  
## <a name="reference"></a>參考資料  
 [parallel_for 函式](../Topic/parallel_for%20Function.md)  
  
 [parallel_for_each 函式](../Topic/parallel_for_each%20Function.md)  
  
 [parallel_invoke 函式](../Topic/parallel_invoke%20Function.md)  
  
 [affinity_partitioner 類別](../../parallel/concrt/reference/affinity-partitioner-class.md)  
  
 [auto_partitioner 類別](../../parallel/concrt/reference/auto-partitioner-class.md)  
  
 [simple_partitioner 類別](../../parallel/concrt/reference/simple-partitioner-class.md)  
  
 [static_partitioner 類別](../../parallel/concrt/reference/static-partitioner-class.md)  
  
 [parallel_sort 函式](../Topic/parallel_sort%20Function.md)  
  
 [parallel_buffered_sort 函式](../Topic/parallel_buffered_sort%20Function.md)  
  
 [parallel_radixsort 函式](../Topic/parallel_radixsort%20Function.md)

