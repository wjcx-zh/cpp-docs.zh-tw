---
title: 終結框架視窗 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- PostNcDestroy
dev_langs:
- C++
helpviewer_keywords:
- Default method [MFC]
- DestroyWindow method [MFC]
- frame windows [MFC], destroying
- OnNcDestroy method, and frame windows
- document frame windows [MFC], destroying
- destroying frame windows
- MFC, frame windows
- windows [MFC], destroying
- OnClose method [MFC]
- PostNcDestroy method [MFC]
ms.assetid: 5affca77-1999-4507-a2b2-9aa226611b4b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 81182c0e5633e19126d3036b5793de7658ad3d2a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343472"
---
# <a name="destroying-frame-windows"></a>終結框架視窗
MFC 架構會管理視窗解構，以及建立這些 framework 文件和檢視相關聯的視窗。 如果您建立其他視窗，您必須負責終結它們。  
  
 在架構中，當使用者關閉框架視窗時，視窗的預設[OnClose](../mfc/reference/cwnd-class.md#onclose)處理常式呼叫[DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow)。 當 Windows 視窗終結時呼叫之最後一個成員函式[OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy)，其會進行一些清除，呼叫[預設](../mfc/reference/cwnd-class.md#default)成員函式以執行 Windows 清除，最後再呼叫虛擬成員函式[PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy)。 [CFrameWnd](../mfc/reference/cframewnd-class.md)實作`PostNcDestroy`刪除 c + + 視窗物件。 您絕對不應該使用 c + +**刪除**框架視窗上的運算子。 請改用 `DestroyWindow`。  
  
 當主視窗關閉時，會關閉應用程式。 如果那里修改未儲存的文件，架構會顯示訊息方塊詢問如果應該儲存文件，並可確保適當的文件會儲存必要。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [建立文件框架視窗](../mfc/creating-document-frame-windows.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用框架視窗](../mfc/using-frame-windows.md)

