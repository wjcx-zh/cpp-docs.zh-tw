---
title: 部署、執行和偵錯 Linux 專案 | Microsoft Docs
ms.custom: ''
ms.date: 11/06/2017
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: f7084cdb-17b1-4960-b522-f84981bea879
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: b3f3742f8a63bf93f5686143daeea23ba13255be
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="deploy-run-and-debug-your-linux-project"></a>部署、執行和偵錯 Linux 專案

建立 Linux 專案並使用 [Linux 連線管理員](../linux/connect-to-your-remote-linux-computer.md)連線到專案後，即可執行與偵錯專案。 您可以在遠端目標上編譯、執行及偵錯程式碼。

有數種方式可以與 Linux 專案互動，並對其進行偵錯。

* 使用中斷點、監看式視窗以及將滑鼠指標停留在變數上等傳統 Visual Studio 功能進行偵錯。 使用這些方法，可讓您以對其他專案類型所使用的一般方式進行偵錯。
* 在特殊的主控台視窗中檢視目標電腦的輸出。 您也可以使用主控台將輸出傳送到目標電腦。

## <a name="debug-your-linux-project"></a>對 Linux 專案進行偵錯

1. 在 [偵錯] 屬性頁面中選取偵錯模式。

    GDB 用來偵錯在 Linux 上執行的應用程式。  不過，這可以透過兩種不同的模式執行，而您可以從專案 [偵錯] 屬性頁的 [偵錯模式] 選項中進行選取：

    ![GDB 選項](media/settings_debugger.png)

    - 在 **gdbserver** 模式中，GDB 會在本機執行，以連線到在遠端系統上執行的 gdbserver。  請注意，這是 Linux 主控台視窗唯一支援的模式。

    - 在 **gdb** 模式中，Visual Studio 偵錯工具會在遠端系統上驅動 GDB，這在本機與目標電腦上所安裝 GDB 的版本不同時較為相容。 |

    > [!NOTE] 
    > 若無法在 gdbserver 偵錯模式中叫用中斷電，請嘗試 gdb 模式。 必須先在遠端目標上[安裝](../linux/download-install-and-setup-the-linux-development-workload.md) gdb。

2. 在 Visual Studio 中使用標準 [偵錯] 工具列選取遠端目標。

    當遠端目標可用時，該目標會以名稱或 IP 位址的形式列出。

    ![遠端目標](media/remote_target.png)

    若尚未連線至遠端目標，您會看到使用 [Linux 連線管理員](../linux/connect-to-your-remote-linux-computer.md) 以連線到遠端目標的指示。

    ![遠端架構](media/architecture.png)

3. 在某些您認定會執行之程式碼的左側裝訂邊上按一下，即可設定中斷點。

    在您設定中斷點的程式碼上會顯示紅點。

4. 按一下 **F5** (或 [偵錯] > [開始偵錯]) 以開始偵錯。

    當您開始偵錯時，應用程式會在啟動前於遠端目標上編譯。 任何編譯錯誤都會顯示在 [錯誤清單] 視窗中。

    如果沒有任何錯誤，應用程式就會啟動，而偵錯工具則會在中斷點暫停。

    ![叫用中斷點](media/hit_breakpoint.png)  

    您現在可以和目前狀態下的應用程式互動、檢視變數，以及按下 **F10** 或 **F11** 等命令鍵逐步完成程式碼。

4. 若想使用 Linux 主控台與應用程式互動，請選取 [偵錯] > [Linux 主控台]。

  ![Linux 主控台功能表](media/consolemenu.png)

  此主控台將會顯示來自目標電腦的任何主控台輸出，以及接受輸入，並將其傳送至目標電腦。

  ![Linux 主控台視窗](media/consolewindow.png)

## <a name="configure-other-debugging-options"></a>設定其他偵錯選項

* 使用專案 [偵錯] 屬性頁中的 [程式引數] 項目，即可將命令列引數傳遞至可執行檔。
  
  ![程式引數](media/settings_programarguments.png)

* 使用 [其他偵錯工具命令] 項目，可以將特定偵錯工具選項傳遞至 GDB。  例如，您可能想要忽略 SIGILL (不合法指令) 訊號。  您可以使用 **handle** 命令來進行這項作業。  如上所示將下列項目新增至 [其他偵錯工具命令] 項目：

  ```handle SIGILL nostop noprint```

## <a name="next-steps"></a>後續步驟

* 若要在 Linux 上偵錯 ARM 裝置，請參閱此部落格文章：[Debugging an embedded ARM device in Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2018/01/10/debugging-an-embedded-arm-device-in-visual-studio/) (在 Visual Studio 中對內嵌 ARM 裝置進行偵錯)。

* 若要使用 **Attach to Process**命令進行偵錯，請參閱此部落格文章：[Linux C++ Workload improvements to the Project System, Linux Console Window, rsync and Attach to Process](https://blogs.msdn.microsoft.com/vcblog/2018/03/13/linux-c-workload-improvements-to-the-project-system-linux-console-window-rsync-and-attach-to-process/) (專案系統、Linux 主控台視窗、rsync 及附加至處理序的 Linux C++ 工作負載改善)。

## <a name="see-also"></a>另請參閱
[C++ 偵錯工具屬性 (Linux C++)](../linux/prop-pages/debugging-linux.md)。
