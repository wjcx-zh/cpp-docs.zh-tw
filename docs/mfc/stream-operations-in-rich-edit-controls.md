---
title: "資料流 Rich Edit 控制項中的作業 |Microsoft 文件"
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
- CRichEditCtrl class [MFC], stream operations
- CRichEditCtrl class [MFC], stream storage
- rich edit controls [MFC], stream operations
- storage, stream in CRichEditCtrl
- stream operations in CRichEditCtrl
- stream storage and CRichEditCtrl
ms.assetid: 110b4684-1e76-4ca6-9ef0-5bc8b2d93c78
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c1a73790124adbc1ff8a89290bf4e1d7a4fa6824
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="stream-operations-in-rich-edit-controls"></a>Rich Edit 控制項中的資料流作業
您可以使用資料流將資料傳入或傳出 rich edit 控制項傳送 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md))。 資料流由定義[EDITSTREAM](http://msdn.microsoft.com/library/windows/desktop/bb787891)結構，指定緩衝區和應用程式定義的回呼函式。  
  
 若要讀取資料讀入 rich edit 控制項 （也就是資料流中的資料），使用[StreamIn](../mfc/reference/cricheditctrl-class.md#streamin)成員函式。 控制項會重複呼叫應用程式定義的回呼函式，每一次呼叫都會將一部分的資料傳送至緩衝區。  
  
 若要儲存內容豐富的編輯控制項 （也就是資料流出資料），您可以使用[StreamOut](../mfc/reference/cricheditctrl-class.md#streamout)成員函式。 此控制項會將資料重複寫入緩衝區，然後再呼叫應用程式定義的回呼函式。 回呼函式會在每次呼叫時儲存緩衝區的內容。  
  
## <a name="see-also"></a>請參閱  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控制項](../mfc/controls-mfc.md)

