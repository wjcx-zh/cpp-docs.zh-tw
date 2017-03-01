---
title: "編輯樣式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ES_READONLY
- ES_WANTRETURN
- ES_UPPERCASE
- ES_NUMBER
- ES_AUTOHSCROLL
- ES_LOWERCASE
- ES_RIGHT
- ES_MULTILINE
- ES_PASSWORD
- ES_NOHIDESEL
- ES_OEMCONVERT
- ES_LEFT
- ES_CENTER
dev_langs:
- C++
helpviewer_keywords:
- ES_WANTRETURN constant
- edit styles [MFC]
- ES_RIGHT constant
- ES_READONLY constant
- ES_PASSWORD constant
- ES_MULTILINE constant
- ES_LEFT constant
- ES_AUTOVSCROLL constant
- ES_OEMCONVERT constant
- ES_LOWERCASE constant
- ES_NUMBER constant
- ES_UPPERCASE constant
- ES_NOHIDESEL constant
- ES_AUTOHSCROLL constant
- ES_CENTER constant
ms.assetid: e6291dd6-f2cb-4ce2-ac31-32272526625c
caps.latest.revision: 12
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
ms.openlocfilehash: 275e0d2dede038bdbe9061bc8051408442aa70bf
ms.lasthandoff: 02/24/2017

---
# <a name="edit-styles"></a>編輯樣式
-   **ES_AUTOHSCROLL**自動捲動 10 個字元右邊的文字，當使用者輸入的行結尾字元。 當使用者按下 ENTER 鍵時，控制項捲動至位置 0 的所有文字。  
  
-   **ES_AUTOVSCROLL**自動捲動文字向上移動一個頁面，當使用者按下 ENTER 的最後一行。  
  
-   **ES_CENTER**中心在單行或多行編輯控制項。  
  
-   **ES_LEFT**靠左對齊的文字，在單行或多行編輯控制項。  
  
-   **ES_LOWERCASE**將轉換成小寫輸入到編輯控制項的所有字元。  
  
-   **ES_MULTILINE**指定多行編輯控制項。 （預設值是單一線條）。如果**ES_AUTOVSCROLL**指定樣式中，編輯控制項盡可能顯示的行數，並以垂直方式捲動當使用者按下 ENTER 鍵。 如果**ES_AUTOVSCROLL**是沒有指定，編輯控制項會顯示的行數與嗶聲，如果可以顯示沒有更多行時，按下 ENTER。 如果**ES_AUTOHSCROLL**指定樣式、 多行編輯控制項自動水平捲動插入號通過控制項右緣。 若要啟動新的一行，使用者必須按 ENTER。 如果**ES_AUTOHSCROLL**是沒有指定，控制項自動換行文字時所需的下一行的開頭，按下 ENTER 時也啟動新的一行。 自動換行的位置取決於視窗大小。 如果視窗大小變更，則會重新顯示自動換行位置變更和文字。 多行編輯控制項可有捲軸。 含捲軸的編輯控制處理自己的捲軸訊息。 編輯不使用捲軸捲軸上面所述的控制項和處理任何捲動訊息傳送的父視窗。  
  
-   **ES_NOHIDESEL**編輯控制項通常隱藏選取範圍，當控制項失去輸入的焦點，並反轉選取範圍，當控制項收到輸入的焦點時。 指定**ES_NOHIDESEL**刪除此預設動作。  
  
-   **ES_NUMBER**允許編輯控制項中輸入的數字。  
  
-   **ES_OEMCONVERT**編輯控制項中輸入的文字會從 ANSI 字元集轉換為 OEM 字集，然後回到 ANSI。 這可確保適當的字元轉換時，應用程式會呼叫`AnsiToOem`Windows 函式可將編輯控制項中的 ANSI 字串轉換為 OEM 字元。 這個樣式是最適合用來編輯控制項包含檔名。  
  
-   **ES_PASSWORD**會顯示為星號的所有字元 (**\***) 輸入到編輯控制項。 應用程式可以使用`SetPasswordChar`成員函式來變更顯示的字元。  
  
-   **ES_READONLY**可防止使用者輸入或編輯編輯控制項中的文字。  
  
-   **ES_RIGHT**靠右對齊的文字，在單行或多行編輯控制項。  
  
-   **ES_UPPERCASE**將轉換成大寫輸入到編輯控制項的所有字元。  
  
-   **ES_WANTRETURN**指定當使用者按下 ENTER 鍵，同時將多行編輯控制項在對話方塊中輸入文字時插入歸位字元。 若沒有這個樣式中，按下 ENTER 鍵已按下對話方塊方塊的預設按鈕相同的效果。 此樣式影響不在單一行編輯控制項。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 使用的樣式](../../mfc/reference/styles-used-by-mfc.md)   
 [CEdit::Create](../../mfc/reference/cedit-class.md#create)   
 [編輯控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb775464)


