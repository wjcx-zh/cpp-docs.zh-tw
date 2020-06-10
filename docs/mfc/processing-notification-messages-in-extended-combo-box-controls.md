---
title: 處理擴充下拉式方塊控制項中的通知訊息
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes [MFC], notifications
- notifications [MFC], extended combo box controls
ms.assetid: 4e442758-d054-4746-bb1a-6ff84accb127
ms.openlocfilehash: 58a7c5ec36807489d24014055c39775b4552be03
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620991"
---
# <a name="processing-notification-messages-in-extended-combo-box-controls"></a>處理擴充下拉式方塊控制項中的通知訊息

當使用者與擴充的下拉式方塊互動時，控制項 (`CComboBoxEx`) 會將通知訊息傳送至其父視窗，通常是檢視或對話方塊物件。 如果您想要執行動作以作為回應，請處理這些訊息。 例如，當使用者啟動下拉式清單，或按一下控制項的編輯方塊時，就會傳送 CBEN_BEGINEDIT 通知。

使用 [[類別] [Wizard]](reference/mfc-class-wizard.md) ，將通知處理常式新增至您要執行之訊息的父類別。

下列清單描述擴充的下拉式方塊控制項所傳送的各種通知。

- CBEN_BEGINEDIT 當使用者啟動下拉式清單，或按一下控制項的編輯方塊時所傳送。

- CBEN_DELETEITEM 項目已刪除時所傳送。

- CBEN_DRAGBEGIN 當使用者開始拖曳顯示在控制項編輯部分的項目影像時所傳送。

- CBEN_ENDEDIT 當使用者已經結束編輯方塊內的作業，或已從控制項下拉式清單中選取項目時所傳送。

- CBEN_GETDISPINFO 要擷取回呼項目的顯示資訊時所傳送。

- CBEN_INSERTITEM 當新項目已插入控制項中時所傳送。

## <a name="see-also"></a>另請參閱

[使用 CComboBoxEx](using-ccomboboxex.md)<br/>
[控制項](controls-mfc.md)
