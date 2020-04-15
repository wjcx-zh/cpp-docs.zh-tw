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
ms.openlocfilehash: 1458039c25f2379b3c3db553b2010e9391df28db
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375097"
---
# <a name="cmfcribbonmainpanel-class"></a>CMFCRibbonMainPanel 類別

實現功能區面板,當您按下[CMFC 功能應用程式按鈕](../../mfc/reference/cmfcribbonapplicationbutton-class.md)時顯示。

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
|[CMFC功能中心面板:添加](#add)|將功能區元素添加到應用程式按鈕面板的左側窗格中。 (覆寫[CMFC 功能面板::新增](../../mfc/reference/cmfcribbonpanel-class.md#add).)|
|[CMFC 功能中心面板::新增最新檔案清單](#addrecentfileslist)|將文字字串添加到最近的檔案清單選單。|
|[CMFC 剪彩主面板::添加](#addtobottom)|將功能區元素添加到功能區應用程式面板的底部窗格中。|
|[CMFC 功能主面板::添加右側](#addtoright)|將功能區元素添加到應用程式按鈕面板的右側窗格中。|
|`CMFCRibbonMainPanel::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|
|[CMFC 功能主機面板::取得命令框架](#getcommandsframe)|返回表示功能區主面板區域的矩形。|
|`CMFCRibbonMainPanel::GetThisClass`|框架用於獲取指向與此類類型關聯的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|

## <a name="remarks"></a>備註

框架顯示開啟應用程式`CMFCRibbonMainPanel`面板時的 。 它包含三個窗格:

- 左方窗格包含與檔案關聯的指令,如 **'開啟**'**Save**、**列印**、**關閉**。 要向此窗格加入命令,請致電[CMFCRibbonMainPanel:::添加](#add)。

- 右方窗格包含修改在左下格中按下的命令的選項。 例如,如果從左側窗格按一下 **「保存為」** 則右側窗格可以顯示可用的檔案類型。 要將專案加入此窗格,請執行電[CMFC 功能區主面板::新增右](#addtoright)。

- 底部窗格包含允許您更改應用程式設定並退出程式的按鈕。 要將專案加入此表單,請執行電[CMFC 功能區主面板::新增到底部](#addtobottom)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)

[CMFCRibbonMainPanel](../../mfc/reference/cmfcribbonmainpanel-class.md)

## <a name="requirements"></a>需求

**標題:** afxRibbonMainPanel.h

## <a name="cmfcribbonmainpaneladd"></a><a name="add"></a>CMFC功能中心面板:添加

將功能區元素添加到應用程式按鈕面板的左側窗格中。

```
virtual void Add(CMFCRibbonBaseElement* pElem);
```

### <a name="parameters"></a>參數

*佩萊姆*<br/>
[進出]指向要添加到主面板的功能區元素的指標。

### <a name="remarks"></a>備註

向面板添加功能區元素。 使用此方法添加的元素將位於主面板的左列中。

## <a name="cmfcribbonmainpaneladdrecentfileslist"></a><a name="addrecentfileslist"></a>CMFC 功能中心面板::新增最新檔案清單

將文字字串添加到最近的檔案清單選單。

```
void AddRecentFilesList(
    LPCTSTR lpszLabel,
    int nWidth = 300);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
指定要加入最近檔案清單的字串。

*n 寬度*<br/>
指定最近檔案清單面板的寬度(以像素為單位)。

### <a name="remarks"></a>備註

## <a name="cmfcribbonmainpaneladdtobottom"></a><a name="addtobottom"></a>CMFC 剪彩主面板::添加

將功能區元素添加到功能區應用程式面板的底部窗格中。

```
void AddToBottom(CMFCRibbonMainPanelButton* pElem);
```

### <a name="parameters"></a>參數

*佩萊姆*<br/>
[進出]指向功能區元素的指標,用於添加到主面板的底部。

### <a name="remarks"></a>備註

## <a name="cmfcribbonmainpaneladdtoright"></a><a name="addtoright"></a>CMFC 功能主面板::添加右側

將功能區元素添加到應用程式按鈕面板的右側窗格中。

```
void AddToRight(
    CMFCRibbonBaseElement* pElem,
    int nWidth = 300);
```

### <a name="parameters"></a>參數

*佩萊姆*<br/>
指向要添加到主面板右側的功能區元素的指標。

*n 寬度*<br/>
指定右側面板的寬度(以像素為單位)。

### <a name="remarks"></a>備註

使用此函數向右側面板添加功能區元素。 右側面板通常顯示最近的檔案清單,但您可以在此處添加任何其他功能區元素。

## <a name="cmfcribbonmainpanelgetcommandsframe"></a><a name="getcommandsframe"></a>CMFC 功能主機面板::取得命令框架

返回表示功能區主面板區域的矩形。

```
CRect GetCommandsFrame() const;
```

### <a name="return-value"></a>傳回值

表示功能區主面板區域的矩形。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFC 剪彩面板類](../../mfc/reference/cmfcribbonpanel-class.md)
