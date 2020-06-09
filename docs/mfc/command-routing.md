---
title: 命令傳送
ms.date: 09/06/2019
helpviewer_keywords:
- MFC, command routing
- command handling [MFC], routing commands
- handlers [MFC]
- handlers, command [MFC]
- command routing
ms.assetid: 9393a956-bdd4-47c5-9013-dbd680433f93
ms.openlocfilehash: e47ffd38b342301da32abae9690738ef83c0426b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620685"
---
# <a name="command-routing"></a>命令傳送

您在使用命令時的責任僅限於在命令與其處理函式之間建立訊息對應連線，這是您使用[MFC 類別 Wizard](reference/mfc-class-wizard.md)的工作。 您也必須撰寫命令處理常式的程式碼。

Windows 訊息通常會傳送至主框架視窗，但命令訊息會接著路由傳送至其他物件。 此架構會將命令路由傳送通過標準順序的命令目標物件，其中一個物件應該會有該命令的處理常式。 每個命令目標物件會檢查其訊息對應，以確認是否可以處理傳入訊息。

不同的命令目標類別會在不同時間檢查自己的訊息對應。 一般而言，一個類別會將命令路由傳送至一些其他物件，讓它們有機會優先處理命令。 如果這些物件不會處理命令，則原始類別會檢查自己的訊息對應。 然後，如果其本身無法提供處理常式，則可能會將命令路由傳送至更多命令目標。 以下的 [標準命令路由](#_core_standard_command_route) 表格顯示每個類別如何建構此順序。 命令目標路由傳送命令的一般順序為︰

1. 至其目前作用中的子命令目標物件。

1. 至其本身。

1. 至其他命令目標。

相較于您的處理常式回應命令的方式，此路由機制的成本昂貴，路由的成本很低。 請記住，只有在使用者與使用者介面物件互動時，此架構才會產生命令。

### <a name="standard-command-route"></a><a name="_core_standard_command_route"></a> 標準命令路由

|當此類型的物件收到命令時。 . .|它會依照下列順序，提供機會給自己及其他命令目標物件來處理命令︰|
|----------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
|MDI 框架視窗 (`CMDIFrameWnd`)|1. 使用中`CMDIChildWnd`<br />2. 此框架視窗<br />3. 應用程式（ `CWinApp` 物件）|
|文件框架視窗 (`CFrameWnd`、 `CMDIChildWnd`)|1. 即時檢視<br />2. 此框架視窗<br />3. 應用程式（ `CWinApp` 物件）|
|檢視|1. 此視圖<br />2. 附加至視圖的檔|
|Document|1. 這份檔<br />2. 附加至檔的檔範本|
|對話方塊|1. 此對話方塊<br />2. 擁有對話方塊的視窗<br />3. 應用程式（ `CWinApp` 物件）|

在上表第二欄的編號項目提到其他物件 (例如文件) 的情況下，請參閱第一欄的對應項目。 例如，當您在第二欄中讀到「檢視將命令轉送至其文件」時，請參閱第一欄的「文件」項目以進一步路由傳送。

## <a name="see-also"></a>另請參閱

[架構如何呼叫處理常式](how-the-framework-calls-a-handler.md)
