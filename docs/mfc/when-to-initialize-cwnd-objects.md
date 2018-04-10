---
title: 初始化 CWnd 物件的時機 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3d1efceb4fa826d5cd2bf8dc900180eb36cea4de
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="when-to-initialize-cwnd-objects"></a>初始化 CWnd 物件的時機
您無法建立您自己的子視窗或任何 Windows API 函式呼叫的建構函式中`CWnd`-衍生物件。 這是因為`HWND`如`CWnd`物件尚未建立。 必須以進行最特定的 Windows 初始設定，例如新增子視窗[OnCreate](../mfc/reference/cwnd-class.md#oncreate)訊息處理常式。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [建立文件框架視窗](../mfc/creating-document-frame-windows.md)  
  
-   [文件/檢視建立](../mfc/document-view-creation.md)  
  
## <a name="see-also"></a>請參閱  
 [使用框架視窗](../mfc/using-frame-windows.md)

