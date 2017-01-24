---
title: "逐步解說：實作未來 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "實作未來 [並行執行階段]"
  - "未來, 實作 [並行執行階段]"
ms.assetid: 82ea75cc-aaec-4452-b10d-8abce0a87e5b
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 逐步解說：實作未來
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主題說明如何在您的應用程式中實作 future。 本主題示範如何結合現有的功能並行執行階段中轉換成多個執行。  
  
> [!IMPORTANT]
>  本主題將基於示範目的說明未來的概念。 我們建議您改用 [std:: future](../../standard-library/future-class.md) 或 [concurrency:: task](../../parallel/concrt/reference/task-class-concurrency-runtime.md) 當您需要計算值供日後使用的非同步工作。  
  
 A *工作* 是能分解成更精細的其他計算的計算。 A *未來* 是非同步工作的計算值供日後使用。  
  
 若要實作 future，本主題定義 `async_future` 類別。  `async_future` 類別會使用並行執行階段的下列元件︰ [task_group](../Topic/task_group%20Class.md) 類別和 [concurrency:: single_assignment](../../parallel/concrt/reference/single-assignment-class.md) 類別。  `async_future` 類別會使用 `task_group` 來以非同步方式計算值的類別和 `single_assignment` 類別，以儲存計算的結果。 建構函式 `async_future` 類別會計算結果，將工作函式和 `get` 方法會擷取結果。  
  
### <a name="to-implement-the-asyncfuture-class"></a>若要實作 async_future 類別  
  
1.  宣告樣板類別，名為 `async_future` 參數化的產生的計算類型。 新增 `public` 和 `private` 區段，這個類別。  
  
 [!code-cpp[concrt-futures#2](../../parallel/concrt/codesnippet/CPP/walkthrough-implementing-futures_1.cpp)]  
  
2.  在 `private` 區段 `async_future` 類別中，宣告 `task_group` 和 `single_assignment` 資料成員。  
  
 [!code-cpp[concrt-futures#3](../../parallel/concrt/codesnippet/CPP/walkthrough-implementing-futures_2.cpp)]  
  
3.  在 `public` 區段 `async_future` 類別也會實作建構函式。 建構函式是在計算結果，則工作函式參數化的範本。 建構函式會以非同步方式執行中的工作函式 `task_group` 資料成員，並使用 [concurrency:: send](../Topic/send%20Function.md) 函式可將結果寫入 `single_assignment` 資料成員。  
  
 [!code-cpp[concrt-futures#4](../../parallel/concrt/codesnippet/CPP/walkthrough-implementing-futures_3.cpp)]  
  
4.  在 `public` 區段 `async_future` 類別也會實作解構函式。 解構函式會等候工作完成。  
  
 [!code-cpp[concrt-futures#5](../../parallel/concrt/codesnippet/CPP/walkthrough-implementing-futures_4.cpp)]  
  
5.  在 `public` 區段 `async_future` 類別也會實作 `get` 方法。 這個方法會使用 [concurrency:: receive](../Topic/receive%20Function.md) 函式來擷取工作函式的結果。  
  
 [!code-cpp[concrt-futures#6](../../parallel/concrt/codesnippet/CPP/walkthrough-implementing-futures_5.cpp)]  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例顯示完整 `async_future` 類別和其用法範例。  `wmain` 函式會建立 std::[向量](../../standard-library/vector-class.md) 物件，其中包含 10000 的隨機整數值。 然後它會使用 `async_future` 物件中包含的最小和最大值 `vector` 物件。  
  
### <a name="code"></a>程式碼  
 [!code-cpp[concrt-futures#1](../../parallel/concrt/codesnippet/CPP/walkthrough-implementing-futures_6.cpp)]  
  
### <a name="comments"></a>註解  
 這個範例會產生下列輸出：  
  
```Output  
smallest: 0  
largest:  9999  
average:  4981  
```  
  
 此範例會使用 `async_future::get` 方法來擷取計算的結果。  `async_future::get` 方法會等候完成計算是否仍在作用中的計算。  
  
## <a name="robust-programming"></a>穩固程式設計  
 若要擴充 `async_future` 類別以處理工作函式所擲回的例外狀況，請修改 `async_future::get` 方法以呼叫 [concurrency::task_group::wait](../Topic/task_group::wait%20Method.md) 方法。  `task_group::wait` 方法會擲回任何例外狀況所產生的工作函式。  
  
 下列範例顯示的修改的版本 `async_future` 類別。  `wmain` 函式使用 `try`-`catch` 區塊的結果列印 `async_future` 物件，或是要列印的工作函式所產生的例外狀況的值。  
  
 [!code-cpp[concrt-futures-with-eh#1](../../parallel/concrt/codesnippet/CPP/walkthrough-implementing-futures_7.cpp)]  
  
 這個範例會產生下列輸出：  
  
```Output  
caught exception: error  
```  
  
 如需有關並行執行階段中的例外狀況處理模型的詳細資訊，請參閱 [例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 複製範例程式碼並將它貼在 Visual Studio 專案中，或貼入名為的檔案 `futures.cpp` ，然後在 Visual Studio 命令提示字元] 視窗中執行下列命令。  
  
 **cl.exe /EHsc futures.cpp**  
  
## <a name="see-also"></a>另請參閱  
 [並行執行階段逐步解說](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [task_group 類別](../Topic/task_group%20Class.md)   
 [single_assignment 類別](../../parallel/concrt/reference/single-assignment-class.md)
