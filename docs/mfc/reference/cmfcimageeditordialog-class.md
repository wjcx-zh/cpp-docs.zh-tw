---
title: CMFCImageEditorDialog 類別
ms.date: 11/19/2018
f1_keywords:
- CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog::CMFCImageEditorDialog
helpviewer_keywords:
- CMFCImageEditorDialog [MFC], CMFCImageEditorDialog
ms.assetid: 6a7d08f3-1ec2-4062-9b79-a0c2776b58d1
ms.openlocfilehash: 23c2a919428689fe107b82041bd87b758ede2bc9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367472"
---
# <a name="cmfcimageeditordialog-class"></a>CMFCImageEditorDialog 類別

類`CMFCImageEditorDialog`支援圖像編輯器對話方塊。

## <a name="syntax"></a>語法

```
class CMFCImageEditorDialog : public CDialogEx
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFC 影像編輯器:CMFC影像編輯器對話](#cmfcimageeditordialog)|建構 `CMFCImageEditorDialog` 物件。|

## <a name="remarks"></a>備註

該`CMFCImageEditorDialog`類提供一個對話框,其中包括:

- 用於修改圖像中單個像素的圖片區域。

- 繪圖工具以修改圖片區域中的圖元。

- 用於指定繪圖工具使用的顏色的調色板。

- 顯示編輯效果的預覽區域。

下圖顯示了圖像編輯器對話方塊。

![CMFCImageEditorDialog 對話方塊](../../mfc/reference/media/imageedit.png "CMFCImageEditorDialog 對話方塊")

使用物件的一種方法`CMFCImageEditorDialog`是傳遞要`CBitmap`編輯 的圖像。 不要創建大圖像,因為圖像編輯區域的大小有限,並且調整邏輯圖元大小以適合該區域。 調用`DoModal`方法以啟動模式對話方塊。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)

## <a name="requirements"></a>需求

**標題:** afx 影像編輯器.h

## <a name="cmfcimageeditordialogcmfcimageeditordialog"></a><a name="cmfcimageeditordialog"></a>CMFC 影像編輯器:CMFC影像編輯器對話

建構 `CMFCImageEditorDialog` 物件。

```
CMFCImageEditorDialog(
    CBitmap* pBitmap,
    CWnd* pParent=NULL,
    int nBitsPixel=-1);
```

### <a name="parameters"></a>參數

*pBitmap*<br/>
指向圖像的指標。

*pParent*<br/>
指向當前圖像編輯器對話框的父視窗。

*nBits 圖元*<br/>
用於表示單個像素顏色(也稱為顏色深度)的位數。  如果*nBitsPixel*參數為 -1,則顏色深度將從*pBitmap*參數指定的圖像派生。 預設值為 -1。

### <a name="return-value"></a>傳回值

要修改圖像,請將圖像指標傳遞給`CMFCImageEditorDialog`構造函數。 然後調用`DoModal`方法以打開一個模態對話方塊。 當`DoModal`方法返回時,位圖包含新圖像。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

下面的示例演示如何構造`CMFCImageEditorDialog`類的物件。 此示例是[「新控制件」範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#8](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_1.cpp)]
[!code-cpp[NVC_MFC_NewControls#40](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_2.cpp)]

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)
