---
title: "ToolBar 控制項樣式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ToolBar control styles
ms.assetid: 0f717eb9-fa32-4263-b852-809238863feb
caps.latest.revision: 16
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
ms.openlocfilehash: 1c50009a50c5b80e007add9de679315df6aecea9
ms.lasthandoff: 02/24/2017

---
# <a name="toolbar-control-styles"></a>ToolBar 控制項樣式
[CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)具有一組決定外觀的樣式旗標和按鈕的行為。 您可以設定這些旗標的組合，藉由呼叫[CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle)。 本主題列出樣式旗標值及其意義。  
  
## <a name="property-values"></a>屬性 Values  
 下列值可決定控制項所代表按鈕的類型：  
  
 TBBS_BUTTON  
 標準按鈕 (預設值)。  
  
 TBBS_CHECKBOX  
 核取方塊。  
  
 TBBS_CHECKGROUP  
 核取方塊群組的開頭。  
  
 TBBS_GROUP  
 按鈕群組的開頭。  
  
 TBBS_SEPARATOR  
 分隔符號。  
  
 下列值表示控制項的目前狀態：  
  
 TBBS_CHECKED  
 核取方塊已核取。  
  
 TBBS_DISABLED  
 控制項已停用。  
  
 TBBS_INDETERMINATE  
 核取方塊處於不定狀態。  
  
 TBBS_PRESSED  
 按鈕已按下。  
  
 下列值可變更工具列中按鈕的配置：  
  
 TBBS_BREAK  
 將項目放置在新的一行或一欄中，而不分隔資料行。  
  
## <a name="remarks"></a>備註  
 目前的樣式會儲存在[CMFCToolBarButton::m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle)。 中未設定為新值`m_nStyle`直接，因為某些衍生的類別可讓您執行額外處理，當您呼叫`SetStyles`。  
  
 視覺管理員會決定每個狀態下的按鈕外觀。 請參閱[視覺化管理員](../../mfc/visualization-manager.md)如需詳細資訊。  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxtoolbarbutton.h  
  
## <a name="see-also"></a>另請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)   
 [CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [視覺化管理員](../../mfc/visualization-manager.md)



