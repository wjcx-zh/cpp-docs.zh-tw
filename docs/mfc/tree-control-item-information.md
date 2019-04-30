---
title: 樹狀目錄控制項目資訊
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], item information
- CTreeCtrl class [MFC], item information
ms.assetid: 8dcab855-27de-49e9-95d8-f78ba963ea71
ms.openlocfilehash: e0eb8af4fbbb6f59c0dda75ec3705183ce916350
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407857"
---
# <a name="tree-control-item-information"></a>樹狀目錄控制項目資訊

樹狀目錄控制項 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 擷取控制項中項目的相關資訊的成員函式數目。 [GetItem](../mfc/reference/ctreectrl-class.md#getitem)成員函式會擷取部分或所有項目相關聯的資料。 這項資料可以包含項目的文字、狀態、影像、子項目計數和應用程式定義的 32 位元資料值。 另外還有[SetItem](../mfc/reference/ctreectrl-class.md#setitem)函式，可以設定某些或所有項目相關聯的資料。

[GetItemState](../mfc/reference/ctreectrl-class.md#getitemstate)， [GetItemText](../mfc/reference/ctreectrl-class.md#getitemtext)， [GetItemData](../mfc/reference/ctreectrl-class.md#getitemdata)，以及[GetItemImage](../mfc/reference/ctreectrl-class.md#getitemimage)成員函式會擷取個別的屬性項目。 這些函式都具有用於設定項目屬性的有對應 Set 函式。

[GetNextItem](../mfc/reference/ctreectrl-class.md#getnextitem)成員函式會擷取與目前的項目指定的關聯性樹狀目錄控制項目。 這個函式會擷取項目的父代、下一個或上一個可見項目、第一個子項目等等，依此類推。 也有周遊樹狀結構的成員函式：[GetRootItem](../mfc/reference/ctreectrl-class.md#getrootitem)， [GetFirstVisibleItem](../mfc/reference/ctreectrl-class.md#getfirstvisibleitem)， [GetNextVisibleItem](../mfc/reference/ctreectrl-class.md#getnextvisibleitem)， [GetPrevVisibleItem](../mfc/reference/ctreectrl-class.md#getprevvisibleitem)， [GetChildItem](../mfc/reference/ctreectrl-class.md#getchilditem)，[GetNextSiblingItem](../mfc/reference/ctreectrl-class.md#getnextsiblingitem)， [GetPrevSiblingItem](../mfc/reference/ctreectrl-class.md#getprevsiblingitem)， [GetParentItem](../mfc/reference/ctreectrl-class.md#getparentitem)， [GetSelectedItem](../mfc/reference/ctreectrl-class.md#getselecteditem)，和[GetDropHilightItem](../mfc/reference/ctreectrl-class.md#getdrophilightitem)。

[GetItemRect](../mfc/reference/ctreectrl-class.md#getitemrect)成員函式會擷取樹狀目錄控制項目的週框。 [GetCount](../mfc/reference/ctreectrl-class.md#getcount)並[GetVisibleCount](../mfc/reference/ctreectrl-class.md#getvisiblecount)成員函式擷取樹狀結構控制項中的項目計數和目前顯示在樹狀目錄控制項的視窗中，分別是項目計數。 您可以確保特定的項目為可見，藉由呼叫[EnsureVisible](../mfc/reference/ctreectrl-class.md#ensurevisible)成員函式。

## <a name="see-also"></a>另請參閱

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
