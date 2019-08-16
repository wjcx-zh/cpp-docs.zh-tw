---
title: CClientDC 類別
ms.date: 11/04/2016
f1_keywords:
- CClientDC
- AFXWIN/CClientDC
- AFXWIN/CClientDC::CClientDC
- AFXWIN/CClientDC::m_hWnd
helpviewer_keywords:
- CClientDC [MFC], CClientDC
- CClientDC [MFC], m_hWnd
ms.assetid: 8a871d6b-06f8-496e-9fa3-9a5780848369
ms.openlocfilehash: 46428740d052c70218d4443395777428cdf3c3b0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507332"
---
# <a name="cclientdc-class"></a>CClientDC 類別

會負責呼叫在結構時間[GetDC](/windows/win32/api/winuser/nf-winuser-getdc)的 Windows 函式, 並在析構時間[ReleaseDC](/windows/win32/api/winuser/nf-winuser-releasedc) 。

## <a name="syntax"></a>語法

```
class CClientDC : public CDC
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CClientDC::CClientDC](#cclientdc)|構造連接至的`CWnd`物件。`CClientDC`|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CClientDC::m_hWnd](#m_hwnd)|這`CClientDC`是有效的視窗的 HWND。|

## <a name="remarks"></a>備註

這表示與`CClientDC`物件相關聯的裝置內容是視窗的工作區。

如需的詳細`CClientDC`資訊, 請參閱[裝置](../../mfc/device-contexts.md)內容。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CClientDC`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="cclientdc"></a>CClientDC:: CClientDC

建立`CClientDC`物件, 以存取*pWnd*所指向之[CWnd](../../mfc/reference/cwnd-class.md)的工作區。

```
explicit CClientDC(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
裝置內容物件將會存取其工作區的視窗。

### <a name="remarks"></a>備註

此函式會呼叫 Windows 函數[GetDC](/windows/win32/api/winuser/nf-winuser-getdc)。

如果 Windows `CResourceException` `GetDC`呼叫失敗, 則會擲回例外狀況 (類型為)。 如果 Windows 已配置所有可用的裝置內容, 則可能無法使用裝置內容。 您的應用程式會在 Windows 下的任何指定時間, 競爭五個通用的顯示內容。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#42](../../mfc/codesnippet/cpp/cclientdc-class_1.cpp)]

##  <a name="m_hwnd"></a>  CClientDC::m_hWnd

用來建立`CWnd` `CClientDC`物件之指標的。 `HWND`

```
HWND m_hWnd;
```

### <a name="remarks"></a>備註

*m_hWnd*是受保護的變數。

### <a name="example"></a>範例

  請參閱[CClientDC:: CClientDC](#cclientdc)的範例。

## <a name="see-also"></a>另請參閱

[MFC 範例 MDI](../../overview/visual-cpp-samples.md)<br/>
[CDC 類別](../../mfc/reference/cdc-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDC 類別](../../mfc/reference/cdc-class.md)
