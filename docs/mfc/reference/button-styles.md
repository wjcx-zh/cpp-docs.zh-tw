---
title: "按鈕樣式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BS_DEFPUSHBUTTON"
  - "BS_NOTIFY"
  - "BS_MULTILINE"
  - "BS_AUTOCHECKBOX"
  - "BS_3STATE"
  - "BS_BITMAP"
  - "BS_TOP"
  - "BS_PUSHBUTTON"
  - "BS_PUSHLIKE"
  - "BS_AUTO3STATE"
  - "BS_CHECKBOX"
  - "BS_AUTORADIOBUTTON"
  - "BS_RADIOBUTTON"
  - "BS_OWNERDRAW"
  - "BS_LEFT"
  - "BS_USERBUTTON"
  - "BS_RIGHTBUTTON"
  - "BS_RIGHT"
  - "BS_LEFTTEXT"
  - "BS_TEXT"
  - "BS_BOTTOM"
  - "BS_GROUPBOX"
  - "BS_FLAT"
  - "BS_VCENTER"
  - "BS_ICON"
  - "BS_CENTER"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BS_3STATE 常數"
  - "BS_AUTO3STATE 常數"
  - "BS_AUTOCHECKBOX 常數"
  - "BS_AUTORADIOBUTTON 常數"
  - "BS_BITMAP 常數"
  - "BS_BOTTOM 常數"
  - "BS_CENTER 常數"
  - "BS_CHECKBOX 常數"
  - "BS_DEFPUSHBUTTON 常數"
  - "BS_FLAT 常數"
  - "BS_GROUPBOX 常數"
  - "BS_ICON 常數"
  - "BS_LEFT 常數"
  - "BS_LEFTTEXT 常數"
  - "BS_MULTILINE 常數"
  - "BS_NOTIFY 常數"
  - "BS_OWNERDRAW 常數"
  - "BS_PUSHBUTTON 常數"
  - "BS_PUSHLIKE 常數"
  - "BS_RADIOBUTTON 常數"
  - "BS_RIGHT 常數"
  - "BS_RIGHTBUTTON 常數"
  - "BS_TEXT 常數"
  - "BS_TOP 常數"
  - "BS_USERBUTTON 常數"
  - "BS_VCENTER 常數"
  - "按鈕物件 (CButton), 按鈕樣式"
  - "樣式, 按鈕物件"
ms.assetid: 41206f72-2b92-4250-ae32-31184046402f
caps.latest.revision: 20
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 按鈕樣式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主題說明按鈕類型和樣式。  
  
## 按鈕類型  
 下表列出按鈕類型。  您可以選擇性地選擇下列其中一項。  如果您不指定按鈕類型，則預設為  `BS_PUSHBUTTON`。  
  
|型別|說明|  
|--------|--------|  
|`BS_3STATE`|建立具有三種狀態的核取方塊按鈕：`BST_CHECKED`、`BST_INDETERMINATE` 和 `BST_UNCHECKED`。  按一下這個按鈕會傳送 `BN_CLICKED` 通知給主控視窗，但不會變更按鈕的狀態。  根據預設，相關文字會顯示在核取方塊的右邊。  若要將文字顯示到核取方塊左邊，請使用 `BS_LEFTTEXT` 或 `BS_RIGHTBUTTON` 樣式。|  
|`BS_AUTO3STATE`|建立具有三種狀態的核取方塊按鈕：`BST_CHECKED`、`BST_INDETERMINATE` 和 `BST_UNCHECKED`。  按一下這個按鈕會傳送 `BN_CLICKED` 通知給主控視窗並變更按鈕的狀態。  按鈕狀態會依照 `BST_CHECKED`、`BST_INDETERMINATE` 和 `BST_UNCHECKED` 的順序循環。  根據預設，相關文字會顯示在核取方塊的右邊。  若要將文字顯示到核取方塊左邊，請使用 `BS_LEFTTEXT` 或 `BS_RIGHTBUTTON` 樣式。|  
|`BS_AUTOCHECKBOX`|建立具有兩種狀態的核取方塊按鈕：`BST_CHECKED` 和 `BST_UNCHECKED`。  按一下這個按鈕會傳送 `BN_CLICKED` 通知給主控視窗並變更按鈕的狀態。  根據預設，相關文字會顯示在核取方塊的右邊。  若要將文字顯示到核取方塊左邊，請使用 `BS_LEFTTEXT` 或 `BS_RIGHTBUTTON` 樣式。|  
|`BS_AUTORADIOBUTTON`|建立具有兩種狀態的選項按鈕：`BST_CHECKED` 和 `BST_UNCHECKED`。  選項按鈕通常用於群組，而每個群組一次最多只能有一個選取的選項。  按一下這個按鈕會傳送 `BN_CLICKED` 通知給主控視窗，將按下的選項按鈕的狀態設定為 `BST_CHECKED`，並將按鈕群組中其他選項按鈕的狀態設定為 `BST_UNCHECKED`。  根據預設，相關文字顯示在選項按鈕的右邊。  若要將文字顯示到選項按鈕左邊，請使用 `BS_LEFTTEXT` 或 `BS_RIGHTBUTTON` 樣式。|  
|`BS_CHECKBOX`|建立具有兩種狀態的核取方塊按鈕：`BST_CHECKED` 和 `BST_UNCHECKED`。  按一下這個按鈕會傳送 `BN_CLICKED` 通知給主控視窗，但不會變更按鈕的狀態。  根據預設，相關文字會顯示在核取方塊的右邊。  若要將文字顯示到核取方塊左邊，請使用 `BS_LEFTTEXT` 或 `BS_RIGHTBUTTON` 樣式。|  
|`BS_COMMANDLINK`|建立命令連結按鈕。  命令連結按鈕是 [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] 特有的命令按鈕，會在主要文字左邊顯示一個綠色箭號，並在主要文字下方顯示附註。  您可以使用 [CButton::SetNote](../Topic/CButton::SetNote.md) 來設定附註文字。|  
|`BS_DEFCOMMANDLINK`|建立命令連結按鈕。  命令連結按鈕是 [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] 特有的命令按鈕，會在主要文字左邊顯示一個綠色箭號，並在主要文字下方顯示附註。  您可以使用 [CButton::SetNote](../Topic/CButton::SetNote.md) 來設定附註文字。  如果按鈕顯示在對話方塊中，即使按鈕沒有輸入焦點，按 ENTER 鍵會傳送 `BN_CLICKED` 通知給對話方塊。|  
|`BS_DEFPUSHBUTTON`|建立具有沉重黑色框線的命令按鈕。  如果按鈕顯示在對話方塊中，即使按鈕沒有輸入焦點，按 ENTER 鍵會傳送 `BN_CLICKED` 通知給對話方塊。|  
|`BS_DEFSPLITBUTTON`|建立分割按鈕。  分割按鈕是 [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] 特有的命令按鈕，包含下拉箭號附近的按鈕。  當您按一下按鈕時，會執行預設命令。  當您按一下下拉箭號時，其他命令功能表隨即出現。  如果分割按鈕顯示在對話方塊中，即使按鈕沒有輸入焦點，按 ENTER 鍵會傳送 `BN_CLICKED` 通知給對話方塊。|  
|`BS_GROUPBOX`|建立其他按鈕可以群組在一起的矩形。  與此樣式相關聯的文字會顯示在矩形的左上角顯示。|  
|`BS_OWNERDRAW`|建立一個主控描繪按鈕。  當按鈕的視覺外觀變更時，架構會呼叫 `DrawItem` 方法。  當您使用 `CBitmapButton` 類別時，必須設定這個樣式。|  
|`BS_PUSHBUTTON`|建立命令按鈕，當使用者按一下這個按鈕時，會傳送 `BN_CLICKED` 通知給主控視窗。|  
|`BS_RADIOBUTTON`|建立具有兩種狀態的選項按鈕：`BST_CHECKED` 和 `BST_UNCHECKED`。  選項按鈕通常用於群組，而每個群組一次最多只能有一個選取的選項。  按一下這個按鈕會傳送 `BN_CLICKED` 通知給主控視窗，但不會自動變更群組中任何按鈕的狀態。  根據預設，相關文字顯示在選項按鈕的右邊。  若要將文字顯示到選項按鈕左邊，請使用 `BS_LEFTTEXT` 或 `BS_RIGHTBUTTON` 樣式。|  
|`BS_SPLITBUTTON`|建立分割按鈕。  分割按鈕是 [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] 特有的命令按鈕，包含下拉箭號附近的按鈕。  當您按一下按鈕時，會執行預設命令。  當您按一下下拉箭號時，其他命令功能表隨即出現。|  
|`BS_USERBUTTON`|過時，但是為了與 16 位元版本的 Windows 相容而提供。  Win32 應用程式應該改用 `BS_OWNERDRAW`。|  
  
## 選項按鈕和核取方塊樣式  
 下表列出選項按鈕和核取方塊專用的樣式。  這些樣式在所有其他按鈕類型中都會被忽略。  您可以選擇性地選擇下列其中一項或多項。  
  
|樣式|說明|  
|--------|--------|  
|`BS_LEFTTEXT`|與選項按鈕或核取方塊樣式搭配時，文字會在選項按鈕或核取方塊的左邊出現。|  
|`BS_RIGHTBUTTON`|與選項按鈕或核取方塊樣式搭配時，文字會在選項按鈕或核取方塊的左邊出現。  這個樣與 `BS_LEFTTEXT` 樣式完全相同。|  
|`BS_PUSHLIKE`|讓核取方塊或選項按鈕的外觀和行為看起像命令按鈕。  當按鈕的狀態為 `BST_CHECKED` 時，會顯示為已按下的外觀；當狀態為 `BST_INDETERMINATE` 時，顯示已按下且變暗的外觀；當狀態為 `BST_UNCHECKED` 時，顯示放開的外觀。|  
  
## 文字對齊樣式  
 下表列出水平和垂直文字對齊選項。  您可以選擇性地選擇下列其中一項。  
  
|樣式|說明|  
|--------|--------|  
|`BS_LEFT`|將按鈕矩形中的文字靠左對齊。  不過，如果按鈕是沒有 `BS_RIGHTBUTTON` 樣式的核取方塊或選項按鈕時，文字會靠左對齊核取方塊或選項按鈕的右邊。|  
|`BS_RIGHT`|將按鈕矩形中的文字靠右對齊。  不過，如果按鈕是沒有 `BS_RIGHTBUTTON` 樣式的核取方塊或選項按鈕時，文字會靠右對齊核取方塊或選項按鈕的右邊。|  
|`BS_CENTER`|將按鈕矩形中的文字水平置中。|  
|`BS_TOP`|將文字放置在按鈕矩形的頂端。|  
|`BS_BOTTOM`|將文字放置在按鈕矩形的底部。|  
|`BS_VCENTER`|將按鈕矩形中的文字垂直置中。|  
  
## 按鈕內容選項  
 下表列出指示在按鈕中顯示哪些項目的選項。  只顯示文字的按鈕類型會忽略這些樣式。  您可以選擇性地選擇下列其中一項。  
  
|樣式|說明|  
|--------|--------|  
|`BS_BITMAP`|指定按鈕顯示點陣圖。|  
|`BS_ICON`|指定按鈕要顯示圖示。|  
|`BS_TEXT`|指定按鈕顯示文字。|  
  
## 其他選項  
 下表列出您可以搭配任何按鈕類型使用的其他選項。  您可以選擇性地選擇下列其中一項或多項。  
  
|樣式|說明|  
|--------|--------|  
|`BS_FLAT`|指定按鈕是二維，不使用預設陰影繪製來建立三維影像。|  
|`BS_MULTILINE`|如果文字字串太長而無法容納在矩形按鈕中，請讓按鈕文字自動換行為多行。|  
|`BS_NOTIFY`|使按鈕傳送 `BN_DBLCLK`、`BN_KILLFOCUS` 和 `BN_SETFOCUS` 通知訊息給其父視窗。  請注意，不論是否指定這個樣式，按鈕都會傳送 `BN_CLICKED` 通知。|  
  
## 請參閱  
 [MFC 使用的樣式](../../mfc/reference/styles-used-by-mfc.md)   
 [CButton::Create](../Topic/CButton::Create.md)   
 [按鈕樣式](http://msdn.microsoft.com/library/windows/desktop/bb775951)   
 [BN\_CLICKED Notification](_win32_bn_clicked_notification)