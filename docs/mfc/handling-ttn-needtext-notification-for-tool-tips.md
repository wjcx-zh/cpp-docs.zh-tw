---
title: 處理工具提示的 TTN_NEEDTEXT 告知 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TTN_NEEDTEXT
dev_langs:
- C++
helpviewer_keywords:
- TTN_NEEDTEXT message [MFC]
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: d0370a65-21ba-4676-bcc5-8cf851bbb15c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ce7a4d6dc6edf122b5d9b5301768dea8389e771e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="handling-ttnneedtext-notification-for-tool-tips"></a>處理工具提示的 TTN_NEEDTEXT 告知
做為一部分[啟用工具提示](../mfc/enabling-tool-tips.md)，您處理**TTN_NEEDTEXT**將下列項目加入至主控視窗的訊息對應的訊息：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_1.cpp)]  
  
 `memberFxn`  
 需要此按鈕的文字時所要呼叫此成員函式。  
  
 請注意，工具提示的識別碼一律為 0。  
  
 您的處理常式函式類別定義中進行宣告，如下所示：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#53](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_2.h)]  
  
 其中是設為斜體的參數：  
  
 `id`  
 傳送通知之控制項的識別項。 未使用。 控制項 id 取自**NMHDR**結構。  
  
 `pNMHDR`  
 指標[NMTTDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb760258)結構。 此外也會討論這個結構中進一步[TOOLTIPTEXT 結構](../mfc/tooltiptext-structure.md)。  
  
 `pResult`  
 結果的程式碼之指標您可以設定才能傳回。 **TTN_NEEDTEXT**處理常式可以忽略`pResult`參數。  
  
 例如表單檢視通知處理常式中：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#54](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_3.cpp)]  
  
 呼叫`EnableToolTips`(取自此片段`OnInitDialog`):  
  
 [!code-cpp[NVC_MFCControlLadenDialog#55](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_4.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [非衍生自 CFrameWnd 之視窗中的工具提示](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)

