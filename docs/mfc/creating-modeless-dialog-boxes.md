---
title: 建立非強制回應對話方塊
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
ms.assetid: 70d78c7f-3d40-477b-9f78-0f33c359f88b
ms.openlocfilehash: 7da6d82257d1407dfcf4d6d3c15cdadbb8c0fa30
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685659"
---
# <a name="creating-modeless-dialog-boxes"></a>建立非強制回應對話方塊

對於非強制回應對話方塊，您必須提供您自己在對話方塊類別中的公用建構函式。 若要建立非強制回應對話方塊，請呼叫您的公用函式，然後呼叫對話方塊物件的[create](../mfc/reference/cdialog-class.md#create)成員函式來載入對話方塊資源。 您可以在此函式呼叫期間或之後呼叫**Create** 。 如果對話資源具有屬性**WS_VISIBLE**，則會立即出現對話方塊。 如果不是，您必須呼叫其[ShowWindow](../mfc/reference/cwnd-class.md#showwindow)成員函式。

## <a name="see-also"></a>另請參閱

[在 MFC 中使用對話方塊](../mfc/life-cycle-of-a-dialog-box.md)
