---
title: 樹狀目錄控制項的父和子項目
ms.date: 11/04/2016
helpviewer_keywords:
- parent items in CTreeCtrl [MFC]
- child items in tree control [MFC]
- CTreeCtrl class [MFC], parent and child items
- tree controls [MFC], parent and child items
ms.assetid: abcea1e4-fe9b-40d9-86dc-1db235f8f103
ms.openlocfilehash: 5a02194ccef8eca81971bb4e8ae24d859e578bcc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513966"
---
# <a name="tree-control-parent-and-child-items"></a>樹狀目錄控制項的父和子項目

樹狀目錄控制項 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 中的任何專案, 都可以有子專案的清單, 它們都與它相關聯。 有一個或多個子項目的項目稱為父項目。 子項目會在其父項目下方以縮排顯示，表示其附屬於父代。 沒有父代的項目會位於階層架構的頂端並稱為根項目。

在任何指定時間內，父項目的子項目清單狀態可以是展開或摺疊。 當其狀態為展開時，表示子項目會顯示在父項目下方。 當它摺疊時，則不會顯示子項目。 當使用者按兩下父專案, 或當使用者按一下與父專案相關聯的按鈕時, 如果父系具有**TVS_HASBUTTONS**樣式, 此清單就會在展開和折迭的狀態之間自動切換。 應用程式可以使用[expand](../mfc/reference/ctreectrl-class.md#expand)成員函式來展開或折迭子專案。

您可以藉由呼叫[InsertItem](../mfc/reference/ctreectrl-class.md#insertitem)成員函式, 將專案加入至樹狀目錄控制項。 此函式會傳回**HTREEITEM**類型的控制碼, 其可唯一識別專案。 在加入項目時，您必須指定新項目之父項目的控制代碼。 如果您在[TVINSERTSTRUCT](/windows/win32/api/commctrl/ns-commctrl-tvinsertstructw)結構或*hParent*參數中指定**Null**或**TVI_ROOT**值, 而不是父專案控制碼, 則會將專案加入為根項目。

當父專案的子專案清單即將展開或折迭時, 樹狀目錄控制項會傳送[TVN_ITEMEXPANDING](/windows/win32/Controls/tvn-itemexpanding)通知訊息。 通知為您提供一個機會，可防止變更或根據子項目清單狀態設定父項目的任何屬性。 變更清單的狀態之後, 樹狀目錄控制項會傳送[TVN_ITEMEXPANDED](/windows/win32/Controls/tvn-itemexpanded)通知訊息。

當子項目清單展開時，它會以相對於父項目的位置進行縮排。 您可以使用[SetIndent](../mfc/reference/ctreectrl-class.md#setindent)成員函式來設定縮排的數量, 或使用[setindent](../mfc/reference/ctreectrl-class.md#getindent)成員函式來抓取目前的數量。

## <a name="see-also"></a>另請參閱

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
