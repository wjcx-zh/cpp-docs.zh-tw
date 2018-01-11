---
title: "中的通知訊息的處理擴充下拉式方塊控制項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- extended combo boxes [MFC], notifications
- notifications [MFC], extended combo box controls
ms.assetid: 4e442758-d054-4746-bb1a-6ff84accb127
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a78e7b9fd8f9c67f14a4bb51088866785d372cca
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="processing-notification-messages-in-extended-combo-box-controls"></a>處理擴充下拉式方塊控制項中的通知訊息
當使用者與擴充的下拉式方塊互動時，控制項 (`CComboBoxEx`) 會將通知訊息傳送至其父視窗，通常是檢視或對話方塊物件。 如果您想要執行動作以作為回應，請處理這些訊息。 例如，當使用者啟動下拉式清單，或按一下控制項的編輯方塊時，就會傳送 **CBEN_BEGINEDIT** 通知。  
  
 使用 [屬性] 視窗，將通知處理常式加入您想要實作之這些訊息的父類別。  
  
 下列清單描述擴充的下拉式方塊控制項所傳送的各種通知。  
  
-   **CBEN_BEGINEDIT** 當使用者啟動下拉式清單，或按一下控制項的編輯方塊時所傳送。  
  
-   **CBEN_DELETEITEM** 項目已刪除時所傳送。  
  
-   **CBEN_DRAGBEGIN** 當使用者開始拖曳顯示在控制項編輯部分的項目影像時所傳送。  
  
-   **CBEN_ENDEDIT** 當使用者已經結束編輯方塊內的作業，或已從控制項下拉式清單中選取項目時所傳送。  
  
-   **CBEN_GETDISPINFO** 要擷取回呼項目的顯示資訊時所傳送。  
  
-   **CBEN_INSERTITEM** 當新項目已插入控制項中時所傳送。  
  
## <a name="see-also"></a>請參閱  
 [使用 CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [控制項](../mfc/controls-mfc.md)

