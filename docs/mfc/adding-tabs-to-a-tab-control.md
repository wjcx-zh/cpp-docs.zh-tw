---
title: "將索引標籤加入索引標籤控制項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- tab controls [MFC], adding tabs
- putting tabs on CTabCtrls [MFC]
- CTabCtrl class [MFC], adding tabs
- tabs [MFC], adding to CTabCtrl class [MFC]
ms.assetid: 7f3d9340-e3c7-4c71-9912-be57534ecc78
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 46012a265c1ecefa7af63f829be22e6132e036cb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="adding-tabs-to-a-tab-control"></a>將索引標籤加入至索引標籤控制項
在建立索引標籤控制項後 ([CTabCtrl](../mfc/reference/ctabctrl-class.md))，新增您需要的索引。  
  
### <a name="to-add-a-tab-item"></a>若要加入索引標籤項目  
  
1.  準備[TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554)結構。  
  
2.  呼叫[ctabctrl:: Insertitem](../mfc/reference/ctabctrl-class.md#insertitem)，傳遞結構。  
  
3.  對其他索引標籤項目重複步驟 1 和 2。  
  
 如需詳細資訊，請參閱[建立索引標籤控制項](http://msdn.microsoft.com/library/windows/desktop/bb760550)Windows SDK 中。  
  
## <a name="see-also"></a>請參閱  
 [使用 CTabCtrl](../mfc/using-ctabctrl.md)   
 [控制項](../mfc/controls-mfc.md)

