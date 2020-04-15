---
title: CMFCImageEditorPaletteBar 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCImageEditorPaletteBar
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar::GetRowHeight
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable
helpviewer_keywords:
- CMFCImageEditorPaletteBar [MFC], GetRowHeight
- CMFCImageEditorPaletteBar [MFC], IsButtonExtraSizeAvailable
ms.assetid: 3fb7ba8e-f254-4d56-b913-9941b4ed8138
ms.openlocfilehash: 33d4bc0c72718d028031ac11bc67da6aec5e4907
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374418"
---
# <a name="cmfcimageeditorpalettebar-class"></a>CMFCImageEditorPaletteBar 類別

為圖像編輯器對話方塊提供調色板欄功能。

## <a name="syntax"></a>語法

```
class CMFCImageEditorPaletteBar : public CMFCToolBar
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|||
|-|-|
|名稱|描述|
|[CMFC影像編輯器調色板列::取得羅高](#getrowheight)|返回工具列按鈕的高度。 (覆寫[CMFC 工具列:取得羅高](../../mfc/reference/cmfctoolbar-class.md#getrowheight).)|
|[CMFC 影像編輯器調色盤列:是按鈕超尺寸可用](#isbuttonextrasizeavailable)|確定工具列是否可以顯示具有擴展邊框的按鈕。 (覆寫[CMFC 工具列:是按鈕外大尺寸](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable).)|

### <a name="remarks"></a>備註

這個類別並不適合直接從您的程式碼使用。

框架使用此類在圖像編輯器對話框中顯示調色板欄。 有關影像編輯器對話框的詳細資訊,請參閱[CMFCImage 編輯器對話類](../../mfc/reference/cmfcimageeditordialog-class.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBa](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFC 影像編輯器列](../../mfc/reference/cmfcimageeditorpalettebar-class.md)

## <a name="requirements"></a>需求

**標題:** afx 影像編輯器.h

## <a name="cmfcimageeditorpalettebargetrowheight"></a><a name="getrowheight"></a>CMFC影像編輯器調色板列::取得羅高

返回工具列按鈕的高度。

```
virtual int GetRowHeight() const;
```

### <a name="return-value"></a>傳回值

工具列上每個按鈕的高度。

## <a name="cmfcimageeditorpalettebarisbuttonextrasizeavailable"></a><a name="isbuttonextrasizeavailable"></a>CMFC 影像編輯器調色盤列:是按鈕超尺寸可用

確定工具列是否可以顯示具有擴展邊框的按鈕。

```
virtual BOOL IsButtonExtraSizeAvailable() const;
```

### <a name="return-value"></a>傳回值

此方法返回 FALSE。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCImageEditorDialog 類別](../../mfc/reference/cmfcimageeditordialog-class.md)
