---
title: "對話方塊資料驗證 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- validating data [MFC], message boxes
- data validation [MFC], dialog boxes
- dialog boxes [MFC], validating data
- validating data [MFC], dialog box data entry
- DDV (dialog data validation) [MFC]
- data validation [MFC], message boxes
ms.assetid: f070c309-2044-4ff2-8c92-1ec1ea84af58
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 01766dd741ed87d9ac11b8858221a1bd09b0cf31
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="dialog-data-validation"></a>對話方塊資料驗證
中的範例所示，您可以藉由呼叫 DDV 函式，指定除了資料交換的驗證[對話方塊資料交換](../mfc/dialog-data-exchange.md)。 `DDV_MaxChars`呼叫在範例中會驗證輸入文字方塊控制項中的字串不是超過 20 個字元。 DDV 函式通常提醒使用者，以訊息方塊，如果驗證失敗，並將焦點放在違規的控制項，讓使用者可以重新輸入資料。 DDV 函式的特定控制項必須針對相同的控制項的 DDX 函式之後立即呼叫。  
  
 您也可以定義您自己自訂的 DDX 和 DDV 常式。 如需這個和其他方面的 DDX 和 DDV 的詳細資訊，請參閱[MFC 技術提示 26](../mfc/tn026-ddx-and-ddv-routines.md)。  
  
 [加入成員變數精靈](../ide/add-member-variable-wizard.md)寫入所有的 DDX 和 DDV 資料對應中為您呼叫。  
  
## <a name="see-also"></a>請參閱  
 [對話方塊資料交換和驗證](../mfc/dialog-data-exchange-and-validation.md)   
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)   
 [對話方塊資料交換](../mfc/dialog-data-exchange.md)

