---
title: "加入控制項以手動方式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows common controls [MFC], adding
- dialog box controls [MFC], adding to dialog boxes
- controlling input focus
- input focus control
- focus, controlling input [MFC]
- controls [MFC], adding to dialog boxes
- common controls [MFC], adding
ms.assetid: bc843e59-0c51-4b5b-8bf2-343f716469d2
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b13f6fdfb3c11819eb8d8838e5617e7a349d1023
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="adding-controls-by-hand"></a>以手動方式加入控制項
您可以[將控制項加入對話方塊中，使用對話方塊編輯器](../mfc/using-the-dialog-editor-to-add-controls.md)或將它們加入您自己，以程式碼。  
  
 若要建立您自己的控制項物件，您通常會內嵌 c + + 在 c + + 對話方塊的控制項物件或框架視窗物件。 Framework 中其他許多物件，例如控制項需要兩階段建構。 您應該呼叫控制項的**建立**一部分建立父對話方塊或框架視窗的成員函式。 對話方塊中，通常這是[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)，和框架視窗中[OnCreate](../mfc/reference/cwnd-class.md#oncreate)。  
  
 下列範例示範您可以宣告`CEdit`物件衍生的對話方塊類別的類別宣告中，然後呼叫**建立**成員函式中的`OnInitDialog`。 因為`CEdit`物件宣告為內嵌物件，它會自動建構對話方塊物件的建構，但仍然必須初始化使用它自己時**建立**成員函式。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#1](../mfc/codesnippet/cpp/adding-controls-by-hand_1.h)]  
  
 下列`OnInitDialog`函式中設定一個矩形，然後呼叫**建立**建立 Windows 編輯控制項，並將它附加至未初始化`CEdit`物件。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#2](../mfc/codesnippet/cpp/adding-controls-by-hand_2.cpp)]  
  
 在建立之後編輯物件，您也可以設定輸入的焦點至控制項藉由呼叫`SetFocus`成員函式。 最後，您會傳回從 0`OnInitDialog`以顯示您將焦點設定。 如果您傳回非零值時，對話方塊管理員會將焦點設定到對話方塊項目清單中的第一個控制項項目。 在大部分情況下，您會想要將控制項加入至您的對話方塊中，使用對話方塊編輯器。  
  
## <a name="see-also"></a>請參閱  
 [建立及使用控制項](../mfc/making-and-using-controls.md)   
 [控制項](../mfc/controls-mfc.md)   
 [CDialog::OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)

