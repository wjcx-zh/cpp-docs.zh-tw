---
title: 建立非強制回應對話方塊 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
ms.assetid: 70d78c7f-3d40-477b-9f78-0f33c359f88b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 77b80f66f2956e71b90e4d939a0fb74aef28edb1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407032"
---
# <a name="creating-modeless-dialog-boxes"></a>建立非強制回應對話方塊

對於非強制回應對話方塊，您必須提供您自己在對話方塊類別中的公用建構函式。 若要建立非強制回應對話方塊中，呼叫您的公用建構函式，並接著呼叫對話方塊物件的[建立](../mfc/reference/cdialog-class.md#create)成員函式，以載入對話方塊資源。 您可以呼叫**建立**期間或之後的建構函式呼叫。 如果對話方塊資源具有屬性**WS_VISIBLE**，對話方塊會立即顯示。 如果沒有，您必須呼叫其[ShowWindow](../mfc/reference/cwnd-class.md#showwindow)成員函式。

## <a name="see-also"></a>另請參閱

[對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)

