---
title: 變更清單控制項樣式 |Microsoft 文件
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
ms.openlocfilehash: 18d54d22106742cab8d1cdfe9c32adc0a98fb41b
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929539"
---
# <a name="changing-list-control-styles"></a>變更清單控制項樣式
您可以變更清單控制項的視窗樣式 ([CListCtrl](../mfc/reference/clistctrl-class.md)) 在任何時間之後建立它。 藉由變更視窗樣式，您可以變更的檢視控制項使用的類型。 比方說，若要模擬 [總管] 中，您可能會提供功能表項目或工具列按鈕控制項不同的檢視之間的切換： 圖示檢視、 清單檢視中，等等。  
  
 例如，當使用者選取您的功能表項目，您可以進行的呼叫[GetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633584) ，擷取目前控制項的樣式，然後再呼叫[SetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633591)重設樣式。 如需詳細資訊，請參閱[使用清單檢視控制項](http://msdn.microsoft.com/library/windows/desktop/bb774736)Windows SDK 中。  
  
 中所列的可用樣式[建立](../mfc/reference/clistctrl-class.md#create)。 樣式**LVS_ICON**， **LVS_SMALLICON**， **LVS_LIST**，和**LVS_REPORT**指定四個清單控制項檢視。  
  
## <a name="extended-styles"></a>延伸的樣式  
 除了清單控制項的標準的樣式，都有另一個集合，稱為 「 延伸樣式。 這些樣式，討論[擴充清單檢視樣式](http://msdn.microsoft.com/library/windows/desktop/bb774732)在 Windows SDK 中，提供各種不同的自訂清單控制項的行為的實用功能。 若要實作的特定樣式 （例如，動態顯示選取項目） 的行為，請呼叫[CListCtrl::SetExtendedStyle](../mfc/reference/clistctrl-class.md#setextendedstyle)，傳遞所需的樣式。 下列範例會示範函式呼叫：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#22](../mfc/codesnippet/cpp/changing-list-control-styles_1.cpp)]  
  
> [!NOTE]
>  工作的動態顯示選取項目，您必須擁有  **LVS_EX_ONECLICKACTIVATE**或**LVS_EX_TWOCLICKACTIVATE**開啟。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控制項](../mfc/controls-mfc.md)

