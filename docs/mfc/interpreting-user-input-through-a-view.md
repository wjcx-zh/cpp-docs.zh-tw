---
title: "透過檢視解譯使用者輸入 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- interpreting user input through views [MFC]
- views [MFC], user interface and input
- input [MFC], view class [MFC]
- CView class [MFC], interpreting user input
- user input [MFC], interpreting through view class [MFC]
ms.assetid: f0302a70-661f-4781-8fe7-78f082bef2a5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 88308000e35853a2e2159fa33a0629a3def7a7a6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="interpreting-user-input-through-a-view"></a>透過檢視解譯使用者輸入
檢視的其他成員函式處理，並解譯所有使用者輸入。 您通常會在您要處理的檢視類別定義訊息處理常式成員函式：  
  
-   Windows[訊息](../mfc/messages.md)滑鼠和鍵盤動作所產生。  
  
-   [命令](../mfc/user-interface-objects-and-command-ids.md)從功能表、 工具列按鈕和快速鍵。  
  
 這些訊息處理常式成員函式解譯的下列動作做為資料輸入、 選取項目，或編輯，包括將資料移至，並從剪貼簿：  
  
-   滑鼠動作和點選、 拖曳和按兩下  
  
-   按鍵  
  
-   功能表命令  
  
 Windows 訊息檢視控制代碼取決於您的應用程式需求。  
  
 [訊息處理和對應的主題](../mfc/message-handling-and-mapping.md)說明如何將功能表項目與其他使用者介面物件指派給命令，以及如何將命令繫結至處理函式。 [訊息處理和對應的主題](../mfc/message-handling-and-mapping.md)也說明 MFC 將命令路由，並將標準 Windows 訊息傳送到包含處理常式的物件。  
  
 例如，您的應用程式可能需要實作直接繪製在檢視中的滑鼠。 Scribble 範例示範如何處理`WM_LBUTTONDOWN`， `WM_MOUSEMOVE`，和`WM_LBUTTONUP`訊息分別若要開始，繼續進行，且結尾繪製的直線線段。 相反地，您有時可能需要解譯成選取在檢視中的按一下滑鼠。 您的檢視`OnLButtonDown`處理常式函式會判斷使用者是否已繪製，或是選取。 如果選取，此處理常式會判斷是否在檢視中的某些物件的界限內按一下，而且如果是這樣，alter 顯示畫面來顯示為已選取的物件。  
  
 您的檢視可能也會處理某些功能表命令，例如剪下、 複製、 貼上，或刪除選取的資料使用剪貼簿的 [編輯] 功能表命令。 這類處理常式會呼叫某些剪貼簿 相關的成員函式類別的`CWnd`傳送選取的資料項目或從剪貼簿。  
  
## <a name="see-also"></a>另請參閱  
 [使用檢視](../mfc/using-views.md)

