---
title: 建立狀態列的方法 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CStatusBar class [MFC], vs. CStatusBarCtrl
- methods [MFC], creating status bars
- CStatusBarCtrl class [MFC], vs. CStatusBar
- CStatusBarCtrl class [MFC], creating
- methods [MFC]
- status bars [MFC], creating
ms.assetid: 9aeaf290-7099-4762-a5ba-9c26705333c9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b0428bfc906ba6e8a1ecc7bd7c198327e8c31505
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="methods-of-creating-a-status-bar"></a>建立狀態列的方法
MFC 提供兩個類別建立狀態列： [CStatusBar](../mfc/reference/cstatusbar-class.md)和[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) （包裝 Windows 通用控制項 API）。 `CStatusBar` 提供的所有功能的通用控制項狀態列，它會自動與互動功能表和工具列，以及處理許多必要的通用控制項設定和結構。不過，產生可執行檔通常會大於使用建立`CStatusBarCtrl`。  
  
 `CStatusBarCtrl` 通常較小的可執行檔，而且結果可能會想要使用`CStatusBarCtrl`如果您不想要整合到 MFC 架構的狀態列。 如果您打算使用`CStatusBarCtrl`並整合到 MFC 架構的 [狀態] 列，您必須另花心思通訊狀態列控制項至 MFC 的操作。 這種通訊並不困難。不過，它是額外的工作，當您使用時，就不需要`CStatusBar`。  
  
 Visual c + + 提供兩種方式可利用狀態列通用控制項。  
  
-   建立狀態列使用`CStatusBar`，然後呼叫[CStatusBar::GetStatusBarCtrl](../mfc/reference/cstatusbar-class.md#getstatusbarctrl)存取`CStatusBarCtrl`成員函式。  
  
-   建立狀態列使用[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)的建構函式。  
  
 這兩種方法可讓您存取狀態列控制項的成員函式。 當您呼叫 `CStatusBar::GetStatusBarCtrl`時，會傳回 `CStatusBarCtrl` 物件的參考，因此您可以使用任一組成員函式。 請參閱[CStatusBar](../mfc/reference/cstatusbar-class.md)建構和建立使用狀態列資訊`CStatusBar`。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [控制項](../mfc/controls-mfc.md)

