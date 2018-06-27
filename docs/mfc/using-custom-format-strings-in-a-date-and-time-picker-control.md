---
title: 使用自訂格式字串中的日期和時間選擇器控制項 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CDateTimeCtrl class [MFC], display styles
- DateTimePicker control [MFC], display styles
- DateTimePicker control [MFC]
ms.assetid: 7d577f03-6ca0-4597-9093-50b78f304719
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9aeb6c02041a4ba90f9721f23a1397e17a4cdf81
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36955754"
---
# <a name="using-custom-format-strings-in-a-date-and-time-picker-control"></a>在日期時間選擇器控制項中使用自訂格式字串
根據預設，日期時間選擇器控制項會以三種格式類型 (每種格式對應一獨特的樣式) 顯示目前的日期或時間：  
  
-   **DTS_LONGDATEFORMAT**以長格式，產生如 「 星期三，年 1 月 3，2000"的輸出中顯示的日期。  
  
-   **DTS_SHORTDATEFORMAT**簡短格式，產生如 「 1/3/00 」 的輸出中顯示的日期。  
  
-   **DTS_TIMEFORMAT**以長格式，產生如 「 5:31:42 PM 」 的輸出中顯示的時間。  
  
 不過，您可以使用自訂格式字串，自訂日期或時間的顯示外觀。 這個自訂字串由現有的格式字元、非格式字元組成或混合兩者。 建置自訂字串之後，呼叫以[cdatetimectrl:: Setformat](../mfc/reference/cdatetimectrl-class.md#setformat)傳入您自訂的字串。 日期和時間選擇器控制項會使用您的自訂格式字串顯示目前的值。  
  
 下列範例程式碼 (其中*這裡，m_dtPicker*是`CDateTimeCtrl`物件) 示範一個可行的解決方案：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#7](../mfc/codesnippet/cpp/using-custom-format-strings-in-a-date-and-time-picker-control_1.cpp)]  
  
 除了自訂格式字串，日期和時間選擇器控制項也支援[回呼欄位](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [控制項](../mfc/controls-mfc.md)

