---
title: "不使用程式碼精靈的控制項類型安全存取 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- dialog boxes [MFC], accessing controls
- dialog box controls [MFC], accessing
ms.assetid: 325b4927-d49b-42b4-8e0b-fc84f31fb059
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 50206ec8196247deb4a63f7ac2685eed47fab5bb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="type-safe-access-to-controls-without-code-wizards"></a>不使用程式碼精靈的控制項類型安全存取
要建立類型安全存取控制項的第一個方法就是使用內嵌成員函式，將類別 `CWnd` 的 `GetDlgItem` 成員函式的傳回類型轉換為適當的 C++ 控制項類型，如下列範例所示：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#50](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_1.cpp)]  
  
 接著您可以使用這個成員函式，透過與下列類似的程式碼，以類型安全的方式來存取控制項：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#51](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_2.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [在對話方塊中的控制項類型安全存取](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)   
 [使用程式碼精靈的控制項型別安全存取](../mfc/type-safe-access-to-controls-with-code-wizards.md)

