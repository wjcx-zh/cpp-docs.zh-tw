---
title: CMFCDesktopAlertDialog 類別
ms.date: 10/18/2018
f1_keywords:
- CMFCDesktopAlertDialog
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog::CreateFromParams
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog::GetDlgSize
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog::HasFocus
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog::PreTranslateMessage
helpviewer_keywords:
- CMFCDesktopAlertDialog [MFC], CreateFromParams
- CMFCDesktopAlertDialog [MFC], GetDlgSize
- CMFCDesktopAlertDialog [MFC], HasFocus
- CMFCDesktopAlertDialog [MFC], PreTranslateMessage
ms.assetid: a53c60aa-9607-485b-b826-ec64962075f6
ms.openlocfilehash: 479959e9b021255e309caf6fee02588a8cd8f1d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367647"
---
# <a name="cmfcdesktopalertdialog-class"></a>CMFCDesktopAlertDialog 類別

該`CMFCDesktopAlertDialog`類與[CMFC DesktopAlertWnd 類](../../mfc/reference/cmfcdesktopalertwnd-class.md)一起使用,以在彈出視窗中顯示自定義對話方塊。

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

## <a name="syntax"></a>語法

```
class CMFCDesktopAlertDialog : public CDialogEx
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCDesktopAlertDialog::CreateFromParams](#createfromparams)||
|[CMFCDesktopAlertDialog::GetDlgSize](#getdlgsize)||
|[CMFCDesktopAlertDialog::HasFocus](#hasfocus)||
|[CMFCDesktopAlertDialog::PreTranslateMessage](#pretranslatemessage)|(覆寫 `CDialogEx::PreTranslateMessage`。)|

### <a name="remarks"></a>備註

執行下列步驟，在快顯視窗中顯示自訂對話方塊：

1. 從 `CMFCDesktopAlertDialog` 衍生類別。

1. 在專案的資源中建立子對話方塊範本。

1. 調用[CMFCDesktopAlertwnd::](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)使用對話方塊樣本的資源 ID 和指向派生類的運行時類資訊的指標作為參數進行創建。

1. 設計自訂對話方塊以處理來自裝載控制項的所有通知，或設計裝載控制項來直接處理這些通知。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCDesktopAlertDialog](../../mfc/reference/cmfcdesktopalertdialog-class.md)

## <a name="requirements"></a>需求

**標題:** afxDesktopAlertDialog.h

## <a name="cmfcdesktopalertdialogcreatefromparams"></a><a name="createfromparams"></a>CMFC 桌面警示對話::從帕拉姆斯創建

```
BOOL CreateFromParams(
    CMFCDesktopAlertWndInfo& params,
    CMFCDesktopAlertWnd* pParent);
```

### <a name="parameters"></a>參數

[在]*參數*<br/>

[在]*p 父級*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcdesktopalertdialoggetdlgsize"></a><a name="getdlgsize"></a>CMFC 桌面警報對話::獲取Dlgsize

```
CSize GetDlgSize();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcdesktopalertdialoghasfocus"></a><a name="hasfocus"></a>CMFC 桌面警示對話::有焦點

```
BOOL HasFocus() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcdesktopalertdialogpretranslatemessage"></a><a name="pretranslatemessage"></a>CMFC 桌面警示對話::P重新翻譯訊息

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>參數

[在]*pMsg*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertWnd Class](../../mfc/reference/cmfcdesktopalertwnd-class.md)<br/>
[CMFCDesktopAlertWndInfo 類別](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)<br/>
[CDialogEx 類別](../../mfc/reference/cdialogex-class.md)
