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
ms.openlocfilehash: d815abbd48e1744900853fcf81dc05b6af62788c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509059"
---
# <a name="cmfcdesktopalertwndinfo-class"></a>CMFCDesktopAlertWndInfo 類別

`CMFCDesktopAlertWndInfo`類別會搭配[CMFCDesktopAlertWnd 類別](../../mfc/reference/cmfcdesktopalertwnd-class.md)。 這會指定如果桌面警示視窗出現時要顯示的控制項。

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
|[CMFCDesktopAlertWndInfo::operator =](#operator_eq)||

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMFCDesktopAlertWndInfo::m_hIcon](#m_hicon)|顯示之圖示的控制代碼。|
|[CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid)|桌面警示視窗上的連結相關聯的命令識別碼。|
|[CMFCDesktopAlertWndInfo::m_strText](#m_strtext)|會顯示在桌面警示視窗文字。|
|[CMFCDesktopAlertWndInfo::m_strURL](#m_strurl)|會顯示在桌面警示視窗中的連結。|

## <a name="remarks"></a>備註

`CMFCDesktopAlertWndInfo`類別傳遞給[cmfcdesktopalertwnd:: Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)方法，以指定的桌面警示視窗的 [預設] 對話方塊顯示的項目。 [預設] 對話方塊可以包含三個項目：

- 圖示，它會設定藉由呼叫[CMFCDesktopAlertWndInfo::m_hIcon](#m_hicon)。

- 標籤或文字訊息，它會設定藉由呼叫[CMFCDesktopAlertWndInfo::m_strText](#m_strtext)。

- 藉由呼叫設定連結[CMFCDesktopAlertWndInfo::m_strURL](#m_strurl)。 若要設定在按一下連結時執行的命令，請呼叫[CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid)。

如果預設對話方塊不足夠，您可以建立自訂對話方塊，並將它傳遞給[cmfcdesktopalertwnd:: Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)而不是使用這個類別的方法。 如需詳細資訊，請參閱 < [CMFCDesktopAlertDialog 類別](../../mfc/reference/cmfcdesktopalertdialog-class.md)。

## <a name="example"></a>範例

下列範例示範如何使用中的各種成員`CMFCDesktopAlertWndInfo`類別。 範例會示範如何將控制代碼設定為顯示圖示，會顯示在桌面警示視窗，顯示在桌面警示視窗中，連結和桌面警示視窗上的連結相關聯的命令 ID 的文字。 此範例中是屬於[桌面警示示範範例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_DesktopAlertDemo#3](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)

## <a name="requirements"></a>需求

**標頭：** afxDesktopAlertDialog.h

##  <a name="operator_eq"></a>  CMFCDesktopAlertWndInfo::operator =

如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。

```
CMFCDesktopAlertWndInfo& operator=(CMFCDesktopAlertWndInfo& src);
```

### <a name="parameters"></a>參數

[in]*src*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="m_hicon"></a>  CMFCDesktopAlertWndInfo::m_hIcon

顯示之圖示的控制代碼。

```
HICON m_hIcon;
```

### <a name="remarks"></a>備註

##  <a name="m_nurlcmdid"></a>  CMFCDesktopAlertWndInfo::m_nURLCmdID

桌面警示視窗上的連結相關聯的命令識別碼。

```
UINT m_nURLCmdID;
```

### <a name="remarks"></a>備註

當使用者按一下連結所指定的命令 ID 傳送至快顯視窗的擁有者[CMFCDesktopAlertWndInfo::m_strURL](#m_strurl)。

##  <a name="m_strtext"></a>  CMFCDesktopAlertWndInfo::m_strText

會顯示在桌面警示視窗文字。

```
CString m_strText;
```

### <a name="remarks"></a>備註

##  <a name="m_strurl"></a>  CMFCDesktopAlertWndInfo::m_strURL

會顯示在桌面警示視窗中的連結。

```
CString m_strURL;
```

### <a name="remarks"></a>備註

當使用者按一下連結時，此命令可[CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid)命令 ID 將會傳送至快顯視窗的擁有者。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertWnd 類別](../../mfc/reference/cmfcdesktopalertwnd-class.md)<br/>
[Cmfcdesktopalertwnd:: Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)<br/>
[CMFCDesktopAlertDialog 類別](../../mfc/reference/cmfcdesktopalertdialog-class.md)
