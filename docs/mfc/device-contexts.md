---
title: 裝置內容 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: efda2666a1d7cf47a485a9e1ceb53c09f4966989
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43203828"
---
# <a name="device-contexts"></a>裝置內容
裝置內容是包含相關資訊的繪製屬性的顯示器或印表機等裝置的 Windows 資料結構。 所有的繪製呼叫都會經過封裝 Windows Api，以繪製線條、 圖形和文字的裝置內容物件。 裝置內容允許在 Windows 中的裝置獨立繪圖。 裝置內容可用來繪製到螢幕、 印表機，或中繼檔。  
  
 [CPaintDC](../mfc/reference/cpaintdc-class.md)物件會封裝 Windows，呼叫常見慣用語`BeginPaint`函式，然後繪製在裝置內容中，然後呼叫`EndPaint`函式。 `CPaintDC`建構函式呼叫`BeginPaint`，和解構函式呼叫`EndPaint`。 簡化的程序是建立[CDC](../mfc/reference/cdc-class.md)物件，繪製，然後再終結`CDC`物件。 在架構中，即使此程序大多會自動化。 特別的是，您`OnDraw`函式傳遞`CPaintDC`已經備妥 (透過`OnPrepareDC`)，而只是繪製到其中。 終結由架構和基礎裝置內容就會發行 Windows 中，從呼叫傳回時您`OnDraw`函式。  
  
 [CClientDC](../mfc/reference/cclientdc-class.md)物件會封裝代表只在視窗工作區的裝置內容的使用。 `CClientDC`建構函式呼叫`GetDC`函式和解構函式呼叫`ReleaseDC`函式。 [CWindowDC](../mfc/reference/cwindowdc-class.md)物件會封裝代表整個視窗中，包括其框架的裝置內容。  
  
 [CMetaFileDC](../mfc/reference/cmetafiledc-class.md)物件會封裝為 Windows 中繼檔繪製。 相對於`CPaintDC`傳遞給`OnDraw`，您必須在此情況下呼叫[OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc)自己。  
  
## <a name="mouse-drawing"></a>滑鼠的繪圖  
 在架構程式中的大部分繪製 —，因此大部分的裝置內容工作 — 都在檢視表的`OnDraw`成員函式。 不過，您仍然可以用於其他用途使用的裝置內容物件。 比方說，若要提供在檢視中的滑鼠移動追蹤意見反應，您需要直接在檢視繪製，而不需等待`OnDraw`呼叫。  
  
 在此情況下，您可以使用[CClientDC](../mfc/reference/cclientdc-class.md)直接在檢視中繪製的裝置內容物件。  
  
### <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼  
  
-   [裝置內容 （定義）](https://msdn.microsoft.com/library/windows/desktop/dd183553)  
  
-   [在檢視中繪圖](../mfc/drawing-in-a-view.md)  
  
-   [透過檢視解譯使用者輸入](../mfc/interpreting-user-input-through-a-view.md)  
  
-   [線條和曲線](https://msdn.microsoft.com/library/windows/desktop/dd145028)  
  
-   [填滿的圖案](https://msdn.microsoft.com/library/windows/desktop/dd162714)  
  
-   [字型和文字](/windows/desktop/gdi/fonts-and-text)  
  
-   [色彩](https://msdn.microsoft.com/library/windows/desktop/dd183450)  
  
-   [座標空間和轉換](https://msdn.microsoft.com/library/windows/desktop/dd183475)  
  
## <a name="see-also"></a>另請參閱  
 [視窗物件](../mfc/window-objects.md)

