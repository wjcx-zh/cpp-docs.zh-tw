---
title: CTreeCtrl 和CTreeView
ms.date: 11/04/2016
f1_keywords:
- CTreeCtrl
- CTreeView
helpviewer_keywords:
- tree view controls
- CTreeCtrl class [MFC], vs. CTreeView class [MFC]
- CTreeView class [MFC], vs. CTreeCtrl class [MFC]
- tree controls [MFC], and tree view
ms.assetid: bba5af25-103f-4b53-84d3-071bc9bd6494
ms.openlocfilehash: 29349e169e5ad8475001235d9b355da52156d683
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62241929"
---
# <a name="ctreectrl-vs-ctreeview"></a>CTreeCtrl 和CTreeView

MFC 提供封裝樹狀目錄控制項的兩個類別：[CTreeCtrl](../mfc/reference/ctreectrl-class.md)並[CTreeView](../mfc/reference/ctreeview-class.md)。 每個類別是在不同的情況下很有用。

使用`CTreeCtrl`時需要純文字的子視窗控制項; 比方說，在對話方塊中。 特別是要使用`CTreeCtrl`如果在視窗中，如同一般的對話方塊中會有其他子控制項。

使用`CTreeView`當您想要做為文件/檢視架構中的 [檢視] 視窗的樹狀目錄控制項，以及樹狀目錄控制項。 A`CTreeView`會佔用整個工作區的框架視窗或分隔器視窗。 它會自動調整大小時調整它的父視窗，而且它可以處理來自功能表、 快速鍵和工具列的命令訊息。 由於樹狀目錄控制項包含顯示樹狀結構所需的資料，對應的文件物件不必是複雜的作業，您甚至可以使用[CDocument](../mfc/reference/cdocument-class.md)做為文件範本中的文件類型。

## <a name="see-also"></a>另請參閱

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
