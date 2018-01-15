---
title: "建立工具列的方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CToolBarCtrl class [MFC], and CToolBar class [MFC]
- CToolBar class [MFC], creating toolbars
- MFC toolbars
- toolbar controls [MFC]
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: f19d8d65-d49f-445c-abe8-d47d3e4101c8
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6d93f8e43c933e9c8054e798c11754cc48bf54a5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="methods-of-creating-a-toolbar"></a>建立工具列的方法
MFC 提供兩個類別來建立工具列： [CToolBar](../mfc/reference/ctoolbar-class.md)和[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) （包裝 Windows 通用控制項 API）。 `CToolBar`提供所有工具列通用控制項的功能，也可以處理許多必要的通用控制項設定和結構。不過，產生可執行檔通常會大於使用建立`CToolBarCtrl`。  
  
 `CToolBarCtrl`通常較小的可執行檔，而且結果可能會想要使用`CToolBarCtrl`如果您不想要整合到 MFC 架構的工具列。 如果您打算使用`CToolBarCtrl`並整合到 MFC 架構的工具列，您必須另花心思將傳達至 MFC 工具列控制項操作。 這種通訊並不困難。不過，它是額外的工作，當您使用時，就不需要`CToolBar`。  
  
 Visual c + + 提供兩種方式可利用工具列通用控制項。  
  
-   建立工具列使用`CToolBar`，然後呼叫[CToolBar::GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl)存取`CToolBarCtrl`成員函式。  
  
-   建立工具列使用[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)的建構函式。  
  
 這兩種方法可讓您存取工具列控制項的成員函式。 當您呼叫 `CToolBar::GetToolBarCtrl`時，會傳回 `CToolBarCtrl` 物件的參考，因此您可以使用任一組成員函式。 請參閱[CToolBar](../mfc/reference/ctoolbar-class.md)建構和建立工具列，使用如`CToolBar`。  
  
## <a name="see-also"></a>請參閱  
 [使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [控制項](../mfc/controls-mfc.md)

