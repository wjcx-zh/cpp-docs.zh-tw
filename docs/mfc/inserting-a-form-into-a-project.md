---
title: "將表單插入專案 |Microsoft 文件"
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
- inserting forms [MFC]
- Insert New dialog box [MFC]
- forms, adding to projects
ms.assetid: f3bd2998-3ce2-496d-ac5c-57ca70eec7cb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 968c24a4f64b88be6de95f0f1dd98c09eb494a97
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="inserting-a-form-into-a-project"></a>將表單插入專案中
表單控制項提供方便的容器。 您可以輕鬆地插入 MFC 為基礎的形式您的應用程式，只要應用程式支援的 MFC 程式庫。  
  
### <a name="to-insert-a-form-into-your-project"></a>若要將表單插入專案  
  
1.  從類別檢視中，選取您要加入表單的專案，並按一下滑鼠右鍵。  
  
2.  從捷徑功能表，按一下 **新增**，然後按一下 **加入類別**。  
  
     如果**新表單**命令無法使用，可以根據您的專案上 Active Template Library (ATL)。 若要將表單加入 ATL 專案時，您必須[指定某些設定](../atl/reference/application-settings-atl-project-wizard.md)首次建立專案時。  
  
3.  從**MFC**資料夾中，按一下  **MFC 類別**。  
  
4.  使用 MFC 類別精靈，使新的類別衍生自[CFormView](../mfc/reference/cformview-class.md)。  
  
 Visual c + + 將表單加入您的應用程式中，開啟對話方塊編輯器內，讓您可以開始新增控制項和整體設計處理。  
  
 若要執行下列其他步驟 （不適用於對話方塊架構應用程式）：  
  
1.  覆寫`OnUpdate`成員函式。  
  
2.  實作的成員函式，將資料從您的檢視移至您的文件。  
  
3.  建立`OnPrint`成員函式。  
  
## <a name="see-also"></a>請參閱  
 [表單檢視](../mfc/form-views-mfc.md)

