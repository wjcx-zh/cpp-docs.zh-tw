---
title: 平行容器和物件
ms.date: 03/27/2019
helpviewer_keywords:
- parallel objects
- parallel containers
- concurrent containers
ms.assetid: 90ab715c-29cd-48eb-8e76-528619aab466
ms.openlocfilehash: f3fb2bb57c8bcf65de0a7f74f2992050d8257429
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363051"
---
# <a name="parallel-containers-and-objects"></a>平行容器和物件

並行模式庫 (PPL) 包括幾個容器和物件,它們提供對其元素的線程安全訪問。

*併發容器*提供對最重要的操作的併發安全訪問。 此處,併發安全意味著指標或反覆運算器始終有效。 它不是元素初始化或特定遍歷順序的保證。 這些容器的功能與標準庫C++提供的功能類似。 例如,[併發::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)類類似於[std::vector](../../standard-library/vector-class.md)類,只不過`concurrent_vector`類允許您並行追加元素。 當您具有並行代碼,需要讀取和寫入對同一容器的訪問時,請使用併發容器。

*併發物件*在元件之間併發共用。 並行計算併發物件狀態的進程會產生與另一個串行計算相同狀態的進程相同的結果。 [併發::可組合](../../parallel/concrt/reference/combinable-class.md)類是併發物件類型的一個示例。 該`combinable`類允許您並行執行計算,然後將這些計算合併到最終結果中。 否則,使用同步機制(例如互斥體)來同步對共用變數或資源的訪問,請使用併發物件。

## <a name="sections"></a><a name="top"></a>部分

本主題詳細介紹了以下並行容器和物件。

併發容器:

- [concurrent_vector 類別](#vector)

  - [concurrent_vector和向量之間的差異](#vector-differences)

  - [併發安全操作](#vector-safety)

  - [異常安全](#vector-exceptions)

- [concurrent_queue 類別](#queue)

  - [concurrent_queue和佇列之間的差異](#queue-differences)

  - [併發安全操作](#queue-safety)

  - [反覆運算器支援](#queue-iterators)

- [concurrent_unordered_map 類別](#unordered_map)

  - [concurrent_unordered_map和unordered_map之間的差異](#map-differences)

  - [併發安全操作](#map-safety)

- [concurrent_unordered_multimap 類別](#unordered_multimap)

- [concurrent_unordered_set 類別](#unordered_set)

- [concurrent_unordered_multiset類](#unordered_multiset)

併發物件:

- [combinable 類別](#combinable)

  - [方法和功能](#combinable-features)

  - [範例](#combinable-examples)

## <a name="concurrent_vector-class"></a><a name="vector"></a>concurrent_vector類

[併發::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)類是一個序列容器類,它就像[std:::vector](../../standard-library/vector-class.md)類一樣,允許您隨機訪問其元素。 該`concurrent_vector`類支援併發安全追加和元素訪問操作。 追加操作不會使現有指標或反覆運算器無效。 反覆運算器訪問和遍歷操作也是併發安全的。 此處,併發安全意味著指標或反覆運算器始終有效。 它不是元素初始化或特定遍歷順序的保證。

### <a name="differences-between-concurrent_vector-and-vector"></a><a name="vector-differences"></a>concurrent_vector和向量之間的差異

該`concurrent_vector`類`vector`與 類非常相似。 `concurrent_vector`物件上的追加、元素訪問和反覆運算器存取操作的複雜性`vector`與 物件相同。 以下各點說明瞭與`concurrent_vector`的不同`vector`位置:

- 對`concurrent_vector`物件的追加、元素訪問、反覆運算器訪問和反覆運算器遍歷操作是併發安全的。

- 只能向`concurrent_vector`物件的末尾添加元素。 類別`concurrent_vector`不提供方法`insert`。

- 物件`concurrent_vector`在附加時不使用[移動語意](../../cpp/rvalue-reference-declarator-amp-amp.md)。

- 類`concurrent_vector`不提供`erase``pop_back`或 方法。 與`vector`,使用[clear](reference/concurrent-vector-class.md#clear)方法從`concurrent_vector`物件中刪除 所有元素。

- 類`concurrent_vector`不連續地存儲在記憶體中。 因此,不能以可以使用陣列`concurrent_vector`的所有方式使用類。 例如,對於名為`v``concurrent_vector`type 的變數,表達`&v[0]+2`式 生成未定義的行為。

- 類`concurrent_vector`定義[grow_by](reference/concurrent-vector-class.md#grow_by)和[grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least)方法。 這些方法類似於[調整大小](reference/concurrent-vector-class.md#resize)方法,只不過它們是併發安全的。

- 對`concurrent_vector`象 在追加或調整其大小時不會重新置放其元素。 這使得現有指標和反覆運算器能夠在併發操作期間保持有效。

- 運行時不為類型`concurrent_vector``bool`定義的專用版本。

### <a name="concurrency-safe-operations"></a><a name="vector-safety"></a>併發安全操作

追加或增加`concurrent_vector`物件大小或`concurrent_vector`訪問 物件中的元素的所有方法都是併發安全的。 此處,併發安全意味著指標或反覆運算器始終有效。 它不是元素初始化或特定遍歷順序的保證。 這個規則的例外情況是方法`resize`。

下表顯示了併發安全的常見`concurrent_vector`方法和運算符。

||||
|-|-|-|
|[在](reference/concurrent-vector-class.md#at)|[結束](reference/concurrent-vector-class.md#end)|[operator&#91;&#93;](reference/concurrent-vector-class.md#operator_at)|
|[開始](reference/concurrent-vector-class.md#begin)|[前面](reference/concurrent-vector-class.md#front)|[push_back](reference/concurrent-vector-class.md#push_back)|
|[返回](reference/concurrent-vector-class.md#back)|[grow_by](reference/concurrent-vector-class.md#grow_by)|[rbegin](reference/concurrent-vector-class.md#rbegin)|
|[能力](reference/concurrent-vector-class.md#capacity)|[grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least)|[rend](reference/concurrent-vector-class.md#rend)|
|[空](reference/concurrent-vector-class.md#empty)|[max_size](reference/concurrent-vector-class.md#max_size)|[大小](reference/concurrent-vector-class.md#size)|

例如`reserve`,運行時提供的與標準庫C++相容的操作並不併發安全。 下表顯示了非併發安全的常見方法和運算符。

|||
|-|-|
|[配置](reference/concurrent-vector-class.md#assign)|[儲備](reference/concurrent-vector-class.md#reserve)|
|[清楚](reference/concurrent-vector-class.md#clear)|[調整](reference/concurrent-vector-class.md#resize)|
|[運算子*](reference/concurrent-vector-class.md#operator_eq)|[shrink_to_fit](reference/concurrent-vector-class.md#shrink_to_fit)|

修改現有元素值的操作不併發安全。 使用同步物件(如[reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)物件)將併發讀取和寫入操作同步到同一數據元素。 關於同步物件的詳細資訊,請參閱[同步資料結構](../../parallel/concrt/synchronization-data-structures.md)。

轉換使用`vector``concurrent_vector`使用的現有代碼時,併發操作可能會導致應用程式的行為發生更改。 例如,請考慮以下程式,該程序同時在物件上執行兩個`concurrent_vector`任務。 第一個任務將其他元素追加到`concurrent_vector`物件。 第二個任務計算同一物件中所有元素的總和。

[!code-cpp[concrt-vector-safety#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_1.cpp)]

儘管該方法`end`是併發安全的,但對[push_back](reference/concurrent-vector-class.md#push_back)方法的併發調用會導致`end`返回的值發生更改。 反覆運算器遍歷的元素數不確定。 因此,每次運行該程式時,此程序都會產生不同的結果。 當元素類型不小時,在和`push_back``end`調用之間可能存在爭用條件。 該方法`end`可能會返回已分配但未完全初始化的元素。

### <a name="exception-safety"></a><a name="vector-exceptions"></a>異常安全

如果成長或分配操作引發異常,`concurrent_vector`則物件的狀態將無效。 除非另有說明,`concurrent_vector`否則處於無效狀態的物件的行為未定義。 但是,析構函數始終釋放物件分配的記憶體,即使對象處於無效狀態也是如此。

向量元素`T`的數據類型必須滿足以下要求。 否則,`concurrent_vector`類的行為未定義。

- 析構函數不得投擲。

- 如果預設或複製構造函數引發,則不能使用`virtual`關鍵字聲明析構函數,並且必須使用零初始化記憶體正常工作。

【[頂端](#top)

## <a name="concurrent_queue-class"></a><a name="queue"></a>concurrent_queue類

[併發::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md)類,就像[std::queue](../../standard-library/queue-class.md)類一樣,允許您訪問其正面和後元素。 該`concurrent_queue`類啟用併發安全排隊和取消排隊操作。 此處,併發安全意味著指標或反覆運算器始終有效。 它不是元素初始化或特定遍歷順序的保證。 該`concurrent_queue`類還提供非併發安全的反覆運算器支援。

### <a name="differences-between-concurrent_queue-and-queue"></a><a name="queue-differences"></a>concurrent_queue和佇列之間的差異

該`concurrent_queue`類`queue`與 類非常相似。 以下各點說明瞭與`concurrent_queue`的不同`queue`位置:

- `concurrent_queue`物件上的排隊和取消排隊操作是併發安全的。

- 類`concurrent_queue`提供非併發安全的反覆運算器支援。

- 類`concurrent_queue`不提供`front``pop`或 方法。 類`concurrent_queue`通過定義[try_pop](reference/concurrent-queue-class.md#try_pop)方法替換這些方法。

- 類別`concurrent_queue`不提供方法`back`。 因此,您不能引用佇列的末尾。

- 類別`concurrent_queue`提供[unsafe_size](reference/concurrent-queue-class.md#unsafe_size)方法而不是`size`方法 。 該方法`unsafe_size`不併發安全。

### <a name="concurrency-safe-operations"></a><a name="queue-safety"></a>併發安全操作

從`concurrent_queue`物件排隊或取消排隊的所有方法都是併發安全的。 此處,併發安全意味著指標或反覆運算器始終有效。 它不是元素初始化或特定遍歷順序的保證。

下表顯示了併發安全的常見`concurrent_queue`方法和運算符。

|||
|-|-|
|[空](reference/concurrent-queue-class.md#empty)|[推](reference/concurrent-queue-class.md#push)|
|[get_allocator](reference/concurrent-queue-class.md#get_allocator)|[try_pop](reference/concurrent-queue-class.md#try_pop)|

儘管該方法`empty`是併發安全的,但併發操作可能會導致佇列`empty`在 方法返回之前增長或收縮。

下表顯示了非併發安全的常見方法和運算符。

|||
|-|-|
|[清楚](reference/concurrent-queue-class.md#clear)|[unsafe_end](reference/concurrent-queue-class.md#unsafe_end)|
|[unsafe_begin](reference/concurrent-queue-class.md#unsafe_begin)|[unsafe_size](reference/concurrent-queue-class.md#unsafe_size)|

### <a name="iterator-support"></a><a name="queue-iterators"></a>反覆運算器支援

提供`concurrent_queue`不併發安全的反覆運算器。 我們建議您僅使用這些反覆運算器進行調試。

`concurrent_queue`反覆運算器僅向前方向遍歷元素。 下表顯示了每個反覆運算器支援的運算符。

|運算子|描述|
|--------------|-----------------|
|`operator++`|前進到佇列中的下一個專案。 此運算元重載,以提供預增量和增量後語義。|
|`operator*`|檢索對當前項的引用。|
|`operator->`|檢索指向當前項的指標。|

【[頂端](#top)

## <a name="concurrent_unordered_map-class"></a><a name="unordered_map"></a>concurrent_unordered_map類

[併發:::concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md)類是一個關聯容器類,它就像[std::unordered_map](../../standard-library/unordered-map-class.md)類一樣,控制類型[std::p空氣\<const Key、Ty>](../../standard-library/pair-structure.md)的元素的不同長度序列。 將無序地圖視為字典,您可以將鍵和值對添加到或按鍵查找值。 當您有多個線程或任務必須同時訪問共用容器、插入或更新它時,此類非常有用。

下面的範例顯示了`concurrent_unordered_map`使用的基本結構。 本示例在範圍 ['a'," "i"中插入字元鍵。 由於操作順序尚未確定,因此每個鍵的最終值也不確定。 但是,可以安全地並行執行插入。

[!code-cpp[concrt-unordered-map-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_2.cpp)]

有關用於`concurrent_unordered_map`並行執行映射和減少操作的範例,請參閱[如何:在並行中執行映射和減少操作](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)。

### <a name="differences-between-concurrent_unordered_map-and-unordered_map"></a><a name="map-differences"></a>concurrent_unordered_map和unordered_map之間的差異

該`concurrent_unordered_map`類`unordered_map`與 類非常相似。 以下各點說明瞭與`concurrent_unordered_map`的不同`unordered_map`位置:

- `erase` `bucket_size``unsafe_erase``unsafe_bucket``unsafe_bucket_count`、`bucket_count`與方法分別命名為、 與`unsafe_bucket_size``bucket`。 `unsafe_`命名約定指示這些方法不併發安全。 有關併發安全的詳細資訊,請參閱[併發安全操作](#map-safety)。

- 插入操作不會使現有指標或反覆運算器無效,也不會更改地圖中已存在的項的順序。 可以同時執行插入和遍歷操作。

- `concurrent_unordered_map`僅支援正向反覆運算。

- 插入不會使 或更新`equal_range`由返回的反覆運算器無效或更新。 插入可以將不相等項追加到範圍的末尾。 開始反覆運算器指向相等的專案。

為了説明避免死鎖,在調用記憶體`concurrent_unordered_map`分配器、哈希函數或其他用戶定義的代碼時,沒有保留鎖的方法。 此外,必須確保哈希函數始終計算同一值的等鍵。 最佳哈希函數在哈希代碼空間之間統一分配密鑰。

### <a name="concurrency-safe-operations"></a><a name="map-safety"></a>併發安全操作

該`concurrent_unordered_map`類支援併發安全插入和元素訪問操作。 插入操作不會使現有指標或反覆運算器失效。 反覆運算器訪問和遍歷操作也是併發安全的。 此處,併發安全意味著指標或反覆運算器始終有效。 它不是元素初始化或特定遍歷順序的保證。 下表顯示了常用`concurrent_unordered_map`的方法和運算符,這些方法和運算符是併發安全的。

|||||
|-|-|-|-|
|[在](reference/concurrent-unordered-map-class.md#at)|`count`|`find`|[key_eq](reference/concurrent-unordered-map-class.md#key_eq)|
|`begin`|`empty`|`get_allocator`|`max_size`|
|`cbegin`|`end`|`hash_function`|[operator&#91;&#93;](reference/concurrent-unordered-map-class.md#operator_at)|
|`cend`|`equal_range`|[插入](reference/concurrent-unordered-map-class.md#insert)|`size`|

儘管可以從`count`併發運行的線程中安全地調用該方法,但如果同時將新值插入容器中,則不同的線程可以接收不同的結果。

下表顯示了非併發安全的常用方法和運算符。

||||
|-|-|-|
|`clear`|`max_load_factor`|`rehash`|
|`load_factor`|[運算子*](reference/concurrent-unordered-map-class.md#operator_eq)

除了這些方法之外,任何以方法`unsafe_`開頭的方法也並不併發安全。

【[頂端](#top)

## <a name="concurrent_unordered_multimap-class"></a><a name="unordered_multimap"></a>concurrent_unordered_multimap 類別

[併發::concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)類`concurrent_unordered_map`與 類非常相似,只不過它允許多個值映射到同一個鍵。 它還在`concurrent_unordered_map`以下方面有所不同:

- [concurrent_unordered_multimap::插入](reference/concurrent-unordered-multimap-class.md#insert)方法傳回反覆運算器`std::pair<iterator, bool>`而不是 。

- 類別`concurrent_unordered_multimap`不提供,也不`operator[]`提供方法`at`。

下面的範例顯示了`concurrent_unordered_multimap`使用的基本結構。 本示例在範圍 ['a'," "i"中插入字元鍵。 `concurrent_unordered_multimap`使金鑰具有多個值。

[!code-cpp[concrt-unordered-multimap-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_3.cpp)]

【[頂端](#top)

## <a name="concurrent_unordered_set-class"></a><a name="unordered_set"></a>concurrent_unordered_set類

[併發::concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md)類`concurrent_unordered_map`與 類非常相似,只不過它管理值而不是鍵和值對。 類別`concurrent_unordered_set`不提供,也不`operator[]`提供方法`at`。

下面的範例顯示了`concurrent_unordered_set`使用的基本結構。 本示例在範圍 ['a'," "i"中插入字元值。 並行執行插入是安全的。

[!code-cpp[concrt-unordered-set#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_4.cpp)]

【[頂端](#top)

## <a name="concurrent_unordered_multiset-class"></a><a name="unordered_multiset"></a>concurrent_unordered_multiset類

[併發:::concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)類與類非常相似`concurrent_unordered_set`, 只不過它允許重複值。 它還在`concurrent_unordered_set`以下方面有所不同:

- [concurrent_unordered_multiset::插入](reference/concurrent-unordered-multiset-class.md#insert)方法傳回反覆運算器`std::pair<iterator, bool>`而不是 。

- 類別`concurrent_unordered_multiset`不提供,也不`operator[]`提供方法`at`。

下面的範例顯示了`concurrent_unordered_multiset`使用的基本結構。 本示例在範圍 ['a'," "i"中插入字元值。 `concurrent_unordered_multiset`使值多次發生。

[!code-cpp[concrt-unordered-multiset#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_5.cpp)]

【[頂端](#top)

## <a name="combinable-class"></a><a name="combinable"></a>可組合類

[併發::可組合](../../parallel/concrt/reference/combinable-class.md)類提供可重用的線程本地存儲,允許您執行細粒度計算,然後將這些計算合併到最終結果中。 您可以將 `combinable` 物件視為削減變數。

當您`combinable`具有在多個線程或任務之間共用的資源時,該類非常有用。 該`combinable`類通過以無鎖方式提供對共享資源的訪問,説明您消除共享狀態。 因此,此類提供了使用同步機制(例如互斥體)來同步對來自多個線程的共享數據的訪問的替代方法。

### <a name="methods-and-features"></a><a name="combinable-features"></a>方法和功能

下表顯示了`combinable`類的一些重要方法。 關於所有類別的詳細資訊,`combinable`請參考[可組合類別](../../parallel/concrt/reference/combinable-class.md)。

|方法|描述|
|------------|-----------------|
|[local](reference/combinable-class.md#local)|檢索對與當前線程上下文關聯的局部變數的引用。|
|[清楚](reference/combinable-class.md#clear)|從`combinable`物件中刪除所有線程局部變數。|
|[結合](reference/combinable-class.md#combine)<br /><br /> [combine_each](reference/combinable-class.md#combine_each)|使用提供的組合函數從所有線程局部計算集生成最終值。|

類`combinable`是一個範本類,在最終合併的結果上參數化。 如果呼叫預設建構函數,`T`樣本參數類型必須具有預設建構函數和複製建構函數。 如果`T`範本參數類型沒有預設建構函數,請調用以初始化函數作為其參數的構造函數的重載版本。

呼叫[組合](reference/combinable-class.md#combine)或[combine_each](reference/combinable-class.md#combine_each)`combinable`方法後, 可以將其他資料儲存在物件中。 您還可以多次調用`combine``combine_each`和 方法。 如果`combinable`物件中的局部值沒有變化,`combine`則`combine_each`和 方法每次調用它們時都會生成相同的結果。

### <a name="examples"></a><a name="combinable-examples"></a>例子

有關如何使用類別的範例,`combinable`請參閱以下主題:

- [如何：使用可組合的類別改善效能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)

- [如何：使用 combinable 結合集合](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)

【[頂端](#top)

## <a name="related-topics"></a>相關主題

[如何：使用平行容器提高效率](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br/>
展示如何使用並行容器並行高效地存儲和訪問數據。

[如何：使用可組合的類別改善效能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br/>
演示如何使用`combinable`類 消除共享狀態,從而提高性能。

[如何：使用 combinable 結合集合](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)<br/>
展示如何使用函數`combine`合併線程本地數據集。

[平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
描述 PPL,它提供了一個命令式程式設計模型,可促進可伸縮性和易用性,用於開發併發應用程式。

## <a name="reference"></a>參考

[concurrent_vector 類別](../../parallel/concrt/reference/concurrent-vector-class.md)

[concurrent_queue 類別](../../parallel/concrt/reference/concurrent-queue-class.md)

[concurrent_unordered_map 類別](../../parallel/concrt/reference/concurrent-unordered-map-class.md)

[concurrent_unordered_multimap 類別](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)

[concurrent_unordered_set 類別](../../parallel/concrt/reference/concurrent-unordered-set-class.md)

[concurrent_unordered_multiset類](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)

[combinable 類別](../../parallel/concrt/reference/combinable-class.md)
