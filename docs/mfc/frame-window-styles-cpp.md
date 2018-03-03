---
title: "框架視窗樣式 （c + +） |Microsoft 文件"
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
- window styles [MFC]
- PreCreateWindow method, setting window styles
- windows [MFC], MFC
- frame windows [MFC], styles
- MFC, frame windows
- styles [MFC], windows
ms.assetid: fc5058c1-eec8-48d8-9f76-3fc01cfa53f7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a5bdc0204c538f476c791657d8b29a28b7baedd4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="frame-window-styles-c"></a>框架視窗樣式 (C++)
就架構框架視窗也適用於大部分程式中，但您可以使用進階函式來取得額外的彈性[PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow)和 MFC 全域函式[AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass). `PreCreateWindow`是的成員函式`CWnd`。  
  
 如果您套用**WS_HSCROLL**和**WS_VSCROLL**主框架視窗的樣式，它們會改為套用至**MDICLIENT**視窗，以便使用者可以向上捲動**MDICLIENT**區域。  
  
 如果視窗的**FWS_ADDTOTITLE**樣式位元設定 （這是預設） 時，從檢視可以得知框架視窗標題為何，若要檢視的文件名稱為基礎的視窗的標題列中顯示。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [管理 MDI 子視窗 (MDICLIENT)](../mfc/managing-mdi-child-windows.md)，內包含的 MDI 子視窗的 MDI 框架視窗  
  
-   [變更 MFC 所建立之視窗的樣式](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)  
  
-   [視窗樣式](../mfc/reference/styles-used-by-mfc.md#window-styles)  
  
## <a name="see-also"></a>請參閱  
 [框架視窗](../mfc/frame-windows.md)

