---
title: "裝置內容 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OnPrepareDC method [MFC]
- windows [MFC], and device context
- drawing [MFC], device context
- CClientDC class [MFC], and GetDC method [MFC]
- drawing [MFC], in mouse and device contexts
- CDC class [MFC], objects
- device contexts [MFC]
- client areas
- CMetaFileDC class [MFC], and OnPrepareDC method [MFC]
- GDI objects [MFC], device contexts
- graphic objects [MFC], device contexts
- frame windows [MFC], device contexts
- metafiles and device contexts
- EndPaint method [MFC]
- printers [MFC], device contexts
- mouse [MFC], drawing and device contexts
- BeginPaint method, CPaintDC
- CPaintDC class [MFC], device context for painting
- windows [MFC], drawing directly into
- client areas, and device context
- device contexts [MFC], CDC class [MFC]
- user interface [MFC], device contexts
- device-independent drawing
- GetDC method and CClientDC class [MFC]
- CClientDC class [MFC], and ReleaseDC method [MFC]
- ReleaseDC method [MFC]
- device contexts [MFC], about device contexts
- drawing [MFC], directly into windows
- painting and device context
ms.assetid: d0cd51f1-f778-4c7e-bf50-d738d10433c7
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 26d4a0e32a8b24a72447cf4227be128659316c0b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="device-contexts"></a>裝置內容
裝置內容會包含顯示或印表機等裝置的繪圖屬性相關資訊的 Windows 資料結構。 所有的繪製呼叫是透過裝置內容物件，此物件會封裝 Windows Api 來繪製線條、 圖形和文字。 裝置內容允許 Windows 中的裝置獨立繪圖。 裝置內容可以用來繪製到螢幕、 印表機或中繼檔。  
  
 [CPaintDC](../mfc/reference/cpaintdc-class.md)物件中封裝的 Windows 中，呼叫慣用語`BeginPaint`函式，然後繪製在裝置內容中，然後再呼叫`EndPaint`函式。 `CPaintDC`建構函式呼叫`BeginPaint`，和解構函式呼叫`EndPaint`。 簡化的程序是建立[CDC](../mfc/reference/cdc-class.md)物件、 繪製，然後摧毀`CDC`物件。 在架構中，即使此程序的許多會自動化。 特別是，您`OnDraw`函式傳遞`CPaintDC`已準備 (透過`OnPrepareDC`)，您只需繪製它。 由架構終結和基礎的裝置內容，會從呼叫傳回時發行到 Windows 您`OnDraw`函式。  
  
 [CClientDC](../mfc/reference/cclientdc-class.md)物件會封裝使用的裝置內容，表示只在視窗的用戶端區域。 `CClientDC`建構函式呼叫`GetDC`函式和解構函式呼叫`ReleaseDC`函式。 [CWindowDC](../mfc/reference/cwindowdc-class.md)物件會封裝代表整個視窗中，包括其框架的裝置內容。  
  
 [CMetaFileDC](../mfc/reference/cmetafiledc-class.md)物件會封裝為 Windows 中繼檔繪製。 相對於`CPaintDC`傳遞至`OnDraw`，您必須在此情況下呼叫[OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc)自己。  
  
## <a name="mouse-drawing"></a>滑鼠的繪圖  
 在架構程式中的大部分繪製 —，因此大部分的裝置內容工作 — 在檢視中進行`OnDraw`成員函式。 不過，您仍然可以用於其他用途使用裝置內容物件。 例如，若要在檢視中的滑鼠移動提供追蹤的意見反應，您需要繪製直接在檢視，而不需等待`OnDraw`呼叫。  
  
 在此情況下，您可以使用[CClientDC](../mfc/reference/cclientdc-class.md)直接在檢視中繪製的裝置內容物件。  
  
### <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [裝置內容 （定義）](http://msdn.microsoft.com/library/windows/desktop/dd183553)  
  
-   [在檢視中繪圖](../mfc/drawing-in-a-view.md)  
  
-   [透過檢視解譯使用者輸入](../mfc/interpreting-user-input-through-a-view.md)  
  
-   [線條和曲線](http://msdn.microsoft.com/library/windows/desktop/dd145028)  
  
-   [填滿的圖案](http://msdn.microsoft.com/library/windows/desktop/dd162714)  
  
-   [字型和文字](http://msdn.microsoft.com/library/windows/desktop/dd144819)  
  
-   [色彩](http://msdn.microsoft.com/library/windows/desktop/dd183450)  
  
-   [座標空間和轉換](http://msdn.microsoft.com/library/windows/desktop/dd183475)  
  
## <a name="see-also"></a>請參閱  
 [視窗物件](../mfc/window-objects.md)

