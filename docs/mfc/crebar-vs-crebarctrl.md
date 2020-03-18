---
title: CReBar 和 CReBarCtrl 比較
ms.date: 11/04/2016
helpviewer_keywords:
- CReBar class [MFC], vs. CReBarCtrl
- rebar controls [MFC], CReBarCtrl class [MFC]
- GetReBarCtrl class [MFC]
ms.assetid: 7f9c1d7e-5d5f-4956-843c-69ed3df688d0
ms.openlocfilehash: 94f889be453a17a55357a260bd2a0c07037f6ded
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445280"
---
# <a name="crebar-vs-crebarctrl"></a>CReBar 和 CReBarCtrl 比較

MFC 提供兩個類別來建立 Rebar： [CReBar](../mfc/reference/crebar-class.md)和[CReBarCtrl](../mfc/reference/crebarctrl-class.md) （包裝 Windows 通用控制項 API）。 `CReBar` 提供 Rebar 通用控制項的所有功能，而且它會為您處理許多必要的通用控制項設定和結構。

如果您不想要整合 Rebar MFC 架構，`CReBarCtrl` 是 Win32 Rebar 控制項的包裝函式類別，因此可能會更容易實作。 如果您計劃使用 `CReBarCtrl` 並整合 Rebar 到 MFC 架構中，您必須另花心思將 Rebar 控制項操作傳達至 MFC。 這種通訊並不容易;不過，當您使用 `CReBar`時，這是不必要的額外工作。

Visual C++ 提供兩種利用 Rebar 通用控制項的方式。

- 使用 `CReBar`建立 Rebar，然後呼叫[CReBar：： GetReBarCtrl](../mfc/reference/crebar-class.md#getrebarctrl)以取得 `CReBarCtrl` 成員函式的存取權。

    > [!NOTE]
    >  `CReBar::GetReBarCtrl` 是可轉換 Rebar 物件之**this**指標的內嵌成員函式。 這表示在執行階段的函式呼叫沒有額外負荷。

- 使用[CReBarCtrl](../mfc/reference/crebarctrl-class.md)的函式建立 Rebar。

任何一個方法都可讓您存取 Rebar 控制項的成員函式。 當您呼叫 `CReBar::GetReBarCtrl`時，會傳回 `CReBarCtrl` 物件的參考，因此您可以使用任一組成員函式。 如需使用 `CReBar`來建立 Rebar 的詳細資訊，請參閱[CReBar](../mfc/reference/crebar-class.md) 。

## <a name="see-also"></a>另請參閱

[使用 CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
