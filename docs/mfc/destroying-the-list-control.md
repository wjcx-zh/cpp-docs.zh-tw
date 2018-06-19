---
title: 終結清單控制項 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- list controls [MFC], destroying
- CListCtrl class [MFC], destroying controls
ms.assetid: 513ec820-3a02-49d2-b073-a6a7a3fc91b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: edb26671ba775cfa7daf98d39c7eccc9fd4111bd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343278"
---
# <a name="destroying-the-list-control"></a>終結清單控制項
如果您將內嵌程式[CListCtrl](../mfc/reference/clistctrl-class.md)物件的檢視或對話方塊類別資料成員當做其擁有者被終結時終結。 如果您使用[CListView](../mfc/reference/clistview-class.md)，架構會在終結檢視時終結控制項。  
  
 如果您對於要儲存在應用程式中的某些清單資料而非清單控制項進行配置，則必須為其解除配置進行安排。 如需詳細資訊，請參閱[回呼項目和回呼遮罩](http://msdn.microsoft.com/library/windows/desktop/bb774736)Windows SDK 中。  
  
 此外，您必須負責解除配置您所建立並與清單控制項關聯的所有影像清單。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控制項](../mfc/controls-mfc.md)

