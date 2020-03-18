---
title: CTreeCtrl 和 CTreeView 比較
ms.date: 11/04/2016
helpviewer_keywords:
- tree view controls
- CTreeCtrl class [MFC], vs. CTreeView class [MFC]
- CTreeView class [MFC], vs. CTreeCtrl class [MFC]
- tree controls [MFC], and tree view
ms.assetid: bba5af25-103f-4b53-84d3-071bc9bd6494
ms.openlocfilehash: 7c78dfa9920c913fdbedb009c5a6f275a3e3e273
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445225"
---
# <a name="ctreectrl-vs-ctreeview"></a>CTreeCtrl 和 CTreeView 比較

MFC 提供兩個封裝樹狀目錄控制項的類別： [CTreeCtrl](../mfc/reference/ctreectrl-class.md)和[CTreeView](../mfc/reference/ctreeview-class.md)。 在不同的情況下，每個類別都很有用。

當您需要一般的子視窗控制項時，請使用 `CTreeCtrl`。例如，在對話方塊中。 如果視窗中會有其他子控制項，則您特別想要使用 `CTreeCtrl`，如同在一般的對話方塊中。

當您想要讓樹狀目錄控制項在檔/視圖架構和樹狀目錄控制項中做為「視圖視窗」的作用時，請使用 `CTreeView`。 `CTreeView` 將會佔用框架視窗或分隔器視窗的整個工作區。 當調整其父視窗的大小時，它會自動調整大小，而且可以從功能表、快速鍵和工具列處理命令訊息。 由於樹狀目錄控制項包含顯示樹狀結構所需的資料，因此對應的檔物件不一定要複雜，因為您甚至可以使用[CDocument](../mfc/reference/cdocument-class.md)做為檔範本中的檔案類型。

## <a name="see-also"></a>另請參閱

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
