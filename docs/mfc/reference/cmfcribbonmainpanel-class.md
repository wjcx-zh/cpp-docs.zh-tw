---
title: CMFCRibbonMainPanel 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CMFCRibbonMainPanel [MFC], Add
- CMFCRibbonMainPanel [MFC], AddRecentFilesList
- CMFCRibbonMainPanel [MFC], AddToBottom
- CMFCRibbonMainPanel [MFC], AddToRight
- CMFCRibbonMainPanel [MFC], GetCommandsFrame
ms.assetid: 1af78798-5e75-4365-9c81-a54aa5679602
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05257749c95b619c479538a1322746ae2b487b6a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcribbonmainpanel-class"></a>CMFCRibbonMainPanel 類別
實作功能區面板，其中顯示當您按一下[CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonMainPanel : public CMFCRibbonPanel  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|`CMFCRibbonMainPanel::CMFCRibbonMainPanel`|預設建構函式。|  
|`CMFCRibbonMainPanel::~CMFCRibbonMainPanel`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonMainPanel::Add](#add)|將功能區項目加入至應用程式按鈕面板的左窗格中。 (覆寫[cmfcribbonpanel:: Add](../../mfc/reference/cmfcribbonpanel-class.md#add)。)|  
|[CMFCRibbonMainPanel::AddRecentFilesList](#addrecentfileslist)|將文字字串加入至新的檔案清單功能表。|  
|[CMFCRibbonMainPanel::AddToBottom](#addtobottom)|將功能區項目加入至應用程式功能區面板的下方窗格中。|  
|[CMFCRibbonMainPanel::AddToRight](#addtoright)|將功能區項目加入至應用程式按鈕面板的右窗格中。|  
|`CMFCRibbonMainPanel::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|[CMFCRibbonMainPanel::GetCommandsFrame](#getcommandsframe)|傳回代表 [功能區的 main] 面板的區域的矩形。|  
|`CMFCRibbonMainPanel::GetThisClass`|由架構用來取得指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|  
  
## <a name="remarks"></a>備註  
 架構會顯示`CMFCRibbonMainPanel`當您開啟 [應用程式] 面板。 它包含三個窗格：  
  
-   左的窗格包含命令相關聯的檔案，例如**開啟**，**儲存**，**列印**，和**關閉**。 若要將命令新增到這個窗格中，呼叫[CMFCRibbonMainPanel::Add](#add)。  
  
-   在右窗格包含修改命令，按一下左窗格中的選項。 例如，如果您按一下**存**右窗格可以從左窗格中，顯示可用的檔案類型。 若要加入此窗格中的項目，請呼叫[CMFCRibbonMainPanel::AddToRight](#addtoright)。  
  
-   下方窗格包含可讓您變更應用程式的設定，並結束程式的按鈕。 若要加入此窗格中的項目，請呼叫[CMFCRibbonMainPanel::AddToBottom](#addtobottom)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)  
  
 [CMFCRibbonMainPanel](../../mfc/reference/cmfcribbonmainpanel-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxRibbonMainPanel.h  
  
##  <a name="add"></a>  CMFCRibbonMainPanel::Add  
 將功能區項目加入至應用程式按鈕面板的左窗格中。  
  
```  
virtual void Add(CMFCRibbonBaseElement* pElem);
```  
  
### <a name="parameters"></a>參數  
 [in][out] `pElem`  
 將新增到 [主面板] 功能區項目的指標。  
  
### <a name="remarks"></a>備註  
 將功能區項目的加入面板。 使用此方法加入的項目將會位於畫面左側的 [主面板]。  
  
##  <a name="addrecentfileslist"></a>  CMFCRibbonMainPanel::AddRecentFilesList  
 將文字字串加入至新的檔案清單功能表。  
  
```  
void AddRecentFilesList(
    LPCTSTR lpszLabel,  
    int nWidth = 300);
```  
  
### <a name="parameters"></a>參數  
 `lpszLabel`  
 指定要加入新的檔案清單的字串。  
  
 `nWidth`  
 像素為單位的最新的檔案清單 面板中指定的寬度。  
  
### <a name="remarks"></a>備註  
  
##  <a name="addtobottom"></a>  CMFCRibbonMainPanel::AddToBottom  
 將功能區項目加入至應用程式功能區面板的下方窗格中。  
  
```  
void AddToBottom(CMFCRibbonMainPanelButton* pElem);
```  
  
### <a name="parameters"></a>參數  
 [in][out] `pElem`  
 將新增到底部的 [主面板] 功能區項目的指標。  
  
### <a name="remarks"></a>備註  
  
##  <a name="addtoright"></a>  CMFCRibbonMainPanel::AddToRight  
 將功能區項目加入至應用程式按鈕面板的右窗格中。  
  
```  
void AddToRight(
    CMFCRibbonBaseElement* pElem,  
    int nWidth = 300);
```  
  
### <a name="parameters"></a>參數  
 `pElem`  
 要加入至右邊的 [主面板] 功能區項目的指標。  
  
 `nWidth`  
 指定的寬度，以像素的右方面板。  
  
### <a name="remarks"></a>備註  
 使用此函式右面板中加入功能區項目。 右側面板通常會顯示最近使用的檔案清單，但您可以加入其他任何功能區項目這裡。  
  
##  <a name="getcommandsframe"></a>  CMFCRibbonMainPanel::GetCommandsFrame  
 傳回代表 [功能區的 main] 面板的區域的矩形。  
  
```  
CRect GetCommandsFrame() const;  
```  
  
### <a name="return-value"></a>傳回值  
 代表功能區主面板的區域的矩形。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonPanel 類別](../../mfc/reference/cmfcribbonpanel-class.md)
