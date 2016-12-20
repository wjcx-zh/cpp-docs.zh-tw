---
title: "逐步解說：建立代理程式架構應用程式 | Microsoft Docs"
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
  - "非同步代理程式，建立"
  - "代理程式類別，範例"
ms.assetid: 730f42ce-6d58-4753-b948-fd9c9ef2ce6c
caps.latest.revision: 24
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 逐步解說：建立代理程式架構應用程式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主題說明如何建立基本的代理程式架構應用程式。  在這個逐步解說中，您可以建立會以非同步方式讀取文字檔資料的代理程式。  這個應用程式會使用 Adler\-32 總和檢查碼演算法來計算該檔案的內容總和檢查碼。  
  
## 必要條件  
 您必須了解下列主題，才能完成這個逐步解說：  
  
-   [非同步代理程式](../../parallel/concrt/asynchronous-agents.md)  
  
-   [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)  
  
-   [訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)  
  
-   [同步處理資料結構](../../parallel/concrt/synchronization-data-structures.md)  
  
##  <a name="top"></a> 章節  
 這個逐步解說示範如何執行下列工作：  
  
-   [建立主控台應用程式](#createApplication)  
  
-   [建立 file\_reader 類別](#createAgentClass)  
  
-   [在應用程式中使用 file\_reader 類別](#useAgentClass)  
  
##  <a name="createApplication"></a> 建立主控台應用程式  
 本節顯示如何建立 Visual C\+\+ 主控台應用程式，這個應用程式會參考程式要使用的標頭檔。  
  
#### 若要使用 Win32 主控台應用程式精靈建立 Visual C\+\+ 應用程式  
  
1.  按一下 \[**檔案**\] 功能表上的 \[**開新檔案**\]，然後按一下 \[**專案**\] 以顯示 \[**新增專案**\] 對話方塊。  
  
2.  在 \[**新增專案**\] 對話方塊中，選取 \[**專案類型**\] 窗格中的 \[**Visual C\+\+**\] 節點，然後選取 \[**範本**\] 窗格中的 \[**Win32 主控台應用程式**\]。  輸入專案的名稱 \(例如 `BasicAgent`\)，然後按一下 \[**確定**\] 以顯示 \[**Win32 主控台應用程式精靈**\]。  
  
3.  按一下 \[**Win32 主控台應用程式精靈**\] 對話方塊中的 \[**完成**\]。  
  
4.  在 stdafx.h 中，加入下列程式碼。  
  
     [!code-cpp[concrt-basic-agent#1](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_1.h)]  
  
     標頭檔 agents.h 包含 [concurrency::agent](../../parallel/concrt/reference/agent-class.md) 類別的功能。  
  
5.  建置並執行應用程式，以確認應用程式建立成功。  若要建置應用程式，請按一下 \[**建置**\] 功能表上的 \[**建置方案**\]。  如果應用程式建置成功，請按一下 \[**偵錯**\] 功能表上的 \[**開始偵錯**\] 執行應用程式。  
  
 \[[上方](#top)\]  
  
##  <a name="createAgentClass"></a> 建立 file\_reader 類別  
 本節顯示如何建立 `file_reader` 類別。  執行階段會排定每個代理程式在專屬的內容中執行工作。  因此，您可以建立會以同步方式執行工作，但是會以非同步方式與其他元件互動的代理程式。  `file_reader` 類別會讀取指定輸入檔中的資料，並將該檔案中的資料傳送至指定的目標元件。  
  
#### 若要建立 file\_reader 類別  
  
1.  將新的 C\+\+ 標頭檔加入至專案。  作法是以滑鼠右鍵按一下 \[**方案總管**\] 中的 \[**標頭檔**\] 節點，然後按一下 \[**加入**\]，再按一下 \[**新項目**\]。  選取 \[**範本**\] 窗格中的 \[**標頭檔 \(.h\)**\]。  在 \[**加入新項目**\] 對話方塊的 \[**名稱**\] 方塊中，輸入 `file_reader.h`，然後按一下 \[**加入**\]。  
  
2.  在 file\_reader.h 中，加入下列程式碼。  
  
     [!code-cpp[concrt-basic-agent#17](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_2.h)]  
  
3.  在 file\_reader.h 中，建立名為 `file_reader` 且衍生自 `agent` 的類別。  
  
     [!code-cpp[concrt-basic-agent#2](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_3.h)]  
  
4.  在類別的 `private` 區段中，加入下列資料成員。  
  
     [!code-cpp[concrt-basic-agent#3](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_4.h)]  
  
     `_file_name` 成員是代理程式所讀取的檔案名稱。  `_target` 成員是代理程式將檔案內容寫入至的 [concurrency::ITarget](../../parallel/concrt/reference/itarget-class.md) 物件。  `_error` 成員保留在代理程式的生命週期期間發生的任何錯誤。  
  
5.  將 `file_reader` 建構函式的下列程式碼加入至 `file_reader` 類別的 `public` 區段。  
  
     [!code-cpp[concrt-basic-agent#4](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_5.h)]  
  
     每個建構函式多載都會設定 `file_reader` 資料成員。  第二個和第三個建構函式多載可讓應用程式對代理程式使用特定排程器。  第一個多載會對代理程式使用預設排程器。  
  
6.  將 `get_error` 方法加入至 `file_reader` 類別的 public 區段。  
  
     [!code-cpp[concrt-basic-agent#5](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_6.h)]  
  
     `get_error` 方法會擷取在代理程式的生命週期期間發生的任何錯誤。  
  
7.  在類別的 `protected` 區段中，實作 [concurrency::agent::run](../Topic/agent::run%20Method.md) 方法。  
  
     [!code-cpp[concrt-basic-agent#6](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_7.h)]  
  
     `run` 方法會開啟檔案，並從中讀取資料。  `run` 方法會使用例外狀況處理，以擷取在檔案處理期間發生的任何錯誤。  
  
     每次這個方法在讀取檔案中的資料時，都會呼叫 [concurrency::asend](../Topic/asend%20Function.md) 函式，以將該資料傳送至目標緩衝區。  它會將空字串傳送至其目標緩衝區，來表示處理結束。  
  
 下列範例顯示 file\_reader.h 的完整內容。  
  
 [!code-cpp[concrt-basic-agent#7](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_8.h)]  
  
 \[[上方](#top)\]  
  
##  <a name="useAgentClass"></a> 在應用程式中使用 file\_reader 類別  
 本節顯示如何使用 `file_reader` 類別來讀取文字檔的內容。  其中也顯示如何建立 [concurrency::call](../../parallel/concrt/reference/call-class.md) 物件，這個物件會接收此檔案資料並計算其 Adler\-32 總和檢查碼。  
  
#### 若要在應用程式中使用 file\_reader 類別  
  
1.  在 BasicAgent.cpp 中，加入下列 `#include` 陳述式。  
  
     [!code-cpp[concrt-basic-agent#8](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_9.cpp)]  
  
2.  在 BasicAgent.cpp 中，加入下列 `using` 指示詞。  
  
     [!code-cpp[concrt-basic-agent#9](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_10.cpp)]  
  
3.  在 `_tmain` 函式中，建立表示處理結束的 [concurrency::event](../../parallel/concrt/reference/event-class.md) 物件。  
  
     [!code-cpp[concrt-basic-agent#10](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_11.cpp)]  
  
4.  建立會在收到資料時更新總和檢查碼的 `call` 物件。  
  
     [!code-cpp[concrt-basic-agent#11](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_12.cpp)]  
  
     這個 `call` 物件也會在收到表示處理結束的空字串時設定 `event` 物件。  
  
5.  建立 `file_reader` 物件，這個物件要會讀取 test.txt 檔案並將該檔案的內容寫入至 `call` 物件。  
  
     [!code-cpp[concrt-basic-agent#12](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_13.cpp)]  
  
6.  啟動代理程式，並等候它執行完成。  
  
     [!code-cpp[concrt-basic-agent#13](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_14.cpp)]  
  
7.  等候 `call` 物件收到所有資料並執行完成。  
  
     [!code-cpp[concrt-basic-agent#14](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_15.cpp)]  
  
8.  檢查檔案讀取器是否發生錯誤。  如果未發生錯誤，請計算最終的 Adler\-32 總和，並將總和列印至主控台。  
  
     [!code-cpp[concrt-basic-agent#15](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_16.cpp)]  
  
 下列範例顯示完整的 BasicAgent.cpp 檔。  
  
 [!code-cpp[concrt-basic-agent#16](../../parallel/concrt/codesnippet/CPP/walkthrough-creating-an-agent-based-application_17.cpp)]  
  
 \[[上方](#top)\]  
  
## 範例輸入  
 這是輸入檔 text.txt 的範例內容：  
  
  **The quick brown fox**  
**jumps**  
**over the lazy dog**   
## 範例輸出  
 與範例輸入搭配使用時，這個程式會產生下列輸出：  
  
  **Adler\-32 sum is fefb0d75**   
## 健全的程式設計  
 若要防止對資料成員的並行存取，建議您將實際執行工作的方法加入至類別的 `protected` 或 `private` 區段。  請只將會對代理程式傳送或接收訊息的方法加入至類別的 `public` 區段。  
  
 永遠呼叫 [concurrency::agent::done](../Topic/agent::done%20Method.md) 方法讓代理程式變成已完成狀態。  您通常會先呼叫這個方法，再從 `run` 方法返回。  
  
## 後續步驟  
 如需代理程式架構應用程式的另一個範例，請參閱[逐步解說：使用聯結以避免死結](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)。  
  
## 請參閱  
 [非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)   
 [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)   
 [訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)   
 [同步處理資料結構](../../parallel/concrt/synchronization-data-structures.md)   
 [逐步解說：使用聯結以避免死結](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)