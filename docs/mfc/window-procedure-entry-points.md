---
title: 視窗程序進入點 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- state management, window procedures
- MFC, managing state data
- window procedure entry points
- entry points, window procedures
ms.assetid: a6b46a7f-6e42-45f2-9ae6-82e19fc57148
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 315526a8f95a1d62ac89f3a76fab492c9b136715
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956378"
---
# <a name="window-procedure-entry-points"></a>視窗程序進入點
為了保護 MFC 視窗程序，模組會具有特殊視窗程序的實作進行靜態連結。 當模組與 MFC 連結 (Link) 時，就會自動進行連結 (Linkage)。 此視窗程序會使用 AFX_MANAGE_STATE 巨集來適當地設定有效的模組狀態，然後呼叫`AfxWndProc`，而後者會委派至`WindowProc`成員函式的適當`CWnd`-衍生物件。  
  
## <a name="see-also"></a>另請參閱  
 [管理 MFC 模組的狀態資料](../mfc/managing-the-state-data-of-mfc-modules.md)

