---
title: 樹狀目錄控制項目標籤
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], item labels
- labels, CTreeCtrl items
- CTreeCtrl class [MFC], item labels
- item labels, tree controls
- item labels
ms.assetid: fe834107-1a25-4280-aced-774c11565805
ms.openlocfilehash: 16bb2bbe63eaf8ea4ce30040589d4a8a4cf4dfd3
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741468"
---
# <a name="tree-control-item-labels"></a>樹狀目錄控制項目標籤

您通常會在將專案加入至樹狀目錄控制項（[CTreeCtrl](../mfc/reference/ctreectrl-class.md)）時，指定專案標籤的文字。 成員函式可以傳遞定義專案屬性的 [TVITEM](/windows/win32/api/commctrl/ns-commctrl-tvitemw) 結構，包括包含標籤文字的字串。`InsertItem` `InsertItem`有數個多載，可以使用各種不同的參數組合來呼叫。

樹狀目錄控制項會配置記憶體來儲存每個專案;專案標籤的文字會佔用此記憶體的重要部分。 如果您的應用程式在樹狀目錄控制項中維護字串的複本，您`TV_ITEM`可以藉由在或*lpszItem*的*pszText*成員中指定**LPSTR_TEXTCALLBACK**值，來減少控制項的記憶體需求。參數，而不是將實際字串傳遞至樹狀目錄控制項。 使用**LPSTR_TEXTCALLBACK**會讓樹狀目錄控制項在每次需要重新繪製專案時，從應用程式抓取專案標籤的文字。 若要取出文字，樹狀目錄控制項會傳送[TVN_GETDISPINFO](/windows/win32/Controls/tvn-getdispinfo)通知訊息，其中包含[NMTVDISPINFO](/windows/win32/api/commctrl/ns-commctrl-nmtvdispinfow)結構的位址。 您必須藉由設定內含結構的適當成員來回應。

樹狀目錄控制項使用從建立樹狀目錄控制項的進程堆積所配置的記憶體。 樹狀目錄控制項中的專案數目上限是以堆積中可用的記憶體數量為基礎。 每個專案都會使用64個位元組。

## <a name="see-also"></a>另請參閱

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
