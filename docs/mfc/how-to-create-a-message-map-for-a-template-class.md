---
title: 如何： 建立樣板類別的訊息對應 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- template classes [MFC], creating message maps
- message maps [MFC], template classes
ms.assetid: 4e7e24f8-06df-4b46-82aa-7435c8650de3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6781ca14b174608a815a0300750dd6a3d9aa96bb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354776"
---
# <a name="how-to-create-a-message-map-for-a-template-class"></a>如何：建立樣板類別的訊息對應
MFC 中的訊息對應提供有效方法將 Windows 訊息導向到適當的 C++ 物件執行個體。 MFC 訊息對應目標的範例，包括應用程式類別、文件和檢視類別、控制項類別等等。  
  
 傳統的 MFC 訊息對應宣告使用[BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map)巨集來宣告的訊息對應，每個訊息處理常式類別方法的巨集項目開始，最後[END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map)巨集來宣告的訊息對應的結尾。  
  
 有一個限制[BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map)包含樣板引數的類別一起使用時，就會發生巨集。 當搭配使用樣板類別，此巨集會因為在巨集展開期間缺少樣板參數而導致編譯時間錯誤。 [BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map)巨集設計用來允許類別包含單一的樣板引數宣告自己的訊息對應。  
  
## <a name="example"></a>範例  
 請考慮使用範例其中 MFC [CListBox](../mfc/reference/clistbox-class.md)類別會擴充以提供與外部資料來源的同步處理。 虛構**CSyncListBox**類別的宣告，如下所示：  
  
 [!code-cpp[NVC_MFC_CListBox#42](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_1.h)]  
  
 **CSyncListBox**類別是描述將與同步處理的資料來源為單一類型樣板化。 它也會宣告三種方法，將參與類別的訊息對應： **OnPaint**， **OnDestroy**，和**OnSynchronize**。 **OnSynchronize**方法實作，如下所示：  
  
 [!code-cpp[NVC_MFC_CListBox#43](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_2.cpp)]  
  
 上述實作允許**CSyncListBox**類別實作的任何類別類型上特製化**GetCount**方法，例如**CArray**， **CList**，和**CMap**。 **StringizeElement**函式是由下列原型的樣板函式：  
  
 [!code-cpp[NVC_MFC_CListBox#44](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_3.cpp)]  
  
 通常，這個類別的訊息對應會定義如下：  
  
 `BEGIN_MESSAGE_MAP(CSyncListBox, CListBox)`  
  
 `ON_WM_PAINT()`  
  
 `ON_WM_DESTROY()`  
  
 `ON_MESSAGE(LBN_SYNCHRONIZE, OnSynchronize)`  
  
 `END_MESSAGE_MAP()`  
  
 其中**LBN_SYNCHRONIZE**是應用程式，例如定義的自訂使用者訊息：  
  
 [!code-cpp[NVC_MFC_CListBox#45](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_4.cpp)]  
  
 以上巨集對應不會進行編譯，因為用的樣板規格**CSyncListBox**類別巨集展開期間將會遺失。 **BEGIN_TEMPLATE_MESSAGE_MAP**巨集便可解決這個所指定的樣板參數併入展開的巨集對應。 這個類別的訊息對應會成為：  
  
 [!code-cpp[NVC_MFC_CListBox#46](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_5.cpp)]  
  
 以下示範的範例使用方式**CSyncListBox**類別使用**CStringList**物件：  
  
 [!code-cpp[NVC_MFC_CListBox#47](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_6.cpp)]  
  
 若要完成的測試， **StringizeElement**函式必須專門用來搭配**CStringList**類別：  
  
 [!code-cpp[NVC_MFC_CListBox#48](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_7.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map)   
 [訊息處理和對應](../mfc/message-handling-and-mapping.md)

