---
title: 處理標題控制項告知 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CHeaderCtrl class [MFC], processing notifications
- controls [MFC], header
- notifications [MFC], processing for CHeaderCtrl
- header controls [MFC], processing notifications
- header control notifications
ms.assetid: e6c6af7c-d458-4d33-85aa-48014ccde5f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fd7c6fa8a85aee06aca3b1bf804a06df428e82cb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387753"
---
# <a name="processing-header-control-notifications"></a>處理標題控制項告知

在檢視或對話方塊類別中，使用 [屬性] 視窗來建立[OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify) switch 陳述式的任何標頭控制項使用的處理常式函式 ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) 您想要的通知訊息處理 (請參閱[將訊息對應至函式](../mfc/reference/mapping-messages-to-functions.md))。 通知會傳送至父視窗中，當使用者按一下或按兩下標頭項目，拖曳分割線之間的項目，依此類推。

標頭控制項相關聯的通知訊息所述[標頭控制項參考](https://msdn.microsoft.com/library/windows/desktop/bb775239)Windows SDK 中。

## <a name="see-also"></a>另請參閱

[使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

