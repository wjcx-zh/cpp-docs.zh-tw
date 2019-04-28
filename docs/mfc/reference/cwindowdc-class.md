---
title: CWindowDC 類別
ms.date: 11/04/2016
f1_keywords:
- CWindowDC
- AFXWIN/CWindowDC
- AFXWIN/CWindowDC::CWindowDC
- AFXWIN/CWindowDC::m_hWnd
helpviewer_keywords:
- CWindowDC [MFC], CWindowDC
- CWindowDC [MFC], m_hWnd
ms.assetid: 876a3641-4cde-471c-b0d1-fe58b32af79c
ms.openlocfilehash: 55a9ccfc496c95c9e7410cbd5645135ee555ff26
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323381"
---
# <a name="cwindowdc-class"></a>CWindowDC 類別

衍生自 `CDC`。

## <a name="syntax"></a>語法

```
class CWindowDC : public CDC
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CWindowDC::CWindowDC](#cwindowdc)|建構 `CWindowDC` 物件。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CWindowDC::m_hWnd](#m_hwnd)|此 HWND`CWindowDC`附加。|

## <a name="remarks"></a>備註

呼叫 Windows 函式[GetWindowDC](/windows/desktop/api/winuser/nf-winuser-getwindowdc)在建構階段並[ReleaseDC](/windows/desktop/api/winuser/nf-winuser-releasedc)在解構階段。 這表示`CWindowDC`物件存取整個螢幕區域[CWnd](../../mfc/reference/cwnd-class.md) （用戶端和非工作區）。

如需有關使用`CWindowDC`，請參閱 <<c2> [ 裝置內容](../../mfc/device-contexts.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CWindowDC`

## <a name="requirements"></a>需求

標題： afxwin.h

##  <a name="cwindowdc"></a>  CWindowDC::CWindowDC

建構`CWindowDC`存取整個螢幕區域 （用戶端和非工作區） 的物件`CWnd`指向的物件*pWnd*。

```
explicit CWindowDC(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
視窗的裝置內容物件將會存取其工作區中。

### <a name="remarks"></a>備註

建構函式會呼叫 Windows 函式[GetWindowDC](/windows/desktop/api/winuser/nf-winuser-getwindowdc)。

例外狀況 (型別的`CResourceException`) 便會擲回 Windows`GetWindowDC`呼叫就會失敗。 裝置內容可能無法使用，如果 Windows 已有配置所有其可用的裝置內容。 您的應用程式競爭五個一般顯示的可用內容，在 Windows 下一次。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#188](../../mfc/codesnippet/cpp/cwindowdc-class_1.cpp)]

##  <a name="m_hwnd"></a>  CWindowDC::m_hWnd

HWND`CWnd`指標用來建構`CWindowDC`物件。

```
HWND m_hWnd;
```

### <a name="remarks"></a>備註

`m_hWnd` 是受保護的類型 HWND 的變數。

### <a name="example"></a>範例

  範例，請參閱[CWindowDC::CWindowDC](#cwindowdc)。

## <a name="see-also"></a>另請參閱

[CDC 類別](../../mfc/reference/cdc-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDC 類別](../../mfc/reference/cdc-class.md)
