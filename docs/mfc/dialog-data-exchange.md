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
ms.openlocfilehash: c12953ab0b9922788747246a97115188b2f686ed
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616833"
---
# <a name="dialog-data-exchange"></a>對話方塊資料交換

如果您使用 DDX 機制，通常您會在 `OnInitDialog` 處理常式或對話方塊建構函式中，設定對話方塊物件成員變數的初始值設定。 在對話方塊顯示之前，架構的 DDX 機制會將成員變數的值傳送至對話方塊中的控制項，當對話方塊本身出現以回應或時，就會出現此方塊 `DoModal` `Create` 。 `OnInitDialog` 的 `CDialog` 預設實作會呼叫類別 `UpdateData` 的 `CWnd` 成員函式，以初始化對話方塊中的控制項。

當使用者按一下 [確定] 按鈕時（或者每當您 `UpdateData` 使用引數**TRUE**呼叫成員函式時），相同的機制就會將值從控制項傳送至成員變數。 對話方塊資料驗證機制會驗證您所指定驗證規則的所有資料項目。

下圖說明對話方塊的資料交換。

![對話方塊資料交換](../mfc/media/vc379d1.gif "對話方塊資料交換") <br/>
對話方塊資料交換

`UpdateData`雙向運作，如傳遞給它的**BOOL**參數所指定。 若要執行交換，`UpdateData` 會設定 `CDataExchange` 物件並呼叫您對話方塊類別中 `CDialog` 的 `DoDataExchange` 成員函式的覆寫。 `DoDataExchange` 會採用 `CDataExchange` 類型的引數。 傳遞至 `CDataExchange` 的 `UpdateData` 物件表示交換的內容，定義如交換方向等此類資訊。

當您 (或程式碼精靈) 覆寫 `DoDataExchange` 時，請指定每個資料成員 (控制項) 的 DDX 函式的呼叫。 每個 DDX 函式會根據 `CDataExchange` 傳遞給 `DoDataExchange` 的 `UpdateData` 引數所提供之內容，得知如何進行雙向的資料交換。

MFC 提供許多 DDX 函式，以進行不同種類的交換。 下列範例顯示呼叫兩個 DDX 函式和一個 DDV 函式的 `DoDataExchange` 覆寫：

[!code-cpp[NVC_MFCControlLadenDialog#49](codesnippet/cpp/dialog-data-exchange_1.cpp)]

`DDX_` 和 `DDV_` 程式碼行為資料對應。 所顯示的範例 DDX 和 DDV 函式分別屬於核取方塊控制項和編輯方塊控制項。

如果使用者取消強制回應對話方塊，成員函式會 `OnCancel` 終止對話方塊，並傳回 `DoModal` **IDCANCEL**值。 在這種情況下，對話方塊和對話方塊物件之間不會進行資料交換。

## <a name="see-also"></a>另請參閱

[對話方塊資料交換和驗證](dialog-data-exchange-and-validation.md)<br/>
[在 MFC 中使用對話方塊](life-cycle-of-a-dialog-box.md)<br/>
[對話方塊資料驗證](dialog-data-validation.md)
