---
title: 處理擴充下拉式方塊控制項中的通知訊息
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes [MFC], notifications
- notifications [MFC], extended combo box controls
ms.assetid: 4e442758-d054-4746-bb1a-6ff84accb127
ms.openlocfilehash: 1890267f26ef43fd1dbf8fdea28f02e3d882d475
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378189"
---
# <a name="processing-notification-messages-in-extended-combo-box-controls"></a>處理擴充下拉式方塊控制項中的通知訊息

當使用者與擴充的下拉式方塊互動時，控制項 (`CComboBoxEx`) 會將通知訊息傳送至其父視窗，通常是檢視或對話方塊物件。 如果您想要執行動作以作為回應，請處理這些訊息。 例如，當使用者啟動下拉式清單，或按一下控制項的編輯方塊中，CBEN_BEGINEDIT 會傳送通知。

使用 [屬性] 視窗，將通知處理常式加入您想要實作之這些訊息的父類別。

下列清單描述擴充的下拉式方塊控制項所傳送的各種通知。

- 當使用者啟動下拉式清單，或按一下控制項的編輯方塊中，就會傳送 CBEN_BEGINEDIT。

- CBEN_DELETEITEM 傳送已刪除項目時。

- 當使用者開始拖曳顯示在控制項編輯部分中的項目影像時，就會傳送 CBEN_DRAGBEGIN。

- 當使用者已經結束編輯方塊內的作業，或已從控制項下拉式清單中選取項目時，就會傳送 CBEN_ENDEDIT。

- CBEN_GETDISPINFO 傳送要擷取回呼項目的顯示資訊。

- 當控制項已插入新項目時，就會傳送 CBEN_INSERTITEM。

## <a name="see-also"></a>另請參閱

[使用 CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[控制項](../mfc/controls-mfc.md)
