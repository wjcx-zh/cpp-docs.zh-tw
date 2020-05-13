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
ms.openlocfilehash: abe8a3220fd37a0375fcf37504c715edf4c6962e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352299"
---
# <a name="cclientdc-class"></a>CClientDC 類別

負責在施工時調用 Windows 函數[GetDC,](/windows/win32/api/winuser/nf-winuser-getdc)在銷毀時[調用釋放 DC。](/windows/win32/api/winuser/nf-winuser-releasedc)

## <a name="syntax"></a>語法

```
class CClientDC : public CDC
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CClientDC:CClientDC](#cclientdc)|建構連線到`CClientDC`的物件`CWnd`。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CClientDC:m_hWnd](#m_hwnd)|其`CClientDC`有效的視窗的 HWND。|

## <a name="remarks"></a>備註

這意味著與`CClientDC`物件關聯的設備上下文是視窗的工作區。

有關 的詳細`CClientDC`資訊 ,請參閱[裝置上下文](../../mfc/device-contexts.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CClientDC`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="cclientdccclientdc"></a><a name="cclientdc"></a>CClientDC:CClientDC

建構一個`CClientDC`物件,該物件訪問*pWnd*指向的[CWnd](../../mfc/reference/cwnd-class.md)的工作區。

```
explicit CClientDC(CWnd* pWnd);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
設備上下文對象將訪問其工作區的視窗。

### <a name="remarks"></a>備註

建構函式呼叫 Windows 函數[GetDC](/windows/win32/api/winuser/nf-winuser-getdc)。

如果 Windows`GetDC``CResourceException`調用 失敗,將引發異常(類型類型)。 如果 Windows 已分配其所有可用設備上下文,則設備上下文可能不可用。 您的應用程式競爭 Windows 下任何給定時間可用的五個常見顯示上下文。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#42](../../mfc/codesnippet/cpp/cclientdc-class_1.cpp)]

## <a name="cclientdcm_hwnd"></a><a name="m_hwnd"></a>CClientDC:m_hWnd

建`HWND`構物件的`CWnd`指標的`CClientDC`。

```
HWND m_hWnd;
```

### <a name="remarks"></a>備註

*m_hWnd*是受保護的變數。

### <a name="example"></a>範例

  請參考[CClientDC 範例:cClientDC](#cclientdc)。

## <a name="see-also"></a>另請參閱

[MFC 樣品 MDI](../../overview/visual-cpp-samples.md)<br/>
[CDC 類別](../../mfc/reference/cdc-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDC 類別](../../mfc/reference/cdc-class.md)
