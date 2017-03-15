---
title: "按鈕樣式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BS_DEFPUSHBUTTON
- BS_NOTIFY
- BS_MULTILINE
- BS_AUTOCHECKBOX
- BS_3STATE
- BS_BITMAP
- BS_TOP
- BS_PUSHBUTTON
- BS_PUSHLIKE
- BS_AUTO3STATE
- BS_CHECKBOX
- BS_AUTORADIOBUTTON
- BS_RADIOBUTTON
- BS_OWNERDRAW
- BS_LEFT
- BS_USERBUTTON
- BS_RIGHTBUTTON
- BS_RIGHT
- BS_LEFTTEXT
- BS_TEXT
- BS_BOTTOM
- BS_GROUPBOX
- BS_FLAT
- BS_VCENTER
- BS_ICON
- BS_CENTER
dev_langs:
- C++
helpviewer_keywords:
- BS_NOTIFY constant
- BS_RIGHTBUTTON constant
- styles, button objects
- BS_USERBUTTON constant
- BS_VCENTER constant
- BS_PUSHLIKE constant
- BS_RADIOBUTTON constant
- BS_PUSHBUTTON constant
- BS_DEFPUSHBUTTON constant
- BS_LEFTTEXT constant
- button objects (CButton), button styles
- BS_AUTO3STATE constant
- BS_3STATE constant
- BS_OWNERDRAW constant
- BS_AUTORADIOBUTTON constant
- BS_GROUPBOX constant
- BS_BITMAP constant
- BS_CENTER constant
- BS_MULTILINE constant
- BS_BOTTOM constant
- BS_FLAT constant
- BS_AUTOCHECKBOX constant
- BS_RIGHT constant
- BS_CHECKBOX constant
- BS_LEFT constant
- BS_ICON constant
- BS_TOP constant
- BS_TEXT constant
ms.assetid: 41206f72-2b92-4250-ae32-31184046402f
caps.latest.revision: 20
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
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: cdd577cd6915a1f3c1e05fae68f7fed47cc79236
ms.lasthandoff: 02/24/2017

---
# <a name="button-styles"></a>按鈕樣式
本主題說明的按鈕類型和樣式。  
  
## <a name="button-types"></a>按鈕類型  
 下表列出的按鈕類型。 您可以選擇下列其中一個項目。 如果未指定按鈕類型，預設值是`BS_PUSHBUTTON`。  
  
|類型|描述|  
|----------|-----------------|  
|`BS_3STATE`|建立具有三種狀態的核取方塊按鈕︰ `BST_CHECKED`， `BST_INDETERMINATE`，和`BST_UNCHECKED`。 按一下按鈕會傳送`BN_CLICKED`主控視窗的通知，但不變更按鈕的狀態。 根據預設，相關聯的文字會顯示核取方塊的右邊。 若要顯示的文字左邊的核取方塊，請使用`BS_LEFTTEXT`或`BS_RIGHTBUTTON`樣式。|  
|`BS_AUTO3STATE`|建立具有三種狀態的核取方塊按鈕︰ `BST_CHECKED`， `BST_INDETERMINATE`，和`BST_UNCHECKED`。 按一下按鈕會傳送`BN_CLICKED`主控視窗的通知，並變更按鈕的狀態。 按鈕狀態的順序循環`BST_CHECKED`， `BST_INDETERMINATE`，和`BST_UNCHECKED`。 根據預設，相關聯的文字會顯示核取方塊的右邊。 若要顯示的文字左邊的核取方塊，請使用`BS_LEFTTEXT`或`BS_RIGHTBUTTON`樣式。|  
|`BS_AUTOCHECKBOX`|建立核取方塊按鈕有兩個狀態︰`BST_CHECKED`和`BST_UNCHECKED`。 按一下按鈕會傳送`BN_CLICKED`主控視窗的通知，並變更按鈕的狀態。 根據預設，相關聯的文字會顯示核取方塊的右邊。 若要顯示的文字左邊的核取方塊，請使用`BS_LEFTTEXT`或`BS_RIGHTBUTTON`樣式。|  
|`BS_AUTORADIOBUTTON`|建立選項按鈕，有兩個狀態︰`BST_CHECKED`和`BST_UNCHECKED`。 選項按鈕通常用在群組中，與具有其中一個已檢查的選項，一次最多每個群組。 按一下按鈕會傳送`BN_CLICKED`主控視窗的通知設定的狀態已按下的選項按鈕以`BST_CHECKED`，並設定按鈕群組中的所有其他選項按鈕狀態`BST_UNCHECKED`。 根據預設，相關聯的文字會顯示右邊的選項按鈕。 若要顯示的文字左邊的選項按鈕，使用`BS_LEFTTEXT`或`BS_RIGHTBUTTON`樣式。|  
|`BS_CHECKBOX`|建立核取方塊按鈕有兩個狀態︰`BST_CHECKED`和`BST_UNCHECKED`。 按一下按鈕會傳送`BN_CLICKED`主控視窗的通知，但不變更按鈕的狀態。 根據預設，相關聯的文字會顯示核取方塊的右邊。 若要顯示的文字左邊的核取方塊，請使用`BS_LEFTTEXT`或`BS_RIGHTBUTTON`樣式。|  
|`BS_COMMANDLINK`|建立命令連結按鈕。 命令連結按鈕是在特定的命令按鈕[!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)]主要文字和主要的文字下方的附註的左邊顯示綠色箭號。 您可以設定附註文字使用[CButton::SetNote](../../mfc/reference/cbutton-class.md#setnote)。|  
|`BS_DEFCOMMANDLINK`|建立命令連結按鈕。 命令連結按鈕是在特定的命令按鈕[!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)]主要文字和主要的文字下方的附註的左邊顯示綠色箭號。 您可以設定附註文字使用[CButton::SetNote](../../mfc/reference/cbutton-class.md#setnote)。 如果按鈕在對話方塊中，按下 ENTER 鍵傳送`BN_CLICKED`按鈕沒有輸入的焦點時，即使 對話方塊中的通知。|  
|`BS_DEFPUSHBUTTON`|建立具有大量的黑色框線的命令按鈕。 如果按鈕在對話方塊中，按下 ENTER 鍵傳送`BN_CLICKED`按鈕沒有輸入的焦點時，即使 對話方塊中的通知。|  
|`BS_DEFSPLITBUTTON`|建立分割按鈕。 分割按鈕是在特定的命令按鈕[!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)]包含旁的下拉箭號按鈕。 當您按一下按鈕時，預設會執行命令。 當您按一下下拉箭號時，就會出現其他命令的功能表。 如果 [分割] 按鈕，在對話方塊中按下 ENTER 鍵傳送`BN_CLICKED`通知加入對話方塊中，即使沒有輸入的焦點的按鈕。|  
|`BS_GROUPBOX`|建立可以群組其他按鈕的矩形。 這個樣式相關聯的文字會顯示在矩形的左上角。|  
|`BS_OWNERDRAW`|建立主控描繪的按鈕。 這個架構會呼叫`DrawItem`時 按鈕的視覺外觀的方法已變更。 當您使用時，就必須設定此樣式`CBitmapButton`類別。|  
|`BS_PUSHBUTTON`|建立傳送命令按鈕`BN_CLICKED`主控視窗，當使用者按一下按鈕時的通知。|  
|`BS_RADIOBUTTON`|建立選項按鈕，有兩個狀態︰`BST_CHECKED`和`BST_UNCHECKED`。 選項按鈕通常用在群組中，與具有其中一個已檢查的選項，一次最多每個群組。 按一下按鈕會傳送`BN_CLICKED`主控視窗的通知，但不會自動變更群組中的任何按鍵的狀態。 根據預設，相關聯的文字會顯示右邊的選項按鈕。 若要顯示的文字左邊的選項按鈕，使用`BS_LEFTTEXT`或`BS_RIGHTBUTTON`樣式。|  
|`BS_SPLITBUTTON`|建立分割按鈕。 分割按鈕是在特定的命令按鈕[!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)]包含旁的下拉箭號按鈕。 當您按一下按鈕時，預設會執行命令。 當您按一下下拉箭號時，就會出現其他命令的功能表。|  
|`BS_USERBUTTON`|已過時，但提供的 16 位元版本的 Windows 相容性。 Win32 應用程式應該使用`BS_OWNERDRAW`改。|  
  
## <a name="radio-button-and-check-box-styles"></a>選項按鈕和核取方塊樣式  
 下表列出樣式所特有的選項按鈕和核取方塊。 這些樣式會遭到忽略其他所有的按鈕類型。 您可以選擇一或多個項目。  
  
|樣式|描述|  
|-----------|-----------------|  
|`BS_LEFTTEXT`|結合使用選項按鈕或核取方塊樣式時，文字會出現在左邊的選項按鈕或核取方塊。|  
|`BS_RIGHTBUTTON`|結合使用選項按鈕或核取方塊樣式時，文字會出現在左邊的選項按鈕或核取方塊。 這個樣式等同於`BS_LEFTTEXT`樣式。|  
|`BS_PUSHLIKE`|對於核取方塊或選項按鈕外觀和行為就像命令按鈕一樣。 [] 按鈕時，會顯示已按下狀態`BST_CHECKED`、 按下並呈現暗灰色，其狀態為時`BST_INDETERMINATE`，且其狀態為時釋放`BST_UNCHECKED`。|  
  
## <a name="text-alignment-styles"></a>文字對齊樣式  
 下表列出水平和垂直文字對齊選項。 您可以選擇下列其中一個項目。  
  
|樣式|說明|  
|-----------|-----------------|  
|`BS_LEFT`|靠左對齊按鈕的矩形中的文字。 不過，如果按鈕是核取方塊或選項按鈕，並沒有`BS_RIGHTBUTTON`樣式的文字會保留在核取方塊或選項按鈕的右邊對齊。|  
|`BS_RIGHT`|按鈕的矩形中的文字靠右對齊。 不過，如果按鈕是核取方塊或選項按鈕，並沒有`BS_RIGHTBUTTON`樣式的文字是正確的核取方塊或選項按鈕的右邊對齊。|  
|`BS_CENTER`|置中按鈕的矩形中的水平文字。|  
|`BS_TOP`|將文字放在矩形上方的按鈕。|  
|`BS_BOTTOM`|將文字放在按鈕的矩形的底部。|  
|`BS_VCENTER`|置中按鈕的矩形垂直文字。|  
  
## <a name="button-content-options"></a>按鈕的內容選項  
 下表列出的選項，以指出按鈕中顯示的內容。 僅顯示文字的按鈕類型會忽略這些樣式。 您可以選擇下列其中一個項目。  
  
|樣式|描述|  
|-----------|-----------------|  
|`BS_BITMAP`|指定按鈕顯示點陣圖。|  
|`BS_ICON`|指定按鈕會顯示圖示。|  
|`BS_TEXT`|指定按鈕會顯示文字。|  
  
## <a name="other-options"></a>其他選項  
 下表列出您可以使用任何按鈕類型的其他選項。 您可以選擇一或多個項目。  
  
|樣式|說明|  
|-----------|-----------------|  
|`BS_FLAT`|指定按鈕是二維的和不使用預設陰影，以建立&3;d 影像繪製。|  
|`BS_MULTILINE`|如果太長而無法容納於按鈕的矩形中，每一行文字字串，包裝成好幾行，則按鈕文字。|  
|`BS_NOTIFY`|可讓按鈕以傳送`BN_DBLCLK`， `BN_KILLFOCUS`，和`BN_SETFOCUS`通知訊息至其父視窗。 請注意，按鈕傳送`BN_CLICKED`無論指定此樣式的通知。|  
  
## <a name="see-also"></a>另請參閱  
 [MFC 使用的樣式](../../mfc/reference/styles-used-by-mfc.md)   
 [CButton::Create](../../mfc/reference/cbutton-class.md#create)
 [按鈕樣式](http://msdn.microsoft.com/library/windows/desktop/bb775951)   




