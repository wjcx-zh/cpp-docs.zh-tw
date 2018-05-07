---
title: CCmdUI 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CCmdUI
dev_langs:
- C++
helpviewer_keywords:
- updating user interface objects [MFC]
- user interface objects [MFC], updating
- CCmdUI class [MFC], menu updating
- update handlers [MFC]
- toolbars [MFC], updating
ms.assetid: 2f2bae62-8c29-45a4-bbce-490eb01907d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dde8c31620f64e6201c59b7031c789caa16c4902
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="the-ccmdui-class"></a>CCmdUI 類別
當路由傳送更新命令至其處理常式時，此架構會傳遞 `CCmdUI` 物件指標 (或 `CCmdUI` 衍生類別的物件指標) 給處理常式。 這個物件代表產生命令之功能表項目或工具列按鈕或其他使用者介面物件。 更新處理常式會藉由指標呼叫 `CCmdUI` 結構的成員函式來更新使用者介面物件。 例如，這是 [全部清除] 功能表項目的更新處理常式：  
  
 [!code-cpp[NVC_MFCDocView#3](../mfc/codesnippet/cpp/the-ccmdui-class_1.cpp)]  
  
 此處理常式會呼叫**啟用**具有功能表項目的存取權的物件成員函式。 **啟用**將項目可供使用。  
  
## <a name="see-also"></a>另請參閱  
 [如何：更新使用者介面物件](../mfc/how-to-update-user-interface-objects.md)

