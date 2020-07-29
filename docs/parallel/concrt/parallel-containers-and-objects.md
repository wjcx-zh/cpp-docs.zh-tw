---
title: 平行容器和物件
ms.date: 03/27/2019
helpviewer_keywords:
- parallel objects
- parallel containers
- concurrent containers
ms.assetid: 90ab715c-29cd-48eb-8e76-528619aab466
ms.openlocfilehash: dffe9b3490f52645414643ebc23ab78553abafff
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213901"
---
# <a name="parallel-containers-and-objects"></a>平行容器和物件

平行模式程式庫（PPL）包含數個容器和物件，可提供其元素的安全線程存取。

*並行容器*可為最重要的作業提供並行安全存取。 在這裡，並行安全表示指標或反覆運算器一律有效。 不保證專案初始化或特定的遍歷順序。 這些容器的功能與 c + + 標準程式庫所提供的功能類似。 例如， [concurrency：： concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)類別與[std：： vector](../../standard-library/vector-class.md)類別類似，不同之處在于 `concurrent_vector` 類別可讓您以平行方式附加元素。 當您的平行程式碼同時需要相同容器的讀取和寫入權限時，請使用並行容器。

*並行物件*會同時在元件之間共用。 以平行方式計算並行物件狀態的處理常式，會產生與另一個處理常式順序連續計算相同狀態的結果。 [Concurrency：：組合](../../parallel/concrt/reference/combinable-class.md)類別是並行物件類型的其中一個範例。 `combinable`類別可讓您平行執行計算，然後將這些計算結合成最終結果。 當您以其他方式使用同步處理機制（例如 mutex）來同步存取共用變數或資源時，請使用並行物件。

## <a name="sections"></a><a name="top"></a>各節

本主題詳細說明下列平行容器和物件。

並行容器：

- [concurrent_vector 類別](#vector)

  - [Concurrent_vector 與向量之間的差異](#vector-differences)

  - [並行-安全作業](#vector-safety)

  - [例外狀況安全](#vector-exceptions)

- [concurrent_queue 類別](#queue)

  - [Concurrent_queue 與佇列之間的差異](#queue-differences)

  - [並行-安全作業](#queue-safety)

  - [反覆運算器支援](#queue-iterators)

- [concurrent_unordered_map 類別](#unordered_map)

  - [Concurrent_unordered_map 和 unordered_map 之間的差異](#map-differences)

  - [並行-安全作業](#map-safety)

- [concurrent_unordered_multimap 類別](#unordered_multimap)

- [concurrent_unordered_set 類別](#unordered_set)

- [concurrent_unordered_multiset 類別](#unordered_multiset)

並行物件：

- [組合類別](#combinable)

  - [方法和功能](#combinable-features)

  - [範例](#combinable-examples)

## <a name="concurrent_vector-class"></a><a name="vector"></a>concurrent_vector 類別

[Concurrency：： concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)類別是一種序列容器類別，如同[std：： vector](../../standard-library/vector-class.md)類別，可讓您隨機存取其元素。 `concurrent_vector`類別會啟用並行安全的附加和元素存取作業。 附加作業不會使現有的指標或反覆運算器失效。 反覆運算器存取和遍歷作業也是並行安全的。 在這裡，並行安全表示指標或反覆運算器一律有效。 不保證專案初始化或特定的遍歷順序。

### <a name="differences-between-concurrent_vector-and-vector"></a><a name="vector-differences"></a>Concurrent_vector 與向量之間的差異

`concurrent_vector`類別與類別十分相似 `vector` 。 物件上的附加、專案存取和反覆運算器存取作業的複雜性與 `concurrent_vector` `vector` 物件相同。 下列幾點說明與 `concurrent_vector` 不同之處 `vector` ：

- 物件上的附加、專案存取、反覆運算器存取和 iterator 遍歷作業 `concurrent_vector` 是並行安全的。

- 您只能將元素加入至物件的結尾 `concurrent_vector` 。 `concurrent_vector`類別不提供 `insert` 方法。

- `concurrent_vector`當您附加至物件時，它不會使用[移動語義](../../cpp/rvalue-reference-declarator-amp-amp.md)。

- `concurrent_vector`類別並未提供 `erase` 或 `pop_back` 方法。 如同 `vector` ，使用[clear](reference/concurrent-vector-class.md#clear)方法從物件中移除所有元素 `concurrent_vector` 。

- `concurrent_vector`類別不會將其元素連續儲存于記憶體中。 因此，您無法使用 `concurrent_vector` 類別，方法是您可以使用陣列的所有方式。 例如，針對型別為 `v` 的變數 `concurrent_vector` ，運算式會 `&v[0]+2` 產生未定義的行為。

- `concurrent_vector`類別會定義[grow_by](reference/concurrent-vector-class.md#grow_by)和[grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least)方法。 這些方法與重[設大小](reference/concurrent-vector-class.md#resize)方法相似，不同之處在于它們是並行安全的。

- `concurrent_vector`當您附加至物件或調整其大小時，物件不會重新放置其元素。 這讓現有的指標和反覆運算器在並行作業期間仍然有效。

- 執行時間不會針對類型定義的特殊化版本 `concurrent_vector` **`bool`** 。

### <a name="concurrency-safe-operations"></a><a name="vector-safety"></a>並行-安全作業

附加至或增加 `concurrent_vector` 物件大小或存取物件中元素的所有方法， `concurrent_vector` 都是並行安全的。 在這裡，並行安全表示指標或反覆運算器一律有效。 不保證專案初始化或特定的遍歷順序。 此規則的例外狀況是 `resize` 方法。

下表顯示 `concurrent_vector` 並行安全的常見方法與運算子。

||||
|-|-|-|
|[at](reference/concurrent-vector-class.md#at)|[成品](reference/concurrent-vector-class.md#end)|[operator&#91;&#93;](reference/concurrent-vector-class.md#operator_at)|
|[起點](reference/concurrent-vector-class.md#begin)|[前端](reference/concurrent-vector-class.md#front)|[push_back](reference/concurrent-vector-class.md#push_back)|
|[返回](reference/concurrent-vector-class.md#back)|[grow_by](reference/concurrent-vector-class.md#grow_by)|[rbegin](reference/concurrent-vector-class.md#rbegin)|
|[存儲](reference/concurrent-vector-class.md#capacity)|[grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least)|[rend](reference/concurrent-vector-class.md#rend)|
|[empty](reference/concurrent-vector-class.md#empty)|[max_size](reference/concurrent-vector-class.md#max_size)|[size](reference/concurrent-vector-class.md#size)|

執行時間提供與 c + + 標準程式庫相容的作業（例如） `reserve` 不是並行安全的。 下表顯示不是並行安全的常見方法與運算子。

|||
|-|-|
|[assign](reference/concurrent-vector-class.md#assign)|[留成](reference/concurrent-vector-class.md#reserve)|
|[明確](reference/concurrent-vector-class.md#clear)|[調整](reference/concurrent-vector-class.md#resize)|
|[operator =](reference/concurrent-vector-class.md#operator_eq)|[shrink_to_fit](reference/concurrent-vector-class.md#shrink_to_fit)|

修改現有元素值的作業不是並行安全。 使用[reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)物件之類的同步物件，將並行讀取和寫入作業同步處理至相同的資料元素。 如需同步處理物件的詳細資訊，請參閱[同步處理資料結構](../../parallel/concrt/synchronization-data-structures.md)。

當您將使用的現有程式碼轉換為 `vector` 使用時 `concurrent_vector` ，並行作業會導致應用程式的行為變更。 例如，請考慮下列在物件上同時執行兩項工作的程式 `concurrent_vector` 。 第一個工作會將其他元素附加至 `concurrent_vector` 物件。 第二個工作會計算相同物件中所有元素的總和。

[!code-cpp[concrt-vector-safety#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_1.cpp)]

雖然此 `end` 方法是並行安全的，但同時呼叫[push_back](reference/concurrent-vector-class.md#push_back)方法會導致傳回的值 `end` 變更。 反覆運算器所遍歷的元素數目不確定。 因此，每次執行此程式時，可能會產生不同的結果。 當專案類型為非一般時，與呼叫之間有可能存在競爭條件 `push_back` `end` 。 `end`方法可能會傳回已配置但未完全初始化的元素。

### <a name="exception-safety"></a><a name="vector-exceptions"></a>例外狀況安全

如果成長或指派作業擲回例外狀況，物件的狀態 `concurrent_vector` 就會變成無效。 除非另有指示， `concurrent_vector` 否則處於無效狀態之物件的行為是未定義的。 不過，即使物件處於無效狀態，此析構函式一律會釋出物件所配置的記憶體。

向量元素的資料類型 `T` 必須符合下列需求。 否則，類別的行為 `concurrent_vector` 會是未定義的。

- 此析構函式不能擲回。

- 如果預設或複製的函式擲回，則不能使用關鍵字來宣告該處理常式， **`virtual`** 而且它必須正確地使用零初始化的記憶體。

[[頂端](#top)]

## <a name="concurrent_queue-class"></a><a name="queue"></a>concurrent_queue 類別

[Concurrency：： concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md)類別就如同[std：： queue](../../standard-library/queue-class.md)類別，可讓您存取其 front 和 back 元素。 `concurrent_queue`類別會啟用並行安全的排入佇列和清除佇列作業。 在這裡，並行安全表示指標或反覆運算器一律有效。 不保證專案初始化或特定的遍歷順序。 `concurrent_queue`類別也提供不是並行安全的反覆運算器支援。

### <a name="differences-between-concurrent_queue-and-queue"></a><a name="queue-differences"></a>Concurrent_queue 與佇列之間的差異

`concurrent_queue`類別與類別十分相似 `queue` 。 下列幾點說明與 `concurrent_queue` 不同之處 `queue` ：

- 物件的排入佇列和清除佇列作業 `concurrent_queue` 是並行安全的。

- `concurrent_queue`類別提供了不是並行安全的反覆運算器支援。

- `concurrent_queue`類別並未提供 `front` 或 `pop` 方法。 類別會藉 `concurrent_queue` 由定義[try_pop](reference/concurrent-queue-class.md#try_pop)方法來取代這些方法。

- `concurrent_queue`類別不提供 `back` 方法。 因此，您無法參考佇列的結尾。

- `concurrent_queue`類別會提供[unsafe_size](reference/concurrent-queue-class.md#unsafe_size)方法，而不是 `size` 方法。 `unsafe_size`方法不是並行安全的。

### <a name="concurrency-safe-operations"></a><a name="queue-safety"></a>並行-安全作業

從物件排入佇列或清除佇列的所有方法 `concurrent_queue` 都是並行安全的。 在這裡，並行安全表示指標或反覆運算器一律有效。 不保證專案初始化或特定的遍歷順序。

下表顯示 `concurrent_queue` 並行安全的常見方法與運算子。

|||
|-|-|
|[empty](reference/concurrent-queue-class.md#empty)|[push](reference/concurrent-queue-class.md#push)|
|[get_allocator](reference/concurrent-queue-class.md#get_allocator)|[try_pop](reference/concurrent-queue-class.md#try_pop)|

雖然此 `empty` 方法是並行安全的，但並行作業可能會在方法傳回之前，讓佇列成長或縮小 `empty` 。

下表顯示不是並行安全的常見方法與運算子。

|||
|-|-|
|[明確](reference/concurrent-queue-class.md#clear)|[unsafe_end](reference/concurrent-queue-class.md#unsafe_end)|
|[unsafe_begin](reference/concurrent-queue-class.md#unsafe_begin)|[unsafe_size](reference/concurrent-queue-class.md#unsafe_size)|

### <a name="iterator-support"></a><a name="queue-iterators"></a>反覆運算器支援

`concurrent_queue`提供了不是並行安全的反覆運算器。 我們建議您只使用這些反覆運算器來進行偵錯工具。

`concurrent_queue`反覆運算器只會在正向方向中遍歷專案。 下表顯示每個反覆運算器支援的運算子。

|運算子|說明|
|--------------|-----------------|
|`operator++`|前進到佇列中的下一個專案。 這個運算子會多載，以同時提供預先遞增和後置遞增的語義。|
|`operator*`|抓取目前專案的參考。|
|`operator->`|抓取目前專案的指標。|

[[頂端](#top)]

## <a name="concurrent_unordered_map-class"></a><a name="unordered_map"></a>concurrent_unordered_map 類別

[Concurrency：： concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md)類別是一種關聯的容器類別，就像[std：： unordered_map](../../standard-library/unordered-map-class.md)類別一樣，它會控制類型[std：:p 空中 \<const Key, Ty> ](../../standard-library/pair-structure.md)之元素的變動長度序列。 將未排序的對應視為字典，您可以在其中加入索引鍵和值組，或依索引鍵來查閱值。 當您有多個執行緒或工作必須同時存取共用容器、插入其中或進行更新時，這個類別會很有用。

下列範例顯示使用的基本結構 `concurrent_unordered_map` 。 這個範例會在 [' a '，' i '] 範圍內插入字元鍵。 由於作業的順序不確定，因此，每個索引鍵的最終值也會是不確定的。 不過，您可以放心地平行執行插入。

[!code-cpp[concrt-unordered-map-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_2.cpp)]

如需使用 `concurrent_unordered_map` 以平行方式執行對應和減少作業的範例，請參閱[如何：平行執行對應和減少作業](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)。

### <a name="differences-between-concurrent_unordered_map-and-unordered_map"></a><a name="map-differences"></a>Concurrent_unordered_map 和 unordered_map 之間的差異

`concurrent_unordered_map`類別與類別十分相似 `unordered_map` 。 下列幾點說明與 `concurrent_unordered_map` 不同之處 `unordered_map` ：

- `erase`、、 `bucket` `bucket_count` 和 `bucket_size` 方法分別命名為 `unsafe_erase` 、、 `unsafe_bucket` `unsafe_bucket_count` 和 `unsafe_bucket_size` 。 `unsafe_`命名慣例指出這些方法不是並行安全的。 如需並行安全性的詳細資訊，請參閱[並行安全作業](#map-safety)。

- 插入作業不會使現有的指標或反覆運算器無效，也不會變更已存在於對應中的專案順序。 Insert 和穿越作業可以同時發生。

- `concurrent_unordered_map`僅支援向前反復專案。

- 插入並不會使傳回的反覆運算器失效或更新 `equal_range` 。 插入可以將不相等的專案附加至範圍結尾。 開始反覆運算器指向相等的專案。

為避免鎖死， `concurrent_unordered_map` 在呼叫記憶體配置器、雜湊函數或其他使用者定義的程式碼時，沒有任何方法持有鎖定。 此外，您必須確定雜湊函式一律會將相等的索引鍵評估為相同的值。 最佳的雜湊函式會在雜湊碼空間中均勻散發金鑰。

### <a name="concurrency-safe-operations"></a><a name="map-safety"></a>並行-安全作業

`concurrent_unordered_map`類別會啟用並行安全的插入和元素存取作業。 插入作業不會使現有的指標或反覆運算器失效。 反覆運算器存取和遍歷作業也是並行安全的。 在這裡，並行安全表示指標或反覆運算器一律有效。 不保證專案初始化或特定的遍歷順序。 下表顯示常使用的 `concurrent_unordered_map` 方法和並行安全運算子。

|||||
|-|-|-|-|
|[at](reference/concurrent-unordered-map-class.md#at)|`count`|`find`|[key_eq](reference/concurrent-unordered-map-class.md#key_eq)|
|`begin`|`empty`|`get_allocator`|`max_size`|
|`cbegin`|`end`|`hash_function`|[operator&#91;&#93;](reference/concurrent-unordered-map-class.md#operator_at)|
|`cend`|`equal_range`|[insert](reference/concurrent-unordered-map-class.md#insert)|`size`|

雖然 `count` 可以從同時執行的執行緒安全地呼叫方法，但如果新的值同時插入容器，則不同的執行緒可能會收到不同的結果。

下表顯示常用的方法和不是並行安全的運算子。

||||
|-|-|-|
|`clear`|`max_load_factor`|`rehash`|
|`load_factor`|[operator =](reference/concurrent-unordered-map-class.md#operator_eq)

除了這些方法以外，任何以開頭的方法 `unsafe_` 也不是並行安全。

[[頂端](#top)]

## <a name="concurrent_unordered_multimap-class"></a><a name="unordered_multimap"></a>concurrent_unordered_multimap 類別

[Concurrency：： concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)類別與類別密切相似， `concurrent_unordered_map` 不同之處在于它可讓多個值對應至相同的索引鍵。 它也不同于 `concurrent_unordered_map` ，方法如下：

- [Concurrent_unordered_multimap：： insert](reference/concurrent-unordered-multimap-class.md#insert)方法會傳回反覆運算器，而不是 `std::pair<iterator, bool>` 。

- `concurrent_unordered_multimap`類別並未提供 `operator[]` 或 `at` 方法。

下列範例顯示使用的基本結構 `concurrent_unordered_multimap` 。 這個範例會在 [' a '，' i '] 範圍內插入字元鍵。 `concurrent_unordered_multimap`讓索引鍵具有多個值。

[!code-cpp[concrt-unordered-multimap-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_3.cpp)]

[[頂端](#top)]

## <a name="concurrent_unordered_set-class"></a><a name="unordered_set"></a>concurrent_unordered_set 類別

[Concurrency：： concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md)類別與類別密切相似， `concurrent_unordered_map` 不同之處在于它會管理值，而不是索引鍵和值組。 `concurrent_unordered_set`類別並未提供 `operator[]` 或 `at` 方法。

下列範例顯示使用的基本結構 `concurrent_unordered_set` 。 這個範例會在 [' a '，' i '] 範圍內插入字元值。 以平行方式執行插入是安全的。

[!code-cpp[concrt-unordered-set#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_4.cpp)]

[[頂端](#top)]

## <a name="concurrent_unordered_multiset-class"></a><a name="unordered_multiset"></a>concurrent_unordered_multiset 類別

[Concurrency：： concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)類別與類別密切相似， `concurrent_unordered_set` 不同之處在于它允許重複的值。 它也不同于 `concurrent_unordered_set` ，方法如下：

- [Concurrent_unordered_multiset：： insert](reference/concurrent-unordered-multiset-class.md#insert)方法會傳回反覆運算器，而不是 `std::pair<iterator, bool>` 。

- `concurrent_unordered_multiset`類別並未提供 `operator[]` 或 `at` 方法。

下列範例顯示使用的基本結構 `concurrent_unordered_multiset` 。 這個範例會在 [' a '，' i '] 範圍內插入字元值。 `concurrent_unordered_multiset`讓值發生多次。

[!code-cpp[concrt-unordered-multiset#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_5.cpp)]

[[頂端](#top)]

## <a name="combinable-class"></a><a name="combinable"></a>組合類別

[Concurrency：：組合](../../parallel/concrt/reference/combinable-class.md)類別提供可重複使用的執行緒區域儲存區，可讓您執行更細緻的計算，然後將這些計算合併成最終結果。 您可以將 `combinable` 物件視為削減變數。

`combinable`當您有多個執行緒或工作之間共用的資源時，類別會很有用。 此 `combinable` 類別可讓您以無鎖定的方式提供對共用資源的存取權，以消除共用狀態。 因此，此類別提供使用同步處理機制（例如，mutex）來同步存取多個執行緒之共用資料的替代方法。

### <a name="methods-and-features"></a><a name="combinable-features"></a>方法和功能

下表顯示類別的一些重要方法 `combinable` 。 如需所有類別方法的詳細資訊 `combinable` ，請參閱可[組合的類別](../../parallel/concrt/reference/combinable-class.md)。

|方法|說明|
|------------|-----------------|
|[本機](reference/combinable-class.md#local)|抓取與目前線程內容相關聯之本機變數的參考。|
|[明確](reference/combinable-class.md#clear)|從物件中移除所有線程區域變數 `combinable` 。|
|[起來](reference/combinable-class.md#combine)<br /><br /> [combine_each](reference/combinable-class.md#combine_each)|使用所提供的結合函數，從所有線程區域計算的集合產生最終值。|

`combinable`類別是在最終合併結果上參數化的樣板類別。 如果您呼叫預設的函式，樣板 `T` 參數類型必須有預設的「函式」和「複製」（template）函數。 如果 `T` 範本參數類型沒有預設的處理常式，請呼叫接受初始化函數做為其參數的多載版本的函式。

`combinable`呼叫 [[合併](reference/combinable-class.md#combine)] 或 [ [combine_each](reference/combinable-class.md#combine_each) ] 方法之後，您可以將其他資料儲存在物件中。 您也可以多次呼叫 `combine` 和 `combine_each` 方法。 如果物件中沒有任何本機值 `combinable` 變更， `combine` 和 `combine_each` 方法會在每次呼叫時產生相同的結果。

### <a name="examples"></a><a name="combinable-examples"></a> 範例

如需如何使用類別的範例 `combinable` ，請參閱下列主題：

- [如何：使用可組合的來改善效能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)

- [如何：使用可組合的結合集合](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)

[[頂端](#top)]

## <a name="related-topics"></a>相關主題

[如何：使用平行容器提高效率](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br/>
示範如何使用平行容器，以平行方式有效率地儲存和存取資料。

[如何：使用可組合的來改善效能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br/>
示範如何使用 `combinable` 類別來消除共用狀態，從而改善效能。

[如何：使用可組合的結合集合](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)<br/>
示範如何使用 `combine` 函數來合併執行緒區域的資料集。

[平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
說明 PPL，其提供命令式程式設計模型，可提升擴充性和方便使用，以開發並行應用程式。

## <a name="reference"></a>參考

[concurrent_vector 類別](../../parallel/concrt/reference/concurrent-vector-class.md)

[concurrent_queue 類別](../../parallel/concrt/reference/concurrent-queue-class.md)

[concurrent_unordered_map 類別](../../parallel/concrt/reference/concurrent-unordered-map-class.md)

[concurrent_unordered_multimap 類別](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)

[concurrent_unordered_set 類別](../../parallel/concrt/reference/concurrent-unordered-set-class.md)

[concurrent_unordered_multiset 類別](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)

[組合類別](../../parallel/concrt/reference/combinable-class.md)
