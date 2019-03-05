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
ms.openlocfilehash: 57b1df49616967841a433a36a504beed0b900cde
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278531"
---
# <a name="cmfcimageeditordialog-class"></a>CMFCImageEditorDialog 類別

`CMFCImageEditorDialog`類別支援影像編輯器 對話方塊。

## <a name="syntax"></a>語法

```
class CMFCImageEditorDialog : public CDialogEx
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCImageEditorDialog::CMFCImageEditorDialog](#cmfcimageeditordialog)|建構 `CMFCImageEditorDialog` 物件。|

## <a name="remarks"></a>備註

`CMFCImageEditorDialog`類別提供一個對話方塊，其中包含：

- 您用來修改映像中的個別像素 [圖片] 區域中。

- 繪圖工具來修改 [圖片] 區域中的像素。

- 若要指定使用繪圖工具的色彩調色盤。

- 預覽區域會顯示您的編輯的效果。

下圖顯示的影像編輯器 對話方塊。

![CMFCImageEditorDialog 對話方塊](../../mfc/reference/media/imageedit.png "CMFCImageEditorDialog 對話方塊")

使用一種方式`CMFCImageEditorDialog`物件是將它傳遞`CBitmap`編輯映像。 請勿建立大型映像，因為編輯區域的映像具有大小限制，且邏輯像素大小會進行調整以納入區域。 呼叫`DoModal`方法來啟動強制回應對話方塊。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)

## <a name="requirements"></a>需求

**標頭：** afximageeditordialog.h

##  <a name="cmfcimageeditordialog"></a>  CMFCImageEditorDialog::CMFCImageEditorDialog

建構 `CMFCImageEditorDialog` 物件。

```
CMFCImageEditorDialog(
    CBitmap* pBitmap,
    CWnd* pParent=NULL,
    int nBitsPixel=-1);
```

### <a name="parameters"></a>參數

*pBitmap*<br/>
映像的指標。

*pParent*<br/>
目前的影像編輯器對話方塊的父視窗的指標。

*nBitsPixel*<br/>
用來代表單一像素，也稱為色彩深度的色彩位元數。  如果*nBitsPixel*參數為-1，色彩深度衍生自所指定的影像*pBitmap*參數。 預設值為 -1。

### <a name="return-value"></a>傳回值

若要修改映像，將傳遞的映像指標`CMFCImageEditorDialog`建構函式。 然後呼叫`DoModal`方法來開啟強制回應對話方塊。 當`DoModal`方法傳回時，點陣圖包含新的映像。

### <a name="remarks"></a>備註

### <a name="example"></a>範例

下列範例示範如何建構的物件`CMFCImageEditorDialog`類別。 此範例中是屬於[新的控制項範例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_NewControls#8](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_1.cpp)]
[!code-cpp[NVC_MFC_NewControls#40](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_2.cpp)]

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)
