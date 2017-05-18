---
title: "CMFCTabToolTipInfo 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCTabToolTipInfo
dev_langs:
- C++
helpviewer_keywords:
- CMFCTabToolTipInfo struct
ms.assetid: 9c3b3fb9-1497-4d59-932b-0da9348dd5e2
caps.latest.revision: 27
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
ms.openlocfilehash: b9750cd9369313a3ed6ea9474d401cd0068a75fa
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctabtooltipinfo-structure"></a>CMFCTabToolTipInfo 結構
此結構會提供有關使用者停留 MDI 索引標籤的資訊。  
  
## <a name="syntax"></a>語法  
  
```  
struct CMFCTabToolTipInfo  
```  
  
## <a name="members"></a>Members  
  
### <a name="data-members"></a>資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCTabToolTipInfo::m_nTabIndex](#m_ntabindex)|指定的索引標籤控制項的索引。|  
|[CMFCTabToolTipInfo::m_pTabWnd](#m_ptabwnd)|索引標籤控制項的指標。|  
|[CMFCTabToolTipInfo::m_strText](#m_strtext)|工具提示文字。|  
  
## <a name="remarks"></a>備註  
 指標`CMFCTabToolTipInfo`結構傳遞做為參數的`AFX_WM_ON_GET_TAB_TOOLTIP`訊息。 MDI 索引標籤已啟用，而且使用者停留在索引標籤控制項時，會產生此訊息。  
  
## <a name="example"></a>範例  
 下列範例將示範如何`CMFCTabToolTipInfo`用於[MDITabsDemo 範例︰ MFC 索引標籤式 MDI 應用程式](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MDITabsDemo #&2;](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CMFCTabToolTipInfo](../../mfc/reference/cmfctabtooltipinfo-structure.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxbasetabctrl.h  
  
##  <a name="m_ntabindex"></a>CMFCTabToolTipInfo::m_nTabIndex  
 指定的索引標籤控制項的索引。  
  
```  
int m_nTabIndex;  
```  
  
### <a name="remarks"></a>備註  
 使用者停留超過此索引標籤的索引。  
  
### <a name="example"></a>範例  
 下列範例將示範如何`m_nTabIndex`用於[MDITabsDemo 範例︰ MFC 索引標籤式 MDI 應用程式](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MDITabsDemo #&2;](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]  
  
##  <a name="m_ptabwnd"></a>CMFCTabToolTipInfo::m_pTabWnd  
 索引標籤控制項的指標。  
  
```  
CMFCBaseTabCtrl* m_pTabWnd;  
```  
  
### <a name="example"></a>範例  
 下列範例將示範如何`m_pTabWnd`用於[MDITabsDemo 範例︰ MFC 索引標籤式 MDI 應用程式](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MDITabsDemo #&2;](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]  
  
##  <a name="m_strtext"></a>CMFCTabToolTipInfo::m_strText  
 工具提示文字。  
  
```  
CString m_strText;  
```  
  
### <a name="remarks"></a>備註  
 如果字串是空的不會顯示工具提示。  
  
### <a name="example"></a>範例  
 下列範例將示範如何`m_strText`用於[MDITabsDemo 範例︰ MFC 索引標籤式 MDI 應用程式](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_MDITabsDemo #&2;](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)

