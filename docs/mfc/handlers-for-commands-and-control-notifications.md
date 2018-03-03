---
title: "命令和控制項告知處理常式 |Microsoft 文件"
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
- commands [MFC], handlers for
- functions [MFC], handler
- handlers [MFC]
- controls [MFC], notifications
- handlers [MFC], control notification [MFC]
- notifications [MFC], handlers for control
- handlers [MFC], command
ms.assetid: 20f57f4a-f577-4c09-80a2-43faf32a1c2e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 748bdd1a2ce6b94a2c935df94de68767ee36875e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="handlers-for-commands-and-control-notifications"></a>命令和控制項告知的處理常式
沒有命令或控制項通知訊息的預設處理常式。 因此，您只能依照慣例為這些類別的訊息命名您的處理常式。 當您將命令或控制項通知對應到處理常式時，[屬性] 視窗會根據命令 ID 或控制通知碼建議一個名稱。 您可以接受建議的名稱、加以變更或予以取代。  
  
 慣例會建議您針對其所代表的使用者介面物件，為兩個類別中的處理常式命名。 結果，[編輯] 功能表上 [剪下] 命令的處理常式可能也會被命名  
  
 [!code-cpp[NVC_MFCMessageHandling#4](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_1.h)]  
  
 因為剪下 命令的實作在應用程式中，架構會預先定義為 剪下 命令的命令 ID **ID_EDIT_CUT**。 如需所有預先定義的命令 ID 的清單，請參閱檔案 AFXRES.H。 如需詳細資訊，請參閱[標準命令](../mfc/standard-commands.md)。  
  
 此外，慣例會建議的處理常式**BN_CLICKED**可能名為從標示為 「 My Button 」 按鈕的通知訊息  
  
 [!code-cpp[NVC_MFCMessageHandling#5](../mfc/codesnippet/cpp/handlers-for-commands-and-control-notifications_2.h)]  
  
 因為它相當於應用程式特定的使用者介面物件，所以您可以指派這個 `IDC_MY_BUTTON` 命令 ID。  
  
 兩種類別的訊息都不接受引數並且不會傳回值。  
  
## <a name="see-also"></a>請參閱  
 [宣告訊息處理函式](../mfc/declaring-message-handler-functions.md)
