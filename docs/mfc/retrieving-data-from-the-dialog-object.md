---
title: 從對話方塊物件擷取資料 |Microsoft 文件
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
ms.openlocfilehash: 8b221bd97d9ee943e19b043bcc9be6aba0fa1672
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929591"
---
# <a name="retrieving-data-from-the-dialog-object"></a>從對話方塊物件擷取資料
架構提供簡單的方法初始化控制項在對話方塊中的值，以及從控制項擷取值。 更耗費人力手動方法會呼叫函式，例如`SetDlgItemText`和`GetDlgItemText`類別成員函式`CWnd`，套用至控制項視窗。 這些函式，存取每個控制項，分別可設定或取得它的值，呼叫函式，例如`SetWindowText`和`GetWindowText`。 架構的方法會自動初始化和擷取。  
  
 對話方塊資料交換 (DDX) 可讓您更輕鬆地交換對話方塊物件中的對話方塊方塊中，成員變數中的控制項之間的資料。 此交換適用於這兩種方式。 若要初始化的控制項在對話方塊中，您可以在對話方塊物件中設定資料成員的值和架構會傳輸值控制項對話方塊顯示之前。 然後您可以隨時更新對話方塊資料成員的使用者所輸入的資料。 此時，您可以使用資料可藉由參考資料成員變數。  
  
 您也可以排列自動驗證對話方塊資料驗證 (DDV) 使用的對話方塊控制項的值。  
  
 DDX 和 DDV 會更詳細地說明[對話方塊資料交換和驗證](../mfc/dialog-data-exchange-and-validation.md)。  
  
 對於強制回應對話方塊，您可以擷取使用者輸入時任何資料`DoModal`傳回 IDOK 但對話方塊之前就會終結物件。 對於非強制回應對話方塊，您可以擷取資料從對話方塊物件隨時藉由呼叫`UpdateData`與引數**TRUE** ，然後存取對話方塊類別成員變數。 此主題會更詳細地討論[對話方塊資料交換和驗證](../mfc/dialog-data-exchange-and-validation.md)。  
  
## <a name="see-also"></a>另請參閱  
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)

