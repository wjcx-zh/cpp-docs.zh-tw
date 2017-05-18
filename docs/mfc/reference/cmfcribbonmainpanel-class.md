---
title: "CMFCRibbonMainPanel 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonMainPanel
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::Add
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddRecentFilesList
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddToBottom
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddToRight
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::GetCommandsFrame
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonMainPanel class
ms.assetid: 1af78798-5e75-4365-9c81-a54aa5679602
caps.latest.revision: 23
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 3fc37a953e62e6ea90de8402b7f2912b06967e13
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonmainpanel-class"></a>CMFCRibbonMainPanel 類別
實作功能區面板，其中顯示當您按一下[CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonMainPanel : public CMFCRibbonPanel  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|`CMFCRibbonMainPanel::CMFCRibbonMainPanel`|預設建構函式。|  
|`CMFCRibbonMainPanel::~CMFCRibbonMainPanel`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonMainPanel::Add](#add)|將功能區項目加入至應用程式按鈕面板的左窗格中。 (覆寫[CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add)。)|  
|[CMFCRibbonMainPanel::AddRecentFilesList](#addrecentfileslist)|將新的檔案清單 功能表上的文字字串。|  
|[CMFCRibbonMainPanel::AddToBottom](#addtobottom)|將功能區項目加入至應用程式功能區面板的下方窗格中。|  
|[CMFCRibbonMainPanel::AddToRight](#addtoright)|將功能區項目加入至應用程式按鈕面板的右窗格中。|  
|`CMFCRibbonMainPanel::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|[CMFCRibbonMainPanel::GetCommandsFrame](#getcommandsframe)|傳回表示區域的主要功能區面板的矩形。|  
|`CMFCRibbonMainPanel::GetThisClass`|由架構用來取得變數的指標， [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與這個類別的型別相關聯的物件。|  
  
## <a name="remarks"></a>備註  
 架構會顯示`CMFCRibbonMainPanel`當您開啟 [應用程式] 面板。 它包含三個窗格︰  
  
-   左的窗格包含命令相關聯的檔案，例如**開啟**，**儲存**，**列印**，和**關閉**。 若要將命令加入到這個窗格中，呼叫[CMFCRibbonMainPanel::Add](#add)。  
  
-   右窗格包含選項，修改您按一下左窗格中的命令。 例如，如果您按一下**另存新檔**左窗格中，從右窗格可以顯示可用的檔案類型。 若要加入此窗格中的項目，呼叫[CMFCRibbonMainPanel::AddToRight](#addtoright)。  
  
-   下方窗格包含可讓您變更應用程式的設定，並結束程式的按鈕。 若要加入此窗格中的項目，呼叫[CMFCRibbonMainPanel::AddToBottom](#addtobottom)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)  
  
 [CMFCRibbonMainPanel](../../mfc/reference/cmfcribbonmainpanel-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxRibbonMainPanel.h  
  
##  <a name="add"></a>CMFCRibbonMainPanel::Add  
 將功能區項目加入至應用程式按鈕面板的左窗格中。  
  
```  
virtual void Add(CMFCRibbonBaseElement* pElem);
```  
  
### <a name="parameters"></a>參數  
 [in][out]`pElem`  
 將加入至主面板功能區項目的指標。  
  
### <a name="remarks"></a>備註  
 將功能區項目加入面板。 使用此方法加入的項目位於畫面左側的 主面板。  
  
##  <a name="addrecentfileslist"></a>CMFCRibbonMainPanel::AddRecentFilesList  
 將新的檔案清單 功能表上的文字字串。  
  
```  
void AddRecentFilesList(
    LPCTSTR lpszLabel,  
    int nWidth = 300);
```  
  
### <a name="parameters"></a>參數  
 `lpszLabel`  
 指定要加入新的檔案清單的字串。  
  
 `nWidth`  
 指定寬度，單位為像素的最新的檔案清單 面板。  
  
### <a name="remarks"></a>備註  
  
##  <a name="addtobottom"></a>CMFCRibbonMainPanel::AddToBottom  
 將功能區項目加入至應用程式功能區面板的下方窗格中。  
  
```  
void AddToBottom(CMFCRibbonMainPanelButton* pElem);
```  
  
### <a name="parameters"></a>參數  
 [in][out]`pElem`  
 若要新增至主面板底部的功能區項目指標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="addtoright"></a>CMFCRibbonMainPanel::AddToRight  
 將功能區項目加入至應用程式按鈕面板的右窗格中。  
  
```  
void AddToRight(
    CMFCRibbonBaseElement* pElem,  
    int nWidth = 300);
```  
  
### <a name="parameters"></a>參數  
 `pElem`  
 要加入至主面板右上角的功能區項目指標。  
  
 `nWidth`  
 指定寬度，單位為像素的右方面板。  
  
### <a name="remarks"></a>備註  
 將功能區項目新增至右側面板中使用此函式。 右側面板通常會顯示最近使用的檔案清單，但您可以新增任何其他功能區項目這裡。  
  
##  <a name="getcommandsframe"></a>CMFCRibbonMainPanel::GetCommandsFrame  
 傳回表示區域的主要功能區面板的矩形。  
  
```  
CRect GetCommandsFrame() const;  
```  
  
### <a name="return-value"></a>傳回值  
 表示區域的主要功能區面板的矩形。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonPanel 類別](../../mfc/reference/cmfcribbonpanel-class.md)

