---
title: "下拉式方塊樣式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CBS_LOWERCASE
- CBS_SORT
- CBS_OWNERDRAWVARIABLE
- CBS_OEMCONVERT
- CBS_AUTOHSCROLL
- CBS_NOINTEGRALHEIGHT
- CBS_SIMPLE
- CBS_DROPDOWNLIST
- CBS_DROPDOWN
- CBS_UPPERCASE
- CBS_HASSTRINGS
- CBS_DISABLENOSCROLL
- CBS_OWNERDRAWFIXED
dev_langs:
- C++
helpviewer_keywords:
- CBS_OWNERDRAWVARIABLE constant [MFC]
- CBS_NOINTEGRALHEIGHT constant [MFC]
- CBS_SIMPLE constant [MFC]
- CBS_AUTOHSCROLL constant [MFC]
- CBS_OEMCONVERT constant [MFC]
- CBS_DISABLENOSCROLL constant [MFC]
- CBS_HASSTRINGS constant [MFC]
- CBS_LOWERCASE constant [MFC]
- CBS_SORT constant [MFC]
- CBS_DROPDOWN constant [MFC]
- CBS_OWNERDRAWFIXED constant [MFC]
- combo boxes [MFC], styles
- CBS_UPPERCASE constant [MFC]
- CBS_DROPDOWNLIST constant
ms.assetid: d21a5023-e6a2-495b-a6bd-010a515cbc63
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 028a58c443ba45a4b8167a17f73f6f3fa54e4ca7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="combo-box-styles"></a>下拉式方塊樣式
MFC 中提供下列下拉式方塊樣式。  
  
-   **CBS_AUTOHSCROLL** ：當使用者在行尾處輸入字元時，自動將編輯控制項中的文字往右捲動。 如果未設定此樣式，則只會允許符合矩形界限的文字。  
  
-   **CBS_DISABLENOSCROLL** ：在清單方塊中未包含足夠的項目可以捲動時，清單方塊會顯示已停用的垂直捲軸。 若沒有這個樣式，在清單方塊中未包含足夠的項目時，捲軸會隱藏。  
  
-   **CBS_DROPDOWN** ：類似於 **CBS_SIMPLE**，不過除非使用者選取編輯控制項旁的圖示，否則不會顯示清單方塊。  
  
-   **CBS_DROPDOWNLIST** ：類似於 **CBS_DROPDOWN**，不過編輯控制項會由顯示清單方塊中目前選取範圍的靜態文字項目取代。  
  
-   **CBS_HASSTRINGS** ：主控描繪下拉式方塊包含由字串組成的項目。 下拉式方塊會維護記憶體和字串的指標，讓應用程式可以使用 `GetText` 成員函式來擷取特定項目的文字。  
  
-   **CBS_LOWERCASE** ：將選取欄位和清單中的所有文字轉換成小寫。  
  
-   **CBS_NOINTEGRALHEIGHT** ：將下拉式方塊的大小，指定為應用程式建立下拉式方塊時所指定的相同大小。 一般而言，Windows 會調整下拉式方塊的大小，使下拉式方塊不會只顯示一部分的項目。  
  
-   **CBS_OEMCONVERT** ：在下拉式方塊編輯控制項中輸入的文字，會從 ANSI 字元集轉換成 OEM 字集，然後再轉換回 ANSI。 如此可確保當應用程式呼叫 `AnsiToOem` Windows 函式將下拉式方塊中的 ANSI 字串轉換成 OEM 字元時，會進行適當的字元轉換。 此樣式是最適合用於包含檔案名稱的下拉式方塊，而且只適用於使用 **CBS_SIMPLE** 或 **CBS_DROPDOWN** 樣式建立的下拉式方塊。  
  
-   **CBS_OWNERDRAWFIXED** ：清單方塊的擁有者會負責繪製其內容；清單方塊內的所有項目具有相同的高度。  
  
-   **CBS_OWNERDRAWVARIABLE** ：清單方塊的擁有者會負責繪製其內容；清單方塊內項目的高度是可變的。  
  
-   **CBS_SIMPLE** ：永遠顯示清單方塊。 編輯控制項會顯示清單方塊中目前的選取範圍。  
  
-   **CBS_SORT** ：自動排序輸入至清單方塊中的字串。  
  
-   **CBS_UPPERCASE** ：將選取欄位和清單中的所有文字轉換成大寫。  
  
## <a name="see-also"></a>請參閱  
 [MFC 使用的樣式](../../mfc/reference/styles-used-by-mfc.md)   
 [CComboBox::Create](ccombobox class.md # ccombobox__create   



