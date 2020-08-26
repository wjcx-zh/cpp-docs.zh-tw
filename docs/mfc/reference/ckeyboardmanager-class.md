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
ms.openlocfilehash: e67bbb18b6a87edfaa4bc4c410ec28eb613ed51d
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841489"
---
# <a name="ckeyboardmanager-class"></a>CKeyboardManager 類別

管理主框架視窗及子框架視窗的快速鍵資料表。

## <a name="syntax"></a>語法

```
class CKeyboardManager : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|-|-|
|[CKeyboardManager：： CKeyboardManager](#ckeyboardmanager)|建構 `CKeyboardManager` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|-|-|
|[CKeyboardManager：：清理](#cleanup)|清除快速鍵資料表。|
|[CKeyboardManager：： FindDefaultAccelerator](#finddefaultaccelerator)|抓取指定命令和視窗的預設快速鍵。|
|[CKeyboardManager：： IsKeyHandled](#iskeyhandled)|判斷索引鍵是否由快速鍵對應表處理。|
|[CKeyboardManager：： IsKeyPrintable](#iskeyprintable)|指出字元是否可列印。|
|[CKeyboardManager：： IsShowAllAccelerators](#isshowallaccelerators)|指出功能表是否顯示命令的所有快速鍵，或僅顯示預設快速鍵。|
|[CKeyboardManager：： LoadState](#loadstate)|從 Windows 登錄載入快速鍵資料表。|
|[CKeyboardManager：： ResetAll](#resetall)|從應用程式資源重載快速鍵資料表。|
|[CKeyboardManager：： SaveState](#savestate)|將快速鍵表儲存至 Windows 登錄。|
|[CKeyboardManager：： ShowAllAccelerators](#showallaccelerators)|指定架構是否顯示所有命令的所有快速鍵，或每個命令的單一快速鍵。 這個方法不會影響只有一個相關聯快速鍵的命令。|
|[CKeyboardManager：： TranslateCharToUpper](#translatechartoupper)|將字元轉換成其上方的暫存器。|
|[CKeyboardManager：： UpdateAccelTable](#updateacceltable)|以新的快速鍵資料表更新快速鍵資料表。|

## <a name="remarks"></a>備註

此類別的成員可讓您儲存和載入快速鍵資料表至 Windows 登錄、使用範本更新簡短的索引鍵資料表，以及在框架視窗中尋找命令的預設快速鍵。 此外， `CKeyboardManager` 物件也可讓您控制如何向使用者顯示快速鍵。

您不應該手動建立 `CKeyboardManager` 物件。 它會由您應用程式的架構自動建立。 不過，您應該在應用程式的初始化程式期間呼叫 [CWinAppEx：： InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager) 。 若要取得應用程式的鍵盤管理員指標，請呼叫 [CWinAppEx：： GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager)。

## <a name="example"></a>範例

下列範例示範如何 `CKeyboardManager` 從類別取出物件的指標 `CWinAppEx` ，以及如何顯示與功能表命令相關聯的所有快速鍵。 此程式碼片段是 [自訂頁面範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_CustomPages#5](../../mfc/reference/codesnippet/cpp/ckeyboardmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)

## <a name="requirements"></a>規格需求

**標頭：** afxkeyboardmanager。h

## <a name="ckeyboardmanagerckeyboardmanager"></a><a name="ckeyboardmanager"></a> CKeyboardManager：： CKeyboardManager

建構 `CKeyboardManager` 物件。

```
CKeyboardManager();
```

### <a name="remarks"></a>備註

在大多數情況下，您不需要 `CKeyboardManager` 直接建立。 根據預設，架構會為您建立一個。 若要取得的指標 `CKeyboardManager` ，請呼叫 [CWinAppEx：： GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager)。 如果您手動建立一個，您必須使用 [CWinAppEx：： InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)方法將它初始化。

## <a name="ckeyboardmanagercleanup"></a><a name="cleanup"></a> CKeyboardManager：：清理

釋出 `CKeyboardManager` 資源，並清除所有快速鍵對應。

```
static void CleanUp();
```

### <a name="remarks"></a>備註

如需快速鍵的詳細資訊，請參閱 [鍵盤和滑鼠自訂](../../mfc/keyboard-and-mouse-customization.md)。

當應用程式結束時，您不需要呼叫此函式，因為架構會在應用程式結束時自動呼叫此函數。

## <a name="ckeyboardmanagerfinddefaultaccelerator"></a><a name="finddefaultaccelerator"></a> CKeyboardManager：： FindDefaultAccelerator

抓取指定命令和視窗的預設快速鍵。

```
static BOOL FindDefaultAccelerator(
    UINT uiCmd,
    CString& str,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
在命令識別碼。

*str*<br/>
擴展物件的參考 `CString` 。

*pWndFrame*<br/>
在框架視窗的指標。

*bIsDefaultFrame*<br/>
在指定框架視窗是否為預設框架視窗。

### <a name="return-value"></a>傳回值

如果找到快捷方式，則為非零;否則為0。

### <a name="remarks"></a>備註

這個方法會查閱 *uiCmd* 所指定的命令，並抓取預設快速鍵。 然後，方法會接受與此快速鍵相關聯的字串，並將值寫入 *str* 參數。

## <a name="ckeyboardmanageriskeyhandled"></a><a name="iskeyhandled"></a> CKeyboardManager：： IsKeyHandled

判斷指定的索引鍵是否由 [CKeyboardManager 類別](../../mfc/reference/ckeyboardmanager-class.md)處理。

```
static BOOL __stdcall IsKeyHandled(
    WORD nKey,
    BYTE fVirt,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>參數

*nKey*\
在要檢查的索引鍵。

*fVirt*\
在指定快速鍵的行為。 如需可能值的清單，請參閱 [ACCEL 結構](/windows/win32/api/winuser/ns-winuser-accel)。

*pWndFrame*\
在框架視窗。 這個方法會判斷快速鍵是否在此框架中處理。

*bIsDefaultFrame*\
在布林值參數，指出 *pWndFrame* 是否為預設的框架視窗。

### <a name="return-value"></a>傳回值

如果快速鍵已處理，則為 TRUE。 如果未處理索引鍵或 *pWndFrame* 為 Null，則為 FALSE。

### <a name="remarks"></a>備註

輸入參數必須符合快速鍵對應表中的專案，以供 *nKey* 和 *fVirt* ，以判斷快速鍵是否在 *pWndFrame*中處理。

## <a name="ckeyboardmanageriskeyprintable"></a><a name="iskeyprintable"></a> CKeyboardManager：： IsKeyPrintable

指出字元是否可列印。

```
static BOOL __stdcall IsKeyPrintable(const UINT nChar);
```

### <a name="parameters"></a>參數

*nChar*\
在這個方法所檢查的字元。

### <a name="return-value"></a>傳回值

如果字元是可列印的，則為非零，否則為零。

### <a name="remarks"></a>備註

如果呼叫 [GetKeyboardState](/windows/win32/api/winuser/nf-winuser-getkeyboardstate) 失敗，這個方法會失敗。

## <a name="ckeyboardmanagerisshowallaccelerators"></a><a name="isshowallaccelerators"></a> CKeyboardManager：： IsShowAllAccelerators

指出功能表是否顯示與功能表命令相關聯的所有快速鍵，或僅顯示預設快速鍵。

```
static BOOL IsShowAllAccelerators();
```

### <a name="return-value"></a>傳回值

如果應用程式列出功能表命令的所有快速鍵，則為非零;如果應用程式只顯示預設快速鍵，則為0。

### <a name="remarks"></a>備註

應用程式會在功能表列中列出功能表命令的快速鍵。 使用函式 [CKeyboardManager：： ShowAllAccelerators](#showallaccelerators) 來控制應用程式是否要列出所有快速鍵，或只列出預設快速鍵。

## <a name="ckeyboardmanagerloadstate"></a><a name="loadstate"></a> CKeyboardManager：： LoadState

從 Windows 登錄載入快速鍵資料表。

```
BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>參數

*lpszProfileName*<br/>
在儲存資料的登錄路徑 `CKeyboardManager` 。

*pDefaultFrame*<br/>
在要做為預設視窗使用之框架視窗的指標。

### <a name="return-value"></a>傳回值

如果狀態已成功載入，則為非零，否則為0。

### <a name="remarks"></a>備註

如果 *lpszProfileName* 參數為 Null，這個方法會檢查資料的預設登錄位置 `CKeyboardManager` 。 預設登錄位置是由 [CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)指定。 資料之前必須以方法 [CKeyboardManager：： SaveState](#savestate)來撰寫。

如果您未指定預設視窗，將會使用應用程式的主框架視窗。

## <a name="ckeyboardmanagerresetall"></a><a name="resetall"></a> CKeyboardManager：： ResetAll

從應用程式資源重載快速鍵資料表。

```cpp
void ResetAll();
```

### <a name="remarks"></a>備註

此函式會清除儲存在實例中的快捷方式 `CKeyboardManager` 。 然後，它會從應用程式資源重載鍵盤管理員的狀態。

## <a name="ckeyboardmanagersavestate"></a><a name="savestate"></a> CKeyboardManager：： SaveState

將快速鍵表儲存至 Windows 登錄。

```
BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>參數

*lpszProfileName*<br/>
在用於儲存狀態的登錄路徑 `CKeyboardManager` 。

*pDefaultFrame*<br/>
在成為預設視窗之框架視窗的指標。

### <a name="return-value"></a>傳回值

如果已成功儲存鍵盤管理員狀態，則為非零，否則為0。

### <a name="remarks"></a>備註

如果 *lpszProfileName* 參數為 Null，這個方法會將狀態寫入 `CKeyboardManager` 至 [CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)所指定的預設位置。 如果您指定位置，稍後可以使用 [CKeyboardManager：： LoadState](#loadstate)方法來載入資料。

如果您未指定預設視窗，將會使用主框架視窗作為預設視窗。

## <a name="ckeyboardmanagershowallaccelerators"></a><a name="showallaccelerators"></a> CKeyboardManager：： ShowAllAccelerators

顯示與功能表命令相關聯的所有快速鍵。

```
static void ShowAllAccelerators(
    BOOL bShowAll = TRUE,
    LPCTSTR lpszDelimiter = _afxDefaultAcceleratorDelimiter);
```

### <a name="parameters"></a>參數

*bShowAll*<br/>
在若為 TRUE，則會顯示所有快速鍵。 如果為 FALSE，則只會顯示第一個快速鍵。

*lpszDelimiter*<br/>
在要在快速鍵之間插入的字串。 如果只顯示一個快速鍵，則此分隔符號不會有任何作用。

### <a name="remarks"></a>備註

根據預設，如果某個命令有一個以上相關聯的快捷方式索引鍵，則只會顯示第一個快速鍵。 此函數可讓您列出所有與所有命令相關聯的快速鍵。

快速鍵會列在功能表列的命令旁邊。 如果顯示所有快速鍵， *lpszDelimiter* 提供的字串將會分隔個別的快速鍵。

## <a name="ckeyboardmanagertranslatechartoupper"></a><a name="translatechartoupper"></a> CKeyboardManager：： TranslateCharToUpper

將字元轉換成其上方的暫存器。

```
static UINT TranslateCharToUpper(const UINT nChar);
```

### <a name="parameters"></a>參數

*nChar*<br/>
在要轉換的字元。

### <a name="return-value"></a>傳回值

輸入參數的上方註冊字元。

## <a name="ckeyboardmanagerupdateacceltable"></a><a name="updateacceltable"></a> CKeyboardManager：： UpdateAccelTable

以新的快速鍵資料表更新快速鍵資料表。

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
在檔範本的指標。

*lpAccel*<br/>
在新快速鍵的指標。

*nSize*<br/>
在新快速鍵表的大小。

*pDefaultFrame*<br/>
在預設框架視窗的指標。

*hAccelNew*<br/>
在新快速鍵資料表的控制碼。

### <a name="return-value"></a>傳回值

如果方法成功，則為非零;否則為0。

### <a name="remarks"></a>備註

使用此函式可將現有的快捷方式資料表取代為數個框架視窗物件的新快速鍵。 函式會接收檔範本做為參數，以取得連接至指定檔範本的所有框架視窗物件的存取權。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)<br/>
[CWinAppEx：： InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)<br/>
[鍵盤和滑鼠自訂](../../mfc/keyboard-and-mouse-customization.md)
