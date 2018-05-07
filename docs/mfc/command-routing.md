---
title: 命令路由 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, command routing
- command handling [MFC], routing commands
- handlers [MFC]
- handlers, command [MFC]
- command routing
ms.assetid: 9393a956-bdd4-47c5-9013-dbd680433f93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ecb836f8fee1efab7f5f925c6ec3ce0f470d666b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="command-routing"></a>命令傳送
處理命令時，您只需負責在命令與其處理函式之間建立訊息對應連接，而這項工作可透過 [屬性] 視窗來完成。 您也必須撰寫大部分的命令處理常式。  
  
 Windows 訊息通常會傳送至主框架視窗，但命令訊息會接著路由傳送至其他物件。 此架構會將命令路由傳送通過標準順序的命令目標物件，其中一個物件應該會有該命令的處理常式。 每個命令目標物件會檢查其訊息對應，以確認是否可以處理傳入訊息。  
  
 不同的命令目標類別會在不同時間檢查自己的訊息對應。 一般而言，一個類別會將命令路由傳送至一些其他物件，讓它們有機會優先處理命令。 如果這些物件不會處理命令，則原始類別會檢查自己的訊息對應。 然後，如果其本身無法提供處理常式，則可能會將命令路由傳送至更多命令目標。 以下的 [標準命令路由](#_core_standard_command_route) 表格顯示每個類別如何建構此順序。 命令目標路由傳送命令的一般順序為︰  
  
1.  至其目前作用中的子命令目標物件。  
  
2.  至其本身。  
  
3.  至其他命令目標。  
  
 您如何的處理常式未回應命令此路由機制比較的昂貴，路由的成本很低。 請記住，只有在使用者與使用者介面物件互動時，此架構才會產生命令。  
  
### <a name="_core_standard_command_route"></a> 標準命令路由  
  
|當此類型的物件收到命令時。 。 。|它會依照下列順序，提供機會給自己及其他命令目標物件來處理命令︰|  
|----------------------------------------------------------|-----------------------------------------------------------------------------------------------------|  
|MDI 框架視窗 (`CMDIFrameWnd`)|1.使用中 `CMDIChildWnd`<br />2.此框架視窗<br />3.應用程式 (`CWinApp`物件)|  
|文件框架視窗 (`CFrameWnd`、 `CMDIChildWnd`)|1.現用檢視表<br />2.此框架視窗<br />3.應用程式 (`CWinApp`物件)|  
|檢視|1.此檢視<br />2.附加至檢視的文件|  
|文件|1.此文件<br />2.附加至文件的文件範本|  
|對話方塊|1.此對話方塊<br />2.擁有此對話方塊的視窗<br />3.應用程式 (`CWinApp`物件)|  
  
 在上表第二欄的編號項目提到其他物件 (例如文件) 的情況下，請參閱第一欄的對應項目。 例如，當您在第二欄中讀到「檢視將命令轉送至其文件」時，請參閱第一欄的「文件」項目以進一步路由傳送。  
  
## <a name="see-also"></a>另請參閱  
 [架構如何呼叫處理常式](../mfc/how-the-framework-calls-a-handler.md)

