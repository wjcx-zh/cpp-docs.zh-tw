---
title: 視窗物件 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- objects [MFC], window
- Windows window [MFC]
- MFC, windows
- frame windows [MFC], C++ window objects
- window objects [MFC]
- windows [MFC], C++ window objects
- window messages [MFC]
- HWND
- messages [MFC], Windows
- Visual C++, window objects [MFC]
- HWND, window objects [MFC]
ms.assetid: 28b33ce2-af05-4617-9d03-1cb9a02be687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 63b8d8dbde679d030eddd77fae6ca1fab519fdac
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385267"
---
# <a name="window-objects"></a>視窗物件
MFC 提供類別[CWnd](../mfc/reference/cwnd-class.md)封裝`HWND`視窗的控制代碼。 `CWnd` 物件是 C++ 視窗物件，與表示 Windows 視窗但包含它的 `HWND` 有所區別。 使用 `CWnd` 衍生您自己的子視窗類別，或使用衍生自 `CWnd` 的其中一個 MFC 類別。 `CWnd` 類別是所有視窗的基底類別，包括框架視窗、對話方塊、子視窗、控制項及控制列，例如工具列。 了解[c + + 視窗物件和 HWND 之間的關聯性](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md)是使用 MFC 的有效程式設計非常重要。  
  
 MFC 提供了一些預設的視窗功能和管理，不過，您可以從 `CWnd` 衍生自己的類別，並且使用其成員函式自訂提供的功能。 您可以建立子視窗可以建構`CWnd`物件並呼叫其[建立](../mfc/reference/cwnd-class.md#create)成員函數，然後自訂子視窗使用`CWnd`成員函式。 您可以將內嵌衍生自物件[CView](../mfc/reference/cview-class.md)，例如表單檢視或樹狀檢視，框架視窗中的。 可以支援多個檢視透過分割窗格，類別所提供的文件和[CSplitterWnd](../mfc/reference/csplitterwnd-class.md)。  
  
 每個從 `CWnd` 類別衍生的物件都包含訊息對應，您可以透過訊息對應將 Windows 訊息或命令 ID 對應至自己的處理常式。  
  
 有關 Windows 的一般程式設計文獻提供了學習如何使用 `CWnd` 成員函式的良好資源，這類成員函式用於封裝 `HWND` API。  
  
## <a name="functions-for-operating-on-a-cwnd"></a>在 CWnd 上運作的函式  
 `CWnd` 和其[衍生的視窗類別](../mfc/derived-window-classes.md)提供建構函式、 解構函式和成員函式來初始化物件、 建立基礎 Windows 結構，以及存取封裝`HWND`。 `CWnd` 也提供封裝 Windows API 的成員函式，用於傳送訊息、存取視窗的狀態、轉換座標、更新、捲動、存取 [剪貼簿]，以及許多其他工作。 採用 `HWND` 引數的大部分 Windows 視窗管理 API 都會封裝為 `CWnd` 的成員函式。 函式及其參數的名稱會保存在 `CWnd` 成員函式中。 如需詳細資訊會由封裝 Windows Api `CWnd`，請參閱類別[CWnd](../mfc/reference/cwnd-class.md)。  
  
## <a name="cwnd-and-windows-messages"></a>CWnd 和 Windows 訊息  
 `CWnd` 的其中一個主要目的是提供處理 Windows 訊息的介面，例如 `WM_PAINT` 或 `WM_MOUSEMOVE`。 成員函式的許多`CWnd`是標準訊息的處理常式 — 那些開頭為識別項**afx_msg**和前置詞 「 開啟 」，例如`OnPaint`和**OnMouseMove**。 [訊息處理和對應](../mfc/message-handling-and-mapping.md)涵蓋了訊息和訊息處理的詳細資訊。 其中的資訊同樣適用於架構的視窗，以及您基於特殊目的自行建立的視窗。  
  
### <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [C + + 視窗物件和 HWND 之間的關聯性](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md)  
  
-   [衍生的視窗類別](../mfc/derived-window-classes.md)  
  
-   [建立視窗](../mfc/creating-windows.md)  
  
-   [終結視窗物件](../mfc/destroying-window-objects.md)  
  
-   [從 HWND 中斷連結 CWnd](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
-   [使用視窗物件](../mfc/working-with-window-objects.md)  
  
-   [裝置內容](../mfc/device-contexts.md)： 讓 Windows 繪製裝置獨立的物件  
  
-   [圖形物件](../mfc/graphic-objects.md)： 畫筆、 筆刷、 字型、 點陣圖、 調色盤、 區域  
  
## <a name="see-also"></a>另請參閱  
 [Windows](../mfc/windows.md)

