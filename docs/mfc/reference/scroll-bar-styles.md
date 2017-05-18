---
title: "捲軸樣式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SBS_VERT
- SBS_SIZEBOXBOTTOMRIGHTALIGN
- SBS_LEFTALIGN
- SBS_RIGHTALIGN
- SBS_TOPALIGN
- SBS_SIZEBOXTOPLEFTALIGN
- SBS_BOTTOMALIGN
- SBS_SIZEBOX
- SBS_HORZ
dev_langs:
- C++
helpviewer_keywords:
- SBS_HORZ constant
- SBS_TOPALIGN constant
- SBS_SIZEBOX constant
- SBS_BOTTOMALIGN constant
- SBS_VERT constant
- SBS_LEFTALIGN constant
- SBS_SIZEBOXBOTTOMRIGHTALIGN constant
- scroll bars, styles
- SBS_SIZEBOXTOPLEFTALIGN constant
- SBS_RIGHTALIGN constant
ms.assetid: 8bcde35b-387d-49ae-bdd6-7cda9f5dae26
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
ms.openlocfilehash: 778fe7b0f6f6319884df4ed9c5ccbe8e34bd8d42
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="scroll-bar-styles"></a>捲軸樣式
-   **SBS_BOTTOMALIGN**搭配**SBS_HORZ**樣式。 捲軸的下邊緣與在指定的矩形的下邊緣對齊**建立**成員函式。 捲軸列有系統捲軸的預設高度。  
  
-   **SBS_HORZ**指定水平捲軸。 如果沒有**SBS_BOTTOMALIGN**或**SBS_TOPALIGN**指定樣式、 高度、 寬度和位置中，已捲軸**建立**成員函式。  
  
-   **SBS_LEFTALIGN**搭配**SBS_VERT**樣式。 捲軸的左邊的緣與在指定的矩形的左邊緣對齊**建立**成員函式。 捲軸列有系統捲軸的預設寬度。  
  
-   **SBS_RIGHTALIGN**搭配**SBS_VERT**樣式。 捲軸的右邊緣與在指定的矩形的右邊緣對齊**建立**成員函式。 捲軸列有系統捲軸的預設寬度。  
  
-   **SBS_SIZEBOX**指定大小方塊。 如果沒有**SBS_SIZEBOXBOTTOMRIGHTALIGN**或**SBS_SIZEBOXTOPLEFTALIGN**指定樣式、 大小方塊具有高度、 寬度和位置中**建立**成員函式。  
  
-   **SBS_SIZEBOXBOTTOMRIGHTALIGN**搭配**SBS_SIZEBOX**樣式。 對齊右下角的 [大小] 方塊中指定的矩形的右下角**建立**成員函式。 [大小] 中有系統大小方塊的預設大小。  
  
-   **SBS_SIZEBOXTOPLEFTALIGN**搭配**SBS_SIZEBOX**樣式。 對齊左上角的 [大小] 方塊中指定的矩形的左上角**建立**成員函式。 [大小] 中有系統大小方塊的預設大小。  
  
-   **SBS_SIZEGRIP**相同**SBS_SIZEBOX**，但凸起邊緣。  
  
-   **SBS_TOPALIGN**搭配**SBS_HORZ**樣式。 捲軸的上邊緣與在指定的矩形的頂端對齊**建立**成員函式。 捲軸列有系統捲軸的預設高度。  
  
-   **SBS_VERT**指定垂直捲軸。 如果沒有**SBS_RIGHTALIGN**或**SBS_LEFTALIGN**指定樣式、 高度、 寬度和位置中，已捲軸**建立**成員函式。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 使用的樣式](../../mfc/reference/styles-used-by-mfc.md)   
 [CScrollBar::Create](../../mfc/reference/cscrollbar-class.md#create)   
 [捲軸控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb787533)


