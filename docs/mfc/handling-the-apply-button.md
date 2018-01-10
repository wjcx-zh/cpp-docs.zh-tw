---
title: "處理套用按鈕 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Apply button in property sheet
- property sheets, Apply button
ms.assetid: 7e977015-59b8-406f-b545-aad0bfd8d55b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d72186d3b3d29613007291396aa07ba4060a726a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="handling-the-apply-button"></a>處理套用按鈕
屬性工作表具有標準對話方塊所沒有的能力：它們可讓使用者在關閉屬性工作表之前套用所做的變更。 這可使用 [套用] 按鈕來完成。 本文將討論您可以用於正確實作這項功能的方法。  
  
 當使用者按一下 [確定] 以關閉對話方塊時，強制回應對話方塊通常會將設定值套用至外部物件。 這也適用於屬性工作表：當使用者按一下 [確定] 時，在屬性工作表的新設定就會生效。  
  
 不過，您可能會想要讓使用者儲存設定，而不需關閉屬性工作表對話方塊。 這是 [套用] 按鈕的功能。 [套用] 按鈕會將屬性頁中所有目前的設定套用到外部物件，而不是只套用目前作用中之網頁的目前設定。  
  
 根據預設，[套用] 按鈕一律為停用狀態。 您必須撰寫程式碼以在適當時間啟用 [套用] 按鈕，因此，您必須撰寫程式碼來實作 [套用] 的效用，如下所述。  
  
 如果您不想為使用者提供 [套用] 功能，不一定非要移除 [套用] 按鈕不可。 您可以將它停用，對於使用 Windows 未來版本會提供之標準屬性工作表支援的應用程式中，這是常見的作法。  
  
 若要呈報頁面為正在修改，並啟用 [套用] 按鈕，請呼叫**cpropertypage:: Setmodified (TRUE)**。 如果有任何網頁呈報為已修改，不論目前作用中的網頁是否已修改，[套用] 按鈕都會維持啟用狀態。  
  
 您應該呼叫[cpropertypage:: Setmodified](../mfc/reference/cpropertypage-class.md#setmodified)每當使用者變更網頁中的任何設定。 若要偵測當使用者變更頁面中的設定的一種方式為每個屬性頁中的控制項實作變更通知處理常式，例如**EN_CHANGE**或**BN_CLICKED**。  
  
 若要實作 [套用] 按鈕的功用，屬性工作表必須呼叫其擁有者，或者應用程式的其他外部物件，如此就可套用目前屬性頁中的設定。 同時，屬性工作表應該停用 [套用] 按鈕藉由呼叫**cpropertypage:: Setmodified (FALSE)**套用到外部物件修改的所有頁面。  
  
 如需此程序的範例，請參閱 MFC 一般範例[PROPDLG](../visual-cpp-samples.md)。  
  
## <a name="see-also"></a>請參閱  
 [屬性工作表](../mfc/property-sheets-mfc.md)

