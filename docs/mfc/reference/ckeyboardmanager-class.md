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
ms.openlocfilehash: 3360a28d50f64546837cc5ef35dcfc761b4fb0f5
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341497"
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
|[CKeyboardManager::CKeyboardManager](#ckeyboardmanager)|建構 `CKeyboardManager` 物件。|

### <a name="public-methods"></a>公用方法

|||
|-|-|
|名稱|描述|
|[CKeyboardManager::CleanUp](#cleanup)|清除的快速鍵資料表。|
|[CKeyboardManager::FindDefaultAccelerator](#finddefaultaccelerator)|擷取指定的命令和視窗的預設快速鍵。|
|[CKeyboardManager::IsKeyHandled](#iskeyhandled)|決定索引鍵由快速鍵對應表。|
|[CKeyboardManager::IsKeyPrintable](#iskeyprintable)|指出是否可列印字元。|
|[CKeyboardManager::IsShowAllAccelerators](#isshowallaccelerators)|指出功能表是否顯示所有命令的快速鍵或只有預設捷徑的金鑰。|
|[CKeyboardManager::LoadState](#loadstate)|從 Windows 登錄載入快速鍵資料表。|
|[CKeyboardManager::ResetAll](#resetall)|重新載入應用程式資源的快顯索引鍵資料表。|
|[CKeyboardManager::SaveState](#savestate)|將 Windows 登錄捷徑索引鍵的資料表。|
|[CKeyboardManager::ShowAllAccelerators](#showallaccelerators)|指定是否，架構會顯示所有命令，所有的快速鍵或每個命令的單一快速鍵。 這個方法不會影響有只有一個相關聯的快速鍵的命令。|
|[CKeyboardManager::TranslateCharToUpper](#translatechartoupper)|將字元轉換至其上方的暫存器。|
|[CKeyboardManager::UpdateAccelTable](#updateacceltable)|更新快顯的索引鍵資料表與新的快顯索引鍵的資料表。|

## <a name="remarks"></a>備註

這個類別的成員可讓您儲存和載入至 Windows 登錄快速鍵資料表，請使用範本來更新快顯索引鍵資料表名稱，並在框架視窗中尋找命令的預設快速鍵。 颾魤 ㄛ`CKeyboardManager`物件可讓您控制向使用者顯示快速鍵的方式。

您不應建立`CKeyboardManager`手動物件。 它將會自動建立您的應用程式的架構。 不過，您應該呼叫[CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)您的應用程式在初始化過程。 若要取得您的應用程式鍵盤管理員的指標，呼叫[CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager)。

## <a name="example"></a>範例

下列範例示範如何擷取指標`CKeyboardManager`物件從`CWinAppEx`類別，以及如何顯示所有關聯的快速鍵與功能表命令。 此程式碼片段是一部分[自訂頁面範例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_CustomPages#5](../../mfc/reference/codesnippet/cpp/ckeyboardmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)

## <a name="requirements"></a>需求

**標頭：** afxkeyboardmanager.h

##  <a name="ckeyboardmanager"></a>  CKeyboardManager::CKeyboardManager

建構 `CKeyboardManager` 物件。

```
CKeyboardManager();
```

### <a name="remarks"></a>備註

在大部分情況下，您不需要建立`CKeyboardManager`直接。 根據預設，架構會建立一個。 若要取得的指標`CKeyboardManager`，呼叫[CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager)。 如果您不要以手動方式建立，您就必須將它初始化的方法[CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)。

##  <a name="cleanup"></a>  CKeyboardManager::CleanUp

釋放`CKeyboardManager`資源，並清除所有快顯的索引鍵對應。

```
static void CleanUp();
```

### <a name="remarks"></a>備註

如需快速鍵的詳細資訊，請參閱[鍵盤和滑鼠自訂](../../mfc/keyboard-and-mouse-customization.md)。

您不必呼叫此函式，因為架構會呼叫它自動在應用程式結束時，您的應用程式結束時。

##  <a name="finddefaultaccelerator"></a>  CKeyboardManager::FindDefaultAccelerator

擷取指定的命令和視窗的預設快速鍵。

```
static BOOL FindDefaultAccelerator(
    UINT uiCmd,
    CString& str,
    CFrameWnd* pWndFrame,
    BOOL bIsDefaultFrame);
```

### <a name="parameters"></a>參數

*uiCmd*<br/>
[in]命令 id。

*str*<br/>
[out]參考`CString`物件。

*pWndFrame*<br/>
[in]框架視窗的指標。

*bIsDefaultFrame*<br/>
[in]指定的框架視窗是否為預設的框架視窗。

### <a name="return-value"></a>傳回值

如果所找到的快顯，非零值。否則為 0。

### <a name="remarks"></a>備註

這個方法會查詢所指定的命令*uiCmd*並擷取預設的快速鍵。 然後方法會採用此捷徑索引鍵相關聯的字串，並將寫入的值*str*參數。

##  <a name="iskeyhandled"></a>  CKeyboardManager::IsKeyHandled

判斷是否有指定的索引鍵由[CKeyboardManager 類別](../../mfc/reference/ckeyboardmanager-class.md)。

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
|*nKey*|[in]要檢查的索引鍵。|
|*fVirt*|[in]指定攠摝坫行為。 如需可能值的清單，請參閱 <<c0> [ 加速度結構](/windows/desktop/api/winuser/ns-winuser-tagaccel)。|
|*pWndFrame*|[in]框架視窗。 這個方法會判斷是否要將攠摝坫處理這個框架中。|
|*bIsDefaultFrame*|[in]布林值，指出參數是否*pWndFrame*是預設框架視窗。|

### <a name="return-value"></a>傳回值

如果在處理的快速鍵，則為 TRUE。 FALSE 如果未處理的索引鍵，或如果*pWndFrame*是 NULL。

### <a name="remarks"></a>備註

輸入的參數必須符合的快速鍵對應表中這兩個項目*nKey*並*fVirt*以判斷是否已處理攠摝坫*pWndFrame*。

##  <a name="iskeyprintable"></a>  CKeyboardManager::IsKeyPrintable

指出是否可列印字元。

```
static BOOL __stdcall IsKeyPrintable(const UINT nChar);
```

### <a name="parameters"></a>參數

|||
|-|-|
|參數|描述|
|*nChar*|[in]這個方法會檢查的字元。|

### <a name="return-value"></a>傳回值

非零值可列印字元時，如果零不是。

### <a name="remarks"></a>備註

如果呼叫，這個方法就會失敗[GetKeyboardState](/windows/desktop/api/winuser/nf-winuser-getkeyboardstate)失敗。

##  <a name="isshowallaccelerators"></a>  CKeyboardManager::IsShowAllAccelerators

指出功能表是否顯示所有關聯的快速鍵與功能表命令或只有預設的快速鍵。

```
static BOOL IsShowAllAccelerators();
```

### <a name="return-value"></a>傳回值

非零值，如果應用程式會列出所有的快速鍵功能表命令的方式。0，表示應用程式會顯示預設快捷鍵。

### <a name="remarks"></a>備註

應用程式列出的功能表列中的功能表命令的快速鍵。 使用函式[Showallaccelerators](#showallaccelerators)來控制是否應用程式會列出所有的快速鍵或只是預設的快速鍵。

##  <a name="loadstate"></a>  CKeyboardManager::LoadState

從 Windows 登錄載入快速鍵資料表。

```
BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>參數

*lpszProfileName*<br/>
[in]登錄路徑其中`CKeyboardManager`資料會儲存。

*pDefaultFrame*<br/>
[in]作為預設的視窗框架視窗的指標。

### <a name="return-value"></a>傳回值

如果狀態載入成功則為 0 否則，非零值。

### <a name="remarks"></a>備註

如果*lpszProfileName*參數為 NULL，這個方法會檢查預設登錄位置`CKeyboardManager`資料。 所指定的預設登錄位置[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)。 資料必須與方法先前寫入[CKeyboardManager::SaveState](#savestate)。

如果您未指定預設的視窗，將會使用您的應用程式的主框架視窗。

##  <a name="resetall"></a>  CKeyboardManager::ResetAll

重新載入應用程式資源的快顯索引鍵資料表。

```
void ResetAll();
```

### <a name="remarks"></a>備註

此函式會清除儲存在快速鍵`CKeyboardManager`執行個體。 然後，它會重新載入鍵盤管理員，從應用程式資源的狀態。

##  <a name="savestate"></a>  CKeyboardManager::SaveState

將 Windows 登錄捷徑索引鍵的資料表。

```
BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    CFrameWnd* pDefaultFrame = NULL);
```

### <a name="parameters"></a>參數

*lpszProfileName*<br/>
[in]儲存的登錄路徑`CKeyboardManager`狀態。

*pDefaultFrame*<br/>
[in]會變成預設的視窗框架視窗的指標。

### <a name="return-value"></a>傳回值

非零值，如果鍵盤管理員狀態儲存成功，否則為 0。

### <a name="remarks"></a>備註

如果*lpszProfileName*參數為 NULL，此方法將寫入`CKeyboardManager`狀態轉換所指定的預設位置[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)。 如果您指定的位置，您可以將資料載入更新版本使用的方法[CKeyboardManager::LoadState](#loadstate)。

如果您未指定預設的視窗，主框架視窗會用作預設的視窗。

##  <a name="showallaccelerators"></a>  Showallaccelerators

顯示所有關聯的快速鍵與功能表命令。

```
static void ShowAllAccelerators(
    BOOL bShowAll = TRUE,
    LPCTSTR lpszDelimiter = _afxDefaultAcceleratorDelimiter);
```

### <a name="parameters"></a>參數

*bShowAll*<br/>
[in]如果為 TRUE，將會顯示所有的快速鍵。 如果為 FALSE，則會顯示第一個的快速鍵。

*lpszDelimiter*<br/>
[in]要插入快捷鍵之間的字串。 如果只有一個攠摝坫會顯示此分隔符號會有任何作用。

### <a name="remarks"></a>備註

根據預設，如果命令具有與其建立關聯的多個快速鍵將顯示的第一個的快速鍵。 此函式可讓您列出的所有命令相關都聯的所有快速鍵。

將列出的鍵盤快速鍵，功能表列中的命令旁。 顯示所有的快速鍵，則字串會提供所*lpszDelimiter*分隔個別的快速鍵。

##  <a name="translatechartoupper"></a>  CKeyboardManager::TranslateCharToUpper

將字元轉換至其上方的暫存器。

```
static UINT TranslateCharToUpper(const UINT nChar);
```

### <a name="parameters"></a>參數

*nChar*<br/>
[in]要轉換的字元。

### <a name="return-value"></a>傳回值

是輸入參數的上層暫存器的字元。

##  <a name="updateacceltable"></a>  CKeyboardManager::UpdateAccelTable

更新快顯的索引鍵資料表與新的快顯索引鍵的資料表。

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
[in]文件範本指標。

*lpAccel*<br/>
[in]新的快顯索引鍵的指標。

*nSize*<br/>
[in]新的快顯資料表的大小。

*pDefaultFrame*<br/>
[in]預設框架視窗的指標。

*hAccelNew*<br/>
[in]新的快顯資料表控制代碼。

### <a name="return-value"></a>傳回值

如果方法成功則為非零否則為 0。

### <a name="remarks"></a>備註

使用此函式來取代現有的快顯資料表具有數個框架視窗物件的新快速鍵。 在函數收到的文件範本做為參數，以取得連線到指定的文件範本的所有框架視窗物件的存取權。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)<br/>
[CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)<br/>
[鍵盤和滑鼠自訂](../../mfc/keyboard-and-mouse-customization.md)
