---
title: 如何： 建立樣板類別的訊息對應 |Microsoft Docs
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
ms.openlocfilehash: 701e6f2912c3f9a8b5f138d8f188003f9db43021
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096132"
---
# <a name="how-to-create-a-message-map-for-a-template-class"></a>如何：建立樣板類別的訊息對應
MFC 中的訊息對應提供有效方法將 Windows 訊息導向到適當的 C++ 物件執行個體。 MFC 訊息對應目標的範例，包括應用程式類別、文件和檢視類別、控制項類別等等。  
  
 傳統的 MFC 訊息對應使用宣告[BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map)巨集以宣告訊息對應巨集項目，每個訊息處理常式類別方法的開頭和最後[END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map)巨集以宣告訊息對應的結尾。  
  
 有一項限制[BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map)包含樣板引數的類別一起使用時，就會發生巨集。 當搭配使用樣板類別，此巨集會因為在巨集展開期間缺少樣板參數而導致編譯時間錯誤。 [BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map)巨集的設計是允許類別包含單一樣板引數來宣告其本身的訊息對應。  
  
## <a name="example"></a>範例  
 請試想，MFC [CListBox](../mfc/reference/clistbox-class.md)類別會擴充，以提供與外部資料來源的同步處理。 虛構`CSyncListBox`類別的宣告，如下所示：  
  
 [!code-cpp[NVC_MFC_CListBox#42](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_1.h)]  
  
 `CSyncListBox`類別是描述會與同步處理的資料來源為單一類型樣板化。 它也會宣告將參與類別的訊息對應中的三種方法： `OnPaint`， `OnDestroy`，和`OnSynchronize`。 `OnSynchronize`方法實作，如下所示：  
  
 [!code-cpp[NVC_MFC_CListBox#43](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_2.cpp)]  
  
 上述實作允許`CSyncListBox`類別會實作任何類別類型上特製化`GetCount`方法，例如`CArray`， `CList`，和`CMap`。 `StringizeElement`函式是由下列原型的樣板函式：  
  
 [!code-cpp[NVC_MFC_CListBox#44](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_3.cpp)]  
  
 通常，這個類別的訊息對應會定義如下：  
  
```cpp
BEGIN_MESSAGE_MAP(CSyncListBox, CListBox)
  ON_WM_PAINT()
  ON_WM_DESTROY()
  ON_MESSAGE(LBN_SYNCHRONIZE, OnSynchronize)
END_MESSAGE_MAP()
```
  
 何處**LBN_SYNCHRONIZE**是這類應用程式時，所定義的自訂使用者訊息：  
  
 [!code-cpp[NVC_MFC_CListBox#45](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_4.cpp)]  
  
 以上巨集對應不會進行編譯，因為，樣板規格`CSyncListBox`類別巨集展開期間將會遺失。 **BEGIN_TEMPLATE_MESSAGE_MAP**巨集解決這個問題所指定的樣板參數併入展開的巨集對應。 這個類別的訊息對應會成為：  
  
 [!code-cpp[NVC_MFC_CListBox#46](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_5.cpp)]  
  
 以下示範的範例用法`CSyncListBox`類別使用`CStringList`物件：  
  
 [!code-cpp[NVC_MFC_CListBox#47](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_6.cpp)]  
  
 若要完成本測試中，`StringizeElement`函式，必須使用特製化`CStringList`類別：  
  
 [!code-cpp[NVC_MFC_CListBox#48](../mfc/codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_7.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map)   
 [訊息處理和對應](../mfc/message-handling-and-mapping.md)

