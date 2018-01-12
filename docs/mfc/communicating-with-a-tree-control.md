---
title: "與樹狀目錄控制項通訊 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2ef1188c9519e57c8132a2b20fc3b272d6c0ac51
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="communicating-with-a-tree-control"></a>與樹狀目錄控制項通訊
您可以使用不同方法呼叫成員函式[CTreeCtrl](../mfc/reference/ctreectrl-class.md)根據物件的建立方式的物件：  
  
-   如果樹狀目錄控制項位於對話方塊中，請使用您在對話方塊類別中建立之 `CTreeCtrl` 類型的成員變數。  
  
-   如果樹狀目錄控制項是一個子視窗，請使用您用來建構物件的 `CTreeCtrl` 物件 (或指標)。  
  
-   如果您使用`CTreeView`物件，請使用此函式[ctreeview::](../mfc/reference/ctreeview-class.md#gettreectrl)取得樹狀目錄控制項的參考。 您可以使用這個值初始化其他參考或指派參考的位址給 `CTreeCtrl` 指標。  
  
## <a name="see-also"></a>請參閱  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控制項](../mfc/controls-mfc.md)

