---
title: CMFCWindowsManagerDialog 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog::CMFCWindowsManagerDialog
helpviewer_keywords:
- CMFCWindowsManagerDialog [MFC], CMFCWindowsManagerDialog
ms.assetid: 35b4b0db-33c4-4b22-94d8-5e3396341340
ms.openlocfilehash: 5089decc7a118cd867aa14df51f5d7e269221108
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58767399"
---
# <a name="cmfcwindowsmanagerdialog-class"></a>CMFCWindowsManagerDialog 類別

`CMFCWindowsManagerDialog`物件可讓使用者管理 MDI 應用程式中的 MDI 子視窗。

## <a name="syntax"></a>語法

```
class CMFCWindowsManagerDialog : public CDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCWindowsManagerDialog::CMFCWindowsManagerDialog](#cmfcwindowsmanagerdialog)|建構 `CMFCWindowsManagerDialog` 物件。|

## <a name="remarks"></a>備註

`CMFCWindowsManagerDialog`包含應用程式中目前開啟的 MDI 子視窗的清單。 使用者可以使用此對話方塊，手動控制 MDI 子視窗的狀態。

`CMFCWindowsManagerDialog` 內嵌於[CMDIFrameWndEx 類別](../../mfc/reference/cmdiframewndex-class.md)。 `CMFCWindowsManagerDialog`不是您應該以手動方式建立的類別。 相反地，呼叫此函式[CMDIFrameWndEx::ShowWindowsDialog](../../mfc/reference/cmdiframewndex-class.md#showwindowsdialog)，它就會建立及顯示`CMFCWindowsManagerDialog`物件。

## <a name="example"></a>範例

下列範例示範如何建構`CMFCWindowsManagerDialog`藉由呼叫物件`CMDIFrameWndEx::ShowWindowsDialog`。 此程式碼片段是一部分[Visual Studio 示範範例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_VisualStudioDemo#18](../../mfc/codesnippet/cpp/cmfcwindowsmanagerdialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)

## <a name="requirements"></a>需求

**標頭：** afxWindowsManagerDialog.h

##  <a name="cmfcwindowsmanagerdialog"></a>  CMFCWindowsManagerDialog::CMFCWindowsManagerDialog

建構[CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)物件。

```
CMFCWindowsManagerDialog(
    CMDIFrameWndEx* pMDIFrame,
    BOOL bHelpButton = FALSE);
```

### <a name="parameters"></a>參數

*pMDIFrame*<br/>
[in]父系或擁有者視窗的指標。

*bHelpButton*<br/>
[in]布林值參數，指定是否要顯示架構**協助** 按鈕。

### <a name="remarks"></a>備註

如需有關視覺管理員的詳細資訊，請參閱[視覺化管理員](../../mfc/visualization-manager.md)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMDIFrameWndEx 類別](../../mfc/reference/cmdiframewndex-class.md)
