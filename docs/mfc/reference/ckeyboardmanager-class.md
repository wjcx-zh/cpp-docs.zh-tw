---
title: CKeyboardManager 類別
ms.date: 11/04/2016
f1_keywords:
- CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager::CKeyboardManager
- AFXKEYBOARDMANAGER/CKeyboardManager::CleanUp
- AFXKEYBOARDMANAGER/CKeyboardManager::FindDefaultAccelerator
- AFXKEYBOARDMANAGER/CKeyboardManager::IsKeyHandled
- AFXKEYBOARDMANAGER/CKeyboardManager::IsKeyPrintable
- AFXKEYBOARDMANAGER/CKeyboardManager::IsShowAllAccelerators
- AFXKEYBOARDMANAGER/CKeyboardManager::LoadState
- AFXKEYBOARDMANAGER/CKeyboardManager::ResetAll
- AFXKEYBOARDMANAGER/CKeyboardManager::SaveState
- AFXKEYBOARDMANAGER/CKeyboardManager::ShowAllAccelerators
- AFXKEYBOARDMANAGER/CKeyboardManager::TranslateCharToUpper
- AFXKEYBOARDMANAGER/CKeyboardManager::UpdateAccelTable
helpviewer_keywords:
- CKeyboardManager [MFC], CKeyboardManager
- CKeyboardManager [MFC], CleanUp
- CKeyboardManager [MFC], FindDefaultAccelerator
- CKeyboardManager [MFC], IsKeyHandled
- CKeyboardManager [MFC], IsKeyPrintable
- CKeyboardManager [MFC], IsShowAllAccelerators
- CKeyboardManager [MFC], LoadState
- CKeyboardManager [MFC], ResetAll
- CKeyboardManager [MFC], SaveState
- CKeyboardManager [MFC], ShowAllAccelerators
- CKeyboardManager [MFC], TranslateCharToUpper
- CKeyboardManager [MFC], UpdateAccelTable
ms.assetid: 4809ece6-89df-4479-8b53-9bf476ee107b
ms.openlocfilehash: a8053ab33a2b49eb2c447cdaa1cb2b9e356bc696
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754923"
---
# <a name="ckeyboardmanager-class"></a>CKeyboardManager 類別

管理主框架視窗及子框架視窗的快速鍵資料表。

## <a name="syntax"></a>語法

```
class CKeyboardManager : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|||
|-|-|
|名稱|描述|
|[鍵盤管理員:鍵盤管理員](#ckeyboardmanager)|建構 `CKeyboardManager` 物件。|

### <a name="public-methods"></a>公用方法

|||
|-|-|
|名稱|描述|
|[鍵盤管理員::清理](#cleanup)|清除快速鍵表。|
|[鍵盤管理員::尋找預設加速器](#finddefaultaccelerator)|檢索指定命令和視窗的預設快速鍵。|
|[鍵盤管理員::按鍵處理](#iskeyhandled)|確定金鑰是否由加速器表處理。|
|[鍵盤管理員:可鍵列印](#iskeyprintable)|指示字元是否可列印。|
|[鍵盤管理員::是顯示所有加速器](#isshowallaccelerators)|指示選單是顯示命令的所有快速鍵還是僅顯示預設快速鍵。|
|[鍵盤管理員::載入狀態](#loadstate)|從 Windows 註冊表載入快速鍵表。|
|[鍵盤管理員::重置所有](#resetall)|從應用程式資源重新載入快速鍵表。|
|[鍵盤管理員::儲存狀態](#savestate)|將快速鍵表保存到 Windows 註冊表。|
|[鍵盤管理員::顯示所有加速器](#showallaccelerators)|指定框架是顯示所有命令的所有快速鍵,還是顯示每個命令的單個快速鍵。 此方法不會影響只有一個關聯的快捷鍵的命令。|
|[鍵盤管理員::翻譯字元上部](#translatechartoupper)|將字元轉換為其上寄存器。|
|[鍵盤管理員::更新AccelTable](#updateacceltable)|使用新的快速鍵表更新快速鍵表。|

## <a name="remarks"></a>備註

此類的成員使您能夠將快速鍵表保存到 Windows 註冊表,使用範本更新短切鍵表,並在框架視窗中尋找命令的預設快捷鍵。 此外,`CKeyboardManager`該物件允許您控制向使用者顯示快速鍵的方式。

不應手動創建`CKeyboardManager`物件。 它將由應用程式的框架自動創建。 但是,您應該在應用程式的初始化過程中調用[CWinAppEx:init 鍵盤管理器](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)。 要取得指向應用程式的鍵盤管理員的指標,請致電[CWinAppEx::get 鍵盤管理員](../../mfc/reference/cwinappex-class.md#getkeyboardmanager)。

## <a name="example"></a>範例

下面的範例展示如何從`CKeyboardManager``CWinAppEx`類檢索指向物件的指標,以及如何顯示與功能表命令關聯的所有快速鍵。 此代碼段是[自定義頁示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_CustomPages#5](../../mfc/reference/codesnippet/cpp/ckeyboardmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)

## <a name="requirements"></a>需求

**標題:** afx鍵盤管理員.h

## <a name="ckeyboardmanagerckeyboardmanager"></a><a name="ckeyboardmanager"></a>鍵盤管理員:鍵盤管理員

建構 `CKeyboardManager` 物件。

```
CKeyboardManager();
```

### <a name="remarks"></a>備註

在大多數情況下,您不必直接創建`CKeyboardManager`。 默認情況下,框架會為您創建一個。 要取得指向的`CKeyboardManager`指標,請致電[CWinAppEx::取得鍵盤管理器](../../mfc/reference/cwinappex-class.md#getkeyboardmanager)。 如果手動創建一個,則必須使用[方法 CWinAppEx::init鍵盤管理器](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)初始化它。

## <a name="ckeyboardmanagercleanup"></a><a name="cleanup"></a>鍵盤管理員::清理

釋放`CKeyboardManager`資源並清除所有快速鍵映射。

```
static void CleanUp();
```

### <a name="remarks"></a>備註

有關快捷鍵的詳細資訊,請參閱[鍵盤和滑鼠自訂](../../mfc/keyboard-and-mouse-customization.md)。

當應用程式退出時,您不必調用此功能,因為框架會在應用程式退出期間自動調用它。

## <a name="ckeyboardmanagerfinddefaultaccelerator"></a><a name="finddefaultaccelerator"></a>鍵盤管理員::尋找預設加速器

檢索指定命令和視窗的預設快速鍵。

```
static BOOL FindDefaultAccelerator(
    UINT uiCmd,
    CString& str,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>參數

*烏伊Cmd*<br/>
[在]命令識別碼。

*Str*<br/>
[出]對物件的參考`CString`。

*pWndFrame*<br/>
[在]指向框架視窗的指標。

*bIsDefaultFrame*<br/>
[在]指定框架視窗是否為預設框架視窗。

### <a name="return-value"></a>傳回值

如果找到快捷方式,則非零;否則 0。

### <a name="remarks"></a>備註

此方法查找*uiCmd*指定的命令並檢索預設快速鍵。 然後,該方法獲取與此快速鍵關聯的字串,並將值寫入*str*參數。

## <a name="ckeyboardmanageriskeyhandled"></a><a name="iskeyhandled"></a>鍵盤管理員::按鍵處理

確定指定的密鑰是否由[CKeyboardManager 類](../../mfc/reference/ckeyboardmanager-class.md)處理。

```
static BOOL __stdcall IsKeyHandled(
    WORD nKey,
    BYTE fVirt,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*N 鍵*|[在]要檢查的鍵。|
|*fVirt*|[在]指定快速鍵的行為。 有關可能值的清單,請參閱[ACCEL 結構](/windows/win32/api/winuser/ns-winuser-accel)。|
|*pWndFrame*|[在]框架視窗。 此方法確定是否在此幀中處理快速鍵。|
|*bIsDefaultFrame*|[在]指示*pWndFrame*是否為預設幀視窗的布爾參數。|

### <a name="return-value"></a>傳回值

如果處理快捷鍵,則為 TRUE。 如果未處理金鑰或*pWndFrame*為 NULL,則 FALSE。

### <a name="remarks"></a>備註

輸入參數必須匹配*nKey*和*fVirt*的加速器表中的項目,以確定是否在*pWndFrame*中處理快速鍵。

## <a name="ckeyboardmanageriskeyprintable"></a><a name="iskeyprintable"></a>鍵盤管理員:可鍵列印

指示字元是否可列印。

```
static BOOL __stdcall IsKeyPrintable(const UINT nChar);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*n查爾*|[在]此方法檢查的字元。|

### <a name="return-value"></a>傳回值

如果字元可列印,則為非零,如果不是,則為零。

### <a name="remarks"></a>備註

如果對[GetKeyboardState](/windows/win32/api/winuser/nf-winuser-getkeyboardstate)的呼叫失敗,此方法將失敗。

## <a name="ckeyboardmanagerisshowallaccelerators"></a><a name="isshowallaccelerators"></a>鍵盤管理員::是顯示所有加速器

指示功能表是顯示與功能表命令關聯的所有快捷鍵,還是僅顯示預設快速鍵。

```
static BOOL IsShowAllAccelerators();
```

### <a name="return-value"></a>傳回值

如果應用程式列出了功能表命令的所有快捷鍵,則非零;如果應用程式僅顯示默認快速鍵,則為 0。

### <a name="remarks"></a>備註

應用程式在功能表列中列出功能表命令的快捷鍵。 使用函數[CKeyboardManager::ShowAllAccelerators](#showallaccelerators)控制應用程式是否列出所有快速鍵還是僅列出預設快速鍵。

## <a name="ckeyboardmanagerloadstate"></a><a name="loadstate"></a>鍵盤管理員::載入狀態

從 Windows 註冊表載入快速鍵表。

```
BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>參數

*lpsz 設定檔名稱*<br/>
[在]保存`CKeyboardManager`數據的註冊錶路徑。

*pDefaultFrame*<br/>
[在]指向幀視窗的指標,用於默認視窗。

### <a name="return-value"></a>傳回值

如果狀態已成功載入,則為非零,否則為 0。

### <a name="remarks"></a>備註

如果*lpszProfileName*參數為 NULL,則此`CKeyboardManager`方法將檢查 資料的預設註冊表位置。 默認註冊表位置由[CWinAppEx 類](../../mfc/reference/cwinappex-class.md)指定。 數據以前必須使用方法[CKeyboardManager::::保存狀態](#savestate)編寫。

如果不指定預設視窗,將使用應用程式的主框架視窗。

## <a name="ckeyboardmanagerresetall"></a><a name="resetall"></a>鍵盤管理員::重置所有

從應用程式資源重新載入快速鍵表。

```cpp
void ResetAll();
```

### <a name="remarks"></a>備註

此函數清除存儲在實例中的`CKeyboardManager`快捷方式。 然後,它將從應用程式資源重新載入鍵盤管理員的狀態。

## <a name="ckeyboardmanagersavestate"></a><a name="savestate"></a>鍵盤管理員::儲存狀態

將快速鍵表保存到 Windows 註冊表。

```
BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>參數

*lpsz 設定檔名稱*<br/>
[在]用於保存狀態的`CKeyboardManager`註冊錶路徑。

*pDefaultFrame*<br/>
[在]指向幀視窗的指標,該指標將成為默認視窗。

### <a name="return-value"></a>傳回值

如果鍵盤管理器狀態已成功保存,則為非零,否則為 0。

### <a name="remarks"></a>備註

如果*lpszProfileName*參數為 NULL,則`CKeyboardManager`此方法將 狀態寫入[CWinAppEx 類](../../mfc/reference/cwinappex-class.md)指定的預設位置。 如果指定位置,則可以稍後使用方法[CKeyboardManager:::LoadState](#loadstate)載入數據。

如果不指定預設視窗,則主框架視窗將用作預設視窗。

## <a name="ckeyboardmanagershowallaccelerators"></a><a name="showallaccelerators"></a>鍵盤管理員::顯示所有加速器

顯示與功能表命令關聯的所有快速鍵。

```
static void ShowAllAccelerators(
    BOOL bShowAll = TRUE,
    LPCTSTR lpszDelimiter = _afxDefaultAcceleratorDelimiter);
```

### <a name="parameters"></a>參數

*b 顯示所有*<br/>
[在]如果為 TRUE,將顯示所有快速鍵。 如果 FALSE,則僅顯示第一個快速鍵。

*lpsz 分隔符*<br/>
[在]要在快速鍵之間插入的字串。 如果只顯示一個快速鍵,則此分隔符不起作用。

### <a name="remarks"></a>備註

默認情況下,如果命令有多個與其關聯的快捷鍵,則僅顯示第一個快速鍵。 此功能使您能夠列出與所有命令關聯的所有快捷鍵。

快捷鍵將列在功能表欄中命令旁邊。 如果顯示所有快捷鍵,*則 lpszDelimiter*提供的字串將分隔各個快捷鍵。

## <a name="ckeyboardmanagertranslatechartoupper"></a><a name="translatechartoupper"></a>鍵盤管理員::翻譯字元上部

將字元轉換為其上寄存器。

```
static UINT TranslateCharToUpper(const UINT nChar);
```

### <a name="parameters"></a>參數

*n查爾*<br/>
[在]要轉換的字元。

### <a name="return-value"></a>傳回值

作為輸入參數的上部寄存器的字元。

## <a name="ckeyboardmanagerupdateacceltable"></a><a name="updateacceltable"></a>鍵盤管理員::更新AccelTable

使用新的快速鍵表更新快速鍵表。

```
BOOL UpdateAccelTable(
    CMultiDocTemplate* pTemplate,
    LPACCEL lpAccel,
    int nSize,
    CFrameWnd* pDefaultFrame = NULL);

BOOL UpdateAccelTable(
    CMultiDocTemplate* pTemplate,
    HACCEL hAccelNew,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>參數

*pTemplate*<br/>
[在]指向文檔範本的指標。

*lpAccel*<br/>
[在]指向新快速鍵的指標。

*nSize*<br/>
[在]新快捷方式表的大小。

*pDefaultFrame*<br/>
[在]指向預設幀視窗的指標。

*哈克爾新*<br/>
[在]新快捷方式表的句柄。

### <a name="return-value"></a>傳回值

如果方法成功,則非零;否則 0。

### <a name="remarks"></a>備註

使用此函數可以將現有快捷表替換為多個框架視窗物件的新快速鍵。 該函數接收文檔範本作為參數,以獲取對連接到給定文檔範本的所有幀視窗對象的訪問。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)<br/>
[CWinAppEx::Init鍵盤管理員](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)<br/>
[鍵盤和滑鼠自訂](../../mfc/keyboard-and-mouse-customization.md)
