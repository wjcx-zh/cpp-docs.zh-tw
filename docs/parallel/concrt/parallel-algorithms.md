---
title: 平行演算法
ms.date: 11/19/2018
helpviewer_keywords:
- parallel algorithms [Concurrency Runtime]
ms.assetid: 045dca7b-4d73-4558-a44c-383b88a28473
ms.openlocfilehash: a31787172c89e23e5eb32aa203b9f541584c0f68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363201"
---
# <a name="parallel-algorithms"></a>平行演算法

並行模式庫 (PPL) 提供同時執行數據集合工作的演演演算法。 這些演算法類似於C++標準庫提供的演演演算法。

並行演演演算法由併發運行時的現有功能組成。 例如,[併發::p阿拉雷爾]演演演算法](reference/concurrency-namespace-functions.md#parallel_for)使用[併發::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)物件來執行並行迴圈反覆運算。 給定`parallel_for`可用的計算資源數量,演演演算法分區以最佳方式工作。

## <a name="sections"></a><a name="top"></a>部分

- [parallel_for 演算法](#parallel_for)

- [parallel_for_each 演算法](#parallel_for_each)

- [parallel_invoke 演算法](#parallel_invoke)

- [parallel_transform 和 parallel_reduce 演算法](#parallel_transform_reduce)

  - [parallel_transform 演算法](#parallel_transform)

  - [parallel_reduce 演算法](#parallel_reduce)

  - [範例: 平行執行對應和簡化](#map_reduce_example)

- [分割工作](#partitions)

- [平行排序](#parallel_sorting)

  - [選擇排序演算法](#choose_sort)

## <a name="the-parallel_for-algorithm"></a><a name="parallel_for"></a>parallel_for演演演算法

[併發::p阿拉雷爾]演算法](reference/concurrency-namespace-functions.md#parallel_for)重複並行執行相同的任務。 每個任務都由反覆運算值參數化。 當您的循環正文不共用該迴圈的反覆運算之間的資源時,此演演演算法非常有用。

該`parallel_for`演演演算法以最佳方式對任務進行分區,以實現並行執行。 它使用工作竊取演演演算法和範圍竊取來平衡這些分區,當工作負載不平衡時。 當一個循環反覆運算協同阻止時,運行時將分配給當前線程的反覆運算範圍重新分配給其他線程或處理器。 同樣,當線程完成一系列反覆運算時,運行時將工作從其他線程重新分發到該線程。 該`parallel_for`演算法支援*嵌入 sock 。* 當一個並行迴圈包含另一個並行迴圈時,運行時以有效的方式協調迴圈實體之間的處理資源,以便進行並行執行。

該`parallel_for`演演演算法有多個重載版本。 第一個版本採用起始值、結束值和工作函數(lambda 運算式、函數物件或函數指標)。 第二個版本採用起始值、結束值、要步進的值和工作函數。 此函數的第一個版本使用 1 作為步驟值。 其餘版本採用分區器物件,從而使您能夠指定如何在`parallel_for`線程之間分區範圍。 本文檔中的[分區工作](#partitions)部分將更詳細地解釋分區器。

您可以轉換許多`for`循環來`parallel_for`使用 。 但是,該`parallel_for`演`for`演演算法與語句在以下方面有所不同:

- 演`parallel_for``parallel_for`演算法 不按預先確定的順序執行任務。

- 該`parallel_for`演演演算法不支援任意終止條件。 當`parallel_for`反覆運算變數的當前值小於`last`一個時,演演演算法將停止。

- 類型`_Index_type`參數必須是積分類型。 此積分類型可以簽名或無符號。

- 循環反覆運算必須向前。 如果`parallel_for`參數小於`_Step`1, 則演演演算法將引發類型[std::invalid_argument](../../standard-library/invalid-argument-class.md)的異常。

- 演算法`parallel_for`的異常處理機制不同`for`於循環的機制。 如果並行迴圈正文中同時出現多個異常,則運行時僅將其中一個異常傳播到調用`parallel_for`的線程。 此外,當一個迴圈反覆運算引發異常時,運行時不會立即停止整個迴圈。 相反,循環處於已取消的狀態,運行時將丟棄尚未啟動的任何任務。 有關異常處理和並行演演算法的詳細資訊,請參閱[錯誤](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。

儘管該`parallel_for`演演演算法不支援任意終止條件,但您可以使用取消來停止所有任務。 有關取消的詳細資訊,請參閱[PPL 中的取消](cancellation-in-the-ppl.md)。

> [!NOTE]
> 負載平衡和支援功能(如取消)導致的計劃成本可能無法克服並行執行迴圈正文的好處,尤其是在迴圈正文相對較小時。 您可以通過在並行迴圈中使用分區器來最小化此開銷。 有關詳細資訊,請參閱本文件後面的[分割區工作](#partitions)。

### <a name="example"></a>範例

下面的示例顯示了`parallel_for`演演算法的基本結構。 本示例並行將範圍 [1, 5] 中的每個值列印到主控台。

[!code-cpp[concrt-parallel-for-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_1.cpp)]

此範例產生以下範例輸出:

```Output
1 2 4 3 5
```

由於`parallel_for`演演演算法並行作用於每個專案,因此將值列印到主控台的順序將有所不同。

有關使用`parallel_for`該演算法的完整範例,請參閱[如何:編寫parallel_for迴圈](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)。

【[頂端](#top)

## <a name="the-parallel_for_each-algorithm"></a><a name="parallel_for_each"></a>parallel_for_each演演演算法

[併發::parallel_for_每個](reference/concurrency-namespace-functions.md#parallel_for_each)演算法並行執行反覆運算容器上的任務,如C++標準庫提供的任務。 它使用演算法使用的相同分割區`parallel_for`邏輯 。

該`parallel_for_each`演算法類似於C++標準庫[std:for_each](../../standard-library/algorithm-functions.md#for_each)演演演算法,只是`parallel_for_each`該演演演算法同時執行任務。 與其他並行演演算法`parallel_for_each`一樣 ,不按特定順序執行任務。

儘管該`parallel_for_each`演算法適用於正向反覆運算器和隨機存取反覆運算器,但它在隨機存取反覆運算器方面性能更好。

### <a name="example"></a>範例

下面的示例顯示了`parallel_for_each`演演算法的基本結構。 本示例並行將[std::array](../../standard-library/array-class-stl.md)物件中的每個值列印到主控台。

[!code-cpp[concrt-parallel-for-each-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_2.cpp)]

此範例產生以下範例輸出:

```Output
4 5 1 2 3
```

由於`parallel_for_each`演演演算法並行作用於每個專案,因此將值列印到主控台的順序將有所不同。

有關使用`parallel_for_each`該演算法的完整範例,請參閱[如何:編寫parallel_for_each迴圈](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)。

【[頂端](#top)

## <a name="the-parallel_invoke-algorithm"></a><a name="parallel_invoke"></a>parallel_invoke演演算法

[併發::p阿拉勒_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)演演算法並行執行一組任務。 直到每個任務完成,它才會返回。 當您有多個要同時執行的獨立任務時,此演演演算法非常有用。

該`parallel_invoke`演演演算法以一系列工作函數(lambda 函數、函數物件或函數指標)作為其參數。 該`parallel_invoke`演演演算法重載為 2 到 10 個參數。 傳遞給的每個函數`parallel_invoke`都必須採用零參數。

與其他並行演演算法`parallel_invoke`一樣 ,不按特定順序執行任務。 主題[任務並行性解釋](../../parallel/concrt/task-parallelism-concurrency-runtime.md)了`parallel_invoke`演演算法與任務和任務組的關係。

### <a name="example"></a>範例

下面的示例顯示了`parallel_invoke`演演算法的基本結構。 此示例同時調用三個`twice`局部變數上的函數,並將結果列印到主控台。

[!code-cpp[concrt-parallel-invoke-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_3.cpp)]

這個範例會產生下列輸出：

```Output
108 11.2 HelloHello
```

有關使用`parallel_invoke`該演算法的完整範例,請參閱[「如何:使用parallel_invoke編寫並行排序例」](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)以及如何[:使用parallel_invoke執行並行操作](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)。

【[頂端](#top)

## <a name="the-parallel_transform-and-parallel_reduce-algorithms"></a><a name="parallel_transform_reduce"></a>parallel_transform和parallel_reduce演演算法

[併發::p阿拉利爾]變換](reference/concurrency-namespace-functions.md#parallel_transform)[和併發::p阿拉勒-減少](reference/concurrency-namespace-functions.md#parallel_reduce)演演演算法是C++標準庫演演演算法的並行版本,分別[:轉換](../../standard-library/algorithm-functions.md#transform)和[std::累積](../../standard-library/numeric-functions.md#accumulate)。 併發運行時版本與C++標準庫版本類似,只不過操作順序由於並行執行而未確定。 使用足夠大的集,以便並行處理,獲得性能和可擴充性優勢,請使用這些演演演算法。

> [!IMPORTANT]
> `parallel_transform`和`parallel_reduce`演演演算法僅支援隨機存取、雙向和轉發反覆運算器,因為這些反覆運算器生成穩定的記憶體位址。 此外,這些反覆運算器必須生成非`const`l值。

### <a name="the-parallel_transform-algorithm"></a><a name="parallel_transform"></a>parallel_transform演演算法

您可以使用該`parallel transform`演算法執行許多資料並行化操作。 例如，您可以：

- 調整圖像的亮度,並執行其他圖像處理操作。

- 在兩個向量之間求和或取點積,對向量執行其他數值計算。

- 執行三維光線跟蹤,其中每次反覆運算引用必須渲染的一個圖元。

下面的範例顯示了用於調用`parallel_transform`演演算法的基本結構。 此示例以兩種方式否定:[向量](../../standard-library/vector-class.md)物件的每個元素。 第一種方式使用 lambda 運算式。 第二種方式使用[std::否定](../../standard-library/negate-struct.md),它派生自[std:::unary_function](../../standard-library/unary-function-struct.md)。

[!code-cpp[concrt-basic-parallel-transform#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_4.cpp)]

> [!WARNING]
> 此示例演示了的基本`parallel_transform`用途。 由於工作函數不執行大量工作,因此在此示例中不會顯著提高性能。

該`parallel_transform`演演演算法有兩個重載。 第一個重載需要一個輸入範圍和一個一元函數。 一元函數可以是 lambda 運算式,它採用一個參數、一個函數物件或派`unary_function`生自的類型。 第二個重載需要兩個輸入範圍和一個二進制函數。 二進位函數可以是一個 lambda 運算式,它採用兩個參數,一個函數物件,或者從[std:::binary_function](../../standard-library/binary-function-struct.md)派生的類型。 下面的示例說明了這些差異。

[!code-cpp[concrt-parallel-transform-vectors#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_5.cpp)]

> [!IMPORTANT]
> 輸出的反覆運算器`parallel_transform`必須完全重疊輸入反覆運算器或根本不重疊。 如果輸入和輸出反覆運算器部分重疊,則未指定此演算法的行為。

### <a name="the-parallel_reduce-algorithm"></a><a name="parallel_reduce"></a>parallel_reduce演演算法

當您`parallel_reduce`具有滿足關聯屬性的操作序列時,該演演演算法非常有用。 (此演演演算法不需要交換屬性。下面是可以使用 執行的一些`parallel_reduce`操作 :

- 乘以矩陣序列以生成矩陣。

- 將向量乘以矩陣序列以生成向量。

- 計算字串序列的長度。

- 將元素清單(如字串)合併到一個元素中。

以下基本範例展示如何使用`parallel_reduce`該演演演算法將字串序列合併到一個字串中。 與 示例`parallel_transform`一 樣,在本基本示例中,性能提升是不需要的。

[!code-cpp[concrt-basic-parallel-reduce#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_6.cpp)]

在許多情況下,您可以將`parallel_reduce`演演演算法與[併發::可組合](../../parallel/concrt/reference/combinable-class.md)類`parallel_for_each`一起使用作為速 記。

### <a name="example-performing-map-and-reduce-in-parallel"></a><a name="map_reduce_example"></a>範例:並行執行映射和減少

*映射*操作將函數應用於序列中的每個值。 *減少*操作將序列的元素合併為一個值。 您可以使用C++標準庫[的std::轉換](../../standard-library/algorithm-functions.md#transform)和[std::累積](../../standard-library/numeric-functions.md#accumulate)函數來執行映射和減少操作。 但是,對於許多問題,可以使用`parallel_transform`該演演演算法並行執行`parallel_reduce`映射操作, 並且演演演演算法並行執行縮減操作。

下面的示例比較以串列和並行計算質數總和所需的時間。 地圖相將非質值轉換為 0,減少相數求和值。

[!code-cpp[concrt-parallel-map-reduce-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_7.cpp)]

有關並行執行映射和減少操作的另一個範例,請參閱[如何:在並行中執行映射和減少操作](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)。

【[頂端](#top)

## <a name="partitioning-work"></a><a name="partitions"></a>分割區工作

要並行化數據源上的操作,一個基本步驟是將源*分區*為多個部分,這些部分可以同時由多個線程訪問。 分區器指定並行演演算法應如何劃分線程之間的範圍。 如本文檔中前面所述,PPL 使用預設分區機制創建初始工作負載,然後使用工作竊取演演演算法和範圍竊取在工作負載不平衡時平衡這些分區。 例如,當一個迴圈反覆運算完成一系列反覆運算時,運行時將工作從其他線程重新分發到該線程。 但是,對於某些方案,您可能需要指定更適合您的問題的不同分區機制。

`parallel_for_each``parallel_for`與`parallel_transform`演算法提供重載版本,這些版本採用`_Partitioner`其他參數 。 此參數定義劃分工作的分區器類型。 以下是 PPL 定義的分割區器類型:

[併發::affinity_partitioner](../../parallel/concrt/reference/affinity-partitioner-class.md)<br/>
將工作劃分為固定數量的範圍(通常是可用於在迴圈上工作的輔助線程數)。 此分區程序類型類似於`static_partitioner`,但通過將其範圍映射到輔助線程的方式提高了緩存相關性。 當迴圈多次通過同一數據集執行(如迴圈中的迴圈)且數據適合緩存時,此分區程序類型可以提高性能。 此分區程式不完全參與取消。 它還不使用協作阻塞語義,因此不能與具有正向依賴關係的並行迴圈一起使用。

[併發::auto_partitioner](../../parallel/concrt/reference/auto-partitioner-class.md)<br/>
將工作劃分為初始範圍數(通常是可用於在迴圈上工作的輔助線程數)。 默認情況下,當您不調用採用`_Partitioner`參數的重載並行演演演算法時,運行時預設使用此類型。 每個範圍可以劃分為子範圍,從而實現負載平衡。 當一系列工作完成時,運行時將子工作範圍從其他線程重新分發到該線程。 如果工作負荷不屬於其他類別之一,或者需要完全支援取消或協作阻止,請使用此分區程式。

[併發:simple_partitioner](../../parallel/concrt/reference/simple-partitioner-class.md)<br/>
將工作劃分為多個範圍,以便每個範圍至少具有由給定塊大小指定的反覆運算次數。 此分區程序類型參與負載平衡;但是,運行時不會將範圍劃分為子範圍。 對於每個工作人員,運行時檢查取消,並在`_Chunk_size`反覆運算完成後執行負載平衡。

[併發::static_partitioner](../../parallel/concrt/reference/static-partitioner-class.md)<br/>
將工作劃分為固定數量的範圍(通常是可用於在迴圈上工作的輔助線程數)。 此分區程序類型可以提高性能,因為它不使用工作竊取,因此開銷較小。 當並行迴圈的每個反覆運算執行固定和統一的工作量,並且不需要支援取消或轉發協作阻塞時,使用此分區器類型。

> [!WARNING]
> 和`parallel_for_each``parallel_transform`演演演算法僅支援使用隨機存取反覆運算器(如std::[向量](../../standard-library/vector-class.md))的容器作為靜態、簡單和關聯分區器。 使用使用雙向和轉發反覆運算器的容器會產生編譯時錯誤。 預設分割區器`auto_partitioner`, 支援所有這些三種反覆運算器類型。

通常,這些分區器以相同的方式使用,但`affinity_partitioner`除外。 大多數分區程式類型不保持狀態,並且不由運行時修改。 因此,您可以在調用網站創建這些分區器物件,如以下示例所示。

[!code-cpp[concrt-static-partitioner#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_8.cpp)]

但是,必須將`affinity_partitioner`物件作為`const`非 l 值引用傳遞,以便演演演算法可以儲存狀態以供將來循環重用。 下面的範例顯示了一個基本應用程式,該應用程式對數據集並行多次執行相同的操作。 使用`affinity_partitioner`可以提高性能,因為陣列可能適合緩存。

[!code-cpp[concrt-affinity-partitioner#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_9.cpp)]

> [!CAUTION]
> 變更現有代碼時,請謹慎使用`static_partitioner`或`affinity_partitioner`。 這些分區程式類型不使用負載平衡或範圍竊取,因此可以更改應用程式的行為。

確定在任何給定方案中是否使用分區程式的最佳方法是試驗和測量在代表性負載和計算機配置下完成操作所需的時間。 例如，在只有幾個核心的多核心電腦上，靜態分割可能會帶來顯著的加速效果，但在有較多核心的電腦上，則可能拖慢速度。

【[頂端](#top)

## <a name="parallel-sorting"></a><a name="parallel_sorting"></a>平行排序

PPL 提供三種排序演演演算法:[併發::p阿拉勒排序](reference/concurrency-namespace-functions.md#parallel_sort)、[併發::p阿拉勒_緩衝排序](reference/concurrency-namespace-functions.md#parallel_buffered_sort))和[併發::p阿拉勒_radixsort。](reference/concurrency-namespace-functions.md#parallel_radixsort) 當您有一個可以受益於並行排序的數據集時,這些排序演演演算法非常有用。 特別是,當您擁有大型數據集或使用計算成本高昂的比較操作對數據進行排序時,並行排序非常有用。 每個演演演算法都對就位的元素進行排序。

和`parallel_sort``parallel_buffered_sort`演演演算法都是基於比較的演演演算法。 也就是說,它們按值比較元素。 該`parallel_sort`演算法沒有額外的記憶體要求,適用於通用排序。 該`parallel_buffered_sort`演演演算法的性能`parallel_sort`可以優於 ,但它需要 O(N) 空間。

該`parallel_radixsort`演演算法基於哈希。 也就是說,它使用整數鍵對元素進行排序。 通過使用鍵,此演演演算法可以直接計算元素的目標,而不是使用比較。 例如`parallel_buffered_sort`,此演演演算法需要 O(N) 空間。

下表總結了三個並行排序演演演算法的重要屬性。

|演算法|描述|排序機制|排序穩定性|記憶體需求|時間複雜性|反覆發性器存取|
|---------------|-----------------|-----------------------|--------------------|-------------------------|---------------------|---------------------|
|`parallel_sort`|基於通用的比較排序。|基於比較(升序)|不穩定|None|O((N/P)日誌(N/P)= 2N((P-1)/P))|隨機|
|`parallel_buffered_sort`|需要 O(N) 空間的基於通用比較的快速排序。|基於比較(升序)|不穩定|需要額外的 O(N) 空間|O((N/P)日誌(N)|隨機|
|`parallel_radixsort`|需要 O(N) 空間的基於整數鍵的排序。|基於哈希|穩定|需要額外的 O(N) 空間|O(不適用)|隨機|

下圖以更圖形方式顯示了三個並行排序演演演算法的重要屬性。

![排序演算法的比較](../../parallel/concrt/media/concrt_parallel_sorting.png "排序演算法的比較")

這些並行排序演演演算法遵循取消和異常處理的規則。 有關併發執行時中的取消與例外處理的詳細資訊,請參閱[取消並行演演算法](../../parallel/concrt/cancellation-in-the-ppl.md#algorithms)與[錯誤](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。

> [!TIP]
> 這些並行排序演算法支持移動語義。 您可以定義移動分配運算符,以使交換操作能夠更高效地發生。 有關移動語義和移動賦值運算符的詳細資訊,請參閱[Rvalue 參考聲明器: &&](../../cpp/rvalue-reference-declarator-amp-amp.md),以及[移動構造函數和移動賦值運算符 (C++)。](../../cpp/move-constructors-and-move-assignment-operators-cpp.md) 如果不提供移動賦值運算元或交換函數,則排序演演演算法將使用複製構造函數。

以下基本範例示範如何使用`parallel_sort``vector``int`對值進行排序。 預設情況下,`parallel_sort`使用[std::減去](../../standard-library/less-struct.md)來比較值。

[!code-cpp[concrt-basic-parallel-sort#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_10.cpp)]

此示例演示如何提供自定義比較函數。 它使用[std::複合::::實際](../../standard-library/complex-class.md#real)方法按升序排序[std::複式\<雙>](../../standard-library/complex-double.md)值。

[!code-cpp[concrt-basic-parallel-sort#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_11.cpp)]

此示例演示如何向`parallel_radixsort`演演算法提供哈希函數。 此示例對三維點進行排序。 點根據它們與參考點的距離進行排序。

[!code-cpp[concrt-parallel-sort-points#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_12.cpp)]

例如,此示例使用相對較小的數據集。 您可以增加向量的初始大小,以試驗對較大數據集的性能改進。

此示例使用 lambda 表示式作為哈希函數。 您還可以使用 std::[哈希類](../../standard-library/hash-class.md)的內置實現之一,或定義您自己的專門化。 您還可以使用自訂哈希函數物件,如本示例所示:

[!code-cpp[concrt-parallel-sort-points#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_13.cpp)]

[!code-cpp[concrt-parallel-sort-points#3](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_14.cpp)]

哈希函數必須返回積分類型[(std::is_integral::值](../../standard-library/is-integral-class.md)必須**為 true**)。 這個積分類型必須轉換為類型`size_t`。

### <a name="choosing-a-sorting-algorithm"></a><a name="choose_sort"></a>選擇排序演算法

在許多情況下,`parallel_sort`提供速度和記憶體性能的最佳平衡。 但是,隨著數據集的大小、可用處理器的數量或比較函數的複雜性增加,`parallel_buffered_sort``parallel_radixsort`或者性能會更好。 確定在任何給定方案中使用哪種排序演演演算法的最佳方法是試驗和測量在代表性計算機配置下對典型數據進行排序所需的時間。 選擇排序策略時,請記住以下準則。

- 數據集的大小。 在本文中,*小型*資料集包含的元素少於 1,000 個,*中型*數據集包含 10,000 到 100,000 個元素,*大型*數據集包含超過 100,000 個元素。

- 比較函數或哈希函數執行的工作量。

- 可用計算資源的數量。

- 數據集的特徵。 例如,對於已接近排序的數據,一種演演演算法可能運行良好,但對於完全未排序的數據則表現不佳。

- 塊大小。 可選`_Chunk_size`參數指定演算法何時從並行排序實現切換到串列排序實現,因為它將整體排序細分為較小的工作單元。 例如,如果提供 512,則當工作單元包含 512 或更少的元素時,演演演算法將切換到串行實現。 串行實現可以提高整體性能,因為它消除了並行處理數據所需的開銷。

並行對小型數據集進行排序可能不值得,即使您擁有大量可用的計算資源或比較函數或哈希函數執行的工作量也相對較大。 您可以使用[std::排序](../../standard-library/algorithm-functions.md#sort)函數對小型資料集進行排序。 (`parallel_sort``parallel_buffered_sort`並`sort`指定大於資料集的塊大小時呼叫;但是`parallel_buffered_sort`, 由於鎖定爭用或記憶體分配,分配 O(N) 空間可能需要更多時間。

如果必須保存記憶體或記憶體分配器存在鎖定爭用,請使用`parallel_sort`對中等大小的數據集進行排序。 `parallel_sort`不需要額外的空間;其他演演演算法需要 O(N) 空間。

用於`parallel_buffered_sort`對中型數據集進行排序,以及應用程式何時滿足額外的 O(N) 空間要求。 `parallel_buffered_sort`當您擁有大量的計算資源或昂貴的比較函數或哈希函數時,這尤其有用。

用於`parallel_radixsort`對大型資料集進行排序,以及應用程式何時滿足額外的 O(N) 空間要求。 `parallel_radixsort`當等效比較操作更昂貴或兩個操作都開銷時,特別有用。

> [!CAUTION]
> 實現良好的哈希函數需要瞭解數據集範圍以及數據集中的每個元素如何轉換為相應的無符號值。 由於哈希操作適用於未簽名的值,因此如果無法生成未簽名哈希值,請考慮不同的排序策略。

下面的範例比較`sort`、`parallel_sort``parallel_buffered_sort`和的`parallel_radixsort`性能與同一組大型隨機數據。

[!code-cpp[concrt-choosing-parallel-sort#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_15.cpp)]

此範例中,假定在排序期間分配 O(N) 空間是可以接受`parallel_radixsort`的, 因此在此電腦上配置上對此數據集執行最佳性能。

【[頂端](#top)

## <a name="related-topics"></a>相關主題

|Title|描述|
|-----------|-----------------|
|[如何：撰寫 parallel_for 迴圈](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)|演示如何使用該`parallel_for`演算法執行矩陣乘法。|
|[如何：撰寫 parallel_for_each 迴圈](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)|演示如何使用`parallel_for_each`該演演演算法並行計算[std::array](../../standard-library/array-class-stl.md)物件中的質數計數。|
|[如何：使用 parallel_invoke 撰寫平行排序常式](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|顯示如何使用 `parallel_invoke` 演算法，以改善 bitonic 排序演算法的效能。|
|[操作操作操作:使用parallel_invoke執行並行操作](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|顯示如何使用 `parallel_invoke` 演算法，以改善在共用資料來源上執行多個作業的程式效能。|
|[如何：平行執行對應和縮減作業](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|展示如何使用`parallel_transform`和`parallel_reduce`演算法執行映射並減少計算檔中單詞事件的操作。|
|[平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|描述 PPL,它提供了一個命令式程式設計模型,可促進可伸縮性和易用性,用於開發併發應用程式。|
|[PPL 中的取消](cancellation-in-the-ppl.md)|解釋取消在 PPL 中的角色、如何取消並行工作以及如何確定任務組何時取消。|
|[例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|解釋異常處理在併發運行時中的角色。|

## <a name="reference"></a>參考

[parallel_for功能](reference/concurrency-namespace-functions.md#parallel_for)

[parallel_for_each 函式](reference/concurrency-namespace-functions.md#parallel_for_each)

[parallel_invoke 函式](reference/concurrency-namespace-functions.md#parallel_invoke)

[affinity_partitioner 類別](../../parallel/concrt/reference/affinity-partitioner-class.md)

[auto_partitioner 類別](../../parallel/concrt/reference/auto-partitioner-class.md)

[simple_partitioner 類別](../../parallel/concrt/reference/simple-partitioner-class.md)

[static_partitioner 類別](../../parallel/concrt/reference/static-partitioner-class.md)

[parallel_sort 函式](reference/concurrency-namespace-functions.md#parallel_sort)

[parallel_buffered_sort功能](reference/concurrency-namespace-functions.md#parallel_buffered_sort)

[parallel_radixsort功能](reference/concurrency-namespace-functions.md#parallel_radixsort)
