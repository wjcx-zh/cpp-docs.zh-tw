---
title: 視窗程序進入點
ms.date: 11/04/2016
helpviewer_keywords:
- state management, window procedures
- MFC, managing state data
- window procedure entry points
- entry points, window procedures
ms.assetid: a6b46a7f-6e42-45f2-9ae6-82e19fc57148
ms.openlocfilehash: 9e395ff96d27476bc2869e23139cb2d1233f02ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500915"
---
# <a name="window-procedure-entry-points"></a>視窗程序進入點

為了保護 MFC 視窗程序，模組會具有特殊視窗程序的實作進行靜態連結。 當模組與 MFC 連結 (Link) 時，就會自動進行連結 (Linkage)。 這個視窗程序會使用 AFX_MANAGE_STATE 巨集來適當地設定有效的模組狀態，然後它會呼叫`AfxWndProc`，而後者會委派至`WindowProc`成員函式的適當`CWnd`-衍生物件。

## <a name="see-also"></a>另請參閱

[管理 MFC 模組的狀態資料](../mfc/managing-the-state-data-of-mfc-modules.md)

