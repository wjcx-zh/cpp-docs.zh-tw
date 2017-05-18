---
title: "視窗樣式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- WS_MINIMIZEBOX
- WS_SIZEBOX
- WS_CLIPCHILDREN
- WS_TILED
- WS_GROUP
- WS_VSCROLL
- WS_CHILD
- WS_TABSTOP
- WS_HSCROLL
- WS_THICKFRAME
- WS_DISABLED
- WS_POPUP
- WS_ICONIC
- WS_MAXIMIZE
- WS_VISIBLE
- WS_POPUPWINDOW
- WS_TILEDWINDOW
- WS_DLGFRAME
- WS_MINIMIZE
- WS_CAPTION
- WS_OVERLAPPED
- WS_BORDER
- WS_MAXIMIZEBOX
- WS_OVERLAPPEDWINDOW
- WS_SYSMENU
- WS_CHILDWINDOW
- WS_CLIPSIBLINGS
dev_langs:
- C++
helpviewer_keywords:
- WS_THICKFRAME constant
- WS_TILEDWINDOW constant
- WS_MAXIMIZEBOX constant
- WS_DLGFRAME constant
- WS_CHILDWINDOW constant
- window styles, in MFC
- WS_CHILD constant
- WS_GROUP constant
- WS_MINIMIZE constant
- WS_CAPTION constant
- WS_MAXIMIZE constant
- WS_POPUP constant
- WS_SYSMENU constant
- WS_TILED constant
- window styles
- WS_POPUPWINDOW constant
- WS_CLIPSIBLINGS constant
- WS_BORDER constant
- WS_DISABLED constant
- WS_VSCROLL constant
- WS_OVERLAPPED constant
- WS_MINIMIZEBOX constant
- WS_VISIBLE constant
- WS_OVERLAPPEDWINDOW constant
- WS_TABSTOP constant
- WS_ICONIC constant
- WS_SIZEBOX constant
- WS_HSCROLL constant
- WS_CLIPCHILDREN constant
- styles, windows
ms.assetid: c85ffbe4-f4ff-4227-917a-48ec4a411842
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: d814e3a10132fb3fe88969ce434f8286b02afba5
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="window-styles"></a>視窗樣式
-   `WS_BORDER`建立有框線的視窗。  
  
-   **WS_CAPTION**建立一個視窗的標題列 (表示`WS_BORDER`樣式)。 不能與**WS_DLGFRAME**樣式。  
  
-   **WS_CHILD**建立子視窗。 不能與`WS_POPUP`樣式。  
  
-   **WS_CHILDWINDOW**相同**WS_CHILD**樣式。  
  
-   **WS_CLIPCHILDREN**排除父視窗內繪圖時，子視窗佔用的區域。 當您建立父視窗使用。  
  
-   **WS_CLIPSIBLINGS**剪輯相對於彼此的子視窗，也就是特定的子視窗當接收繪製訊息， **WS_CLIPSIBLINGS**樣式會裁剪範圍外的子視窗，來更新所有其他重疊的子視窗。 (如果**WS_CLIPSIBLINGS**未指定，而且子視窗有重疊，工作區的子視窗內繪圖時，可能要在其中繪製鄰近的子視窗的工作區。)搭配**WS_CHILD**只樣式。  
  
-   **WS_DISABLED**建立視窗一開始是停用。  
  
-   **WS_DLGFRAME**視窗建立具有雙框線，但沒有標題。  
  
-   **WS_GROUP**指定一組控制項中的使用者可以移動控制項至下一個使用方向鍵的第一個控制項。 所有控制項，以定義**WS_GROUP**樣式**FALSE**之後的第一個控制項屬於相同的群組。 下一個控制項與**WS_GROUP**樣式啟動下一個群組 （也就是一個群組結尾開始下）。  
  
-   **WS_HSCROLL**建立一個具有水平捲軸的視窗。  
  
-   **WS_ICONIC**建立一個一開始最小化的視窗。 相同**WS_MINIMIZE**樣式。  
  
-   **WS_MAXIMIZE**建立視窗的大小上限。  
  
-   **WS_MAXIMIZEBOX**建立的視窗已經最大化 按鈕。  
  
-   **WS_MINIMIZE**建立一個一開始最小化的視窗。 搭配**WS_OVERLAPPED**只樣式。  
  
-   **WS_MINIMIZEBOX**會建立具有最小化按鈕的視窗。  
  
-   **WS_OVERLAPPED**建立重疊的視窗。 重疊的視窗通常會具有標題和框線。  
  
-   **WS_OVERLAPPEDWINDOW**建立的重疊的視窗與**WS_OVERLAPPED**， **WS_CAPTION**， **WS_SYSMENU**， **WS_THICKFRAME**， **WS_MINIMIZEBOX**，和**WS_MAXIMIZEBOX**樣式。  
  
-   `WS_POPUP`建立快顯視窗。 不能與**WS_CHILD**樣式。  
  
-   **WS_POPUPWINDOW**建立的快顯視窗`WS_BORDER`， `WS_POPUP`，和**WS_SYSMENU**樣式。 **WS_CAPTION**樣式必須結合**WS_POPUPWINDOW**樣式來顯示 [控制] 功能表。  
  
-   **WS_SIZEBOX**建立有調整大小框線的視窗。 相同**WS_THICKFRAME**樣式。  
  
-   **WS_SYSMENU**建立有控制功能表方塊標題列中的視窗。 僅用於視窗具有標題列。  
  
-   **WS_TABSTOP**的控制項，讓使用者可以使用 TAB 鍵移動指定任意數目。 TAB 鍵移至所指定的下一個控制項的使用者**WS_TABSTOP**樣式。  
  
-   **WS_THICKFRAME**建立可用來調整視窗大小粗框架的視窗。  
  
-   **WS_TILED**建立重疊的視窗。 重疊的視窗具有標題列，並加上框線。 相同**WS_OVERLAPPED**樣式。  
  
-   **WS_TILEDWINDOW**建立的重疊的視窗與**WS_OVERLAPPED**， **WS_CAPTION**， **WS_SYSMENU**， **WS_THICKFRAME**， **WS_MINIMIZEBOX**，和**WS_MAXIMIZEBOX**樣式。 相同**WS_OVERLAPPEDWINDOW**樣式。  
  
-   **WS_VISIBLE**建立一個一開始即可見的視窗。  
  
-   **WS_VSCROLL**建立一個具有垂直捲軸的視窗。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 使用的樣式](../../mfc/reference/styles-used-by-mfc.md)   
 [Cwnd:: Create](../../mfc/reference/cwnd-class.md#create)   
 [CWnd::CreateEx](../../mfc/reference/cwnd-class.md#createex)   
 [功能是](http://msdn.microsoft.com/library/windows/desktop/ms632679)


