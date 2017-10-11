---
title: "部署、執行和偵錯 Linux 專案 | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-linux
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7084cdb-17b1-4960-b522-f84981bea879
author: BrianPeek
ms.author: brpeek
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 1f36435bbb8238fb6068e7b58f9142eda62bc28c
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---

# <a name="deploy-run-and-debug-your-project"></a>部署、執行和偵錯專案

現在，建立專案時，您需要連線到 Linux 電腦，也就是會在其中編譯、執行和偵錯程式碼。

1. 如所示，使用 Visual Studio 中的標準下拉式清單來設定遠端目標架構：![遠端架構](media/architecture.png)

有數種方式可以與 Linux 專案互動，並對其進行偵錯。

* 傳統 Visual Studio 功能 (例如中斷點、監看式視窗，以及暫留變數) 都會如預期般運作，因此您可以如常進行偵錯。
* 您可以使用 [偵錯] > [Linux 主控台] 功能表項目來開啟特殊 [Linux 主控台] 視窗。

  ![Linux 主控台功能表](media/consolemenu.png)

  此主控台將會顯示來自目標電腦的任何主控台輸出，以及接受輸入，並將其傳送至目標電腦。

  ![Linux 主控台視窗](media/consolewindow.png)

* 使用專案 [偵錯] 屬性頁中的 [程式引數] 項目，即可將命令列引數傳遞至可執行檔。
  
  ![程式引數](media/settings_programarguments.png)

* GDB 用來偵錯在 Linux 上執行的應用程式。  不過，這可以透過兩種不同的模式執行，而您可以從專案 [偵錯] 屬性頁的 [偵錯模式] 選項中進行選取：

  ![GDB 選項](media/settings_debugger.png)

  | 選取範圍 | 說明
  | --------- | ---
  | gdbserver | GDB 會在本機執行，以連線到在遠端系統上執行的 gdbserver。  請注意，這是 Linux 主控台視窗唯一支援的模式。 
  | gdb       | Visual Studio 偵錯工具會在遠端系統上驅動 GDB，如果本機版本的 GDB 與目標電腦上安裝的版本不相符，則這較為相容

* 使用 [其他偵錯工具命令] 項目，可以將特定偵錯工具選項傳遞至 GDB。  例如，您可能想要忽略 SIGILL (不合法指令) 訊號。  您可以使用 **handle** 命令來進行這項作業。  如上所示將下列項目新增至 [其他偵錯工具命令] 項目：

  ```handle SIGILL nostop noprint```

