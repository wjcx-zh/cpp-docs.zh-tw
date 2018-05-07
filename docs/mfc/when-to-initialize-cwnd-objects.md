---
title: 初始化 CWnd 物件的時機 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- window objects [MFC], when to initialize CWnd
- initializing CWnd objects [MFC]
- initializing objects [MFC], CWnd
- CWnd objects [MFC], when HWND is attached
- HWND, when attached to CWnd object
- CWnd objects [MFC], when to initialize
ms.assetid: 4d31bcb1-73db-4f2f-b71c-89b087569a10
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ee10a4632809a224028bfa482f80ed9e8a9334a5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="when-to-initialize-cwnd-objects"></a>初始化 CWnd 物件的時機
您無法建立您自己的子視窗或任何 Windows API 函式呼叫的建構函式中`CWnd`-衍生物件。 這是因為`HWND`如`CWnd`物件尚未建立。 必須以進行最特定的 Windows 初始設定，例如新增子視窗[OnCreate](../mfc/reference/cwnd-class.md#oncreate)訊息處理常式。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [建立文件框架視窗](../mfc/creating-document-frame-windows.md)  
  
-   [文件/檢視建立](../mfc/document-view-creation.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用框架視窗](../mfc/using-frame-windows.md)

