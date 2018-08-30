---
title: 將項目加入至標題控制項 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [MFC], header
- CHeaderCtrl class [MFC], adding items
- header controls [MFC], adding items to
ms.assetid: 2e9a28b1-7302-4a93-8037-c5a4183e589a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a6450d99b8df436c64337e52fc14244ecbb0edfc
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206143"
---
# <a name="adding-items-to-the-header-control"></a>將項目加入至標題控制項
建立標題控制項之後 ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) 在其父視窗中，新增多個 「 標頭項目 」，您需要： 通常是其中每個資料行。  
  
### <a name="to-add-a-header-item"></a>若要加入標題項目  
  
1.  準備[HD_ITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema)結構。  
  
2.  呼叫[cheaderctrl:: Insertitem](../mfc/reference/cheaderctrl-class.md#insertitem)，傳遞結構。  
  
3.  針對其他項目重複步驟 1 和 2。  
  
 如需詳細資訊，請參閱 <<c0> [ 新增至標題控制項的項目](/windows/desktop/Controls/header-controls)Windows SDK 中。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [控制項](../mfc/controls-mfc.md)

