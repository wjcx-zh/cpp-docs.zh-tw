---
title: CTooltip管理員類別
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
ms.openlocfilehash: 4e721740fc100a34ea08dd7ff5f9291eea2d9b36
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752173"
---
# <a name="ctooltipmanager-class"></a>CTooltip管理員類別

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

使用[CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)`CMFCToolTipInfo`類`CTooltipManager`,並一起實現應用程式中的自定義工具提示。 有關如何使用這些工具提示類別的範例,請參閱[CMFCToolTipCtrl 類別主題](../../mfc/reference/cmfctooltipctrl-class.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)

## <a name="requirements"></a>需求

**標題:** afxtooltip管理員.h

## <a name="ctooltipmanagercreatetooltip"></a><a name="createtooltip"></a>CTooltip管理員:建立工具提示

建立工具提示控制項。

```
static BOOL CreateToolTip(
    CToolTipCtrl*& pToolTip,
    CWnd* pWndParent,
    UINT nType);
```

### <a name="parameters"></a>參數

*pToolTip*<br/>
[出]對工具提示指標的引用。 當函數返回時,它將指向新創建的工具提示。

*pwnd 父級*<br/>
[在]工具提示的父級。

*nType*<br/>
[在]工具提示的類型。

### <a name="return-value"></a>傳回值

如果已成功創建工具提示,則非零。

### <a name="remarks"></a>備註

您必須調用[CTooltipManager::DeleteToolTip](#deletetooltip)刪除在*pToolTip*中傳遞的工具提示控制項。

[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)根據*nType*指定的工具提示類型設定它創建的每個工具提示的可視顯示參數。 要改變一個或多個工具提示類型的參數,請致電[CTooltipManager::設定工具提示Params](#settooltipparams)。

下表列的工具提示類型:

|工具提示類型|控制類別|範例類型|
|------------------|----------------------|-------------------|
|AFX_TOOLTIP_TYPE_BUTTON|一個按鈕。|CMFCButton|
|AFX_TOOLTIP_TYPE_CAPTIONBAR|標題欄。|CMFCCaptionBar|
|AFX_TOOLTIP_TYPE_DEFAULT|不適合其他類別的任何控制項。|無。|
|AFX_TOOLTIP_TYPE_DOCKBAR|可停靠窗格。|CDockablePane|
|AFX_TOOLTIP_TYPE_EDIT|文字方塊。|無。|
|AFX_TOOLTIP_TYPE_MINIFRAME|小型框架。|CPaneFrameWnd|
|AFX_TOOLTIP_TYPE_PLANNER|規劃師|無。|
|AFX_TOOLTIP_TYPE_RIBBON|帶狀欄。|CMFC絲帶欄,CMFC絲帶面板功能表欄|
|AFX_TOOLTIP_TYPE_TAB|選項卡控件。|CMFCTabCtrl|
|AFX_TOOLTIP_TYPE_TOOLBAR|工具列。|CMFC工具列,CMFCPopupMenuBar|
|AFX_TOOLTIP_TYPE_TOOLBOX|工具箱。|無。|

## <a name="ctooltipmanagerdeletetooltip"></a><a name="deletetooltip"></a>CTooltip管理員::DeleteTooltip

刪除工具提示控制項。

```
static void DeleteToolTip(CToolTipCtrl*& pToolTip);
```

### <a name="parameters"></a>參數

*pToolTip*<br/>
[進出]指向要銷毀的工具提示的指標的引用。

### <a name="remarks"></a>備註

呼叫此方法的每個[CToolTipCtrl 類別](../../mfc/reference/ctooltipctrl-class.md)由[CTooltipManager 建立::建立工具提示](#createtooltip)。 父控件應從其`OnDestroy`處理程式調用此方法。 這是正確從框架中刪除工具提示所必需的。 此方法在返回之前將*pToolTip*設定為 NULL。

## <a name="ctooltipmanagersettooltipparams"></a><a name="settooltipparams"></a>CTooltip管理員::設定工具提示

自定義指定 Windows 控制件類型的工具提示控制項的外觀。

```cpp
void SetTooltipParams(
    UINT nTypes,
    CRuntimeClass* pRTC=RUNTIME_CLASS(CMFCToolTipCtrl),
    CMFCToolTipInfo* pParams=NULL);
```

### <a name="parameters"></a>參數

*n 類型*<br/>
[在]指定控制項類型。

*pRTC*<br/>
[在]自定義工具提示的運行時類。

*pParams*<br/>
[在]工具提示參數。

### <a name="remarks"></a>備註

此方法設置[CToolTipManager](../../mfc/reference/ctooltipmanager-class.md)在建立工具提示時使用的運行時類和初始參數。 當控制項呼叫[CTooltipManager::CreateTooltip](#createtooltip)並傳遞工具提示類型(這是*nTypes*指示的類型之一),工具提示管理員將創建一個工具提示控制項,該控件是*pRTC*指定的執行時類的實例,並將*pParams*指定的參數傳遞給新的工具提示。

呼叫此方法時,所有現有的工具提示擁有者都會收到AFX_WM_UPDATETOOLTIPS消息,他們必須使用[CTooltipManager:::createToolTip](#createtooltip)重新建立工具提示。

*nTypes*可以是[CTooltipManager 使用的有效工具提示類型的任意組合:創建工具提示](#createtooltip),也可以AFX_TOOLTIP_TYPE_ALL。 如果傳遞AFX_TOOLTIP_TYPE_ALL,則所有工具提示類型都受到影響。

### <a name="example"></a>範例

下面的示例演示如何使用`SetTooltipParams``CTooltipManager`類的方法。 這段程式碼片段是 [Draw 用戶端範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_DrawClient#11](../../mfc/reference/codesnippet/cpp/ctooltipmanager-class_1.cpp)]

## <a name="ctooltipmanagersettooltiptext"></a><a name="settooltiptext"></a>CTooltip管理員::設定工具提示文字

設定工具提示的文本和說明。

```
static void SetTooltipText(
    TOOLINFO* pTI,
    CToolTipCtrl* pToolTip,
    UINT nType,
    const CString strText,
    LPCTSTR lpszDescr=NULL);
```

### <a name="parameters"></a>參數

*Pti*<br/>
[在]指向 TOOLINFO 物件的指標。

*pToolTip*<br/>
[進出]指向工具提示控件的指標,用於設置文本和說明。

*nType*<br/>
[在]指定與此工具提示關聯的控制項類型。

*斯特文字*<br/>
[在]要設定為工具提示文本的文本。

*lpszDescr*<br/>
[在]指向工具提示說明的指標。 可以是 NULL。

### <a name="remarks"></a>備註

*nType*的值必須與[CTooltipManager 的](#createtooltip) *nType*參數的值相同:創建工具提示時創建工具提示。

## <a name="ctooltipmanagerupdatetooltips"></a><a name="updatetooltips"></a>CTool提示管理員::更新工具提示

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

```cpp
void UpdateTooltips();
```

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolTipCtrl 類別](../../mfc/reference/cmfctooltipctrl-class.md)<br/>
[CMFCToolTipInfo 類別](../../mfc/reference/cmfctooltipinfo-class.md)
