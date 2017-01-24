---
title: "逐步解說：搭配非同步方法使用偵錯工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "非同步功能, 使用偵錯工具"
  - "await 運算子, 使用偵錯工具"
  - "逐步執行命令, 位於 await 運算子"
  - "跳離函式命令, 在 async 方法內"
  - "不進入函式命令, 位於 await 運算子"
ms.assetid: 5adb2531-3f09-4b7e-8baa-29de80abee6e
caps.latest.revision: 23
caps.handback.revision: 23
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
---
# 逐步解說：搭配非同步方法使用偵錯工具
使用 Async 功能，您就可以呼叫非同步方法，而不需要使用回呼或將您的程式碼分散到多種方法或 lambda 運算式上。  若要讓同步程式碼變成非同步，請呼叫非同步方法，而不要呼叫同步方法，然後再加入幾個關鍵字到程式碼中。  如需詳細資訊，請參閱[使用 Async 和 Await 設計非同步程式](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)。  
  
 在 Visual Studio 偵錯工具中，您可以使用 \[**逐步執行**\]、\[**不進入函式**\] 和 \[**跳離函式**\] 命令搭配 `Async` 功能。  您也可以繼續使用中斷點，特別是在包含 await 運算子的陳述式中檢視控制流程。  在這個逐步解說中，您將完成下列工作，這些工作可依任意順序執行。  
  
-   使用中斷點示範 await 陳述式中的控制流程。  
  
-   了解 \[**逐步執行**\] 和 \[**不進入函式**\] 命令在包含 await 運算子之陳述式中的行為。  
  
-   了解從非同步方法內部使用 \[**跳離函式**\] 命令時，該命令的行為。  
  
## 顯示控制流程的中斷點  
 如果您以 [Async](../Topic/Async%20\(Visual%20Basic\).md) \(Visual Basic\) 或 [async](../Topic/async%20\(C%23%20Reference\).md) \(C\#\) 修飾詞標記方法，就可以在該方法中使用 [Await](../Topic/Async%20\(Visual%20Basic\).md) \(Visual Basic\) 或 [await](../Topic/await%20\(C%23%20Reference\).md) \(C\#\) 運算子。  若要建立 await 運算式，請將 await 運算子與工作產生關聯。  針對工作呼叫 await 運算式時，目前方法會立即結束，並傳回不同的工作。  與 await 運算子相關聯的工作完成時，就會在相同方法中繼續執行。  如需詳細資訊，請參閱 [非同步程式中的控制流程](../Topic/Control%20Flow%20in%20Async%20Programs%20\(C%23%20and%20Visual%20Basic\).md)。  
  
> [!NOTE]
>  非同步方法會在遇到第一個不完整的等候物件或是到達非同步方法的結尾時 \(以先發生者為準\)，返回呼叫端。  
  
> [!NOTE]
>  這些範例中的主控台應用程式會使用 <xref:System.Threading.Tasks.Task.Wait%2A> 方法防止應用程式在 `Main` 中終止。  您不應該在主控台應用程式之外使用 <xref:System.Threading.Tasks.Task.Wait%2A> 方法，否則可能發生死結的情況。  
  
 下列程序將設定中斷點，以示範應用程式到達 await 陳述式時所發生的情況。  您也可以藉由加入 `Debug.WriteLine` 陳述式示範控制流程。  
  
1.  建立主控台應用程式，然後將下列程式碼貼入其中：  
  
     [!code-cs[csAsyncDebugging#1](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_1.cs)]
     [!code-vb[csAsyncDebugging#1](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_1.vb)]  
  
2.  在以「設定中斷點」註解結尾的三個程式行上設定偵錯中斷點。  
  
3.  選擇 F5 鍵，或是在功能表列上選擇 \[**偵錯**\]、\[**開始偵錯**\] 執行應用程式。  
  
     應用程式會進入 `ProcessAsync` 方法，並且在包含 await 運算子的程式行上中斷。  
  
4.  再次選擇 F5 鍵。  
  
     因為應用程式在包含 await 運算子的陳述式上停止，所以應用程式會立即結束非同步方法並傳回工作。  因此，應用程式會結束 `ProcessAsync` 方法，並且在呼叫方法 \(`Main`\) 中的中斷點處中斷。  
  
5.  再次選擇 F5 鍵。  
  
     當 `DoSomethingAsync` 方法完成時，程式碼會在呼叫方法中的 await 陳述式之後繼續。  因此，應用程式會在 `ProcessAsync` 方法中的中斷點處中斷。  
  
     當 `DoSomethingAsync` 初次等候時，`ProcessAsync` 方法會結束並傳回工作。  接著等候的 `DoSomethingAsync` 方法就會完成，await 陳述式的評估會產生 `DoSomethingAsync` 的傳回值。  `DoSomethingAsync` 方法定義為傳回 `Task (Of Integer)` \(Visual Basic 中\) 或 `Task<int>` \(C\# 中\)，因此其傳回陳述式中的值為整數。  如需詳細資訊，請參閱[非同步方法的傳回類型](../Topic/Async%20Return%20Types%20\(C%23%20and%20Visual%20Basic\).md)。  
  
### 取得然後等候工作  
 在 `ProcessAsync` 方法中，陳述式 `Dim result = Await DoSomethingAsync()` \(Visual Basic\) 或 `var result = await DoSomethingAsync();` \(C\#\) 為下列兩個陳述式的縮減：  
  
 [!code-cs[csAsyncDebugging#2](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_2.cs)]
 [!code-vb[csAsyncDebugging#2](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_2.vb)]  
  
 第一行程式碼會呼叫非同步方法並傳回工作。  該工作會與下一行程式碼的 await 運算子相關聯。  await 陳述式會結束方法 \(`ProcessAsync`\) 和傳回不同的工作。  與 await 運算子相關聯的工作完成時，程式碼會在方法 \(`ProcessAsync`\) 中的 await 陳述式之後繼續。  
  
 當 await 陳述式立即傳回不同的工作時，該工作是包含 await 運算子之非同步方法的傳回引數 \(`ProcessAsync`\)。  await 傳回的工作包括在相同方法中的 await 之後執行程式碼，這也是為什麼這項工作不同於與 await 相關聯的工作。  
  
## 逐步執行和不進入函式  
 \[**逐步執行**\] 命令會逐步執行方法，不過 \[**不進入函式**\] 命令會執行方法呼叫，然後在呼叫方法的下一行中斷。  如需詳細資訊，請參閱[程式碼的逐步執行、不進入函式或跳離函式](../Topic/Navigating%20through%20Code%20with%20the%20Debugger.md#BKMK_Step_into__over__or_out_of_the_code)。  
  
 下列程序將說明當您在 await 陳述式中選擇 \[**逐步執行**\] 或 \[**不進入函式**\] 命令時，會發生什麼情況。  
  
1.  將主控台應用程式中的程式碼替換成下列程式碼：  
  
     [!code-cs[csAsyncDebugging#3](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_3.cs)]
     [!code-vb[csAsyncDebugging#3](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_3.vb)]  
  
2.  選擇 F11 鍵，或選擇功能表列上的 \[**偵錯**\]、\[**逐步執行**\]，開始示範包含 await 運算子之陳述式中的 `Step Into` 命令。  
  
     應用程式會在第一行開始並中斷，也就是 Visual Basic 中的 `Sub Main()` 或 C\# 中 `Main` 方法的左大括號。  
  
3.  再選擇 F11 鍵三次。  
  
     應用程式現在應該會在 `ProcessAsync` 方法的 await 陳述式中。  
  
4.  選擇 F11 鍵。  
  
     應用程式會進入 `DoSomethingAsync` 方法並且在第一行中斷。  即使在 `await` 陳述式中，應用程式立即返回呼叫方法 \(`Main`\)，這種行為仍會發生。  
  
5.  繼續選擇 F11 鍵，直到應用程式返回 `ProcessAsync` 方法中的 await 陳述式。  
  
6.  選擇 F11 鍵。  
  
     應用程式會在 await 陳述式後面的那一行中斷。  
  
7.  在功能表列上，選擇 \[**偵錯**\]、\[**停止偵錯**\]，停止應用程式執行。  
  
     下列步驟將示範 await 陳述式中的 \[**不進入函式**\] 命令。  
  
8.  選擇 F11 鍵四次，或選擇功能表列上的 \[**偵錯**\]、\[**逐步執行**\] 四次。  
  
     應用程式現在應該會在 `ProcessAsync` 方法的 await 陳述式中。  
  
9. 選擇 F10 鍵，或是選擇功能表列上的 \[**偵錯**\]、\[**不進入函式**\]。  
  
     此時會在 await 陳述式後面的那一行中斷執行。  即使在 await 陳述式中應用程式立即返回呼叫方法 \(`Main`\)，這種行為仍會發生。  `Step Over` 命令也會如預期一般，不進入執行 `DoSomethingAsync` 方法。  
  
10. 在功能表列上，選擇 \[**偵錯**\]、\[**停止偵錯**\]，停止應用程式執行。  
  
     如下列步驟所示，await 運算子與非同步方法呼叫位於不同程式行上時，\[**逐步執行**\] 和 \[**不進入函式**\] 命令的行為會稍有不同。  
  
11. 在 `ProcessAsync` 方法中，將 await 陳述式取代為下列程式碼。  原始 await 陳述式是下列兩個陳述式的縮減。  
  
     [!code-cs[csAsyncDebugging#2](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_2.cs)]
     [!code-vb[csAsyncDebugging#2](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_2.vb)]  
  
12. 選擇 F11 鍵，或選擇功能表列上的 \[**偵錯**\]、\[**逐步執行**\] 多次，開始執行並逐步執行程式碼。  
  
     在呼叫 `DoSomethingAsync` 處，\[**逐步執行**\] 命令會在 `DoSomethingAsync` 方法內中斷，而 \[**不進入函式**\] 命令則會移至下一個陳述式，就如預期一般。  在 await 陳述式中，這兩個命令會在 await 後面的陳述式中斷。  
  
## 跳離函式  
 在不是非同步的方法中，\[**跳離函式**\] 命令會在方法呼叫後面的程式碼上中斷呼叫方法。  若是非同步方法，在呼叫方法內中斷執行的邏輯更為複雜，而且該邏輯取決於 \[**跳離函式**\] 命令是否在非同步方法的第一行上。  
  
1.  將主控台應用程式中的程式碼替換成下列程式碼：  
  
     [!code-cs[csAsyncDebugging#4](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_4.cs)]
     [!code-vb[csAsyncDebugging#4](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_4.vb)]  
  
2.  在 `DoSomethingAsync` 方法的 `Debug.WriteLine("before")` 這行上設定中斷點。  
  
     這樣做是為了示範非同步方法中不是第一行之 \[**跳離函式**\] 命令的行為。  
  
3.  選擇 F5 鍵，或是在功能表列上選擇 \[**偵錯**\]、\[**開始偵錯**\] 啟動應用程式。  
  
     程式碼會在 `DoSomethingAsync` 方法中的 `Debug.WriteLine("before")` 上中斷。  
  
4.  選擇 Shift\+F11 鍵，或是選擇功能表列上的 \[**偵錯**\]、\[**跳離函式**\]。  
  
     應用程式會針對與目前方法相關聯的工作，在呼叫方法的 await 陳述式處中斷。  因此，應用程式會在 `ProcessAsync` 方法的 await 陳述式上中斷。  應用程式不會在 `Dim z = 0` \(Visual Basic\) 或 `int z = 0;` \(C\#\) 上中斷，這是接在 `DoSomethingAsync` 方法呼叫後面的程式碼。  
  
5.  選擇功能表列上的 \[**偵錯**\]、\[**停止偵錯**\]，停止應用程式執行。  
  
     下列步驟將示範從非同步方法的第一行 \[**跳離函式**\] 時會發生什麼情況。  
  
6.  移除現有的中斷點，然後在 `DoSomethingAsync` 方法的第一行上加入中斷點。  
  
     在 C\# 中，在 `DoSomethingAsync` 方法的左大括號上加入中斷點。  在 Visual Basic 中，在包含 `Async Function DoSomethingAsync() As Task(Of Integer)` 的程式行上加入中斷點。  
  
7.  選擇 F5 鍵以啟動應用程式。  
  
     程式碼會在 `DoSomethingAsync` 方法的第一行上中斷。  
  
8.  在功能表列上，選擇 \[**偵錯**\]、\[**視窗**\]、\[**輸出**\]。  
  
     \[**輸出**\] 視窗隨即開啟。  
  
9. 選擇 Shift\+F11 鍵，或是選擇功能表列上的 \[**偵錯**\]、\[**跳離函式**\]。  
  
     應用程式會繼續執行，直到非同步方法到達它的第一個 await，然後應用程式會在呼叫陳述式處中斷。  因此，應用程式會在 `Dim the Task = DoSomethingAsync()` \(Visual Basic\) 或 `var theTask = DoSomethingAsync();` \(C\#\) 中斷。  「之前」訊息出現在 \[輸出\] 視窗中，但是「之後」訊息尚未出現。  
  
10. 選擇 F5 鍵，繼續執行應用程式。  
  
     應用程式會繼續執行，而且陳述式會接在呼叫的非同步函式 \(`DoSomethingAsync`\) 中的 await 陳述式後面。  「之後」訊息會出現在 \[輸出\] 視窗中。  
  
## 請參閱  
 [使用偵錯工具巡覽程式碼](../Topic/Navigating%20through%20Code%20with%20the%20Debugger.md)