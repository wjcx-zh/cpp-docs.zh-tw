---
title: 按鈕樣式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
- BS_NOTIFY constant [MFC]
- BS_RIGHTBUTTON constant [MFC]
- styles [MFC], button objects
- BS_USERBUTTON constant [MFC]
- BS_VCENTER constant [MFC]
- BS_PUSHLIKE constant [MFC]
- BS_RADIOBUTTON constant [MFC]
- BS_PUSHBUTTON constant [MFC]
- BS_DEFPUSHBUTTON constant [MFC]
- BS_LEFTTEXT constant [MFC]
- button objects (CButton), button styles
- BS_AUTO3STATE constant [MFC]
- BS_3STATE constant [MFC]
- BS_OWNERDRAW constant [MFC]
- BS_AUTORADIOBUTTON constant [MFC]
- BS_GROUPBOX constant [MFC]
- BS_BITMAP constant [MFC]
- BS_CENTER constant [MFC]
- BS_MULTILINE constant [MFC]
- BS_BOTTOM constant [MFC]
- BS_FLAT constant [MFC]
- BS_AUTOCHECKBOX constant [MFC]
- BS_RIGHT constant [MFC]
- BS_CHECKBOX constant [MFC]
- BS_LEFT constant [MFC]
- BS_ICON constant [MFC]
- BS_TOP constant [MFC]
- BS_TEXT constant
ms.assetid: 41206f72-2b92-4250-ae32-31184046402f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3ec945c95b81570e52cca03ed4e52355350d8121
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="button-styles"></a>按鈕樣式
本主題描述的按鈕類型和樣式。  
  
## <a name="button-types"></a>按鈕類型  
 下表列出的按鈕類型。 您可以選擇下列其中一項。 如果您不指定按鈕類型，預設值是`BS_PUSHBUTTON`。  
  
|類型|描述|  
|----------|-----------------|  
|`BS_3STATE`|建立具有三個狀態的核取方塊按鈕： `BST_CHECKED`， `BST_INDETERMINATE`，和`BST_UNCHECKED`。 按一下按鈕傳送`BN_CLICKED`至主控視窗的通知，但不變更按鈕的狀態。 根據預設，右邊的核取方塊會顯示相關聯的文字。 若要顯示的文字左邊的核取方塊，請使用`BS_LEFTTEXT`或`BS_RIGHTBUTTON`樣式。|  
|`BS_AUTO3STATE`|建立具有三個狀態的核取方塊按鈕： `BST_CHECKED`， `BST_INDETERMINATE`，和`BST_UNCHECKED`。 按一下按鈕傳送`BN_CLICKED`至主控視窗的通知，並變更按鈕的狀態。 按鈕狀態的順序中的循環`BST_CHECKED`， `BST_INDETERMINATE`，和`BST_UNCHECKED`。 根據預設，右邊的核取方塊會顯示相關聯的文字。 若要顯示的文字左邊的核取方塊，請使用`BS_LEFTTEXT`或`BS_RIGHTBUTTON`樣式。|  
|`BS_AUTOCHECKBOX`|建立有兩個狀態的核取方塊按鈕：`BST_CHECKED`和`BST_UNCHECKED`。 按一下按鈕傳送`BN_CLICKED`至主控視窗的通知，並變更按鈕的狀態。 根據預設，右邊的核取方塊會顯示相關聯的文字。 若要顯示的文字左邊的核取方塊，請使用`BS_LEFTTEXT`或`BS_RIGHTBUTTON`樣式。|  
|`BS_AUTORADIOBUTTON`|建立選項按鈕，有兩個狀態：`BST_CHECKED`和`BST_UNCHECKED`。 選項按鈕通常用在群組中，與每個群組具有最多一次一個選取的選項。 按一下按鈕傳送`BN_CLICKED`通知至主控視窗中，設定按下的選項按鈕的狀態`BST_CHECKED`，設定按鈕群組中的所有其他選項按鈕的狀態和`BST_UNCHECKED`。 根據預設，會顯示相關聯的文字右邊的選項按鈕。 若要顯示的文字左邊的選項按鈕，使用`BS_LEFTTEXT`或`BS_RIGHTBUTTON`樣式。|  
|`BS_CHECKBOX`|建立有兩個狀態的核取方塊按鈕：`BST_CHECKED`和`BST_UNCHECKED`。 按一下按鈕傳送`BN_CLICKED`至主控視窗的通知，但不變更按鈕的狀態。 根據預設，右邊的核取方塊會顯示相關聯的文字。 若要顯示的文字左邊的核取方塊，請使用`BS_LEFTTEXT`或`BS_RIGHTBUTTON`樣式。|  
|`BS_COMMANDLINK`|建立命令連結按鈕。 命令連結按鈕是特有的命令按鈕[!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)]會顯示綠色箭號左邊的主要文字和主要的文字下方的附註。 您可以設定附註文字使用[CButton::SetNote](../../mfc/reference/cbutton-class.md#setnote)。|  
|`BS_DEFCOMMANDLINK`|建立命令連結按鈕。 命令連結按鈕是特有的命令按鈕[!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)]會顯示綠色箭號左邊的主要文字和主要的文字下方的附註。 您可以設定附註文字使用[CButton::SetNote](../../mfc/reference/cbutton-class.md#setnote)。 如果按鈕在對話方塊中，按下 ENTER 鍵傳送`BN_CLICKED`對話方塊按鈕沒有輸入的焦點時，即使的通知。|  
|`BS_DEFPUSHBUTTON`|建立具有大量的黑色框線的命令按鈕。 如果按鈕在對話方塊中，按下 ENTER 鍵傳送`BN_CLICKED`對話方塊按鈕沒有輸入的焦點時，即使的通知。|  
|`BS_DEFSPLITBUTTON`|建立分割按鈕。 分割按鈕是特有的命令按鈕[!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)]包含旁的下拉箭號按鈕。 當您按一下按鈕時，會執行預設命令。 當您按一下下拉箭號時，就會顯示其他命令的功能表。 如果 [分割] 按鈕，在對話方塊中按下 ENTER 鍵傳送`BN_CLICKED`通知對話方塊中，即使在沒有輸入的焦點的按鈕。|  
|`BS_GROUPBOX`|建立可以群組其他按鈕的矩形。 以這個樣式相關聯的文字會顯示在矩形的左上角。|  
|`BS_OWNERDRAW`|建立主控描繪按鈕。 這個架構會呼叫`DrawItem`當按鈕的視覺外觀的方法已經變更。 當您使用時，就必須設定此樣式`CBitmapButton`類別。|  
|`BS_PUSHBUTTON`|建立傳送命令按鈕`BN_CLICKED`至主控視窗的使用者按一下按鈕時的通知。|  
|`BS_RADIOBUTTON`|建立選項按鈕，有兩個狀態：`BST_CHECKED`和`BST_UNCHECKED`。 選項按鈕通常用在群組中，與每個群組具有最多一次一個選取的選項。 按一下按鈕傳送`BN_CLICKED`至主控視窗的通知，但不會自動變更群組中的任何按鈕的狀態。 根據預設，會顯示相關聯的文字右邊的選項按鈕。 若要顯示的文字左邊的選項按鈕，使用`BS_LEFTTEXT`或`BS_RIGHTBUTTON`樣式。|  
|`BS_SPLITBUTTON`|建立分割按鈕。 分割按鈕是特有的命令按鈕[!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)]包含旁的下拉箭號按鈕。 當您按一下按鈕時，會執行預設命令。 當您按一下下拉箭號時，就會顯示其他命令的功能表。|  
|`BS_USERBUTTON`|已過時，但是提供與 Windows 的 16 位元版本的相容性。 Win32 應用程式應該使用`BS_OWNERDRAW`改為。|  
  
## <a name="radio-button-and-check-box-styles"></a>選項按鈕和核取方塊樣式  
 下表列出樣式所特有的選項按鈕和核取方塊。 這些樣式會遭到忽略所有其他的按鈕類型。 您可以選擇一或多個項目。  
  
|樣式|描述|  
|-----------|-----------------|  
|`BS_LEFTTEXT`|選項按鈕或核取方塊樣式與結合時，文字會出現在左邊的選項按鈕或核取方塊。|  
|`BS_RIGHTBUTTON`|選項按鈕或核取方塊樣式與結合時，文字會出現在左邊的選項按鈕或核取方塊。 這個樣式等同於`BS_LEFTTEXT`樣式。|  
|`BS_PUSHLIKE`|可讓選項按鈕外觀和行為像命令按鈕或核取方塊。 [] 按鈕時，會顯示已按下狀態`BST_CHECKED`、 按下並呈現暗灰色，其狀態為時`BST_INDETERMINATE`，並釋放其狀態為時`BST_UNCHECKED`。|  
  
## <a name="text-alignment-styles"></a>文字對齊樣式  
 下表列出水平和垂直文字對齊選項。 您可以選擇下列其中一項。  
  
|樣式|描述|  
|-----------|-----------------|  
|`BS_LEFT`|靠左對齊按鈕矩形中的文字。 不過，如果按鈕是核取方塊或選項按鈕，並沒有`BS_RIGHTBUTTON`樣式的文字會保留在核取方塊或選項按鈕的右邊對齊。|  
|`BS_RIGHT`|靠右對齊按鈕矩形中的文字。 不過，如果按鈕是核取方塊或選項按鈕，並沒有`BS_RIGHTBUTTON`樣式的文字是正確的核取方塊或選項按鈕的右邊對齊。|  
|`BS_CENTER`|在按鈕矩形內，水平置中文字。|  
|`BS_TOP`|將文字放在按鈕矩形的頂端。|  
|`BS_BOTTOM`|將文字放在按鈕矩形的底部。|  
|`BS_VCENTER`|置中 按鈕矩形中，垂直文字。|  
  
## <a name="button-content-options"></a>按鈕內容選項  
 下表列出的選項，以指出按鈕中顯示的內容。 只會顯示文字的按鈕類型會忽略這些樣式。 您可以選擇下列其中一項。  
  
|樣式|描述|  
|-----------|-----------------|  
|`BS_BITMAP`|指定按鈕會顯示點陣圖。|  
|`BS_ICON`|指定按鈕顯示的圖示。|  
|`BS_TEXT`|指定按鈕顯示的文字。|  
  
## <a name="other-options"></a>其他選項  
 下表列出您可以使用任何按鈕類型的其他選項。 您可以選擇一或多個項目。  
  
|樣式|描述|  
|-----------|-----------------|  
|`BS_FLAT`|指定按鈕是二維和不使用預設陰影，以建立三維的影像繪製。|  
|`BS_MULTILINE`|如果文字字串太長而無法容納在單一行中的按鈕矩形，包裝成好幾行，則按鈕文字。|  
|`BS_NOTIFY`|可讓按鈕以傳送`BN_DBLCLK`， `BN_KILLFOCUS`，和`BN_SETFOCUS`通知訊息給其父視窗。 請注意，按鈕傳送`BN_CLICKED`不論是否指定此樣式的通知。|  
  
## <a name="see-also"></a>另請參閱  
 [MFC 使用的樣式](../../mfc/reference/styles-used-by-mfc.md)   
 [CButton::Create](../../mfc/reference/cbutton-class.md#create) [按鈕樣式](http://msdn.microsoft.com/library/windows/desktop/bb775951)   



