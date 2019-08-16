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
ms.openlocfilehash: 0ef9b4917dc834eb8335690f9b0d171245f5c170
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502159"
---
# <a name="cwindowdc-class"></a>CWindowDC 類別

衍生自 `CDC`。

## <a name="syntax"></a>語法

```
class CWindowDC : public CDC
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CWindowDC::CWindowDC](#cwindowdc)|建構 `CWindowDC` 物件。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|說明|
|----------|-----------------|
|[CWindowDC::m_hWnd](#m_hwnd)|附加此`CWindowDC`的 HWND。|

## <a name="remarks"></a>備註

在結構時間呼叫 Windows 函式[GetWindowDC](/windows/win32/api/winuser/nf-winuser-getwindowdc), 並在析構時間[ReleaseDC](/windows/win32/api/winuser/nf-winuser-releasedc) 。 這表示`CWindowDC`物件會存取[CWnd](../../mfc/reference/cwnd-class.md)的整個螢幕區域 (用戶端和非工作區)。

如需使用`CWindowDC`的詳細資訊, 請參閱[裝置](../../mfc/device-contexts.md)內容。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CWindowDC`

## <a name="requirements"></a>需求

標頭: afxwin.h。h

##  <a name="cwindowdc"></a>  CWindowDC::CWindowDC

建立`CWindowDC`物件, 以存取*pWnd*所`CWnd`指向之物件的整個螢幕區域 (用戶端和非工作區)。

```
explicit CWindowDC(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
裝置內容物件將存取其工作區的視窗。

### <a name="remarks"></a>備註

此函式會呼叫 Windows 函數[GetWindowDC](/windows/win32/api/winuser/nf-winuser-getwindowdc)。

如果 Windows `CResourceException` `GetWindowDC`呼叫失敗, 則會擲回例外狀況 (類型為)。 如果 Windows 已配置所有可用的裝置內容, 則可能無法使用裝置內容。 您的應用程式會在 Windows 下的任何指定時間, 競爭五個通用的顯示內容。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#188](../../mfc/codesnippet/cpp/cwindowdc-class_1.cpp)]

##  <a name="m_hwnd"></a>  CWindowDC::m_hWnd

`CWnd`指標的 HWND 是用來`CWindowDC`建立物件。

```
HWND m_hWnd;
```

### <a name="remarks"></a>備註

`m_hWnd`是 HWND 類型的受保護變數。

### <a name="example"></a>範例

  請參閱[CWindowDC:: CWindowDC](#cwindowdc)的範例。

## <a name="see-also"></a>另請參閱

[CDC 類別](../../mfc/reference/cdc-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDC 類別](../../mfc/reference/cdc-class.md)
