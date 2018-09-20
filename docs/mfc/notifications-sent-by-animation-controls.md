---
title: 動畫控制項傳送的通知 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb83fe6195c01c1e9dbcc2c00e43738af9ebc8e2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386388"
---
# <a name="notifications-sent-by-animation-controls"></a>動畫控制項傳送的告知

動畫控制項 ([CAnimateCtrl](../mfc/reference/canimatectrl-class.md)) 會傳送兩種不同的通知訊息。 傳送通知的形式[WM_COMMAND](/windows/desktop/menurc/wm-command)訊息。

[ACN_START](/windows/desktop/Controls/acn-start)當動畫控制項開始播放短片時，傳送訊息。 [ACN_STOP](/windows/desktop/Controls/acn-stop)動畫控制項完成或停止播放短片時，會傳送訊息。

## <a name="see-also"></a>另請參閱

[使用 CAnimateCtrl](../mfc/using-canimatectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

