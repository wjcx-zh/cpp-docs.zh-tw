---
title: ON_UPDATE_COMMAND_UI 巨集 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- ON_UPDATE_COMMAND_UI
dev_langs:
- C++
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- update handlers [MFC]
- command-handler macros
- updating user-interface objects [MFC]
ms.assetid: 3e72b50f-4119-4c82-81cf-6e09b132de05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 43caffe53be180221b4145a03df7cfc41c31828e
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928634"
---
# <a name="onupdatecommandui-macro"></a>ON_UPDATE_COMMAND_UI 巨集
使用**屬性**視窗連接使用者介面物件的命令目標物件中的命令更新處理常式。 它會自動連接 ON_UPDATE_COMMAND_UI 巨集的使用者介面物件的識別碼，並將處理更新的物件中建立處理常式。 請參閱[訊息對應到函式](../mfc/reference/mapping-messages-to-functions.md)如需詳細資訊。  
  
 例如，若要更新程式的 [編輯] 功能表中 [全部清除] 命令，使用**屬性**視窗的訊息對應項目將在所選類別中，函式宣告命令更新處理常式呼叫`OnUpdateEditClearAll`類別中宣告，並且類別的實作檔中空白的函式樣板。 函式原型如下所示：  
  
 [!code-cpp[NVC_MFCDocView#2](../mfc/codesnippet/cpp/on-update-command-ui-macro_1.h)]  
  
 像所有處理常式函式會顯示**afx_msg**關鍵字。 就像所有更新處理常式，它會採用一個引數，即指向 `CCmdUI` 物件的指標。  
  
## <a name="see-also"></a>另請參閱  
 [如何：更新使用者介面物件](../mfc/how-to-update-user-interface-objects.md)

