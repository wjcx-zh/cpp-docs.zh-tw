---
title: CMFCDesktopAlertDialog 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDesktopAlertDialog
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog::CreateFromParams
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog::GetDlgSize
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog::HasFocus
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog::PreTranslateMessage
dev_langs:
- C++
helpviewer_keywords:
- CMFCDesktopAlertDialog [MFC], CreateFromParams
- CMFCDesktopAlertDialog [MFC], GetDlgSize
- CMFCDesktopAlertDialog [MFC], HasFocus
- CMFCDesktopAlertDialog [MFC], PreTranslateMessage
ms.assetid: a53c60aa-9607-485b-b826-ec64962075f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7045692504fa2a33fc6ddf8485038193ea416b06
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377418"
---
# <a name="cmfcdesktopalertdialog-class"></a>CMFCDesktopAlertDialog 類別

`CMFCDesktopAlertDialog`類別可搭配使用[CMFCDesktopAlertWnd 類別](../../mfc/reference/cmfcdesktopalertwnd-class.md)快顯視窗中顯示自訂對話方塊。

如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。

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

1. 呼叫[cmfcdesktopalertwnd:: Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)的對話方塊範本和衍生類別的執行階段類別資訊，做為參數指向的資源識別碼。

1. 設計自訂對話方塊以處理來自裝載控制項的所有通知，或設計裝載控制項來直接處理這些通知。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCDesktopAlertDialog](../../mfc/reference/cmfcdesktopalertdialog-class.md)

## <a name="requirements"></a>需求

**標頭：** afxDesktopAlertDialog.h

##  <a name="createfromparams"></a>  CMFCDesktopAlertDialog::CreateFromParams


```
BOOL CreateFromParams(
    CMFCDesktopAlertWndInfo& params,
    CMFCDesktopAlertWnd* pParent);
```

### <a name="parameters"></a>參數

*params*<br/>
[in][in]*pParent*

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="getdlgsize"></a>  CMFCDesktopAlertDialog::GetDlgSize


```
CSize GetDlgSize();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="hasfocus"></a>  CMFCDesktopAlertDialog::HasFocus


```
BOOL HasFocus() const;
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="pretranslatemessage"></a>  CMFCDesktopAlertDialog::PreTranslateMessage


```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>參數

[in]*pMsg*

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertWnd 類別](../../mfc/reference/cmfcdesktopalertwnd-class.md)<br/>
[CMFCDesktopAlertWndInfo 類別](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)<br/>
[CDialogEx 類別](../../mfc/reference/cdialogex-class.md)
