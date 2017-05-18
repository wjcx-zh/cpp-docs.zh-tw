---
title: "靜態樣式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SS_SUNKEN
- SS_CENTER
- SS_ENHMETAFILE
- SS_RIGHT
- SS_BLACKRECT
- SS_LEFTNOWORDWRAP
- SS_GRAYFRAME
- SS_USERITEM
- SS_GRAYRECT
- SS_WHITEFRAME
- SS_ETCHEDFRAME
- SS_ETCHEDVERT
- SS_WHITERECT
- SS_PATHELLIPSIS
- SS_WORDELLIPSIS
- SS_NOPREFIX
- SS_BITMAP
- SS_SIMPLE
- SS_CENTERIMAGE
- SS_BLACKFRAME
- SS_OWNERDRAW
- SS_REALSIZEIMAGE
- SS_RIGHTJUST
- SS_ICON
- SS_NOTIFY
- SS_ETCHEDHORZ
- SS_LEFT
- SS_ENDELLIPSIS
dev_langs:
- C++
helpviewer_keywords:
- SS_ICON constant
- SS_WHITEFRAME constant
- SS_BLACKFRAME constant
- SS_ETCHEDHORZ constant
- SS_OWNERDRAW constant
- SS_BITMAP constant
- SS_NOPREFIX constant
- SS_NOTIFY constant
- SS_CENTER constant
- SS_REALSIZEIMAGE constant
- SS_ETCHEDFRAME constant
- SS_CENTERIMAGE constant
- SS_SUNKEN constant
- SS_ENDELLIPSIS constant
- SS_WORDELLIPSIS constant
- SS_WHITERECT constant
- SS_ETCHEDVERT constant
- SS_GRAYFRAME constant
- SS_LEFTNOWORDWRAP constant
- SS_LEFT constant
- SS_SIMPLE constant
- static styles
- SS_ENHMETAFILE constant
- SS_GRAYRECT constant
- SS_USERITEM constant
- SS_PATHELLIPSIS constant
- SS_BLACKRECT constant
- SS_RIGHT constant
- SS_RIGHTJUST constant
ms.assetid: a1114548-fc6d-491d-8c46-21d11b8574f5
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: ad34c688fdfd3c2b4c81a0a03fbce53a905162ad
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="static-styles"></a>靜態樣式
-   **SS_BITMAP**指定點陣圖會以靜態控制項中顯示。 指定的文字是點陣圖 （不是檔名） 的資源檔中其他位置定義的名稱。 樣式會忽略 nWidth 和 nHeight 參數;控制項自動調整大小以容納點陣圖。  
  
-   **SS_BLACKFRAME**有使用相同的視窗框架色彩繪製框架指定方塊。 預設為黑色。  
  
-   **SS_BLACKRECT**指定用來繪製視窗框架的色彩填滿的矩形。 預設為黑色。  
  
-   **SS_CENTER**指定一個簡單的矩形，並顯示指定的矩形中置中對齊的文字。 文字格式顯示之前。 自動包裝會延伸超過一行結尾的文字置中的下一行的開頭。  
  
-   **SS_CENTERIMAGE**指定，是否點陣圖或圖示小於靜態控制項的工作區，其餘的工作區的填滿的左上角的圖示的點陣圖中像素色彩。 如果靜態控制項包含一行文字，文字是垂直置中控制項的工作區中。  
  
-   **SS_ENDELLIPSIS**或**SS_PATHELLIPSIS**取代一部分指定字串的省略符號，如有必要，以便將指定的矩形中。  
  
     您可以指定**SS_END_ELLIPSIS**取代字串結尾處的字元或**SS_PATHELLIPSIS**取代字串中間的字元。 如果字串包含反斜線 (\\) 個字元， **SS_PATHELLIPSIS**會保留最多的文字反斜線越好。  
  
-   **SS_ENHMETAFILE**指定要顯示在靜態控制項的增強型中繼檔。 指定的文字是中繼檔的名稱。 增強型中繼檔靜態控制項有固定的大小。中繼檔會調整為適合靜態控制項工作區。  
  
-   **SS_ETCHEDFRAME**繪製靜態控制項使用的框架**EDGE_ETCHED**邊緣樣式。  
  
-   **SS_ETCHEDHORZ**繪製框線和下邊緣使用靜態控制項**EDGE_ETCHED**邊緣樣式。  
  
-   **SS_ETCHEDVERT**繪製使用 EDGE_ETCHED 邊緣樣式靜態控制項的左、 右邊緣。  
  
-   **SS_GRAYFRAME**有相同的色彩做為螢幕背景 （桌面），以繪製框架指定方塊。 預設為灰色。  
  
-   **SS_GRAYRECT**指定用來填滿螢幕背景的色彩填滿的矩形。 預設為灰色。  
  
-   **SS_ICON**指定在對話方塊中所顯示的圖示。 指定的文字是圖示 （不是檔名） 的資源檔中其他位置定義的名稱。 `nWidth`和`nHeight`參數都會被忽略，圖示會自動調整大小。  
  
-   **SS_LEFT**指定一個簡單的矩形，並顯示指定的文字的矩形中排清左。 文字格式顯示之前。 會擴充超過一行結尾的文字自動包裝至下一步排清左一行的開頭。  
  
-   **SS_LEFTNOWORDWRAP**指定一個簡單的矩形，並顯示指定的文字的矩形中排清左。 索引標籤會展開，但不是會包含文字。 會裁剪超出行結尾的文字。  
  
-   **SS_NOPREFIX**除非指定此樣式時，Windows 會解譯對應前置詞字元控制項的文字中的任何連字號 （&） 字元。 在此情況下，會移除連字號，然後在字串中的下一個字元會加上底線。 如果靜態控制項是以包含文字，不需要這項功能， **SS_NOPREFIX**可能會增加。 這個靜態控制項樣式可能包含與任何已定義的靜態控制項。 您可以結合**SS_NOPREFIX**具有其他樣式使用位元 OR 運算子。 這是最常時使用其他字串可能包含連字號或檔名必須可在對話方塊中的靜態控制項中顯示。  
  
-   **SS_NOTIFY**傳送父視窗**STN_CLICKED**， **STN_DBLCLK**， **STN_DISABLE**，和**STN_ENABLE**通知訊息，當使用者按一下或按兩下控制項時。  
  
-   **SS_OWNERDRAW**指定靜態控制項的擁有者會負責繪製控制項。 擁有者視窗會收到`WM_DRAWITEM`訊息時需要繪製的控制項。  
  
-   **SS_REALSIZEIMAGE**防止靜態圖示或點陣圖的控制項 (也就是靜態控制項有**SS_ICON**或**SS_BITMAP**樣式) 無法載入或繪製調整。 如果圖示或點陣圖大於目的區域，則會裁剪影像。  
  
-   **SS_RIGHT**指定一個簡單的矩形，並顯示指定的文字的矩形中排清權限。 文字格式顯示之前。 會擴充超過一行結尾的文字自動包裝至下一步排清右邊一行的開頭。  
  
-   **SS_RIGHTJUST**指定靜態控制項的右下角**SS_BITMAP**或**SS_ICON**樣式會保持固定時的控制項調整大小。 只有上方和左方側邊會調整以配合新點陣圖或圖示。  
  
-   **SS_SIMPLE**指定一個簡單的矩形，並顯示一行文字的矩形中排清左。 無法縮短的一行文字，或以任何方式改變。 (必須處理控制項的父視窗或對話方塊方塊`WM_CTLCOLOR`訊息。)  
  
-   **SS_SUNKEN**繪製半凹陷框線靜態控制項。  
  
-   **SS_USERITEM**指定使用者定義的項目。  
  
-   **SS_WHITEFRAME**有使用相同的視窗背景色彩繪製框架指定方塊。 預設為白色。  
  
-   **SS_WHITERECT**指定用來填滿視窗背景的色彩填滿的矩形。 預設為白色。  
  
-   **SS_WORDELLIPSIS**截斷，不符合，並加入省略符號的文字。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 使用的樣式](../../mfc/reference/styles-used-by-mfc.md)   
 [CStatic::Create](../../mfc/reference/cstatic-class.md#create)   
 [DrawEdge](http://msdn.microsoft.com/library/windows/desktop/dd162477)   
 [靜態控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760773)


