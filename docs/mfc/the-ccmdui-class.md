---
title: "CCmdUI 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CCmdUI
dev_langs: C++
helpviewer_keywords:
- updating user interface objects [MFC]
- user interface objects [MFC], updating
- CCmdUI class [MFC], menu updating
- update handlers [MFC]
- toolbars [MFC], updating
ms.assetid: 2f2bae62-8c29-45a4-bbce-490eb01907d5
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: efb87fc04ee9ee55806ec4fc1103ded42231b433
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="the-ccmdui-class"></a>CCmdUI 類別
當路由傳送更新命令至其處理常式時，此架構會傳遞 `CCmdUI` 物件指標 (或 `CCmdUI` 衍生類別的物件指標) 給處理常式。 這個物件代表產生命令之功能表項目或工具列按鈕或其他使用者介面物件。 更新處理常式會藉由指標呼叫 `CCmdUI` 結構的成員函式來更新使用者介面物件。 例如，這是 [全部清除] 功能表項目的更新處理常式：  
  
 [!code-cpp[NVC_MFCDocView#3](../mfc/codesnippet/cpp/the-ccmdui-class_1.cpp)]  
  
 此處理常式會呼叫**啟用**具有功能表項目的存取權的物件成員函式。 **啟用**將項目可供使用。  
  
## <a name="see-also"></a>請參閱  
 [如何：更新使用者介面物件](../mfc/how-to-update-user-interface-objects.md)

