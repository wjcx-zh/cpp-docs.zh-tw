---
title: 動畫控制項傳送的告知 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- notifications [MFC], animation controls
- CAnimateCtrl class [MFC], notifications
- controls [MFC], animation
- animation controls [MFC], notifications
ms.assetid: 584f5824-446b-4a1a-85f7-ef61842c8186
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c1696389ce3dc40c5d02ec660ebaeb6bf3e6c3ec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33345236"
---
# <a name="notifications-sent-by-animation-controls"></a>動畫控制項傳送的告知
動畫控制項 ([CAnimateCtrl](../mfc/reference/canimatectrl-class.md)) 會傳送通知訊息的兩個不同的類型。 傳送通知的形式[WM_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591)訊息。  
  
 [ACN_START](http://msdn.microsoft.com/library/windows/desktop/bb761891)當動畫控制項開始播放短片時，傳送訊息。 [ACN_STOP](http://msdn.microsoft.com/library/windows/desktop/bb761893)動畫控制項完成或停止播放短片時，會傳送訊息。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CAnimateCtrl](../mfc/using-canimatectrl.md)   
 [控制項](../mfc/controls-mfc.md)

