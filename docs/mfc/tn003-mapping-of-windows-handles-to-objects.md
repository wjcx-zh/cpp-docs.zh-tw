---
title: "TN003： 將 Windows 控制代碼到物件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mapping
dev_langs:
- C++
helpviewer_keywords:
- TN003
- handle maps
- Windows handles to objects [MFC]
- mappings [MFC], Windows handles to objects
ms.assetid: fbea9f38-992c-4091-8dbc-f29e288617d6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7e53b2569b0da6bfa63c94adb7bb163e5bcd6b7b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="tn003-mapping-of-windows-handles-to-objects"></a>TN003：將 Windows 控制代碼對應到物件
此提示描述 MFC 支援對應 Windows 的常式物件的 c + + 物件的控制代碼。  
  
## <a name="the-problem"></a>問題  
 Windows 物件通常會以各種[處理](http://msdn.microsoft.com/library/windows/desktop/aa383751)MFC 類別物件包裝 Windows 物件控制代碼與 c + + 物件。 控制代碼的包裝函式的 MFC 類別程式庫可讓您尋找具有特定的控制代碼的 Windows 物件包裝的 c + + 物件。 不過，有時候物件沒有 c + + 包裝函式物件，並在這些時間系統會建立暫存物件做為 c + + 包裝函式。  
  
 使用處理常式對應的 Windows 物件如下所示：  
  
-   HWND ([CWnd](../mfc/reference/cwnd-class.md)和`CWnd`-衍生的類別)  
  
-   HDC ([CDC](../mfc/reference/cdc-class.md)和`CDC`-衍生的類別)  
  
-   HMENU ([CMenu](../mfc/reference/cmenu-class.md))  
  
-   HPEN ([CGdiObject](../mfc/reference/cgdiobject-class.md))  
  
-   HBRUSH (`CGdiObject`)  
  
-   HFONT (`CGdiObject`)  
  
-   HBITMAP (`CGdiObject`)  
  
-   HPALETTE (`CGdiObject`)  
  
-   HRGN (`CGdiObject`)  
  
-   HIMAGELIST ([CImageList](../mfc/reference/cimagelist-class.md))  
  
-   通訊端 ([CSocket](../mfc/reference/csocket-class.md))  
  
 這些物件的任何一個提供的控制代碼，您可以找到 MFC 包裝之物件的控制代碼藉由呼叫靜態方法`FromHandle`。 例如，假設呼叫 HWND`hWnd`下, 面將傳回的指標`CWnd`包裝`hWnd`:  
  
```  
CWnd::FromHandle(hWnd)  
```  
  
 如果`hWnd`沒有特定的包裝函式物件，暫時`CWnd`是用來包裝`hWnd`。 這可讓您能夠從任何控制代碼取得有效的 c + + 物件。  
  
 包裝函式物件之後，您可以從包裝函式類別的公用成員變數來擷取其控制代碼。 如果是`CWnd`，`m_hWnd`包含該物件的 HWND。  
  
## <a name="attaching-handles-to-mfc-objects"></a>附加至 MFC 物件的控制代碼  
 提供 Windows 物件的新建立的控制代碼的包裝函式物件和控制代碼，您可以建立關聯的兩個藉由呼叫`Attach`函式，如此範例所示：  
  
```  
CWnd myWnd;  
myWnd.Attach(hWnd);
```  
  
 這會永久對應建立關聯的項目`myWnd`和`hWnd`。 呼叫`CWnd::FromHandle(hWnd)`現在會傳回指標`myWnd`。 當`myWnd`已刪除，解構函式會自動終結`hWnd`經由呼叫 Windows [DestroyWindow](http://msdn.microsoft.com/library/windows/desktop/ms632682)函式。 如果這不預期，`hWnd`必須中斷連線`myWnd`之前`myWnd`終結 (離開的範圍時，通常`myWnd`已定義)。 `Detach`方法的做法。  
  
```  
myWnd.Detach();
```  
  
## <a name="more-about-temporary-objects"></a>暫存物件有關的詳細資訊  
 建立暫存物件的每當`FromHandle`有還沒有包裝函式物件的控制代碼。 這些暫存物件會從其控制代碼中斷連結和刪除`DeleteTempMap`函式。 根據預設[CWinThread::OnIdle](../mfc/reference/cwinthread-class.md#onidle)自動呼叫`DeleteTempMap`支援暫存的控制代碼對應之每個類別。 這表示您不能假設暫存物件的指標才有效遠從函式的結束點已取得指標的位置。  
  
## <a name="wrapper-objects-and-multiple-threads"></a>包裝函式物件和多個執行緒  
 暫時性和永久性物件會維護每個執行緒為基礎。 也就是說，一個執行緒無法存取另一個執行緒的 c + + 包裝函式物件，無論它是暫時性或永久性。  
  
 若要將這些物件從一個執行緒，一律傳送它們做為其原生`HANDLE`型別。 從一個執行緒的 c + + 包裝函式物件傳遞至另一個通常會導致非預期的結果。  
  
## <a name="see-also"></a>請參閱  
 [依數字的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)

