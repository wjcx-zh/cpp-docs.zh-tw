---
title: "MFC ActiveX 控制項： 進階屬性實作 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
ms.assetid: ec2e6759-5a8e-41d8-a275-99af8ff6f32e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5ac8b2cb1a9c8de43ecfbd2f4712d19750bb143a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-advanced-property-implementation"></a>MFC ActiveX 控制項：進階屬性實作
本文說明實作進階屬性中的 ActiveX 控制項的相關主題：  
  
-   [唯讀和唯寫屬性](#_core_read2donly_and_write2donly_properties)  
  
-   [從屬性傳回的錯誤碼](#_core_returning_error_codes_from_a_property)  
  
##  <a name="_core_read2donly_and_write2donly_properties"></a>唯讀和唯寫屬性  
 加入屬性精靈 提供快速且輕鬆的方法，以實作控制項的唯讀或唯寫屬性。  
  
#### <a name="to-implement-a-read-only-or-write-only-property"></a>若要實作唯讀或唯寫屬性  
  
1.  載入控制項專案。  
  
2.  在 [類別檢視] 中，展開控制項的程式庫節點。  
  
3.  在控制項的介面節點 (程式庫節點的第二個節點) 上按一下滑鼠右鍵，開啟捷徑功能表。  
  
4.  從捷徑功能表，按一下 **新增**，然後按一下 **加入屬性**。  
  
     這會開啟[加入屬性精靈](../ide/names-add-property-wizard.md)。  
  
5.  在**屬性名稱**方塊中，輸入您的屬性名稱。  
  
6.  在 [實作類型] 中，按一下 [Get/Set 方法] 。  
  
7.  在**屬性型別**方塊中，選取適當的型別屬性。  
  
8.  如果您的唯讀屬性，請，清除 Set 函式名稱。 如果您的唯寫屬性，請，清除 Get 函式名稱。  
  
9. 按一下 [ **完成**]。  
  
 當您這樣做時，加入屬性精靈插入函式`SetNotSupported`或`GetNotSupported`取代正常的分派對應項目中設定或取得函式。  
  
 如果您想要變更現有的屬性是唯讀或唯寫時，您可以手動編輯分派對應，並從控制項類別中移除不必要的 Set 或 Get 函式。  
  
 如果您想要有條件地唯讀或唯寫 （例如，在特定模式下操作您的控制項時，才） 的屬性，您可以提供 Set 或 Get 函式，按照一般，並呼叫`SetNotSupported`或`GetNotSupported`函式在適當的地方。 例如:   
  
 [!code-cpp[NVC_MFC_AxUI#29](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-property-implementation_1.cpp)]  
  
 此程式碼範例會呼叫`SetNotSupported`如果`m_bReadOnlyMode`資料成員是**TRUE**。 如果**FALSE**，則屬性會設定新的值。  
  
##  <a name="_core_returning_error_codes_from_a_property"></a>從屬性傳回的錯誤碼  
 若要指出錯誤發生時嘗試取得或設定屬性，使用`COleControl::ThrowError`函式，其採用`SCODE`（狀態碼） 做為參數。 您可以使用預先定義的 `SCODE` 或自行定義一個。 取得一份預先定義`SCODE`s 和定義自訂指示`SCODE`s，請參閱[處理您的 ActiveX 控制項中的錯誤](../mfc/mfc-activex-controls-advanced-topics.md)中發行項的 ActiveX 控制項： 進階主題。  
  
 針對最常見預先定義的 helper 函式存在`SCODE`s，例如[colecontrol:: Setnotsupported](../mfc/reference/colecontrol-class.md#setnotsupported)， [colecontrol:: Getnotsupported](../mfc/reference/colecontrol-class.md#getnotsupported)，和[COleControl::SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted)。  
  
> [!NOTE]
>  `ThrowError`適用於做為傳回從錯誤中屬性的 Get 或 Set 函式或自動化方法。 這些只適用於適當的例外狀況處理常式會出現在堆疊上的時候。  
  
 如需回報程式碼的其他區域中的例外狀況的詳細資訊，請參閱[colecontrol:: Fireerror](../mfc/reference/colecontrol-class.md#fireerror)和區段[處理您的 ActiveX 控制項中的錯誤](../mfc/mfc-activex-controls-advanced-topics.md)文章 ActiveX 控制項： 進階主題。  
  
## <a name="see-also"></a>請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控制項： 屬性](../mfc/mfc-activex-controls-properties.md)   
 [MFC ActiveX 控制項： 方法](../mfc/mfc-activex-controls-methods.md)   
 [COleControl 類別](../mfc/reference/colecontrol-class.md)
