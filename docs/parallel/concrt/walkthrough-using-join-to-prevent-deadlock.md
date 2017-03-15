---
title: "逐步解說：使用聯結以避免死結 | Microsoft Docs"
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
  - "使用聯結避免死結 [並行執行階段]"
  - "死結，避免 [並行執行階段]"
  - "非窮盡聯結，範例"
  - "聯結類別，範例"
ms.assetid: d791f697-bb93-463e-84bd-5df1651b7446
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# 逐步解說：使用聯結以避免死結
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主題會使用哲學家用餐問題，說明如何使用 [concurrency::join](../../parallel/concrt/reference/join-class.md) 類別來避免應用程式中的死結。  在軟體應用程式中，如果有兩個以上的處理序各擁有一項資源，而互相等候另一個處理序釋放另一項資源，即會發生「*死結*」\(Deadlock\)。  
  
 我們常用哲學家用餐問題做為特定範例，說明多個並行處理序之間共用一組資源時可能會發生的一般問題集。  
  
## 必要條件  
 在您開始閱讀此逐步解說前，請先參閱下列主題：  
  
-   [非同步代理程式](../../parallel/concrt/asynchronous-agents.md)  
  
-   [逐步解說：建立代理程式架構應用程式](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)  
  
-   [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)  
  
-   [訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)  
  
-   [同步處理資料結構](../../parallel/concrt/synchronization-data-structures.md)  
  
##  <a name="top"></a> 章節  
 此逐步解說包含下列章節：  
  
-   [哲學家用餐問題](#problem)  
  
-   [直覺實作](#deadlock)  
  
-   [使用聯結以避免死結](#solution)  
  
##  <a name="problem"></a> 哲學家用餐問題  
 哲學家用餐問題說明了應用程式中為何會發生死結。  在此問題中，有五位哲學家圍坐在一個圓桌。  每位哲學家各交替著思考與用餐的動作。  每位哲學家都必須與左邊的哲學家共用一根筷子，與右邊的哲學家也必須共用一根筷子。  下圖顯示其座位配置。  
  
 ![哲學家用餐問題](../../parallel/concrt/media/dining_philosophersproblem.png "Dining\_PhilosophersProblem")  
  
 哲學家必須同時擁有兩根筷子，才能用餐。  如果每個哲學家各有一根筷子，而都在等候另一根，則沒有哲學家可以用餐，大家都得挨餓。  
  
 \[[上方](#top)\]  
  
##  <a name="deadlock"></a> 直覺實作  
 下列範例說明哲學家用餐問題的直覺實作。  衍生自 [concurrency::agent](../../parallel/concrt/reference/agent-class.md) 的 `philosopher` 類別，可讓每一位哲學家獨立執行動作。  此範例使用 [concurrency::critical\_section](../../parallel/concrt/reference/critical-section-class.md) 物件的共用陣列，給予每個 `philosopher` 物件獨佔存取一雙筷子的權限。  
  
 我們以 `philosopher` 類別代表一個哲學家，說明實作與圖例的關聯性。  `int` 變數代表每根筷子。  `critical_section` 物件做為筷子的持有者。  `run` 方法模擬哲學家的生命。  `think` 方法模擬思考的動作，`eat` 方法則模擬用餐的動作。  
  
 `philosopher` 在呼叫 `eat` 方法前，會先同時鎖定前述兩個 `critical_section` 物件，以模擬從持有者手中拿走筷子的動作。  在呼叫 `eat` 之後，`philosopher` 物件會將 `critical_section` 物件重新設為未鎖定的狀態，將筷子歸還給持有者。  
  
 `pickup_chopsticks` 方法說明可能會發生死結的情況。  如果每個 `philosopher` 物件皆取得其中一個鎖定的存取權，則沒有任何 `philosopher` 物件可繼續動作，因為另一個鎖定皆由其他 `philosopher` 物件所控制。  
  
## 範例  
  
### 說明  
  
### 程式碼  
 [!code-cpp[concrt-philosophers-deadlock#1](../../parallel/concrt/codesnippet/CPP/walkthrough-using-join-to-prevent-deadlock_1.cpp)]  
  
## 編譯程式碼  
 請複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼在名為 `philosophers-deadlock.cpp` 的檔案中，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 **cl.exe \/EHsc philosophers\-deadlock.cpp**  
  
 \[[上方](#top)\]  
  
##  <a name="solution"></a> 使用聯結以避免死結  
 本節說明如何使用訊息緩衝區和訊息傳遞函式消除死結的可能性。  
  
 為使此範例與前一個範例產生關聯，`philosopher` 類別會使用 [concurrency::unbounded\_buffer](../Topic/unbounded_buffer%20Class.md) 物件與 `join` 物件取代每一個 `critical_section` 物件。  `join` 物件做為將筷子提供給哲學家的仲裁者。  
  
 此範例會使用 `unbounded_buffer` 類別，因為當目標接收到來自 `unbounded_buffer` 物件的訊息時，該訊息會從訊息佇列中移除。  這可讓保有訊息的 `unbounded_buffer` 物件指出筷子處於可用狀態。  未獲得訊息的 `unbounded_buffer` 物件則會指出有人正在使用筷子。  
  
 此範例會使用非窮盡 \(non\-greedy\) `join` 物件，因為非窮盡聯結只有在兩個 `unbounded_buffer` 物件都包含訊息時，才會給予每個 `philosopher` 物件兩根筷子的存取權。  窮盡 \(greedy\) 聯結不會避免死結，因為只要一有訊息，窮盡聯結就會立即接受。  如果所有窮盡 `join` 物件都接收其中一個訊息，但無止盡地等待另一個訊息變成可用訊息，就會發生死結。  
  
 如需窮盡和非窮盡聯結的詳細資訊，以及各種訊息緩衝區類型之間的差異資訊，請參閱[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)。  
  
#### 若要在此範例中避免死結  
  
1.  從範例中移除下列程式碼。  
  
     [!code-cpp[concrt-philosophers-deadlock#2](../../parallel/concrt/codesnippet/CPP/walkthrough-using-join-to-prevent-deadlock_2.cpp)]  
  
2.  將 `philosopher` 類別之 `_left` 和 `_right` 資料成員的類型變更為 `unbounded_buffer`。  
  
     [!code-cpp[concrt-philosophers-join#2](../../parallel/concrt/codesnippet/CPP/walkthrough-using-join-to-prevent-deadlock_3.cpp)]  
  
3.  修改 `philosopher` 建構函式，以 `unbounded_buffer` 物件做為其參數。  
  
     [!code-cpp[concrt-philosophers-join#3](../../parallel/concrt/codesnippet/CPP/walkthrough-using-join-to-prevent-deadlock_4.cpp)]  
  
4.  修改 `pickup_chopsticks` 方法，以使用非窮盡 `join` 物件接收來自一雙筷子之訊息緩衝區的訊息。  
  
     [!code-cpp[concrt-philosophers-join#4](../../parallel/concrt/codesnippet/CPP/walkthrough-using-join-to-prevent-deadlock_5.cpp)]  
  
5.  修改 `putdown_chopsticks` 方法，將訊息傳送至一雙筷子的訊息緩衝區，以釋放筷子的存取權。  
  
     [!code-cpp[concrt-philosophers-join#5](../../parallel/concrt/codesnippet/CPP/walkthrough-using-join-to-prevent-deadlock_6.cpp)]  
  
6.  修改 `run` 方法以保有 `pickup_chopsticks` 方法的結果，並將這些結果傳遞至 `putdown_chopsticks` 方法。  
  
     [!code-cpp[concrt-philosophers-join#6](../../parallel/concrt/codesnippet/CPP/walkthrough-using-join-to-prevent-deadlock_7.cpp)]  
  
7.  將 `wmain` 函式中的 `chopsticks` 變數宣告修改成各包含一則訊息之 `unbounded_buffer` 物件的陣列。  
  
     [!code-cpp[concrt-philosophers-join#7](../../parallel/concrt/codesnippet/CPP/walkthrough-using-join-to-prevent-deadlock_8.cpp)]  
  
## 範例  
  
### 說明  
 以下顯示使用非窮盡 `join` 物件消除死結風險的完整範例。  
  
### 程式碼  
 [!code-cpp[concrt-philosophers-join#1](../../parallel/concrt/codesnippet/CPP/walkthrough-using-join-to-prevent-deadlock_9.cpp)]  
  
### 註解  
 這個範例產生下列輸出。  
  
  **衙里斯多德吃了 50 次。**  
**迪卡爾吃了 50 次。**  
**哈比斯吃了 50 次。**  
**蘇格拉底 吃了 50 次。**  
**柏拉圖吃了 50 次。**   
## 編譯程式碼  
 請複製範例程式碼，並將它貼在 Visual Studio 專案中，或貼在名為  `philosophers-join.cpp` 的檔案中，然後在 Visual Studio 的 \[命令提示字元\] 視窗中執行下列命令。  
  
 **cl.exe \/EHsc philosophers\-join.cpp**  
  
 \[[上方](#top)\]  
  
## 請參閱  
 [並行執行階段逐步解說](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)   
 [非同步代理程式](../../parallel/concrt/asynchronous-agents.md)   
 [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)   
 [訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)   
 [同步處理資料結構](../../parallel/concrt/synchronization-data-structures.md)