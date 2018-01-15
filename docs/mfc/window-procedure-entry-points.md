---
title: "視窗程序進入點 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- state management, window procedures
- MFC, managing state data
- window procedure entry points
- entry points, window procedures
ms.assetid: a6b46a7f-6e42-45f2-9ae6-82e19fc57148
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5f4e99ce38bd5ae472d688dc779bdd4ccf9fd4c5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="window-procedure-entry-points"></a>視窗程序進入點
為了保護 MFC 視窗程序，模組會具有特殊視窗程序的實作進行靜態連結。 當模組與 MFC 連結 (Link) 時，就會自動進行連結 (Linkage)。 此視窗程序使用`AFX_MANAGE_STATE`巨集來適當地設定有效的模組狀態，然後呼叫**AfxWndProc**，而後者會委派至`WindowProc`成員函式的適當`CWnd`-衍生物件。  
  
## <a name="see-also"></a>請參閱  
 [管理 MFC 模組的狀態資料](../mfc/managing-the-state-data-of-mfc-modules.md)

