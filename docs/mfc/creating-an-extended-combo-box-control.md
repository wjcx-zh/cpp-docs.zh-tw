---
title: 建立擴充的下拉式方塊控制項 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- extended combo boxes
- CComboBoxEx class [MFC], creating extended combo box controls
- extended combo boxes [MFC], creating
ms.assetid: a964267e-97b6-4e77-9f89-55bb5c68913f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c6a891aeadf2fa8366eec52a967e13776db6523
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341208"
---
# <a name="creating-an-extended-combo-box-control"></a>建立擴充的下拉式方塊控制項
建立擴充的下拉式方塊控制項的方式取決於您是使用控制項在對話方塊中還是非對話方塊視窗中建立。  
  
### <a name="to-use-ccomboboxex-directly-in-a-dialog-box"></a>在對話方塊中直接使用 CComboBoxEx  
  
1.  在對話方塊編輯器中，將擴充的下拉式方塊控制項加入至對話方塊範本資源。 指定其控制項 ID.  
  
2.  指定需要使用 [屬性] 對話方塊的擴充的下拉式方塊控制項的樣式。  
  
3.  使用[加入成員變數精靈](../ide/adding-a-member-variable-visual-cpp.md)新增類型的成員變數[CComboBoxEx](../mfc/reference/ccomboboxex-class.md)與控制項屬性。 您可以使用這個成員呼叫 `CComboBoxEx` 成員函式。  
  
4.  使用 [屬性] 視窗將在您需要處理所有擴充的下拉式方塊控制項通知訊息的對話方塊類別中的處理常式函式對應 (請參閱[訊息對應到函式](../mfc/reference/mapping-messages-to-functions.md))。  
  
5.  在[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)，設定的任何其他樣式`CComboBoxEx`物件。  
  
### <a name="to-use-ccomboboxex-in-a-nondialog-window"></a>若要在非對話方塊視窗中使用 CComboBoxEx  
  
1.  在檢視或視窗類別中定義控制項。  
  
2.  呼叫控制項的[建立](../mfc/reference/ctabctrl-class.md#create)成員函式，可能在[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)，方式與父視窗[OnCreate](../mfc/reference/cwnd-class.md#oncreate)處理常式函式。 設定控制項的樣式。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [控制項](../mfc/controls-mfc.md)

