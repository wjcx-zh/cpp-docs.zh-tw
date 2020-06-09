---
title: 如何：建立樣板類別的訊息對應
ms.date: 11/04/2016
helpviewer_keywords:
- template classes [MFC], creating message maps
- message maps [MFC], template classes
ms.assetid: 4e7e24f8-06df-4b46-82aa-7435c8650de3
ms.openlocfilehash: 65ddc77b4e8fd466c7d651e54e93a504b4858da1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620054"
---
# <a name="how-to-create-a-message-map-for-a-template-class"></a>如何：建立樣板類別的訊息對應

MFC 中的訊息對應提供有效方法將 Windows 訊息導向到適當的 C++ 物件執行個體。 MFC 訊息對應目標的範例，包括應用程式類別、文件和檢視類別、控制項類別等等。

傳統 MFC 訊息對應是使用[BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map)宏來宣告，以宣告訊息對應的開頭、每個訊息處理常式類別方法的宏專案，最後是[END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map)宏來宣告訊息對應的結尾。

當與包含樣板引數的類別搭配使用時，會發生[BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map)宏的其中一項限制。 當搭配使用樣板類別，此巨集會因為在巨集展開期間缺少樣板參數而導致編譯時期錯誤。 [BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map)宏的設計，是為了允許包含單一樣板引數的類別，宣告自己的訊息對應。

## <a name="example"></a>範例

假設有一個範例，其中 MFC [CListBox](reference/clistbox-class.md)類別會擴充，以提供與外部資料源的同步處理。 虛構類別的宣告 `CSyncListBox` 方式如下：

[!code-cpp[NVC_MFC_CListBox#42](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_1.h)]

`CSyncListBox`類別會在單一類型上進行樣板化，以描述其將與之同步處理的資料來源。 它也會宣告三個將參與類別之訊息對應的方法： `OnPaint` 、 `OnDestroy` 和 `OnSynchronize` 。 方法的執行方式如下 `OnSynchronize` ：

[!code-cpp[NVC_MFC_CListBox#43](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_2.cpp)]

上述的實作為可讓 `CSyncListBox` 類別在任何執行方法的類別類型上特製化 `GetCount` ，例如 `CArray` 、 `CList` 和 `CMap` 。 函式 `StringizeElement` 是由下列所提供的樣板函式原型：

[!code-cpp[NVC_MFC_CListBox#44](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_3.cpp)]

通常，這個類別的訊息對應會定義如下：

```cpp
BEGIN_MESSAGE_MAP(CSyncListBox, CListBox)
  ON_WM_PAINT()
  ON_WM_DESTROY()
  ON_MESSAGE(LBN_SYNCHRONIZE, OnSynchronize)
END_MESSAGE_MAP()
```

其中**LBN_SYNCHRONIZE**是應用程式所定義的自訂使用者訊息，例如：

[!code-cpp[NVC_MFC_CListBox#45](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_4.cpp)]

上述宏對應將不會編譯，因為在宏展開期間，類別的範本規格 `CSyncListBox` 將會遺失。 **BEGIN_TEMPLATE_MESSAGE_MAP**宏會藉由將指定的樣板參數併入展開的宏對應來解決此情況。 這個類別的訊息對應會成為：

[!code-cpp[NVC_MFC_CListBox#46](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_5.cpp)]

以下示範使用物件之類別的範例用法 `CSyncListBox` `CStringList` ：

[!code-cpp[NVC_MFC_CListBox#47](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_6.cpp)]

若要完成測試，函式 `StringizeElement` 必須專門用來與類別搭配使用 `CStringList` ：

[!code-cpp[NVC_MFC_CListBox#48](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_7.cpp)]

## <a name="see-also"></a>另請參閱

[BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map)<br/>
[訊息處理和對應](message-handling-and-mapping.md)
