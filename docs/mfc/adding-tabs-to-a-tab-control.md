---
title: 將索引標籤加入至索引標籤控制項 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tab controls [MFC], adding tabs
- putting tabs on CTabCtrls [MFC]
- CTabCtrl class [MFC], adding tabs
- tabs [MFC], adding to CTabCtrl class [MFC]
ms.assetid: 7f3d9340-e3c7-4c71-9912-be57534ecc78
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb8caad0b7d1f632a2d97e4ea6bda7c93a2b4d74
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43218293"
---
# <a name="adding-tabs-to-a-tab-control"></a>將索引標籤加入至索引標籤控制項
之後建立的索引標籤控制項 ([CTabCtrl](../mfc/reference/ctabctrl-class.md))，將多個索引標籤，視需要新增。  
  
### <a name="to-add-a-tab-item"></a>若要加入索引標籤項目  
  
1.  準備[TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema)結構。  
  
2.  呼叫[ctabctrl:: Insertitem](../mfc/reference/ctabctrl-class.md#insertitem)，傳遞結構。  
  
3.  對其他索引標籤項目重複步驟 1 和 2。  
  
 如需詳細資訊，請參閱 <<c0> [ 建立的索引標籤控制項](/windows/desktop/Controls/tab-controls)Windows SDK 中。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CTabCtrl](../mfc/using-ctabctrl.md)   
 [控制項](../mfc/controls-mfc.md)

