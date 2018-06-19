---
title: 將控制項加入至屬性工作表 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [MFC], adding to property sheets
- property sheets, adding controls
ms.assetid: 24ad4c0b-c1db-4850-b9f0-34aae8d74571
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8437fcdaa04ce7dd2b0a214e4bd3a63ca421d014
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341087"
---
# <a name="adding-controls-to-a-property-sheet"></a>將控制項加入至屬性工作表
根據預設，屬性工作表會配置視窗區域給屬性頁、索引標籤索引和 [確定]、[取消] 和 [套用] 按鈕  (非強制回應的屬性工作表沒有 [確定]、[取消] 和 [套用] 按鈕)。您可以將其他控制項加入屬性工作表。 例如，如果套用至外部物件，您可以在屬性頁區域右邊加入預覽視窗，向使用者顯示目前設定的外觀。  
  
 您可以在 `OnCreate` 處理常式中將控制項加入屬性工作表對話方塊。 包容的其他控制項通常需要擴大屬性工作表對話方塊的大小。 在呼叫基底類別**cpropertysheet:: Oncreate**，呼叫[GetWindowRect](../mfc/reference/cwnd-class.md#getwindowrect)若要取得目前所配置的屬性工作表視窗的高度與寬度，擴大矩形的尺寸，然後呼叫[MoveWindow](../mfc/reference/cwnd-class.md#movewindow)若要變更屬性工作表視窗的大小。  
  
## <a name="see-also"></a>另請參閱  
 [屬性工作表](../mfc/property-sheets-mfc.md)   
 [CPropertyPage 類別](../mfc/reference/cpropertypage-class.md)   
 [CPropertySheet 類別](../mfc/reference/cpropertysheet-class.md)
