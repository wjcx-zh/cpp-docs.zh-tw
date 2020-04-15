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
ms.openlocfilehash: 27c0ea3cfcf62060800c1c0b034dde7de6357250
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368498"
---
# <a name="cancellation-in-the-ppl"></a>PPL 中的取消

本文件說明取消在平行模式程式庫 (PPL) 中的角色、如何取消平行工作，以及如何判斷平行工作取消的時間。

> [!NOTE]
> 執行階段使用例外狀況處理來實作取消。 請勿在您的程式碼中攔截或處理這些例外狀況。 此外，我們建議您在工作的函式主體中撰寫例外狀況安全的程式碼。 例如,可以使用*資源獲取初始化*(RAII) 模式,以確保在任務正文中引發異常時正確處理資源。 有關使用 RAII 模式清理可取消工作中的資源的完整範例,請參閱[演練:從使用者介面線程中移除工作](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)。

## <a name="key-points"></a>重點

- 取消是合作式的，而且涉及要求取消的程式碼與回應取消的工作兩者之間的協調。

- 可能的話，請使用取消語彙基元來取消工作。 [併發::cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md)類定義取消權杖。

- 使用取消權杖時,請使用[併發::cancellation_token_source::取消](reference/cancellation-token-source-class.md#cancel)方法啟動取消,[併發::cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task)函數回應取消。 使用[併發:cancellation_token:is_canceled](reference/cancellation-token-class.md#is_canceled)方法檢查任何其他任務是否請求取消。

- 取消不會立即發生。 如果任務或任務組被取消,則不會啟動新工作,但活動工作必須檢查並回應取消。

- 以值為基礎的接續會繼承其前項工作的取消語彙基元。 以工作為基礎的接續絕不會繼承其前項工作的語彙基元。

- 調用採用`cancellation_token`對象的構造函數或函數,但不希望該操作是可調用的,請使用[併發::cancellation_token::無](reference/cancellation-token-class.md#none)方法。 此外,如果不將取消令牌傳遞給[併發::任務](../../parallel/concrt/reference/task-class.md)構造函數或[併發::create_task](reference/concurrency-namespace-functions.md#create_task)函數,則該任務是無法調用的。

## <a name="in-this-document"></a><a name="top"></a>在本文件中

- [平行工作樹狀結構](#trees)

- [取消平行工作](#tasks)

  - [使用取消語彙基元來取消平行工作](#tokens)

  - [使用 cancel 方法來取消平行工作](#cancel)

  - [使用例外狀況來取消平行工作](#exceptions)

- [取消平行演算法](#algorithms)

- [不使用取消的時機](#when)

## <a name="parallel-work-trees"></a><a name="trees"></a>平行工作樹

PPL 使用工作和工作群組來管理細部的工作和計算。 可以嵌入工作群組以形成並行工作的*樹*。 下圖顯示平行工作樹狀。 在此圖中，`tg1` 和 `tg2` 代表工作群組；`t1`、`t2`、`t3`、`t4` 和 `t5` 代表工作群組執行的工作。

![平行工作樹狀](../../parallel/concrt/media/parallelwork_trees.png "平行工作樹狀")

下列範例顯示在圖中建立樹狀結構時需要的程式碼。 在此示例中,`tg1``tg2`併[發::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)物件;`t1` `t3``t2`、、 和 為[一致:task_handle](../../parallel/concrt/reference/task-handle-class.md)物件。 `t4` `t5`

[!code-cpp[concrt-task-tree#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_1.cpp)]

您還可以使用[併發::task_group](reference/task-group-class.md)類創建類似的工作樹。 [併發::任務](../../parallel/concrt/reference/task-class.md)類還支援工作樹的概念。 不過，`task` 樹狀是相依性樹狀。 在 `task` 樹狀結構中，未來工作會在目前工作之後完成。 在工作群組樹狀中，內部工作會在外部工作之前完成。 有關工作和工作組之間的差異的詳細資訊,請參閱[工作並行性](../../parallel/concrt/task-parallelism-concurrency-runtime.md)。

【[頂端](#top)

## <a name="canceling-parallel-tasks"></a><a name="tasks"></a>取消並行任務

有多種方式可取消平行工作。 慣用的方法是使用取消語彙基元。 任務組還支援[併發::task_group:::取消](reference/task-group-class.md#cancel)方法和[併發::structured_task_group::取消](reference/structured-task-group-class.md#cancel)方法。 最後一種方式是在工作的工作函式主體中擲回例外狀況。 無論您選擇哪一個方法，請了解取消不會立即發生。 如果任務或任務組被取消,則不會啟動新工作,但活動工作必須檢查並回應取消。

有關取消並行任務的更多範例,請參閱[演練:使用工作和 XML HTTP 請求進行連線](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md),[如何:使用取消從並行循環中斷](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md),以及如何[:使用異常處理從並行迴圈中斷](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)。

### <a name="using-a-cancellation-token-to-cancel-parallel-work"></a><a name="tokens"></a>使用取消權杖取消並行工作

`task`、`task_group` 和 `structured_task_group` 類別可透過使用取消語彙基元來支援取消。 PPL 為此定義[併發:::cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md)[和併發:cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md)類。 當您使用取消語彙基元取消工作時，執行階段就不會啟動訂閱這個語彙基元的新工作。 已處於活動狀態的工作可以使用[is_canceled](../../parallel/concrt/reference/cancellation-token-class.md#is_canceled)成員函數監視取消令牌並在可以時停止。

要啟動取消,請調用[併發:cancellation_token_source::取消](reference/cancellation-token-source-class.md#cancel)方法。 您回應取消的方式如下：

- 對於`task`物件,請使用[併發::cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task)函數。 `cancel_current_task` 會取消目前的工作及任何其以值為基礎的接續。 ( 沒有取消與工作或其延續關聯的取消*權杖*。

- 對於任務組和並行演演演算法,使用[併發:is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling)函數檢測取消,並在函數返回**true**時儘快從任務正文返回。 (請勿從工作群組呼叫 `cancel_current_task`。)

下列範例顯示工作取消的第一個基本模式。 工作主體偶爾會在迴圈內檢查取消。

[!code-cpp[concrt-task-basic-cancellation#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_2.cpp)]

`cancel_current_task` 函式會擲回；因此，您不需要明確地從目前的迴圈或函式傳回。

> [!TIP]
> 或者,您可以調用[併發::interruption_point](reference/concurrency-namespace-functions.md#interruption_point)函`cancel_current_task`數, 而不是 。

當您回應取消時務必要呼叫 `cancel_current_task`，因為它會將工作轉換成已取消的狀態。 如果您提早傳回，而不是呼叫 `cancel_current_task`，則作業會轉換成已完成狀態，並且會執行任何以值為基礎的接續。

> [!CAUTION]
> 永遠不會從您的程式碼擲回 `task_canceled`。 請改為呼叫 `cancel_current_task`。

當工作以取消狀態結束時,[並發::任務:get](reference/task-class.md#get)方法將併[發:::task_canceled](../../parallel/concrt/reference/task-canceled-class.md)。 (相反,[併發::任務::等待](reference/task-class.md#wait)返回[task_status::取消](reference/concurrency-namespace-enums.md#task_group_status),不引發。下面的示例說明了基於任務的延續的此行為。 一律會呼叫以工作為基礎的接續，即使前項工作已取消亦然。

[!code-cpp[concrt-task-canceled#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_3.cpp)]

由於以值為基礎的接續會繼承其前項工作的語彙基元 (除非接續是以明確的語彙基元建立)，因此即使前項工作仍在執行中，接續也會立即進入已取消的狀態。 因此，在取消之後，前項工作所擲回的任何例外狀況都不會散佈到接續工作。 取消一律會覆寫前項工作的狀態。 下列範例類似於上一個範例，但說明了以值為基礎的接續的行為。

[!code-cpp[concrt-task-canceled#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_4.cpp)]

> [!CAUTION]
> 如果不將取消令牌傳遞給`task`建構函數或[併發:create_task](reference/concurrency-namespace-functions.md#create_task)函數,則該任務是無法調用的。 此外，您必須傳遞相同的取消語彙基元給任何巢狀工作的建構函式 (也就是在另一個工作主體內建立的工作)，以便同時取消所有工作。

您可能會想要在取消取消語彙基元時，執行任意程式碼。 例如,如果使用者在使用者介面上選擇 **「取消」** 按鈕來取消該操作,則可以禁用該按鈕,直到使用者開始另一個操作。 下面的示例演示如何使用[併發::cancellation_token:register_callback](reference/cancellation-token-class.md#register_callback)方法來註冊取消取消令牌時運行的回調函數。

[!code-cpp[concrt-task-cancellation-callback#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_5.cpp)]

文件[「任務並行性」](../../parallel/concrt/task-parallelism-concurrency-runtime.md)解釋了基於值的延續和基於任務的延續之間的區別。 如果您未提供 `cancellation_token` 物件給接續工作，接續會以下列方式繼承前項工作的取消語彙基元：

- 以值為基礎的接續一律會繼承前項工作的取消語彙基元。

- 以工作為基礎的接續絕不會繼承前項工作的取消語彙基元。 明確地傳遞取消語彙基元是使得以工作為基礎的接續可取消的唯一方式。

這些行為不會受到錯誤工作 (也就是擲回例外狀況的工作) 影響。 在這種情況下,基於值的延續將被取消;因此,將取消基於值的延續。不會取消基於任務的延續。

> [!CAUTION]
> 在另一項工作中建立的工作 (也就是巢狀工作) 不會繼承父工作的取消語彙基元。 只有以值為基礎的接續才會繼承其前項工作的取消語彙基元。

> [!TIP]
> 調用採用`cancellation_token`對象的構造函數或函數時,請使用[併發::cancellation_token::無](reference/cancellation-token-class.md#none)方法,並且不希望該操作是可調用的。

您也可以提供取消語彙基元給 `task_group` 或 `structured_task_group` 物件的建構函式。 其中的一個重要環節是子工作群組會繼承這個取消語彙基元。 有關使用[並發::run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token)函數來執行`parallel_for`呼叫 來展示此概念的範例,請參閱本文件後面的[取消並行演演算法](#algorithms)。

【[頂端](#top)

#### <a name="cancellation-tokens-and-task-composition"></a>取消語彙基元和工作組合

[併發::when_all](reference/concurrency-namespace-functions.md#when_all)[和併發::when_any](reference/concurrency-namespace-functions.md#when_all)函數可以説明您組成多個任務以實現通用模式。 本章節描述這些函式如何使用取消語彙基元。

當您向`when_all``when_any`和函數提供取消令牌時,該函數僅在取消該取消令牌或其中一個參與者任務以已取消狀態結束或引發異常時才取消。

當您未提供取消語彙基元給 `when_all` 函式時，它會從組合整體作業之每個工作繼承取消語彙基元。 當其中任何一個令牌`when_all`被取消且至少有一個參與者任務尚未啟動或正在運行時,將從返回的任務將被取消。 當其中一個任務引發異常時,將發生類似的行為 -`when_all`返回的任務將立即取消該異常。

從 `when_any` 函式傳回的工作完成時，執行階段會選擇該工作的取消語彙基元。 如果參與者工作都未在已完成狀態中完成，而且一個或多個工作擲回例外狀況，則其中一項擲回的工作會被選來完成 `when_any`，其語彙基元則會被選為最終工作的語彙基元。 如果多個工作在已完成狀態中完成，從 `when_any` 工作傳回的工作便會在已完成狀態中結束。 執行階段會嘗試挑選已完成的工作，該工作的語彙基元在完成時不是已取消狀態，因此即使其他正在執行的工作可能會在稍後才完成，從 `when_any` 傳回的工作也不會立即取消。

【[頂端](#top)

### <a name="using-the-cancel-method-to-cancel-parallel-work"></a><a name="cancel"></a>使用取消方法取消並行工作

[併發::task_group::取消](reference/task-group-class.md#cancel)[和併發::structured_task_group::取消](reference/structured-task-group-class.md#cancel)方法將任務組設置為已取消狀態。 在您呼叫 `cancel` 之後，工作群組不會啟動未來工作。 有多個子工作可以呼叫 `cancel` 方法。 已取消的任務會導致[併發::task_group::等待](reference/task-group-class.md#wait)[和併發::structured_task_group:等待](reference/structured-task-group-class.md#wait)方法返回[併發::已取消](reference/concurrency-namespace-enums.md#task_group_status)。

如果任務組被取消,則從每個子任務到運行時的調用可能會觸發*中斷點*,從而導致運行時引發和捕獲內部異常類型以取消活動任務。 並行執行階段不會定義特定的中斷點；中斷點可以發生在對執行階段的任何呼叫。 執行階段必須處理其所擲回的例外狀況，才能執行取消。 因此，請不要在工作的主體中處理未知例外狀況。

如果子工作會執行耗時的作業，而且不會呼叫執行階段，則其必須定期檢查取消，並及時結束。 下列範例顯示判斷工作何時取消的一個方法。 工作 `t4` 會在遇到錯誤時取消父工作群組。 工作 `t5` 偶爾會呼叫 `structured_task_group::is_canceling` 方法來檢查取消。 如果父工作群組遭到取消，工作 `t5` 會列印訊息並結束。

[!code-cpp[concrt-task-tree#6](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_6.cpp)]

此示例檢查任務迴圈每 100<sup>次</sup>反覆運算取消。 您檢查取消的頻率取決於您的工作執行的工作量，以及您需要工作回應取消的速度。

如果無法訪問父任務組物件,請調用[併發::is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling)函數以確定是否取消父任務組。

`cancel` 方法只會影響子工作。 例如，如果您在平行工作樹狀結構的圖形取消工作群組 `tg1`，則樹狀結構中的所有工作 (`t1`、`t2`、`t3`、`t4` 和 `t5`) 都會受到影響。 如果您取消巢狀的工作群組 `tg2`，只有工作 `t4` 和 `t5` 會受到影響。

當您呼叫 `cancel` 方法時，所有的子工作群組也會被取消。 不過，取消不會影響工作群組在平行工作樹狀中的任何父項。 下列範例藉由在平行工作樹狀結構圖上建置來顯示這點。

第一個範例會建立工作 `t4` 的工作函式，這個工作是 `tg2` 工作群組的子系。 工作函式會在迴圈中呼叫 `work` 函式。 如果任何對 `work` 的呼叫失敗，工作便會取消其父工作群組。 這會使工作群組 `tg2` 進入已取消的狀態，但不會取消工作群組 `tg1`。

[!code-cpp[concrt-task-tree#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_7.cpp)]

第二個範例類似於第一個，不同之處在於工作會取消工作群組 `tg1`。 這會影響樹狀中的所有工作 (`t1`、`t2`、`t3`、`t4` 和 `t5`)。

[!code-cpp[concrt-task-tree#3](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_8.cpp)]

`structured_task_group` 類別不是安全執行緒。 因此，呼叫其父系 `structured_task_group` 物件的子工作會產生未指定的行為。 此規則的例外情況是`structured_task_group::cancel`[和併發:structured_task_group::is_canceling](reference/structured-task-group-class.md#is_canceling)方法。 子工作可以呼叫這些方法來取消父工作群組，並檢查取消。

> [!CAUTION]
> 雖然您可以使用取消語彙基元來取消工作群組所執行的工作，且此工作群組是執行作為 `task` 物件的子系，但您不能使用 `task_group::cancel` 或 `structured_task_group::cancel` 方法來取消在工作群組中執行的 `task` 物件。

【[頂端](#top)

### <a name="using-exceptions-to-cancel-parallel-work"></a><a name="exceptions"></a>使用例外取消並行工作

在取消平行工作樹狀時，使用取消語彙基元和 `cancel` 方法會比例外狀況處理更有效率。 取消語彙基元和 `cancel` 方法使用由上而下的方式取消工作以及任何子工作。 相反地，例外狀況處理則使用由下而上的方式執行，且必須在例外狀況往上傳播時個別取消每一個子工作群組。 主題[「異常處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)」解釋了併發運行時如何使用異常來傳達錯誤。 不過，並非所有例外狀況都表示發生錯誤。 比方說，搜尋演算法在找到結果時，可能會取消其相關聯的工作。 不過，如先前所述，例外狀況處理的效率會比使用 `cancel` 方法來取消平行工作來得低。

> [!CAUTION]
> 我們建議您只在必要時使用例外狀況取消平行工作。 取消語彙基元和工作群組 `cancel` 方法會更有效率且較不容易出錯。

當您在傳遞給工作群組的工作函式主體中擲回例外狀況時，執行階段會儲存該例外狀況，並將其封送處理至等候工作群組完成的內容。 如同 `cancel` 方法，執行階段會捨棄任何尚未開始的工作，而且不接受新的工作。

第三個範例類似於第二個，不同之處在於工作 `t4` 會擲回例外狀況以取消工作群組 `tg2`。 `try`-本`catch`示例使用塊在任務`tg2`組 等待其子任務完成時檢查取消。 就像第一個範例，這會使工作群組 `tg2` 進入已取消的狀態，但它並不會取消工作群組 `tg1`。

[!code-cpp[concrt-task-tree#4](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_9.cpp)]

第四個範例使用例外狀況處理來取消整個工作樹狀。 範例會在工作群組 `tg1` 等候子工作完成時攔截例外狀況，而不是在工作群組 `tg2` 等候子工作時。 就像第二個範例，這會導致樹狀結構中的兩個工作群組 `tg1` 和 `tg2` 進入已取消的狀態。

[!code-cpp[concrt-task-tree#5](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_10.cpp)]

因為 `task_group::wait` 和 `structured_task_group::wait` 方法會在子工作擲回例外狀況時擲回，所以您不會收到其傳回值。

【[頂端](#top)

## <a name="canceling-parallel-algorithms"></a><a name="algorithms"></a>取消並行演演算法

PPL 中的平行演算法 (例如 `parallel_for`) 是建置在工作群組上。 因此，您可以使用許多相同的技巧來取消平行演算法。

下列範例說明幾種取消平行演算法的方法。

下列範例使用 `run_with_cancellation_token` 函式來呼叫 `parallel_for` 演算法。 `run_with_cancellation_token` 函式採用取消語彙基元作為引數，並以同步方式呼叫所提供的工作函式。 由於平行演算法是建置在工作上，所以其會繼承父工作的取消語彙基元。 因此，`parallel_for` 可以回應取消。

[!code-cpp[concrt-cancel-parallel-for#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_11.cpp)]

下面的示例使用[併發::structured_task_group::run_and_wait](reference/structured-task-group-class.md#run_and_wait)方法`parallel_for`調用 該演演演算法。 `structured_task_group::run_and_wait` 方法會等候所提供的工作完成。 `structured_task_group` 物件可讓工作函式取消工作。

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

【[頂端](#top)

## <a name="when-not-to-use-cancellation"></a><a name="when"></a>何時不使用取消

當一群相關工作的每個成員都能及時結束時，使用取消是適當的。 不過，在某些情節中，取消可能不適合您的應用程式。 例如，因為工作取消是合作式的，所以如果任何個別的工作受阻，整體工作集便不會取消。 例如，如果一項工作尚未開始，但它會解除封鎖另一個使用中的工作，當工作群組取消時，它便不會開始。 這可能會導致應用程式中發生死結。 第二個可能不適合使用取消的範例是，當工作已取消，但其子工作會執行很重要的作業 (例如釋放資源) 時。 由於取消父工作時會取消整體的工作集，因此將不會執行該作業。 有關說明這一點的範例,請參閱"並行模式庫"主題中的"最佳實踐"中的"[瞭解取消和異常處理如何影響物件銷毀](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction)"部分。

【[頂端](#top)

## <a name="related-topics"></a>相關主題

|Title|描述|
|-----------|-----------------|
|[如何：使用取消來中斷平行迴圈](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)|顯示如何使用取消來實作平行搜尋演算法。|
|[如何：使用例外狀況處理來中斷平行迴圈](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|顯示如何使用 `task_group` 類別來撰寫基本樹狀的搜尋演算法。|
|[例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|描述執行階段如何處理工作群組、輕量型工作和非同步代理程式所擲回的例外狀況，以及如何回應您的應用程式中的例外狀況。|
|[工作平行](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|描述工作如何與工作群組產生關聯，以及如何在應用程式中使用非結構化和結構化工作。|
|[平行演算法](../../parallel/concrt/parallel-algorithms.md)|描述平行演算法，這會同時對資料集合執行工作。|
|[平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|提供平行模式程式庫的總覽。|

## <a name="reference"></a>參考

[task 類別 (並行執行階段)](../../parallel/concrt/reference/task-class.md)

[cancellation_token_source 類別](../../parallel/concrt/reference/cancellation-token-source-class.md)

[cancellation_token 類別](../../parallel/concrt/reference/cancellation-token-class.md)

[task_group 類別](reference/task-group-class.md)

[structured_task_group 類別](../../parallel/concrt/reference/structured-task-group-class.md)

[parallel_for功能](reference/concurrency-namespace-functions.md#parallel_for)
