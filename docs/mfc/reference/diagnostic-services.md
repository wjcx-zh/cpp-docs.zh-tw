---
title: 診斷服務
ms.date: 11/04/2016
helpviewer_keywords:
- diagnosi [MFC]s, diagnostic services
- diagnostic macros [MFC], list of general MFC
- services [MFC], diagnostic
- MFC, diagnostic services
- general diagnostic functions and variables [MFC]
- diagnostics [MFC], diagnostic functions and variables
- diagnostics [MFC], list of general MFC
- diagnosis [MFC], diagnostic functions and variables
- diagnosis [MFC], list of general MFC
- general diagnostic macros in MFC
- diagnostic macros [MFC]
- diagnostic services [MFC]
- object diagnostic functions in MFC
- diagnostics [MFC], diagnostic services
- diagnostic functions and variables [MFC]
ms.assetid: 8d78454f-9fae-49c2-88c9-d3fabd5393e8
ms.openlocfilehash: 8db12a73d64641a52fea3056de8ab3180c9239b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365787"
---
# <a name="diagnostic-services"></a>診斷服務

MFC 程式庫提供許多診斷服務，可讓您更輕鬆地對程式進行偵錯。 這些診斷服務包含巨集和全域函式，可讓您追蹤程式的記憶體配置、在執行階段傾印物件的內容，以及在執行階段列印偵錯訊息。 診斷服務的巨集和全域函式可分為下列分類：

- 一般診斷巨集

- 一般診斷函式和變數

- 物件診斷函式

這些巨集和函式都可以在 MFC 的偵錯和發行版本中，供所有衍生自 `CObject` 的類別使用。 但是,除DEBUG_NEW和 VERIFY 外,其他所有內容在發佈版本中不執行任何操作。

在偵錯程式庫中，所有配置的記憶體區塊都會以一系列「保護位元組」(Guard Byte) 來提供支援。 如果這些位元組受到錯誤記憶體寫入的干擾，則診斷常式可能會回報問題。 如果您在實作檔中包含此行：

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

在實現檔中,對**new**的所有呼叫都將儲存發生記憶體分配的檔名和行號。 函數[CMemoryState::DumpAllObjects 因為](cmemorystate-structure.md#dumpallobjectssince)將顯示此額外資訊,允許您識別記憶體洩漏。 有關診斷輸出的其他資訊,請參閱[CDumpContext](../../mfc/reference/cdumpcontext-class.md)類。

此外，C 執行階段程式庫也支援一組可用來偵錯應用程式的診斷函式。 有關詳細資訊,請參閱執行時庫參考中的[除錯例程式](../../c-runtime-library/debug-routines.md)。

### <a name="mfc-general-diagnostic-macros"></a>MFC 一般診斷巨集

|||
|-|-|
|[斷言](#assert)|如果指定的運算式在程式庫的偵錯版本中評估為 FALSE，則會列印訊息，再中止程式。|
|[ASSERT_KINDOF](#assert_kindof)|測試某物件是屬於指定類別，還是屬於該類別的衍生類別。|
|[ASSERT_VALID](#assert_valid)|藉由呼叫物件的 `AssertValid` 成員函式來測試其內部有效性，通常會覆寫自 `CObject`。|
|[DEBUG_NEW](#debug_new)|提供偵錯模式中所有物件配置的檔案名稱和行號，以協助找出記憶體流失的問題。|
|[DEBUG_ONLY](#debug_only)|類似於 ASSERT，但不會測試運算式的值；適用於只能在偵錯模式中執行的程式碼。|
|[確保和ENSURE_VALID](#ensure)|用於驗證數據正確性。|
|[THIS_FILE](#this_file)|展開到正在編譯的檔的名稱。|
|[追蹤](#trace)|提供此程式庫之偵錯版本中類似 `printf`的功能。|
|[驗證](#verify)|類似於 ASSERT，但不僅會評估此程式庫之發行版本中的運算式，也會評估偵錯版本中的運算式。|

### <a name="mfc-general-diagnostic-variables-and-functions"></a>MFC 一般診斷變數和函式

|||
|-|-|
|[afxDump](#afxdump)|將[CDumpContext](../../mfc/reference/cdumpcontext-class.md)資訊發送到除錯器輸出視窗或調試終端的全域變數。|
|[afxMemDF](#afxmemdf)|全域變數，可控制偵錯記憶體配置器的行為。|
|[AfxCheckError](#afxcheckerror)|全域變數，可用來測試所傳遞的 SCODE 以查看其是否為錯誤；如果是，則擲回適當的錯誤。|
|[AfxCheckMemory](#afxcheckmemory)|檢查目前配置之所有記憶體的完整性。|
|[AfxDebugBreak](#afxdebugbreak)|導致執行中斷。|
|[afxDump](#cdumpcontext_in_mfc)|如果在偵錯工具中呼叫，則會一面進行偵錯，一面傾印物件的狀態。|
|[afxDump](#afxdump)|在調試時轉儲對象狀態的內部函數。|
|[AfxDumpStack](#afxdumpstack)|產生目前堆疊的映像。 這個函式一律會以靜態方式連結。|
|[AfxEnableMemoryLeakDump](#afxenablememoryleakdump)|啟用記憶體流失傾印。|
|[AfxEnableMemoryTracking](#afxenablememorytracking)|開啟和關閉記憶體追蹤。|
|[AfxIsMemoryBlock](#afxismemoryblock)|確認已適當地配置記憶體區塊。|
|[AfxIsValidAddress](#afxisvalidaddress)|確認記憶體位址範圍落在程式的範圍內。|
|[AfxIsValidString](#afxisvalidstring)|判斷字串指標是否有效。|
|[AfxSetAllocHook](#afxsetallochook)|允許對每個記憶體配置呼叫函式。|

### <a name="mfc-object-diagnostic-functions"></a>MFC 物件診斷函式

|||
|-|-|
|[AfxDoForAllClasses](#afxdoforallclasses)|針對所有可支援執行階段類型檢查的 `CObject`衍生類別執行指定的函式。|
|[AfxDoForAllObjects](#afxdoforallobjects)|對使用**new**new`CObject`分配 的所有派生物件執行指定的函數。|

### <a name="mfc-compilation-macros"></a>MFC 編譯宏

|||
|-|-|
|[_AFX_SECURE_NO_WARNINGS](#afx_secure_no_warnings)|隱藏關於使用被取代 MFC 的功能的編譯器警告。|

## <a name="_afx_secure_no_warnings"></a><a name="afx_secure_no_warnings"></a>_AFX_SECURE_NO_WARNINGS

隱藏關於使用被取代 MFC 的功能的編譯器警告。

### <a name="syntax"></a>語法

```
_AFX_SECURE_NO_WARNINGS
```

### <a name="example"></a>範例

如果沒有定義 _AFX_SECURE_NO_WARNINGS，則此程式碼範例會產生編譯器警告。

```cpp
// define this before including any afx files in *pch.h* (*stdafx.h* in Visual Studio 2017 and earlier)
#define _AFX_SECURE_NO_WARNINGS
```

```cpp
CRichEditCtrl* pRichEdit = new CRichEditCtrl;
pRichEdit->Create(WS_CHILD|WS_VISIBLE|WS_BORDER|ES_MULTILINE,
   CRect(10,10,100,200), pParentWnd, 1);
char sz[256];
pRichEdit->GetSelText(sz);
```

## <a name="afxdebugbreak"></a><a name="afxdebugbreak"></a>AfxDebugBreak

調用此函數以在執行 MFC 應用程式的調試版本時導致`AfxDebugBreak`中斷 (在調用到的位置)。

### <a name="syntax"></a>語法

```
void AfxDebugBreak( );
```

### <a name="remarks"></a>備註

`AfxDebugBreak`在 MFC 應用程式的發佈版本中不起作用,應刪除。 此功能應僅在 MFC 應用程式中使用。 使用 Win32`DebugBreak`API 版本 ,會導致非 MFC 應用程式中的中斷。

### <a name="requirements"></a>需求

**標題:** afxver_.h

## <a name="assert"></a><a name="assert"></a>斷言

評估其參數。

```
ASSERT(booleanExpression)
```

### <a name="parameters"></a>參數

*布林運算式*<br/>
指定計算為非零或 0 的運算式(包括指標值)。

### <a name="remarks"></a>備註

如果結果為 0,宏將列印診斷消息並中止程式。 如果條件為非零,則不執行任何操作。

診斷資訊的格式如下

`assertion failed in file <name> in line <num>`

*其中名稱*是源文件的名稱 *,num*是源檔中失敗的斷言的行號。

在 MFC 的發表版本中,ASSERT 不計算運算式,因此不會中斷程式。 如果無論環境如何,都必須計算表達式,請使用 VERIFY 宏代替 ASSERT。

> [!NOTE]
> 此功能僅在 MFC 的調試版本中可用。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#44](../../mfc/codesnippet/cpp/diagnostic-services_2.cpp)]

### <a name="requirements"></a>需求

**標題:** afx.h

## <a name="assert_kindof"></a><a name="assert_kindof"></a>ASSERT_KINDOF

此宏斷言指向的對像是指定類的物件,或者是從指定類派生的類的物件。

```
ASSERT_KINDOF(classname, pobject)
```

### <a name="parameters"></a>參數

*類別*<br/>
`CObject`派生類的名稱。

*pobject*<br/>
指向類物件的指標。

### <a name="remarks"></a>備註

*pobject*參數應是指向物件的指標,並且可以是**const**。 物件指向,類必須支援`CObject`運行時類資訊。 例如,為了確保它是`pDocument`指向`CMyDoc`類或其任何衍生物的物件的指標,您可以編寫代碼:

[!code-cpp[NVC_MFCDocView#194](../../mfc/codesnippet/cpp/diagnostic-services_3.cpp)]

使用`ASSERT_KINDOF`巨集與編碼完全相同:

[!code-cpp[NVC_MFCDocView#195](../../mfc/codesnippet/cpp/diagnostic-services_4.cpp)]

此函數僅適用於使用 [DECLARE_DYNAMIC](運行時-物件-服務.md_declare_dynamic 或[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)宏聲明的類。

> [!NOTE]
> 此功能僅在 MFC 的調試版本中可用。

### <a name="requirements"></a>需求

**標題:** afx.h

## <a name="assert_valid"></a><a name="assert_valid"></a>ASSERT_VALID

用於測試有關物件內部狀態有效性的假設。

```
ASSERT_VALID(pObject)
```

### <a name="parameters"></a>參數

*pObject*<br/>
指定派生自`CObject``AssertValid`具有成員函數重寫版本的類的物件。

### <a name="remarks"></a>備註

ASSERT_VALID調用作為`AssertValid`參數傳遞的對象的成員函數。

在 MFC 的發佈版本中,ASSERT_VALID不執行任何操作。 在調試版本中,它驗證指標,檢查 NULL,並調用物件自己的`AssertValid`成員函數。 如果其中任何一個測試失敗,警報消息的顯示方式與[ASSERT](#assert)相同。

> [!NOTE]
> 此功能僅在 MFC 的調試版本中可用。

有關詳細資訊和範例,請參閱除錯[MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCObjectSample#19](../../mfc/codesnippet/cpp/diagnostic-services_5.cpp)]

### <a name="requirements"></a>需求

**標題:** afx.h

## <a name="debug_new"></a><a name="debug_new"></a>DEBUG_NEW

協助查找記憶體洩漏。

```
#define  new DEBUG_NEW
```

### <a name="remarks"></a>備註

您可以在程式中的任何地方使用DEBUG_NEW,通常使用**新**運算符分配堆存儲。

在除錯模式下(定義 **_DEBUG**符號時),DEBUG_NEW追蹤它分配的每個物件的檔名和行號。 然後,當您使用[CMemoryState::DumpAllObjects 由於](cmemorystate-structure.md#dumpallobjectssince)成員函數,使用DEBUG_NEW分配的每個物件都顯示檔名和行號。

若要使用DEBUG_NEW,請將以下指令插入到來源檔案中:

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

插入此指令後,預處理器將在使用**新**時插入DEBUG_NEW,MFC 將執行其餘操作。 編譯程式的發佈版本時,DEBUG_NEW解析為簡單的**新**操作,並且不會生成檔名和行號資訊。

> [!NOTE]
> 在早期版本的 MFC(4.1 和更早版本)中,您`#define`需要將語句放在調用IMPLEMENT_DYNCREATE或IMPLEMENT_SERIAL宏的所有語句之後。 現已不再需要這麼做。

### <a name="requirements"></a>需求

**標題:** afx.h

## <a name="debug_only"></a><a name="debug_only"></a>DEBUG_ONLY

在除錯模式下(定義 **_DEBUG**符號時),DEBUG_ONLY計算其參數。

```
DEBUG_ONLY(expression)
```

### <a name="remarks"></a>備註

在發佈版本中,DEBUG_ONLY不評估其參數。 當您的代碼應僅在調試生成中執行時,這非常有用。

DEBUG_ONLY巨集等效於`#ifdef _DEBUG``#endif`帶的周邊*表示式*。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#32](../../mfc/codesnippet/cpp/diagnostic-services_6.cpp)]

### <a name="requirements"></a>需求

**標題:** afx.h

### <a name="ensure-and-ensure_valid"></a><a name="ensure"></a>確保和ENSURE_VALID

用於驗證數據正確性。

### <a name="syntax"></a>語法

```
ENSURE(  booleanExpression )
ENSURE_VALID( booleanExpression  )
```

### <a name="parameters"></a>參數

*布林運算式*<br/>
指定要測試的布爾表達式。

### <a name="remarks"></a>備註

這些宏的目的是改進參數的驗證。 宏可防止進一步處理代碼中不正確的參數。 與 ASSERT 宏不同,"確保"宏除了生成斷言外,還引發異常。

宏根據專案配置以兩種方式工作。 宏調用 ASSERT,然後在斷言失敗時引發異常。 因此,在調試配置(即定義_DEBUG)中,宏生成斷言和異常,而在發佈配置中,宏僅生成異常(ASSERT 不評估發佈配置中的表達式)。

宏ENSURE_ARG類似於"確保"宏。

ENSURE_VALID調用ASSERT_VALID宏(僅在調試生成中具有效果)。 此外,如果指標為 NULL,ENSURE_VALID將引發異常。 NULL 測試在除錯和發佈配置中都執行。

如果其中任何一個測試失敗,警報消息的顯示方式與 ASSERT 相同。 如果需要,宏將引發無效的參數異常。

### <a name="requirements"></a>需求

**標題:** afx.h

## <a name="this_file"></a><a name="this_file"></a>THIS_FILE

展開到正在編譯的檔的名稱。

### <a name="syntax"></a>語法

```
THIS_FILE
```

### <a name="remarks"></a>備註

該資訊由 ASSERT 和 VERIFY 宏使用。 應用程式精靈和程式碼精靈將宏放在他們創建的原始碼檔中。

### <a name="example"></a>範例

```cpp
#ifdef _DEBUG
#undef THIS_FILE
static char THIS_FILE[] = __FILE__;
#endif

// __FILE__ is one of the six predefined ANSI C macros that the
// compiler recognizes.
```

### <a name="requirements"></a>需求

**標題:** afx.h

## <a name="trace"></a><a name="trace"></a>追蹤

將指定的字串發送到當前應用程式的除錯器。

```
TRACE(exp)
TRACE(DWORD  category,  UINT  level, LPCSTR lpszFormat, ...)
```

### <a name="remarks"></a>備註

有關 TRACE的說明,請參閱[ATLTRACE2。](../../atl/reference/debugging-and-error-reporting-macros.md#atltrace2) TRACE 和 ATLTRACE2 具有相同的行為。

在 MFC 的調試版本中,此宏將指定的字串發送到當前應用程式的調試器。 在發佈版本中,此宏不會編譯到任何內容(根本不生成任何代碼)。

有關詳細資訊,請參閱除錯[MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。

### <a name="requirements"></a>需求

**標題:** afx.h

## <a name="verify"></a><a name="verify"></a>驗證

在 MFC 的調試版本中,評估其參數。

```
VERIFY(booleanExpression)
```

### <a name="parameters"></a>參數

*布林運算式*<br/>
指定計算為非零或 0 的運算式(包括指標值)。

### <a name="remarks"></a>備註

如果結果為 0,宏將列印診斷消息並停止程式。 如果條件為非零,則不執行任何操作。

診斷資訊的格式如下

`assertion failed in file <name> in line <num>`

*其中名稱*是源文件的名稱 *,num*是源檔中失敗的斷言的行號。

在 MFC 的發表版本中,VERIFY 會評估表達式,但不會列印或中斷程式。 例如,如果表達式是函數調用,則將發出調用。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#198](../../mfc/codesnippet/cpp/diagnostic-services_7.cpp)]

### <a name="requirements"></a>需求

**標題:** afx.h

## <a name="afxdump-cdumpcontext-in-mfc"></a><a name="cdumpcontext_in_mfc"></a>afxDump(MFC 中的 CDumpContext)

在應用程式中提供基本的物件轉儲功能。

```
CDumpContext  afxDump;
```

### <a name="remarks"></a>備註

`afxDump`是預先定義的[CDumpContext](../../mfc/reference/cdumpcontext-class.md)物件,允許`CDumpContext`您將資訊 發送到除錯器輸出視窗或調試終端。 通常,作為參數`afxDump`提供`CObject::Dump`到 。

在 Windows NT 和`afxDump`所有版本的 Windows 下,在除錯應用程式時,輸出將發送到可視化 C++的輸出調試視窗。

此變數僅在 MFC 的調試版本中定義。 關於詳細資訊,`afxDump`請參考[除錯 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#23](../../mfc/codesnippet/cpp/diagnostic-services_8.cpp)]

### <a name="requirements"></a>需求

**標題:** afx.h

## <a name="afxdump-internal"></a><a name="afxdump"></a>AfxDump(內部)

MFC 用於在調試時轉儲物件狀態的內部函數。

### <a name="syntax"></a>語法

```
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>參數

*Pob*<br/>
指向派生自`CObject`的類物件的指標。

### <a name="remarks"></a>備註

`AfxDump`呼叫物件`Dump`的成員函數並將資訊發送到`afxDump`變數指定的位置。 `AfxDump`僅在 MFC 的調試版本中可用。

程式代碼不應調用`AfxDump`,而應調用相應`Dump`對象 的成員函數。

### <a name="requirements"></a>需求

**標題:** afx.h

## <a name="afxmemdf"></a><a name="afxmemdf"></a>afxMemDF

此變數可從除錯器或程式存取,並允許您調整分配診斷。

```
int  afxMemDF;
```

### <a name="remarks"></a>備註

`afxMemDF`可以具有枚舉指定的以下值`afxMemDF`:

- `allocMemDF`打開調試分配器(調試庫中的預設設置)。

- `delayFreeMemDF`延遲釋放記憶體。 當程式釋放記憶體塊時,分配器不會將該記憶體返回到基礎操作系統。 這將對程式造成最大的記憶體壓力。

- `checkAlwaysMemDF``AfxCheckMemory`每次分配或釋放記憶體時調用。 這將顯著減緩記憶體分配和處理。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#30](../../mfc/codesnippet/cpp/diagnostic-services_9.cpp)]

### <a name="requirements"></a>需求

**標題:** afx.h

## <a name="afxcheckerror"></a><a name="afxcheckerror"></a>AfxCheck錯誤

這個函式會測試傳遞的 SCODE，以查看其是否為錯誤。

```
void AFXAPI AfxCheckError(SCODE sc);
throw CMemoryException*
throw COleException*
```

### <a name="remarks"></a>備註

如果是錯誤，函式會擲回例外狀況。 如果傳遞的 SCODE E_OUTOFMEMORY,則函數通過調用[AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception)引發[CMemoryException。](../../mfc/reference/cmemoryexception-class.md) 否則,函數通過調用[AfxThrowOleException](exception-processing.md#afxthrowoleexception)引發[COleException。](../../mfc/reference/coleexception-class.md)

這個函式可用來檢查對應用程式中 OLE 函式呼叫的傳回值。 藉由在應用程式中以此函式測試傳回值，您可以用最少的程式碼因應錯誤狀況。

> [!NOTE]
> 這個函式在偵錯和非偵錯組建中具有相同的效果。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#33](../../mfc/codesnippet/cpp/diagnostic-services_10.cpp)]

### <a name="requirements"></a>需求

**標題:** afx.h

## <a name="afxcheckmemory"></a><a name="afxcheckmemory"></a>AfxCheck記憶體

此函數驗證可用記憶體池並根據需要列印錯誤消息。

```
BOOL  AfxCheckMemory();
```

### <a name="return-value"></a>傳回值

如果沒有記憶體錯誤,則非零;否則 0。

### <a name="remarks"></a>備註

如果函數未檢測到記憶體損壞,則不會列印任何內容。

將檢查當前在堆上分配的所有記憶體區,包括**由新**分配但未通過直接呼叫基礎記憶體分配器(如**malloc**函數`GlobalAlloc`或 Windows 函數)分配的記憶體區塊。 如果發現任何塊已損壞,則會將消息列印到調試器輸出。

如果引入列

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

在程式模組中,然後後續調用以`AfxCheckMemory`顯示分配記憶體的檔名和行號。

> [!NOTE]
> 如果模組包含可序列化類的一個或多個實現,則必須將`#define`該行放在最後一個IMPLEMENT_SERIAL宏調用之後。

此函數僅適用於 MFC 的調試版本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCObjectSample#26](../../mfc/codesnippet/cpp/diagnostic-services_11.cpp)]

### <a name="requirements"></a>需求

**標題:** afx.h

## <a name="afxdump-mfc"></a><a name="afxdump"></a>AfxDump (MFC)

在調試器中調用此函數,以在調試時轉儲對象的狀態。

```
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>參數

*Pob*<br/>
指向派生自`CObject`的類物件的指標。

### <a name="remarks"></a>備註

`AfxDump`呼叫物件`Dump`的成員函數並將資訊發送到`afxDump`變數指定的位置。 `AfxDump`僅在 MFC 的調試版本中可用。

程式代碼不應調用`AfxDump`,而應調用相應`Dump`對象 的成員函數。

### <a name="requirements"></a>需求

**標題:** afx.h

## <a name="afxdumpstack"></a><a name="afxdumpstack"></a>AfxDumpStack

此全域函數可用於生成當前堆疊的映射。

```
void AFXAPI AfxDumpStack(DWORD dwTarget = AFX_STACK_DUMP_TARGET_DEFAULT);
```

### <a name="parameters"></a>參數

*dwTarget*<br/>
指示轉儲輸出的目標。 可以使用位 OR ( **&#124;**) 運算子組合的可能值如下所示:

- AFX_STACK_DUMP_TARGET_TRACE通過[TRACE](#trace)宏發送輸出。 TRACE 宏僅在調試生成中生成輸出;它在發佈版本中不生成輸出。 此外,TRACE 可以重定向到調試器之外的其他目標。

- AFX_STACK_DUMP_TARGET_DEFAULT將轉儲輸出發送到預設目標。 對於調試生成,輸出將轉到 TRACE 宏。 在版本版本中,輸出將轉到剪貼簿。

- AFX_STACK_DUMP_TARGET_CLIPBOARD僅將輸出發送到剪貼簿。 使用CF_TEXT剪貼簿格式,數據以純文本形式放置在剪貼簿上。

- AFX_STACK_DUMP_TARGET_BOTH同時將輸出發送到剪貼簿和 TRACE 宏。

- AFX_STACK_DUMP_TARGET_ODS通過 Win32`OutputDebugString()`函數將輸出直接發送到調試器。 當除錯器附加到行程時,此選項將在調試和發佈版本中生成調試器輸出。 AFX_STACK_DUMP_TARGET_ODS始終到達調試器(如果已連接),並且無法重定向。

### <a name="remarks"></a>備註

下面的範例反映了從 MFC 對話方塊應用程式中的`AfxDumpStack`按鈕處理程式 呼叫產生的輸出的一行:

```Output
=== begin AfxDumpStack output ===
00427D55: DUMP2\DEBUG\DUMP2.EXE! void AfxDumpStack(unsigned long) + 181 bytes
0040160B: DUMP2\DEBUG\DUMP2.EXE! void CDump2Dlg::OnClipboard(void) + 14 bytes
0044F884: DUMP2\DEBUG\DUMP2.EXE! int _AfxDispatchCmdMsg(class CCmdTarget *,
unsigned int,int,void ( CCmdTarget::*)(void),void *,unsigned int,struct
AFX_CMDHANDLE
0044FF7B: DUMP2\DEBUG\DUMP2.EXE! virtual int CCmdTarget::OnCmdMsg(unsigned
int,int,void *,struct AFX_CMDHANDLERINFO *) + 626 bytes
00450C71: DUMP2\DEBUG\DUMP2.EXE! virtual int CDialog::OnCmdMsg(unsigned
int,int,void *,struct AFX_CMDHANDLERINFO *) + 36 bytes
00455B27: DUMP2\DEBUG\DUMP2.EXE! virtual int CWnd::OnCommand(unsigned
int,long) + 312 bytes
00454D3D: DUMP2\DEBUG\DUMP2.EXE! virtual int CWnd::OnWndMsg(unsigned
int,unsigned int,long,long *) + 83 bytes
00454CC0: DUMP2\DEBUG\DUMP2.EXE! virtual long CWnd::WindowProc(unsigned
int,unsigned int,long) + 46 bytes
004528D9: DUMP2\DEBUG\DUMP2.EXE! long AfxCallWndProc(class CWnd *,struct
HWND__ *,unsigned int,unsigned int,long) + 237 bytes
00452D34: DUMP2\DEBUG\DUMP2.EXE! long AfxWndProc(struct HWND__ *,unsigned
int,unsigned int,long) + 129 bytes
BFF73663: WINDOWS\SYSTEM\KERNEL32.DLL! ThunkConnect32 + 2148 bytes
BFF928E0: WINDOWS\SYSTEM\KERNEL32.DLL! UTUnRegister + 2492 bytes
=== end AfxDumpStack() output ===
```

上面輸出中的每一行指示最後一個函數調用的位址、包含函數調用的模組的完整路徑名稱以及調用的函數原型。 如果堆疊上的函數調用未在函數的確切位址發生,則顯示位元組的偏移量。

例如,下表描述了上述輸出的第一行:

|輸出|描述|
|------------|-----------------|
|`00427D55:`|最後一個函數調用的返回位址。|
|`DUMP2\DEBUG\DUMP2.EXE!`|包含函數調用的模組的完整路徑名稱。|
|`void AfxDumpStack(unsigned long)`|調用的功能原型。|
|`+ 181 bytes`|從函數原型的位址(在本例中)`void AfxDumpStack(unsigned long)`到返回位址(在本例中為) 的偏移(在本例`00427D55`中為 )。|

`AfxDumpStack`在 MFC 庫的調試和非調試版本中可用;但是,即使可執行檔在共用 DLL 中使用 MFC,該函數始終以靜態方式連結。 在共用庫實現中,該函數位於 MFCS42 中。LIB 庫(及其變體)。

要成功使用此功能,請使用:

- 檔圖像HLP。DLL 必須位於您的路徑上。 如果沒有此 DLL,該函數將顯示一條錯誤消息。 有關 IMAGEHLP 提供的函數集的資訊,請參閱[影像說明庫](/windows/win32/Debug/image-help-library)。

- 堆疊上具有幀的模組必須包括調試資訊。 如果它們不包含調試資訊,則函數仍將生成堆疊跟蹤,但跟蹤將不太詳細。

### <a name="requirements"></a>需求

**標題:** afx.h

## <a name="afxenablememoryleakdump"></a><a name="afxenablememoryleakdump"></a>Afxenable記憶體洩漏轉儲

啟用並禁用AFX_DEBUG_STATE析構函數中的記憶體洩漏轉儲。

```
BOOL AFXAPI AfxEnableMemoryLeakDump(BOOL bDump);
```

### <a name="parameters"></a>參數

*b轉儲*<br/>
[在]TRUE 表示記憶體洩漏轉儲已啟用;如果已啟用,則為 TRUE。FALSE 表示記憶體洩漏轉儲已禁用。

### <a name="return-value"></a>傳回值

此旗標先前的值。

### <a name="remarks"></a>備註

當應用程式卸載 MFC 程式庫時，MFC 程式庫會檢查記憶體流失。 此時,任何記憶體洩漏都通過 Visual Studio 的**調試**視窗報告給使用者。

如果您的應用程式在 MFC 程式庫之前先載入另一個程式庫，系統會將該程式庫中的一些記憶體配置誤報為記憶體流失。 因為 MFC 程式庫發生記憶體流失誤報的情況，這些誤報可能會導致您的應用程式關閉速度很慢。 在這種情況下，請使用 `AfxEnableMemoryLeakDump` 以停用記憶體流失傾印。

> [!NOTE]
> 如果您使用這個方法來關閉記憶體流失傾印，就不會收到應用程式中有效的記憶體流失報告。 因此，僅有當您確信記憶體流失報告包含誤報的記憶體流失，才建議使用這個方法。

### <a name="requirements"></a>需求

**標題:** afx.h

## <a name="afxenablememorytracking"></a><a name="afxenablememorytracking"></a>Afx 啟用記憶體追蹤

診斷記憶體追蹤通常在 MFC 的調試版本中啟用。

```
BOOL AfxEnableMemoryTracking(BOOL bTrack);
```

### <a name="parameters"></a>參數

*b軌道*<br/>
將此值設定為 TRUE 將打開記憶體追蹤;FALSE 將其關閉。

### <a name="return-value"></a>傳回值

跟蹤啟用標誌的上一個設置。

### <a name="remarks"></a>備註

使用此函數可以禁用對代碼部分的跟蹤,您知道這些部分正在正確分配塊。

關於詳細資訊,`AfxEnableMemoryTracking`請參考[除錯 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。

> [!NOTE]
> 此函數僅適用於 MFC 的調試版本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#24](../../mfc/codesnippet/cpp/diagnostic-services_12.cpp)]

### <a name="requirements"></a>需求

**標題:** afx.h

## <a name="afxismemoryblock"></a><a name="afxismemoryblock"></a>AfxIs記憶體塊

測試記憶體位址,以確保它表示由**new**的診斷版本分配的當前活動記憶體區塊。

```
BOOL AfxIsMemoryBlock(
    const void* p,
    UINT nBytes,
    LONG* plRequestNumber = NULL);
```

### <a name="parameters"></a>參數

*P*<br/>
指向要測試的記憶體塊。

*n 位元組*<br/>
包含以位元組為單位的記憶體區塊的長度。

*plRequest 編號*<br/>
指向將用**long**記憶體區塊的分配序列號填充的長整數,如果它不表示當前活動記憶體塊,則指向零。

### <a name="return-value"></a>傳回值

如果當前分配了記憶體塊且長度正確,則非零;否則 0。

### <a name="remarks"></a>備註

它還根據原始分配的大小檢查指定的大小。 如果函數返回非零,則分配序列號將在*plRequestNumber*中返回。 此數位表示塊相對於所有其他**新**分配的分配順序。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#27](../../mfc/codesnippet/cpp/diagnostic-services_13.cpp)]

### <a name="requirements"></a>需求

**標題:** afx.h

## <a name="afxisvalidaddress"></a><a name="afxisvalidaddress"></a>AfxIsValid位址

測試任何記憶體位址,以確保它完全包含在程式的記憶體空間中。

```
BOOL AfxIsValidAddress(
    const void* lp,
    UINT nBytes,
    BOOL bReadWrite = TRUE);
```

### <a name="parameters"></a>參數

*lp*<br/>
指向要測試的記憶體位址。

*n 位元組*<br/>
包含要測試的記憶體位元組數。

*bReadWrite*<br/>
指定記憶體是用於讀取和寫入 (TRUE) 還是僅用於讀取 (FALSE)。

### <a name="return-value"></a>傳回值

在調試生成中,如果指定的記憶體塊完全包含在程式的記憶體空間中,則非零;否則 0。

在非除錯產生中,如果*lp*不是 NULL,則非零;否則 0。

### <a name="remarks"></a>備註

該位址不限於**由 new**分配的塊。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#28](../../mfc/codesnippet/cpp/diagnostic-services_14.cpp)]

### <a name="requirements"></a>需求

**標題:** afx.h

## <a name="afxisvalidstring"></a><a name="afxisvalidstring"></a>AfxIs 有效字串

使用此函數可確定指向字串的指標是否有效。

```
BOOL  AfxIsValidString(
    LPCSTR lpsz,
    int nLength = -1);
```

### <a name="parameters"></a>參數

*lpsz*<br/>
要測試的指標。

*N 長度*<br/>
指定要測試的字串的長度(以位元組為單位)。 值 -1 表示字串將為 null 終止。

### <a name="return-value"></a>傳回值

在除錯產生中,如果指定的指標指向指定大小的字串,則非零;否則 0。

在非調試生成中,如果*lpsz*不是 NULL,則非零;否則 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#29](../../mfc/codesnippet/cpp/diagnostic-services_15.cpp)]

### <a name="requirements"></a>需求

**標題:** afx.h

## <a name="afxsetallochook"></a><a name="afxsetallochook"></a>阿FXSetAllocHook

設置一個挂鉤,在分配每個記憶體塊之前啟用指定函數的調用。

```
AFX_ALLOC_HOOK AfxSetAllocHook(AFX_ALLOC_HOOK pfnAllocHook);
```

### <a name="parameters"></a>參數

*普芬·洛克胡克*<br/>
指定要呼叫的函數的名稱。 有關分配函數的原型,請參閱備註。

### <a name="return-value"></a>傳回值

如果要允許分配,則非零;否則 0。

### <a name="remarks"></a>備註

Microsoft 基礎類庫調試記憶體分配器可以調用使用者定義的挂鉤函數,以允許使用者監視記憶體分配並控制是否允許分配。 分配掛鉤函數的原型化如下:

**BOOL AFXAPI 阿洛克胡克(size_t,** `nSize` **BOOL** `bObject` **, 長**`lRequestNumber` **);**

*nSize*<br/>
建議記憶體分配的大小。

*bObject*<br/>
如果分配是派生`CObject`物件的,則為 TRUE;否則 FALSE。

*l 請求號碼*<br/>
記憶體分配的序列號。

請注意,AFXAPI 調用約定意味著被調用人必須從堆疊中刪除參數。

### <a name="requirements"></a>需求

**標題:** afx.h

## <a name="afxdoforallclasses"></a><a name="afxdoforallclasses"></a>阿FXDofor所有類

調用應用程式記憶體空間中所有可`CObject`序列化派生類的指定反覆運算函數。

```
void
AFXAPI AfxDoForAllClasses(
    void (* pfn)(const CRuntimeClass* pClass, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>參數

*普芬*<br/>
指向要為每個類調用的反覆運算函數。 函數參數是指向`CRuntimeClass`物件的指標和指向調用方提供到函數的額外數據的空指標。

*pContext*<br/>
指向調用方可以向反覆運算函數提供的可選數據。 此指標可以是 NULL。

### <a name="remarks"></a>備註

可`CObject`序列化派生類是使用DECLARE_SERIAL宏派生的類。 每次調用*pContext*`AfxDoForAllClasses`中傳遞給的指標都會傳遞給指定的反覆運算函數。

> [!NOTE]
> 此函數僅適用於 MFC 的調試版本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#113](../../mfc/codesnippet/cpp/diagnostic-services_16.cpp)]

[!code-cpp[NVC_MFCCollections#114](../../mfc/codesnippet/cpp/diagnostic-services_17.cpp)]

### <a name="requirements"></a>需求

**標題:** afx.h

## <a name="afxdoforallobjects"></a><a name="afxdoforallobjects"></a>AfxDofor所有物件

為派生自`CObject`已使用**new**分配的所有物件執行指定的反覆運算函數。

```
void AfxDoForAllObjects(
    void (* pfn)(CObject* pObject, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>參數

*普芬*<br/>
指向要為每個物件執行的反覆運算函數。 函數參數是指向`CObject`a 的指標,是指向調用方向函數提供的額外數據的空指標。

*pContext*<br/>
指向調用方可以向反覆運算函數提供的可選數據。 此指標可以是 NULL。

### <a name="remarks"></a>備註

不會枚舉堆疊、全域或嵌入物件。 每次調用`AfxDoForAllObjects`*pContext*中傳遞到的指標都會傳遞給指定的反覆運算函數。

> [!NOTE]
> 此函數僅適用於 MFC 的調試版本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#115](../../mfc/codesnippet/cpp/diagnostic-services_18.cpp)]

[!code-cpp[NVC_MFCCollections#116](../../mfc/codesnippet/cpp/diagnostic-services_19.cpp)]

## <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)<br/>
[CObject::Dump](cobject-class.md#dump)
