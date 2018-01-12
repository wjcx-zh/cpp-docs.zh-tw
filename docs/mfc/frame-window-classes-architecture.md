---
title: "框架視窗類別 （架構） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.frame
dev_langs: C++
helpviewer_keywords: frame window classes [MFC], document/view architecture
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f1caf8e4b93e18675b810ced962df6e8adcf521a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="frame-window-classes-architecture"></a>框架視窗類別 (架構)
在文件/檢視架構中，框架視窗會是包含 [檢視] 視窗的視窗。 它們也支援讓控制列附加至它們。  
  
 在多個文件介面 (MDI) 應用程式主視窗衍生自`CMDIFrameWnd`。 間接包含文件的框架，也就是`CMDIChildWnd`物件。 `CMDIChildWnd`物件，依序包含文件的檢視。  
  
 在單一文件介面 (SDI) 應用程式，主要視窗中，衍生自`CFrameWnd`，包含目前的文件的檢視。  
  
 [CFrameWnd](../mfc/reference/cframewnd-class.md)  
 SDI 應用程式的主框架視窗的基底類別。 也其他框架視窗類別的基底類別。  
  
 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)  
 MDI 應用程式的主框架視窗的基底類別。  
  
 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)  
 MDI 應用程式的文件框架視窗的基底類別。  
  
 [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)  
 當就地編輯伺服器文件時，則您可以提供檢視框架視窗。  
  
## <a name="see-also"></a>請參閱  
 [類別概觀](../mfc/class-library-overview.md)

