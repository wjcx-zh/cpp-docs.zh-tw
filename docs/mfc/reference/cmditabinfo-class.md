---
title: "CMDITabInfo 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMDITabInfo
- AFXMDICLIENTAREAWND/CMDITabInfo
- AFXMDICLIENTAREAWND/CMDITabInfo::Serialize
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bAutoColor
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bDocumentMenu
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bEnableTabSwap
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bFlatFrame
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabCloseButton
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabCustomTooltips
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabIcons
- AFXMDICLIENTAREAWND/CMDITabInfo::m_nTabBorderSize
- AFXMDICLIENTAREAWND/CMDITabInfo::m_style
- AFXMDICLIENTAREAWND/CMDITabInfo::m_tabLocation
dev_langs:
- C++
helpviewer_keywords:
- CMDITabInfo class
- CMDITabInfo class, constructor
ms.assetid: 988ae1b7-4f7f-4239-b88f-7e28b3291c5e
caps.latest.revision: 37
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
ms.openlocfilehash: a45532c98d5da7d89d27e3d29d9b40075cf0376f
ms.lasthandoff: 02/24/2017

---
# <a name="cmditabinfo-class"></a>CMDITabInfo 類別
`CMDITabInfo`類別用來將參數傳遞至[CMDIFrameWndEx::EnableMDITabbedGroups](../../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups)方法。 設定這個類別的成員以控制 MDI 索引標籤式群組的行為。  
  
## <a name="syntax"></a>語法  
  
```  
class CMDITabInfo   
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|`CMDITabInfo::CMDITabInfo`|預設建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMDITabInfo::Serialize](#serialize)|從封存中讀取或寫入此物件。|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CMDITabInfo::m_bActiveTabCloseButton;](#m_bactivetabclosebutton_)|指定是否**關閉**按鈕顯示在作用中 索引標籤的標籤。|  
|[CMDITabInfo::m_bAutoColor](#m_bautocolor)|指定是否要 MDI 索引標籤的色彩。|  
|[CMDITabInfo::m_bDocumentMenu](#m_bdocumentmenu)|指定的索引標籤群組是否顯示快顯功能表會顯示開啟文件的清單，或顯示捲軸按鈕。|  
|[CMDITabInfo::m_bEnableTabSwap](#m_benabletabswap)|指定使用者是否可以拖曳來交換的索引標籤的位置。|  
|[CMDITabInfo::m_bFlatFrame](#m_bflatframe)|指定的索引標籤是否具有平面的框架。|  
|[CMDITabInfo::m_bTabCloseButton](#m_btabclosebutton)|指定是否要顯示每個索引標籤的標籤**關閉** 按鈕。|  
|[CMDITabInfo::m_bTabCustomTooltips](#m_btabcustomtooltips)|指定是否啟用自訂的工具提示。|  
|[CMDITabInfo::m_bTabIcons](#m_btabicons)|指定是否要在 MDI 索引標籤上顯示圖示。|  
|[CMDITabInfo::m_nTabBorderSize](#m_ntabbordersize)|指定每個索引標籤視窗的框線的大小。|  
|[CMDITabInfo::m_style](#m_style)|指定索引標籤的標籤的樣式。|  
|[CMDITabInfo::m_tabLocation](#m_tablocation)|指定是否位於頂端或底部的頁面 索引標籤的標籤。|  
  
## <a name="remarks"></a>備註  
 這個類別指定的參數，此架構會建立 MDI 索引標籤群組。  
  
## <a name="example"></a>範例  
 下列範例示範如何設定各種成員變數中的值`CMDITabInfo`類別。  
  
 [!code-cpp[NVC_MFC_MDITab #&1;](../../mfc/reference/codesnippet/cpp/cmditabinfo-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CMDITabInfo](../../mfc/reference/cmditabinfo-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxmdiclientareawnd.h  
  
##  <a name="m_bactivetabclosebutton_"></a>CMDITabInfo::m_bActiveTabCloseButton;  
 指定是否**關閉**按鈕顯示在作用中 索引標籤的標籤。  
  
```  
BOOL m_bActiveTabCloseButton;  
```  
  
### <a name="remarks"></a>備註  
 如果`TRUE`，作用中 索引標籤的標籤會顯示**關閉** 按鈕。 **關閉**按鈕將會從右上角的 索引標籤區域中移除。 否則，不會顯示作用中 索引標籤的標籤**關閉** 按鈕。 **關閉**按鈕將會出現在索引標籤區域右上角。  
  
##  <a name="m_bautocolor"></a>CMDITabInfo::m_bAutoColor  
 指定每個 MDI 索引標籤是否有它自己的色彩。  
  
```  
BOOL m_bAutoColor;  
```  
  
### <a name="remarks"></a>備註  
 如果`TRUE`，每個索引標籤會有它自己的色彩。 MFC 程式庫所管理的色彩。 否則，會顯示索引標籤，以白色。 預設值是 `FALSE`。  
  
##  <a name="m_bdocumentmenu"></a>CMDITabInfo::m_bDocumentMenu  
 指定是否每個索引標籤會顯示快顯功能表會顯示在右邊緣的索引標籤區域開啟文件的清單。  
  
```  
BOOL m_bDocumentMenu;  
```  
  
### <a name="remarks"></a>備註  
 如果`TRUE`，每個索引標籤上的 windows 會顯示快顯功能表會顯示在右邊緣的索引標籤區域中，開啟文件的清單否則，索引標籤視窗會顯示捲軸按鈕索引標籤區域右邊緣。 預設值是 `FALSE`。  
  
##  <a name="m_benabletabswap"></a>CMDITabInfo::m_bEnableTabSwap  
 指定使用者是否可以拖曳來交換的索引標籤的位置。  
  
```  
BOOL m_bEnableTabSwap;  
```  
  
### <a name="remarks"></a>備註  
 如果`TRUE`，使用者可以藉由拖曳索引標籤變更索引標籤的位置。 否則，使用者無法變更索引標籤的位置。 預設值是 `TRUE`。  
  
##  <a name="m_bflatframe"></a>CMDITabInfo::m_bFlatFrame  
 指定每個索引標籤視窗是否有一般的框架。  
  
```  
BOOL m_bFlatFrame;  
```  
  
##  <a name="m_btabclosebutton"></a>CMDITabInfo::m_bTabCloseButton  
 指定是否要顯示每個索引標籤視窗**關閉** 按鈕。  
  
```  
BOOL m_bTabCloseButton;  
```  
  
### <a name="remarks"></a>備註  
 如果`TRUE`，每個索引標籤 視窗會顯示**關閉**右邊緣的索引標籤上的按鈕。 否則，**關閉**按鈕不會顯示。 預設值是 `TRUE`。  
  
##  <a name="m_btabcustomtooltips"></a>CMDITabInfo::m_bTabCustomTooltips  
 指定是否索引標籤會顯示工具提示。  
  
```  
BOOL m_bTabCustomTooltips;  
```  
  
### <a name="remarks"></a>備註  
 如果`TRUE`，在應用程式傳送`AFX_WM_ON_GET_TAB_TOOLTIP`主框架的訊息。 您可以使用來處理此訊息`ON_REGISTERED_MESSAGE`巨集。  
  
##  <a name="m_btabicons"></a>CMDITabInfo::m_bTabIcons  
 指定是否要在 MDI 索引標籤上顯示圖示。  
  
```  
BOOL m_bTabIcons;  
```  
  
### <a name="remarks"></a>備註  
 如果`TRUE`，每個 MDI 索引標籤上顯示圖示。 否則，圖示不會顯示在索引標籤上。 預設值是 `FALSE`。  
  
##  <a name="m_ntabbordersize"></a>CMDITabInfo::m_nTabBorderSize  
 指定框線的大小，單位為像素的每個索引標籤視窗。  
  
```  
int m_nTabBorderSize;  
```  
  
### <a name="remarks"></a>備註  
 [CMFCVisualManager::GetMDITabsBordersSize](../../mfc/reference/cmfcvisualmanager-class.md#getmditabsborderssize)傳回預設值。  
  
##  <a name="m_style"></a>CMDITabInfo::m_style  
 指定索引標籤的標籤的樣式。  
  
```  
CMFCTabCtrl::Style m_style  
```  
  
### <a name="remarks"></a>備註  
 指定其中一個索引標籤的下列樣式︰  
  
 `STYLE_3D`  
 3D 樣式。  
  
 `STYLE_3D_ONENOTE`  
 Microsoft OneNote 樣式。  
  
 `STYLE_3D_VS2005`  
 Microsoft Visual Studio 2005 樣式。  
  
 `STYLE_3D_SCROLLED`  
 3D 樣式與矩形的索引標籤。  
  
 `STYLE_FLAT_SHARED_HORZ_SCROLL`  
 使用共用的水平捲軸的平面樣式。  
  
 `STYLE_3D_ROUNDED_SCROLL`  
 使用圓形的索引標籤的&3;D 樣式。  
  
##  <a name="m_tablocation"></a>CMDITabInfo::m_tabLocation  
 指定是否位於頂端或底部的頁面 索引標籤的標籤。  
  
```  
CMFCTabCtrl::Location m_tabLocation;  
```  
  
### <a name="remarks"></a>備註  
 適用於下列位置旗標的其中一個索引標籤︰  
  
-   LOCATION_BOTTOM︰ 索引標籤的標籤位於頁面底部。  
  
-   LOCATION_TOP︰ 索引標籤的標籤都位於頁面頂端  
  
##  <a name="serialize"></a>CMDITabInfo::Serialize  
 讀取或寫入此物件從封存到封存。  
  
```  
void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>參數  
 [in] `ar`  
 A [CArchive 類別](../../mfc/reference/carchive-class.md)来序列化物件。  
  
## <a name="see-also"></a>另請參閱  
 [Cmdiframewndex 是類別](../../mfc/reference/cmdiframewndex-class.md)   
 [MDI 索引標籤式群組](../../mfc/mdi-tabbed-groups.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)

