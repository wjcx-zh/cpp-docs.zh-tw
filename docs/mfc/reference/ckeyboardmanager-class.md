---
title: CKeyboardManager 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1b9d4aace502310836429ec8f8f9db74d7cf17ff
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369098"
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
|[CKeyboardManager::IsShowAllAccelerators](#isshowallaccelerators)|表示功能表是否顯示所有命令的快速鍵或只有預設快顯的金鑰。|  
|[CKeyboardManager::LoadState](#loadstate)|從 Windows 登錄載入的快速鍵資料表。|  
|[CKeyboardManager::ResetAll](#resetall)|重新載入應用程式資源的快速鍵資料表。|  
|[CKeyboardManager::SaveState](#savestate)|儲存至 Windows 登錄的快顯索引鍵的資料表。|  
|[CKeyboardManager::ShowAllAccelerators](#showallaccelerators)|指定架構顯示所有命令，用於所有的快速鍵或每個命令的單一快速鍵。 這個方法不會影響具有只有一個相關聯的快速鍵的命令。|  
|[CKeyboardManager::TranslateCharToUpper](#translatechartoupper)|將字元轉換成其上方的暫存器。|  
|[CKeyboardManager::UpdateAccelTable](#updateacceltable)|更新快顯的索引鍵資料表與新的快速鍵資料表。|  
  
## <a name="remarks"></a>備註  
 這個類別的成員可讓您儲存及載入的快速鍵資料表至 Windows 登錄，請使用範本來更新快顯索引鍵資料表中，並在框架視窗中尋找預設的快速鍵命令。 此外，`CKeyboardManager`物件可讓您控制如何將快速鍵顯示給使用者。  
  
 您不應建立`CKeyboardManager`手動物件。 它將會自動建立應用程式的架構。 不過，您應該呼叫[CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)的過程中初始化您的應用程式。 若要取得您的應用程式鍵盤管理員的指標，呼叫[CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager)。  
  
## <a name="example"></a>範例  
 下列範例示範如何擷取指標`CKeyboardManager`物件從`CWinAppEx`類別，以及如何顯示與功能表命令相關聯的所有快速鍵。 此程式碼片段是部分[自訂網頁範例](../../visual-cpp-samples.md)。  
  
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
 在大部分情況下，您不必建立`CKeyboardManager`直接。 根據預設，此架構為您建立一個。 若要取得的指標`CKeyboardManager`，呼叫[CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager)。 如果您不要手動建立一個，您必須初始化執行個體與方法[CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)。  
  
##  <a name="cleanup"></a>  CKeyboardManager::CleanUp  
 釋出`CKeyboardManager`資源，並清除所有快顯的索引鍵對應。  
  
```  
static void CleanUp();
```  
  
### <a name="remarks"></a>備註  
 如需快速鍵的詳細資訊，請參閱[鍵盤和滑鼠自訂](../../mfc/keyboard-and-mouse-customization.md)。  
  
 您沒有應用程式結束，因為架構會呼叫它自動在應用程式結束時呼叫此函式。  
  
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
 [輸入] `uiCmd`  
 命令 ID。  
  
 [輸出] `str`  
 對 `CString` 物件的參考。  
  
 [輸入] `pWndFrame`  
 框架視窗的指標。  
  
 [輸入] `bIsDefaultFrame`  
 指定的框架視窗是否為預設的框架視窗。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果找到捷徑否則便是 0。  
  
### <a name="remarks"></a>備註  
 這個方法會查詢所指定的命令`uiCmd`並擷取預設的快速鍵。 然後方法會採用這個快顯索引鍵相關聯的字串，並寫入至值`str`參數。  
  
##  <a name="iskeyhandled"></a>  CKeyboardManager::IsKeyHandled  
 判斷指定的索引鍵由處理[CKeyboardManager 類別](../../mfc/reference/ckeyboardmanager-class.md)。  
  
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
|[輸入] `nKey`|要進行檢查的按鍵。|  
|[輸入] `fVirt`|指定攠摝坫行為。 如需可能值的清單，請參閱[快速鍵結構](http://msdn.microsoft.com/library/windows/desktop/ms646340)。|  
|[輸入] `pWndFrame`|框架視窗。 這個方法會決定是否要將攠摝坫處理在這個框架中。|  
|[輸入] `bIsDefaultFrame`|布林值，指出參數是否`pWndFrame`是預設框架視窗。|  
  
### <a name="return-value"></a>傳回值  
 `TRUE` 如果處理的快速鍵。 `FALSE` 如果索引鍵不處理或`pWndFrame`是`NULL`。  
  
### <a name="remarks"></a>備註  
 輸入的參數必須符合的項目快速鍵對應表中這兩個的`nKey`和`fVirt`來判斷是否進行處理攠摝坫`pWndFrame`。  
  
##  <a name="iskeyprintable"></a>  CKeyboardManager::IsKeyPrintable  
 指出是否可列印字元。  
  
```  
static BOOL __stdcall IsKeyPrintable(const UINT nChar);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[輸入] `nChar`|這個方法會檢查字元。|  
  
### <a name="return-value"></a>傳回值  
 為非零，如果可列印的字元，零如果不是。  
  
### <a name="remarks"></a>備註  
 如果呼叫這個方法會失敗[GetKeyboardState](http://msdn.microsoft.com/library/windows/desktop/ms646299)失敗。  
  
##  <a name="isshowallaccelerators"></a>  CKeyboardManager::IsShowAllAccelerators  
 表示功能表是否顯示與功能表命令相關聯的所有快速鍵或只有預設快顯索引鍵。  
  
```  
static BOOL IsShowAllAccelerators();
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果應用程式列出所有的快速鍵功能表命令。如果應用程式會顯示預設快捷鍵，0。  
  
### <a name="remarks"></a>備註  
 應用程式列出功能表列中的功能表命令的快速鍵。 使用函數[CKeyboardManager::ShowAllAccelerators](#showallaccelerators)來控制是否應用程式列出所有的快速鍵或只要預設的快速鍵。  
  
##  <a name="loadstate"></a>  CKeyboardManager::LoadState  
 從 Windows 登錄載入的快速鍵資料表。  
  
```  
BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    CFrameWnd* pDefaultFrame = NULL);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszProfileName`  
 登錄路徑其中`CKeyboardManager`資料會儲存。  
  
 [輸入] `pDefaultFrame`  
 要做為預設的視窗框架視窗的指標。  
  
### <a name="return-value"></a>傳回值  
 非零，如果狀態程式成功載入則為 0。  
  
### <a name="remarks"></a>備註  
 如果`lpszProfileName`參數是`NULL`，這個方法會檢查的預設登錄位置`CKeyboardManager`資料。 所指定的預設登錄位置[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)。 資料必須與方法先前寫入[CKeyboardManager::SaveState](#savestate)。  
  
 如果您未指定預設的視窗，將會使用您的應用程式的主框架視窗。  
  
##  <a name="resetall"></a>  CKeyboardManager::ResetAll  
 重新載入應用程式資源的快速鍵資料表。  
  
```  
void ResetAll();
```  
  
### <a name="remarks"></a>備註  
 此函式會清除儲存在快速鍵`CKeyboardManager`執行個體。 然後，它會重新載入鍵盤管理員，從應用程式資源的狀態。  
  
##  <a name="savestate"></a>  CKeyboardManager::SaveState  
 儲存至 Windows 登錄的快顯索引鍵的資料表。  
  
```  
BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    CFrameWnd* pDefaultFrame = NULL);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `lpszProfileName`  
 儲存的登錄路徑`CKeyboardManager`狀態。  
  
 [輸入] `pDefaultFrame`  
 變成預設視窗框架視窗的指標。  
  
### <a name="return-value"></a>傳回值  
 如果鍵盤管理員狀態已儲存成功非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 如果`lpszProfileName`參數是`NULL`，此方法將寫入`CKeyboardManager`狀態所指定的預設位置[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)。 如果您指定的位置，您可以將資料載入稍後使用方法[CKeyboardManager::LoadState](#loadstate)。  
  
 如果您未指定預設的視窗，主框架視窗會當做預設的視窗。  
  
##  <a name="showallaccelerators"></a>  CKeyboardManager::ShowAllAccelerators  
 顯示與功能表命令相關聯的所有快速鍵。  
  
```  
static void ShowAllAccelerators(
    BOOL bShowAll = TRUE,  
    LPCTSTR lpszDelimiter = _afxDefaultAcceleratorDelimiter);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `bShowAll`  
 如果`true`，將會顯示所有的快速鍵。 如果`false`，將會顯示的第一個的快速鍵。  
  
 [輸入] `lpszDelimiter`  
 要插入攠摝坫之間的字串。 如果只會顯示一個快顯金鑰，這個分隔符號會有任何作用。  
  
### <a name="remarks"></a>備註  
 根據預設，如果命令具有多個與它相關聯的快顯索引鍵將顯示的第一個的快速鍵。 此函式可讓您列出所有的命令相關聯的所有快速鍵。  
  
 旁邊的功能表列中的命令會列出的鍵盤快速鍵。 如果顯示的快速鍵，所提供字串`lpszDelimiter`分隔個別的快速鍵。  
  
##  <a name="translatechartoupper"></a>  CKeyboardManager::TranslateCharToUpper  
 將字元轉換成其上方的暫存器。  
  
```  
static UINT TranslateCharToUpper(const UINT nChar);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `nChar`  
 要轉換的字元。  
  
### <a name="return-value"></a>傳回值  
 上方的暫存器的輸入參數的字元。  
  
##  <a name="updateacceltable"></a>  CKeyboardManager::UpdateAccelTable  
 更新快顯的索引鍵資料表與新的快速鍵資料表。  
  
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
 [輸入] `pTemplate`  
 文件範本指標。  
  
 [輸入] `lpAccel`  
 新的快顯索引鍵的指標。  
  
 [輸入] `nSize`  
 新的快速鍵資料表的大小。  
  
 [輸入] `pDefaultFrame`  
 預設框架視窗的指標。  
  
 [輸入] `hAccelNew`  
 新的快速鍵資料表控制代碼。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果方法成功。否則便是 0。  
  
### <a name="remarks"></a>備註  
 使用此函式來取代現有的快顯資料表具有數個框架視窗物件的新快速鍵。 在函數收到的文件範本做為參數，以取得連接至給定文件範本的所有框架視窗物件的存取權。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)   
 [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)   
 [鍵盤和滑鼠自訂](../../mfc/keyboard-and-mouse-customization.md)



