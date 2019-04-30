---
title: CMFCRibbonMainPanel 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonMainPanel
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::Add
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddRecentFilesList
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddToBottom
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddToRight
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::GetCommandsFrame
helpviewer_keywords:
- CMFCRibbonMainPanel [MFC], Add
- CMFCRibbonMainPanel [MFC], AddRecentFilesList
- CMFCRibbonMainPanel [MFC], AddToBottom
- CMFCRibbonMainPanel [MFC], AddToRight
- CMFCRibbonMainPanel [MFC], GetCommandsFrame
ms.assetid: 1af78798-5e75-4365-9c81-a54aa5679602
ms.openlocfilehash: e4bd1ab8cffc87d5079518cf9a1d6e430ca40fd9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403590"
---
# <a name="cmfcribbonmainpanel-class"></a>CMFCRibbonMainPanel 類別

實作功能區面板，其中顯示當您按一下  [CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)。

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
|[CMFCRibbonMainPanel::AddRecentFilesList](#addrecentfileslist)|將新的檔案清單功能表中的文字字串。|
|[CMFCRibbonMainPanel::AddToBottom](#addtobottom)|將功能區項目加入至功能區應用程式面板的下方窗格中。|
|[CMFCRibbonMainPanel::AddToRight](#addtoright)|將功能區項目加入至應用程式按鈕面板的右窗格中。|
|`CMFCRibbonMainPanel::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|[CMFCRibbonMainPanel::GetCommandsFrame](#getcommandsframe)|傳回矩形，表示功能區的 main 面板的區域。|
|`CMFCRibbonMainPanel::GetThisClass`|Framework 用來取得的指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|

## <a name="remarks"></a>備註

架構會顯示`CMFCRibbonMainPanel`當您開啟應用程式的面板。 它包含三個窗格：

- 左的窗格包含命令相關聯的檔案，例如**開放**，**儲存**，**列印**，以及**關閉**。 若要加入此窗格中的命令，請呼叫[CMFCRibbonMainPanel::Add](#add)。

- 右窗格包含修改的左窗格中按一下 命令的選項。 例如，如果您按一下**另存新檔**左窗格中，從右窗格可以顯示可用的檔案類型。 若要加入此窗格中的項目，請呼叫[CMFCRibbonMainPanel::AddToRight](#addtoright)。

- 下方窗格包含按鈕，可讓您變更應用程式的設定，並結束程式。 若要加入此窗格中的項目，請呼叫[CMFCRibbonMainPanel::AddToBottom](#addtobottom)。

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

*pElem*<br/>
[in、 out]若要加入至主面板的功能區項目指標。

### <a name="remarks"></a>備註

將功能區項目的加入面板。 使用此方法加入的項目會位於主面板左側資料行。

##  <a name="addrecentfileslist"></a>  CMFCRibbonMainPanel::AddRecentFilesList

將新的檔案清單功能表中的文字字串。

```
void AddRecentFilesList(
    LPCTSTR lpszLabel,
    int nWidth = 300);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
指定要加入至新的檔案清單的字串。

*nWidth*<br/>
指定寬度，單位為像素的最新的檔案清單 面板。

### <a name="remarks"></a>備註

##  <a name="addtobottom"></a>  CMFCRibbonMainPanel::AddToBottom

將功能區項目加入至功能區應用程式面板的下方窗格中。

```
void AddToBottom(CMFCRibbonMainPanelButton* pElem);
```

### <a name="parameters"></a>參數

*pElem*<br/>
[in、 out]將新增至 [main] 面板底部的功能區項目指標。

### <a name="remarks"></a>備註

##  <a name="addtoright"></a>  CMFCRibbonMainPanel::AddToRight

將功能區項目加入至應用程式按鈕面板的右窗格中。

```
void AddToRight(
    CMFCRibbonBaseElement* pElem,
    int nWidth = 300);
```

### <a name="parameters"></a>參數

*pElem*<br/>
要加入至主面板右側的功能區項目指標。

*nWidth*<br/>
指定寬度，單位為像素的右方面板。

### <a name="remarks"></a>備註

若要將功能區項目新增至右窗格的 使用此函式。 右窗格的 通常會顯示最近的檔案清單，但您可以加入其他任何功能區項目這裡。

##  <a name="getcommandsframe"></a>  CMFCRibbonMainPanel::GetCommandsFrame

傳回矩形，表示功能區的 main 面板的區域。

```
CRect GetCommandsFrame() const;
```

### <a name="return-value"></a>傳回值

表示功能區的主面板區域的矩形。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonPanel 類別](../../mfc/reference/cmfcribbonpanel-class.md)
