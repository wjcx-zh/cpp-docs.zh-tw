---
title: 如何： 使用訊息對應交互參考 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.messages
dev_langs:
- C++
helpviewer_keywords:
- windows [MFC], message maps
ms.assetid: 2e863d23-9e58-45ba-b5e4-a8ceefccd0c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fccdf620cbdaeffc7fb201e014edc4c7c1dddc83
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434449"
---
# <a name="how-to-use-the-message-map-cross-reference"></a>如何：使用訊息對應交互參考

在標示的項目\<memberFxn >，撰寫您自己的成員函式，針對衍生[CWnd](../../mfc/reference/cwnd-class.md)類別。 您可以自行為函式命名。 其他函式如 `OnActivate`，是 `CWnd` 類別的成員函式。 如果呼叫這些函式，它們就會將訊息傳遞至 `DefWindowProc` Windows 函式。 若要處理 Windows 通知訊息，請覆寫衍生類別中對應的 `CWnd` 函式。 您的函式應該呼叫基底類別中被覆寫的函式，讓基底類別和 Windows 回應訊息。

在所有情況下，都將函式原型放在 `CWnd`衍生類別標頭，並且撰寫訊息對應項目，如下所示。

使用下列詞彙:

|詞彙|定義|
|----------|----------------|
|id|任何使用者定義的功能表項目 ID （WM_COMMAND 訊息） 或控制項 ID （子視窗通知訊息）。|
|「訊息」和「wNotifyCode」|在 WINDOWS.H 定義的 Windows 視窗訊息 ID。|
|nMessageVariable|包含傳回值的變數名稱`RegisterWindowMessage`Windows 函式。|

## <a name="see-also"></a>另請參閱

[訊息對應](../../mfc/reference/message-maps-mfc.md)

