---
title: 從對話方塊物件擷取資料
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], retrieving user data
- dialog box data [MFC]
- data [MFC], retrieving
- GetDlgItemText method [MFC]
- SetDlgItemText method [MFC]
- SetWindowText method [MFC]
- dialog box data [MFC], retrieving
- retrieving data [MFC]
- user input [MFC], retrieving from MFC dialog boxes
- capturing user input [MFC]
- dialog box controls [MFC], initializing values
- DDX (dialog data exchange) [MFC]
- MFC dialog boxes [MFC], retrieving user input
- data retrieval [MFC], dialog boxes
- data [MFC], dialog boxes
- DDX (dialog data exchange) [MFC], about DDX
- DDX (dialog data exchange) [MFC], retrieving data from Dialog object
- GetWindowText method [MFC]
ms.assetid: bdca2b61-6b53-4c2e-b426-8712c7a38ec0
ms.openlocfilehash: 903d76a1e672d05a3c093e528f7153562df8e3e5
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685573"
---
# <a name="retrieving-data-from-the-dialog-object"></a>從對話方塊物件擷取資料

此架構可讓您輕鬆地初始化對話方塊中的控制項值，以及從控制項抓取值。 較繁瑣的手動方法是呼叫函式，例如適用于控制視窗的類別 `CWnd`的 `SetDlgItemText` 和 `GetDlgItemText` 成員函式。 使用這些函式，您可以個別存取每個控制項來設定或取得其值，並呼叫 `SetWindowText` 和 `GetWindowText`等函數。 架構的方法會自動化初始化和抓取。

對話方塊資料交換（DDX）可讓您更輕鬆地在對話方塊中的控制項和對話方塊物件中的成員變數之間交換資料。 這種交換的運作方式有兩種。 若要初始化對話方塊中的控制項，您可以在對話方塊物件中設定資料成員的值，架構會在顯示對話方塊之前，將值傳送至控制項。 然後，您隨時都可以使用使用者輸入的資料來更新對話方塊資料成員。 在該時間點，您可以藉由參考資料成員變數來使用資料。

您也可以使用對話方塊資料驗證（DDV）來安排要自動驗證的對話方塊控制項值。

[對話方塊資料交換和驗證](../mfc/dialog-data-exchange-and-validation.md)中會更詳細地說明 DDX 和 DDV。

對於強制回應對話方塊，您可以在 `DoModal` 傳回 IDOK，但在終結對話方塊物件之前，抓取使用者輸入的任何資料。 對於非強制回應對話方塊，您可以隨時使用引數**TRUE**呼叫 `UpdateData`，然後存取對話方塊類別成員變數，以從對話方塊物件中取出資料。 在[對話資料交換和驗證](../mfc/dialog-data-exchange-and-validation.md)中，將會更詳細地討論此主題。

## <a name="see-also"></a>另請參閱

[在 MFC 中使用對話方塊](../mfc/life-cycle-of-a-dialog-box.md)
