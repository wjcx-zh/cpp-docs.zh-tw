---
title: "部署、執行和偵錯 Linux 專案 | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7084cdb-17b1-4960-b522-f84981bea879
author: BrianPeek
ms.author: brpeek
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: dff1e9e03911f65dfcffcd078e0739224f73f4aa
ms.openlocfilehash: db868094a8f10ad05ed6f95bf8a4c8a29a2c941e

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



<!--HONumber=Feb17_HO4-->


