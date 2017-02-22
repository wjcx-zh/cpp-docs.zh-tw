---
title: "工作平行處理原則 (並行執行階段) | Microsoft Docs"
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
  - "結構化工作群組 [並行執行階段]"
  - "結構化工作 [並行執行階段]"
  - "工作群組 [並行執行階段]"
  - "工作平行處理原則"
  - "工作 [並行執行階段]"
ms.assetid: 42f05ac3-2098-494a-ba84-737fcdcad077
caps.latest.revision: 56
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 56
---
# 工作平行處理原則 (並行執行階段)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

並行執行階段中 *工作* 是可以執行特定工作，通常會與其他工作平行執行的工作單位。 工作可以分解為其他更細部工作組織成 *工作群組*。  
  
 當您撰寫非同步程式碼，並想要在非同步作業完成之後執行一些作業時，您可以使用工作。 例如，您可以使用工作以非同步方式讀取檔案，然後使用 [另一項工作 — *接續工作*, ，本文稍後說明 — 處理資料之後可供使用。 反過來說，您可以使用工作群組將平行工作分解成較小的片段。 例如，假設您擁有可將剩餘工作分成兩個分割的遞迴演算法， 您就可以使用工作群組同時執行這些分割，然後等待分割的工作完成。  
  
> [!TIP]
>  當您想要以平行方式集合的每個項目套用相同的常式時，使用平行演算法，例如 [concurrency:: parallel_for](../Topic/parallel_for%20Function.md), ，而不是工作或工作群組。 如需平行演算法的詳細資訊，請參閱 [平行演算法](../../parallel/concrt/parallel-algorithms.md)。  
  
## <a name="key-points"></a>重點  
  
-   當您以傳址方式將變數傳遞給 Lambda 運算式時，必須保證該變數的存留期會保存直到工作完成為止。  
  
-   使用工作 ( [concurrency:: task](../../parallel/concrt/reference/task-class-concurrency-runtime.md) 類別) 當您撰寫非同步程式碼。 Task 類別使用 Windows 執行緒集區做為其排程器，而不使用並行執行階段。  
  
-   使用工作群組 ( [task_group](../Topic/task_group%20Class.md) 類別或 [concurrency:: parallel_invoke](../Topic/parallel_invoke%20Function.md) 演算法) 當您想要平行將工作分解成較小的片段，然後等待完成這些較小的片段。  
  
-   使用 [concurrency::task::then](../Topic/task::then%20Method.md) 方法來建立接續。 A *接續* 是另一項工作完成之後以非同步方式執行的工作。 您可以連接任意數目的接續，形成非同步工作鏈結。  
  
-   以工作為基礎的接續一定會排定在前項工作完成時執行，即使當前項工作取消或擲回例外狀況時亦然。  
  
-   使用 [concurrency:: 超連結 」 (v=VS.110).aspx http://msdn.microsoft.com/library/system.threading.tasks.task.whenall"when_all](../Topic/when_all%20Function.md) 建立每個成員的一組工作完成後完成的工作。 使用 [concurrency::when_any](../Topic/when_all%20Function.md) 建立一個成員的一組工作完成後完成的工作。  
  
-   工作和工作群組可以參與平行模式程式庫 (PPL) 取消機制。 如需詳細資訊，請參閱 [取消](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation_in_the_ppl)。  
  
-   若要深入了解執行階段如何處理工作和工作群組所擲回的例外狀況，請參閱 [例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。  
  
## <a name="in-this-document"></a>本文內容  
  
- [使用 Lambda 運算式](#lambdas)  
  
- [工作類別](#task-class)  
  
- [接續工作](#continuations)  
  
- [值為基礎與以工作為基礎的接續](#value-versus-task)  
  
- [組成工作](#composing-tasks)  
  
    - [When_all 函式](#when-all)  
  
    - [When_any 函式](#when-any)  
  
- [延遲的執行工作](#delayed-tasks)  
  
- [工作群組](#task-groups)  
  
- [比較 structured_task_group 的 task_group](#comparing-groups)  
  
- [範例](#example)  
  
- [穩固程式設計](#robust)  
  
##  <a name="a-namelambdasa-using-lambda-expressions"></a><a name="lambdas"></a> 使用 Lambda 運算式  
 由於 Lambda 運算式的語法簡潔，因此 Lambda 運算式是定義工作和工作群組所執行工作的常見方式。 以下有一些使用提示：  
  
-   工作通常是在背景執行緒上執行，因此當您擷取 Lambda 運算式中的變數時請注意物件存留期。 當您以傳值方式擷取變數時，會在 Lambda 主體中建立該變數的複本。 當您以傳址方式擷取時，則不會建立複本。 因此，請確定您以傳址方式擷取的任何變數，存留期比使用它的工作還長。  
  
-   當您將 Lambda 運算式傳遞至工作時，請不要以傳址方式擷取在堆疊上配置的變數。  
  
-   您需要明確瞭解在 Lambda 運算式中擷取的變數，以便識別哪些以傳值方式擷取，而哪些則以傳址方式擷取。 因此我們建議您不要針對 Lambda 運算式使用 `[=]` 或 `[&]` 選項。  
  
 常見的模式是接續鏈結中的一項工作指派給變數時，另一項工作讀取該變數。 由於每項接續工作會保存不同的變數複本，因此您無法以傳值方式擷取。 針對堆疊配置的變數，您也無法以傳址方式擷取，因為變數可能不再有效。  
  
 若要解決這個問題，請使用智慧型指標，例如 [std:: shared_ptr](../../standard-library/shared-ptr-class.md), ，以換行的變數，並傳值方式傳遞智慧型指標。 如此一來，便可以指派和讀取基礎物件，且存留期會比使用它的工作長。 即使變數是 Windows 執行階段物件的指標或參考計數的控制代碼 (`^`)，也請使用這項技術。 以下是基本的範例：  
  
 [!code-cpp[concrt-lambda-task-lifetime#1](../../parallel/concrt/codesnippet/CPP/task-parallelism-concurrency-runtime_1.cpp)]  
  
 如需 lambda 運算式的詳細資訊，請參閱 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)。  
  
##  <a name="a-nametask-classa-the-task-class"></a><a name="task-class"></a> 工作類別  
 您可以使用 [concurrency:: task](../../parallel/concrt/reference/task-class-concurrency-runtime.md) 類別來撰寫成一組相關作業的工作。 支援此組合模型的概念 *接續*。 當執行接續可讓程式碼之前，或 *前項*, ，工作完成。 前項工作的結果會傳遞做為一或多個接續工作的輸入。 當前項工作完成時，等候它的任何接續工作都會排定執行。 每個接續工作會收到一份前項工作之結果的複本。 這些接續工作也可能依次成為其他接續的前項工作，藉此建立工作鏈結。 接續可協助您建立任意長度的工作鏈結，這些工作之間有特定的相依性。 此外，工作可以在工作啟動之前參與取消，或是在工作執行時以合作的方式參與取消。 如需此取消模型的詳細資訊，請參閱 [取消](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation_in_the_ppl)。  
  
 `task` 是範本類別。 類型參數 `T` 是工作所產生之結果的類型。 如果工作不會傳回值，此類型可以是 `void`。 `T` 無法使用 `const` 修飾詞。  
  
 當您建立工作時，便會提供 *工作函式* ，以執行工作主體。 此工作函式的形式會是 Lambda 函式、函式指標或函式物件。 若要等候工作完成而不需要取得的結果，請呼叫 [concurrency::task::wait](../Topic/task::wait%20Method.md) 方法。  `task::wait` 方法會傳回 [concurrency::task_status](../Topic/task_group_status%20Enumeration.md) 值，描述工作已完成或取消。 若要取得工作的結果，請呼叫 [concurrency](../Topic/task::get%20Method.md) 方法。 這個方法會呼叫 `task::wait` 等候工作完成，因此會阻擋目前執行緒的執行，直到得到結果為止。  
  
 下列範例示範如何建立工作、等候其結果，並顯示其值。 這份文件中的範例使用 Lambda 函式，因為其提供更簡潔的語法。 不過，當您使用工作時，您也可以使用函式指標和函式物件。  
  
 [!code-cpp[concrt-basic-task#1](../../parallel/concrt/codesnippet/CPP/task-parallelism-concurrency-runtime_2.cpp)]  
  
 當您使用 [concurrency::create_task](../Topic/create_task%20Function.md) 函式，您可以使用 `auto` 關鍵字，而不宣告型別。 例如，請考慮這段可建立與列印識別矩陣的程式碼：  
  
 [!code-cpp[concrt-create-task#1](../../parallel/concrt/codesnippet/CPP/task-parallelism-concurrency-runtime_3.cpp)]  
  
 您可以使用 `create_task` 函式來建立對等的作業。  
  
 [!code-cpp[concrt-create-task#2](../../parallel/concrt/codesnippet/CPP/task-parallelism-concurrency-runtime_4.cpp)]  
  
 如果在工作執行期間擲回例外狀況，執行階段會在後續呼叫 `task::get` 或 `task::wait`，或以工作為基礎的接續時，封送處理該例外狀況。 如需工作例外狀況處理機制的詳細資訊，請參閱 [例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。  
  
 如需範例，會使用 `task`, ，[concurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md), ，取消作業，請參閱 [逐步解說︰ 連接使用的工作和 XML HTTP 要求](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)。 (本文件稍後會說明 `task_completion_event` 類別。)  
  
> [!TIP]
>  若要了解詳細資料中的工作特有的 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式，請參閱 [c + + 中的非同步程式設計](http://msdn.microsoft.com/zh-tw/512700b7-7863-44cc-93a2-366938052f31) 和 [c + + 為 Windows 市集應用程式建立非同步作業](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)。  
  
##  <a name="a-namecontinuationsa-continuation-tasks"></a><a name="continuations"></a> 接續工作  
 在非同步程式設計中，非同步作業完成時叫用第二個作業，並將資料傳遞給它，是非常普遍的。 傳統上，這項作業使用回呼方法完成。 並行執行階段中，在相同的功能由提供 *接續工作*。 接續工作 （也只稱為接續） 是由另一項工作，也就是叫用非同步工作 *前項*, ，當前項完成時。 藉由使用接續，您可以：  
  
-   將資料從前項傳遞至接續。  
  
-   指定叫用或不叫用接續的精確條件。  
  
-   在接續開始之前或在執行時以合作的方式取消接續。  
  
-   提供有關該如何排定接續的提示。 (這只適用於 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式。 如需詳細資訊，請參閱 [c + + 為 Windows 市集應用程式建立非同步作業](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)。)  
  
-   從相同前項叫用多個接續。  
  
-   當多個前項中的所有或任何一項完成時，叫用一個接續。  
  
-   將接續一個接著一個地鏈結起來，可至任意長度。  
  
-   使用接續處理前項所擲回的例外狀況。  
  
 這些功能可讓您在第一個工作完成時執行一或多個工作。 例如，您可以建立接續，在第一個工作從磁碟讀取檔案之後將其壓縮。  
  
 下列範例會修改上一個使用 [concurrency::task::then](../Topic/task::then%20Method.md) 方法來排程列印前項工作的值可用時的接續。  
  
 [!code-cpp[concrt-basic-continuation#1](../../parallel/concrt/codesnippet/CPP/task-parallelism-concurrency-runtime_5.cpp)]  
  
 您可以將工作鏈結及巢狀化至任何長度。 工作也可以有多個接續。 下列範例說明基本的接續鏈結，其可將前一個工作的值遞增三次。  
  
 [!code-cpp[concrt-continuation-chain#1](../../parallel/concrt/codesnippet/CPP/task-parallelism-concurrency-runtime_6.cpp)]  
  
 接續也可以傳回另一項工作。 如果沒有取消，則這項工作會在後續的接續之前執行。 此技巧稱為 *非同步包裝*。 非同步解除包裝適用於您想要在背景中執行其他工作，但不是想讓目前的工作阻擋目前的執行緒時。 (這常見於 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式，接續在應用程式中可在 UI 執行緒上執行)。 下列範例顯示三個工作。 第一項工作會傳回另一項在接續工作之前執行的工作。  
  
 [!code-cpp[concrt-async-unwrapping#1](../../parallel/concrt/codesnippet/CPP/task-parallelism-concurrency-runtime_7.cpp)]  
  
> [!IMPORTANT]
>  當工作的接續傳回類型 `N` 的巢狀工作時，產生的工作類型為 `N`，而非 `task<N>`，並且會在巢狀工作完成時完成。 換句話說，接續會執行巢狀工作的解除包裝。  
  
##  <a name="a-namevalue-versus-taska-value-based-versus-task-based-continuations"></a><a name="value-versus-task"></a> 值為基礎與以工作為基礎的接續  
 假如有 `task` 物件，其傳回類型是 `T`，則您可以提供類型 `T` 或 `task<T>` 的值給其接續工作。 接受類型的接續 `T` 稱為 *值為主的接續*。 以值為基礎的接續會排定在前項工作完成且沒有錯誤也未取消時執行。 接受類型的接續 `task<T>` 為其參數稱為 *工作為主的接續*。 以工作為基礎的接續一定會排定在前項工作完成時執行，即使當前項工作取消或擲回例外狀況時亦然。 接著您便可以呼叫 `task::get` 取得前項工作的結果。 如果前項工作已取消，則 `task::get` 會擲回 [concurrency::task_canceled](../../parallel/concrt/reference/task-canceled-class.md)。 如果前項工作擲回例外狀況，`task::get` 會重新擲回該例外狀況。 以工作為基礎的接續在其前項工作取消時，不會標示為已取消。  
  
##  <a name="a-namecomposing-tasksa-composing-tasks"></a><a name="composing-tasks"></a> 組成工作  
 本章節描述 [concurrency:: when_all](../Topic/when_all%20Function.md) 和 [concurrency::when_any](../Topic/when_all%20Function.md) 函式，可協助您撰寫多個工作來實作常見的模式。  
  
###  <a name="a-namewhen-alla-the-whenall-function"></a><a name="when-all"></a> When_all 函式  
 `when_all` 函式會產生在一組工作完成之後完成的工作。 此函數會傳回 std::[向量](../../standard-library/vector-class.md) 物件，其中包含集合中每個工作的結果。 下列基本範例使用 `when_all` 來建立代表其他三個工作已完成的工作。  
  
 [!code-cpp[concrt-join-tasks#1](../../parallel/concrt/codesnippet/CPP/task-parallelism-concurrency-runtime_8.cpp)]  
  
> [!NOTE]
>  您傳遞給 `when_all` 的工作必須一致。 也就是說，它們必須全部傳回相同的類型。  
  
 您也可以使用 `&&` 語法來產生在一組工作完成之後完成的工作，如下列範例所示。  
  
 `auto t = t1 && t2; // same as when_all`  
  
 將接續與 `when_all` 搭配使用是常見的作法，用來在一組工作完成後執行動作。 下列範例會修改前一個範例，列印皆會產生 `int` 結果的三項工作的總和。  
  
 [!code-cpp[concrt-join-tasks#2](../../parallel/concrt/codesnippet/CPP/task-parallelism-concurrency-runtime_9.cpp)]  
  
 在此範例中，您也可以指定`task<vector<int>>` 來產生工作為基礎的接續。  
  
 如果一組工作中有任何工作取消或擲回例外狀況，`when_all` 會立即完成，並且不會等待其餘的工作完成。 如果擲回例外狀況，執行階段會在您對 `when_all` 傳回的工作物件呼叫 `task::get` 或 `task::wait` 時重新擲回例外狀況。 如果有多個工作擲回例外狀況，執行階段會選擇其中之一。 因此，請確保您在所有工作完成之後，觀察到所有例外狀況；未處理的工作例外狀況會導致應用程式終止。  
  
 以下是可用來確保您的程式會觀察到所有例外狀況的公用程式函式。 針對提供的範圍內每一項工作，`observe_all_exceptions` 會觸發重新擲回發生的任何例外狀況，接著抑制該例外狀況。  
  
 [!code-cpp[concrt-eh-when_all#1](../../parallel/concrt/codesnippet/CPP/task-parallelism-concurrency-runtime_10.cpp)]  
  
 請考慮使用 C++ 和 XAML 的 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式，並將一組檔案寫入至磁碟。 下列範例顯示如何使用 `when_all` 和 `observe_all_exceptions` 以確保程式會觀察到所有例外狀況。  
  
 [!code-cpp[concrt-eh-when_all#2](../../parallel/concrt/codesnippet/CPP/task-parallelism-concurrency-runtime_11.cpp)]  
  
##### <a name="to-run-this-example"></a>執行此範例  
  
1.  在 MainPage.xaml 中加入 `Button` 控制項。  
  
 [!code-xml[concrt-eh-when_all#3](../../parallel/concrt/codesnippet/Xaml/task-parallelism-concurrency-runtime_12.xaml)]  
  
2.  在 MainPage.xaml.h中，將這些向前宣告加入 `MainPage` 類別宣告的 `private` 區段。  
  
 [!code-cpp[concrt-eh-when_all#4](../../parallel/concrt/codesnippet/CPP/task-parallelism-concurrency-runtime_13.h)]  
  
3.  在 MainPage.xaml.cpp 中實作 `Button_Click` 事件處理常式。  
  
 [!code-cpp[concrt-eh-when_all#5](../../parallel/concrt/codesnippet/CPP/task-parallelism-concurrency-runtime_14.cpp)]  
  
4.  在 MainPage.xaml.cpp 中實作 `WriteFilesAsync`，如範例所示。  
  
> [!TIP]
> `when_all` 是未封鎖的函式，會產生 `task` 做為其結果。 不同於 [task:: wait](../Topic/task::wait%20Method.md), ，則您可以放心呼叫此函式 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] ASTA (應用程式 STA) 執行緒上的應用程式。  
  
###  <a name="a-namewhen-anya-the-whenany-function"></a><a name="when-any"></a> When_any 函式  
 `when_any` 函式會產生在一組工作的第一項工作完成之後完成的工作。 此函數會傳回 [std:: initializer_list](../../standard-library/pair-structure.md) 物件，其中包含已完成工作的結果，該工作集合中的索引。  
  
 `when_any` 函式在下列情節中特別有用：  
  
-   重複的作業。 請考慮能夠以多種方式執行的演算法或作業。 您可以使用 `when_any` 函式選擇先完成的作業，然後取消其餘作業。  
  
-   交錯作業。 您可以啟動所有必須完成的多個作業，並使用 `when_any` 函式在每個作業完成時處理結果。 完成作業後，您可以開始一個或多個其他工作。  
  
-   已節流的作業。 您可以使用 `when_any` 函式來限制並行作業的數目，以擴充前一個情節。  
  
-   過期的作業。 您可以使用 `when_any` 函式，選取一或多個工作，還是在指定時間之後完成的工作。  
  
 如同 `when_all`，使用具有 `when_any` 的接續在一組工作中的第一項工作完成時執行動作是很常見的方式。 下列的基本範例使用 `when_any` 來建立在其他三個工作中第一個工作完成時完成的工作。  
  
 [!code-cpp[concrt-select-task#1](../../parallel/concrt/codesnippet/CPP/task-parallelism-concurrency-runtime_15.cpp)]  
  
 在此範例中，您也可以指定 `task<pair<int, size_t>>` 來產生以工作為基礎的接續。  
  
> [!NOTE]
>  如同 `when_all`，您將傳遞給 `when_any` 的工作必須全部傳回相同的類型。  
  
 您也可以使用 `||` 語法來產生工作，在一組工作中的第一項工作完成之後完成，如下列範例所示。  
  
 `auto t = t1 || t2; // same as when_any`  
  
> [!TIP]
>  如同 `when_all`，`when_any` 是未封鎖的函式，可以在 ASTA 執行緒上的 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式中安全地呼叫。  
  
##  <a name="a-namedelayed-tasksa-delayed-task-execution"></a><a name="delayed-tasks"></a> 延遲的執行工作  
 有時必須要延遲工作的執行，直到滿足條件為止，或者啟動工作以回應外部事件。 例如在非同步程式設計中，您可能必須啟動工作以回應 I/O 完成事件。  
  
 有兩種方法可以完成這項作業：使用接續，或啟動工作並等待工作之工作函式內的事件。 然而，在某些情況中無法使用這些方法。 例如，若要建立接續，您必須要有前項工作。 不過，如果您沒有前項工作，您可以建立 *工作完成事件* 和更新版本可供使用時，鏈結前項工作完成事件。 此外，因為等待中的工作也會阻擋執行緒，您可以使用工作完成事件在非同步作業完成時執行工作，並藉此釋放執行緒。  
  
  [Concurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) 類別有助於簡化處理這類組合的工作。 就像 `task` 類別，類型參數 `T` 是工作所產生之結果的類型。 如果工作不會傳回值，此類型可以是 `void`。 `T` 無法使用 `const` 修飾詞。 一般而言，會提供 `task_completion_event` 物件給執行緒或工作，在物件的值可用時對其發出通知。 同時，一或多個工作會設定為該事件的接聽程式。 設定事件之後，接聽程式工作便會完成，而其接續工作會排定繼續執行。  
  
 如需範例，會使用 `task_completion_event` 實作延遲之後完成的工作，請參閱 [How to︰ 建立工作，完成後延遲](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)。  
  
##  <a name="a-nametask-groupsa-task-groups"></a><a name="task-groups"></a> 工作群組  
 A *工作群組* 組織工作的集合。 工作群組將工作推送至竊取工作的佇列。 排程器將工作從這個佇列移除，並在可用的運算資源上執行。 將工作加入工作群組之後，您可以等待所有工作完成，或取消尚未開始的工作。  
  
 使用 PPL [task_group](../Topic/task_group%20Class.md) 和 [structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) 類別來代表工作群組和 [concurrency::task_handle](../../parallel/concrt/reference/task-handle-class.md) 類別來代表這些群組中執行的工作。 `task_handle` 類別會封裝執行工作的程式碼。 就像 `task` 類別，此工作函式的形式會是 Lambda 函式、函式指標或函式物件。 您通常不需要直接使用 `task_handle` 物件。 相反地，您會將工作函式傳遞至工作群組，而工作群組會建立和管理 `task_handle` 物件。  
  
 PPL 工作群組分成這兩種類別︰ *非結構化的工作群組* 和 *結構化工作群組*。 PPL 使用 `task_group` 類別來代表非結構化工作群組，並使用 `structured_task_group` 類別來代表結構化工作群組。  
  
> [!IMPORTANT]
>  PPL 也會定義 [concurrency:: parallel_invoke](../Topic/parallel_invoke%20Function.md) 演算法，使用 `structured_task_group` 平行執行的一組工作的類別。 由於 `parallel_invoke` 演算法的語法更簡潔，如果可以的話，我們建議您使用它，而不要使用 `structured_task_group` 類別。 本主題 [平行演算法](../../parallel/concrt/parallel-algorithms.md) 描述 `parallel_invoke` 詳細。  
  
 當您有數個想要同時執行的獨立工作，而且必須等候所有工作完成才能繼續時，請使用 `parallel_invoke`。 這項技術通常稱為 *分岔和聯結* 平行處理原則。 當您有數個想要同時執行的獨立工作，但是想要等候工作晚點才完成時，請使用 `task_group`。 例如，您可以將工作加入 `task_group` 物件，並等候工作在另一個函式或另一個執行緒中完成。  
  
 工作群組支援取消的概念。 取消可讓您通知所有作用中的工作，您想要取消整體作業。 取消也會讓尚未開始的工作無法開始。 如需取消的詳細資訊，請參閱 [取消](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation_in_the_ppl)。  
  
 執行階段也提供例外狀況處理模型，可讓您從工作擲回例外狀況，並在等候相關聯的工作群組完成時，處理該例外狀況。 如需有關此例外狀況處理模型的詳細資訊，請參閱 [例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。  
  
##  <a name="a-namecomparing-groupsa-comparing-taskgroup-to-structuredtaskgroup"></a><a name="comparing-groups"></a> 比較 structured_task_group 的 task_group  
 雖然我們建議您使用 `task_group` 或 `parallel_invoke`，而不要使用 `structured_task_group` 類別，但在某些情況下您會想要使用 `structured_task_group`，例如您撰寫平行處理演算法 (可執行數目可變的工作或要求取消的支援) 時。 本章節將說明 `task_group` 和 `structured_task_group` 類別之間的差異。  
  
 `task_group` 類別是安全執行緒。 因此，您可以從多個執行緒將工作加入 `task_group` 物件，並從多個執行緒等候或取消 `task_group` 物件。 `structured_task_group` 物件的建構和解構必須出現在相同的語彙範圍中。 此外，`structured_task_group` 物件上的所有作業必須在同一個執行緒上進行。 此規則的例外狀況是 [concurrency::structured_task_group::cancel](../Topic/structured_task_group::cancel%20Method.md) 和 [concurrency::structured_task_group::is_canceling](../Topic/structured_task_group::is_canceling%20Method.md) 方法。 子工作可以呼叫這些方法來取消父工作群組，或在任何時候檢查取消。  
  
 您可以在執行其他工作 `task_group` 物件之後呼叫 [concurrency::task_group::wait](../Topic/task_group::wait%20Method.md) 或 [concurrency::task_group::run_and_wait](../Topic/task_group::run_and_wait%20Method.md) 方法。 相反地，如果您在執行其他工作 `structured_task_group` 物件之後呼叫 [concurrency::structured_task_group::wait](../Topic/structured_task_group::wait%20Method.md) 或 [concurrency::structured_task_group::run_and_wait](../Topic/structured_task_group::run_and_wait%20Method.md) 方法，則行為是未定義。  
  
 因為 `structured_task_group` 類別不會同步處理多個執行緒，所以其執行額外負荷比 `task_group` 類別少。 因此，如果您的問題並不需要從多個執行緒排定工作，而且您無法使用 `parallel_invoke` 演算法，`structured_task_group` 類別便可以協助您撰寫效能更好的程式碼。  
  
 如果您在一個 `structured_task_group` 物件內使用另一個 `structured_task_group` 物件，內部物件必須在外部物件完成之前完成與終結。 `task_group` 類別不需要巢狀工作群組在外部群組完成之前完成。  
  
 非結構化工作群組和結構化工作群組處理工作控制代碼的方式不同。 您可以直接將工作函式傳遞給 `task_group` 物件；`task_group` 物件會建立和管理您的工作控制代碼。 `structured_task_group` 類別會要求您管理每一項工作的 `task_handle` 物件。 每個 `task_handle` 物件都必須在其關聯之 `structured_task_group` 物件的整個存留期間維持有效。 使用 [concurrency::make_task](../Topic/make_task%20Function.md) 函式來建立 `task_handle` 物件，如下列的基本範例所示︰  
  
 [!code-cpp[concrt-make-task-structure#1](../../parallel/concrt/codesnippet/CPP/task-parallelism-concurrency-runtime_16.cpp)]  
  
 若要管理工作有多個工作的控點，使用的堆疊配置常式例如 [_malloca](../../c-runtime-library/reference/malloca.md) 或容器類別，例如 std::[向量](../../standard-library/vector-class.md)。  
  
 `task_group` 和 `structured_task_group` 都支援取消。 如需取消的詳細資訊，請參閱 [取消](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation_in_the_ppl)。  
  
##  <a name="a-nameexamplea-example"></a><a name="example"></a> 範例  
 下列基本範例顯示如何使用工作群組。 這個範例會使用 `parallel_invoke` 演算法來同時執行兩個工作。 每個工作會將子工作加入 `task_group` 物件。 請注意，`task_group` 類別允許多個工作同時對其加入工作。  
  
 [!code-cpp[concrt-using-task-groups#1](../../parallel/concrt/codesnippet/CPP/task-parallelism-concurrency-runtime_17.cpp)]  
  
 以下是此範例的範例輸出：  
  
```Output  
Message from task: Hello  
Message from task: 3.14  
Message from task: 42  
```  
  
 因為 `parallel_invoke` 演算法同時執行工作，所以輸出訊息的順序可能有所不同。  
  
 完整的範例，示範如何使用 `parallel_invoke` 演算法，請參閱 [How to︰ 使用 parallel_invoke 撰寫平行排序常式](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md) 和 [How to︰ 使用 parallel_invoke 執行平行作業](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)。 如需完整的範例使用 `task_group` 類別來實作非同步 future，請參閱 [逐步解說︰ 實作未來](../../parallel/concrt/walkthrough-implementing-futures.md)。  
  
##  <a name="a-namerobusta-robust-programming"></a><a name="robust"></a> 穩固程式設計  
 請確定當您使用工作、工作群組和平行演算法時，了解取消和例外狀況處理的角色。 例如，在平行工作的樹狀結構中，已取消的工作會導致子工作無法執行。 如果其中一項子工作所執行的作業對應用程式很重要 (例如釋放資源)，這可能會造成問題。 此外，如果子工作擲回例外狀況，該例外狀況可能會透過物件解構函式散佈，並在應用程式中導致未定義的行為。 如需說明這些點的範例，請參閱 [了解如何取消和例外狀況處理會影響物件解構](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) 平行模式程式庫文件中的最佳作法一節。 如需取消和 PPL 中的例外狀況處理模型的詳細資訊，請參閱 [取消](../../parallel/concrt/cancellation-in-the-ppl.md) 和 [例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|說明|  
|-----------|-----------------|  
|[如何︰ 使用 parallel_invoke 撰寫平行排序常式](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|顯示如何使用 `parallel_invoke` 演算法，以改善 bitonic 排序演算法的效能。|  
|[如何︰ 使用 parallel_invoke 執行平行作業](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|顯示如何使用 `parallel_invoke` 演算法，以改善在共用資料來源上執行多個作業的程式效能。|  
|[如何︰ 建立延遲之後完成的工作](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|示範如何使用 `task`, ，`cancellation_token_source`, ，`cancellation_token`, ，和 `task_completion_event` 類別建立延遲之後完成的工作。|  
|[逐步解說︰ 實作未來](../../parallel/concrt/walkthrough-implementing-futures.md)|顯示如何將並行執行階段中現有功能結合，成為可完成更多事項的功能。|  
|[平行模式程式庫 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|描述 PPL，其提供開發並行處理應用程式的命令式程式設計模型。|  
  
## <a name="reference"></a>參考資料  
 [task 類別 （並行執行階段）](../../parallel/concrt/reference/task-class-concurrency-runtime.md)  
  
 [task_completion_event 類別](../../parallel/concrt/reference/task-completion-event-class.md)  
  
 [when_all 函式](../Topic/when_all%20Function.md)  
  
 [when_any 函式](../Topic/when_any%20Function.md)  
  
 [task_group 類別](../Topic/task_group%20Class.md)  
  
 [parallel_invoke 函式](../Topic/parallel_invoke%20Function.md)  
  
 [structured_task_group 類別](../../parallel/concrt/reference/structured-task-group-class.md)
