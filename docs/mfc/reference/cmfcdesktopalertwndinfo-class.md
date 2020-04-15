---
title: CMFCDesktopAlertWndInfo 類別
ms.date: 10/18/2018
f1_keywords:
- CMFCDesktopAlertWndInfo
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_hIcon
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_nURLCmdID
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_strText
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_strURL
helpviewer_keywords:
- CMFCDesktopAlertWndInfo [MFC], m_hIcon
- CMFCDesktopAlertWndInfo [MFC], m_nURLCmdID
- CMFCDesktopAlertWndInfo [MFC], m_strText
- CMFCDesktopAlertWndInfo [MFC], m_strURL
ms.assetid: 5c9bb84e-6c96-4748-8e74-6951b6ae8e84
ms.openlocfilehash: f51c1b75e0c096a34b190e36e097aaca4109b5f8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367592"
---
# <a name="cmfcdesktopalertwndinfo-class"></a>CMFCDesktopAlertWndInfo 類別

該`CMFCDesktopAlertWndInfo`類與[CMFC 桌面警報類](../../mfc/reference/cmfcdesktopalertwnd-class.md)一起使用。 這會指定如果桌面警示視窗出現時要顯示的控制項。

## <a name="syntax"></a>語法

```
class CMFCDesktopAlertWndInfo
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|`CMFCDesktopAlertWndInfo::~CMFCDesktopAlertWndInfo`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFC桌面警報資訊::操作員*](#operator_eq)||

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMFC桌面警報資訊::m_hIcon](#m_hicon)|顯示的圖示的句柄。|
|[CMFC 桌面警報資訊::m_nURLCmdID](#m_nurlcmdid)|與桌面警報視窗中的連結關聯的命令 ID。|
|[CMFC桌面警報資訊::m_strText](#m_strtext)|桌面警示視窗中顯示的文字。|
|[CMFC桌面警報資訊::m_strURL](#m_strurl)|桌面警示視窗中顯示的連結。|

## <a name="remarks"></a>備註

類`CMFCDesktopAlertWndInfo`將傳遞給[CMFCDesktopAlertWnd::創建](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)方法來指定桌面警報視窗的默認對話框中顯示的元素。 預設對話框可以包含三個專案:

- 一個圖示,它通過調用[CMFCDesktopAlertWndinfo::m_hIcon](#m_hicon)設置。

- 標籤或簡訊,通過調用[CMFCDesktopAlertWndinfo:m_strText](#m_strtext)設置。

- 連結,通過調用[CMFCDesktopAlertWndinfo:m_strURL](#m_strurl)設置。 要設定按下連結時執行的指令,請致電[CMFCDesktopAlertWndinfo::m_nURLCmdID](#m_nurlcmdid)。

如果默認對話框不夠,您可以創建自定義對話框並將其傳遞給[CMFCDesktopAlertWnd::創建](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)方法,而不是使用此類。 有關詳細資訊,請參閱[CMFC 桌面警示對話類別](../../mfc/reference/cmfcdesktopalertdialog-class.md)。

## <a name="example"></a>範例

下面的範例展示如何在`CMFCDesktopAlertWndInfo`類中使用各種成員。 此範例展示如何將句柄設定為顯示的圖示、桌面警報視窗中顯示的文本、桌面警報視窗中顯示的連結以及與桌面警報視窗中的連結關聯的命令 ID。 此示例是[桌面警報演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_DesktopAlertDemo#3](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)

## <a name="requirements"></a>需求

**標題:** afxDesktopAlertDialog.h

## <a name="cmfcdesktopalertwndinfooperator"></a><a name="operator_eq"></a>CMFC桌面警報資訊::操作員*

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

```
CMFCDesktopAlertWndInfo& operator=(CMFCDesktopAlertWndInfo& src);
```

### <a name="parameters"></a>參數

[在]*斯爾克*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcdesktopalertwndinfom_hicon"></a><a name="m_hicon"></a>CMFC桌面警報資訊::m_hIcon

顯示的圖示的句柄。

```
HICON m_hIcon;
```

### <a name="remarks"></a>備註

## <a name="cmfcdesktopalertwndinfom_nurlcmdid"></a><a name="m_nurlcmdid"></a>CMFC 桌面警報資訊::m_nURLCmdID

與桌面警報視窗中的連結關聯的命令 ID。

```
UINT m_nURLCmdID;
```

### <a name="remarks"></a>備註

當使用者按下[CMFCDesktopAlertWndinfo 指定的](#m_strurl)連結時,命令 ID 將發送給彈出視窗的擁有者:m_strURL 。

## <a name="cmfcdesktopalertwndinfom_strtext"></a><a name="m_strtext"></a>CMFC桌面警報資訊::m_strText

桌面警示視窗中顯示的文字。

```
CString m_strText;
```

### <a name="remarks"></a>備註

## <a name="cmfcdesktopalertwndinfom_strurl"></a><a name="m_strurl"></a>CMFC桌面警報資訊::m_strURL

桌面警示視窗中顯示的連結。

```
CString m_strURL;
```

### <a name="remarks"></a>備註

當用戶按一下該連結時,具有[CMFCDesktopAlertWndinfo:m_nURLCmdID](#m_nurlcmdid)命令 ID 的命令將發送給彈出視窗的擁有者。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertWnd Class](../../mfc/reference/cmfcdesktopalertwnd-class.md)<br/>
[CMFC 桌面警示::建立](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)<br/>
[CMFCDesktopAlertDialog 類別](../../mfc/reference/cmfcdesktopalertdialog-class.md)
