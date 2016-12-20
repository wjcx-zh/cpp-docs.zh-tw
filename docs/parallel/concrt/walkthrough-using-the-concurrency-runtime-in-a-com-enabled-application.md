---
title: "逐步解說：在啟用 COM 的應用程式中使用並行執行階段 | Microsoft Docs"
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
  - "並行執行階段, 搭配 COM 使用"
  - "COM, 搭配並行執行階段使用"
ms.assetid: a7c798b8-0fc8-4bee-972f-22ef158f7f48
caps.latest.revision: 14
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 逐步解說：在啟用 COM 的應用程式中使用並行執行階段
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件示範如何在採用元件物件模型 \(COM\) 的應用程式中使用並行執行階段。  
  
## 必要條件  
 在您開始閱讀此逐步解說前，請先參閱下列文件：  
  
-   [工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)  
  
-   [平行演算法](../../parallel/concrt/parallel-algorithms.md)  
  
-   [非同步代理程式](../../parallel/concrt/asynchronous-agents.md)  
  
-   [例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)  
  
 如需 COM 的詳細資訊，請參閱[元件物件模型 \(COM\)](http://msdn.microsoft.com/library/windows/desktop/ms680573)。  
  
## 管理 COM 程式庫的存留期  
 雖然 COM 與並行執行階段的搭配使用會遵循與任何其他並行機制相同的原則，但是下列方針可協助您有效地一起使用這些程式庫。  
  
-   執行緒必須在使用 COM 程式庫前先呼叫 [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279)。  
  
-   執行緒可以多次呼叫 `CoInitializeEx`，只要它在每一次呼叫時提供相同的引數即可。  
  
-   針對 `CoInitializeEx` 的每一次呼叫，執行緒還必須呼叫 [CoUninitialize](http://msdn.microsoft.com/library/windows/desktop/ms688715)。  換句話說，對 `CoInitializeEx` 和 `CoUninitialize` 的呼叫必須平衡。  
  
-   若要從某個執行緒 Apartment 切換至另一個執行緒 Apartment，執行緒必須在呼叫具有新執行緒規格的 `CoInitializeEx` 之前，先完全釋放 COM 程式庫。  
  
 當 COM 與並行執行階段搭配使用時，其他 COM 原則適用。  例如，在單一執行緒 Apartment \(STA\) 中建立物件並將該物件封送處理至另一個 Apartment 的應用程式，也必須提供訊息迴圈以處理傳入訊息。  另外請記得 Apartment 之間的物件封送處理會導致效能降低。  
  
### 搭配使用 COM 與平行模式程式庫  
 當您搭配使用 COM 與平行模式程式庫 \(PPL\) 中的元件 \(例如，工作群組或平行演算法\) 時，請在您於每一項工作或反覆運算期間使用 COM 程式庫之前呼叫 `CoInitializeEx`，並且在每一項工作或反覆運算完成前呼叫 `CoUninitialize`。  下列範例顯示如何使用 [concurrency::structured\_task\_group](../../parallel/concrt/reference/structured-task-group-class.md) 物件管理 COM 程式庫的存留期。  
  
 [!code-cpp[concrt-parallel-scripts#1](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_1.cpp)]  
  
 您必須確定在取消工作或平行演算法時或是在工作主體擲回例外狀況時，已正確地釋放 COM 程式庫。  若要保證工作在其結束前呼叫 `CoUninitialize`，請使用 `try-finally` 區塊或「*資源擷取為初始設定*」\(Resource Acquisition Is Initialization，RAII\) 模式。  下列範例會在工作完成或取消時，或是在例外狀況擲回時，使用 `try-finally` 區塊來釋放 COM 程式庫。  
  
 [!code-cpp[concrt-parallel-scripts#2](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_2.cpp)]  
  
 下列範例使用 RAII 模式來定義 `CCoInitializer` 類別，而該類別可在指定的範圍內管理 COM 程式庫的存留期。  
  
 [!code-cpp[concrt-parallel-scripts#3](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_3.cpp)]  
  
 您可以使用 `CCoInitializer` 類別，在工作結束時自動釋放 COM 程式庫，如下所述。  
  
 [!code-cpp[concrt-parallel-scripts#4](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_4.cpp)]  
  
 如需在並行執行階段中取消作業的詳細資訊，請參閱[取消](../../parallel/concrt/cancellation-in-the-ppl.md)。  
  
### 搭配使用 COM 與非同步代理程式  
 當您搭配使用 COM 與非同步代理程式時，請在 [concurrency::agent::run](../Topic/agent::run%20Method.md) 方法中使用 COM 程式庫之前，針對代理程式呼叫 `CoInitializeEx`。  然後在 `run` 方法傳回前呼叫 `CoUninitialize`。  請不要在代理程式的建構函式或解構函式中使用 COM 管理常式，而且不要覆寫 [concurrency::agent::start](../Topic/agent::start%20Method.md) 或 [concurrency::agent::done](../Topic/agent::done%20Method.md) 方法，因為這些方法是呼叫自與 `run` 方法不同的執行緒。  
  
 下列範例會顯示一個名為 `CCoAgent` 的基本代理程式，而該代理程式可以在 `run` 方法中管理 COM 程式庫。  
  
 [!code-cpp[concrt-parallel-scripts#5](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_5.cpp)]  
  
 本逐步解說稍後會提供完整的範例。  
  
### 搭配使用 COM 與輕量型工作  
 [工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md) 這份文件說明輕量型工作在並行執行階段中的角色。  您可以搭配使用 COM 與輕量型工作，就像搭配您在 Windows API 中傳遞至 `CreateThread` 函式的任何執行緒常式一樣。  這在下列範例中顯示。  
  
 [!code-cpp[concrt-parallel-scripts#6](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_6.cpp)]  
  
## 啟用 COM 的應用程式範例  
 本節顯示啟用 COM 的完整應用程式，而該應用程式會使用 `IScriptControl` 介面來執行可計算第 n 個 Fibonacci 數字的指令碼。  這個範例會先從主執行緒呼叫指令碼，然後使用 PPL 與代理程式同時呼叫指令碼。  
  
 請考慮下列 Helper 函式 `RunScriptProcedure`，這個函式會在 `IScriptControl` 物件中呼叫一個程序。  
  
 [!code-cpp[concrt-parallel-scripts#7](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_7.cpp)]  
  
 `wmain` 函式會建立 `IScriptControl` 物件，加入可計算第 n 個 Fibonacci 數字的指令碼，然後呼叫 `RunScriptProcedure` 函式以執行該指令碼。  
  
 [!code-cpp[concrt-parallel-scripts#8](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_8.cpp)]  
  
### 從 PPL 呼叫指令碼  
 下列函式 `ParallelFibonacci` 使用 [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) 演算法來平行呼叫指令碼。  此函式使用 `CCoInitializer` 類別管理 COM 程式庫在工作的每次反覆運算期間內的存留期。  
  
 [!code-cpp[concrt-parallel-scripts#9](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_9.cpp)]  
  
 若要將 `ParallelFibonacci` 函式用於此範例，請在 `wmain` 函式傳回前加入下列程式碼。  
  
 [!code-cpp[concrt-parallel-scripts#10](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_10.cpp)]  
  
### 從代理程式呼叫指令碼  
 下列範例顯示的 `FibonacciScriptAgent` 類別會呼叫指令碼程序來計算第 n 個 Fibonacci 數字。  `FibonacciScriptAgent` 類別會利用訊息傳遞將來自主程式的輸入值接收到指令碼函式。  `run` 方法可管理 COM 程式庫在整個工作期間內的留存期。  
  
 [!code-cpp[concrt-parallel-scripts#11](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_11.cpp)]  
  
 下列函式 \(`AgentFibonacci`\) 會建立數個 `FibonacciScriptAgent` 物件，並利用訊息傳遞將數個輸入值傳送至這些物件。  
  
 [!code-cpp[concrt-parallel-scripts#12](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_12.cpp)]  
  
 若要將 `AgentFibonacci` 函式用於此範例，請在 `wmain` 函式傳回前加入下列程式碼。  
  
 [!code-cpp[concrt-parallel-scripts#13](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_13.cpp)]  
  
### 完整的範例  
 下列程式碼顯示了完整的範例，而該範例使用平行演算法與非同步代理程式來呼叫可計算 Fibonacci 數字的指令碼程序。  
  
 [!code-cpp[concrt-parallel-scripts#14](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_14.cpp)]  
  
 這個範例 \(Example\) 會產生下列範例 \(Sample\) 輸出。  
  
  **主執行緒:**  
**fib\(15\) \= 610**  
**平行費氏數列:**  
**fib\(15\)\= 610**  
**fib\(10\)\= 55**  
**fib\(16\)\= 987**  
**fib\(18\)\= 2584**  
**fib\(11\)\= 89**  
**fib\(17\)\= 1597**  
**fib\(19\)\= 4181**  
**fib\(12\)\= 144**  
**fib\(13\)\= 233**  
**fib\(14\)\= 377**  
**代理程式費氏數列:**  
**fib\(30\)\= 832040**  
**fib\(22\)\= 17711**  
**fib\(10\)\= 55**  
**fib\(12\)\= 144**   
## 編譯程式碼  
 請複製範例程式碼並將它貼在 Visual Studio 專案中，或是貼在名為 `parallel-scripts.cpp` 的檔案中，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 **cl.exe \/EHsc parallel\-scripts.cpp \/link ole32.lib**  
  
## 請參閱  
 [並行執行階段逐步解說](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [工作平行處理原則](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [平行演算法](../../parallel/concrt/parallel-algorithms.md)   
 [非同步代理程式](../../parallel/concrt/asynchronous-agents.md)   
 [例外狀況處理](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [取消](../../parallel/concrt/cancellation-in-the-ppl.md)   
 [工作排程器](../../parallel/concrt/task-scheduler-concurrency-runtime.md)