---
title: "平行容器和物件 | Microsoft Docs"
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
  - "平行物件"
  - "平行容器"
  - "並行容器"
ms.assetid: 90ab715c-29cd-48eb-8e76-528619aab466
caps.latest.revision: 34
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 34
---
# 平行容器和物件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

平行模式程式庫 (PPL) 包括數個容器和物件，提供安全執行緒存取其項目。  
  
 A *並行容器* 提供並行安全存取最重要的作業。 這些容器的功能類似於所提供的標準範本庫 (STL)。 例如， [concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) 類別類似於 [std:: vector](../../standard-library/vector-class.md) 類別，但是 `concurrent_vector` 類別可讓您新增項目，以平行方式。 當您需要讀取和寫入存取權的相同容器的平行程式碼時，請使用並行的容器。  
  
 A *並行物件* 同時元件之間共用。 計算的平行的並行物件狀態的處理序會產生相同的結果，以另一個處理程序，會以序列方式計算相同的狀態。  [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) 類別是一種並行的物件類型。  `combinable` 類別可讓您以平行方式，執行計算，然後再結合這些計算成最後的結果。 您會使用同步處理機制，比方說，mutex，以同步存取共用的變數或資源時，請使用並行的物件。  
  
##  <a name="a-nametopa-sections"></a><a name="top"></a> 區段  
 本主題說明下列平行容器和詳細資料中的物件。  
  
 並行容器︰  
  
-   [concurrent_vector 類別](#vector)  
  
    -   [並行向量之間的差異和向量](#vector-differences)  
  
    -   [並行安全作業](#vector-safety)  
  
    -   [例外狀況安全](#vector-exceptions)  
  
-   [concurrent_queue 類別](#queue)  
  
    -   [Concurrent_queue 之間的差異和佇列](#queue-differences)  
  
    -   [並行安全作業](#queue-safety)  
  
    -   [迭代器支援](#queue-iterators)  
  
-   [concurrent_unordered_map 類別](#unordered_map)  
  
    -   [Concurrent_unordered_map 之間的差異和 unordered_map](#map-differences)  
  
    -   [並行安全作業](#map-safety)  
  
-   [concurrent_unordered_multimap 類別](#unordered_multimap)  
  
-   [concurrent_unordered_set 類別](#unordered_set)  
  
-   [concurrent_unordered_multiset 類別](#unordered_multiset)  
  
 並行的物件︰  
  
-   [combinable 類別](#combinable)  
  
    -   [方法和功能](#combinable-features)  
  
    -   [範例](#combinable-examples)  
  
##  <a name="a-namevectora-concurrentvector-class"></a><a name="vector"></a> concurrent_vector 類別  
  [Concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) 類別是序列容器類別，就像 [std:: vector](../../standard-library/vector-class.md) 類別中，可讓您隨機存取其項目。  `concurrent_vector` 類別可讓並行安全附加和項目存取作業。 附加作業不會使失效現有指標或迭代器。 迭代器存取和周遊作業也是並行安全。  
  
###  <a name="a-namevector-differencesa-differences-between-concurrentvector-and-vector"></a><a name="vector-differences"></a> 並行向量之間的差異和向量  
  `concurrent_vector` 類別非常類似 `vector` 類別。 項目存取附加迭代器存取作業的複雜度 `concurrent_vector` 物件所做的相同 `vector` 物件。 下列各點說明 where `concurrent_vector` 不同於 `vector`:  
  
-   附加項目存取、 迭代器存取和迭代器周遊作業上 `concurrent_vector` 物件是並行安全。  
  
-   您可以將項目只能加入結尾 `concurrent_vector` 物件。  `concurrent_vector` 類別不提供 `insert` 方法。  
  
-   A `concurrent_vector` 物件不會使用 [移動語意](../../cpp/rvalue-reference-declarator-amp-amp.md) 當您附加到其中。  
  
-    `concurrent_vector` 類別不提供 `erase` 或 `pop_back` 方法。 如同 `vector`, ，使用 [清除](../Topic/concurrent_vector::clear%20Method.md) 方法以移除所有項目從 `concurrent_vector` 物件。  
  
-    `concurrent_vector` 類別不會儲存其項目連續記憶體中。 因此，您無法使用 `concurrent_vector` 類別中，您可以使用陣列的所有方法。 例如，針對名為的變數 `v` 型別的 `concurrent_vector`, ，運算式 `&v[0]+2` 會產生未定義的行為。  
  
-    `concurrent_vector` 類別會定義 [grow_by](../Topic/concurrent_vector::grow_by%20Method.md) 和 [grow_to_at_least](../Topic/concurrent_vector::grow_to_at_least%20Method.md) 方法。 這些方法類似於 [調整](../Topic/concurrent_vector::resize%20Method.md) 方法，不同之處在於它們是並行安全。  
  
-   A `concurrent_vector` 物件不會不重新配置其項目時附加到它，或調整其大小。 這可讓現有的指標和迭代器，並行作業期間保持有效。  
  
-   執行階段不會定義的特殊的版本 `concurrent_vector` 類型 `bool`。  
  
###  <a name="a-namevector-safetya-concurrency-safe-operations"></a><a name="vector-safety"></a> 並行安全作業  
 所有方法，將附加至或增加的大小 `concurrent_vector` 物件，或存取中的項目 `concurrent_vector` 物件，都是並行安全。 此規則的例外狀況是 `resize` 方法。  
  
 下表顯示常見的 `concurrent_vector` 方法和運算子的並行安全。  
  
||||  
|-|-|-|  
|[在](../Topic/concurrent_vector::at%20Method.md)|[結束](../Topic/concurrent_vector::end%20Method.md)|[運算子 &#91; & #93。](../Topic/concurrent_vector::operatorOperator.md)|  
|[開始](../Topic/concurrent_vector::begin%20Method.md)|[前端](../Topic/concurrent_vector::front%20Method.md)|[push_back](../Topic/concurrent_vector::push_back%20Method.md)|  
|[上一步]](../Topic/concurrent_vector::back%20Method.md)|[grow_by](../Topic/concurrent_vector::grow_by%20Method.md)|[rbegin](../Topic/concurrent_vector::rbegin%20Method.md)|  
|[容量](../Topic/concurrent_vector::capacity%20Method.md)|[grow_to_at_least](../Topic/concurrent_vector::grow_to_at_least%20Method.md)|[rend](../Topic/concurrent_vector::rend%20Method.md)|  
|[空白](../Topic/concurrent_vector::empty%20Method.md)|[max_size](../Topic/concurrent_vector::max_size%20Method.md)|[大小](../Topic/concurrent_vector::size%20Method.md)|  
  
 作業的執行階段提供的 STL、 相容性，例如 `reserve`, ，不是並行安全。 下表顯示常用的方法和運算子不是並行安全。  
  
|||  
|-|-|  
|[指派](../Topic/concurrent_vector::assign%20Method.md)|[保留](../Topic/concurrent_vector::reserve%20Method.md)|  
|[清除](../Topic/concurrent_vector::clear%20Method.md)|[調整大小](../Topic/concurrent_vector::resize%20Method.md)|  
|[運算子 =](../Topic/concurrent_vector::operator=%20Operator.md)|[shrink_to_fit](../Topic/concurrent_vector::shrink_to_fit%20Method.md)|  
  
 修改現有的項目值的作業不是並行安全。 使用同步物件，例如 [reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) ，同步處理並行讀取和寫入作業的相同項目物件。 如需同步處理物件的詳細資訊，請參閱 [同步處理資料結構](../../parallel/concrt/synchronization-data-structures.md)。  
  
 當您轉換現有的程式碼使用 `vector` 使用 `concurrent_vector`, ，並行作業可能會導致您的應用程式，若要變更的行為。 例如，請考慮下列程式同時執行兩項工作的 `concurrent_vector` 物件。 第一項工作會將附加的額外項目 `concurrent_vector` 物件。 第二項工作會計算總和的同一個物件中的所有項目。  
  
 [!code-cpp[concrt-vector-safety#1](../../parallel/concrt/codesnippet/CPP/parallel-containers-and-objects_1.cpp)]  
  
 雖然 `end` 方法是並行安全，同時呼叫 [push_back](../Topic/concurrent_vector::push_back%20Method.md) 方法會導致所傳回的值 `end` 變更。 迭代器周遊的項目數是不定的。 因此，此程式可以執行它每次產生不同的結果。  
  
###  <a name="a-namevector-exceptionsa-exception-safety"></a><a name="vector-exceptions"></a> 例外狀況安全  
 如果成長或指派作業會擲回例外狀況，狀態 `concurrent_vector` 物件就會變成無效。 行為 `concurrent_vector` 處於無效狀態的物件未定義，除非另外註明否則。 不過，解構函式一律釋放的記憶體配置的物件，即使物件是處於無效狀態。  
  
 這些向量的項目資料型別 `T`, ，必須符合下列需求。 否則，行為 `concurrent_vector` 是未定義的類別。  
  
-   解構函式不一定會擲回。  
  
-   如果預設值或複製建構函式擲回，解構函式不能使用宣告 `virtual` 關鍵字且必須正確地使用零初始化記憶體。  
  
 [[靠上](#top)]  
  
##  <a name="a-namequeuea-concurrentqueue-class"></a><a name="queue"></a> concurrent_queue 類別  
  [Concurrency::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) 類別，就像是 [std::queue](../../standard-library/queue-class.md) 類別中，可讓您存取其前方，並傳回項目。  `concurrent_queue` 類別可讓並行安全加入佇列，並清除佇列作業。  `concurrent_queue` 類別也提供不是並行安全的迭代器支援。  
  
###  <a name="a-namequeue-differencesa-differences-between-concurrentqueue-and-queue"></a><a name="queue-differences"></a> Concurrent_queue 之間的差異和佇列  
  `concurrent_queue` 類別非常類似 `queue` 類別。 下列各點說明 where `concurrent_queue` 不同於 `queue`:  
  
-   在佇列中清除佇列作業上和 `concurrent_queue` 物件是並行安全。  
  
-    `concurrent_queue` 類別會提供不是並行安全的迭代器支援。  
  
-    `concurrent_queue` 類別不提供 `front` 或 `pop` 方法。  `concurrent_queue` 類別取代了這些方法，藉由定義 [try_pop](../Topic/concurrent_queue::try_pop%20Method.md) 方法。  
  
-    `concurrent_queue` 類別不提供 `back` 方法。 因此，您不能參考佇列的末端。  
  
-    `concurrent_queue` 類別提供 [unsafe_size](../Topic/concurrent_queue::unsafe_size%20Method.md) 方法，而不是 `size` 方法。  `unsafe_size` 方法不是並行安全。  
  
###  <a name="a-namequeue-safetya-concurrency-safe-operations"></a><a name="queue-safety"></a> 並行安全作業  
 所有方法來加入佇列或清除佇列從 `concurrent_queue` 物件是並行安全。  
  
 下表顯示常見的 `concurrent_queue` 方法和運算子的並行安全。  
  
|||  
|-|-|  
|[空白](../Topic/concurrent_queue::empty%20Method.md)|[推播](../Topic/concurrent_queue::push%20Method.md)|  
|[get_allocator](../Topic/concurrent_queue::get_allocator%20Method.md)|[try_pop](../Topic/concurrent_queue::try_pop%20Method.md)|  
  
 雖然 `empty` 方法是並行安全，並行作業可能會導致佇列成長或壓縮之前 `empty` 方法會傳回。  
  
 下表顯示常用的方法和運算子不是並行安全。  
  
|||  
|-|-|  
|[清除](../Topic/concurrent_queue::clear%20Method.md)|[unsafe_end](../Topic/concurrent_queue::unsafe_end%20Method.md)|  
|[unsafe_begin](../Topic/concurrent_queue::unsafe_begin%20Method.md)|[unsafe_size](../Topic/concurrent_queue::unsafe_size%20Method.md)|  
  
###  <a name="a-namequeue-iteratorsa-iterator-support"></a><a name="queue-iterators"></a> 迭代器支援  
  `concurrent_queue` 提供不是並行安全的迭代器。 我們建議您只用於偵錯使用這些迭代器。  
  
 A `concurrent_queue` 迭代器周遊正向方向的項目。 下表將顯示每個迭代器支援的運算子。  
  
|運算子|說明|  
|--------------|-----------------|  
|[operator + +](http://msdn.microsoft.com/zh-tw/4cfdd07e-927a-42f8-aaa0-d6881687f413)|前移到下一個項目在佇列中。 這個運算子多載之後可提供前置遞增和後置遞增語意 （semantics）。|  
|[運算子 *](http://msdn.microsoft.com/zh-tw/a0e671fc-76e6-4fb4-b95c-ced4dd2b2017)|擷取目前項目的參考。|  
|[-> 運算子](http://msdn.microsoft.com/zh-tw/41fa393d-ae1e-4a38-bb4b-19e8df709ca9)|擷取目前項目的指標。|  
  
 [[靠上](#top)]  
  
##  <a name="a-nameunorderedmapa-concurrentunorderedmap-class"></a><a name="unordered_map"></a> concurrent_unordered_map 類別  
  [HYPERLINK"file:///C:\\\Users\\\thompet\\\AppData\\\Local\\\Temp\\\DxEditor\\\DduePreview\\\Default\\\798d7037-df37-4310-858b-6f590bbf6ebf\\\HTM\\\html\\\a217b4ac-af2b-4d41-94eb-09a75ee28622"concurrency::concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md) 類別是關聯的容器類別，就像 [unordered_map](../../standard-library/unordered-map-class.md) 類別，可控制不同長度序列型別的項目 [std:: initializer_list \< const 金鑰、 Ty >](../../standard-library/pair-structure.md)。 將視為未排序的對應，您可以新增使用索引鍵和值組，或依索引鍵查閱值的字典。 您有多個執行緒或必須同時存取共用的容器、 中、 插入或更新其工作時，此類別會很有用的。  
  
 下列範例顯示使用的基本結構 `concurrent_unordered_map`。 這個範例會將範圍 ['a'、 ' i'] 中的字元按鍵。 因為尚無法確定作業的順序，每個索引鍵的最終值也是不明。 不過，它是安全地以平行方式執行插入。  
  
 [!code-cpp[concrt-unordered-map-structure#1](../../parallel/concrt/codesnippet/CPP/parallel-containers-and-objects_2.cpp)]  
  
 如需範例，會使用 `concurrent_unordered_map` 執行對應和減少作業以平行方式，請參閱 [How to︰ 執行對應和減少作業以平行方式](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)。  
  
###  <a name="a-namemap-differencesa-differences-between-concurrentunorderedmap-and-unorderedmap"></a><a name="map-differences"></a> Concurrent_unordered_map 之間的差異和 unordered_map  
  `concurrent_unordered_map` 類別非常類似 `unordered_map` 類別。 下列各點說明 where `concurrent_unordered_map` 不同於 `unordered_map`:  
  
-    `erase`, ，`bucket`, ，`bucket_count`, ，和 `bucket_size` 方法命名 `unsafe_erase`, ，`unsafe_bucket`, ，`unsafe_bucket_count`, ，和 `unsafe_bucket_size`, 分別。  `unsafe_` 命名慣例表示這些方法不是並行安全。 如需並行安全性的詳細資訊，請參閱 [並行安全作業](#map-safety)。  
  
-   插入作業不會使失效現有指標或迭代器，也不能進行變更的對應已經存在的項目順序。 插入和周遊能同時執行作業。  
  
-   `concurrent_unordered_map` 支援轉送只反覆項目。  
  
-   插入不會使其失效或更新所傳回的迭代器 `equal_range`。 插入可以附加不相等的項目至範圍的結尾。 開始迭代器指向相同的項目。  
  
 為避免發生死結時，沒有方法 `concurrent_unordered_map` 持有鎖定的記憶體配置器、 雜湊函式或其他使用者定義的程式碼呼叫時。 此外，您必須確定雜湊函式一律會評估為相同的值等於索引鍵。 最佳的雜湊函式將索引鍵平均分散在雜湊程式碼空間。  
  
###  <a name="a-namemap-safetya-concurrency-safe-operations"></a><a name="map-safety"></a> 並行安全作業  
  `concurrent_unordered_map` 類別可讓並行安全插入和項目存取作業。 插入作業不會使失效現有指標或迭代器。 迭代器存取和周遊作業也是並行安全。 下表顯示常用 `concurrent_unordered_map` 方法和運算子的並行安全。  
  
|||||  
|-|-|-|-|  
|[在](../Topic/concurrent_unordered_map::at%20Method.md)|`count`|`find`|[key_eq](../Topic/concurrent_unordered_map::key_eq%20Method.md)|  
|`begin`|`empty`|`get_allocator`|`max_size`|  
|`cbegin`|`end`|`hash_function`|[運算子 &#91; & #93。](../Topic/concurrent_unordered_map::operatorOperator.md)|  
|`cend`|`equal_range`|[插入](../Topic/concurrent_unordered_map::insert%20Method.md)|`size`|  
  
 雖然 `count` 可以安全地呼叫方法，從並行執行的執行緒，不同的執行緒可以接收不同的結果，如果新的值同時插入至容器。  
  
 下表顯示常用的方法並不是並行安全的運算子。  
  
||||  
|-|-|-|  
|`clear`|`max_load_factor`|`rehash`|  
|`load_factor`|[運算子 =](../Topic/concurrent_unordered_map::operator=%20Operator.md)|[交換](../Topic/concurrent_unordered_map::swap%20Method.md)|  
  
 這些方法，除了任何方法的開頭 `unsafe_` 也不是並行安全。  
  
 [[靠上](#top)]  
  
##  <a name="a-nameunorderedmultimapa-concurrentunorderedmultimap-class"></a><a name="unordered_multimap"></a> concurrent_unordered_multimap 類別  
  [Concurrency::concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md) 類別非常類似 `concurrent_unordered_map` 類別，但它可讓您將對應至相同的索引鍵的多個值。 它也會不同於 `concurrent_unordered_map` 如下︰  
  
-    [Concurrent_unordered_multimap:: insert](../Topic/concurrent_unordered_multimap::insert%20Method.md) 方法會傳回迭代器，而不是 `std::pair<iterator, bool>`。  
  
-    `concurrent_unordered_multimap` 類別不提供 `operator[]` 和 `at` 方法。  
  
 下列範例顯示使用的基本結構 `concurrent_unordered_multimap`。 這個範例會將範圍 ['a'、 ' i'] 中的字元按鍵。 `concurrent_unordered_multimap` 可讓擁有多個值的索引鍵。  
  
 [!code-cpp[concrt-unordered-multimap-structure#1](../../parallel/concrt/codesnippet/CPP/parallel-containers-and-objects_3.cpp)]  
  
 [[靠上](#top)]  
  
##  <a name="a-nameunorderedseta-concurrentunorderedset-class"></a><a name="unordered_set"></a> concurrent_unordered_set 類別  
  [Concurrency::concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md) 類別非常類似 `concurrent_unordered_map` 類別不同之處在於它管理而不是索引鍵 / 值組的值。  `concurrent_unordered_set` 類別不提供 `operator[]` 和 `at` 方法。  
  
 下列範例顯示使用的基本結構 `concurrent_unordered_set`。 這個範例會將範圍 ['a'、 ' i'] 中的字元值。 它是安全地以平行方式執行插入。  
  
 [!code-cpp[concrt-unordered-set#1](../../parallel/concrt/codesnippet/CPP/parallel-containers-and-objects_4.cpp)]  
  
 [[靠上](#top)]  
  
##  <a name="a-nameunorderedmultiseta-concurrentunorderedmultiset-class"></a><a name="unordered_multiset"></a> concurrent_unordered_multiset 類別  
  [Concurrency::concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md) 類別非常類似 `concurrent_unordered_set` 類別，但它可讓您重複的值。 它也會不同於 `concurrent_unordered_set` 如下︰  
  
-    [Concurrent_unordered_multiset:: insert](../Topic/concurrent_unordered_multiset::insert%20Method.md) 方法會傳回迭代器，而不是 `std::pair<iterator, bool>`。  
  
-    `concurrent_unordered_multiset` 類別不提供 `operator[]` 和 `at` 方法。  
  
 下列範例顯示使用的基本結構 `concurrent_unordered_multiset`。 這個範例會將範圍 ['a'、 ' i'] 中的字元值。 `concurrent_unordered_multiset` 讓您的值發生多次。  
  
 [!code-cpp[concrt-unordered-multiset#1](../../parallel/concrt/codesnippet/CPP/parallel-containers-and-objects_5.cpp)]  
  
 [[靠上](#top)]  
  
##  <a name="a-namecombinablea-combinable-class"></a><a name="combinable"></a> combinable 類別  
  [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) 類別會提供可重複使用、 執行緒區域儲存區，讓您執行更細緻的計算，然後再將這些運算合併成最終的結果。 您可以將 `combinable` 物件視為削減變數。  
  
  `combinable` 類別就很有用，當您有數個執行緒或工作之間共用的資源。  `combinable` 類別可協助您排除共用的狀態，藉由無鎖定的方式提供共用資源的存取權。 因此，這個類別會提供替代同步處理機制，比方說，mutex，來同步處理來自多個執行緒存取共用資料。  
  
###  <a name="a-namecombinable-featuresa-methods-and-features"></a><a name="combinable-features"></a> 方法和功能  
 下表顯示一些重要的方法 `combinable` 類別。 如需有關所有 `combinable` 類別方法，請參閱 [combinable 類別](../../parallel/concrt/reference/combinable-class.md)。  
  
|方法|說明|  
|------------|-----------------|  
|[本機](../Topic/combinable::local%20Method.md)|擷取目前的執行緒內容相關聯的本機變數的參考。|  
|[清除](../Topic/combinable::clear%20Method.md)|移除所有的執行緒本機變數，從 `combinable` 物件。|  
|[結合](../Topic/combinable::combine%20Method.md)<br /><br /> [combine_each](../Topic/combinable::combine_each%20Method.md)|會提供的結合函式使用所有執行緒區域計算一組從產生的最後一個值。|  
  
  `combinable` 類別是參數化的最後的合併結果的範本類別。 如果您呼叫預設建構函式 `T` 範本參數的型別必須具有預設建構函式和複製建構函式。 如果 `T` 範本參數的型別沒有預設建構函式，呼叫會做為其參數的初始化函式的建構函式的多載的版本。  
  
 您可以在其他資料儲存 `combinable` 物件之後呼叫 [結合](../Topic/combinable::combine%20Method.md) 或 [combine_each](../Topic/combinable::combine_each%20Method.md) 方法。 您也可以呼叫 `combine` 和 `combine_each` 方法多次。 如果沒有任何本機值 `combinable` 物件的變更， `combine` 和 `combine_each` 方法會產生相同的結果每次呼叫它們。  
  
###  <a name="a-namecombinable-examplesa-examples"></a><a name="combinable-examples"></a> 範例  
 如需有關如何使用範例 `combinable` 類別，請參閱下列主題︰  
  
-   [如何︰ 使用可組合的類別改善效能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)  
  
-   [如何︰ 使用可組合的類別結合集合](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)  
  
 [[靠上](#top)]  
  
## <a name="related-topics"></a>相關主題  
 [如何︰ 使用平行容器提高效率](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)  
 示範如何使用平行容器有效率地儲存和存取資料，以平行方式。  
  
 [如何︰ 使用可組合的類別改善效能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)  
 示範如何使用 `combinable` 類別以消除共用的狀態，進而改善效能。  
  
 [如何︰ 使用可組合的類別結合集合](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)  
 示範如何使用 `combine` 函式來合併資料的執行緒區域集合。  
  
 [平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)  
 說明 PPL 提供命令式程式設計模型，可提升延展性和方便使用性開發並存應用程式。  
  
## <a name="reference"></a>參考資料  
 [concurrent_vector 類別](../../parallel/concrt/reference/concurrent-vector-class.md)  
  
 [concurrent_queue 類別](../../parallel/concrt/reference/concurrent-queue-class.md)  
  
 [concurrent_unordered_map 類別](../../parallel/concrt/reference/concurrent-unordered-map-class.md)  
  
 [concurrent_unordered_multimap 類別](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)  
  
 [concurrent_unordered_set 類別](../../parallel/concrt/reference/concurrent-unordered-set-class.md)  
  
 [concurrent_unordered_multiset 類別](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)  
  
 [combinable 類別](../../parallel/concrt/reference/combinable-class.md)
