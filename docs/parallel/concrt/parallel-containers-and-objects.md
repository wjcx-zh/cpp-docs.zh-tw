---
title: 平行容器和物件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parallel objects
- parallel containers
- concurrent containers
ms.assetid: 90ab715c-29cd-48eb-8e76-528619aab466
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8256a6d49166b5a002a400892f0808706c66eba9
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43212458"
---
# <a name="parallel-containers-and-objects"></a>平行容器和物件
平行模式程式庫 (PPL) 包含數個容器和物件，提供安全執行緒存取其項目。  
  
 A*並行容器*提供並行安全的存取權最重要的作業。 這些容器的功能類似於 c + + 標準程式庫所提供的。 例如， [concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)類別類似於[std:: vector](../../standard-library/vector-class.md)類別，不同之處在於`concurrent_vector`類別可讓您附加以平行方式的項目。 您需要讀取和寫入至相同的容器的權限的平行程式碼時，請使用並行的容器。  
  
 A*並行物件*會同時共用元件。 計算的平行的並行物件狀態的程序會產生相同的結果，以循序計算的相同狀態的另一個處理程序。 [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md)類別是一個範例是並行的物件類型。 `combinable`類別可讓您以平行方式執行計算，然後再結合成最終結果的計算。 否則會使用同步處理機制，比方說，mutex，來同步存取共用的變數或資源時，請使用並行的物件。  
  
##  <a name="top"></a> 章節  
 本主題描述下列平行容器和詳細資料中的物件。  
  
 並行容器：  
  
-   [concurrent_vector 類別](#ctor)  
  
    -   [之間的差異 concurrent_vector 和向量](#ctor)  
  
    -   [並行安全作業](#ctor)  
  
    -   [例外狀況安全](#ctor)  
  
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
  
 並行的物件：  
  
-   [combinable 類別](#combinable)  
  
    -   [方法和功能](#combinable-features)  
  
    -   [範例](#combinable-examples)  
  
##  <a name="vector"></a> concurrent_vector 類別  
 [Concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)類別是序列容器類別，如同[std:: vector](../../standard-library/vector-class.md)類別中，可讓您隨機存取其項目。 `concurrent_vector`類別啟用並行安全附加和項目存取作業。 附加作業不會使無效現有指標或迭代器。 迭代器存取和周遊作業也是並行安全。  
  
###  <a name="vector-differences"></a> 之間的差異 concurrent_vector 和向量  
 `concurrent_vector`類別很類似`vector`類別。 附加、 項目存取及迭代器存取作業的複雜度`concurrent_vector`物件是否相同`vector`物件。 以下說明何處`concurrent_vector`不同於`vector`:  
  
-   附加、 項目存取、 迭代器存取及迭代器周遊作業上`concurrent_vector`物件就會是並行安全。  
  
-   您可以將項目加入至結尾`concurrent_vector`物件。 `concurrent_vector`類別不提供`insert`方法。  
  
-   A`concurrent_vector`物件不會使用[移動語意](../../cpp/rvalue-reference-declarator-amp-amp.md)當您將附加到它。  
  

-   `concurrent_vector`類別不提供`erase`或`pop_back`方法。 如同`vector`，使用[清除](reference/concurrent-vector-class.md#clear)方法來移除所有項目從`concurrent_vector`物件。  
  
-   `concurrent_vector`類別不會儲存其項目連續記憶體中。 因此，您無法使用`concurrent_vector`類別中，您可以使用陣列的所有方法。 例如，對於名為的變數`v`型別的`concurrent_vector`，運算式`&v[0]+2`會產生未定義的行為。  
  
-   `concurrent_vector`類別會定義[grow_by](reference/concurrent-vector-class.md#grow_by)並[grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least)方法。 這些方法類似[調整大小](reference/concurrent-vector-class.md#resize)方法，不同之處在於它們是並行安全。  
  
-   A`concurrent_vector`物件不會不重新放置其項目時附加到它，或調整其大小。 這可讓現有的指標和迭代器，並行作業期間維持有效。  
  
-   執行階段不會定義的特製化的版本`concurrent_vector`型別的`bool`。  
  
###  <a name="vector-safety"></a> 並行安全作業  
 所有的方法，將附加至或增加的大小`concurrent_vector`物件，或存取中的項目`concurrent_vector`物件，是並行安全。 此規則的例外狀況是`resize`方法。  
  
 下表顯示常見`concurrent_vector`方法和運算子，是並行安全。  
  
||||  
|-|-|-|  

|[在](reference/concurrent-vector-class.md#at)|[端](reference/concurrent-vector-class.md#end)|[運算子&#91;&#93;](reference/concurrent-vector-class.md#operator_at)|  
|[開始](reference/concurrent-vector-class.md#begin)|[front](reference/concurrent-vector-class.md#front)|[push_back](reference/concurrent-vector-class.md#push_back)|  
|[上一步](reference/concurrent-vector-class.md#back)|[grow_by](reference/concurrent-vector-class.md#grow_by)|[rbegin](reference/concurrent-vector-class.md#rbegin)|  
|[容量](reference/concurrent-vector-class.md#capacity)|[grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least)|[rend](reference/concurrent-vector-class.md#rend)|  
|[空](reference/concurrent-vector-class.md#empty)|[max_size](reference/concurrent-vector-class.md#max_size)|[大小](reference/concurrent-vector-class.md#size)|  

  
 作業的執行階段提供相容性的 c + + 標準程式庫，例如`reserve`，不是並行安全。 下表顯示常用的方法和不是並行安全的運算子。  
  
|||  
|-|-|  

|[指派](reference/concurrent-vector-class.md#assign)|[保留](reference/concurrent-vector-class.md#reserve)|  
|[清除](reference/concurrent-vector-class.md#clear)|[調整大小](reference/concurrent-vector-class.md#resize)|  
|[運算子 =](reference/concurrent-vector-class.md#operator_eq)|[shrink_to_fit](reference/concurrent-vector-class.md#shrink_to_fit)|  
  
 修改現有的項目值的作業不是並行安全。 使用同步處理物件，例如[reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)物件，同步處理並行讀取和寫入相同的資料元素中的作業。 如需有關同步處理物件的詳細資訊，請參閱[同步處理資料結構](../../parallel/concrt/synchronization-data-structures.md)。  
  
 當您轉換使用的現有程式碼`vector`使用`concurrent_vector`，並行作業可能會導致您的應用程式，若要變更的行為。 例如，請考慮下列程式，同時對兩個工作`concurrent_vector`物件。 第一項工作會將附加的額外項目`concurrent_vector`物件。 第二項工作會計算總和的相同物件中的所有項目。  
  
 [!code-cpp[concrt-vector-safety#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_1.cpp)]  
  

 雖然`end`方法是並行安全的並行呼叫[push_back](reference/concurrent-vector-class.md#push_back)方法會導致所傳回的值`end`變更。 迭代器周遊的項目數為不定。 因此，此程式可以執行它每次產生不同的結果。  
  
###  <a name="vector-exceptions"></a> 例外狀況安全  
 如果在成長或指派作業會擲回的例外狀況的狀態`concurrent_vector`物件會變成無效。 行為`concurrent_vector`處於無效狀態的物件是未定義，除非另外註明否則。 不過，解構函式一律釋放的記憶體配置的物件，即使物件處於無效狀態。  
  
 項目的資料類型的向量， `T`，必須符合下列需求。 否則，行為`concurrent_vector`類別是未定義。  
  
-   解構函式不一定會擲回。  
  
-   如果預設或複製建構函式擲回，解構函式不能使用宣告`virtual`關鍵字和其必須能正確地以零起始的記憶體。  
  
 [[靠上](#top)]  
  
##  <a name="queue"></a> concurrent_queue 類別  
 [Concurrency::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md)類別，就像[std::queue](../../standard-library/queue-class.md)類別中，可讓您存取其前方，並傳回項目。 `concurrent_queue`類別啟用並行安全加入佇列，並清除佇列作業。 `concurrent_queue`類別也會提供不是並行安全的迭代器支援。  
  
###  <a name="queue-differences"></a> Concurrent_queue 之間的差異和佇列  
 `concurrent_queue`類別很類似`queue`類別。 以下說明何處`concurrent_queue`不同於`queue`:  
  
-   加入佇列及清除佇列作業在`concurrent_queue`物件就會是並行安全。  
  
-   `concurrent_queue`類別會提供不是並行安全的迭代器支援。  
  

-   `concurrent_queue`類別不提供`front`或`pop`方法。 `concurrent_queue`類別取代了這些方法，藉由定義[try_pop](reference/concurrent-queue-class.md#try_pop)方法。  
  
-   `concurrent_queue`類別不提供`back`方法。 因此，您不能參考佇列結尾。  
  
-   `concurrent_queue`類別會提供[unsafe_size](reference/concurrent-queue-class.md#unsafe_size)方法，而非`size`方法。 `unsafe_size`方法不是並行安全。  

  
###  <a name="queue-safety"></a> 並行安全作業  
 所有方法來加入佇列或清除佇列從`concurrent_queue`物件就會是並行安全。  
  
 下表顯示常見`concurrent_queue`方法和運算子，是並行安全。  
  
|||  
|-|-|  
|[empty](reference/concurrent-queue-class.md#empty)|[push](reference/concurrent-queue-class.md#push)|  
|[get_allocator](reference/concurrent-queue-class.md#get_allocator)|[try_pop](reference/concurrent-queue-class.md#try_pop)|  


  
 雖然`empty`是並行安全的方法，並行作業可能會造成擴張或縮小之前佇列`empty`方法會傳回。  
  
 下表顯示常用的方法和不是並行安全的運算子。  
  
|||  
|-|-|  
|[clear](reference/concurrent-queue-class.md#clear)|[unsafe_end](reference/concurrent-queue-class.md#unsafe_end)|  
|[unsafe_begin](reference/concurrent-queue-class.md#unsafe_begin)|[unsafe_size](reference/concurrent-queue-class.md#unsafe_size)|  


  
###  <a name="queue-iterators"></a> 迭代器支援  
 `concurrent_queue`提供不是並行安全的迭代器。 我們建議您只用於偵錯使用這些迭代器。  
  
 A`concurrent_queue`迭代器周遊僅會以正向方向的項目。 下表將顯示每個迭代器支援的運算子。  
  
|運算子|描述|  
|--------------|-----------------|  
|[operator++](https://msdn.microsoft.com/4cfdd07e-927a-42f8-aaa0-d6881687f413)|前移到下一個項目在佇列中。 這個運算子會多載，以提供前置遞增和後置遞增的語意。|  
|[operator*](https://msdn.microsoft.com/a0e671fc-76e6-4fb4-b95c-ced4dd2b2017)|擷取目前項目的參考。|  
|[operator->](https://msdn.microsoft.com/41fa393d-ae1e-4a38-bb4b-19e8df709ca9)|擷取目前項目的指標。|  
  
 [[靠上](#top)]  
  
##  <a name="unordered_map"></a> concurrent_unordered_map 類別  
 [HYPERLINK"file:///C:\\\Users\\\thompet\\\AppData\\\Local\\\Temp\\\DxEditor\\\DduePreview\\\Default\\\798d7037-df37-4310-858b-6f590bbf6ebf\\\HTM\\\html\\\a217b4ac-af2b-4d41-94eb-09a75ee28622"concurrency:: concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md)類別關聯容器類別，如同[std:: unordered_map](../../standard-library/unordered-map-class.md)類別中，控制不同長度序列的項目型別的[std:: pair\<const Key，Ty >](../../standard-library/pair-structure.md)。 想像成未排序對應的字典，您可以新增的索引鍵和值組，或依索引鍵查閱值。 當您有多個執行緒或工作，需要同時存取共用的容器，將插入它，或更新時，這個類別就很有用的。  
  
 下列範例示範使用的基本結構`concurrent_unordered_map`。 這個範例會將範圍 ['a'、 ' i'] 中的字元按鍵。 因為作業的順序未定，每個索引鍵的最終值也是未定。 不過，它是安全地以平行方式執行插入作業。  
  
 [!code-cpp[concrt-unordered-map-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_2.cpp)]  
  
 如需使用的範例`concurrent_unordered_map`若要執行對應和縮減作業以平行方式，請參閱[如何： 執行對應和縮減作業，以平行方式](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)。  
  
###  <a name="map-differences"></a> Concurrent_unordered_map 之間的差異和 unordered_map  
 `concurrent_unordered_map`類別很類似`unordered_map`類別。 以下說明何處`concurrent_unordered_map`不同於`unordered_map`:  
  
-   `erase`， `bucket`， `bucket_count`，以及`bucket_size`方法的命名`unsafe_erase`， `unsafe_bucket`， `unsafe_bucket_count`，以及`unsafe_bucket_size`分別。 `unsafe_`命名慣例可讓您指出這些方法不是並行安全。 如需有關並行安全的詳細資訊，請參閱[並行安全作業](#map-safety)。  
  
-   插入作業不會使無效現有指標或迭代器，也不能進行變更已經存在於對應中項目的順序。 插入和周遊作業可以同時出現。  
  
-   `concurrent_unordered_map` 支援轉送只有反覆項目。  
  
-   插入不會使其失效或更新所傳回的迭代器`equal_range`。 插入範圍的結尾可以附加不相等項目。 開始迭代器指向的相等項目。  
  
 為避免發生死結時，沒有方法`concurrent_unordered_map`持有鎖定時的記憶體配置器、 雜湊函式或其他使用者定義的程式碼，它會呼叫。 此外，您必須確定雜湊函式一律評估為相同的值等於索引鍵。 最佳的雜湊函式雜湊程式碼空間，請以一致的方式散發金鑰。  
  
###  <a name="map-safety"></a> 並行安全作業  
 `concurrent_unordered_map`類別可讓並行安全 insert 和項目存取作業。 插入作業不會使無效現有指標或迭代器。 迭代器存取和周遊作業也是並行安全。 下表顯示常用`concurrent_unordered_map`方法和運算子，是並行安全。  
  
|||||  
|-|-|-|-|  
|[at](reference/concurrent-unordered-map-class.md#at)|`count`|`find`|[key_eq](reference/concurrent-unordered-map-class.md#key_eq)|  
|`begin`|`empty`|`get_allocator`|`max_size`|  
|`cbegin`|`end`|`hash_function`|[operator&#91;&#93;](reference/concurrent-unordered-map-class.md#operator_at)|  
|`cend`|`equal_range`|[insert](reference/concurrent-unordered-map-class.md#insert)|`size`|  
  
 雖然`count`可以安全地呼叫方法，從並行執行的執行緒，不同的執行緒可以接收不同的結果，如果新的值同時插入至容器。  
  
 下表顯示常用的方法並不是並行安全的運算子。  
  
||||  
|-|-|-|  
|`clear`|`max_load_factor`|`rehash`|  
|`load_factor`|[operator=](reference/concurrent-unordered-map-class.md#operator_eq) 


  
 除了這些方法，任何方法以開始`unsafe_`也不是並行安全。  
  
 [[靠上](#top)]  
  
##  <a name="unordered_multimap"></a> concurrent_unordered_multimap 類別  
 [Concurrency::concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)類別類似`concurrent_unordered_map`類別不同之處在於它可讓您將對應至相同的索引鍵的多個值。 它也不同於`concurrent_unordered_map`如下：  
  
-   [Concurrent_unordered_multimap:: insert](reference/concurrent-unordered-multimap-class.md#insert)方法會傳回迭代器，而不是`std::pair<iterator, bool>`。  

  
-   `concurrent_unordered_multimap`類別不提供`operator[]`和`at`方法。  
  
 下列範例示範使用的基本結構`concurrent_unordered_multimap`。 這個範例會將範圍 ['a'、 ' i'] 中的字元按鍵。 `concurrent_unordered_multimap` 可讓擁有多個值的索引鍵。  
  
 [!code-cpp[concrt-unordered-multimap-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_3.cpp)]  
  
 [[靠上](#top)]  
  
##  <a name="unordered_set"></a> concurrent_unordered_set 類別  
 [Concurrency::concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md)類別類似`concurrent_unordered_map`類別不同之處在於它會管理而不是索引鍵 / 值組的值。 `concurrent_unordered_set`類別不提供`operator[]`和`at`方法。  
  
 下列範例示範使用的基本結構`concurrent_unordered_set`。 這個範例會將範圍 ['a'、 ' i'] 中的字元值。 它可以安全地以平行方式執行插入作業。  
  
 [!code-cpp[concrt-unordered-set#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_4.cpp)]  
  
 [[靠上](#top)]  
  
##  <a name="unordered_multiset"></a> concurrent_unordered_multiset 類別  
 [Concurrency::concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)類別類似`concurrent_unordered_set`類別不同之處在於它可讓您重複的值。 它也不同於`concurrent_unordered_set`如下：  
  

-   [Concurrent_unordered_multiset:: insert](reference/concurrent-unordered-multiset-class.md#insert)方法會傳回迭代器，而不是`std::pair<iterator, bool>`。  

  
-   `concurrent_unordered_multiset`類別不提供`operator[]`和`at`方法。  
  
 下列範例示範使用的基本結構`concurrent_unordered_multiset`。 這個範例會將範圍 ['a'、 ' i'] 中的字元值。 `concurrent_unordered_multiset` 可讓要出現許多次的值。  
  
 [!code-cpp[concrt-unordered-multiset#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_5.cpp)]  
  
 [[靠上](#top)]  
  
##  <a name="combinable"></a> combinable 類別  
 [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md)類別提供可重複使用的執行緒本機儲存體，可讓您執行細部運算，然後將這些運算合併成最終的結果。 您可以將 `combinable` 物件視為削減變數。  
  
 `combinable`類別就很有用，當您有數個執行緒或工作之間共用的資源。 `combinable`類別可協助您排除共用的狀態，藉由無鎖定的方式提供共用資源的存取權。 因此，這個類別會提供使用同步處理機制，比方說，mutex，來同步處理從多個執行緒存取共用資料的替代方案。  
  
###  <a name="combinable-features"></a> 方法和功能  
 下表顯示一些的重要方法`combinable`類別。 如需所有詳細資訊`combinable`類別的方法，請參閱[combinable 類別](../../parallel/concrt/reference/combinable-class.md)。  
  
|方法|描述|  
|------------|-----------------|  
|[local](reference/combinable-class.md#local)|擷取目前的執行緒內容相關聯的本機變數的參考。|  
|[clear](reference/combinable-class.md#clear)|移除所有的執行緒本機變數，從`combinable`物件。|  
|[combine](reference/combinable-class.md#combine)<br /><br /> [combine_each](reference/combinable-class.md#combine_each)|使用提供的結合函式來產生最終的值集中的所有執行緒區域計算。|  
  
 `combinable`類別是最後的合併結果參數化的範本類別。 如果您呼叫預設建構函式，`T`範本參數類型必須有預設建構函式和複製建構函式。 如果`T`範本參數類型沒有預設建構函式，請呼叫採用的初始化函式，做為其參數的建構函式多載的版本。  
  
 您可以將其他資料儲存`combinable`物件之後呼叫[結合](reference/combinable-class.md#combine)或是[combine_each](reference/combinable-class.md#combine_each)方法。 您也可以呼叫`combine`和`combine_each`方法多次。 如果在沒有區域數值`combinable`物件的變更，`combine`和`combine_each`方法都會產生相同的結果進行呼叫時，每次。  
  
###  <a name="combinable-examples"></a> 範例  
 如需如何使用範例`combinable`類別，請參閱下列主題：  
  
-   [如何：使用 combinable 改善效能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)  
  
-   [如何：使用 combinable 結合集合](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)  
  
 [[靠上](#top)]  
  
## <a name="related-topics"></a>相關主題  
 [如何：使用平行容器提高效率](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)  
 示範如何使用平行容器來有效率地儲存及存取資料，以平行方式。  
  
 [如何：使用 combinable 改善效能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)  
 示範如何使用`combinable`類別以消除共用的狀態，進而改善效能。  
  
 [如何：使用 combinable 結合集合](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)  
 示範如何使用`combine`函式來合併資料的執行緒區域集合。  
  
 [平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)  
 描述 PPL，其提供命令式程式設計模型，可提升延展性和輕鬆使用開發並存應用程式。  
  
## <a name="reference"></a>參考資料  
 [concurrent_vector 類別](../../parallel/concrt/reference/concurrent-vector-class.md)  
  
 [concurrent_queue 類別](../../parallel/concrt/reference/concurrent-queue-class.md)  
  
 [concurrent_unordered_map 類別](../../parallel/concrt/reference/concurrent-unordered-map-class.md)  
  
 [concurrent_unordered_multimap 類別](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)  
  
 [concurrent_unordered_set 類別](../../parallel/concrt/reference/concurrent-unordered-set-class.md)  
  
 [concurrent_unordered_multiset 類別](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)  
  
 [combinable 類別](../../parallel/concrt/reference/combinable-class.md)
