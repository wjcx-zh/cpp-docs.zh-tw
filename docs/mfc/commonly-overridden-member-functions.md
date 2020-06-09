---
title: 常被覆寫的成員函式
ms.date: 09/06/2019
helpviewer_keywords:
- CDialog class [MFC], members
- OnInitDialog function
- dialog classes [MFC], commonly overridden member functions
- OnCancel function
- overriding, dialog class members
- OnOK function
- MFC dialog boxes [MFC], overriding member functions
ms.assetid: 78eb566c-e361-4c86-8db5-c7e2791b249a
ms.openlocfilehash: 7d4fc9005ff368ef6a83252e8cf0b2005ecf2cef
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619657"
---
# <a name="commonly-overridden-member-functions"></a>常被覆寫的成員函式

下表列出 `CDialog` 衍生類別中很可能覆寫的成員函式。

### <a name="commonly-overridden-member-functions-of-class-cdialog"></a>通常覆寫的類別 CDialog 成員函式

|成員函數|它的回覆訊息|覆寫的目的|
|---------------------|----------------------------|-----------------------------|
|`OnInitDialog`|**WM_INITDIALOG**|初始化對話方塊的控制項。|
|`OnOK`|**BN_CLICKED**按鈕**IDOK**|當使用者按一下 [確定] 按鈕時會回應。|
|`OnCancel`|**BN_CLICKED**按鈕**IDCANCEL**|當使用者按一下 [取消] 按鈕時會回應。|

`OnInitDialog`、`OnOK` 和 `OnCancel` 是虛擬函式。 若要覆寫它們，您可以使用[MFC 類別 Wizard](reference/mfc-class-wizard.md)，在衍生的對話方塊類別中宣告覆寫函式。

就在對話方塊顯示之前，會呼叫 `OnInitDialog`。 您必須從您的覆寫呼叫預設的 `OnInitDialog` 處理常式 (通常做為處理常式的第一個動作)。 根據預設， `OnInitDialog` 會傳回**TRUE** ，表示焦點應該設定為對話方塊中的第一個控制項。

通常會為非強制回應對話方塊 (而不會為強制回應對話方塊) 覆寫 `OnOK`。 如果您為強制回應對話方塊覆寫此處理常式，請從您的覆寫呼叫基底類別版本，以確保會呼叫 `EndDialog`，或者您自行呼叫 `EndDialog`。

通常會為非強制回應對話方塊覆寫 `OnCancel`。

如需這些成員函式的詳細資訊，請參閱*Mfc 參考*中的類別[CDIALOG](reference/cdialog-class.md)和在[mfc 中使用對話方塊](life-cycle-of-a-dialog-box.md)的討論。

## <a name="see-also"></a>另請參閱

[對話方塊](dialog-boxes.md)<br/>
[常新增的成員函式](commonly-added-member-functions.md)
