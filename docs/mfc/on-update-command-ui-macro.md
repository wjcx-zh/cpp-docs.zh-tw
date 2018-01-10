---
title: "ON_UPDATE_COMMAND_UI 巨集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ON_UPDATE_COMMAND_UI
dev_langs: C++
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- update handlers [MFC]
- command-handler macros
- updating user-interface objects [MFC]
ms.assetid: 3e72b50f-4119-4c82-81cf-6e09b132de05
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3de873cf70bafa77d7c8f4b05c70ce211b2c2258
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="onupdatecommandui-macro"></a>ON_UPDATE_COMMAND_UI 巨集
使用**屬性**視窗連接使用者介面物件的命令目標物件中的命令更新處理常式。 它會自動連接使用者介面物件的 ID 與 `ON_UPDATE_COMMAND_UI` 巨集，並在將處理更新的物件中建立處理常式。 請參閱[訊息對應到函式](../mfc/reference/mapping-messages-to-functions.md)如需詳細資訊。  
  
 例如，若要更新程式的 [編輯] 功能表中 [全部清除] 命令，使用**屬性**視窗的訊息對應項目將在所選類別中，函式宣告命令更新處理常式呼叫`OnUpdateEditClearAll`類別中宣告，並且類別的實作檔中空白的函式樣板。 函式原型如下所示：  
  
 [!code-cpp[NVC_MFCDocView#2](../mfc/codesnippet/cpp/on-update-command-ui-macro_1.h)]  
  
 像所有處理常式函式會顯示**afx_msg**關鍵字。 就像所有更新處理常式，它會採用一個引數，即指向 `CCmdUI` 物件的指標。  
  
## <a name="see-also"></a>請參閱  
 [如何：更新使用者介面物件](../mfc/how-to-update-user-interface-objects.md)

