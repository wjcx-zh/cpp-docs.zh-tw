---
title: 建立和顯示對話方塊 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- opening dialog boxes
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], displaying
ms.assetid: 1c5219ee-8b46-44bc-9708-83705d4f248b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 437fb934e95ce527a77038d643e9cee86b6f1f2c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387740"
---
# <a name="creating-and-displaying-dialog-boxes"></a>建立和顯示對話方塊

建立對話方塊物件作業分成兩個階段。 首先，建構對話方塊物件，然後建立對話方塊視窗。 強制回應和非強制回應對話方塊各用於建立並顯示對話方塊視窗的處理序不盡相同。 下表列出強制回應和非強制回應對話方塊通常建構及顯示的方式。

### <a name="dialog-creation"></a>建立對話方塊

|對話方塊類型|建立方式|
|-----------------|----------------------|
|[非強制回應](../mfc/creating-modeless-dialog-boxes.md)|建構 `CDialog`，然後呼叫 `Create` 成員函式。|
|[強制回應](../mfc/creating-modal-dialog-boxes.md)|建構 `CDialog`，然後呼叫 `DoModal` 成員函式。|

您可以如果您想，建立您的對話方塊中，從[記憶體內部對話方塊範本](../mfc/using-a-dialog-template-in-memory.md)您所建構，而不是從對話方塊範本資源。 這是進階主題。

## <a name="see-also"></a>另請參閱

[對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)

