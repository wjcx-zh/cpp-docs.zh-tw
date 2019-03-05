---
title: CTooltipManager 類別
ms.date: 11/04/2016
f1_keywords:
- CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager::CreateToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::DeleteToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipParams
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipText
- AFXTOOLTIPMANAGER/CTooltipManager::UpdateTooltips
helpviewer_keywords:
- CTooltipManager [MFC], CreateToolTip
- CTooltipManager [MFC], DeleteToolTip
- CTooltipManager [MFC], SetTooltipParams
- CTooltipManager [MFC], SetTooltipText
- CTooltipManager [MFC], UpdateTooltips
ms.assetid: c71779d7-8b6e-47ef-8500-d4552731fe86
ms.openlocfilehash: 7ca0c657872bb2a3c56c9406a88f8c674cb46938
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57260630"
---
# <a name="ctooltipmanager-class"></a>CTooltipManager 類別

維護工具提示的執行階段資訊。 `CTooltipManager` 類別會在每個應用程式具現化一次。

## <a name="syntax"></a>語法

```
class CTooltipManager : public CObject
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CTooltipManager::CreateToolTip](#createtooltip)|建立指定的 Windows 控制項類型的工具提示控制項。|
|[CTooltipManager::DeleteToolTip](#deletetooltip)|刪除工具提示控制項。|
|[CTooltipManager::SetTooltipParams](#settooltipparams)|自訂指定的 Windows 控制項類型的工具提示控制項的視覺外觀。|
|[CTooltipManager::SetTooltipText](#settooltiptext)|設定工具提示控制項的文字和描述。|
|[CTooltipManager::UpdateTooltips](#updatetooltips)||

## <a name="remarks"></a>備註

使用[CMFCToolTipCtrl 類別](../../mfc/reference/cmfctooltipctrl-class.md)， `CMFCToolTipInfo`，和`CTooltipManager`應用程式中實作自訂的工具提示。 如需如何使用這些工具提示類別的範例，請參閱 < [CMFCToolTipCtrl 類別](../../mfc/reference/cmfctooltipctrl-class.md)主題。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)

## <a name="requirements"></a>需求

**標頭：** afxtooltipmanager.h

##  <a name="createtooltip"></a>  CTooltipManager::CreateToolTip

建立工具提示控制項。

```
static BOOL CreateToolTip(
    CToolTipCtrl*& pToolTip,
    CWnd* pWndParent,
    UINT nType);
```

### <a name="parameters"></a>參數

*pToolTip*<br/>
[out]工具提示 」 指標的參考。 它是設定為函式傳回時指向新建立的工具提示。

*pWndParent*<br/>
[in]工具提示的父代。

*nType*<br/>
[in]工具提示的型別。

### <a name="return-value"></a>傳回值

如果已成功建立工具提示，非零值。

### <a name="remarks"></a>備註

您必須呼叫[CTooltipManager::DeleteToolTip](#deletetooltip)刪除會傳回到的工具提示控制項*pToolTip*。

[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)它會建立每個工具提示的視覺顯示參數為基礎的工具提示的集合型別*n*指定。 若要變更一個或多個工具提示類型的參數，呼叫[Settooltipparams](#settooltipparams)。

下表列出有效的工具提示類型：

|工具提示類型|控制項類別|範例型別|
|------------------|----------------------|-------------------|
|AFX_TOOLTIP_TYPE_BUTTON|按鈕。|CMFCButton|
|AFX_TOOLTIP_TYPE_CAPTIONBAR|標題列。|CMFCCaptionBar|
|AFX_TOOLTIP_TYPE_DEFAULT|不符合另一個類別目錄的任何控制項。|無。|
|AFX_TOOLTIP_TYPE_DOCKBAR|可停駐窗格。|CDockablePane|
|AFX_TOOLTIP_TYPE_EDIT|文字方塊。|無。|
|AFX_TOOLTIP_TYPE_MINIFRAME|迷你。|CPaneFrameWnd|
|AFX_TOOLTIP_TYPE_PLANNER|一個活動規劃中。|無。|
|AFX_TOOLTIP_TYPE_RIBBON|功能區列。|CMFCRibbonBar, CMFCRibbonPanelMenuBar|
|AFX_TOOLTIP_TYPE_TAB|索引標籤控制項。|CMFCTabCtrl|
|AFX_TOOLTIP_TYPE_TOOLBAR|工具列。|CMFCToolBar, CMFCPopupMenuBar|
|AFX_TOOLTIP_TYPE_TOOLBOX|工具箱中。|無。|

##  <a name="deletetooltip"></a>  CTooltipManager::DeleteToolTip

刪除工具提示控制項。

```
static void DeleteToolTip(CToolTipCtrl*& pToolTip);
```

### <a name="parameters"></a>參數

*pToolTip*<br/>
[in、 out]指向要終結的工具提示的參考。

### <a name="remarks"></a>備註

呼叫這個方法，每個[CToolTipCtrl 類別](../../mfc/reference/ctooltipctrl-class.md)中建立[CTooltipManager::CreateToolTip](#createtooltip)。 父控制項應該呼叫這個方法，從其`OnDestroy`處理常式。 如此才能正確地移除架構中的工具提示。 這個方法會設定*pToolTip*為之前它會傳回 NULL。

##  <a name="settooltipparams"></a>  CTooltipManager::SetTooltipParams

自訂指定的 Windows 控制項類型的工具提示控制項的外觀。

```
void SetTooltipParams(
    UINT nTypes,
    CRuntimeClass* pRTC=RUNTIME_CLASS(CMFCToolTipCtrl),
    CMFCToolTipInfo* pParams=NULL);
```

### <a name="parameters"></a>參數

*nTypes*<br/>
[in]指定控制項類型。

*pRTC*<br/>
[in]執行階段類別的自訂工具提示。

*pParams*<br/>
[in]工具提示的參數。

### <a name="remarks"></a>備註

這個方法會設定初始參數與執行階段類別的[CToolTipManager](../../mfc/reference/ctooltipmanager-class.md)時它會建立工具提示使用。 當控制項便會呼叫[CTooltipManager::CreateToolTip](#createtooltip)和工具提示中的階段類型，它是其中一個所指定的型別*nTypes*，工具提示管理員建立的執行個體的工具提示控制項指定的執行階段類別*pRTC* ，並傳遞所指定的參數*pParams*新的工具提示。

當您呼叫這個方法時，所有現有的工具提示擁有者會收到 AFX_WM_UPDATETOOLTIPS 訊息而他們必須使用，以重新建立其工具提示[CTooltipManager::CreateToolTip](#createtooltip)。

*nTypes*可以是任何組合有效的工具提示的型別[CTooltipManager::CreateToolTip](#createtooltip)用途，也可以當作 AFX_TOOLTIP_TYPE_ALL。 如果您傳遞 AFX_TOOLTIP_TYPE_ALL 時，會影響所有的工具提示類型。

### <a name="example"></a>範例

下列範例示範如何使用`SetTooltipParams`方法的`CTooltipManager`類別。 這段程式碼片段是 [Draw 用戶端範例](../../visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_DrawClient#11](../../mfc/reference/codesnippet/cpp/ctooltipmanager-class_1.cpp)]

##  <a name="settooltiptext"></a>  CTooltipManager::SetTooltipText

設定文字和工具提示描述。

```
static void SetTooltipText(
    TOOLINFO* pTI,
    CToolTipCtrl* pToolTip,
    UINT nType,
    const CString strText,
    LPCTSTR lpszDescr=NULL);
```

### <a name="parameters"></a>參數

*pTI*<br/>
[in]TOOLINFO 物件的指標。

*pToolTip*<br/>
[in、 out]若要為其設定文字與描述的工具提示控制項的指標。

*nType*<br/>
[in]指定與此工具提示相關聯的控制項型別。

*strText*<br/>
[in]要設定為工具提示文字的文字。

*lpszDescr*<br/>
[in]工具提示描述指標。 可以是 NULL。

### <a name="remarks"></a>備註

值*n*必須是相同的值*n*參數[CTooltipManager::CreateToolTip](#createtooltip)當您建立工具提示。

##  <a name="updatetooltips"></a>  CTooltipManager::UpdateTooltips

如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。

```
void UpdateTooltips();
```

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolTipCtrl 類別](../../mfc/reference/cmfctooltipctrl-class.md)<br/>
[CMFCToolTipInfo 類別](../../mfc/reference/cmfctooltipinfo-class.md)
