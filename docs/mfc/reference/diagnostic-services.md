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
ms.openlocfilehash: 931545e6a79ecaa59d147e48265649ef20466fbd
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837394"
---
# <a name="diagnostic-services"></a>診斷服務

MFC 程式庫提供許多診斷服務，可讓您更輕鬆地對程式進行偵錯。 這些診斷服務包含巨集和全域函式，可讓您追蹤程式的記憶體配置、在執行階段傾印物件的內容，以及在執行階段列印偵錯訊息。 診斷服務的巨集和全域函式可分為下列分類：

- 一般診斷巨集

- 一般診斷函式和變數

- 物件診斷函式

這些巨集和函式都可以在 MFC 的偵錯和發行版本中，供所有衍生自 `CObject` 的類別使用。 不過，除了 DEBUG_NEW 之外，還會確認發行版本中沒有任何內容。

在偵錯程式庫中，所有配置的記憶體區塊都會以一系列「保護位元組」(Guard Byte) 來提供支援。 如果這些位元組受到錯誤記憶體寫入的干擾，則診斷常式可能會回報問題。 如果您在實作檔中包含此行：

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

在您的執行檔中，的所有呼叫 **`new`** 都會儲存發生記憶體配置的檔案名和行號。 [函數 [CMemoryState：:D umpallobjectssince](cmemorystate-structure.md#dumpallobjectssince) ] 會顯示此額外資訊，讓您找出記憶體流失。 另請參閱類別 [CDumpCoNtext](../../mfc/reference/cdumpcontext-class.md) ，以取得診斷輸出的其他資訊。

此外，C 執行階段程式庫也支援一組可用來偵錯應用程式的診斷函式。 如需詳細資訊，請參閱《執行時間程式庫參考》中的 [Debug 常式](../../c-runtime-library/debug-routines.md) 。

### <a name="mfc-general-diagnostic-macros"></a>MFC 一般診斷巨集

|名稱|描述|
|-|-|
|[斷言](#assert)|如果指定的運算式在程式庫的偵錯版本中評估為 FALSE，則會列印訊息，再中止程式。|
|[ASSERT_KINDOF](#assert_kindof)|測試某物件是屬於指定類別，還是屬於該類別的衍生類別。|
|[ASSERT_VALID](#assert_valid)|藉由呼叫物件的 `AssertValid` 成員函式來測試其內部有效性，通常會覆寫自 `CObject`。|
|[DEBUG_NEW](#debug_new)|提供偵錯模式中所有物件配置的檔案名稱和行號，以協助找出記憶體流失的問題。|
|[DEBUG_ONLY](#debug_only)|類似於 ASSERT，但不會測試運算式的值；適用於只能在偵錯模式中執行的程式碼。|
|[確定並 ENSURE_VALID](#ensure)|用來驗證資料的正確性。|
|[THIS_FILE](#this_file)|展開至要編譯之檔案的名稱。|
|[跟蹤](#trace)|提供此程式庫之偵錯版本中類似 `printf`的功能。|
|[驗證](#verify)|類似於 ASSERT，但不僅會評估此程式庫之發行版本中的運算式，也會評估偵錯版本中的運算式。|

### <a name="mfc-general-diagnostic-variables-and-functions"></a>MFC 一般診斷變數和函式

|名稱|描述|
|-|-|
|[afxDump](#afxdump)|將 [CDumpCoNtext](../../mfc/reference/cdumpcontext-class.md) 資訊傳送至偵錯工具輸出視窗或 debug 終端機的全域變數。|
|[afxMemDF](#afxmemdf)|全域變數，可控制偵錯記憶體配置器的行為。|
|[AfxCheckError](#afxcheckerror)|全域變數，可用來測試所傳遞的 SCODE 以查看其是否為錯誤；如果是，則擲回適當的錯誤。|
|[AfxCheckMemory](#afxcheckmemory)|檢查目前配置之所有記憶體的完整性。|
|[AfxDebugBreak](#afxdebugbreak)|導致中斷執行。|
|[afxDump](#cdumpcontext_in_mfc)|如果在偵錯工具中呼叫，則會一面進行偵錯，一面傾印物件的狀態。|
|[afxDump](#afxdump)|內建函式，會在進行偵錯工具時傾印物件的狀態。|
|[AfxDumpStack](#afxdumpstack)|產生目前堆疊的映像。 這個函式一律會以靜態方式連結。|
|[AfxEnableMemoryLeakDump](#afxenablememoryleakdump)|啟用記憶體流失傾印。|
|[AfxEnableMemoryTracking](#afxenablememorytracking)|開啟和關閉記憶體追蹤。|
|[AfxIsMemoryBlock](#afxismemoryblock)|確認已適當地配置記憶體區塊。|
|[AfxIsValidAddress](#afxisvalidaddress)|確認記憶體位址範圍落在程式的範圍內。|
|[AfxIsValidString](#afxisvalidstring)|判斷字串指標是否有效。|
|[AfxSetAllocHook](#afxsetallochook)|允許對每個記憶體配置呼叫函式。|

### <a name="mfc-object-diagnostic-functions"></a>MFC 物件診斷函式

|名稱|描述|
|-|-|
|[AfxDoForAllClasses](#afxdoforallclasses)|針對所有可支援執行階段類型檢查的 `CObject`衍生類別執行指定的函式。|
|[AfxDoForAllObjects](#afxdoforallobjects)|在使用配置的所有衍生物件上執行指定的函 `CObject` 式 **`new`** 。|

### <a name="mfc-compilation-macros"></a>MFC 編譯宏

|名稱|描述|
|-|-|
|[_AFX_SECURE_NO_WARNINGS](#afx_secure_no_warnings)|隱藏關於使用被取代 MFC 的功能的編譯器警告。|

## <a name="_afx_secure_no_warnings"></a><a name="afx_secure_no_warnings"></a> _AFX_SECURE_NO_WARNINGS

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

## <a name="afxdebugbreak"></a><a name="afxdebugbreak"></a> AfxDebugBreak

呼叫此函式，在 `AfxDebugBreak` 執行您的 MFC 應用程式的偵錯工具時，于呼叫的位置)  (中斷。

### <a name="syntax"></a>語法

```cpp
void AfxDebugBreak( );
```

### <a name="remarks"></a>備註

`AfxDebugBreak` 在 MFC 應用程式的發行版本中沒有任何作用，而且應該移除。 此函式應該只在 MFC 應用程式中使用。 使用 WIN32 API 版本， `DebugBreak` 在非 MFC 應用程式中導致中斷。

### <a name="requirements"></a>規格需求

**標頭：** afxver_。h

## <a name="assert"></a><a name="assert"></a> 斷言

評估其引數。

```
ASSERT(booleanExpression)
```

### <a name="parameters"></a>參數

*booleanExpression*<br/>
指定運算式 (包括判斷值為非零或0的指標值) 。

### <a name="remarks"></a>備註

如果結果是0，宏會列印診斷訊息，並中止程式。 如果條件為非零，則不會執行任何動作。

診斷資訊的格式如下

`assertion failed in file <name> in line <num>`

其中 *name* 是原始程式檔的名稱，而 *num* 是原始程式檔中失敗之判斷提示的行號。

在 MFC 的發行版本中，ASSERT 不會評估運算式，因此不會中斷程式。 如果運算式必須在任何環境中評估，請使用 VERIFY 宏取代 ASSERT。

> [!NOTE]
> 此函式僅適用于 MFC 的偵錯工具版本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#44](../../mfc/codesnippet/cpp/diagnostic-services_2.cpp)]

### <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="assert_kindof"></a><a name="assert_kindof"></a> ASSERT_KINDOF

這個宏會判斷提示的物件是指定類別的物件，或是衍生自指定類別之類別的物件。

```
ASSERT_KINDOF(classname, pobject)
```

### <a name="parameters"></a>參數

*classname*<br/>
衍生類別的名稱 `CObject` 。

*pobject*<br/>
類別物件的指標。

### <a name="remarks"></a>備註

*Pobject*參數應該是物件的指標，而且可以是 **`const`** 。 指向的物件和類別必須支援 `CObject` 執行時間類別資訊。 例如，若要確保 `pDocument` 是類別的物件指標 `CMyDoc` ，或其任何衍生物件的指標，您可以撰寫程式碼：

[!code-cpp[NVC_MFCDocView#194](../../mfc/codesnippet/cpp/diagnostic-services_3.cpp)]

使用宏與撰寫 `ASSERT_KINDOF` 程式碼完全相同：

[!code-cpp[NVC_MFCDocView#195](../../mfc/codesnippet/cpp/diagnostic-services_4.cpp)]

此函式僅適用于以 [DECLARE_DYNAMIC] (執行時間-物件--------------服務. md # declare_dynamic 或 [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) 宏所宣告的類別。

> [!NOTE]
> 此函式僅適用于 MFC 的偵錯工具版本。

### <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="assert_valid"></a><a name="assert_valid"></a> ASSERT_VALID

用來測試有關物件內部狀態有效性的假設。

```
ASSERT_VALID(pObject)
```

### <a name="parameters"></a>參數

*pObject*<br/>
指定衍生自之類別的物件 `CObject` ，這個物件具有成員函式的覆寫版本 `AssertValid` 。

### <a name="remarks"></a>備註

ASSERT_VALID 會呼叫 `AssertValid` 傳遞做為其引數之物件的成員函式。

在 MFC 的發行版本中，ASSERT_VALID 不會執行任何動作。 在偵錯工具版本中，它會驗證指標、對 Null 進行檢查，然後呼叫物件本身的成員函式 `AssertValid` 。 如果其中任何一項測試失敗，則會以與 [ASSERT](#assert)相同的方式來顯示警示訊息。

> [!NOTE]
> 此函式僅適用于 MFC 的偵錯工具版本。

如需詳細資訊和範例，請參閱 [偵錯工具 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCObjectSample#19](../../mfc/codesnippet/cpp/diagnostic-services_5.cpp)]

### <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="debug_new"></a><a name="debug_new"></a> DEBUG_NEW

協助找出記憶體流失。

```
#define  new DEBUG_NEW
```

### <a name="remarks"></a>備註

您可以在程式中的任何位置使用 DEBUG_NEW，通常會使用 **`new`** 運算子來配置堆積儲存體。

在 [偵錯工具] 模式中 (**_DEBUG** 符號定義) 時，DEBUG_NEW 會追蹤其所配置之每個物件的檔案名和行號。 然後，當您使用 [CMemoryState：:D umpallobjectssince](cmemorystate-structure.md#dumpallobjectssince) 成員函式時，使用 DEBUG_NEW 配置的每個物件都會以其所配置的檔案名和行號來顯示。

若要使用 DEBUG_NEW，請在原始程式檔中插入下列指示詞：

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

插入此指示詞之後，預處理器會在您使用的任何地方插入 DEBUG_NEW **`new`** ，而 MFC 會執行其餘工作。 當您編譯器的發行版本時，DEBUG_NEW 會解析成簡單的作業 **`new`** ，而且不會產生檔案名和行號資訊。

> [!NOTE]
> 在舊版 MFC (4.1 及更早版本中) 您需要將語句放在 `#define` 所有呼叫 IMPLEMENT_DYNCREATE 或 IMPLEMENT_SERIAL 宏的語句之後。 現已不再需要這麼做。

### <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="debug_only"></a><a name="debug_only"></a> DEBUG_ONLY

在 [偵錯工具] 模式中 (**_DEBUG** 符號定義) 時，DEBUG_ONLY 會評估其引數。

```
DEBUG_ONLY(expression)
```

### <a name="remarks"></a>備註

在發行組建中，DEBUG_ONLY 不會評估其引數。 當您的程式碼應該只在 debug 組建中執行時，這會很有用。

DEBUG_ONLY 宏相當於具有和的*expression*周圍運算式 `#ifdef _DEBUG` `#endif` 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#32](../../mfc/codesnippet/cpp/diagnostic-services_6.cpp)]

### <a name="requirements"></a>規格需求

**標頭：** afx。h

### <a name="ensure-and-ensure_valid"></a><a name="ensure"></a> 確定並 ENSURE_VALID

用來驗證資料的正確性。

### <a name="syntax"></a>語法

```
ENSURE(  booleanExpression )
ENSURE_VALID( booleanExpression  )
```

### <a name="parameters"></a>參數

*booleanExpression*<br/>
指定要測試的布林運算式。

### <a name="remarks"></a>備註

這些宏的目的是要改善參數的驗證。 宏會防止在您的程式碼中進一步處理不正確的參數。 與判斷提示宏不同的是，除了產生判斷提示之外，確定宏還會擲回例外狀況。

宏會根據專案設定，以兩種方式運作。 如果判斷提示失敗，宏會呼叫 ASSERT，然後擲回例外狀況。 因此，在「偵錯工具」（Debug configuration）中 (也就是定義 _DEBUG 的) 宏會在發行設定中產生判斷提示和例外狀況，而宏只會產生例外狀況， (判斷提示不會在發行設定) 中評估運算式。

宏 ENSURE_ARG 的作用就像是「確定」宏。

ENSURE_VALID 會呼叫 ASSERT_VALID 宏 (，此宏只有在) 的 Debug 組建中有效果。 此外，如果指標為 Null，則 ENSURE_VALID 擲回例外狀況。 Null 測試會在 Debug 和 Release 設定中執行。

如果其中任何一項測試失敗，則會以與 ASSERT 相同的方式來顯示警示訊息。 如果需要，宏會擲回不正確引數例外狀況。

### <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="this_file"></a><a name="this_file"></a> THIS_FILE

展開至要編譯之檔案的名稱。

### <a name="syntax"></a>語法

```
THIS_FILE
```

### <a name="remarks"></a>備註

判斷提示會使用此資訊並確認宏。 [應用程式] 和 [程式碼] 嚮導會將宏放在其所建立的原始程式碼檔案中。

### <a name="example"></a>範例

```cpp
#ifdef _DEBUG
#undef THIS_FILE
static char THIS_FILE[] = __FILE__;
#endif

// __FILE__ is one of the six predefined ANSI C macros that the
// compiler recognizes.
```

### <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="trace"></a><a name="trace"></a> 跟蹤

將指定的字串傳送至目前應用程式的偵錯工具。

```
TRACE(exp)
TRACE(DWORD  category,  UINT  level, LPCSTR lpszFormat, ...)
```

### <a name="remarks"></a>備註

如需追蹤的描述，請參閱 [ATLTRACE2](../../atl/reference/debugging-and-error-reporting-macros.md#atltrace2) 。 TRACE 和 ATLTRACE2 具有相同的行為。

在 MFC 的偵錯工具版本中，此宏會將指定的字串傳送至目前應用程式的偵錯工具。 在發行組建中，此宏會編譯成 nothing， (所有) 都不會產生任何程式碼。

如需詳細資訊，請參閱 [偵錯工具 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。

### <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="verify"></a><a name="verify"></a> 驗證

在 MFC 的偵錯工具版本中，會評估其引數。

```
VERIFY(booleanExpression)
```

### <a name="parameters"></a>參數

*booleanExpression*<br/>
指定運算式 (包括判斷值為非零或0的指標值) 。

### <a name="remarks"></a>備註

如果結果是0，宏會列印診斷訊息，並中止程式。 如果條件為非零，則不會執行任何動作。

診斷資訊的格式如下

`assertion failed in file <name> in line <num>`

其中 *name* 是原始程式檔的名稱，而 *num* 是原始程式檔中失敗之判斷提示的行號。

在 MFC 的發行版本中，驗證會評估運算式，但不會列印或中斷程式。 例如，如果運算式是函式呼叫，則會進行呼叫。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#198](../../mfc/codesnippet/cpp/diagnostic-services_7.cpp)]

### <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="afxdump-cdumpcontext-in-mfc"></a><a name="cdumpcontext_in_mfc"></a> MFC 中的 afxDump (CDumpCoNtext) 

在您的應用程式中提供基本的物件傾印功能。

```
CDumpContext  afxDump;
```

### <a name="remarks"></a>備註

`afxDump` 是預先定義的 [CDumpCoNtext](../../mfc/reference/cdumpcontext-class.md) 物件，可讓您將 `CDumpContext` 資訊傳送至偵錯工具輸出視窗或偵錯工具終端。 一般來說，您會提供 `afxDump` 做為的參數 `CObject::Dump` 。

在 [Windows NT] 和 [所有版本的 Windows] 下， `afxDump` 當您對應用程式進行偵錯工具時，輸出會傳送至 Visual C++ 的 [輸出] 偵錯工具。

此變數只會在 MFC 的偵錯工具版本中定義。 如需的詳細資訊 `afxDump` ，請參閱 [偵錯工具 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#23](../../mfc/codesnippet/cpp/diagnostic-services_8.cpp)]

### <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="afxdump-internal"></a><a name="afxdump"></a> AfxDump (內部) 

MFC 在進行偵錯工具時，用來傾印物件狀態的內建函式。

### <a name="syntax"></a>語法

```cpp
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>參數

*Pob*<br/>
衍生自之類別的物件指標 `CObject` 。

### <a name="remarks"></a>備註

`AfxDump` 呼叫物件的成員函式 `Dump` ，並將資訊傳送至變數所指定的位置 `afxDump` 。 `AfxDump` 僅適用于 MFC 的偵錯工具版本。

您的程式碼不應該呼叫 `AfxDump` ，而應該改為呼叫 `Dump` 適當物件的成員函式。

### <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="afxmemdf"></a><a name="afxmemdf"></a> afxMemDF

此變數可從偵錯工具或您的程式存取，並可讓您調整配置診斷。

```
int  afxMemDF;
```

### <a name="remarks"></a>備註

`afxMemDF` 可以有列舉所指定的下列值 `afxMemDF` ：

- `allocMemDF` 開啟偵測器配置器 (預設設定) 的 Debug 程式庫中。

- `delayFreeMemDF` 延遲釋放記憶體。 當您的程式釋放記憶體區塊時，配置器不會將該記憶體傳回至基礎作業系統。 這會將最大的記憶體壓力放在您的程式上。

- `checkAlwaysMemDF``AfxCheckMemory`每次配置或釋放記憶體時呼叫。 這會大幅降低記憶體配置和取消配置。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#30](../../mfc/codesnippet/cpp/diagnostic-services_9.cpp)]

### <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="afxcheckerror"></a><a name="afxcheckerror"></a> AfxCheckError

這個函式會測試傳遞的 SCODE，以查看其是否為錯誤。

```cpp
void AFXAPI AfxCheckError(SCODE sc);
throw CMemoryException*
throw COleException*
```

### <a name="remarks"></a>備註

如果是錯誤，函式會擲回例外狀況。 如果 E_OUTOFMEMORY 傳遞的 SCODE，則函式會藉由呼叫[AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception)擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md) 。 否則，此函式會藉由呼叫[AfxThrowOleException](exception-processing.md#afxthrowoleexception)來擲回[COleException](../../mfc/reference/coleexception-class.md) 。

這個函式可用來檢查對應用程式中 OLE 函式呼叫的傳回值。 藉由在應用程式中以此函式測試傳回值，您可以用最少的程式碼因應錯誤狀況。

> [!NOTE]
> 這個函式在偵錯和非偵錯組建中具有相同的效果。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#33](../../mfc/codesnippet/cpp/diagnostic-services_10.cpp)]

### <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="afxcheckmemory"></a><a name="afxcheckmemory"></a> 時都會 afxcheckmemory

此函數會驗證可用記憶體集區，並視需要列印錯誤訊息。

```
BOOL  AfxCheckMemory();
```

### <a name="return-value"></a>傳回值

如果沒有記憶體錯誤，則為非零;否則為0。

### <a name="remarks"></a>備註

如果函式偵測不到任何記憶體損毀，就不會列印任何專案。

所有目前在堆積上配置的記憶體區塊都會進行檢查，包括配置的記憶體區塊， **`new`** 而不是由直接呼叫基礎記憶體配置器（例如 **malloc** 函式或 Windows 函數）所配置的記憶體區塊 `GlobalAlloc` 。 如果發現任何區塊損毀，則會將訊息列印至偵錯工具輸出。

如果您包含這一行

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

在程式模組中，後續的呼叫會 `AfxCheckMemory` 顯示配置記憶體的檔案名和行號。

> [!NOTE]
> 如果您的模組包含一個或多個可序列化類別的執行，則您必須將該行放在 `#define` 最後一個 IMPLEMENT_SERIAL 宏呼叫之後。

此函式僅適用于 MFC 的偵錯工具版本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCObjectSample#26](../../mfc/codesnippet/cpp/diagnostic-services_11.cpp)]

### <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="afxdump-mfc"></a><a name="afxdump"></a> AfxDump (MFC) 

在偵錯工具中呼叫此函式，以在偵錯工具時傾印物件的狀態。

```cpp
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>參數

*Pob*<br/>
衍生自之類別的物件指標 `CObject` 。

### <a name="remarks"></a>備註

`AfxDump` 呼叫物件的成員函式 `Dump` ，並將資訊傳送至變數所指定的位置 `afxDump` 。 `AfxDump` 僅適用于 MFC 的偵錯工具版本。

您的程式碼不應該呼叫 `AfxDump` ，而應該改為呼叫 `Dump` 適當物件的成員函式。

### <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="afxdumpstack"></a><a name="afxdumpstack"></a> AfxDumpStack

此全域函式可以用來產生目前堆疊的影像。

```cpp
void AFXAPI AfxDumpStack(DWORD dwTarget = AFX_STACK_DUMP_TARGET_DEFAULT);
```

### <a name="parameters"></a>參數

*dwTarget*<br/>
指出傾印輸出的目標。 可能的值可以使用位 OR ( **&#124;**) 運算子來結合，如下所示：

- AFX_STACK_DUMP_TARGET_TRACE 透過 [追蹤](#trace) 宏來傳送輸出。 TRACE 宏只會在 debug 組建中產生輸出;它不會在發行組建中產生任何輸出。 此外，追蹤也可以重新導向至偵錯工具以外的其他目標。

- AFX_STACK_DUMP_TARGET_DEFAULT 將傾印輸出傳送到預設目標。 針對 debug 組建，輸出會移至追蹤宏。 在發行組建中，輸出會移至剪貼簿。

- AFX_STACK_DUMP_TARGET_CLIPBOARD 只會將輸出傳送至剪貼簿。 使用 CF_TEXT 剪貼簿格式，資料會以純文字的形式放置在剪貼簿上。

- AFX_STACK_DUMP_TARGET_BOTH 同時將輸出傳送至剪貼簿和追蹤宏。

- AFX_STACK_DUMP_TARGET_ODS 藉由 Win32 函數將輸出直接傳送至偵錯工具 `OutputDebugString()` 。 當偵錯工具附加至進程時，此選項將會在偵錯工具和發行組建中產生偵錯工具輸出。 AFX_STACK_DUMP_TARGET_ODS 一律會到達偵錯工具 (如果已附加) 且無法重新導向。

### <a name="remarks"></a>備註

下列範例反映從 `AfxDumpStack` MFC 對話應用程式的按鈕處理常式呼叫所產生的單一輸出行：

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

上述輸出中的每一行都會指出最後一個函式呼叫的位址、包含函式呼叫之模組的完整路徑名稱，以及呼叫的函式原型。 如果堆疊上的函式呼叫不會在函式的確切位址上發生，則會顯示位元組的位移。

例如，下表描述上述輸出的第一行：

|輸出|描述|
|------------|-----------------|
|`00427D55:`|最後一個函式呼叫的傳回位址。|
|`DUMP2\DEBUG\DUMP2.EXE!`|包含函式呼叫之模組的完整路徑名稱。|
|`void AfxDumpStack(unsigned long)`|呼叫的函式原型。|
|`+ 181 bytes`|在此情況下，函式原型的位址中的位移（以位元組為單位） (在此案例中， `void AfxDumpStack(unsigned long)`) 為傳回位址 (在此案例中為 `00427D55`) 。|

`AfxDumpStack` 適用于 MFC 程式庫的 debug 和 nondebug 版本;但是，即使您的可執行檔在共用 DLL 中使用 MFC，函式一律會以靜態方式連結。 在共用程式庫的執行中，此函式可在 MFCS42 中找到。LIB 程式庫 (及其變體) 。

若要成功使用此函數：

- 檔案 IMAGEHLP.DLL 必須在您的路徑上。 如果您沒有這個 DLL，此函式會顯示錯誤訊息。 如需 IMAGEHLP.DLL 所提供之函式集的詳細資訊，請參閱 [影像說明庫](/windows/win32/Debug/image-help-library) 。

- 在堆疊上具有框架的模組必須包含偵錯工具資訊。 如果它們不包含調試資訊，函式仍會產生堆疊追蹤，但不會詳細說明追蹤。

### <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="afxenablememoryleakdump"></a><a name="afxenablememoryleakdump"></a> AfxEnableMemoryLeakDump

在 AFX_DEBUG_STATE 的函式中啟用和停用記憶體流失傾印。

```
BOOL AFXAPI AfxEnableMemoryLeakDump(BOOL bDump);
```

### <a name="parameters"></a>參數

*bDump*<br/>
在TRUE 表示已啟用記憶體流失轉儲;FALSE 表示記憶體流失轉儲已停用。

### <a name="return-value"></a>傳回值

此旗標先前的值。

### <a name="remarks"></a>備註

當應用程式卸載 MFC 程式庫時，MFC 程式庫會檢查記憶體流失。 此時，系統會透過 Visual Studio 的 [ **調試** 程式] 視窗，將任何記憶體流失回報給使用者。

如果您的應用程式在 MFC 程式庫之前先載入另一個程式庫，系統會將該程式庫中的一些記憶體配置誤報為記憶體流失。 因為 MFC 程式庫發生記憶體流失誤報的情況，這些誤報可能會導致您的應用程式關閉速度很慢。 在這種情況下，請使用 `AfxEnableMemoryLeakDump` 以停用記憶體流失傾印。

> [!NOTE]
> 如果您使用這個方法來關閉記憶體流失傾印，就不會收到應用程式中有效的記憶體流失報告。 因此，僅有當您確信記憶體流失報告包含誤報的記憶體流失，才建議使用這個方法。

### <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="afxenablememorytracking"></a><a name="afxenablememorytracking"></a> AfxEnableMemoryTracking

診斷記憶體追蹤通常會在 MFC 的偵錯工具版本中啟用。

```
BOOL AfxEnableMemoryTracking(BOOL bTrack);
```

### <a name="parameters"></a>參數

*bTrack*<br/>
將此值設定為 TRUE 會開啟記憶體追蹤;FALSE 關閉。

### <a name="return-value"></a>傳回值

追蹤啟用旗標的先前設定。

### <a name="remarks"></a>備註

使用此函式可停用您知道已正確配置區塊的程式碼區段上的追蹤。

如需的詳細資訊 `AfxEnableMemoryTracking` ，請參閱 [偵錯工具 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。

> [!NOTE]
> 此函式僅適用于 MFC 的偵錯工具版本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#24](../../mfc/codesnippet/cpp/diagnostic-services_12.cpp)]

### <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="afxismemoryblock"></a><a name="afxismemoryblock"></a> AfxIsMemoryBlock

測試記憶體位址，以確保它代表診斷版本所配置的目前作用中記憶體區塊 **`new`** 。

```
BOOL AfxIsMemoryBlock(
    const void* p,
    UINT nBytes,
    LONG* plRequestNumber = NULL);
```

### <a name="parameters"></a>參數

*P*<br/>
指向要測試的記憶體區塊。

*n*<br/>
包含記憶體區塊的長度（以位元組為單位）。

*plRequestNumber*<br/>
指向 **`long`** 將填入記憶體區塊配置序號的整數; 如果不代表目前使用中的記憶體區塊，則為零。

### <a name="return-value"></a>傳回值

如果目前已配置記憶體區塊且長度正確，則為非零。否則為0。

### <a name="remarks"></a>備註

它也會根據原始配置的大小來檢查指定的大小。 如果函數傳回非零值，則會在 *plRequestNumber*中傳回配置序號。 此數位代表配置的區塊相對於所有其他配置的順序 **`new`** 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#27](../../mfc/codesnippet/cpp/diagnostic-services_13.cpp)]

### <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="afxisvalidaddress"></a><a name="afxisvalidaddress"></a> AfxIsValidAddress

測試任何記憶體位址，以確保它完全包含在程式的記憶體空間內。

```
BOOL AfxIsValidAddress(
    const void* lp,
    UINT nBytes,
    BOOL bReadWrite = TRUE);
```

### <a name="parameters"></a>參數

*lp*<br/>
指向要測試的記憶體位址。

*n*<br/>
包含要測試的記憶體位元組數目。

*bReadWrite*<br/>
指定記憶體是否可用於讀取和寫入 (TRUE) 或唯讀取 (FALSE) 。

### <a name="return-value"></a>傳回值

在偵錯工具組建中，如果指定的記憶體區塊完全包含在程式的記憶體空間中，則為非零;否則為0。

在非 debug 組建中，如果 *lp* 不是 Null，則為非零;否則為0。

### <a name="remarks"></a>備註

位址不限於所配置的區塊 **`new`** 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#28](../../mfc/codesnippet/cpp/diagnostic-services_14.cpp)]

### <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="afxisvalidstring"></a><a name="afxisvalidstring"></a> AfxIsValidString

您可以使用此函數來判斷字串的指標是否有效。

```
BOOL  AfxIsValidString(
    LPCSTR lpsz,
    int nLength = -1);
```

### <a name="parameters"></a>參數

*lpsz*<br/>
要測試的指標。

*nLength*<br/>
指定要測試之字串的長度（以位元組為單位）。 -1 的值表示字串將以 null 終止。

### <a name="return-value"></a>傳回值

在 debug 組建中，如果指定的指標指向指定大小的字串，則為非零。否則為0。

在非 debug 組建中，如果 *lpsz* 不是 Null，則為非零;否則為0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#29](../../mfc/codesnippet/cpp/diagnostic-services_15.cpp)]

### <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="afxsetallochook"></a><a name="afxsetallochook"></a> AfxSetAllocHook

設定可以在配置每個記憶體區塊之前呼叫指定函式的勾點。

```
AFX_ALLOC_HOOK AfxSetAllocHook(AFX_ALLOC_HOOK pfnAllocHook);
```

### <a name="parameters"></a>參數

*pfnAllocHook*<br/>
指定要呼叫之函數的名稱。 請參閱配置函數原型的備註。

### <a name="return-value"></a>傳回值

如果您想要允許配置，則為非零。否則為0。

### <a name="remarks"></a>備註

MFC 程式庫 debug 記憶體配置器可呼叫使用者定義的攔截函式，以允許使用者監視記憶體配置，以及控制是否允許配置。 配置攔截函式的原型如下：

**BOOL AFXAPI AllocHook ( size_t** `nSize`**、BOOL** `bObject`**、LONG** `lRequestNumber`**) ;**

*nSize*<br/>
建議的記憶體配置大小。

*bObject*<br/>
如果配置是針對衍生的物件，則為 TRUE， `CObject` 否則為 FALSE。

*lRequestNumber*<br/>
記憶體配置的序號。

請注意，AFXAPI 呼叫慣例暗示被呼叫端必須從堆疊中移除參數。

### <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="afxdoforallclasses"></a><a name="afxdoforallclasses"></a> AfxDoForAllClasses

針對應用程式記憶體空間中的所有可序列化衍生類別，呼叫指定的反復專案函數 `CObject` 。

```cpp
void
AFXAPI AfxDoForAllClasses(
    void (* pfn)(const CRuntimeClass* pClass, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>參數

*pfn*<br/>
指向要針對每個類別呼叫的反復專案函數。 函式引數是物件的指標 `CRuntimeClass` ，以及呼叫端提供給函數之額外資料的 void 指標。

*pContext*<br/>
指向呼叫端可提供給反覆運算函數的選擇性資料。 此指標可以是 Null。

### <a name="remarks"></a>備註

可序列化 `CObject` 衍生類別是使用 DECLARE_SERIAL 宏所衍生的類別。 傳遞至 PCoNtext 的指標 `AfxDoForAllClasses` 會在*pContext*每次呼叫時傳遞至指定的反復專案函數。

> [!NOTE]
> 此函式僅適用于 MFC 的偵錯工具版本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#113](../../mfc/codesnippet/cpp/diagnostic-services_16.cpp)]

[!code-cpp[NVC_MFCCollections#114](../../mfc/codesnippet/cpp/diagnostic-services_17.cpp)]

### <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="afxdoforallobjects"></a><a name="afxdoforallobjects"></a> AfxDoForAllObjects

針對從配置給的所有物件，執行指定的反復專案函數 `CObject` **`new`** 。

```cpp
void AfxDoForAllObjects(
    void (* pfn)(CObject* pObject, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>參數

*pfn*<br/>
指向要針對每個物件執行的反復專案函數。 函式引數是指向的指標 `CObject` ，以及呼叫端提供給函數之額外資料的 void 指標。

*pContext*<br/>
指向呼叫端可提供給反覆運算函數的選擇性資料。 此指標可以是 Null。

### <a name="remarks"></a>備註

堆疊、全域或内嵌物件則不會列舉。 傳遞至 PCoNtext 的 `AfxDoForAllObjects` 指標*pContext*會在每次呼叫時傳遞至指定的反復專案函數。

> [!NOTE]
> 此函式僅適用于 MFC 的偵錯工具版本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#115](../../mfc/codesnippet/cpp/diagnostic-services_18.cpp)]

[!code-cpp[NVC_MFCCollections#116](../../mfc/codesnippet/cpp/diagnostic-services_19.cpp)]

## <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)<br/>
[CObject：:D ump](cobject-class.md#dump)
