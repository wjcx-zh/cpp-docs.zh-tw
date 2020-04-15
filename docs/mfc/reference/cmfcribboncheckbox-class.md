---
title: CMFCRibbonCheckBox 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetCompactSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetIntermediateSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetRegularSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::IsDrawTooltipImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDraw
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawMenuImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawOnList
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::SetACCData
helpviewer_keywords:
- CMFCRibbonCheckBox [MFC], CMFCRibbonCheckBox
- CMFCRibbonCheckBox [MFC], GetCompactSize
- CMFCRibbonCheckBox [MFC], GetIntermediateSize
- CMFCRibbonCheckBox [MFC], GetRegularSize
- CMFCRibbonCheckBox [MFC], IsDrawTooltipImage
- CMFCRibbonCheckBox [MFC], OnDraw
- CMFCRibbonCheckBox [MFC], OnDrawMenuImage
- CMFCRibbonCheckBox [MFC], OnDrawOnList
- CMFCRibbonCheckBox [MFC], SetACCData
ms.assetid: 3a6c3891-c8d1-4af0-b954-7b9ab048782a
ms.openlocfilehash: 089c8056afebef31ff98a435bf145566ae64fe1e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375259"
---
# <a name="cmfcribboncheckbox-class"></a>CMFCRibbonCheckBox 類別

`CMFCRibbonCheckBox` 類別實作可以加入至功能區面板、快速存取工具列或快顯功能表的核取方塊。

## <a name="syntax"></a>語法

```
class CMFCRibbonCheckBox : public CMFCRibbonButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCRibbonCheckBox::CMFCRibbonCheckBox](#cmfcribboncheckbox)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCRibbonCheckBox::GetCompactSize](#getcompactsize)|( 覆寫[CMFC 功能按鈕:取得壓縮大小](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize).)|
|[CMFCRibbonCheckBox::GetIntermediateSize](#getintermediatesize)|(覆寫[CMFC 功能按鈕:取得中間大小](../../mfc/reference/cmfcribbonbutton-class.md#getintermediatesize).)|
|[CMFCRibbonCheckBox::GetRegularSize](#getregularsize)|(覆寫[CMFC 功能按鈕:取得一般大小](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize).)|
|[CMFCRibbonCheckBox::IsDrawTooltipImage](#isdrawtooltipimage)|(覆寫 `CMFCRibbonButton::IsDrawTooltipImage`。)|
|[CMFCRibbonCheckBox::OnDraw](#ondraw)|(覆寫[CMFC 功能按鈕:onDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw).)|
|[CMFCRibbonCheckBox::OnDrawMenuImage](#ondrawmenuimage)|(覆寫[CMFC 功能基礎元素:在DrawMenuImage.)](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage)|
|[CMFCRibbonCheckBox::OnDrawOnList](#ondrawonlist)|(覆寫 `CMFCRibbonButton::OnDrawOnList`。)|
|[CMFCRibbonCheckBox::SetACCData](#setaccdata)|( 覆寫[CMFC 功能按鈕:設定ACC資料](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|

## <a name="remarks"></a>備註

若要在應用程式中使用 `CMFCRibbonCheckBox`，請將下列建構函式加入至您的程式碼：

```
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)
```

*其中 nID*是複選方塊命令 ID,lpszText 是複選*lpszText*框的文本標籤。

您可以使用[CMFC 功能面板:::添加](../../mfc/reference/cmfcribbonpanel-class.md#add),將複選框添加到功能區面板中。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonCheckBox](../../mfc/reference/cmfcribboncheckbox-class.md)

## <a name="requirements"></a>需求

**標題:** afxribboncheckbox.h

## <a name="cmfcribboncheckboxcmfcribboncheckbox"></a><a name="cmfcribboncheckbox"></a>CMFC功能框:CMFC功能框

功能區複選框物件的建構函數

```
CMFCRibbonCheckBox(
    UINT nID,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

*nID*<br/>
[在]指定命令識別碼。

*lpszText*<br/>
[在]指定文字標籤。

### <a name="return-value"></a>傳回值

構造功能區複選框物件。

### <a name="example"></a>範例

下面的示例演示如何構造`CMFCRibbonCheckBox`類的物件。

[!code-cpp[NVC_MFC_RibbonApp#17](../../mfc/reference/codesnippet/cpp/cmfcribboncheckbox-class_1.cpp)]

## <a name="cmfcribboncheckboxgetcompactsize"></a><a name="getcompactsize"></a>CMFC 功能包包::取得壓縮大小

重寫時,獲取複選框的緊湊大小。

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向與複選框關聯的 CDC 的指標。

### <a name="return-value"></a>傳回值

返回包含`CSize`該複選框的緊湊大小的物件。

### <a name="remarks"></a>備註

如果未重寫,請返回複選框的中間大小。

## <a name="cmfcribboncheckboxgetintermediatesize"></a><a name="getintermediatesize"></a>CMFC 功能包複選框:取得中間大小

取得複選框的中間大小。

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向與此複選框關聯的 CDC 的指標。

### <a name="return-value"></a>傳回值

`CSize`包含中間大小的複選框的物件。

### <a name="remarks"></a>備註

如果未重寫,則將中間大小計算為預設複選框大小`AFX_CHECK_BOX_DEFAULT_SIZE`( ) 加上文字大小加上邊距。

## <a name="cmfcribboncheckboxgetregularsize"></a><a name="getregularsize"></a>CMFC 功能檢查框:取得一般大小

取得複選框的一般大小。

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向與此複選框關聯的 CDC 物件的指標。

### <a name="return-value"></a>傳回值

返回包含`CSize`常規大小的物件複選框。

### <a name="remarks"></a>備註

如果未重寫,請返回複選框的中間大小。

## <a name="cmfcribboncheckboxisdrawtooltipimage"></a><a name="isdrawtooltipimage"></a>CMFC 功能框::正在繪製工具提示影像

指示是否存在與複選框關聯的工具提示圖像。

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>傳回值

如果存在與複選框關聯的工具提示圖像,則返回 TRUE;如果沒有,則返回 FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcribboncheckboxondraw"></a><a name="ondraw"></a>CMFC功能框::開獎

框架呼叫使用指定的裝置上下文繪製複選框。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向用於在其中繪製複選框的 CDC 的指標。

### <a name="remarks"></a>備註

## <a name="cmfcribboncheckboxondrawmenuimage"></a><a name="ondrawmenuimage"></a>CMFC功能框::在DrawMenu圖像

由框架調用為複選框繪製功能表影像。

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>參數

[在]*CDC&#42;*<br/>
指向與複選框關聯的 CDC 的指標。

*CRect*<br/>
[在]指定`CRect`用於繪製功能表影像的矩形的物件。

### <a name="return-value"></a>傳回值

如果繪製了圖像,則返回 TRUE;如果未繪製,則返回 FALSE。

### <a name="remarks"></a>備註

如果未重寫,則返回 FALSE。

## <a name="cmfcribboncheckboxondrawonlist"></a><a name="ondrawonlist"></a>CMFC功能框::在畫上清單

框架呼叫以在命令清單框中繪製複選框。

```
virtual void OnDrawOnList(
    CDC* pDC,
    CString strText,
    int nTextOffset,
    CRect rect,
    BOOL bIsSelected,
    BOOL bHighlighted);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向要在其中繪製複選框的設備上下文的指標。

*斯特文字*<br/>
[在]顯示文字。

*n文字位移*<br/>
[在]從清單框左側到顯示文本的距離(以像素為單位)。

*矩形*<br/>
[在]複選框的顯示矩形。

*bIs 選擇*<br/>
[在]如果選中該複選框,則為 TRUE,如果未選中,則為 FALSE。

*突顯突顯*<br/>
[在]如果突出顯示該複選框,則為 TRUE,如果沒有,則為 FALSE。

### <a name="remarks"></a>備註

## <a name="cmfcribboncheckboxsetaccdata"></a><a name="setaccdata"></a>CMFC功能框::設定ACC數據

設置複選框的輔助功能數據。

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>參數

*pParent*<br/>
複選框的父視窗。

*資料*<br/>
複選框的輔助功能數據。

### <a name="return-value"></a>傳回值

始終返回 TRUE。

### <a name="remarks"></a>備註

默認情況下,此方法設置複選框的輔助功能數據,並且始終返回 TRUE。 覆寫此方法以設定協助工具資料並傳回值，以指出成功或失敗。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFC 剪彩面板類](../../mfc/reference/cmfcribbonpanel-class.md)
