---
title: CMFCDesktopAlertWnd Class
ms.date: 10/18/2018
f1_keywords:
- CMFCDesktopAlertWnd
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::Create
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAnimationSpeed
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAnimationType
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAutoCloseTime
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetCaptionHeight
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetDialogSize
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetLastPos
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetTransparency
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::HasSmallCaption
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnBeforeShow
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnClickLinkButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnCommand
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnDraw
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::ProcessCommand
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAnimationSpeed
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAnimationType
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAutoCloseTime
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetSmallCaption
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetTransparency
helpviewer_keywords:
- CMFCDesktopAlertWnd [MFC], Create
- CMFCDesktopAlertWnd [MFC], GetAnimationSpeed
- CMFCDesktopAlertWnd [MFC], GetAnimationType
- CMFCDesktopAlertWnd [MFC], GetAutoCloseTime
- CMFCDesktopAlertWnd [MFC], GetCaptionHeight
- CMFCDesktopAlertWnd [MFC], GetDialogSize
- CMFCDesktopAlertWnd [MFC], GetLastPos
- CMFCDesktopAlertWnd [MFC], GetTransparency
- CMFCDesktopAlertWnd [MFC], HasSmallCaption
- CMFCDesktopAlertWnd [MFC], OnBeforeShow
- CMFCDesktopAlertWnd [MFC], OnClickLinkButton
- CMFCDesktopAlertWnd [MFC], OnCommand
- CMFCDesktopAlertWnd [MFC], OnDraw
- CMFCDesktopAlertWnd [MFC], ProcessCommand
- CMFCDesktopAlertWnd [MFC], SetAnimationSpeed
- CMFCDesktopAlertWnd [MFC], SetAnimationType
- CMFCDesktopAlertWnd [MFC], SetAutoCloseTime
- CMFCDesktopAlertWnd [MFC], SetSmallCaption
- CMFCDesktopAlertWnd [MFC], SetTransparency
ms.assetid: 73a2dd7b-ea84-4ae2-9830-7cf6e8dd2425
ms.openlocfilehash: cf453b6e69f012bedaf0bd91b5eaf11f7caffa12
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752454"
---
# <a name="cmfcdesktopalertwnd-class"></a>CMFCDesktopAlertWnd Class

類`CMFCDesktopAlertWnd`實現無模式對話方塊的功能,該對話框出現在螢幕上,以通知用戶有關事件。

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

## <a name="syntax"></a>語法

```
class CMFCDesktopAlertWnd : public CWnd
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFC 桌面警示::建立](#create)|建立並初始化桌面警報視窗。|
|[CMFC桌面警示::取得動畫速度](#getanimationspeed)|返回動畫速度。|
|[CMFC 桌面警示::取得動畫類型](#getanimationtype)|返回動畫類型。|
|[CMFC 桌面警示::抓取自動關閉時間](#getautoclosetime)|返回自動關閉超時。|
|[CMFC 桌面警示::取得標題高度](#getcaptionheight)|返回標題的高度。|
|[CMFC 桌面警示::取得對話大小](#getdialogsize)||
|[CMFC 桌面警示::取得最後一個Pos](#getlastpos)|返回螢幕上桌面警報視窗的最後一個有效位置。|
|[CMFC桌面警示::獲取透明度](#gettransparency)|返回透明度級別。|
|[CMFC 桌面警示::有小標題](#hassmallcaption)|確定桌面警報視窗是否隨小標題一起顯示。|
|[CMFC 桌面警示::在顯示前開啟](#onbeforeshow)||
|[CMFC 桌面警示::點擊連結按鈕](#onclicklinkbutton)|當用戶按下桌面警報功能表上的連結按鈕時,由框架調用。|
|[CMFC 桌面警示::在命令上](#oncommand)|當使用者從功能表中選擇專案、子控制件發送通知訊息或翻譯快速鍵時,框架將調用此成員函數。 (涵蓋[CWnd:onCommand](../../mfc/reference/cwnd-class.md#oncommand).)|
|[CMFC 桌面警報::開機](#ondraw)||
|[CMFC 桌面警示::Process 命令](#processcommand)||
|[CMFC 桌面警示::設定動畫速度](#setanimationspeed)|設置新的動畫速度。|
|[CMFC 桌面警示::設定動畫類型](#setanimationtype)|設置動畫類型。|
|[CMFC 桌面警示::設定自動關閉時間](#setautoclosetime)|設置自動關閉超時。|
|[CMFC 桌面警示::設定小標題](#setsmallcaption)|在小標題和普通字幕之間切換。|
|[CMFC 桌面警示::設定透明度](#settransparency)|設置透明度級別。|

## <a name="remarks"></a>備註

桌面警報視窗可以是透明的,它可以顯示動畫效果,並且它可以消失(在指定的延遲之後,或者當用戶通過按一下關閉按鈕將其關閉時)。

桌面警報視窗還可以包含預設對話框,該對話框又包含圖示、消息文本(標籤)和連結。 或者,桌面警報視窗可以包含來自應用程式資源的自定義對話方塊。

分兩步創建桌面警報視窗。 首先,調用構造函數構造`CMFCDesktopAlertWnd`物件。 其次,調用[CMFC DesktopAlertwnd::創建](#create)成員函數以創建視窗並將`CMFCDesktopAlertWnd`其附加到 物件。

該`CMFCDesktopAlertWnd`物件創建一個特殊的子對話框,該對話框填充桌面警報視窗的工作區。 該對話框擁有位於它上的所有控制項。

要在彈出視窗上顯示自訂對話框,請按照以下步驟操作:

1. 從 `CMFCDesktopAlertDialog` 衍生類別。

1. 在資源中創建子對話框範本。

1. 調用[CMFCDesktopAlertwnd::](#create)使用對話方塊樣本的資源 ID 和指向派生類的運行時類資訊的指標進行創建。

1. 對自定義對話框進行程式設計,以處理來自託管控件的所有通知,或對託管控件進行程式設計以直接處理這些通知。

使用以下函數控制桌面警示視窗的行為:

- 以呼叫[CMFC 桌面警示的Wnd::設定動畫類型來設定動畫類型](#setanimationtype)。 有效選項包括展開、滑動和淡入淡出。

- 以呼叫[CMFC 桌面警示 Wnd 設定動畫的畫面速度::設定動畫速度](#setanimationspeed)。

- 通過調用[CMFC 桌面AlertWnd::設置透明度](#settransparency)來設置透明度級別。

- 通過調用[CMFCDesktopAlertwnd::setSmallCaption,](#setsmallcaption)將標題的大小更改為小。 小標題高 7 圖元。

## <a name="example"></a>範例

下面的示例說明了如何使用類中`CMFCDesktopAlertWnd`的各種方法來`CMFCDesktopAlertWnd`配置 物件。 該示例演示如何設置動畫類型、設置彈出視窗的透明度、指定警報視窗顯示小標題以及設置警報視窗自動關閉之前經過的時間。 該示例還演示如何創建和初始化桌面警報視窗。 此代碼段是[桌面警報演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_DesktopAlertDemo#1](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwnd-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md)

## <a name="requirements"></a>需求

**標題:** afxDesktopAlertwnd.h

## <a name="cmfcdesktopalertwndcreate"></a><a name="create"></a>CMFC 桌面警示::建立

建立並初始化桌面警報視窗。

```
virtual BOOL Create(
    CWnd* pWndOwner,
    UINT uiDlgResID,
    HMENU hMenu = NULL,
    CPoint ptPos = CPoint(-1,-1),
    CRuntimeClass* pRTIDlgBar = RUNTIME_CLASS(CMFCDesktopAlertDialog));

virtual BOOL Create(
    CWnd* pWndOwner,
    CMFCDesktopAlertWndInfo& params,
    HMENU hMenu = NULL,
    CPoint ptPos = CPoint(-1,-1));
```

### <a name="parameters"></a>參數

*pwndOwner*<br/>
[進出]指定警示視窗的擁有者。 然後,該擁有者將收到桌面警報視窗的所有通知。 此值不能為 NULL。

*烏伊德格雷斯ID*<br/>
[在]指定警示視窗的資源代碼。

*hMenu*<br/>
[在]指定使用者按下功能表按鈕時顯示的功能表。 如果為 NULL,則不顯示選單按鈕。

*ptPos*<br/>
[在]使用螢幕座標指定顯示警報視窗的初始位置。 如果此參數為 (-1, -1),則警報視窗將顯示在螢幕的右下角。

*pRTIDlgBar*<br/>
[在]自定義對話框類的運行時類資訊,該類涵蓋警報視窗的工作區。

*params*<br/>
[在]指定用於建立警報視窗的參數。

### <a name="return-value"></a>傳回值

如果警報視窗已成功創建,則為 TRUE;如果警報視窗已成功創建,則為 TRUE。否則,FALSE。

### <a name="remarks"></a>備註

調用此方法以創建警報視窗。 警報視窗的工作區包含一個子對話框,該對話框承載向用戶顯示的所有控制項。

第一個方法重載創建一個警報視窗,其中包含從應用程式的資源載入的子對話框。 第一種方法重載還可以為自定義對話框類指定運行時類資訊。

第二種方法重載將創建一個包含預設控制項的警報視窗。 您可以通過修改[CMFC 桌面AlertWndinfo 類](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)來指定要顯示的控制項。

## <a name="cmfcdesktopalertwndgetanimationspeed"></a><a name="getanimationspeed"></a>CMFC桌面警示::取得動畫速度

返回動畫速度。

```
UINT GetAnimationSpeed() const;
```

### <a name="return-value"></a>傳回值

警報視窗的動畫速度(以毫秒為單位)。

### <a name="remarks"></a>備註

動畫速度描述警報窗口打開和關閉的速度。

## <a name="cmfcdesktopalertwndgetanimationtype"></a><a name="getanimationtype"></a>CMFC 桌面警示::取得動畫類型

返回動畫類型。

```
CMFCPopupMenu::ANIMATION_TYPE GetAnimationType();
```

### <a name="return-value"></a>傳回值

以下動畫類型之一:

- NO_ANIMATION

- 展開

- 投影片

- 褪色

- SYSTEM_DEFAULT_ANIMATION

## <a name="cmfcdesktopalertwndgetautoclosetime"></a><a name="getautoclosetime"></a>CMFC 桌面警示::抓取自動關閉時間

返回自動關閉超時。

```
int GetAutoCloseTime() const;
```

### <a name="return-value"></a>傳回值

警報視窗將自動關閉的時間(以毫秒為單位)。

### <a name="remarks"></a>備註

使用此方法可確定警報視窗自動關閉之前應經過多長時間。

## <a name="cmfcdesktopalertwndgetcaptionheight"></a><a name="getcaptionheight"></a>CMFC 桌面警示::取得標題高度

返回標題的高度。

```
virtual int GetCaptionHeight();
```

### <a name="return-value"></a>傳回值

標題的高度(以像素為單位)。

### <a name="remarks"></a>備註

可以在派生類中重寫此方法。 預設實現:如果彈出視窗應顯示小標題或從 Windows API`GetSystemMetrics(SM_CYSMCAPTION)`函數 獲取的值,則返回小標題高度值(7 圖元)。

## <a name="cmfcdesktopalertwndgetlastpos"></a><a name="getlastpos"></a>CMFC 桌面警示::取得最後一個Pos

返回螢幕上桌面警報視窗的最後位置。

```
CPoint GetLastPos() const;
```

### <a name="return-value"></a>傳回值

螢幕座標中的一個點。

### <a name="remarks"></a>備註

此方法返回螢幕上警報視窗的最後一個有效位置。

## <a name="cmfcdesktopalertwndgettransparency"></a><a name="gettransparency"></a>CMFC桌面警示::獲取透明度

返回透明度級別。

```
BYTE GetTransparency() const;
```

### <a name="return-value"></a>傳回值

透明度級別介於 0 和 255 之間,包括。 值越大,視窗越不透明。

### <a name="remarks"></a>備註

使用此方法檢索警報視窗的當前透明度級別。

## <a name="cmfcdesktopalertwndhassmallcaption"></a><a name="hassmallcaption"></a>CMFC 桌面警示::有小標題

確定桌面警報視窗是否具有小標題或常規大小標題。

```
BOOL HasSmallCaption() const;
```

### <a name="return-value"></a>傳回值

如果彈出視窗顯示帶有小標題,則為 TRUE;如果彈出視窗顯示時,則為 TRUE。如果彈出視窗顯示帶有常規大小的標題,則 FALSE。

### <a name="remarks"></a>備註

使用此方法可確定彈出視窗是否具有小標題或常規大小標題。 默認情況下,小標題高 7 圖元。 您可以通過調用 Windows API 函數`GetSystemMetrics(SM_CYCAPTION)`獲得一般大小標題的高度。

## <a name="cmfcdesktopalertwndonbeforeshow"></a><a name="onbeforeshow"></a>CMFC 桌面警示::在顯示前開啟

```
virtual BOOL OnBeforeShow(CPoint&);
```

### <a name="parameters"></a>參數

[在]*CPoint&*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcdesktopalertwndonclicklinkbutton"></a><a name="onclicklinkbutton"></a>CMFC 桌面警示::點擊連結按鈕

當用戶按下桌面警報功能表上的連結按鈕時,由框架調用。

```
virtual BOOL OnClickLinkButton(UINT uiCmdID);
```

### <a name="parameters"></a>參數

*烏伊CmdID*<br/>
[在]不使用此參數。

### <a name="return-value"></a>傳回值

一律為 FALSE。

### <a name="remarks"></a>備註

如果要在用戶按一下警報視窗中的連結時收到通知,請在派生類中覆蓋此方法。

## <a name="cmfcdesktopalertwndoncommand"></a><a name="oncommand"></a>CMFC 桌面警示::在命令上

```
virtual BOOL OnCommand(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>參數

[在]*wParam*<br/>

[在]*lParam*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcdesktopalertwndondraw"></a><a name="ondraw"></a>CMFC 桌面警報::開機

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>參數

[在]*pDC*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcdesktopalertwndprocesscommand"></a><a name="processcommand"></a>CMFC 桌面警示::Process 命令

```
BOOL ProcessCommand(HWND hwnd);
```

### <a name="parameters"></a>參數

[在]*霍恩德*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfcdesktopalertwndsetanimationspeed"></a><a name="setanimationspeed"></a>CMFC 桌面警示::設定動畫速度

設置新的動畫速度。

```cpp
void SetAnimationSpeed(UINT nSpeed);
```

### <a name="parameters"></a>參數

*n速度*<br/>
[在]指定新的動畫速度(以毫秒為單位)。

### <a name="remarks"></a>備註

調用此方法以設置警報視窗的動畫速度。 默認動畫速度為 30 毫秒。

## <a name="cmfcdesktopalertwndsetanimationtype"></a><a name="setanimationtype"></a>CMFC 桌面警示::設定動畫類型

設置動畫類型。

```cpp
void SetAnimationType(CMFCPopupMenu::ANIMATION_TYPE type);
```

### <a name="parameters"></a>參數

*type*<br/>
[在]指定動畫類型。

### <a name="remarks"></a>備註

調用此方法以設置動畫類型。 您可以指定下列其中一個值：

- NO_ANIMATION

- 展開

- 投影片

- 褪色

- SYSTEM_DEFAULT_ANIMATION

## <a name="cmfcdesktopalertwndsetautoclosetime"></a><a name="setautoclosetime"></a>CMFC 桌面警示::設定自動關閉時間

設置自動關閉超時。

```cpp
void SetAutoCloseTime(int nTime);
```

### <a name="parameters"></a>參數

*nTime*<br/>
[在]警報視窗自動關閉之前經過的時間(以毫秒為單位)。

### <a name="remarks"></a>備註

如果使用者不與窗互,警報視窗在指定時間后自動關閉。

## <a name="cmfcdesktopalertwndsetsmallcaption"></a><a name="setsmallcaption"></a>CMFC 桌面警示::設定小標題

在小尺寸和常規大小字幕之間切換。

```cpp
void SetSmallCaption(BOOL bSmallCaption = TRUE);
```

### <a name="parameters"></a>參數

*b 小標題*<br/>
[在]TRUE 指定警報視窗顯示一個小標題;否則,FALSE 指定警報視窗顯示常規大小的標題。

### <a name="remarks"></a>備註

呼叫此方法以顯示小大小或常規大小的標題。 默認情況下,小標題高 7 圖元。 您可以通過調用 Windows API 函數`GetSystemMetrics(SM_CYCAPTION)`來取得一般標題的大小。

## <a name="cmfcdesktopalertwndsettransparency"></a><a name="settransparency"></a>CMFC 桌面警示::設定透明度

設置彈出視窗的透明度級別。

```cpp
void SetTransparency(BYTE nTransparency);
```

### <a name="parameters"></a>參數

*n 透明*<br/>
[在]指定透明度級別。 此值必須在 0 和 255 之間(包括)。 值越大,視窗越不透明。

### <a name="remarks"></a>備註

調用此函數以設置彈出視窗的透明度級別。

## <a name="cmfcdesktopalertwndgetdialogsize"></a><a name="getdialogsize"></a>CMFC 桌面警示::取得對話大小

```
virtual CSize GetDialogSize();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertWndInfo 類別](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)<br/>
[CMFCDesktopAlertDialog 類別](../../mfc/reference/cmfcdesktopalertdialog-class.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)
