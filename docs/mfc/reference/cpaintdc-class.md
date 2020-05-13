---
title: CPaintDC 類別
ms.date: 11/04/2016
f1_keywords:
- CPaintDC
- AFXWIN/CPaintDC
- AFXWIN/CPaintDC::CPaintDC
- AFXWIN/CPaintDC::m_ps
- AFXWIN/CPaintDC::m_hWnd
helpviewer_keywords:
- CPaintDC [MFC], CPaintDC
- CPaintDC [MFC], m_ps
- CPaintDC [MFC], m_hWnd
ms.assetid: 7e245baa-bf9b-403e-a637-7218adf28fab
ms.openlocfilehash: 55342b03454a6dba07bc10ea5f0464c34e0e8db3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374781"
---
# <a name="cpaintdc-class"></a>CPaintDC 類別

衍生[CDC 的裝置](../../mfc/reference/cdc-class.md)內容內容 。

## <a name="syntax"></a>語法

```
class CPaintDC : public CDC
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CPaintDC:CPaintDC](#cpaintdc)|建構連線到`CPaintDC`指定的[CWnd](../../mfc/reference/cwnd-class.md)的 。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CPaintDC:m_ps](#m_ps)|包含用於繪製工作區的[PAINTSTRUCT。](/windows/win32/api/winuser/ns-winuser-paintstruct)|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CPaintDC:m_hWnd](#m_hwnd)|此`CPaintDC`物件附加到的 HWND。|

## <a name="remarks"></a>備註

它執行[CWnd::在施工時開始繪製,](../../mfc/reference/cwnd-class.md#beginpaint)在銷毀時[執行 CWnd:endPaint。](../../mfc/reference/cwnd-class.md#endpaint)

物件`CPaintDC`只能在回應[WM_PAINT](/windows/win32/gdi/wm-paint)消息時使用,通常`OnPaint`在消息處理程式成員函數中。

有關`CPaintDC`使用的詳細資訊,請參閱[裝置上下文](../../mfc/device-contexts.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CPaintDC`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="cpaintdccpaintdc"></a><a name="cpaintdc"></a>CPaintDC:CPaintDC

建構`CPaintDC`物件,準備用於繪製的應用程式視窗,並將[PAINTSTRUCT](/windows/win32/api/winuser/ns-winuser-paintstruct)結構存儲在[m_ps](#m_ps)成員變數中。

```
explicit CPaintDC(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
指向`CPaintDC`物件`CWnd`所屬的物件。

### <a name="remarks"></a>備註

如果 Windows `CResourceException` [GetDC](/windows/win32/api/winuser/nf-winuser-getdc)調用失敗,將引發異常(類型類型)。 如果 Windows 已分配其所有可用設備上下文,則設備上下文可能不可用。 您的應用程式競爭 Windows 下任何給定時間可用的五個常見顯示上下文。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#97](../../mfc/codesnippet/cpp/cpaintdc-class_1.cpp)]

## <a name="cpaintdcm_hwnd"></a><a name="m_hwnd"></a>CPaintDC:m_hWnd

`HWND`附加到此`CPaintDC`物件。

```
HWND m_hWnd;
```

### <a name="remarks"></a>備註

*m_hWnd*是HWND類型的受保護變數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#98](../../mfc/codesnippet/cpp/cpaintdc-class_2.cpp)]

## <a name="cpaintdcm_ps"></a><a name="m_ps"></a>CPaintDC:m_ps

`m_ps`是[PAINTSTRUCT](/windows/win32/api/winuser/ns-winuser-paintstruct)類型的公共成員變數。

```
PAINTSTRUCT m_ps;
```

### <a name="remarks"></a>備註

它是`PAINTSTRUCT`傳遞給並填寫的[CWnd::BeginPaint。](../../mfc/reference/cwnd-class.md#beginpaint)

包含`PAINTSTRUCT`應用程式用於繪製與`CPaintDC`物件關聯的視窗的工作區的資訊。

請注意,您可以通過 存取裝置上下`PAINTSTRUCT`文句柄 。 但是,您可以通過從`m_hDC``CPaintDC`CDC 繼承的成員變數更直接地訪問句柄。

### <a name="example"></a>範例

  請參閱[CPaintDC::m_hWnd](#m_hwnd)的範例。

## <a name="see-also"></a>另請參閱

[MFC 樣品 MDI](../../overview/visual-cpp-samples.md)<br/>
[CDC 類別](../../mfc/reference/cdc-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
