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
ms.openlocfilehash: d587f1cfa6ec38dd564da196da8130bffac11302
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503143"
---
# <a name="cpaintdc-class"></a>CPaintDC 類別

衍生自[CDC](../../mfc/reference/cdc-class.md)的裝置內容類別。

## <a name="syntax"></a>語法

```
class CPaintDC : public CDC
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CPaintDC::CPaintDC](#cpaintdc)|結構連接到指定的[CWnd。](../../mfc/reference/cwnd-class.md) `CPaintDC`|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CPaintDC::m_ps](#m_ps)|包含用來繪製工作區的[PAINTSTRUCT](/windows/win32/api/winuser/ns-winuser-paintstruct) 。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CPaintDC::m_hWnd](#m_hwnd)|附加這個`CPaintDC`物件的 HWND。|

## <a name="remarks"></a>備註

它會在結構時間執行[cwnd:: BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint) , 並在析構時間執行[Cwnd:: EndPaint](../../mfc/reference/cwnd-class.md#endpaint) 。

物件只能在回應[WM_PAINT](/windows/win32/gdi/wm-paint)訊息時使用, 通常是在您`OnPaint`的訊息處理常式成員函式中。 `CPaintDC`

如需使用`CPaintDC`的詳細資訊, 請參閱[裝置](../../mfc/device-contexts.md)內容。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CPaintDC`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="cpaintdc"></a>CPaintDC:: CPaintDC

會建立`CPaintDC`物件、準備用於繪製的應用程式視窗, 並將[PAINTSTRUCT](/windows/win32/api/winuser/ns-winuser-paintstruct)結構儲存在[m_ps](#m_ps)成員變數中。

```
explicit CPaintDC(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
指向`CPaintDC`物件所屬`CWnd`的物件。

### <a name="remarks"></a>備註

如果 Windows [GetDC](/windows/win32/api/winuser/nf-winuser-getdc)呼叫失敗`CResourceException`, 則會擲回例外狀況 (屬於類型)。 如果 Windows 已配置所有可用的裝置內容, 則可能無法使用裝置內容。 您的應用程式會在 Windows 下的任何指定時間, 競爭五個通用的顯示內容。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#97](../../mfc/codesnippet/cpp/cpaintdc-class_1.cpp)]

##  <a name="m_hwnd"></a>CPaintDC:: m_hWnd

附加`HWND` 這個`CPaintDC`物件的目標。

```
HWND m_hWnd;
```

### <a name="remarks"></a>備註

*m_hWnd*是 hWnd 類型的受保護變數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#98](../../mfc/codesnippet/cpp/cpaintdc-class_2.cpp)]

##  <a name="m_ps"></a>  CPaintDC::m_ps

`m_ps`是[PAINTSTRUCT](/windows/win32/api/winuser/ns-winuser-paintstruct)類型的公用成員變數。

```
PAINTSTRUCT m_ps;
```

### <a name="remarks"></a>備註

它是由`PAINTSTRUCT` [CWnd:: BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint)傳遞和填寫的。

包含的資訊可讓應用程式用來繪製`CPaintDC`與物件相關聯之視窗的工作區。 `PAINTSTRUCT`

請注意, 您可以透過`PAINTSTRUCT`存取裝置內容控制碼。 不過, 您可以透過`m_hDC` `CPaintDC`繼承自 CDC 的成員變數, 更直接存取控制碼。

### <a name="example"></a>範例

  請參閱[CPaintDC:: m_hWnd](#m_hwnd)的範例。

## <a name="see-also"></a>另請參閱

[MFC 範例 MDI](../../overview/visual-cpp-samples.md)<br/>
[CDC 類別](../../mfc/reference/cdc-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
