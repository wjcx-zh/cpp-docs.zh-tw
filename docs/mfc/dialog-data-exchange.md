---
title: 對話方塊資料交換
ms.date: 11/19/2018
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
ms.openlocfilehash: 9a0199577ea46520c2eadc308812de8a1ce4b514
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "71685802"
---
# <a name="dialog-data-exchange"></a>對話方塊資料交換

如果您使用 DDX 機制，通常您會在 `OnInitDialog` 處理常式或對話方塊建構函式中，設定對話方塊物件成員變數的初始值設定。 在對話方塊顯示之前，架構的 DDX 機制會將成員變數的值傳送至對話方塊中的控制項，當對話方塊本身出現以回應 `DoModal` 或 `Create` 時，就會出現這些變數。 `OnInitDialog` 的 `CDialog` 預設實作會呼叫類別 `UpdateData` 的 `CWnd` 成員函式，以初始化對話方塊中的控制項。

當使用者按一下 [確定] 按鈕時（或者每當您使用引數**TRUE**呼叫 `UpdateData` 成員函式）時，相同的機制就會將值從控制項傳送至成員變數。 對話方塊資料驗證機制會驗證您所指定驗證規則的所有資料項目。

下圖說明對話方塊的資料交換。

![對話方塊資料交換](../mfc/media/vc379d1.gif "對話方塊資料交換") <br/>
對話方塊資料交換

`UpdateData` 會雙向運作，如傳遞給它的**BOOL**參數所指定。 若要執行交換，`UpdateData` 會設定 `CDataExchange` 物件並呼叫您對話方塊類別中 `CDialog` 的 `DoDataExchange` 成員函式的覆寫。 `DoDataExchange` 會採用 `CDataExchange` 類型的引數。 傳遞至 `CDataExchange` 的 `UpdateData` 物件表示交換的內容，定義如交換方向等此類資訊。

當您 (或程式碼精靈) 覆寫 `DoDataExchange` 時，請指定每個資料成員 (控制項) 的 DDX 函式的呼叫。 每個 DDX 函式會根據 `CDataExchange` 傳遞給 `DoDataExchange` 的 `UpdateData` 引數所提供之內容，得知如何進行雙向的資料交換。

MFC 提供許多 DDX 函式，以進行不同種類的交換。 下列範例顯示呼叫兩個 DDX 函式和一個 DDV 函式的 `DoDataExchange` 覆寫：

[!code-cpp[NVC_MFCControlLadenDialog#49](../mfc/codesnippet/cpp/dialog-data-exchange_1.cpp)]

`DDX_` 和 `DDV_` 程式碼行為資料對應。 所顯示的範例 DDX 和 DDV 函式分別屬於核取方塊控制項和編輯方塊控制項。

如果使用者取消強制回應對話方塊，`OnCancel` 成員函式會終止對話方塊，而 `DoModal` 會傳回**IDCANCEL**值。 在這種情況下，對話方塊和對話方塊物件之間不會進行資料交換。

## <a name="see-also"></a>請參閱

[對話方塊資料交換和驗證](../mfc/dialog-data-exchange-and-validation.md)<br/>
[在 MFC 中使用對話方塊](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[對話方塊資料驗證](../mfc/dialog-data-validation.md)
