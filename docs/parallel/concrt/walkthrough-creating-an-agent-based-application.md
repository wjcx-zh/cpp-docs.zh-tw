---
title: 逐步解說： 建立代理程式為基礎的應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- asynchronous agents, creating
- agent class, example
ms.assetid: 730f42ce-6d58-4753-b948-fd9c9ef2ce6c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 78826bb9f00e77a80fb65dd3a3ceda7eedb38796
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="walkthrough-creating-an-agent-based-application"></a>逐步解說：建立代理程式架構應用程式
本主題描述如何建立基本的代理程式架構應用程式。 在本逐步解說，您可以建立以非同步方式從文字檔讀取資料的代理程式。 應用程式使用 adler-32 總和檢查碼演算法計算總和檢查碼的該檔案的內容。  
  
## <a name="prerequisites"></a>必要條件  
 您必須了解下列主題，以完成此逐步解說：  
  
- [非同步代理程式](../../parallel/concrt/asynchronous-agents.md)  
  
- [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)  
  
- [訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)  
  
- [同步處理資料結構](../../parallel/concrt/synchronization-data-structures.md)  
  
##  <a name="top"></a> 章節  
 本逐步解說示範如何執行下列工作：  
  
- [建立主控台應用程式](#createapplication)  
  
- [建立 file_reader 類別](#createagentclass)  
  
- [應用程式中使用 file_reader 類別](#useagentclass)  
  
##  <a name="createapplication"></a> 建立主控台應用程式  
 本節說明如何建立參考的程式將使用的標頭檔的 Visual c + + 主控台應用程式。  
  
#### <a name="to-create-a-visual-c-application-by-using-the-win32-console-application-wizard"></a>若要使用 Win32 主控台應用程式精靈建立的 Visual c + + 應用程式  
  
1.  上**檔案**功能表上，按一下 **新增**，然後按一下 **專案**顯示**新專案** 對話方塊。  
  
2.  在**新專案**對話方塊中，選取**Visual c + +** 節點**專案類型**窗格，然後選取**Win32 主控台應用程式**在**範本**窗格。 例如，輸入專案的名稱`BasicAgent`，然後按一下**確定**顯示**Win32 主控台應用程式精靈**。  
  
3.  在**Win32 主控台應用程式精靈**對話方塊中，按一下 **完成**。  
  
4.  在 stdafx.h，加入下列程式碼。  
  
 [!code-cpp[concrt-basic-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_1.h)]  
  
     標頭檔 agents.h 包含的功能[concurrency:: agent](../../parallel/concrt/reference/agent-class.md)類別。  
  
5.  請確認應用程式已成功建立，方式是建立並執行它。 在建置應用程式，**建置**功能表上，按一下 **建置方案**。 如果應用程式建置成功，則執行應用程式，即可**開始偵錯**上**偵錯**功能表。  
  
 [[靠上](#top)]  
  
##  <a name="createagentclass"></a> 建立 file_reader 類別  
 本節示範如何建立`file_reader`類別。 執行階段排程是在自己的內容中執行工作的每個代理程式。 因此，您可以建立代理程式會執行的工作同步，但以非同步方式與其他元件互動。 `file_reader`類別從給定的輸入檔讀取資料，並從該檔案將資料傳送到給定的目標元件。  
  
#### <a name="to-create-the-filereader-class"></a>若要建立 file_reader 類別  
  
1.  將新的 c + + 標頭檔加入至您的專案。 若要這樣做，請以滑鼠右鍵按一下**標頭檔**節點**方案總管 中**，按一下 **新增**，然後按一下 **新項目**。 在**範本**窗格中，選取**標頭檔 (.h)**。 在**加入新項目** 對話方塊中，輸入`file_reader.h`中**名稱**方塊，然後按一下**新增**。  
  
2.  在 file_reader.h，加入下列程式碼。  
  
 [!code-cpp[concrt-basic-agent#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_2.h)]  
  
3.  File_reader.h，在建立類別，名為`file_reader`衍生自`agent`。  
  
 [!code-cpp[concrt-basic-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_3.h)]  
  
4.  將下列資料成員加入`private`> 一節，您的類別。  
  
 [!code-cpp[concrt-basic-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_4.h)]  
  
     `_file_name`成員是從代理程式讀取的檔案名稱。 `_target`成員是[concurrency:: itarget](../../parallel/concrt/reference/itarget-class.md)物件代理程式寫入至檔案的內容。 `_error`成員保留代理程式的生命期限內，就會發生任何錯誤。  
  
5.  加入下列程式碼`file_reader`建構函式來`public`區段`file_reader`類別。  
  
 [!code-cpp[concrt-basic-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_5.h)]  
  
     設定每個建構函式多載`file_reader`資料成員。 第二個和第三個建構函式多載可讓您的應用程式與代理程式使用特定排程器。 第一個多載會使用代理程式的預設排程器。  
  
6.  新增`get_error`方法的公用區段`file_reader`類別。  
  
 [!code-cpp[concrt-basic-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_6.h)]  
  
     `get_error`方法會擷取代理程式的生命期限內，就會發生任何錯誤。  
  

7.  實作[concurrency::agent::run](reference/agent-class.md#run)方法中的`protected`> 一節，您的類別。  

  
 [!code-cpp[concrt-basic-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_7.h)]  
  
`run`方法開啟的檔案，並從其讀取資料。 `run`方法使用例外狀況處理來擷取檔案處理期間發生任何錯誤。  
  
   它會呼叫這個方法會從檔案讀取資料的每次[concurrency:: asend](reference/concurrency-namespace-functions.md#asend)函式將該資料傳送至目標緩衝區。 會傳送空字串，表示處理結束其目標緩衝區。  

  
 下列範例顯示 file_reader.h 的完整內容。  
  
 [!code-cpp[concrt-basic-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_8.h)]  
  
 [[靠上](#top)]  
  
##  <a name="useagentclass"></a> 應用程式中使用 file_reader 類別  
 本節示範如何使用`file_reader`類別，以讀取文字檔的內容。 它也示範如何建立[concurrency:: call](../../parallel/concrt/reference/call-class.md)接收這個檔案資料並計算其 adler-32 總和檢查碼的物件。  
  
#### <a name="to-use-the-filereader-class-in-your-application"></a>在您的應用程式中使用 file_reader 類別  
  
1.  在 BasicAgent.cpp，加入下列`#include`陳述式。  
  
 [!code-cpp[concrt-basic-agent#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_9.cpp)]  
  
2.  在 BasicAgent.cpp，加入下列`using`指示詞。  
  
 [!code-cpp[concrt-basic-agent#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_10.cpp)]  
  
3.  在`_tmain`函式中，建立[concurrency:: event](../../parallel/concrt/reference/event-class.md)表示處理結束的物件。  
  
 [!code-cpp[concrt-basic-agent#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_11.cpp)]  
  
4.  建立`call`接收資料時，更新總和檢查碼的物件。  
  
 [!code-cpp[concrt-basic-agent#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_12.cpp)]  
  
     這`call`物件也會設定`event`收到空的字串來表示處理結束時的物件。  
  
5.  建立`file_reader`物件可從檔案 test.txt 讀取和寫入至該檔案的內容`call`物件。  
  
 [!code-cpp[concrt-basic-agent#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_13.cpp)]  
  
6.  啟動代理程式，並等候它完成。  
  
 [!code-cpp[concrt-basic-agent#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_14.cpp)]  
  
7.  等候`call`接收所有資料並完成的物件。  
  
 [!code-cpp[concrt-basic-agent#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_15.cpp)]  
  
8.  請檢查錯誤的檔案讀取器。 如果未發生錯誤，計算最終的 adler-32 總和，並列印到主控台的總和。  
  
 [!code-cpp[concrt-basic-agent#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_16.cpp)]  
  
 下列範例會示範完整的 BasicAgent.cpp 檔案。  
  
 [!code-cpp[concrt-basic-agent#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_17.cpp)]  
  
 [[靠上](#top)]  
  
## <a name="sample-input"></a>輸入範例  
 這是輸入的檔 text.txt 的範例內容：  
  
```Output  
The quick brown fox  
jumps  
over the lazy dog  
```  
  
## <a name="sample-output"></a>範例輸出  
 輸入範例搭配使用時，此程式會產生下列輸出：  
  
```Output  
Adler-32 sum is fefb0d75  
```  
  
## <a name="robust-programming"></a>穩固程式設計  
 若要防止資料成員的並行存取，我們建議您新增方法執行的工作來`protected`或`private`> 一節，您的類別。 只能新增傳送或接收訊息或代理程式的方法`public`> 一節，您的類別。  
  

 請務必呼叫[concurrency:: agent:: 完成](reference/agent-class.md#done)方法來移動您的代理程式已完成狀態。 您通常呼叫這個方法，才能從傳回`run`方法。  

  
## <a name="next-steps"></a>後續步驟  
 如需代理程式為基礎的應用程式的其他範例，請參閱[逐步解說： 使用聯結以避免死結](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)。  
  
## <a name="see-also"></a>另請參閱  
 [非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)   
 [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)   
 [訊息傳遞函式](../../parallel/concrt/message-passing-functions.md)   
 [同步處理資料結構](../../parallel/concrt/synchronization-data-structures.md)   
 [逐步解說：使用聯結以避免死結](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)

