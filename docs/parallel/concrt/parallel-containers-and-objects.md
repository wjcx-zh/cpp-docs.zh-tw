---
title: 平行容器和物件
ms.date: 03/27/2019
helpviewer_keywords:
- parallel objects
- parallel containers
- concurrent containers
ms.assetid: 90ab715c-29cd-48eb-8e76-528619aab466
ms.openlocfilehash: 7387173378e79a4707008a11846eab19d7ae4341
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831784"
---
# <a name="parallel-containers-and-objects"></a>平行容器和物件

平行模式程式庫 (PPL) 包含數個容器和物件，可提供其元素的安全線程存取。

*並行容器*可對最重要的作業提供平行存取安全的存取。 在這裡，並行安全表示指標或反覆運算器一律有效。 它不是專案初始化或特定遍歷順序的保證。 這些容器的功能與 c + + 標準程式庫所提供的功能類似。 例如， [concurrency：： concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) 類別與 [std：： vector](../../standard-library/vector-class.md) 類別類似，不同之處在于 `concurrent_vector` 類別可讓您以平行方式附加元素。 當您有平行程式碼需要相同容器的讀取和寫入存取權時，請使用並行容器。

*並行物件*會在元件之間同時共用。 以平行方式計算並行物件狀態的進程，會產生與以順序計算相同狀態的另一個進程相同的結果。 [Concurrency：：可組合](../../parallel/concrt/reference/combinable-class.md)類別是並行物件類型的其中一個範例。 `combinable`類別可讓您以平行方式執行計算，然後將這些計算合併成最終結果。 當您以其他方式使用同步處理機制（例如 mutex）來同步處理共用變數或資源的存取權時，請使用並行物件。

## <a name="sections"></a><a name="top"></a> 部分

本主題詳細說明下列平行容器和物件。

並行容器：

- [concurrent_vector 類別](#vector)

  - [Concurrent_vector 與 vector 之間的差異](#vector-differences)

  - [並行安全作業](#vector-safety)

  - [例外狀況安全性](#vector-exceptions)

- [concurrent_queue 類別](#queue)

  - [Concurrent_queue 和佇列之間的差異](#queue-differences)

  - [並行安全作業](#queue-safety)

  - [Iterator 支援](#queue-iterators)

- [concurrent_unordered_map 類別](#unordered_map)

  - [Concurrent_unordered_map 與 unordered_map 之間的差異](#map-differences)

  - [並行安全作業](#map-safety)

- [concurrent_unordered_multimap 類別](#unordered_multimap)

- [concurrent_unordered_set 類別](#unordered_set)

- [concurrent_unordered_multiset 類別](#unordered_multiset)

並行物件：

- [組合類別](#combinable)

  - [方法和功能](#combinable-features)

  - [範例](#combinable-examples)

## <a name="concurrent_vector-class"></a><a name="vector"></a> concurrent_vector 類別

[Concurrency：： concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)類別是 sequence 容器類別，就像[std：： vector](../../standard-library/vector-class.md)類別一樣，可讓您隨機存取其元素。 `concurrent_vector`類別可啟用並行安全附加和元素存取作業。 附加作業不會讓現有的指標或反覆運算器失效。 反覆運算器存取和遍歷作業也是並行安全的。 在這裡，並行安全表示指標或反覆運算器一律有效。 它不是專案初始化或特定遍歷順序的保證。

### <a name="differences-between-concurrent_vector-and-vector"></a><a name="vector-differences"></a> Concurrent_vector 與 vector 之間的差異

`concurrent_vector`類別與類別非常類似 `vector` 。 物件的附加、專案存取和反覆運算器存取作業的複雜性與 `concurrent_vector` 物件的複雜性相同 `vector` 。 下列各點說明 `concurrent_vector` 與不同之處 `vector` ：

- 附加、專案存取、反覆運算器存取，以及物件上的 iterator 遍歷作業 `concurrent_vector` 都是平行存取安全的。

- 您只能將元素加入至物件的結尾 `concurrent_vector` 。 `concurrent_vector`類別不提供 `insert` 方法。

- `concurrent_vector`當您附加到物件時，物件不會使用[move 語義](../../cpp/rvalue-reference-declarator-amp-amp.md)。

- `concurrent_vector`類別不提供 `erase` 或 `pop_back` 方法。 同樣地 `vector` ，您可以使用 [clear](reference/concurrent-vector-class.md#clear) 方法來移除物件中的所有元素 `concurrent_vector` 。

- `concurrent_vector`類別不會將其元素連續儲存在記憶體中。 因此，您無法 `concurrent_vector` 以您可以使用陣列的所有方式來使用類別。 例如，針對型別為 `v` 的變數 `concurrent_vector` ，運算式會 `&v[0]+2` 產生未定義的行為。

- `concurrent_vector`類別會定義[grow_by](reference/concurrent-vector-class.md#grow_by)和[grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least)方法。 這些方法類似于重 [設大小](reference/concurrent-vector-class.md#resize) 方法，不同之處在于它們是平行存取安全的。

- `concurrent_vector`當您附加至物件或調整其大小時，物件不會重新放置其元素。 這可讓現有的指標和反覆運算器在平行作業期間維持有效。

- 執行時間不會定義類型的特製化版本 `concurrent_vector` **`bool`** 。

### <a name="concurrency-safe-operations"></a><a name="vector-safety"></a> 並行安全作業

附加至或增加 `concurrent_vector` 物件大小或存取物件中專案的所有方法 `concurrent_vector` 都是平行存取安全的。 在這裡，並行安全表示指標或反覆運算器一律有效。 它不是專案初始化或特定遍歷順序的保證。 這項規則的例外狀況是 `resize` 方法。

下表顯示 `concurrent_vector` 並行安全的一般方法與運算子。

:::row:::
   :::column span="":::
      [`at`](reference/concurrent-vector-class.md#at)\
      [`back`](reference/concurrent-vector-class.md#back)\
      [`begin`](reference/concurrent-vector-class.md#begin)\
      [`capacity`](reference/concurrent-vector-class.md#capacity)
   :::column-end:::
   :::column span="":::
      [`empty`](reference/concurrent-vector-class.md#empty)\
      [`end`](reference/concurrent-vector-class.md#end)\
      [`front`](reference/concurrent-vector-class.md#front)\
      [`grow_by`](reference/concurrent-vector-class.md#grow_by)
   :::column-end:::
   :::column span="":::
      [`grow_to_at_least`](reference/concurrent-vector-class.md#grow_to_at_least)\
      [`max_size`](reference/concurrent-vector-class.md#max_size)\
      [`operator[]`](reference/concurrent-vector-class.md#operator_at)\
      [`push_back`](reference/concurrent-vector-class.md#push_back)
   :::column-end:::
   :::column span="":::
      [`rbegin`](reference/concurrent-vector-class.md#rbegin)\
      [`rend`](reference/concurrent-vector-class.md#rend)\
      [`size`](reference/concurrent-vector-class.md#size)
   :::column-end:::
:::row-end:::

例如，執行時間為了與 c + + 標準程式庫相容而提供的作業 `reserve` 不是並行安全的。 下表顯示非平行存取安全的一般方法和運算子。

:::row:::
   :::column span="":::
      [`assign`](reference/concurrent-vector-class.md#assign)\
      [`clear`](reference/concurrent-vector-class.md#clear)
   :::column-end:::
   :::column span="":::
      [`operator=`](reference/concurrent-vector-class.md#operator_eq)\
      [`reserve`](reference/concurrent-vector-class.md#reserve)
   :::column-end:::
   :::column span="":::
      [`resize`](reference/concurrent-vector-class.md#resize)
   :::column-end:::
   :::column span="":::
      [`shrink_to_fit`](reference/concurrent-vector-class.md#shrink_to_fit)
   :::column-end:::
:::row-end:::

修改現有元素值的作業不是平行存取安全的。 使用同步處理物件（例如 [reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) 物件），將並行讀取和寫入作業同步處理至相同的資料元素。 如需同步處理物件的詳細資訊，請參閱 [同步處理資料結構](../../parallel/concrt/synchronization-data-structures.md)。

當您轉換用來使用的現有程式碼時 `vector` `concurrent_vector` ，並行作業可能會導致應用程式的行為變更。 例如，請考慮使用下列程式在物件上同時執行兩項工作 `concurrent_vector` 。 第一個工作會將其他元素附加至 `concurrent_vector` 物件。 第二個工作會計算相同物件中所有元素的總和。

[!code-cpp[concrt-vector-safety#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_1.cpp)]

雖然此 `end` 方法是平行存取安全的，但是對 [push_back](reference/concurrent-vector-class.md#push_back) 方法的並行呼叫會導致傳回的值 `end` 變更。 反覆運算器所遍歷的元素數目不確定。 因此，每次執行此程式時，都會產生不同的結果。 當元素類型不是一般時，與呼叫之間有可能存在競爭條件 `push_back` `end` 。 `end`方法可能會傳回已配置但未完全初始化的元素。

### <a name="exception-safety"></a><a name="vector-exceptions"></a> 例外狀況安全性

如果成長或指派操作擲回例外狀況，則物件的狀態 `concurrent_vector` 會變成無效。 除非另有說明， `concurrent_vector` 否則處於無效狀態之物件的行為是未定義的。 但是，即使物件處於無效狀態，此函式仍一律會釋出物件配置的記憶體。

Vector 元素的資料類型 `T` 必須符合下列需求。 否則，類別的行為 `concurrent_vector` 未定義。

- 此函式不能擲回。

- 如果預設或複製的函式擲回，則不能使用關鍵字來宣告該函 **`virtual`** 式，而且必須正確地使用零初始化的記憶體。

[[頂端](#top)]

## <a name="concurrent_queue-class"></a><a name="queue"></a> concurrent_queue 類別

[Concurrency：： concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md)類別就像[std：： queue](../../standard-library/queue-class.md)類別一樣，可讓您存取其前端和後端專案。 `concurrent_queue`類別可啟用並行安全的排入佇列和清除佇列作業。 在這裡，並行安全表示指標或反覆運算器一律有效。 它不是專案初始化或特定遍歷順序的保證。 `concurrent_queue`類別也提供不可平行存取安全的 iterator 支援。

### <a name="differences-between-concurrent_queue-and-queue"></a><a name="queue-differences"></a> Concurrent_queue 和佇列之間的差異

`concurrent_queue`類別與類別非常類似 `queue` 。 下列各點說明 `concurrent_queue` 與不同之處 `queue` ：

- 物件上的佇列和清除佇列作業 `concurrent_queue` 是平行存取安全的。

- `concurrent_queue`類別提供的 iterator 支援不是平行存取安全的。

- `concurrent_queue`類別不提供 `front` 或 `pop` 方法。 類別會藉 `concurrent_queue` 由定義 [try_pop](reference/concurrent-queue-class.md#try_pop) 方法來取代這些方法。

- `concurrent_queue`類別不提供 `back` 方法。 因此，您無法參考佇列的結尾。

- `concurrent_queue`類別會提供[unsafe_size](reference/concurrent-queue-class.md#unsafe_size)方法，而不是 `size` 方法。 `unsafe_size`方法不是平行存取安全的。

### <a name="concurrency-safe-operations"></a><a name="queue-safety"></a> 並行安全作業

從物件排入佇列或清除佇列的所有方法 `concurrent_queue` 都是並行安全的。 在這裡，並行安全表示指標或反覆運算器一律有效。 它不是專案初始化或特定遍歷順序的保證。

下表顯示 `concurrent_queue` 並行安全的一般方法與運算子。

:::row:::
   :::column span="":::
      [`empty`](reference/concurrent-queue-class.md#empty)
   :::column-end:::
   :::column span="":::
      [`get_allocator`](reference/concurrent-queue-class.md#get_allocator)
   :::column-end:::
   :::column span="":::
      [`push`](reference/concurrent-queue-class.md#push)
   :::column-end:::
   :::column span="":::
      [`try_pop`](reference/concurrent-queue-class.md#try_pop)
   :::column-end:::
:::row-end:::

雖然此 `empty` 方法是平行存取安全的，但是平行作業可能會在方法傳回之前，讓佇列成長或縮減 `empty` 。

下表顯示非平行存取安全的一般方法和運算子。

:::row:::
   :::column span="":::
      [`clear`](reference/concurrent-queue-class.md#clear)
   :::column-end:::
   :::column span="":::
      [`unsafe_begin`](reference/concurrent-queue-class.md#unsafe_begin)
   :::column-end:::
   :::column span="":::
      [`unsafe_end`](reference/concurrent-queue-class.md#unsafe_end)
   :::column-end:::
   :::column span="":::
      [`unsafe_size`](reference/concurrent-queue-class.md#unsafe_size)
   :::column-end:::
:::row-end:::

### <a name="iterator-support"></a><a name="queue-iterators"></a> Iterator 支援

`concurrent_queue`提供不是平行存取安全的反覆運算器。 我們建議您只使用這些反覆運算器進行調試。

`concurrent_queue`反覆運算器只會以正向方向轉送元素。 下表顯示每個 iterator 支援的運算子。

|運算子|描述|
|--------------|-----------------|
|`operator++`|前進到佇列中的下一個專案。 這個運算子會多載，以提供預先遞增和後置遞增的語義。|
|`operator*`|抓取目前專案的參考。|
|`operator->`|抓取目前專案的指標。|

\[[頂端](#top)]

## <a name="concurrent_unordered_map-class"></a><a name="unordered_map"></a> concurrent_unordered_map 類別

[Concurrency：： concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md)類別是關聯的容器類別，就像[std：： unordered_map](../../standard-library/unordered-map-class.md)類別一樣，它會控制[std：:p 空調 \<const Key, Ty> ](../../standard-library/pair-structure.md)類型元素的不同長度序列。 將未排序的對應視為字典，您可以將索引鍵和值組加入或依索引鍵查閱值。 當您有多個執行緒或工作必須同時存取共用容器、將其插入或更新時，這個類別就很有用。

下列範例顯示使用的基本結構 `concurrent_unordered_map` 。 此範例會在 [' a '、' i '] 範圍中插入字元索引鍵。 由於作業的順序不確定，因此每個索引鍵的最終值也會是不確定的。 不過，您可以安全地平行執行插入。

[!code-cpp[concrt-unordered-map-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_2.cpp)]

如需使用 `concurrent_unordered_map` 來執行對應和平行減少作業的範例，請參閱 [如何：平行執行對應和縮減作業](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)。

### <a name="differences-between-concurrent_unordered_map-and-unordered_map"></a><a name="map-differences"></a> Concurrent_unordered_map 與 unordered_map 之間的差異

`concurrent_unordered_map`類別與類別非常類似 `unordered_map` 。 下列各點說明 `concurrent_unordered_map` 與不同之處 `unordered_map` ：

- `erase`、、 `bucket` 和 `bucket_count` `bucket_size` 方法分別命名為 `unsafe_erase` 、、 `unsafe_bucket` `unsafe_bucket_count` 和 `unsafe_bucket_size` 。 `unsafe_`命名慣例指出這些方法不是平行存取安全的。 如需平行存取安全的詳細資訊，請參閱 [平行存取安全作業](#map-safety)。

- 插入作業不會讓現有的指標或反覆運算器失效，也不會變更已存在於對應中的專案順序。 Insert 和遍歷作業可以同時進行。

- `concurrent_unordered_map` 僅支援向前反覆運算。

- 插入並不會使所傳回的反覆運算器失效或更新 `equal_range` 。 插入可以將不相等的專案附加至範圍的結尾。 開始反覆運算器指向相等的專案。

為了避免鎖死， `concurrent_unordered_map` 在呼叫記憶體配置器、雜湊函式或其他使用者定義的程式碼時，不會保留鎖定的方法。 此外，您必須確保雜湊函數一律會將相等的索引鍵評估為相同的值。 最佳的雜湊函式會在雜湊程式碼空間中統一散發索引鍵。

### <a name="concurrency-safe-operations"></a><a name="map-safety"></a> 並行安全作業

`concurrent_unordered_map`類別可啟用並行安全的插入和專案存取作業。 插入作業不會讓現有的指標或反覆運算器失效。 反覆運算器存取和遍歷作業也是並行安全的。 在這裡，並行安全表示指標或反覆運算器一律有效。 它不是專案初始化或特定遍歷順序的保證。 下表顯示並行安全的常用 `concurrent_unordered_map` 方法和運算子。

:::row:::
   :::column span="":::
      [`at`](reference/concurrent-unordered-map-class.md#at)\
      [`begin`](reference/concurrent-unordered-map-class.md#begin)\
      [`cbegin`](reference/concurrent-unordered-map-class.md#cbegin)\
      [`cend`](reference/concurrent-unordered-map-class.md#cend)
   :::column-end:::
   :::column span="":::
      [`count`](reference/concurrent-unordered-map-class.md#count)\
      [`empty`](reference/concurrent-unordered-map-class.md#empty)\
      [`end`](reference/concurrent-unordered-map-class.md#cend)\
      [`equal_range`](reference/concurrent-unordered-map-class.md#equal_range)
   :::column-end:::
   :::column span="":::
      [`find`](reference/concurrent-unordered-map-class.md#find)\
      [`get_allocator`](reference/concurrent-unordered-map-class.md#get_allocator)\
      [`hash_function`](reference/concurrent-unordered-map-class.md#hash_function)\
      [`insert`](reference/concurrent-unordered-map-class.md#insert)
   :::column-end:::
   :::column span="":::
      [`key_eq`](reference/concurrent-unordered-map-class.md#key_eq)\
      [`max_size`](reference/concurrent-unordered-map-class.md#max_size)\
      [`operator[]`](./reference/concurrent-unordered-map-class.md#operator_at)\
      [`size`](reference/concurrent-unordered-map-class.md#size)
   :::column-end:::
:::row-end:::

雖然 `count` 可以安全地從同時執行的執行緒呼叫方法，但如果新值同時插入容器中，則不同的執行緒可能會收到不同的結果。

下表顯示不是並行安全的常用方法和運算子。

:::row:::
   :::column span="":::
      [`clear`](reference/concurrent-unordered-map-class.md#clear)\
      [`load_factor`](reference/concurrent-unordered-map-class.md#load_factor)
   :::column-end:::
   :::column span="":::
      [`max_load_factor`](reference/concurrent-unordered-map-class.md#max_load_factor)
   :::column-end:::
   :::column span="":::
      [`operator=`](reference/concurrent-unordered-map-class.md#operator_eq)
   :::column-end:::
   :::column span="":::
      [`rehash`](reference/concurrent-unordered-map-class.md#rehash)
   :::column-end:::
:::row-end:::

除了這些方法之外，以開頭的任何方法 `unsafe_` 也不是平行存取安全的。

[[頂端](#top)]

## <a name="concurrent_unordered_multimap-class"></a><a name="unordered_multimap"></a> concurrent_unordered_multimap 類別

[Concurrency：： concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)類別與 `concurrent_unordered_map` 類別非常類似，不同之處在于它可讓多個值對應至相同的索引鍵。 它也與 `concurrent_unordered_map` 下列方式不同：

- [Concurrent_unordered_multimap：： insert](reference/concurrent-unordered-multimap-class.md#insert)方法會傳回反覆運算器，而不是 `std::pair<iterator, bool>` 。

- `concurrent_unordered_multimap`類別不提供任何方法，也不提供 `operator[]` `at` 方法。

下列範例顯示使用的基本結構 `concurrent_unordered_multimap` 。 此範例會在 [' a '、' i '] 範圍中插入字元索引鍵。 `concurrent_unordered_multimap` 讓索引鍵具有多個值。

[!code-cpp[concrt-unordered-multimap-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_3.cpp)]

[[頂端](#top)]

## <a name="concurrent_unordered_set-class"></a><a name="unordered_set"></a> concurrent_unordered_set 類別

[Concurrency：： concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md)類別與 `concurrent_unordered_map` 類別非常類似，不同之處在于它會管理值，而不是索引鍵和值組。 `concurrent_unordered_set`類別不提供任何方法，也不提供 `operator[]` `at` 方法。

下列範例顯示使用的基本結構 `concurrent_unordered_set` 。 此範例會在範圍 [' a '，' i '] 中插入字元值。 您可以安全地平行執行插入。

[!code-cpp[concrt-unordered-set#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_4.cpp)]

[[頂端](#top)]

## <a name="concurrent_unordered_multiset-class"></a><a name="unordered_multiset"></a> concurrent_unordered_multiset 類別

[Concurrency：： concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)類別與 `concurrent_unordered_set` 類別非常類似，不同之處在于它允許重複的值。 它也與 `concurrent_unordered_set` 下列方式不同：

- [Concurrent_unordered_multiset：： insert](reference/concurrent-unordered-multiset-class.md#insert)方法會傳回反覆運算器，而不是 `std::pair<iterator, bool>` 。

- `concurrent_unordered_multiset`類別不提供任何方法，也不提供 `operator[]` `at` 方法。

下列範例顯示使用的基本結構 `concurrent_unordered_multiset` 。 此範例會在範圍 [' a '，' i '] 中插入字元值。 `concurrent_unordered_multiset` 讓值多次發生。

[!code-cpp[concrt-unordered-multiset#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_5.cpp)]

[[頂端](#top)]

## <a name="combinable-class"></a><a name="combinable"></a> 組合類別

[Concurrency：：可組合](../../parallel/concrt/reference/combinable-class.md)類別提供可重複使用的執行緒區域儲存區，可讓您執行更精細的計算，然後將這些計算合併為最終結果。 您可以將 `combinable` 物件視為削減變數。

`combinable`當您有多個執行緒或工作之間共用的資源時，類別會很有用。 `combinable`類別可讓您以無鎖定的方式提供共用資源的存取權，以協助您消除共用狀態。 因此，這個類別會提供使用同步處理機制（例如 mutex）的替代方式，以同步處理多個執行緒的共用資料存取。

### <a name="methods-and-features"></a><a name="combinable-features"></a> 方法和功能

下表顯示類別的一些重要方法 `combinable` 。 如需所有類別方法的詳細資訊 `combinable` ，請參閱可 [組合的類別](../../parallel/concrt/reference/combinable-class.md)。

|方法|描述|
|------------|-----------------|
|[當地](reference/combinable-class.md#local)|抓取與目前線程內容相關聯的本機變數參考。|
|[清楚](reference/combinable-class.md#clear)|從物件移除所有線程區域變數 `combinable` 。|
|[結合](reference/combinable-class.md#combine)<br /><br /> [combine_each](reference/combinable-class.md#combine_each)|使用所提供的組合函式，從所有線程區域計算的集合產生最後的值。|

`combinable`類別是在最後合併結果上參數化的範本類別。 如果您呼叫預設的函式，則樣板 `T` 參數型別必須有預設的函式和複製的函數。 如果 `T` 範本參數類型沒有預設的函式，請呼叫採用初始化函式作為其參數的函式的多載版本。

您可以在 `combinable` 呼叫 [組合](reference/combinable-class.md#combine) 或 [combine_each](reference/combinable-class.md#combine_each) 方法之後，將其他資料儲存在物件中。 您也可以多次呼叫 `combine` 和 `combine_each` 方法。 如果物件中沒有區域值 `combinable` 變更， `combine` 和 `combine_each` 方法會在每次呼叫時產生相同的結果。

### <a name="examples"></a><a name="combinable-examples"></a> 範例

如需如何使用類別的範例 `combinable` ，請參閱下列主題：

- [如何：使用可組合的來改善效能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)

- [如何：使用可組合的組合集合](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)

[[頂端](#top)]

## <a name="related-topics"></a>[相關主題]

[如何：使用平行容器提高效率](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br/>
示範如何使用平行容器，以平行方式有效率地儲存及存取資料。

[如何：使用可組合的來改善效能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br/>
顯示如何使用 `combinable` 類別來消除共用狀態，進而改善效能。

[如何：使用可組合的組合集合](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)<br/>
示範如何使用 `combine` 函數來合併執行緒區域資料集。

[平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
描述 PPL，這會提供命令式程式設計模型，以提升開發並行應用程式的擴充性和易用性。

## <a name="reference"></a>參考

[concurrent_vector 類別](../../parallel/concrt/reference/concurrent-vector-class.md)

[concurrent_queue 類別](../../parallel/concrt/reference/concurrent-queue-class.md)

[concurrent_unordered_map 類別](../../parallel/concrt/reference/concurrent-unordered-map-class.md)

[concurrent_unordered_multimap 類別](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)

[concurrent_unordered_set 類別](../../parallel/concrt/reference/concurrent-unordered-set-class.md)

[concurrent_unordered_multiset 類別](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)

[組合類別](../../parallel/concrt/reference/combinable-class.md)
