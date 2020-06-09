---
title: CTreeCtrl 和 CTreeView 比較
ms.date: 11/04/2016
helpviewer_keywords:
- tree view controls
- CTreeCtrl class [MFC], vs. CTreeView class [MFC]
- CTreeView class [MFC], vs. CTreeCtrl class [MFC]
- tree controls [MFC], and tree view
ms.assetid: bba5af25-103f-4b53-84d3-071bc9bd6494
ms.openlocfilehash: 83e07c75b9eab6df05dbcd0f52cfbe8b90e1d768
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620488"
---
# <a name="ctreectrl-vs-ctreeview"></a>CTreeCtrl 和 CTreeView 比較

MFC 提供兩個封裝樹狀目錄控制項的類別： [CTreeCtrl](reference/ctreectrl-class.md)和[CTreeView](reference/ctreeview-class.md)。 在不同的情況下，每個類別都很有用。

`CTreeCtrl`當您需要一般的子視窗控制項時（例如，在對話方塊中），請使用。 `CTreeCtrl`如果視窗中會有其他子控制項，則您特別想要使用，如一般對話方塊中所示。

`CTreeView`當您想要讓樹狀目錄控制項在檔/視圖架構和樹狀目錄控制項中做為視圖視窗的作用時，請使用。 `CTreeView`會佔用框架視窗或分隔器視窗的整個工作區。 當調整其父視窗的大小時，它會自動調整大小，而且可以從功能表、快速鍵和工具列處理命令訊息。 由於樹狀目錄控制項包含顯示樹狀結構所需的資料，因此對應的檔物件不一定要複雜，因為您甚至可以使用[CDocument](reference/cdocument-class.md)做為檔範本中的檔案類型。

## <a name="see-also"></a>另請參閱

[使用 CTreeCtrl](using-ctreectrl.md)<br/>
[控制項](controls-mfc.md)
