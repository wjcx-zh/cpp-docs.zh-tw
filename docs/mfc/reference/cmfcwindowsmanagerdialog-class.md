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
ms.openlocfilehash: e3928c0d3ae4f607dceb99c0762277e8ea9ddbde
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319831"
---
# <a name="cmfcwindowsmanagerdialog-class"></a>CMFCWindowsManagerDialog 類別

該`CMFCWindowsManagerDialog`物件使用戶能夠在 MDI 應用程式中管理 MDI 子視窗。

## <a name="syntax"></a>語法

```
class CMFCWindowsManagerDialog : public CDialog
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCWindows 管理員對話::CMFCWindows管理員對話](#cmfcwindowsmanagerdialog)|建構 `CMFCWindowsManagerDialog` 物件。|

## <a name="remarks"></a>備註

包含`CMFCWindowsManagerDialog`目前在應用程式中打開的 MDI 子視窗的清單。 用戶可以使用此對話方塊手動控制 MDI 子視窗的狀態。

`CMFCWindowsManagerDialog`嵌入在[CMDIFrameWndEx 類](../../mfc/reference/cmdiframewndex-class.md)中。 `CMFCWindowsManagerDialog`不是應手動創建的類。 相反,調用函數[CMDIFrameWndEx::ShowWindowsDialog](../../mfc/reference/cmdiframewndex-class.md#showwindowsdialog),它將創建並顯示`CMFCWindowsManagerDialog`一個 物件。

## <a name="example"></a>範例

下面的示例演示如何通過調用`CMFCWindowsManagerDialog``CMDIFrameWndEx::ShowWindowsDialog`構造物件。 此代碼段是[可視化工作室演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#18](../../mfc/codesnippet/cpp/cmfcwindowsmanagerdialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)

## <a name="requirements"></a>需求

**標題:** afxWindowsManagerDialog.h

## <a name="cmfcwindowsmanagerdialogcmfcwindowsmanagerdialog"></a><a name="cmfcwindowsmanagerdialog"></a>CMFCWindows 管理員對話::CMFCWindows管理員對話

構造[CMFCWindowsManager對話](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)物件。

```
CMFCWindowsManagerDialog(
    CMDIFrameWndEx* pMDIFrame,
    BOOL bHelpButton = FALSE);
```

### <a name="parameters"></a>參數

*pMDI框架*<br/>
[在]指向父視窗或擁有者視窗的指標。

*B 說明按鈕*<br/>
[在]指定框架是否顯示 **「説明」** 按鈕的布林參數。

### <a name="remarks"></a>備註

有關視覺化管理員的詳細資訊,請參考[視覺化管理員](../../mfc/visualization-manager.md)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMDIFrameWndEx 類別](../../mfc/reference/cmdiframewndex-class.md)
