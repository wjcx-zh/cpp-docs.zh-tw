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
ms.openlocfilehash: d414c5f597628576916c5091fa63a4bf673c8c44
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394818"
---
# <a name="adding-columns-to-the-control-report-view"></a>將資料行加入至控制項 (報表檢視)

> [!NOTE]
>  下列程序適用於[CListView](../mfc/reference/clistview-class.md)或是[CListCtrl](../mfc/reference/clistctrl-class.md)物件。

當清單控制項在報表檢視中時，會顯示資料行，提供方法組織每個清單控制項項目的各種子項目。 這個組織方式是在清單控制項和清單控制項項目相關聯的子項目之間以一對一的對應來實作。 如需子項目的的詳細資訊，請參閱[將項目加入至控制項](../mfc/adding-items-to-the-control.md)。 報表檢視中的清單控制項範例是由 Windows 95 和 Windows 98 檔案總管的詳細資料檢視提供。 第一欄列出資料夾、檔案圖示和標籤。 其他欄則列出檔案大小、檔案類型、最後修改日期等等。

即使隨時可以將資料行加入到清單控制項中，資料行只有在控制項的 `LVS_REPORT` 樣式位元開啟時才會顯示。

每個資料行都有相關聯的標頭項目 (請參閱[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) 加上標籤的資料行，並讓使用者能夠調整資料行的物件。

如果您的清單控制項支援報表檢視，您必須在清單控制項項目中為每個可能的子項目加入資料行。 加入資料行，您可以透過準備[LV_COLUMN](/windows/desktop/api/commctrl/ns-commctrl-taglvcolumna)結構，然後呼叫[InsertColumn](../mfc/reference/clistctrl-class.md#insertcolumn)。 在加入必要的資料行之後 (有時稱為標頭項目)，您可以使用屬於內嵌標題控制項的成員函式和樣式重新排列它們。 如需詳細資訊，請參閱 <<c0> [ 排序標題控制項中的項目](../mfc/ordering-items-in-the-header-control.md)。

> [!NOTE]
>  如果清單控制項以建立**LVS_NOCOLUMNHEADER**樣式，插入資料行的任何嘗試會被忽略。

## <a name="see-also"></a>另請參閱

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
