---
title: 如何完成預設列印
ms.date: 11/04/2016
helpviewer_keywords:
- default printing
- printing [MFC], default
- defaults, printing
ms.assetid: 0f698459-0fc9-4d43-97da-29cf0f65daa2
ms.openlocfilehash: 9ca79ec69037b960e7c455f6ab8abd8833b9a8a0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618579"
---
# <a name="how-default-printing-is-done"></a>如何完成預設列印

本文說明 MFC 架構的 Windows 預設列印處理序。

在 MFC 應用程式中，檢視類別具有一個名為 `OnDraw` 的成員函式，其中包含所有繪圖程式碼。 `OnDraw`接受[CDC](reference/cdc-class.md)物件的指標做為參數。 `CDC` 物件表示用於接收由 `OnDraw` 所產生影像的裝置內容。 當顯示檔的視窗收到[WM_PAINT](/windows/win32/gdi/wm-paint)訊息時，架構會呼叫， `OnDraw` 並將畫面的裝置內容（ [CPaintDC](reference/cpaintdc-class.md)物件）傳遞給它。 因此，`OnDraw` 會輸出至螢幕。

在 Windows 程式設計中，將輸出傳送至印表機與將輸出傳送至螢幕非常類似。 這是因為 Windows 繪圖裝置介面 (Graphics Device，GDI) 不受到硬體影響。 您只需使用適當的裝置內容，即可使用相同的 GDI 函式在螢幕上顯示或進行列印。 如果 `CDC` 所接收的 `OnDraw` 物件表示印表機，`OnDraw` 便會輸出到印表機。

如此便可說明 MFC 應用程式是如何執行簡單的列印，而不需要您進行其他的動作。 此架構會顯示 [列印] 對話方塊並建立印表機的裝置內容。 當使用者從 [檔案] 功能表選取 [列印] 命令時，檢視會將這個裝置內容傳遞至 `OnDraw`，以便在印表機上繪製文件。

不過，列印和螢幕顯示之間存在著一些重大的差異。 當您在列印時，必須將文件分割成不同頁面，並且一次顯示一個頁面，而不是在視窗中顯示任何可見的部分。 因此，您必須知道紙張的大小 (不論是 Letter 大小、Legal 大小或信封大小)。 您可能需要以不同方向進行列印，例如橫向和縱向模式。 MFC 程式庫無法預測您的應用程式將會如何處理這些問題，因此，它提供了通訊協定以便讓您加入這些功能。

該通訊協定會在[多頁檔](multipage-documents.md)一文中說明。

## <a name="see-also"></a>另請參閱

[列印](printing.md)
