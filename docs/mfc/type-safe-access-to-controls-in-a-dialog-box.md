---
title: 在對話方塊中的控制項類型安全存取 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- common controls [MFC], in dialog boxes
- Windows common controls [MFC], in dialog boxes
- safe access to dialog box controls
- dialog boxes [MFC], type-safe access to controls
- controls [MFC], accessing in dialog boxes
- type-safe access to dialog box controls
- MFC dialog boxes [MFC], type-safe access to controls
ms.assetid: 67021025-dd93-4d6a-8bed-a1348fe50685
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a876be701b680de0559f123aaaaa68d4c006e41a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="type-safe-access-to-controls-in-a-dialog-box"></a>對話方塊中之控制項的類型安全存取
對話方塊中的控制項可以使用 MFC 控制項類別的介面，例如 `CListBox` 和 `CEdit`。 您可以建立控制項物件，並將它附加至對話方塊控制項。 然後可以透過其類別介面來存取該控制項，呼叫成員函式以便在控制項上作業。 這裡所述的方法是專門設計來提供對控制項的型別安全存取。 這對於編輯方塊和清單方塊之類的控制項而言特別實用。  
  
 有兩個方法可以建立對話方塊中控制項和 `CDialog` 衍生類別中 C++ 控制項成員變數之間的連接：  
  
-   [不使用程式碼精靈](../mfc/type-safe-access-to-controls-without-code-wizards.md)  
  
-   [使用程式碼精靈](../mfc/type-safe-access-to-controls-with-code-wizards.md)  
  
## <a name="see-also"></a>另請參閱  
 [對話方塊](../mfc/dialog-boxes.md)

