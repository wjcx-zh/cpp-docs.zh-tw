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
ms.openlocfilehash: e4f8f678e76113b5d012242f474ff0ab8b0628dd
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505785"
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
|名稱|說明|
|[CKeyboardManager::CKeyboardManager](#ckeyboardmanager)|建構 `CKeyboardManager` 物件。|

### <a name="public-methods"></a>公用方法

|||
|-|-|
|名稱|描述|
|[CKeyboardManager::CleanUp](#cleanup)|清除快速鍵資料表。|
|[CKeyboardManager::FindDefaultAccelerator](#finddefaultaccelerator)|抓取指定命令和視窗的預設快速鍵。|
|[CKeyboardManager::IsKeyHandled](#iskeyhandled)|判斷索引鍵是否由快速鍵對應表處理。|
|[CKeyboardManager::IsKeyPrintable](#iskeyprintable)|指出是否可列印字元。|
|[CKeyboardManager::IsShowAllAccelerators](#isshowallaccelerators)|指出功能表是否顯示命令的所有快速鍵, 或僅顯示預設快速鍵。|
|[CKeyboardManager::LoadState](#loadstate)|從 Windows 登錄載入快速鍵資料表。|
|[CKeyboardManager::ResetAll](#resetall)|從應用程式資源重載快捷方式索引鍵資料表。|
|[CKeyboardManager::SaveState](#savestate)|將快速鍵資料表儲存至 Windows 登錄。|
|[CKeyboardManager::ShowAllAccelerators](#showallaccelerators)|指定架構是否顯示所有命令的所有快速鍵, 或每個命令的單一快速鍵。 這個方法不會影響只有一個相關聯快速鍵的命令。|
|[CKeyboardManager::TranslateCharToUpper](#translatechartoupper)|將字元轉換為其上方的暫存器。|
|[CKeyboardManager::UpdateAccelTable](#updateacceltable)|使用新的快速鍵資料表來更新快速鍵資料表。|

## <a name="remarks"></a>備註

這個類別的成員可讓您將快速鍵資料表儲存和載入至 Windows 登錄, 使用範本來更新簡短的剪下索引鍵資料表, 並在框架視窗中尋找命令的預設快速鍵。 此外, `CKeyboardManager`物件可讓您控制如何向使用者顯示快捷方式索引鍵。

您不應該手動建立`CKeyboardManager`物件。 應用程式的架構會自動建立此檔案。 不過, 您應該在應用程式的初始化過程中呼叫[CWinAppEx:: InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager) 。 若要取得應用程式之鍵盤管理員的指標, 請呼叫[CWinAppEx:: GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager)。

## <a name="example"></a>範例

下列範例示範如何`CKeyboardManager` `CWinAppEx`從類別中取出物件的指標, 以及如何顯示與功能表命令相關聯的所有快速鍵。 此程式碼片段是[自訂頁面範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_CustomPages#5](../../mfc/reference/codesnippet/cpp/ckeyboardmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)

## <a name="requirements"></a>需求

**標頭:** afxkeyboardmanager。h

##  <a name="ckeyboardmanager"></a>CKeyboardManager:: CKeyboardManager

建構 `CKeyboardManager` 物件。

```
CKeyboardManager();
```

### <a name="remarks"></a>備註

在大部分的情況下, 您不需要`CKeyboardManager`直接建立。 根據預設, 架構會為您建立一個。 若要取得的`CKeyboardManager`指標, 請呼叫[CWinAppEx:: GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager)。 如果您手動建立一個, 您必須使用[CWinAppEx:: InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)方法將它初始化。

##  <a name="cleanup"></a>CKeyboardManager:: 清除

`CKeyboardManager`釋放資源並清除所有快速鍵對應。

```
static void CleanUp();
```

### <a name="remarks"></a>備註

如需快速鍵的詳細資訊, 請參閱[鍵盤和滑鼠自訂](../../mfc/keyboard-and-mouse-customization.md)。

當您的應用程式結束時, 您不需要呼叫此函式, 因為架構會在應用程式結束期間自動呼叫此函式。

##  <a name="finddefaultaccelerator"></a>CKeyboardManager:: FindDefaultAccelerator

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
脫銷`CString`物件的參考。

*pWndFrame*<br/>
在框架視窗的指標。

*bIsDefaultFrame*<br/>
在指定框架視窗是否為預設框架視窗。

### <a name="return-value"></a>傳回值

如果找到快捷方式, 則為非零;否則為0。

### <a name="remarks"></a>備註

這個方法會查閱*uiCmd*所指定的命令, 並抓取預設的快速鍵。 然後, 方法會接受與此快速鍵關聯的字串, 並將值寫入*str*參數。

##  <a name="iskeyhandled"></a>CKeyboardManager:: IsKeyHandled

判斷指定的索引鍵是否由[CKeyboardManager 類別](../../mfc/reference/ckeyboardmanager-class.md)處理。

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
|參數|說明|
|*nKey*|在要檢查的索引鍵。|
|*fVirt*|在指定快速鍵的行為。 如需可能值的清單, 請參閱[ACCEL 結構](/windows/win32/api/winuser/ns-winuser-accel)。|
|*pWndFrame*|在框架視窗。 這個方法會決定是否在此框架中處理快捷方式索引鍵。|
|*bIsDefaultFrame*|在布林值參數, 指出*pWndFrame*是否為預設的框架視窗。|

### <a name="return-value"></a>傳回值

如果快速鍵已處理, 則為 TRUE。 如果未處理索引鍵, 或如果*pWndFrame*為 Null, 則為 FALSE。

### <a name="remarks"></a>備註

輸入參數必須符合快速鍵對應表中的專案, 以供*nKey*和*fVirt*用來判斷快速鍵是否在*pWndFrame*中處理。

##  <a name="iskeyprintable"></a>CKeyboardManager:: IsKeyPrintable

指出是否可列印字元。

```
static BOOL __stdcall IsKeyPrintable(const UINT nChar);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*nChar*|在這個方法所檢查的字元。|

### <a name="return-value"></a>傳回值

如果字元可列印, 則為非零, 否則為零。

### <a name="remarks"></a>備註

如果[GetKeyboardState](/windows/win32/api/winuser/nf-winuser-getkeyboardstate)的呼叫失敗, 這個方法就會失敗。

##  <a name="isshowallaccelerators"></a>CKeyboardManager:: IsShowAllAccelerators

指出功能表是否顯示與功能表命令相關聯的所有快速鍵, 或僅顯示預設快速鍵。

```
static BOOL IsShowAllAccelerators();
```

### <a name="return-value"></a>傳回值

如果應用程式列出功能表命令的所有快速鍵, 則為非零;如果應用程式只顯示預設快速鍵, 則為0。

### <a name="remarks"></a>備註

應用程式會在功能表列中列出功能表命令的快速鍵。 使用[CKeyboardManager:: ShowAllAccelerators](#showallaccelerators)函式來控制應用程式是否會列出所有快速鍵, 或只列出預設快速鍵。

##  <a name="loadstate"></a>CKeyboardManager:: LoadState

從 Windows 登錄載入快速鍵資料表。

```
BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>參數

*lpszProfileName*<br/>
在儲存`CKeyboardManager`資料的登錄路徑。

*pDefaultFrame*<br/>
在要當做預設視窗使用之框架視窗的指標。

### <a name="return-value"></a>傳回值

如果成功載入狀態則為非零, 否則為0。

### <a name="remarks"></a>備註

如果*lpszProfileName*參數為 Null, 這個方法會檢查`CKeyboardManager`資料的預設登錄位置。 預設登錄位置是由[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)所指定。 資料必須先前使用[CKeyboardManager:: SaveState](#savestate)方法來撰寫。

如果您未指定預設視窗, 則會使用應用程式的主框架視窗。

##  <a name="resetall"></a>CKeyboardManager:: ResetAll

從應用程式資源重載快捷方式索引鍵資料表。

```
void ResetAll();
```

### <a name="remarks"></a>備註

此函式會清除儲存在`CKeyboardManager`實例中的快捷方式。 然後, 它會從應用程式資源重載鍵盤管理員的狀態。

##  <a name="savestate"></a>CKeyboardManager:: SaveState

將快速鍵資料表儲存至 Windows 登錄。

```
BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>參數

*lpszProfileName*<br/>
在用於儲存`CKeyboardManager`狀態的登錄路徑。

*pDefaultFrame*<br/>
在成為預設視窗之框架視窗的指標。

### <a name="return-value"></a>傳回值

如果成功儲存鍵盤管理員狀態, 則為非零, 否則為0。

### <a name="remarks"></a>備註

如果*lpszProfileName*參數為 Null, 這個方法會將`CKeyboardManager`狀態寫入[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)所指定的預設位置。 如果您指定位置, 則可以稍後使用[CKeyboardManager:: LoadState](#loadstate)方法來載入資料。

如果您未指定預設視窗, 則主框架視窗會當做預設視窗使用。

##  <a name="showallaccelerators"></a>CKeyboardManager:: ShowAllAccelerators

顯示與功能表命令相關聯的所有快速鍵。

```
static void ShowAllAccelerators(
    BOOL bShowAll = TRUE,
    LPCTSTR lpszDelimiter = _afxDefaultAcceleratorDelimiter);
```

### <a name="parameters"></a>參數

*bShowAll*<br/>
在若為 TRUE, 則會顯示所有快速鍵。 如果為 FALSE, 則只會顯示第一個快速鍵。

*lpszDelimiter*<br/>
在要在快速鍵之間插入的字串。 如果只顯示一個快速鍵, 則此分隔符號不會有任何作用。

### <a name="remarks"></a>備註

根據預設, 如果命令有一個以上相關聯的快速鍵, 則只會顯示第一個快速鍵。 此函式可讓您列出所有與所有命令相關聯的快速鍵。

快速鍵會列在功能表列中的命令旁邊。 如果顯示所有快速鍵, *lpszDelimiter*所提供的字串將會分隔個別的快速鍵。

##  <a name="translatechartoupper"></a>  CKeyboardManager::TranslateCharToUpper

將字元轉換為其上方的暫存器。

```
static UINT TranslateCharToUpper(const UINT nChar);
```

### <a name="parameters"></a>參數

*nChar*<br/>
在要轉換的字元。

### <a name="return-value"></a>傳回值

輸入參數的上方暫存器字元。

##  <a name="updateacceltable"></a>CKeyboardManager:: UpdateAccelTable

使用新的快速鍵資料表來更新快速鍵資料表。

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
在新快捷方式資料表的大小。

*pDefaultFrame*<br/>
在預設框架視窗的指標。

*hAccelNew*<br/>
在新快捷方式資料表的控制碼。

### <a name="return-value"></a>傳回值

如果方法成功, 則為非零;否則為0。

### <a name="remarks"></a>備註

使用此函式可將現有的快捷方式資料表取代為數個框架視窗物件的新快速鍵。 函式會接收檔範本做為參數, 以取得連接至指定檔範本之所有框架視窗物件的存取權。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)<br/>
[CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)<br/>
[鍵盤和滑鼠自訂](../../mfc/keyboard-and-mouse-customization.md)
