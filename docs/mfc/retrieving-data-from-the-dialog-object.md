---
title: 從對話方塊物件擷取資料 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3055468c04bba7c9cb999d0a642c0819524ff7e7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391406"
---
# <a name="retrieving-data-from-the-dialog-object"></a>從對話方塊物件擷取資料

架構提供一個簡單的方法初始化對話方塊中控制項的值，以及從控制項擷取值。 更費力手動的方式是呼叫函式，例如`SetDlgItemText`並`GetDlgItemText`類別成員函式`CWnd`，適用於控制 windows。 使用這些函式，存取每個控制項分別可設定或取得它的值，這類呼叫的函式`SetWindowText`和`GetWindowText`。 初始設定和擷取，則會自動化架構的方法。

對話方塊資料交換 (DDX) 可讓您更輕鬆地交換對話方塊物件中的對話方塊方塊中，成員變數中的控制項之間的資料。 此交換適用於這兩種方式。 若要初始化的控制項在對話方塊中，您可以設定資料成員的值在對話方塊物件，以及架構會將值傳送至控制項之前的對話方塊隨即出現。 然後您可以隨時更新對話方塊資料成員的使用者輸入的資料。 此時，您可以使用資料，藉由參考資料成員變數。

您也可以排列要使用對話方塊資料驗證 (DDV) 自動進行驗證的對話方塊控制項的值。

更詳細地說明 DDX 和 DDV [ 對話方塊資料交換和驗證](../mfc/dialog-data-exchange-and-validation.md)。

對於強制回應對話方塊方塊中，您可以擷取使用者時所輸入的任何資料`DoModal`傳回 IDOK 但對話方塊之前終結物件。 對於非強制回應對話方塊方塊中，您可以擷取資料從對話方塊物件隨時藉由呼叫`UpdateData`搭配引數 **，則為 TRUE**並接著存取對話方塊類別成員變數。 這個主題會更詳細地討論[ 對話方塊資料交換和驗證](../mfc/dialog-data-exchange-and-validation.md)。

## <a name="see-also"></a>另請參閱

[對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)

