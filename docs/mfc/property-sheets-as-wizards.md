---
title: "屬性工作表做為精靈 |Microsoft 文件"
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
- property sheets, as wizards
ms.assetid: 1ea66ecb-23b0-484a-838d-58671a2999b5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 65aedc5dbeb8a740d5713983f66eefe693864937
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="property-sheets-as-wizards"></a>屬性工作表做為精靈
精靈屬性工作表的主要特性是所提供的巡覽隨附 [下一步]、[完成]、[上一步] 和 [取消] 按鈕，而非索引標籤。 您需要呼叫[cpropertysheet:: Domodal](../mfc/reference/cpropertysheet-class.md#setwizardmode)之前先呼叫[cpropertysheet:: Setwizardmode](../mfc/reference/cpropertysheet-class.md#domodal)屬性工作表物件，利用這項功能。  
  
 使用者會收到相同[cpropertypage:: Onsetactive](../mfc/reference/cpropertypage-class.md#onsetactive)和[cpropertypage:: Onkillactive](../mfc/reference/cpropertypage-class.md#onkillactive)各個頁面間移動到另一個頁面時的通知。 [下一步] 和 [完成] 按鈕是互斥的控制項，也就是一次只會顯示其中一個。 在第一個頁面，[下一步] 按鈕應會啟用。 如果使用者是在最後一頁，則 [完成] 按鈕應會啟用。 這不是由架構自動完成的。 您必須呼叫[cpropertysheet:: Setwizardbutton](../mfc/reference/cpropertysheet-class.md#setwizardbuttons)為了達成此目的的最後一頁。  
  
 若要顯示所有預設按鈕，您必須顯示 [完成] 按鈕並移到 [下一步] 按鈕。 然後，移到 [上一步] 按鈕，如此才能保持其與 [下一步] 按鈕的相對位置。  
  
## <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#5](../mfc/codesnippet/cpp/property-sheets-as-wizards_1.cpp)]  
  
## <a name="see-also"></a>請參閱  
 [屬性工作表](../mfc/property-sheets-mfc.md)

