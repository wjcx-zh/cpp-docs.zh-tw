---
title: "一般視窗建立順序 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- sequence [MFC], window creation
- frame windows [MFC], creating
- windows [MFC], creating
- sequence [MFC]
ms.assetid: 9cd8c7ea-5e24-429e-b6d9-d7b6041d8ba6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 59bed4387a6b8e6edeb504e29d221e76a0b39d18
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="general-window-creation-sequence"></a>一般視窗建立順序
當您建立您自己的資源，例如子視窗的視窗時，架構會使用許多相同的程序中所述[文件/檢視建立](../mfc/document-view-creation.md)。  
  
 MFC 採用所提供的所有視窗類別[兩階段建構](../mfc/one-stage-and-two-stage-construction-of-objects.md)。 也就是說，在 c + + 的引動過程期間**新**運算子，建構函式會配置及初始化 c + + 物件，但不會建立對應的 Windows 視窗。 藉由呼叫之後完成[建立](../mfc/reference/cwnd-class.md#create)視窗物件的成員函式。  
  
 **建立**成員函式可讓 Windows 視窗，並將其`HWND`c + + 物件的公用資料成員中[m_hWnd](../mfc/reference/cwnd-class.md#m_hwnd)。 **建立**透過建立參數中提供完整的彈性。 然後再呼叫**建立**，您可能想要的視窗類別註冊全域函式[AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass)才能設定框架的圖示和類別樣式。  
  
 您可以使用框架視窗[LoadFrame](../mfc/reference/cframewnd-class.md#loadframe)成員函式，而不是**建立**。 `LoadFrame`可讓 Windows 視窗使用較少的參數。 它會從資源，包括畫面格的標題、 圖示、 快速鍵對應表，以及功能表取得許多預設值。  
  
> [!NOTE]
>  程式圖示、 快速鍵對應表和功能表資源必須通用的資源識別碼，例如**IDR_MAINFRAME**，讓他們做出 LoadFrame 載入。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [視窗物件](../mfc/window-objects.md)  
  
-   [註冊視窗 「 類別 」](../mfc/registering-window-classes.md)  
  
-   [終結視窗物件](../mfc/destroying-window-objects.md)  
  
-   [建立文件框架視窗](../mfc/creating-document-frame-windows.md)  
  
## <a name="see-also"></a>請參閱  
 [建立視窗](../mfc/creating-windows.md)

