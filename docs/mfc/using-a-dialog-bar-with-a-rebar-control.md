---
title: 使用對話方塊列與 Rebar 控制項 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- WM_EX_TRANSPARENT
dev_langs:
- C++
helpviewer_keywords:
- WS_EX_TRANSPARENT style
- rebar controls [MFC], dialog bars
- dialog bars [MFC], using with rebar bands
ms.assetid: e528cea0-6b81-4bdf-9643-7c03b6176590
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 47894c14e3b3d694847f94e7f981c9397383e598
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="using-a-dialog-bar-with-a-rebar-control"></a>搭配使用對話方塊列與 Rebar 控制項
中所述[Rebar 控制項和群組列](../mfc/rebar-controls-and-bands.md)，每個群組列可以包含只有一個子視窗 （或控制項）。 如果您想要有一個以上的子視窗，每個群組列，這可能是一項限制。 方便的因應措施是使用多個控制項建立對話方塊列資源，然後將 rebar 群組列 （包含對話方塊列） 新增至 rebar 控制項。  
  
 一般來說，如果您想要顯示透明對話方塊列頻外，您可以將**WS_EX_TRANSPARENT**延伸對話方塊列物件的樣式。 不過，因為**WS_EX_TRANSPARENT**具有正確繪製背景對話方塊列的一些問題，您必須執行一些額外的工作來達成所要的效果。  
  
 下列程序詳細資料以達到透明而不使用所需的步驟**WS_EX_TRANSPARENT**延伸樣式。  
  
### <a name="to-implement-a-transparent-dialog-bar-in-a-rebar-band"></a>若要實作 rebar 群組列中的透明對話方塊列  
  
1.  使用[加入類別對話方塊](../mfc/reference/adding-an-mfc-class.md)，加入新的類別 (例如， `CMyDlgBar`)，用來實作您的對話方塊列物件。  
  
2.  加入的處理常式`WM_ERASEBKGND`訊息。  
  
3.  在新的處理常式，修改現有的程式碼，以符合下列範例：  
  
     [!code-cpp[NVC_MFCControlLadenDialog#29](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_1.cpp)]  
  
4.  加入的處理常式`WM_MOVE`訊息。  
  
5.  在新的處理常式，修改現有的程式碼，以符合下列範例：  
  
     [!code-cpp[NVC_MFCControlLadenDialog#30](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_2.cpp)]  
  
 新的處理常式，以模擬對話方塊列的透明度的轉送`WM_ERASEBKGND`傳送訊息給父視窗，並強制重新繪製，每次移動對話方塊列物件。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CReBarCtrl](../mfc/using-crebarctrl.md)   
 [控制項](../mfc/controls-mfc.md)

