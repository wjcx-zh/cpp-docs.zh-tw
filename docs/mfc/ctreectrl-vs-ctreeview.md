---
title: CTreeCtrl 和CTreeView |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CTreeCtrl
- CTreeView
dev_langs:
- C++
helpviewer_keywords:
- tree view controls
- CTreeCtrl class [MFC], vs. CTreeView class [MFC]
- CTreeView class [MFC], vs. CTreeCtrl class [MFC]
- tree controls [MFC], and tree view
ms.assetid: bba5af25-103f-4b53-84d3-071bc9bd6494
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e8acaecbdfb99b8ae0b27023145a0ef6aee1f219
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399143"
---
# <a name="ctreectrl-vs-ctreeview"></a>CTreeCtrl 和CTreeView

MFC 提供封裝樹狀目錄控制項的兩個類別： [CTreeCtrl](../mfc/reference/ctreectrl-class.md)並[CTreeView](../mfc/reference/ctreeview-class.md)。 每個類別是在不同的情況下很有用。

使用`CTreeCtrl`時需要純文字的子視窗控制項; 比方說，在對話方塊中。 特別是要使用`CTreeCtrl`如果在視窗中，如同一般的對話方塊中會有其他子控制項。

使用`CTreeView`當您想要做為文件/檢視架構中的 [檢視] 視窗的樹狀目錄控制項，以及樹狀目錄控制項。 A`CTreeView`會佔用整個工作區的框架視窗或分隔器視窗。 它會自動調整大小時調整它的父視窗，而且它可以處理來自功能表、 快速鍵和工具列的命令訊息。 由於樹狀目錄控制項包含顯示樹狀結構所需的資料，對應的文件物件不必是複雜的作業，您甚至可以使用[CDocument](../mfc/reference/cdocument-class.md)做為文件範本中的文件類型。

## <a name="see-also"></a>另請參閱

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

