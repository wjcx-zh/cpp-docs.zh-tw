---
title: PPL 中的取消
ms.date: 11/19/2018
helpviewer_keywords:
- parallel algorithms, canceling [Concurrency Runtime]
- canceling parallel algorithms [Concurrency Runtime]
- parallel tasks, canceling [Concurrency Runtime]
- cancellation in the PPL
- parallel work trees [Concurrency Runtime]
- canceling parallel tasks [Concurrency Runtime]
ms.assetid: baaef417-b2f9-470e-b8bd-9ed890725b35
ms.openlocfilehash: e85de9a07b625030976e6f03c9e965d34c3134d4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220973"
---
# <a name="cancellation-in-the-ppl"></a>PPL 中的取消

本文件說明取消在平行模式程式庫 (PPL) 中的角色、如何取消平行工作，以及如何判斷平行工作取消的時間。

> [!NOTE]
> 執行階段使用例外狀況處理來實作取消。 請勿在您的程式碼中攔截或處理這些例外狀況。 此外，我們建議您在工作的函式主體中撰寫例外狀況安全的程式碼。 例如，您可以使用資源取得*為初始化*（RAII）模式，以確保在工作主體中擲回例外狀況時，會正確處理資源。 如需使用 RAII 模式清除可取消之工作中的資源的完整範例，請參閱[逐步解說：從使用者介面執行緒中移除工作](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)。

## <a name="key-points"></a>重點

- 取消是合作式的，而且涉及要求取消的程式碼與回應取消的工作兩者之間的協調。

- 可能的話，請使用取消語彙基元來取消工作。 [Concurrency：： cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md)類別會定義解除標記。

- 當您使用解除標記時，請使用[concurrency：： cancellation_token_source：： cancel](reference/cancellation-token-source-class.md#cancel)方法來起始取消，而[concurrency：： cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task)函式則會回應取消。 使用[concurrency：： cancellation_token：： is_canceled](reference/cancellation-token-class.md#is_canceled)方法來檢查是否有任何其他工作已要求取消。

- 取消不會立即發生。 雖然取消工作或工作組時，不會啟動新的工作，但作用中的工作必須檢查並回應取消。

- 以值為基礎的接續會繼承其前項工作的取消語彙基元。 以工作為基礎的接續絕不會繼承其前項工作的語彙基元。

- 當您呼叫接受物件但不想要可取消作業的函式或函式時，請使用[concurrency：： cancellation_token：： none](reference/cancellation-token-class.md#none)方法 `cancellation_token` 。 此外，如果您未將解除標記傳遞給[concurrency：： task](../../parallel/concrt/reference/task-class.md)函數或[concurrency：： create_task](reference/concurrency-namespace-functions.md#create_task)函式，則該工作不會可取消。

## <a name="in-this-document"></a><a name="top"></a>本檔中的

- [平行工作樹狀結構](#trees)

- [取消平行工作](#tasks)

  - [使用取消語彙基元來取消平行工作](#tokens)

  - [使用 cancel 方法來取消平行工作](#cancel)

  - [使用例外狀況來取消平行工作](#exceptions)

- [取消平行演算法](#algorithms)

- [不使用取消的時機](#when)

## <a name="parallel-work-trees"></a><a name="trees"></a>平行工作樹狀結構

PPL 使用工作和工作群組來管理細部的工作和計算。 您可以將工作組嵌套，以形成平行工作的*樹狀*結構。 下圖顯示平行工作樹狀。 在此圖中，`tg1` 和 `tg2` 代表工作群組；`t1`、`t2`、`t3`、`t4` 和 `t5` 代表工作群組執行的工作。

![平行工作樹狀](../../parallel/concrt/media/parallelwork_trees.png "平行工作樹狀")

下列範例顯示在圖中建立樹狀結構時需要的程式碼。 在此範例中， `tg1` 和 `tg2` 是[concurrency：： structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)物件; `t1` 、 `t2` 、 `t3` 、 `t4` 和 `t5` 是[concurrency：： task_handle](../../parallel/concrt/reference/task-handle-class.md)物件。

[!code-cpp[concrt-task-tree#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_1.cpp)]

您也可以使用[concurrency：： task_group](reference/task-group-class.md)類別來建立類似的工作樹狀結構。 [Concurrency：： task](../../parallel/concrt/reference/task-class.md)類別也支援工作樹狀結構的概念。 不過，`task` 樹狀是相依性樹狀。 在 `task` 樹狀結構中，未來工作會在目前工作之後完成。 在工作群組樹狀中，內部工作會在外部工作之前完成。 如需工作和工作組之間差異的詳細資訊，請參閱工作[平行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)處理原則。

[[頂端](#top)]

## <a name="canceling-parallel-tasks"></a><a name="tasks"></a>取消平行工作

有多種方式可取消平行工作。 慣用的方法是使用取消語彙基元。 工作組也支援[concurrency：： task_group：： cancel](reference/task-group-class.md#cancel)方法和[concurrency：： structured_task_group：： cancel](reference/structured-task-group-class.md#cancel)方法。 最後一種方式是在工作的工作函式主體中擲回例外狀況。 無論您選擇哪一個方法，請了解取消不會立即發生。 雖然取消工作或工作組時，不會啟動新的工作，但作用中的工作必須檢查並回應取消。

如需取消平行工作的更多範例，請參閱[逐步解說：使用工作和 XML HTTP 要求連接](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)、[如何：使用取消來中斷平行迴圈](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)，以及[如何：使用例外狀況處理來中斷平行迴圈](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)。

### <a name="using-a-cancellation-token-to-cancel-parallel-work"></a><a name="tokens"></a>使用解除標記來取消平行工作

`task`、`task_group` 和 `structured_task_group` 類別可透過使用取消語彙基元來支援取消。 PPL 會針對此目的定義[concurrency：： cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md)和[concurrency：： cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md)類別。 當您使用取消語彙基元取消工作時，執行階段就不會啟動訂閱這個語彙基元的新工作。 已在作用中的工作可以使用[is_canceled](../../parallel/concrt/reference/cancellation-token-class.md#is_canceled)成員函式來監視解除標記，並在可能時停止。

若要起始取消，請呼叫[concurrency：： cancellation_token_source：： cancel](reference/cancellation-token-source-class.md#cancel)方法。 您回應取消的方式如下：

- 針對 `task` 物件，請使用[concurrency：： cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task)函數。 `cancel_current_task` 會取消目前的工作及任何其以值為基礎的接續。 （它不會取消與工作或其接續相關聯的取消*標記*）。

- 針對工作組和平行演算法，請使用[concurrency：： is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling)函式來偵測取消，並在此函式傳回時，儘快從工作主體傳回 **`true`** 。 (請勿從工作群組呼叫 `cancel_current_task`。)

下列範例顯示工作取消的第一個基本模式。 工作主體偶爾會在迴圈內檢查取消。

[!code-cpp[concrt-task-basic-cancellation#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_2.cpp)]

`cancel_current_task` 函式會擲回；因此，您不需要明確地從目前的迴圈或函式傳回。

> [!TIP]
> 或者，您可以呼叫[concurrency：： interruption_point](reference/concurrency-namespace-functions.md#interruption_point)函式，而不是 `cancel_current_task` 。

當您回應取消時務必要呼叫 `cancel_current_task`，因為它會將工作轉換成已取消的狀態。 如果您提早傳回，而不是呼叫 `cancel_current_task`，則作業會轉換成已完成狀態，並且會執行任何以值為基礎的接續。

> [!CAUTION]
> 永遠不會從您的程式碼擲回 `task_canceled`。 請改為呼叫 `cancel_current_task`。

當工作以已取消的狀態結束時， [concurrency：： task：： get](reference/task-class.md#get)方法會擲回[concurrency：： task_canceled](../../parallel/concrt/reference/task-canceled-class.md)。 （相反地， [concurrency：： task：： wait](reference/task-class.md#wait)會傳回[task_status：：已取消](reference/concurrency-namespace-enums.md#task_group_status)，且不會擲回。）下列範例說明以工作為基礎之接續的行為。 一律會呼叫以工作為基礎的接續，即使前項工作已取消亦然。

[!code-cpp[concrt-task-canceled#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_3.cpp)]

由於以值為基礎的接續會繼承其前項工作的語彙基元 (除非接續是以明確的語彙基元建立)，因此即使前項工作仍在執行中，接續也會立即進入已取消的狀態。 因此，在取消之後，前項工作所擲回的任何例外狀況都不會散佈到接續工作。 取消一律會覆寫前項工作的狀態。 下列範例類似於上一個範例，但說明了以值為基礎的接續的行為。

[!code-cpp[concrt-task-canceled#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_4.cpp)]

> [!CAUTION]
> 如果您未將解除標記傳遞給此函式 `task` 或[concurrency：： create_task](reference/concurrency-namespace-functions.md#create_task)函式，則該工作不會可取消。 此外，您必須傳遞相同的取消語彙基元給任何巢狀工作的建構函式 (也就是在另一個工作主體內建立的工作)，以便同時取消所有工作。

您可能會想要在取消取消語彙基元時，執行任意程式碼。 例如，如果您的使用者在使用者介面上選擇 [**取消**] 按鈕來取消作業，您可以停用該按鈕，直到使用者啟動另一個作業為止。 下列範例會示範如何使用[concurrency：： cancellation_token：： register_callback](reference/cancellation-token-class.md#register_callback)方法來註冊解除標記取消時執行的回呼函式。

[!code-cpp[concrt-task-cancellation-callback#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_5.cpp)]

檔工作[平行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)處理原則會說明以值為基礎和以工作為基礎的接續之間的差異。 如果您未提供 `cancellation_token` 物件給接續工作，接續會以下列方式繼承前項工作的取消語彙基元：

- 以值為基礎的接續一律會繼承前項工作的取消語彙基元。

- 以工作為基礎的接續絕不會繼承前項工作的取消語彙基元。 明確地傳遞取消語彙基元是使得以工作為基礎的接續可取消的唯一方式。

這些行為不會受到錯誤工作 (也就是擲回例外狀況的工作) 影響。 在此情況下，會取消以值為基礎的接續;以工作為基礎的接續不會取消。

> [!CAUTION]
> 在另一項工作中建立的工作 (也就是巢狀工作) 不會繼承父工作的取消語彙基元。 只有以值為基礎的接續才會繼承其前項工作的取消語彙基元。

> [!TIP]
> 當您呼叫接受物件的函式或函式，但不想要可取消作業時，請使用[concurrency：： cancellation_token：： none](reference/cancellation-token-class.md#none)方法 `cancellation_token` 。

您也可以提供取消語彙基元給 `task_group` 或 `structured_task_group` 物件的建構函式。 其中的一個重要環節是子工作群組會繼承這個取消語彙基元。 如需使用[concurrency：： run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token)函式執行呼叫來示範此概念的範例 `parallel_for` ，請參閱本檔稍後的[取消平行演算法](#algorithms)。

[[頂端](#top)]

#### <a name="cancellation-tokens-and-task-composition"></a>取消語彙基元和工作組合

[Concurrency：： when_all](reference/concurrency-namespace-functions.md#when_all)和[concurrency：： when_any](reference/concurrency-namespace-functions.md#when_all)函式可協助您撰寫多個工作來執行常見模式。 本章節描述這些函式如何使用取消語彙基元。

當您提供解除標記給和函式 `when_all` 時 `when_any` ，該函式只會在解除標記取消時，或其中一個參與者工作以已取消狀態結束或擲回例外狀況時取消。

當您未提供取消語彙基元給 `when_all` 函式時，它會從組合整體作業之每個工作繼承取消語彙基元。 `when_all`當任何一個標記取消，而且至少有一個參與者工作尚未啟動或正在執行時，會取消從傳回的工作。 當其中一個工作擲回例外狀況時，就會發生類似的行為-從傳回的工作 `when_all` 會立即取消並出現該例外狀況。

從 `when_any` 函式傳回的工作完成時，執行階段會選擇該工作的取消語彙基元。 如果參與者工作都未在已完成狀態中完成，而且一個或多個工作擲回例外狀況，則其中一項擲回的工作會被選來完成 `when_any`，其語彙基元則會被選為最終工作的語彙基元。 如果多個工作在已完成狀態中完成，從 `when_any` 工作傳回的工作便會在已完成狀態中結束。 執行階段會嘗試挑選已完成的工作，該工作的語彙基元在完成時不是已取消狀態，因此即使其他正在執行的工作可能會在稍後才完成，從 `when_any` 傳回的工作也不會立即取消。

[[頂端](#top)]

### <a name="using-the-cancel-method-to-cancel-parallel-work"></a><a name="cancel"></a>使用 cancel 方法來取消平行工作

[Concurrency：： task_group：： cancel](reference/task-group-class.md#cancel)和[concurrency：： structured_task_group：： cancel](reference/structured-task-group-class.md#cancel)方法會將工作組設為已取消狀態。 在您呼叫 `cancel` 之後，工作群組不會啟動未來工作。 有多個子工作可以呼叫 `cancel` 方法。 已取消的工作會導致[concurrency：： task_group：： wait](reference/task-group-class.md#wait)和[concurrency：： structured_task_group：： wait](reference/structured-task-group-class.md#wait)方法傳回[concurrency：：已取消](reference/concurrency-namespace-enums.md#task_group_status)。

如果工作組已取消，則從每個子工作到執行時間的呼叫都會觸發*中中斷點*，這會導致執行時間擲回並攔截內部例外狀況類型，以取消作用中的工作。 並行執行階段不會定義特定的中斷點；中斷點可以發生在對執行階段的任何呼叫。 執行階段必須處理其所擲回的例外狀況，才能執行取消。 因此，請不要在工作的主體中處理未知例外狀況。

如果子工作會執行耗時的作業，而且不會呼叫執行階段，則其必須定期檢查取消，並及時結束。 下列範例顯示判斷工作何時取消的一個方法。 工作 `t4` 會在遇到錯誤時取消父工作群組。 工作 `t5` 偶爾會呼叫 `structured_task_group::is_canceling` 方法來檢查取消。 如果父工作群組遭到取消，工作 `t5` 會列印訊息並結束。

[!code-cpp[concrt-task-tree#6](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_6.cpp)]

這個範例會檢查工作迴圈的每<sup>個100次</sup>反覆運算上是否有取消。 您檢查取消的頻率取決於您的工作執行的工作量，以及您需要工作回應取消的速度。

如果您無法存取父工作組物件，請呼叫[concurrency：： is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling)函式來判斷是否已取消父工作組。

`cancel` 方法只會影響子工作。 例如，如果您在平行工作樹狀結構的圖形取消工作群組 `tg1`，則樹狀結構中的所有工作 (`t1`、`t2`、`t3`、`t4` 和 `t5`) 都會受到影響。 如果您取消巢狀的工作群組 `tg2`，只有工作 `t4` 和 `t5` 會受到影響。

當您呼叫 `cancel` 方法時，所有的子工作群組也會被取消。 不過，取消不會影響工作群組在平行工作樹狀中的任何父項。 下列範例藉由在平行工作樹狀結構圖上建置來顯示這點。

第一個範例會建立工作 `t4` 的工作函式，這個工作是 `tg2` 工作群組的子系。 工作函式會在迴圈中呼叫 `work` 函式。 如果任何對 `work` 的呼叫失敗，工作便會取消其父工作群組。 這會使工作群組 `tg2` 進入已取消的狀態，但不會取消工作群組 `tg1`。

[!code-cpp[concrt-task-tree#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_7.cpp)]

第二個範例類似於第一個，不同之處在於工作會取消工作群組 `tg1`。 這會影響樹狀中的所有工作 (`t1`、`t2`、`t3`、`t4` 和 `t5`)。

[!code-cpp[concrt-task-tree#3](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_8.cpp)]

`structured_task_group` 類別不是安全執行緒。 因此，呼叫其父系 `structured_task_group` 物件的子工作會產生未指定的行為。 此規則的例外狀況為 `structured_task_group::cancel` 和[concurrency：： structured_task_group：： is_canceling](reference/structured-task-group-class.md#is_canceling)方法。 子工作可以呼叫這些方法來取消父工作群組，並檢查取消。

> [!CAUTION]
> 雖然您可以使用取消語彙基元來取消工作群組所執行的工作，且此工作群組是執行作為 `task` 物件的子系，但您不能使用 `task_group::cancel` 或 `structured_task_group::cancel` 方法來取消在工作群組中執行的 `task` 物件。

[[頂端](#top)]

### <a name="using-exceptions-to-cancel-parallel-work"></a><a name="exceptions"></a>使用例外狀況來取消平行工作

在取消平行工作樹狀時，使用取消語彙基元和 `cancel` 方法會比例外狀況處理更有效率。 取消語彙基元和 `cancel` 方法使用由上而下的方式取消工作以及任何子工作。 相反地，例外狀況處理則使用由下而上的方式執行，且必須在例外狀況往上傳播時個別取消每一個子工作群組。 例外狀況[處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)主題會說明並行執行階段如何使用例外狀況來傳達錯誤。 不過，並非所有例外狀況都表示發生錯誤。 比方說，搜尋演算法在找到結果時，可能會取消其相關聯的工作。 不過，如先前所述，例外狀況處理的效率會比使用 `cancel` 方法來取消平行工作來得低。

> [!CAUTION]
> 我們建議您只在必要時使用例外狀況取消平行工作。 取消語彙基元和工作群組 `cancel` 方法會更有效率且較不容易出錯。

當您在傳遞給工作群組的工作函式主體中擲回例外狀況時，執行階段會儲存該例外狀況，並將其封送處理至等候工作群組完成的內容。 如同 `cancel` 方法，執行階段會捨棄任何尚未開始的工作，而且不接受新的工作。

第三個範例類似於第二個，不同之處在於工作 `t4` 會擲回例外狀況以取消工作群組 `tg2`。 這個範例會使用 **`try`** - **`catch`** 區塊，在工作組等候子工作完成時，檢查是否有取消 `tg2` 作業。 就像第一個範例，這會使工作群組 `tg2` 進入已取消的狀態，但它並不會取消工作群組 `tg1`。

[!code-cpp[concrt-task-tree#4](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_9.cpp)]

第四個範例使用例外狀況處理來取消整個工作樹狀。 範例會在工作群組 `tg1` 等候子工作完成時攔截例外狀況，而不是在工作群組 `tg2` 等候子工作時。 就像第二個範例，這會導致樹狀結構中的兩個工作群組 `tg1` 和 `tg2` 進入已取消的狀態。

[!code-cpp[concrt-task-tree#5](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_10.cpp)]

因為 `task_group::wait` 和 `structured_task_group::wait` 方法會在子工作擲回例外狀況時擲回，所以您不會收到其傳回值。

[[頂端](#top)]

## <a name="canceling-parallel-algorithms"></a><a name="algorithms"></a>取消平行演算法

PPL 中的平行演算法 (例如 `parallel_for`) 是建置在工作群組上。 因此，您可以使用許多相同的技巧來取消平行演算法。

下列範例說明幾種取消平行演算法的方法。

下列範例使用 `run_with_cancellation_token` 函式來呼叫 `parallel_for` 演算法。 `run_with_cancellation_token` 函式採用取消語彙基元作為引數，並以同步方式呼叫所提供的工作函式。 由於平行演算法是建置在工作上，所以其會繼承父工作的取消語彙基元。 因此，`parallel_for` 可以回應取消。

[!code-cpp[concrt-cancel-parallel-for#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_11.cpp)]

下列範例會使用[concurrency：： structured_task_group：： run_and_wait](reference/structured-task-group-class.md#run_and_wait)方法來呼叫 `parallel_for` 演算法。 `structured_task_group::run_and_wait` 方法會等候所提供的工作完成。 `structured_task_group` 物件可讓工作函式取消工作。

[!code-cpp[concrt-task-tree#7](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_12.cpp)]

此範例會產生下列輸出。

```Output
The task group status is: canceled.
```

下列範例使用例外狀況處理來取消 `parallel_for` 迴圈。 執行階段會封送處理例外狀況至呼叫的內容。

[!code-cpp[concrt-task-tree#9](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_13.cpp)]

此範例會產生下列輸出。

```Output
Caught 50
```

下列範例使用布林值旗標來協調 `parallel_for` 迴圈中的取消。 每項工作都會執行，因為此範例不使用 `cancel` 方法或例外狀況處理來取消整體的工作集。 因此，這項技術可能具有比取消機制更多的額外計算負荷。

[!code-cpp[concrt-task-tree#8](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_14.cpp)]

每一種取消方法都有相較於其他方法的優點。 請選擇適合您特定需求的方法。

[[頂端](#top)]

## <a name="when-not-to-use-cancellation"></a><a name="when"></a>不使用取消的時機

當一群相關工作的每個成員都能及時結束時，使用取消是適當的。 不過，在某些情節中，取消可能不適合您的應用程式。 例如，因為工作取消是合作式的，所以如果任何個別的工作受阻，整體工作集便不會取消。 例如，如果一項工作尚未開始，但它會解除封鎖另一個使用中的工作，當工作群組取消時，它便不會開始。 這可能會導致應用程式中發生死結。 第二個可能不適合使用取消的範例是，當工作已取消，但其子工作會執行很重要的作業 (例如釋放資源) 時。 由於取消父工作時會取消整體的工作集，因此將不會執行該作業。 如需說明這點的範例，請參閱平行模式程式庫主題的最佳做法中的[瞭解取消和例外狀況處理如何影響物件銷毀](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction)一節。

[[頂端](#top)]

## <a name="related-topics"></a>相關主題

|標題|說明|
|-----------|-----------------|
|[如何：使用取消來中斷平行迴圈](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)|顯示如何使用取消來實作平行搜尋演算法。|
|[如何：使用例外狀況處理來中斷平行迴圈](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|顯示如何使用 `task_group` 類別來撰寫基本樹狀的搜尋演算法。|
|[例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|描述執行階段如何處理工作群組、輕量型工作和非同步代理程式所擲回的例外狀況，以及如何回應您的應用程式中的例外狀況。|
|[工作平行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|描述工作如何與工作群組產生關聯，以及如何在應用程式中使用非結構化和結構化工作。|
|[平行演算法](../../parallel/concrt/parallel-algorithms.md)|描述平行演算法，這會同時對資料集合執行工作。|
|[平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|提供平行模式程式庫的總覽。|

## <a name="reference"></a>參考

[task 類別（並行執行階段）](../../parallel/concrt/reference/task-class.md)

[cancellation_token_source 類別](../../parallel/concrt/reference/cancellation-token-source-class.md)

[cancellation_token 類別](../../parallel/concrt/reference/cancellation-token-class.md)

[task_group 類別](reference/task-group-class.md)

[structured_task_group 類別](../../parallel/concrt/reference/structured-task-group-class.md)

[parallel_for 函式](reference/concurrency-namespace-functions.md#parallel_for)
