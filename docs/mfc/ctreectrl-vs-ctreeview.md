---
title: "CTreeCtrl vs。CTreeView |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CTreeCtrl
- CTreeView
dev_langs: C++
helpviewer_keywords:
- tree view controls
- CTreeCtrl class [MFC], vs. CTreeView class [MFC]
- CTreeView class [MFC], vs. CTreeCtrl class [MFC]
- tree controls [MFC], and tree view
ms.assetid: bba5af25-103f-4b53-84d3-071bc9bd6494
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b5a0dfd4f7b658cc585972ace1335a80b9bbd93a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="ctreectrl-vs-ctreeview"></a>CTreeCtrl vs。CTreeView
MFC 提供封裝樹狀目錄控制項的兩個類別： [CTreeCtrl](../mfc/reference/ctreectrl-class.md)和[CTreeView](../mfc/reference/ctreeview-class.md)。 每個類別是在不同情況下很有用。  
  
 使用`CTreeCtrl`時需要純文字的子視窗控制項; 例如，在對話方塊中。 您特別想要使用`CTreeCtrl`如果在視窗中，如同一般的對話方塊會有其他子控制項。  
  
 使用`CTreeView`當您想要做為文件/檢視架構中的 [檢視] 視窗樹狀目錄控制項，以及樹狀目錄控制項。 A`CTreeView`會佔用整個工作區的框架視窗或分隔視窗。 它會自動調整大小調整其父視窗的大小，而且它可以處理命令訊息，從功能表中，對應鍵和工具列。 樹狀目錄控制項包含顯示樹狀結構所需的資料，對應的文件物件不會有太複雜，甚至可以使用[CDocument](../mfc/reference/cdocument-class.md)做為文件範本中的文件類型。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控制項](../mfc/controls-mfc.md)

