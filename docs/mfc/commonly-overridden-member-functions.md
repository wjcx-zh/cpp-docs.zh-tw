---
title: 常被覆寫的成員函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CDialog class [MFC], members
- OnInitDialog function
- dialog classes [MFC], commonly overridden member functions
- OnCancel function
- overriding, dialog class members
- OnOK function
- MFC dialog boxes [MFC], overriding member functions
ms.assetid: 78eb566c-e361-4c86-8db5-c7e2791b249a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ed090057394c385dd12825864c5de9ff7d079e29
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="commonly-overridden-member-functions"></a>常被覆寫的成員函式
下表列出 `CDialog` 衍生類別中很可能覆寫的成員函式。  
  
### <a name="commonly-overridden-member-functions-of-class-cdialog"></a>通常覆寫的類別 CDialog 成員函式  
  
|成員函式|它的回覆訊息|覆寫的目的|  
|---------------------|----------------------------|-----------------------------|  
|`OnInitDialog`|**WM_INITDIALOG**|初始化對話方塊的控制項。|  
|`OnOK`|**BN_CLICKED**按鈕**IDOK**|當使用者按一下 [確定] 按鈕時會回應。|  
|`OnCancel`|**BN_CLICKED**按鈕**IDCANCEL**|當使用者按一下 [取消] 按鈕時會回應。|  
  
 `OnInitDialog`、`OnOK` 和 `OnCancel` 是虛擬函式。 若要覆寫它們，您必須宣告覆寫的函式在衍生的對話方塊類別中使用[屬性 視窗](/visualstudio/ide/reference/properties-window)。  
  
 就在對話方塊顯示之前，會呼叫 `OnInitDialog`。 您必須從您的覆寫呼叫預設的 `OnInitDialog` 處理常式 (通常做為處理常式的第一個動作)。 根據預設，`OnInitDialog`傳回**TRUE**表示焦點應該設定的第一個控制項，在對話方塊中。  
  
 通常會為非強制回應對話方塊 (而不會為強制回應對話方塊) 覆寫 `OnOK`。 如果您為強制回應對話方塊覆寫此處理常式，請從您的覆寫呼叫基底類別版本，以確保會呼叫 `EndDialog`，或者您自行呼叫 `EndDialog`。  
  
 通常會為非強制回應對話方塊覆寫 `OnCancel`。  
  
 如需有關這些成員函式的詳細資訊，請參閱類別[CDialog](../mfc/reference/cdialog-class.md)中*MFC 參考*和討論[對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)。  
  
## <a name="see-also"></a>另請參閱  
 [對話方塊](../mfc/dialog-boxes.md)   
 [常新增的成員函式](../mfc/commonly-added-member-functions.md)
