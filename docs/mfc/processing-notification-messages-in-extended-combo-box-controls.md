---
title: 處理擴充下拉式方塊控制項中的通知訊息
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes [MFC], notifications
- notifications [MFC], extended combo box controls
ms.assetid: 4e442758-d054-4746-bb1a-6ff84accb127
ms.openlocfilehash: 044cef644f746f7cb70944805882bd8e2f2806b4
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908102"
---
# <a name="processing-notification-messages-in-extended-combo-box-controls"></a>處理擴充下拉式方塊控制項中的通知訊息

當使用者與擴充的下拉式方塊互動時，控制項 (`CComboBoxEx`) 會將通知訊息傳送至其父視窗，通常是檢視或對話方塊物件。 如果您想要執行動作以作為回應，請處理這些訊息。 例如，當使用者啟動下拉式清單，或按一下控制項的編輯方塊時，就會傳送 CBEN_BEGINEDIT 通知。

使用 [[類別] [Wizard]](reference/mfc-class-wizard.md) ，將通知處理常式新增至您要執行之訊息的父類別。

下列清單描述擴充的下拉式方塊控制項所傳送的各種通知。

- 當使用者啟動下拉式清單，或按一下控制項的編輯方塊時，就會傳送 CBEN_BEGINEDIT。

- 刪除專案時傳送的 CBEN_DELETEITEM。

- 當使用者開始拖曳控制項的編輯部分中所顯示之專案的影像時，所傳送的 CBEN_DRAGBEGIN。

- 當使用者已結束編輯方塊中的作業，或已從控制項的下拉式清單中選取專案時，就會傳送 CBEN_ENDEDIT。

- CBEN_GETDISPINFO 傳送以取得回呼專案的顯示資訊。

- 在控制項中插入新的專案時傳送的 CBEN_INSERTITEM。

## <a name="see-also"></a>另請參閱

[使用 CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[控制項](../mfc/controls-mfc.md)
