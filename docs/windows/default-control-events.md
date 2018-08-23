---
title: 預設控制項事件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Dialog editor, default control events
- controls [C++], default control events
- events [C++], controls
- dialog box controls, events
ms.assetid: 75556b23-18f5-4390-97a4-2ecad3309741
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1a208e85418f362bfa698055ba6b3b403c21bce0
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610866"
---
# <a name="default-control-events"></a>預設控制項事件

下列控制項名稱有隨附的預設事件：

|控制項名稱|預設事件|
|------------------|-------------------|
|動畫|ACN_START|
|核取方塊|BN_CLICKED|
|下拉式方塊|CBN_SELCHANGE|
|自訂|TTN_GETDISPINFO|
|日期時間選擇器|DTN_DATETIMECHANGE|
|編輯方塊|EN_CHANGE|
|群組方塊|（不適用）|
|熱鍵|NM_OUTOFMEMORY|
|IP 位址|IPN_FIELDCHANGED|
|清單|LVN_ITEMCHANGE|
|清單方塊|LBN_SELCHANGE|
|月份的行事曆|MCN_SELCHANGE|
|圖片控制項|（不適用）|
|進度|NM_CUSTOMDRAW|
|推播 按鈕|BN_CLICKED|
|選項按鈕|BN_CLICKED|
|豐富的編輯|EN_CHANGE|
|捲軸|NM_THEMECHANGED|
|滑桿|NM_CUSTOMDRAW|
|微調|UDN_DELTAPOS|
|靜態文字|（不適用）|
|索引標籤|TCN_SELCHANGE|
|樹狀結構|TVN_SELCHANGE|

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[定義對話方塊控制項的成員變數](../windows/defining-member-variables-for-dialog-controls.md)  
[與使用者介面物件關聯的訊息類型](../mfc/reference/message-types-associated-with-user-interface-objects.md)  
[編輯訊息處理常式](../mfc/reference/editing-a-message-handler.md)  
[定義反映訊息的訊息處理常式](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)  
[根據新控制項類別來宣告變數](../mfc/reference/declaring-a-variable-based-on-your-new-control-class.md)  
[覆寫虛擬函式](../ide/overriding-a-virtual-function-visual-cpp.md)