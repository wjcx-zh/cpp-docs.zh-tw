---
title: "MFC 使用的樣式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.styles
dev_langs:
- C++
helpviewer_keywords:
- edit styles [MFC]
- window styles, in MFC
- styles
- frame windows, styles
- message-box styles
- styles, MFC
- buttons, MFC toolbars
- list boxes, styles
- static styles
- scroll-bar styles [MFC]
- combo boxes, styles
- extended window styles
ms.assetid: d3b9af37-31b5-4c97-a8ad-189fd724b04c
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 344d2ce3de15403e17f29dc9504253cbb0ade607
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="styles-used-by-mfc"></a>MFC 使用的樣式
當您建立相對應 MFC 物件時，請使用下列的樣式。 在大部分情況下，在中設定這些樣式`dwStyle`參數類別的**建立**函式。  
  
### <a name="mfc-styles"></a>MFC 樣式  
  
|樣式|描述|  
|-----------|-----------------|  
|[按鈕樣式](../../mfc/reference/button-styles.md)|適用於[CButton 類別](../../mfc/reference/cbutton-class.md)物件，例如選項按鈕核取方塊和按鈕。 指定組合中的樣式`dwStyle`參數[CButton::Create](../../mfc/reference/cbutton-class.md#create)。|  
|[下拉式方塊樣式](../../mfc/reference/combo-box-styles.md)|適用於[CComboBox 類別](../../mfc/reference/ccombobox-class.md)物件。 指定組合中的樣式`dwStyle`參數[CComboBox::Create](../../mfc/reference/ccombobox-class.md#create)。|  
|[編輯樣式](../../mfc/reference/edit-styles.md)|適用於[CEdit 類別](../../mfc/reference/cedit-class.md)物件。 指定組合中的樣式`dwStyle`參數[CEdit::Create](../../mfc/reference/cedit-class.md#create)。|  
|[框架視窗樣式](../../mfc/reference/frame-window-styles-mfc.md)|適用於[CFrameWnd 類別](../../mfc/reference/cframewnd-class.md)物件。 指定組合中的樣式`dwStyle`參數[CFrameWnd::Create](../../mfc/reference/cframewnd-class.md#create)。|  
|[清單方塊樣式](../../mfc/reference/list-box-styles.md)|適用於[CListBox 類別](../../mfc/reference/clistbox-class.md)物件。 指定組合中的樣式`dwStyle`參數[CListBox::Create](../../mfc/reference/clistbox-class.md#create)。|  
|[訊息方塊樣式](../../mfc/reference/message-box-styles.md)|適用於[AfxMessageBox](../../mfc/reference/cstring-formatting-and-message-box-display.md#afxmessagebox)項目。 指定組合中的樣式`nType`參數`AfxMessageBox`。|  
|[捲軸樣式](../../mfc/reference/scroll-bar-styles.md)|適用於[CScrollBar 類別](../../mfc/reference/cscrollbar-class.md)物件。 指定組合中的樣式`dwStyle`參數[CScrollBar::Create](../../mfc/reference/cscrollbar-class.md#create)。|  
|[靜態樣式](../../mfc/reference/static-styles.md)|適用於[CStatic 類別](../../mfc/reference/cstatic-class.md)物件。 指定組合中的樣式`dwStyle`參數[CStatic::Create](../../mfc/reference/cstatic-class.md#create)。|  
|[視窗樣式](../../mfc/reference/window-styles.md)|適用於[CWnd 類別](../../mfc/reference/cwnd-class.md)物件。 指定組合中的樣式`dwStyle`參數[cwnd:: Create](../../mfc/reference/cwnd-class.md#create)或[CWnd::CreateEx](../../mfc/reference/cwnd-class.md#createex)。|  
|[延伸的視窗樣式](../../mfc/reference/extended-window-styles.md)|適用於[CWnd 類別](../../mfc/reference/cwnd-class.md)物件。 指定組合中的樣式`dwExStyle`參數[CWnd::CreateEx](../../mfc/reference/cwnd-class.md#createex)。|  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../mfc/class-library-overview.md)


