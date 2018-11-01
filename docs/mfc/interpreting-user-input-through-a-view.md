---
title: 透過檢視解譯使用者輸入
ms.date: 11/04/2016
helpviewer_keywords:
- interpreting user input through views [MFC]
- views [MFC], user interface and input
- input [MFC], view class [MFC]
- CView class [MFC], interpreting user input
- user input [MFC], interpreting through view class [MFC]
ms.assetid: f0302a70-661f-4781-8fe7-78f082bef2a5
ms.openlocfilehash: fe64f7c499b4a7c93f628fa0dff0855c379cbd58
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552560"
---
# <a name="interpreting-user-input-through-a-view"></a>透過檢視解譯使用者輸入

檢視的其他成員函式處理，並解譯所有使用者輸入。 您通常會定義您要處理的檢視類別中的訊息處理常式成員函式：

- Windows[訊息](../mfc/messages.md)滑鼠和鍵盤動作所產生。

- [命令](../mfc/user-interface-objects-and-command-ids.md)從功能表、 工具列按鈕和快速鍵。

這些訊息處理常式成員函式解譯的下列動作做為資料輸入、 在選取的項目，或編輯，包括從剪貼簿來回移動資料：

- 移動滑鼠並按下滑鼠，拖曳和按兩下

- 按鍵動作

- 功能表命令

Windows 訊息，您的檢視會處理會取決於您的應用程式需求。

[訊息處理和對應的主題](../mfc/message-handling-and-mapping.md)說明如何將功能表項目與其他使用者介面物件指派給命令以及如何將命令繫結至處理常式函式。 [訊息處理和對應的主題](../mfc/message-handling-and-mapping.md)也說明 MFC 將命令路由，並將標準 Windows 訊息傳送至含有它們的處理常式的物件。

例如，您的應用程式可能需要實作直接繪製在檢視中的滑鼠。 Scribble 範例示範如何處理 WM_LBUTTONDOWN、 WM_MOUSEMOVE 和 WM_LBUTTONUP 訊息分別，若要開始，繼續執行，並結束繪製的直線線段。 相反地，您有時可能需要解譯為選取項目在檢視中的按一下滑鼠按鍵。 您的檢視`OnLButtonDown`處理常式函式會判斷使用者是否已繪製，或選取。 如果選取，處理常式會判斷是否在檢視中的某些物件的界限內按一下，然後如果是的話，alter 顯示畫面來顯示為已選取的物件。

您的檢視也可能會處理特定的功能表命令，例如來自剪下、 複製、 貼上，或刪除選取的資料，使用 [剪貼簿] 的 [編輯] 功能表。 這類處理常式會呼叫某些剪貼簿 相關的成員函式類別的`CWnd`傳送選取的資料項目或從剪貼簿。

## <a name="see-also"></a>另請參閱

[使用檢視](../mfc/using-views.md)

