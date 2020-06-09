---
title: 將資料行加入至控制項 (報表檢視)
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], adding columns
- report view in CListCtrl class [MFC]
- views [MFC], report
- columns [MFC], adding to CListCtrl
- CListCtrl class [MFC], report view
ms.assetid: 7392c0d7-f8a5-4e7b-9ae7-b53dc9dd80ae
ms.openlocfilehash: 119f0f9cb92d724058ce97fbf477143739ec111e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617316"
---
# <a name="adding-columns-to-the-control-report-view"></a>將資料行加入至控制項 (報表檢視)

> [!NOTE]
> 下列程式適用于[CListView](reference/clistview-class.md)或[CListCtrl](reference/clistctrl-class.md)物件。

當清單控制項在報表檢視中時，會顯示資料行，提供方法組織每個清單控制項項目的各種子項目。 這個組織方式是在清單控制項和清單控制項項目相關聯的子項目之間以一對一的對應來實作。 如需子專案的詳細資訊，請參閱[將專案加入控制項](adding-items-to-the-control.md)。 報表檢視中的清單控制項範例是由 Windows 95 和 Windows 98 檔案總管的詳細資料檢視提供。 第一欄列出資料夾、檔案圖示和標籤。 其他欄則列出檔案大小、檔案類型、最後修改日期等等。

即使隨時可以將資料行加入到清單控制項中，資料行只有在控制項的 `LVS_REPORT` 樣式位元開啟時才會顯示。

每個資料行都有一個相關聯的標頭專案（請參閱[CHeaderCtrl](reference/cheaderctrl-class.md)）物件，它會標記資料行，並允許使用者調整資料行的大小。

如果您的清單控制項支援報表檢視，您必須在清單控制項項目中為每個可能的子項目加入資料行。 藉由準備[LVCOLUMN](/windows/win32/api/commctrl/ns-commctrl-lvcolumnw)結構，然後對[InsertColumn](reference/clistctrl-class.md#insertcolumn)進行呼叫來新增資料行。 在加入必要的資料行之後 (有時稱為標頭項目)，您可以使用屬於內嵌標題控制項的成員函式和樣式重新排列它們。 如需詳細資訊，請參閱[排序標題控制項中的專案](ordering-items-in-the-header-control.md)。

> [!NOTE]
> 如果清單控制項是以**LVS_NOCOLUMNHEADER**樣式建立的，則任何插入資料行的嘗試都會被忽略。

## <a name="see-also"></a>另請參閱

[使用 CListCtrl](using-clistctrl.md)<br/>
[控制項](controls-mfc.md)
