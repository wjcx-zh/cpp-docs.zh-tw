---
title: 變更清單控制項樣式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- styles [MFC], CListCtrl
- CListCtrl class [MFC], styles
- CListCtrl class [MFC], changing styles
ms.assetid: be74a005-0795-417c-9056-f6342aa74b26
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2fdb2bbb3681fab2bae42866df40d0ca363b7935
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676763"
---
# <a name="changing-list-control-styles"></a>變更清單控制項樣式
您可以變更清單控制項的視窗樣式 ([CListCtrl](../mfc/reference/clistctrl-class.md)) 在建立後的任何時間。 藉由變更視窗樣式，您可以變更控制項使用的檢視類型。 比方說，若要模擬 [總管] 中，您可能會提供功能表項目或工具列按鈕來切換不同檢視之間的控制項： 圖示檢視、 清單檢視中，等等。  
  
 例如，當使用者選取您的功能表項目，您可以進行呼叫[GetWindowLong](/windows/desktop/api/winuser/nf-winuser-getwindowlonga)來擷取目前控制項的樣式，然後呼叫[SetWindowLong](/windows/desktop/api/winuser/nf-winuser-setwindowlonga)重設的樣式。 如需詳細資訊，請參閱 <<c0> [ 使用清單檢視控制項](/windows/desktop/Controls/using-list-view-controls)Windows SDK 中。  
  
 列出可用的樣式[建立](../mfc/reference/clistctrl-class.md#create)。 樣式**LVS_ICON**， **LVS_SMALLICON**， **LVS_LIST**，以及**LVS_REPORT**指定四個清單控制項檢視。  
  
## <a name="extended-styles"></a>延伸的樣式  
 除了清單控制項的標準樣式，還有另一個集合，稱為 「 延伸樣式。 這些樣式，討論[擴充清單檢視樣式](/windows/desktop/Controls/extended-list-view-styles)在 Windows SDK 中，提供各種實用的功能，自訂您的清單控制項的行為。 若要實作特定樣式 （例如暫留時的選取範圍） 的行為，請呼叫[CListCtrl::SetExtendedStyle](../mfc/reference/clistctrl-class.md#setextendedstyle)，傳遞所需的樣式。 下列範例會示範函式呼叫：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#22](../mfc/codesnippet/cpp/changing-list-control-styles_1.cpp)]  
  
> [!NOTE]
>  暫留時選擇功能運作，您必須也已經**LVS_EX_ONECLICKACTIVATE**或是**LVS_EX_TWOCLICKACTIVATE**開啟。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控制項](../mfc/controls-mfc.md)

