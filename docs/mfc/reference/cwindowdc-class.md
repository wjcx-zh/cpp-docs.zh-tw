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
ms.openlocfilehash: 89a822280ddebca942016f9a3a334a7128d8456a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371985"
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
|[CWindowDC:CWindowDC](#cwindowdc)|建構 `CWindowDC` 物件。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CWindowDC:m_hWnd](#m_hwnd)|附加到的`CWindowDC`HWND。|

## <a name="remarks"></a>備註

在構造時調用 Windows 函數[GetWindowDC,](/windows/win32/api/winuser/nf-winuser-getwindowdc)在銷毀時[調用釋放 DC。](/windows/win32/api/winuser/nf-winuser-releasedc) 這意味著對`CWindowDC`象 訪問[CWnd](../../mfc/reference/cwnd-class.md)的整個螢幕區域(用戶端和非用戶端區域)。

有關`CWindowDC`使用的詳細資訊,請參閱[裝置上下文](../../mfc/device-contexts.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CWindowDC`

## <a name="requirements"></a>需求

標題: afxwin.h

## <a name="cwindowdccwindowdc"></a><a name="cwindowdc"></a>CWindowDC:CWindowDC

建構一個`CWindowDC`物件,該物件`CWnd`訪問*pWnd*指向的物件的整個螢幕區域(用戶端和非用戶端)。

```
explicit CWindowDC(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
設備上下文對象將訪問其工作區的視窗。

### <a name="remarks"></a>備註

建構函數呼叫 Windows 函數[GetWindowDC](/windows/win32/api/winuser/nf-winuser-getwindowdc)。

如果 Windows`GetWindowDC``CResourceException`調用 失敗,將引發異常(類型類型)。 如果 Windows 已分配其所有可用設備上下文,則設備上下文可能不可用。 您的應用程式競爭 Windows 下任何給定時間可用的五個常見顯示上下文。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#188](../../mfc/codesnippet/cpp/cwindowdc-class_1.cpp)]

## <a name="cwindowdcm_hwnd"></a><a name="m_hwnd"></a>CWindowDC:m_hWnd

指標的`CWnd`HWND 用於構`CWindowDC`造 物件。

```
HWND m_hWnd;
```

### <a name="remarks"></a>備註

`m_hWnd`是 HWND 類型的受保護變數。

### <a name="example"></a>範例

  請參考[CWindowDC 的範例:cWindowDC](#cwindowdc)。

## <a name="see-also"></a>另請參閱

[CDC 類別](../../mfc/reference/cdc-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDC 類別](../../mfc/reference/cdc-class.md)
