---
title: "CMFCToolBarInfo 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarInfo
- AFXTOOLBAR/CMFCToolBarInfo
- AFXTOOLBAR/CMFCToolBarInfo::m_uiColdResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiHotResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeColdResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeHotResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiMenuDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiMenuResID
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarInfo [MFC], m_uiColdResID
- CMFCToolBarInfo [MFC], m_uiDisabledResID
- CMFCToolBarInfo [MFC], m_uiHotResID
- CMFCToolBarInfo [MFC], m_uiLargeColdResID
- CMFCToolBarInfo [MFC], m_uiLargeDisabledResID
- CMFCToolBarInfo [MFC], m_uiLargeHotResID
- CMFCToolBarInfo [MFC], m_uiMenuDisabledResID
- CMFCToolBarInfo [MFC], m_uiMenuResID
ms.assetid: 6dc84482-eaaa-491f-aa5d-dd7a57886b46
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c47be3ddb2302124b233c39aaf8bd829cd481d79
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cmfctoolbarinfo-class"></a>CMFCToolBarInfo 類別
包含在各種狀態下工具列影像的資源 ID。 `CMFCToolBarInfo`是 helper 類別，做為參數的[CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex)方法。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCToolBarInfo  
```  
  
## <a name="members"></a>成員  
  
### <a name="data-members"></a>資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCToolBarInfo::m_uiColdResID](#m_uicoldresid)|包含規則 （非作用） 中工具列影像的工具列點陣圖的資源識別碼。|  
|[CMFCToolBarInfo::m_uiDisabledResID](#m_uidisabledresid)|包含已停用的工具列影像的工具列點陣圖的資源識別碼。|  
|[CMFCToolBarInfo::m_uiHotResID](#m_uihotresid)|包含選取 （熱） 工具列影像的工具列點陣圖的資源識別碼。|  
|[CMFCToolBarInfo::m_uiLargeColdResID](#m_uilargecoldresid)|包含大型的一般工具列影像的工具列點陣圖的資源識別碼。|  
|[CMFCToolBarInfo::m_uiLargeDisabledResID](#m_uilargedisabledresid)|包含大型，工具列點陣圖的資源識別碼停用工具列影像。|  
|[CMFCToolBarInfo::m_uiLargeHotResID](#m_uilargehotresid)|包含大型、 選取工具列影像的工具列點陣圖的資源識別碼。|  
|[CMFCToolBarInfo::m_uiMenuDisabledResID](#m_uimenudisabledresid)|包含已停用的功能表影像的工具列點陣圖的資源識別碼。|  
|[CMFCToolBarInfo::m_uiMenuResID](#m_uimenuresid)|包含功能表影像的工具列點陣圖的資源識別碼。|  
  
## <a name="remarks"></a>備註  
 完整的工具列點陣圖所組成的固定大小的小型工具列影像 （按鈕）。 儲存在每個資源識別碼`CMFCToolBarInfo`物件是點陣圖，其中包含一組完整的工具列中的單一狀態 （範例中，選取、 停用，大或功能表影像） 的映像。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CMFCToolBarInfo](../../mfc/reference/cmfctoolbarinfo-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxtoolbar.h  
  
##  <a name="m_uicoldresid"></a>CMFCToolBarInfo::m_uiColdResID  
 指定工具列的所有一般按鈕影像的資源識別碼。  
  
```  
UINT m_uiColdResID;  
```  
  
##  <a name="m_uidisabledresid"></a>CMFCToolBarInfo::m_uiDisabledResID  
 指定工具列的按鈕無法使用的影像資源識別碼。  
  
```  
UINT m_uiDisabledResID;  
```  
  
##  <a name="m_uihotresid"></a>CMFCToolBarInfo::m_uiHotResID  
 指定工具列的所有反白顯示的按鈕影像的資源識別碼。  
  
```  
UINT m_uiHotResID  
```  
  
##  <a name="m_uilargecoldresid"></a>CMFCToolBarInfo::m_uiLargeColdResID  
 指定工具列的所有規則的大型按鈕影像的資源識別碼。  
  
```  
UINT m_uiLargeColdResID  
```  
  
##  <a name="m_uilargedisabledresid"></a>CMFCToolBarInfo::m_uiLargeDisabledResID  
 指定工具列的所有大型已停用的按鈕影像的資源識別碼。  
  
```  
UINT m_uiLargeDisabledResID;  
```  
  
##  <a name="m_uilargehotresid"></a>CMFCToolBarInfo::m_uiLargeHotResID  
 指定工具列的所有大型反白顯示影像的資源識別碼。  
  
```  
UINT m_uiLargeHotResID;  
```  
  
##  <a name="m_uimenudisabledresid"></a>CMFCToolBarInfo::m_uiMenuDisabledResID  
 指定工具列的命令無法使用的影像資源識別碼。  
  
```  
UINT m_uiMenuDisabledResID;  
```  
  
##  <a name="m_uimenuresid"></a>CMFCToolBarInfo::m_uiMenuResID  
 指定工具列的所有標準功能表項目影像的資源識別碼。  
  
```  
UINT m_uiMenuResID;  
```  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)
