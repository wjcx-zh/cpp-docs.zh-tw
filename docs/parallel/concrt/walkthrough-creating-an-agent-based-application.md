---
title: 逐步解說：建立代理程式架構應用程式
ms.date: 04/25/2019
helpviewer_keywords:
- asynchronous agents, creating
- agent class, example
ms.assetid: 730f42ce-6d58-4753-b948-fd9c9ef2ce6c
ms.openlocfilehash: 20197786e3d3c2d34d29af748c1cc073902cf70d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377449"
---
# <a name="walkthrough-creating-an-agent-based-application"></a>逐步解說：建立代理程式架構應用程式

本主題介紹如何創建基於代理的基本應用程式。 在本演練中,您可以創建一個代理,該代理以非同步方式從文本檔讀取資料。 應用程式使用 Adler-32 檢驗和演算法計算該檔內容的驗證和。

## <a name="prerequisites"></a>Prerequisites

您必須瞭解以下主題才能完成這個演練:

- [非同步代理](../../parallel/concrt/asynchronous-agents.md)

- [非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)

- [訊息傳遞函數](../../parallel/concrt/message-passing-functions.md)

- [同步處理資料結構](../../parallel/concrt/synchronization-data-structures.md)

## <a name="sections"></a><a name="top"></a>部分

這個演練示範如何執行以下工作:

- [建立主控台應用程式](#createapplication)

- [建立file_reader類](#createagentclass)

- [在應用程式中使用file_reader類](#useagentclass)

## <a name="creating-the-console-application"></a><a name="createapplication"></a>建立主控台應用程式

本節演示如何創建C++控制台應用程式,該應用程式引用程式將使用的標頭檔。 初始步驟因您使用的 Visual Studio 版本而異。 要查看您首選版本的 Visual Studio 的文件,請使用**版本**選擇器控制項。 它位於此頁面的目錄頂部。

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-application-in-visual-studio-2019"></a>在 Visual Studio 2019 建立C++主控台應用程式

1. 從主功能表，選擇 [檔案]** [新增]** > ** [專案]** > ****，以開啟 [建立新專案]**** 對話方塊。

1. 在對話方塊頂端，將 [語言]**** 設定為 **C++**，將 [平台]**** 設定為 **Windows**，並將 [專案類型]**** 設定為**主控台**。

1. 從專案類型的篩選清單中，選擇 [主控台應用程式]****，然後選擇 [下一步]****。 在下一頁中,輸入`BasicAgent`為專案的名稱,並根據需要指定專案位置。

1. 選擇 [建立] **** 按鈕以建立專案。

1. 右鍵按下**解決方案資源管理員**中的項目節點,然後選擇**屬性**。 在**配置屬性** > **C/C++** > **預編譯標頭** > **下,預編譯標頭**選擇 **「創建**」。。

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-c-console-application-in-visual-studio-2017-and-earlier"></a>在 Visual Studio 2017 和更早版本中創建C++控制台應用程式

1. 在「**檔案**」 選單上,按下 **「新建**」,然後按下 **「專案**」以顯示 **「新專案**」對話框。

1. 在「**新項目**」 對話框中,在 **「項目類型**」 的窗格中選擇 **「可視C++」** 節點,然後在 **「樣本」** 窗格中選擇**Win32 主控台應用程式**。 鍵入項目的名稱,例如,`BasicAgent`然後按下 **「確定」** 以顯示**Win32 主控台應用程式精靈**。

1. 在**Win32 主控台應用程式精靈**對話框中,按一下「**完成**」。

::: moniker-end

1. 在*pch.h(Visual* Studio 2017 和更早版本中的*stdafx.h)* 中,添加以下代碼:

[!code-cpp[concrt-basic-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_1.h)]

   標頭檔代理.h 包含[併發::代理](../../parallel/concrt/reference/agent-class.md)類的功能。

1. 通過生成並運行應用程式,驗證應用程式是否成功創建。 要生成應用程式,請在 **「生成」** 功能表上單擊 **「生成解決方案**」 。 如果應用程式生成成功,則通過按下 **「調試」** 功能表上的 **「開始調試**」來運行應用程式。

【[頂端](#top)

## <a name="creating-the-file_reader-class"></a><a name="createagentclass"></a>建立file_reader類

完成如何建立類別`file_reader`。 運行時計劃每個代理在其自己的上下文中執行工作。 因此,您可以創建同步執行工作的代理,但與其他元件異步交互。 類`file_reader`從給定的輸入檔讀取數據,並將數據從該檔發送到給定的目標元件。

#### <a name="to-create-the-file_reader-class"></a>建立file_reader類

1. 向專案添加新C++頭檔。 為此,請右鍵單擊**解決方案資源管理員**中的 **「標題檔**」節點,按下「**添加**」,然後單擊 **「新專案**」 。 在 **「樣本」** 窗格中,選擇 **「標題檔案 」(.h)**。 在「**新增新項目」** 對話方塊`file_reader.h`中,在 **「名稱」** 框中鍵入,然後按下「**添加**」 。。

1. 在 file_reader.h 中,添加以下代碼。

[!code-cpp[concrt-basic-agent#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_2.h)]

1. 在 file_reader.h 中,創建派`file_reader``agent`生自的命名類。

[!code-cpp[concrt-basic-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_3.h)]

1. 將以下數據成員添加到類的`private`部分。

[!code-cpp[concrt-basic-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_4.h)]

   成員`_file_name`是代理從中讀取的檔名。 成員`_target`是一個[併發::ITarget](../../parallel/concrt/reference/itarget-class.md)物件,代理將文件的內容寫入。 成員`_error`保留在代理生命週期內發生的任何錯誤。

1. 將建構函數的`file_reader`以下代碼添加`public``file_reader`到類的節。

[!code-cpp[concrt-basic-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_5.h)]

   每個構造函數重載設置`file_reader`數據成員。 第二個和第三個構造函數重載使應用程式能夠將特定的計劃程式與代理一起使用。 第一個重載使用預設計畫程式與代理。

1. 將`get_error`方法添加到`file_reader`類的公共部分。

[!code-cpp[concrt-basic-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_6.h)]

   該方法`get_error`檢索代理生命週期期間發生的任何錯誤。

1. 在類`protected`的節中實現[併發::代理::運行](reference/agent-class.md#run)方法。

[!code-cpp[concrt-basic-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_7.h)]

該方法`run`打開檔並從中讀取數據。 該方法`run`使用異常處理來捕獲檔處理期間發生的任何錯誤。

   每次此方法從檔中讀取數據時,它調用[併發::asend](reference/concurrency-namespace-functions.md#asend)函數以將數據發送到目標緩衝區。 它將空字串發送到其目標緩衝區,以指示處理的結束。

下面的示例顯示了 file_reader.h 的完整內容。

[!code-cpp[concrt-basic-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_8.h)]

【[頂端](#top)

## <a name="using-the-file_reader-class-in-the-application"></a><a name="useagentclass"></a>在應用程式中使用file_reader類

本節演示如何使用`file_reader`類 讀取文本文件的內容。 它還演示如何創建[併發::呼叫](../../parallel/concrt/reference/call-class.md)物件,該物件接收此文件資料並計算其 Adler-32 驗證和。

#### <a name="to-use-the-file_reader-class-in-your-application"></a>在應用程式中使用file_reader類

1. 在 BasicAgent.cpp`#include`中, 添加以下語句。

[!code-cpp[concrt-basic-agent#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_9.cpp)]

1. 在 BasicAgent.cpp`using`中, 添加以下指令。

[!code-cpp[concrt-basic-agent#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_10.cpp)]

1. 在`_tmain`函數中,創建一個[併發::事件](../../parallel/concrt/reference/event-class.md)物件,該物件表示處理結束的信號。

[!code-cpp[concrt-basic-agent#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_11.cpp)]

1. 創建在`call`接收數據時更新校驗和的物件。

[!code-cpp[concrt-basic-agent#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_12.cpp)]

   此`call`物件在接收`event`空 字串時還會設置物件以發出處理結束的信號。

1. 創建從`file_reader`檔案 test.txt 讀取的物件,並將該檔`call`的內容寫入 物件。

[!code-cpp[concrt-basic-agent#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_13.cpp)]

1. 啟動代理並等待它完成。

[!code-cpp[concrt-basic-agent#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_14.cpp)]

1. 等待`call`物件接收所有數據並完成。

[!code-cpp[concrt-basic-agent#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_15.cpp)]

1. 檢查文件讀取器是否存在錯誤。 如果未發生錯誤,請計算最終的 Adler-32 總和,並將總和列印到主控台。

[!code-cpp[concrt-basic-agent#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_16.cpp)]

下面的範例顯示了完整的 BasicAgent.cpp 檔。

[!code-cpp[concrt-basic-agent#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_17.cpp)]

【[頂端](#top)

## <a name="sample-input"></a>範例輸入

這是輸入檔案文字.txt 的範例內容:

```Output
The quick brown fox
jumps
over the lazy dog
```

## <a name="sample-output"></a>範例輸出

當與範例輸入一起使用時,此程式會產生以下輸出:

```Output
Adler-32 sum is fefb0d75
```

## <a name="robust-programming"></a>穩固程式設計

為了防止對數據成員的併發訪問,我們建議您向類`protected`的`private`或部分添加執行工作的方法。 僅將發送或接收消息的方法發送到類的`public`子部分或從代理發送到類的分區。

始終調用[併發::代理::d一](reference/agent-class.md#done)種將代理移動到已完成狀態的方法。 通常,在從方法返回之前調用`run`此方法。

## <a name="next-steps"></a>後續步驟

有關基於代理的應用程式的另一個範例,請參閱[演練:使用聯接來防止死鎖](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)。

## <a name="see-also"></a>另請參閱

[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[非同步訊息區](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[訊息傳遞函數](../../parallel/concrt/message-passing-functions.md)<br/>
[同步處理資料結構](../../parallel/concrt/synchronization-data-structures.md)<br/>
[逐步解說：使用聯結以避免死結](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)
