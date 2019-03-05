---
title: 平行模式程式庫中的最佳作法
ms.date: 11/04/2016
helpviewer_keywords:
- Parallel Patterns Library, practices to avoid
- practices to avoid, Parallel Patterns Library
- best practices, Parallel Patterns Library
- Parallel Patterns Library, best practices
ms.assetid: e43e0304-4d54-4bd8-a3b3-b8673559a9d7
ms.openlocfilehash: fc120ecc122678b54c7dd27b95445f523bc114a6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57293611"
---
# <a name="best-practices-in-the-parallel-patterns-library"></a>平行模式程式庫中的最佳作法

本文件說明平行模式程式庫 (PPL) 最有效的用法。 PPL 提供一般用途的容器、物件和演算法來執行細部平行處理原則。

如需有關 PPL 的詳細資訊，請參閱 <<c0> [ 平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)。

##  <a name="top"></a> 章節

本文件包含下列章節：

- [不要平行處理小型迴圈主體](#small-loops)

- [表示在最高層級的平行處理原則](#highest)

- [使用 parallel_invoke 解決和治問題](#divide-and-conquer)

- [使用取消或例外狀況處理來中斷平行迴圈](#breaking-loops)

- [了解如何取消和例外狀況處理會影響對物件解構的](#object-destruction)

- [不在平行迴圈中重複封鎖](#repeated-blocking)

- [不會執行封鎖作業，當您取消平行工作](#blocking)

- [不會寫入共用的資料，在平行迴圈](#shared-writes)

- [盡可能避免偽共用](#false-sharing)

- [請確定變數是有效的工作存留期](#lifetime)

##  <a name="small-loops"></a> 不要平行處理小型迴圈主體

平行處理相對小型迴圈主體時，所造成的相關排程額外負荷可能會超過平行處理的好處。 請參考下列範例，其會在兩個矩陣中各加入一組項目。

[!code-cpp[concrt-small-loops#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_1.cpp)]

每個平行迴圈反覆項目的工作負載太小，無法從平行處理的額外負荷中獲益。 您可以在迴圈主體中執行更多工作，或循序執行迴圈，藉以提高此迴圈的效能。

[[靠上](#top)]

##  <a name="highest"></a> 表示在最高層級的平行處理原則

只平行處理低階程式碼時，您可以引入不會隨處理器數目增加而延展的分岔/聯結建構。 A*分岔 / 聯結*建構中其中一項工作分成較小的平行子任務的工作，並等候這些子任務完成。 每個子任務可以遞迴分割為更多的子任務。

儘管分岔/聯結模型適合用來解決各種問題，在某些情況下，同步處理的額外負荷可能會降低延展性。 例如，請參考下列處理影像資料的循序程式碼。

[!code-cpp[concrt-image-processing-filter#20](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_2.cpp)]

因為每個迴圈反覆項目都是獨立的，所以您可以平行處理大部分的工作，如下列範例所示。 這個範例會使用[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)演算法平行處理外部迴圈。

[!code-cpp[concrt-image-processing-filter#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_3.cpp)]

下列範例會在迴圈中呼叫 `ProcessImage` 函式，藉以說明分岔/聯結建構。 對 `ProcessImage` 的每個呼叫會等到每個子任務都已經完成之後才傳回。

[!code-cpp[concrt-image-processing-filter#21](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_4.cpp)]

如果平行迴圈的每個反覆項目幾乎不執行工作，或者平行迴圈所執行的工作不平衡 (也就是有些迴圈反覆項目比其他迴圈反覆項目所需時間更長)，頻繁分岔和聯結工作所需的排程額外負荷可能會超過平行執行的好處。 此額外負荷會隨處理器數目增加而增加。

若要減少此範例中的排程額外負荷量，您可以先平行處理外部迴圈，然後再平行處理內部迴圈，或者使用另一個平行建構 (例如管線)。 下列範例會修改`ProcessImages`若要使用的函式[concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)演算法平行處理外部迴圈。

[!code-cpp[concrt-image-processing-filter#22](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_5.cpp)]

使用管線，以平行方式執行影像處理的類似範例，請參閱[逐步解說：建立映像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)。

[[靠上](#top)]

##  <a name="divide-and-conquer"></a> 使用 parallel_invoke 解決和治問題

A*和治*問題是一種使用遞迴將工作分為子任務的分岔 / 聯結建構形式。 除了[concurrency:: task_group](reference/task-group-class.md)並[concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)類別，您也可以使用[concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)演算法解決和治問題。 
  `parallel_invoke` 演算法的語法比工作群組物件的語法更簡潔，如果您有固定的平行工作數時，此演算法很實用。

在下列範例中，會示範如何使用 `parallel_invoke` 演算法來實作雙調排序演算法。

[!code-cpp[concrt-parallel-bitonic-sort#12](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_6.cpp)]

為了減少額外負荷，`parallel_invoke` 演算法會在呼叫端內容上執行最後一個工作序列。

如本範例的完整版本，請參閱[How to:使用 parallel_invoke 撰寫平行排序常式](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)。 如需詳細資訊`parallel_invoke`演算法，請參閱 <<c2> [ 平行演算法](../../parallel/concrt/parallel-algorithms.md)。

[[靠上](#top)]

##  <a name="breaking-loops"></a> 使用取消或例外狀況處理來中斷平行迴圈

PPL 提供兩種方式來取消工作群組或平行演算法所執行的平行工作。 其中一種方式是使用所提供的取消機制[concurrency:: task_group](reference/task-group-class.md)並[concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)類別。 另一種方式是在工作的工作函式主體中擲回例外狀況。 在取消平行工作樹狀時，取消機制比例外狀況處理更有效率。 A*平行工作樹狀*是一群相關的工作群組中的某些工作群組會包含其他工作群組。 取消機制會以由上而下的方式取消工作群組及其子工作群組。 相反地，例外狀況處理則使用由下而上的方式執行，且必須在例外狀況往上傳播時個別取消每一個子工作群組。

當您直接使用工作群組物件時，使用[concurrency::task_group::cancel](reference/task-group-class.md#cancel)或是[concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel)方法來取消屬於該工作群組的工作. 若要取消平行演算法 (例如 `parallel_for`，請建立父工作群組並取消該工作群組。 例如，考慮下列函式 `parallel_find_any`，這個函式會在陣列中平行搜尋值。

[!code-cpp[concrt-parallel-array-search#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_7.cpp)]

因為平行演算法使用工作群組，所以其中一個平行反覆項目取消父工作群組時，整體工作就會被取消。 如本範例的完整版本，請參閱[How to:使用取消來中斷平行迴圈](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)。

雖然比起取消機制，用例外狀況處理來取消平行工作比較沒有效率，但有些案例會適合使用例外狀況處理。 例如，下列方法 `for_all` 會以遞迴方式在 `tree` 結構的每個節點上執行工作函式。 在此範例中，`_children`資料成員[std:: list](../../standard-library/list-class.md)包含`tree`物件。

[!code-cpp[concrt-task-tree-search#6](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_8.cpp)]

如果不需要在樹狀的每個項目上呼叫工作函式，`tree::for_all` 方法的呼叫端可以擲回例外狀況。 下列範例顯示 `search_for_value` 函式，這個函式會在提供的 `tree` 物件中搜尋值。 
  `search_for_value` 函式所使用的工作函式會在樹狀結構的目前項目符合所提供的值時擲回例外狀況。 
  `search_for_value` 函式會使用 `try-catch` 區塊來擷取例外狀況並將結果列印至主控台。

[!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_9.cpp)]

如本範例的完整版本，請參閱[How to:使用例外狀況處理來中斷平行迴圈](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)。

更一般的取消和 PPL 所提供的例外狀況處理機制的詳細資訊，請參閱[PPL 中的取消](cancellation-in-the-ppl.md)並[例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。

[[靠上](#top)]

##  <a name="object-destruction"></a> 了解如何取消和例外狀況處理會影響對物件解構的

在平行工作的樹狀結構中，已取消的工作會導致子工作無法執行。 如果其中一項子工作執行的作業，對您的應用程式很重要，例如釋放資源，這可能會造成問題。 此外，工作取消可能會導致例外狀況透過物件解構函式傳播，而在應用程式中造成未定義的行為。

在下列範例中，`Resource` 類別描述資源，而 `Container` 類別描述保存資源的容器。 在其解構函式中，`Container` 類別會在其中兩個 `Resource` 成員上平行呼叫 `cleanup` 方法，然後在其第三個 `Resource` 成員上呼叫 `cleanup` 方法。

[!code-cpp[concrt-parallel-resource-destruction#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_10.h)]

儘管這個模式本身沒有問題，請考慮下列平行執行兩個工作的程式碼。 第一個工作會建立 `Container` 物件，而第二個工作則會取消整體工作。 舉例來說，此範例會使用兩個[concurrency:: event](../../parallel/concrt/reference/event-class.md)物件，確定之後發生取消`Container`建立物件，`Container`取消後，就會終結物件作業就會發生。

[!code-cpp[concrt-parallel-resource-destruction#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_11.cpp)]

這個範例會產生下列輸出：

```Output
Container 1: Freeing resources...Exiting program...
```

這個程式碼範例包含下列問題，可能導致實際行為不同於預期行為：

- 父工作的取消導致子工作，呼叫[concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)，也會一併取消。 因此，不會釋放這兩個資源。

- 父工作的取消導致子工作擲回內部例外狀況。 因為 `Container` 解構函式不會處理此例外狀況，所以例外狀況會向上傳播，而不會釋放第三個資源。

- 子工作所擲回的例外狀況會透過 `Container` 解構函式傳播。 從解構函式擲回會導致應用程式處於未定義的狀態。

我們建議您不要在工作中執行重要作業 (例如釋放資源)，除非確定不會取消這些工作。 此外，也建議您不要使用會在類型解構函式中擲回的執行階段功能。

[[靠上](#top)]

##  <a name="repeated-blocking"></a> 不在平行迴圈中重複封鎖

這類的平行迴圈[concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for)或是[concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)所支配封鎖作業可能會導致執行階段在短時間內建立多個執行緒。

並行執行階段會在工作完成或以合作方式封鎖或讓渡時執行額外工作。 當某個平行迴圈反覆項目封鎖時，執行階段可能會開始另一個反覆項目。 沒有可用的閒置執行緒時，執行階段會建立新的執行緒。

當平行迴圈的主體偶爾封鎖時，此機制有助於發揮整體工作的最大處理能力。 不過，若有許多反覆項目封鎖時，執行階段會建立許多用來執行額外工作的執行緒。 這可能會導致記憶體不足狀況或硬體資源使用率不佳。

請考慮下列範例會呼叫[concurrency:: send](reference/concurrency-namespace-functions.md#send)函式中的每個反覆項目`parallel_for`迴圈。 因為 `send` 會以合作方式封鎖，所以執行階段會在每次呼叫 `send` 時建立新執行緒以執行額外工作。

[!code-cpp[concrt-repeated-blocking#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_12.cpp)]

我們建議您重構程式碼以避免這個模式。 在這個範例中，您可以在循序的 `for` 迴圈中呼叫 `send`，藉以避免建立額外的執行緒。

[[靠上](#top)]

##  <a name="blocking"></a> 不會執行封鎖作業，當您取消平行工作

如果可能的話，不會執行封鎖作業，然後再呼叫[concurrency::task_group::cancel](reference/task-group-class.md#cancel)或是[concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel)方法來取消平行工作。

當工作執行合作式封鎖作業時，執行階段可以在第一個工作等候資料的同時，執行其他工作。 當等候的工作解除封鎖時，執行階段會重新排定此工作。 執行階段通常會先重新排定最近解除封鎖的工作，然後再重新排定比較久之前解除封鎖的工作。 因此，執行階段可能會在封鎖作業期間排定不必要的工作，這會導致效能降低。 於是，當您在取消平行工作之前執行封鎖作業時，封鎖作業可能會延遲對 `cancel` 的呼叫。 這會導致其他工作執行不必要的工作。

請參閱下列會定義 `parallel_find_answer` 函式的範例，這個函式會在提供的陣列中搜尋符合所提供之述詞函式的項目。 當述詞函式會傳回 **，則為 true**，平行工作函式會建立`Answer`物件，並取消整體工作。

[!code-cpp[concrt-blocking-cancel#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_13.cpp)]


  `new` 運算子執行可能會封鎖的堆積配置。 執行階段會執行其他工作，只有在工作執行合作式封鎖呼叫，例如呼叫時，才[concurrency::critical_section::lock](reference/critical-section-class.md#lock)。

下列範例示範如何防止不必要的工作，因而改善效能。 這個範例會先取消工作群組，然後再配置儲存區給 `Answer` 物件。

[!code-cpp[concrt-blocking-cancel#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_14.cpp)]

[[靠上](#top)]

##  <a name="shared-writes"></a> 不會寫入共用的資料，在平行迴圈

並行執行階段提供許多資料結構，例如[concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)，同步處理共用的資料並行存取。 這些資料結構適合用於許多案例，例如當多個工作不常需要資源共用存取時。

請考慮下列範例使用[concurrency:: parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)演算法並`critical_section`物件來計算中質數的計數[std:: array](../../standard-library/array-class-stl.md)物件。 這個範例不會延展，因為每個執行緒都必須等候存取共用變數 `prime_sum`。

[!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_15.cpp)]

這個範例也會導致效能降低，因為頻繁的封鎖作業實際上會序列化迴圈。 此外，當並行執行階段物件執行封鎖作業時，排程器可能會在第一個執行緒等候資料時，建立其他執行緒以執行其他工作。 如果執行階段因為許多工作正在等候共用資料而建立許多執行緒，應用程式的效能可能會降低或進入資源不足的狀態。

PPL 會定義[concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md)類別，可協助您排除共用的狀態，藉由無鎖定的方式提供共用資源的存取權。 
  `combinable` 類別提供執行緒區域儲存區，可讓您執行細部運算，然後將這些運算合併成最終的結果。 您可以將 `combinable` 物件視為削減變數。

下列範例修改前述範例，改用 `combinable` 物件 (而不是 `critical_section` 物件) 來計算總和。 這個範例會延展，因為每個執行緒都會保存一份自己的區域總和。 這個範例會使用[concurrency::combinable::combine](reference/combinable-class.md#combine)這些區域運算合併成最終結果的方法。

[!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_16.cpp)]

如本範例的完整版本，請參閱[How to:使用 combinable 改善效能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)。 如需詳細資訊`combinable`類別，請參閱[平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)。

[[靠上](#top)]

##  <a name="false-sharing"></a> 盡可能避免偽共用

*虛偽共用*發生於執行於個別處理器的多個並行工作寫入變數位於相同的快取行上。 當一個工作寫入其中一個變數時，兩個變數的快取行皆會失效。 每當快取行失效時，每個處理器必須重新載入此快取行。 因此，偽共用可能會導致應用程式的效能降低。

下列基本範例示範兩個並行工作，每一個都會遞增一個共用計數器變數。

[!code-cpp[concrt-false-sharing#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_17.cpp)]

為了排除這兩個工作之間的資料共用，您可以將範例修改為使用兩個計數器變數。 這個範例會在工作完成後計算最終的計數器值。 不過，這個範例說明偽共用，因為 `count1` 和 `count2` 變數可能位於同一個快取行。

[!code-cpp[concrt-false-sharing#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_18.cpp)]

排除偽共用的一個方式是確定計數器變數位於個別的快取行。 下列範例會將 `count1` 和 `count2` 變數對齊 64 位元組界限。

[!code-cpp[concrt-false-sharing#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_19.cpp)]

這個範例假設記憶體快取大小為 64 位元組或以下。

我們建議您改用[concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md)類別時，您必須共用在工作之間的資料。 
  `combinable` 類別建立執行緒區域變數的方式，使得偽共用比較不可能發生。 如需詳細資訊`combinable`類別，請參閱[平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)。

[[靠上](#top)]

##  <a name="lifetime"></a> 請確定變數是有效的工作存留期

當您將 Lambda 運算式提供給工作群組或平行演算法時，擷取子句指定 Lambda 運算式主體以傳值方式或傳址方式存取封閉範圍中的變數。 當您以傳址方式將變數傳遞給 lambda 運算式時，必須保證該變數的存留期會一直持續到工作完成。

請參閱下列會定義 `object` 類別和 `perform_action` 函式的範例。 
  `perform_action` 函式會建立 `object` 變數，然後以非同步方式在該變數上執行某項動作。 因為工作不保證會在 `perform_action` 函式傳回前完成，所以在工作執行的同時，如果 `object` 變數終結，程式會損毀或表現未指定的行為。

[!code-cpp[concrt-lambda-lifetime#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_20.cpp)]

根據應用程式需求，您可以使用下列其中一個技巧，確保變數在每個工作的整個存留期都維持有效。

下列範例會以傳值方式將 `object` 變數傳遞給工作。 因此，工作會在自己的變數複本上操作。

[!code-cpp[concrt-lambda-lifetime#2](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_21.cpp)]

因為 `object` 變數是以傳值方式傳遞，對此變數的任何狀態變更都不會出現在原始複本中。

下列範例會使用[2&gt;concurrency::task_group::wait&lt;2](reference/task-group-class.md#wait)方法，以確保在工作完成之前`perform_action`函式會傳回。

[!code-cpp[concrt-lambda-lifetime#3](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_22.cpp)]

因為工作現在在函式傳回前完成，所以 `perform_action` 函式不再以非同步方式表現。

下列範例將 `perform_action` 函式修改為可參考 `object` 變數。 呼叫端必須保證 `object` 變數的存留期在工作完成前維持有效。

[!code-cpp[concrt-lambda-lifetime#4](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-parallel-patterns-library_23.cpp)]

您也可以使用指標來控制傳遞給工作群組或平行演算法之物件的存留期。

如需 Lambda 運算式的詳細資訊，請參閱 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)。

[[靠上](#top)]

## <a name="see-also"></a>另請參閱

[並行執行階段最佳做法](../../parallel/concrt/concurrency-runtime-best-practices.md)<br/>
[平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[平行容器和物件](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[平行演算法](../../parallel/concrt/parallel-algorithms.md)<br/>
[PPL 中的取消](cancellation-in-the-ppl.md)<br/>
[例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[逐步解說：建立影像處理網路](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[如何：使用 parallel_invoke 撰寫平行排序常式](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)<br/>
[如何：使用取消中斷平行迴圈](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)<br/>
[如何：使用 combinable 提升效能](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br/>
[非同步代理程式程式庫中的最佳做法](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)<br/>
[並行執行階段中的一般最佳做法](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)
