---
title: 透過檢視解譯使用者輸入 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interpreting user input through views [MFC]
- views [MFC], user interface and input
- input [MFC], view class [MFC]
- CView class [MFC], interpreting user input
- user input [MFC], interpreting through view class [MFC]
ms.assetid: f0302a70-661f-4781-8fe7-78f082bef2a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f62d64ed9479f1d1003536f8c4944b53d04d696f
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931986"
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
  
 例如，您的應用程式可能需要實作直接繪製在檢視中的滑鼠。 Scribble 範例示範如何處理 WM_LBUTTONDOWN、 WM_MOUSEMOVE 及 WM_LBUTTONUP 訊息分別以開始、 繼續和結束繪製的直線線段。 相反地，您有時可能需要解譯成選取在檢視中的按一下滑鼠。 您的檢視`OnLButtonDown`處理常式函式會判斷使用者是否已繪製，或是選取。 如果選取，此處理常式會判斷是否在檢視中的某些物件的界限內按一下，而且如果是這樣，alter 顯示畫面來顯示為已選取的物件。  
  
 您的檢視可能也會處理某些功能表命令，例如剪下、 複製、 貼上，或刪除選取的資料使用剪貼簿的 [編輯] 功能表命令。 這類處理常式會呼叫某些剪貼簿 相關的成員函式類別的`CWnd`傳送選取的資料項目或從剪貼簿。  
  
## <a name="see-also"></a>另請參閱  
 [使用檢視](../mfc/using-views.md)

