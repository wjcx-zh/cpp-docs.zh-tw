---
title: "CMFCDisableMenuAnimation 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDisableMenuAnimation
dev_langs:
- C++
helpviewer_keywords:
- CMFCDisableMenuAnimation class
ms.assetid: c6eb07da-c382-43d6-8028-007f2320e50e
caps.latest.revision: 22
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
ms.openlocfilehash: ea0be944ca70d6f8317fd4bc60fdd50ecc714438
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcdisablemenuanimation-class"></a>CMFCDisableMenuAnimation 類別
停用快顯功能表的動畫。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCDisableMenuAnimation  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|||  
|-|-|  
|名稱|描述|  
|`CMFCDisableMenuAnimation::CMFCDisableMenuAnimation`|建構 `CMFCDisableMenuAnimation` 物件。|  
|`CMFCDisableMenuAnimation::~CMFCDisableMenuAnimation`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|||  
|-|-|  
|名稱|說明|  
|[CMFCDisableMenuAnimation::Restore](#restore)|還原前一個動畫架構用來顯示快顯功能表。|  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|名稱|描述|  
|`CMFCDisableMenuAnimation::m_animType`|儲存前一個快顯功能表的動畫類型。|  
  
### <a name="remarks"></a>備註  
 若要暫時停用快顯功能表動畫，（例如，當您處理滑鼠或鍵盤命令） 使用此協助程式類別。  
  
 A`CMFCDisableMenuAnimation`物件停用在其存留期間的快顯功能表動畫。 建構函式會儲存在目前的快顯功能表動畫類型`m_animType`欄位和目前的動畫類型的集合`CMFCPopupMenu::NO_ANIMATION`。 解構函式會還原先前的動畫類型。  
  
 您可以建立`CMFCDisableMenuAnimation`停用快顯功能表動畫，整個單一函式堆疊上的物件。 如果您想要停用快顯功能表動畫函式之間，建立`CMFCDisableMenuAnimation`物件在堆積上，然後再刪除它，當您想要還原的快顯功能表的動畫。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用堆疊暫時停用功能表動畫。  
  
 [!code-cpp[NVC_MFC_Misc #&1;](../../mfc/reference/codesnippet/cpp/cmfcdisablemenuanimation-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CMFCDisableMenuAnimation](../../mfc/reference/cmfcdisablemenuanimation-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxpopupmenu.h  
  
##  <a name="a-namerestorea--cmfcdisablemenuanimationrestore"></a><a name="restore"></a>CMFCDisableMenuAnimation::Restore  
 還原前一個動畫架構用來顯示快顯功能表。  
  
```  
void Restore ();
```  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫`CMFCDisableMenuAnimation`解構函式來還原前一個動畫架構用來顯示快顯功能表。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCPopupMenu 類別](../../mfc/reference/cmfcpopupmenu-class.md)

