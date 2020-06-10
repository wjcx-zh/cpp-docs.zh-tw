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
ms.openlocfilehash: 43fb903fa169233ce532e41ecdf02c23ab6037c8
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621456"
---
# <a name="interpreting-user-input-through-a-view"></a>透過檢視解譯使用者輸入

View 的其他成員函式會處理並解讀所有使用者輸入。 您通常會在您的 view 類別中定義訊息處理常式成員函式以進行處理：

- 滑鼠和鍵盤動作所產生的 Windows[訊息](messages.md)。

- 來自功能表、工具列按鈕和快速鍵的[命令](user-interface-objects-and-command-ids.md)。

這些訊息處理常式成員函式會將下列動作解讀為資料輸入、選取或編輯，包括將資料移入和移出剪貼簿：

- 滑鼠移動和點擊、拖曳和按兩下

- 次數

- 功能表命令

您的視圖所處理的 Windows 訊息取決於您的應用程式需求。

[訊息處理和對應主題](message-handling-and-mapping.md)會說明如何將功能表項目和其他使用者介面物件指派給命令，以及如何將命令系結至處理常式函式。 [訊息處理和對應主題](message-handling-and-mapping.md)也會說明 MFC 如何路由命令，並將標準 Windows 訊息傳送至包含它們之處理常式的物件。

例如，您的應用程式可能需要在視圖中執行直接的滑鼠繪製。 「塗抹」範例會示範如何分別處理 WM_LBUTTONDOWN、WM_MOUSEMOVE 和 WM_LBUTTONUP 訊息，以開始、繼續和結束線段的繪製。 另一方面，您有時可能需要在您的觀點中，將滑鼠點擊當做選取專案來加以解讀。 您的視圖 `OnLButtonDown` 處理函式會判斷使用者是否已繪製或選取。 如果選取此選項，處理常式會判中斷點擊是否在視圖中某個物件的範圍內，如果是的話，則改變顯示，以顯示選取的物件。

您的視圖可能也會處理特定功能表命令，例如，從 [編輯] 功能表中，使用 [剪貼簿] 來剪下、複製、貼上或刪除選取的資料。 這類處理常式會呼叫類別的一些剪貼簿相關成員函式，以將 `CWnd` 選取的資料項目與剪貼簿傳輸。

## <a name="see-also"></a>另請參閱

[使用檢視](using-views.md)
