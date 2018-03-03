---
title: "設定 CStatusBarCtrl 物件的模式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CStatusBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- simple mode and status bar controls
- IsSimple method, using
- SetSimple method [MFC]
- status bar controls [MFC], simple and nonsimple modes
- non-simple mode and status bar controls
- CStatusBarCtrl class [MFC], simple and nonsimple modes
ms.assetid: ca6076e5-1501-4e33-8d35-9308941e46c0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7c954354321d814952ec3ac5ea148cc9177cd0fe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>設定 CStatusBarCtrl 物件的模式
有兩種模式`CStatusBarCtrl`物件： 簡單和非簡單。 在大多數情況下，您狀態列控制項會有一或多個組件，以及文字和可能的圖示或圖示。 這稱為非簡單模式。 如需此模式的詳細資訊，請參閱[初始化 CStatusBarCtrl 物件的組件](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md)。  
  
 不過，有情況下，您只需要顯示單行文字。 在此情況下，簡單的模式是足以滿足您的需求。 若要變更的模式`CStatusBarCtrl`物件為 simple 時，呼叫以[SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple)成員函式。 狀態列控制項是在簡單模式下，一旦設定文字，藉由呼叫**SetText**成員函式，傳遞的值為 255 **nPane**參數。  
  
 您可以使用[IsSimple](../mfc/reference/cstatusbarctrl-class.md#issimple)函式來判斷何種模式下`CStatusBarCtrl`物件是處於。  
  
> [!NOTE]
>  如果狀態列物件正在從簡單變更為 simple 時，或反之亦然，視窗立即重繪和 （適用），就會自動還原任何已定義的組件。  
  
## <a name="see-also"></a>請參閱  
 [使用 CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [控制項](../mfc/controls-mfc.md)

