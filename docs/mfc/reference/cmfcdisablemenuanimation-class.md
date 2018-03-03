---
title: "CMFCDisableMenuAnimation 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation::Restore
dev_langs:
- C++
helpviewer_keywords:
- CMFCDisableMenuAnimation [MFC], Restore
ms.assetid: c6eb07da-c382-43d6-8028-007f2320e50e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 458a35e708db41ee393da70aedd653aca44cf802
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcdisablemenuanimation-class"></a>CMFCDisableMenuAnimation 類別
停用快顯功能表的動畫。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCDisableMenuAnimation  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|||  
|-|-|  
|名稱|描述|  
|`CMFCDisableMenuAnimation::CMFCDisableMenuAnimation`|建構 `CMFCDisableMenuAnimation` 物件。|  
|`CMFCDisableMenuAnimation::~CMFCDisableMenuAnimation`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|||  
|-|-|  
|名稱|描述|  
|[CMFCDisableMenuAnimation::Restore](#restore)|還原前一個架構用來顯示快顯功能表的動畫。|  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|名稱|描述|  
|`CMFCDisableMenuAnimation::m_animType`|會儲存先前的快顯功能表動畫類型。|  
  
### <a name="remarks"></a>備註  
 若要暫時停用快顯功能表動畫，（例如，當您處理滑鼠或鍵盤命令） 使用此協助程式類別。  
  
 A`CMFCDisableMenuAnimation`物件停用快顯功能表動畫，在其存留期間。 建構函式會儲存在目前的快顯功能表動畫類型`m_animType`欄位和目前的動畫類型的集合`CMFCPopupMenu::NO_ANIMATION`。 解構函式會還原為先前的動畫類型。  
  
 您可以建立`CMFCDisableMenuAnimation`停用快顯功能表動畫，整個單一函式堆疊上的物件。 如果您想要停用快顯功能表動畫，函式之間，建立`CMFCDisableMenuAnimation`物件在堆積上，然後再刪除它，當您想要還原的快顯功能表動畫。  
  
## <a name="example"></a>範例  
 下列範例會示範如何使用堆疊來暫時停用功能表動畫。  
  
 [!code-cpp[NVC_MFC_Misc#1](../../mfc/reference/codesnippet/cpp/cmfcdisablemenuanimation-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CMFCDisableMenuAnimation](../../mfc/reference/cmfcdisablemenuanimation-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxpopupmenu.h  
  
##  <a name="restore"></a>CMFCDisableMenuAnimation::Restore  
 還原前一個架構用來顯示快顯功能表的動畫。  
  
```  
void Restore ();
```  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫`CMFCDisableMenuAnimation`還原架構用來顯示快顯功能表的前一個動畫的解構函式。  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCPopupMenu 類別](../../mfc/reference/cmfcpopupmenu-class.md)
