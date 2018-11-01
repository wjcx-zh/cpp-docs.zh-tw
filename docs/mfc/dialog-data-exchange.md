---
title: 對話方塊資料交換
ms.date: 11/04/2016
helpviewer_keywords:
- initializing dialog boxes
- canceling data exchange
- dialog box data, retrieving
- DDX (dialog data exchange), data exchange mechanism
- dialog boxes [MFC], initializing
- dialog boxes [MFC], retrieving user input using DDX
- dialog box data
- dialog boxes [MFC], data exchange
- CDataExchange class [MFC], using DDX
- DoDataExchange method [MFC]
- user input [MFC], retrieving from MFC dialog boxes
- capturing user input [MFC]
- transferring dialog box data
- DDX (dialog data exchange), canceling
- UpdateData method [MFC]
- retrieving dialog box data [MFC]
ms.assetid: 4675f63b-41d2-45ed-b6c3-235ad8ab924b
ms.openlocfilehash: a72be4daf6c10a7d16b8558bfdddb8337ff1b1be
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566279"
---
# <a name="dialog-data-exchange"></a>對話方塊資料交換

如果您使用 DDX 機制，通常您會在 `OnInitDialog` 處理常式或對話方塊建構函式中，設定對話方塊物件成員變數的初始值設定。 立即對話方塊顯示之前，框架的 DDX 機制會將成員變數的值傳送至的控制項在對話方塊中，出現的位置時對話方塊本身顯示以回應`DoModal`或`Create`。 `OnInitDialog` 的 `CDialog` 預設實作會呼叫類別 `UpdateData` 的 `CWnd` 成員函式，以初始化對話方塊中的控制項。

相同的機制傳送值從控制項至成員變數當使用者按一下 [確定] 按鈕 (或只要您呼叫`UpdateData`成員函式使用引數 **，則為 TRUE**)。 對話方塊資料驗證機制會驗證您所指定驗證規則的所有資料項目。

下圖說明對話方塊的資料交換。

![對話方塊資料交換](../mfc/media/vc379d1.gif "vc379d1")對話方塊資料交換

`UpdateData` 適用於所指定的兩個方向**BOOL**參數傳遞給它。 若要執行交換，`UpdateData` 會設定 `CDataExchange` 物件並呼叫您對話方塊類別中 `CDialog` 的 `DoDataExchange` 成員函式的覆寫。 `DoDataExchange` 會採用 `CDataExchange` 類型的引數。 傳遞至 `CDataExchange` 的 `UpdateData` 物件表示交換的內容，定義如交換方向等此類資訊。

當您 (或程式碼精靈) 覆寫 `DoDataExchange` 時，請指定每個資料成員 (控制項) 的 DDX 函式的呼叫。 每個 DDX 函式會根據 `CDataExchange` 傳遞給 `DoDataExchange` 的 `UpdateData` 引數所提供之內容，得知如何進行雙向的資料交換。

MFC 提供許多 DDX 函式，以進行不同種類的交換。 下列範例顯示呼叫兩個 DDX 函式和一個 DDV 函式的 `DoDataExchange` 覆寫：

[!code-cpp[NVC_MFCControlLadenDialog#49](../mfc/codesnippet/cpp/dialog-data-exchange_1.cpp)]

`DDX_` 和 `DDV_` 程式碼行為資料對應。 所顯示的範例 DDX 和 DDV 函式分別屬於核取方塊控制項和編輯方塊控制項。

如果使用者取消強制回應對話方塊的 `OnCancel`成員函式會結束此對話方塊和`DoModal`傳回的值**IDCANCEL**。 在這種情況下，對話方塊和對話方塊物件之間不會進行資料交換。

## <a name="see-also"></a>另請參閱

[對話方塊資料交換和驗證](../mfc/dialog-data-exchange-and-validation.md)<br/>
[對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[對話方塊資料驗證](../mfc/dialog-data-validation.md)

