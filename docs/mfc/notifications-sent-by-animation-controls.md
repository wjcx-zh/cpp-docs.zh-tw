---
title: "動畫控制項傳送的告知 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c57a33bf4b13397d4f296ef4e5aa8e137c2d3594
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="notifications-sent-by-animation-controls"></a>動畫控制項傳送的告知
動畫控制項 ([CAnimateCtrl](../mfc/reference/canimatectrl-class.md)) 會傳送通知訊息的兩個不同的類型。 傳送通知的形式[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)訊息。  
  
 [ACN_START](http://msdn.microsoft.com/library/windows/desktop/bb761891)當動畫控制項開始播放短片時，傳送訊息。 [ACN_STOP](http://msdn.microsoft.com/library/windows/desktop/bb761893)動畫控制項完成或停止播放短片時，會傳送訊息。  
  
## <a name="see-also"></a>請參閱  
 [使用 CAnimateCtrl](../mfc/using-canimatectrl.md)   
 [控制項](../mfc/controls-mfc.md)

