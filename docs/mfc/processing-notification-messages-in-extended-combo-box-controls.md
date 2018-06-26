---
title: 中的通知訊息的處理擴充下拉式方塊控制項 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- extended combo boxes [MFC], notifications
- notifications [MFC], extended combo box controls
ms.assetid: 4e442758-d054-4746-bb1a-6ff84accb127
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 576735841748d0b99053d038f8d5f674d5692f00
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930185"
---
# <a name="processing-notification-messages-in-extended-combo-box-controls"></a>處理擴充下拉式方塊控制項中的通知訊息
當使用者與擴充的下拉式方塊互動時，控制項 (`CComboBoxEx`) 會將通知訊息傳送至其父視窗，通常是檢視或對話方塊物件。 如果您想要執行動作以作為回應，請處理這些訊息。 例如，當使用者啟動下拉式清單，或按一下控制項的編輯方塊中，CBEN_BEGINEDIT 傳送通知。  
  
 使用 [屬性] 視窗，將通知處理常式加入您想要實作之這些訊息的父類別。  
  
 下列清單描述擴充的下拉式方塊控制項所傳送的各種通知。  
  
-   當使用者啟動下拉式清單，或按一下控制項的編輯方塊中，就會傳送 CBEN_BEGINEDIT。  
  
-   CBEN_DELETEITEM 傳送已刪除項目時。  
  
-   CBEN_DRAGBEGIN 傳送，當使用者開始拖曳顯示在控制項的編輯部分中之項目的影像。  
  
-   CBEN_ENDEDIT 傳送使用者已經結束編輯方塊內的作業，或已從控制項的下拉式清單中選取項目。  
  
-   CBEN_GETDISPINFO 傳送擷取回呼項目的顯示資訊。  
  
-   CBEN_INSERTITEM 送出時已在控制項中插入新項目。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [控制項](../mfc/controls-mfc.md)

