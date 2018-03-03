---
title: "建立對話方塊類別 |Microsoft 文件"
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
- dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- files [MFC], creating
- dialog classes [MFC], Add Class Wizard
- dialog classes [MFC], creating
ms.assetid: d5321741-da41-47a8-bb1c-6a0e8b28c4c1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f2d8d62dc21aacb29f1133596c7f04251e88f1b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="creating-your-dialog-class"></a>建立您的對話方塊類別
在程式中每個對話方塊，建立新的對話方塊類別，才能使用對話方塊資源。  
  
 [將類別加入](../ide/adding-a-class-visual-cpp.md)說明如何建立新的對話方塊類別。 當您使用 加入類別精靈建立對話方塊類別時，它會寫入下列項目。H 和。您指定的 CPP 檔案：  
  
 在中。H 檔案：  
  
-   對話方塊類別的類別宣告。 類別衍生自[CDialog](../mfc/reference/cdialog-class.md)。  
  
 在中。CPP 檔案：  
  
-   此類別的訊息對應。  
  
-   對話方塊中標準建構函式。  
  
-   覆寫[DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)成員函式。 編輯這個函式。 它用於對話方塊資料交換和驗證功能中稍後所述[對話方塊資料交換和驗證](../mfc/dialog-data-exchange-and-validation.md)。  
  
## <a name="see-also"></a>請參閱  
 [使用程式碼精靈建立對話方塊類別](../mfc/creating-a-dialog-class-with-code-wizards.md)   
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)

