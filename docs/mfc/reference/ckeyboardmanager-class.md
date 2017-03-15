---
title: "CKeyboardManager 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CKeyboardManager
dev_langs:
- C++
helpviewer_keywords:
- CKeyboardManager class
ms.assetid: 4809ece6-89df-4479-8b53-9bf476ee107b
caps.latest.revision: 33
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: bbe12d2bf4af0008233df25e09f09008c402ee7f
ms.lasthandoff: 02/24/2017

---
# <a name="ckeyboardmanager-class"></a>CKeyboardManager 類別
管理主框架視窗及子框架視窗的快速鍵資料表。  
  
## <a name="syntax"></a>語法  
  
```  
class CKeyboardManager : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|||  
|-|-|  
|名稱|說明|  
|[CKeyboardManager::CKeyboardManager](#ckeyboardmanager)|建構 `CKeyboardManager` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|||  
|-|-|  
|名稱|說明|  
|[CKeyboardManager::CleanUp](#cleanup)|清除快速鍵資料表。|  
|[CKeyboardManager::FindDefaultAccelerator](#finddefaultaccelerator)|擷取指定的命令和視窗的預設快速鍵。|  
|[CKeyboardManager::IsKeyHandled](#iskeyhandled)|決定索引鍵由快速鍵對應表。|  
|[CKeyboardManager::IsKeyPrintable](#iskeyprintable)|指出是否可列印字元。|  
|[CKeyboardManager::IsShowAllAccelerators](#isshowallaccelerators)|表示功能表是否顯示命令的快速鍵或只有預設的快速鍵。|  
|[CKeyboardManager::LoadState](#loadstate)|從 Windows 登錄載入的快速鍵資料表。|  
|[CKeyboardManager::ResetAll](#resetall)|重新載入應用程式資源的快速鍵資料表。|  
|[CKeyboardManager::SaveState](#savestate)|將捷徑索引鍵的資料表儲存至 Windows 登錄。|  
|[CKeyboardManager::ShowAllAccelerators](#showallaccelerators)|指定是否，架構會顯示所有命令，所有的快速鍵或單一快速鍵，每個命令。 這個方法不會影響必須只有一個相關聯的快速鍵的命令。|  
|[CKeyboardManager::TranslateCharToUpper](#translatechartoupper)|將字元轉換成其上方的暫存器。|  
|[CKeyboardManager::UpdateAccelTable](#updateacceltable)|更新快顯的索引鍵資料表具有新的快速鍵資料表。|  
  
## <a name="remarks"></a>備註  
 這個類別的成員可讓您儲存和載入至 Windows 登錄快速鍵資料表，請使用範本來更新資料表的捷徑，並在框架視窗中尋找命令的預設快速鍵。 此外，`CKeyboardManager`物件可讓您控制如何將快速鍵顯示給使用者。  
  
 您不應該建立`CKeyboardManager`手動物件。 它將會自動建立您的應用程式的架構。 不過，您應該呼叫[CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)您的應用程式在初始化過程。 若要取得您的應用程式鍵盤管理員的指標，呼叫[CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager)。  
  
## <a name="example"></a>範例  
 下列範例示範如何擷取變數的指標，`CKeyboardManager`物件從`CWinAppEx`類別，以及如何顯示所有關聯的快速鍵與功能表命令。 此程式碼片段是一部分[自訂網頁範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_CustomPages #&5;](../../mfc/reference/codesnippet/cpp/ckeyboardmanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxkeyboardmanager.h  
  
##  <a name="a-nameckeyboardmanagera--ckeyboardmanagerckeyboardmanager"></a><a name="ckeyboardmanager"></a>CKeyboardManager::CKeyboardManager  
 建構 `CKeyboardManager` 物件。  
  
```  
CKeyboardManager();
```  
  
### <a name="remarks"></a>備註  
 在大部分情況下，您不需要建立`CKeyboardManager`直接。 根據預設，架構會建立一個用於您。 若要取得的指標`CKeyboardManager`，呼叫[CWinAppEx::GetKeyboardManager](../../mfc/reference/cwinappex-class.md#getkeyboardmanager)。 如果您不要手動建立一個，您必須將它初始化方法[CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)。  
  
##  <a name="a-namecleanupa--ckeyboardmanagercleanup"></a><a name="cleanup"></a>CKeyboardManager::CleanUp  
 釋放`CKeyboardManager`資源，並清除所有的快速鍵對應。  
  
```  
static void CleanUp();
```  
  
### <a name="remarks"></a>備註  
 如需快速鍵的詳細資訊，請參閱[鍵盤和滑鼠自訂](../../mfc/keyboard-and-mouse-customization.md)。  
  
 沒有應用程式結束，因為架構會呼叫它自動在應用程式結束時呼叫此函式。  
  
##  <a name="a-namefinddefaultacceleratora--ckeyboardmanagerfinddefaultaccelerator"></a><a name="finddefaultaccelerator"></a>CKeyboardManager::FindDefaultAccelerator  
 擷取指定的命令和視窗的預設快速鍵。  
  
```  
static BOOL FindDefaultAccelerator(
    UINT uiCmd,  
    CString& str,  
    CFrameWnd* pWndFrame,  
    BOOL bIsDefaultFrame);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiCmd`  
 命令 ID。  
  
 [輸出] `str`  
 對 `CString` 物件的參考。  
  
 [in] `pWndFrame`  
 框架視窗的指標。  
  
 [in] `bIsDefaultFrame`  
 指定的框架視窗是否為預設的框架視窗。  
  
### <a name="return-value"></a>傳回值  
 非零，如果找到捷徑。否則為 0。  
  
### <a name="remarks"></a>備註  
 這個方法會查詢所指定的命令`uiCmd`並擷取預設的快速鍵。 然後方法會採用此快速鍵相關聯的字串值並寫入至`str`參數。  
  
##  <a name="a-nameiskeyhandleda--ckeyboardmanageriskeyhandled"></a><a name="iskeyhandled"></a>CKeyboardManager::IsKeyHandled  
 判斷是否有指定之索引鍵由[CKeyboardManager 類別](../../mfc/reference/ckeyboardmanager-class.md)。  
  
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
|[in] `nKey`|要進行檢查的按鍵。|  
|[in] `fVirt`|指定的快速鍵的行為。 如需可能的值，請參閱[加速度結構](http://msdn.microsoft.com/library/windows/desktop/ms646340)。|  
|[in] `pWndFrame`|框架視窗。 這個方法會判斷是否已處理這個框架中的快速鍵。|  
|[in] `bIsDefaultFrame`|布林值，指出參數是否`pWndFrame`是預設的框架視窗。|  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果處理的快速鍵。 `FALSE`如果索引鍵不處理或`pWndFrame`是`NULL`。  
  
### <a name="remarks"></a>備註  
 輸入的參數必須符合的項目快速鍵對應表中這兩個`nKey`和`fVirt`來判斷是否有處理快速鍵`pWndFrame`。  
  
##  <a name="a-nameiskeyprintablea--ckeyboardmanageriskeyprintable"></a><a name="iskeyprintable"></a>CKeyboardManager::IsKeyPrintable  
 指出是否可列印字元。  
  
```  
static BOOL __stdcall IsKeyPrintable(const UINT nChar);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|[in] `nChar`|這個方法會檢查字元。|  
  
### <a name="return-value"></a>傳回值  
 非零值可列印字元時，如果為零不是。  
  
### <a name="remarks"></a>備註  
 如果呼叫[GetKeyboardState](http://msdn.microsoft.com/library/windows/desktop/ms646299)失敗。  
  
##  <a name="a-nameisshowallacceleratorsa--ckeyboardmanagerisshowallaccelerators"></a><a name="isshowallaccelerators"></a>CKeyboardManager::IsShowAllAccelerators  
 表示功能表是否顯示與功能表命令相關聯的所有快速鍵或只有預設的快速鍵。  
  
```  
static BOOL IsShowAllAccelerators();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果應用程式會列出所有的快速鍵功能表命令的方式。如果應用程式會顯示預設快捷鍵，0。  
  
### <a name="remarks"></a>備註  
 應用程式列出的功能表列中的功能表命令的快速鍵。 使用函數[CKeyboardManager::ShowAllAccelerators](#showallaccelerators)來控制是否應用程式會列出所有的快速鍵或只是預設的快速鍵。  
  
##  <a name="a-nameloadstatea--ckeyboardmanagerloadstate"></a><a name="loadstate"></a>CKeyboardManager::LoadState  
 從 Windows 登錄載入的快速鍵資料表。  
  
```  
BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    CFrameWnd* pDefaultFrame = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszProfileName`  
 登錄路徑位置`CKeyboardManager`資料儲存。  
  
 [in] `pDefaultFrame`  
 要做為預設的視窗框架視窗的指標。  
  
### <a name="return-value"></a>傳回值  
 如果狀態載入成功則為 0 否則為非零。  
  
### <a name="remarks"></a>備註  
 如果`lpszProfileName`參數是`NULL`，這個方法會檢查預設登錄位置`CKeyboardManager`資料。 所指定的預設登錄位置[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)。 資料必須與方法之前寫入[CKeyboardManager::SaveState](#savestate)。  
  
 如果未指定預設的視窗，將會使用您的應用程式的主框架視窗。  
  
##  <a name="a-nameresetalla--ckeyboardmanagerresetall"></a><a name="resetall"></a>CKeyboardManager::ResetAll  
 重新載入應用程式資源的快速鍵資料表。  
  
```  
void ResetAll();
```  
  
### <a name="remarks"></a>備註  
 此函式會清除儲存在快速鍵`CKeyboardManager`執行個體。 然後，它會重新載入鍵盤管理員，從應用程式資源的狀態。  
  
##  <a name="a-namesavestatea--ckeyboardmanagersavestate"></a><a name="savestate"></a>CKeyboardManager::SaveState  
 將捷徑索引鍵的資料表儲存至 Windows 登錄。  
  
```  
BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    CFrameWnd* pDefaultFrame = NULL);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszProfileName`  
 儲存的登錄路徑`CKeyboardManager`狀態。  
  
 [in] `pDefaultFrame`  
 成為預設的視窗框架視窗的指標。  
  
### <a name="return-value"></a>傳回值  
 非零，如果鍵盤管理員狀態已經順利完成，否則為 0。  
  
### <a name="remarks"></a>備註  
 如果`lpszProfileName`參數是`NULL`，此方法將寫入`CKeyboardManager`狀態所指定的預設位置[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)。 如果您指定的位置，您可以將資料載入之後再使用此方法[CKeyboardManager::LoadState](#loadstate)。  
  
 如果未指定預設值 視窗中，主框架視窗會當做預設的視窗。  
  
##  <a name="a-nameshowallacceleratorsa--ckeyboardmanagershowallaccelerators"></a><a name="showallaccelerators"></a>CKeyboardManager::ShowAllAccelerators  
 顯示所有關聯的快速鍵與功能表命令。  
  
```  
static void ShowAllAccelerators(
    BOOL bShowAll = TRUE,  
    LPCTSTR lpszDelimiter = _afxDefaultAcceleratorDelimiter);
```  
  
### <a name="parameters"></a>參數  
 [in] `bShowAll`  
 如果`true`，將會顯示所有的快速鍵。 如果`false`，將會顯示的第一個的快速鍵。  
  
 [in] `lpszDelimiter`  
 要插入快捷鍵之間的字串。 如果只有一個快速鍵會顯示此分隔符號會有任何作用。  
  
### <a name="remarks"></a>備註  
 根據預設，如果命令具有與其相關聯，多個快速鍵將顯示的第一個的快速鍵。 此函式可讓您列出的所有命令相關都聯的所有快速鍵。  
  
 旁邊的功能表列中的命令會列出的鍵盤快速鍵。 如果顯示的快速鍵，所提供字串`lpszDelimiter`分隔個別的快速鍵。  
  
##  <a name="a-nametranslatechartouppera--ckeyboardmanagertranslatechartoupper"></a><a name="translatechartoupper"></a>CKeyboardManager::TranslateCharToUpper  
 將字元轉換成其上方的暫存器。  
  
```  
static UINT TranslateCharToUpper(const UINT nChar);
```  
  
### <a name="parameters"></a>參數  
 [in] `nChar`  
 要轉換的字元。  
  
### <a name="return-value"></a>傳回值  
 輸入參數的上層暫存器就是字元。  
  
##  <a name="a-nameupdateacceltablea--ckeyboardmanagerupdateacceltable"></a><a name="updateacceltable"></a>CKeyboardManager::UpdateAccelTable  
 更新快顯的索引鍵資料表具有新的快速鍵資料表。  
  
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
 [in] `pTemplate`  
 將文件範本的指標。  
  
 [in] `lpAccel`  
 新的快顯金鑰的指標。  
  
 [in] `nSize`  
 新的快速鍵資料表的大小。  
  
 [in] `pDefaultFrame`  
 預設框架視窗的指標。  
  
 [in] `hAccelNew`  
 新的快速鍵資料表控制代碼。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 使用此函式來取代現有的快顯資料表具有數個框架視窗物件的新快速鍵。 在函數收到的文件範本做為參數，以取得連接到指定的文件範本的所有框架視窗物件的存取權。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [Cwinappex 衍生類別](../../mfc/reference/cwinappex-class.md)   
 [CWinAppEx::InitKeyboardManager](../../mfc/reference/cwinappex-class.md#initkeyboardmanager)   
 [鍵盤和滑鼠自訂](../../mfc/keyboard-and-mouse-customization.md)




