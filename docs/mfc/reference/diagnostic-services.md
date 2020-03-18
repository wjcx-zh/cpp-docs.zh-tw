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
ms.openlocfilehash: 6880a6a3d25738bd0480168902044530d06f7e7f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446206"
---
# <a name="diagnostic-services"></a>診斷服務

MFC 程式庫提供許多診斷服務，可讓您更輕鬆地對程式進行偵錯。 這些診斷服務包含巨集和全域函式，可讓您追蹤程式的記憶體配置、在執行階段傾印物件的內容，以及在執行階段列印偵錯訊息。 診斷服務的巨集和全域函式可分為下列分類：

- 一般診斷巨集

- 一般診斷函式和變數

- 物件診斷函式

這些巨集和函式都可以在 MFC 的偵錯和發行版本中，供所有衍生自 `CObject` 的類別使用。 不過，除了 DEBUG_NEW 以外，所有驗證都不會在發行版本中執行任何動作。

在偵錯程式庫中，所有配置的記憶體區塊都會以一系列「保護位元組」(Guard Byte) 來提供支援。 如果這些位元組受到錯誤記憶體寫入的干擾，則診斷常式可能會回報問題。 如果您在實作檔中包含此行：

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

則所有對 **new** 的呼叫都會儲存發生記憶體配置的檔案名稱和行號。 [CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince) 函式會顯示這項額外的資訊，讓您找出記憶體流失的問題。 如需診斷輸出的其他資訊，另請參閱 [CDumpContext](../../mfc/reference/cdumpcontext-class.md) 類別。

此外，C 執行階段程式庫也支援一組可用來偵錯應用程式的診斷函式。 如需詳細資訊，請參閱＜執行階段程式庫參考＞中的 [偵錯常式](../../c-runtime-library/debug-routines.md) 。

### <a name="mfc-general-diagnostic-macros"></a>MFC 一般診斷巨集

|||
|-|-|
|[ASSERT](#assert)|如果指定的運算式在程式庫的偵錯版本中評估為 FALSE，則會列印訊息，再中止程式。|
|[ASSERT_KINDOF](#assert_kindof)|測試物件是指定類別的物件，還是衍生自指定類別之類別的物件。|
|[ASSERT_VALID](#assert_valid)|藉由呼叫物件的 `AssertValid` 成員函式來測試其內部有效性，通常會覆寫自 `CObject`。|
|[DEBUG_NEW](#debug_new)|提供偵錯模式中所有物件配置的檔案名稱和行號，以協助找出記憶體流失的問題。|
|[DEBUG_ONLY](#debug_only)|類似於 ASSERT，但不會測試運算式的值；適用於只能在偵錯模式中執行的程式碼。|
|[確定並 ENSURE_VALID](#ensure)|使用來驗證資料正確性。|
|[THIS_FILE](#this_file)|展開為要編譯的檔案名。|
|[TRACE](#trace)|提供此程式庫之偵錯版本中類似 `printf`的功能。|
|[VERIFY](#verify)|類似於 ASSERT，但不僅會評估此程式庫之發行版本中的運算式，也會評估偵錯版本中的運算式。|

### <a name="mfc-general-diagnostic-variables-and-functions"></a>MFC 一般診斷變數和函式

|||
|-|-|
|[afxDump](#afxdump)|全域變數，可將 [CDumpContext](../../mfc/reference/cdumpcontext-class.md) 資訊傳送至偵錯工具輸出視窗或偵錯終端機。|
|[afxMemDF](#afxmemdf)|全域變數，可控制偵錯記憶體配置器的行為。|
|[AfxCheckError](#afxcheckerror)|全域變數，可用來測試所傳遞的 SCODE 以查看其是否為錯誤；如果是，則擲回適當的錯誤。|
|[AfxCheckMemory](#afxcheckmemory)|檢查目前配置之所有記憶體的完整性。|
|[AfxDebugBreak](#afxdebugbreak)|導致執行中斷。|
|[AfxDump](#cdumpcontext_in_mfc)|如果在偵錯工具中呼叫，則會一面進行偵錯，一面傾印物件的狀態。|
|[AfxDump](#afxdump)|在進行偵錯工具時傾印物件狀態的內部函式。|
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
|[AfxDoForAllObjects](#afxdoforallobjects)|針對所有已透過 `CObject`new **來配置的**衍生物件執行指定函式。|

### <a name="mfc-compilation-macros"></a>MFC 編譯宏

|||
|-|-|
|[_AFX_SECURE_NO_WARNINGS](#afx_secure_no_warnings)|隱藏關於使用被取代 MFC 的功能的編譯器警告。|

## <a name="afx_secure_no_warnings"></a>_AFX_SECURE_NO_WARNINGS

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

## <a name="afxdebugbreak"></a> AfxDebugBreak

呼叫此函式可在執行 MFC 應用程式的 debug 版本時，造成中斷（在呼叫 `AfxDebugBreak`的位置）。

### <a name="syntax"></a>語法

```
void AfxDebugBreak( );
```

### <a name="remarks"></a>備註

`AfxDebugBreak` 在 MFC 應用程式的發行版本中沒有任何作用，應予以移除。 此函式應該只在 MFC 應用程式中使用。 使用 WIN32 API 版本 `DebugBreak`，在非 MFC 應用程式中造成中斷。

### <a name="requirements"></a>需求

**標頭：** afxver_。h

##  <a name="assert"></a>  ASSERT

評估其引數。

```
ASSERT(booleanExpression)
```

### <a name="parameters"></a>參數

*booleanExpression*<br/>
指定評估為非零或0的運算式（包括指標值）。

### <a name="remarks"></a>備註

如果結果為0，宏會列印診斷訊息，並中止程式。 如果條件為非零，則不會執行任何操作。

診斷資訊格式如下

`assertion failed in file <name> in line <num>`

其中*name*是原始程式檔的名稱，而*num*是原始程式檔中失敗之判斷提示的行號。

在 MFC 的發行版本中，ASSERT 不會評估運算式，因此不會中斷程式。 如果必須評估運算式而不考慮環境，請使用 VERIFY 宏來取代 ASSERT。

> [!NOTE]
>  此函式僅適用于 MFC 的「調試」版本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#44](../../mfc/codesnippet/cpp/diagnostic-services_2.cpp)]

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="assert_kindof"></a>  ASSERT_KINDOF

這個宏會判斷提示的物件是指定類別的物件，或是衍生自指定類別的類別物件。

```
ASSERT_KINDOF(classname, pobject)
```

### <a name="parameters"></a>參數

*classname*<br/>
`CObject`衍生類別的名稱。

*pobject*<br/>
類別物件的指標。

### <a name="remarks"></a>備註

*Pobject*參數應該是物件的指標，而且可以是**const**。 指向的物件和類別必須支援 `CObject` 執行時間類別資訊。 例如，為了確保 `pDocument` 是 `CMyDoc` 類別或其任何衍生物件的指標，您可以撰寫程式碼：

[!code-cpp[NVC_MFCDocView#194](../../mfc/codesnippet/cpp/diagnostic-services_3.cpp)]

使用 `ASSERT_KINDOF` 宏與撰寫程式碼完全相同：

[!code-cpp[NVC_MFCDocView#195](../../mfc/codesnippet/cpp/diagnostic-services_4.cpp)]

此函式只適用于使用 [DECLARE_DYNAMIC] （執行時間[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) declare_dynamic-----------------------------

> [!NOTE]
>  此函式僅適用于 MFC 的「調試」版本。

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="assert_valid"></a>  ASSERT_VALID

使用來測試您對物件內部狀態有效性的假設。

```
ASSERT_VALID(pObject)
```

### <a name="parameters"></a>參數

*pObject*<br/>
指定衍生自 `CObject` 之類別的物件，其中包含 `AssertValid` 成員函式的覆寫版本。

### <a name="remarks"></a>備註

ASSERT_VALID 會呼叫當做其引數傳遞之物件的 `AssertValid` 成員函式。

在 MFC 的發行版本中，ASSERT_VALID 不會執行任何操作。 在 Debug 版本中，它會驗證指標、針對 Null 進行檢查，並呼叫物件本身的 `AssertValid` 成員函式。 如果其中任何一項測試失敗，則會以與[ASSERT](#assert)相同的方式來顯示警示訊息。

> [!NOTE]
>  此函式僅適用于 MFC 的「調試」版本。

如需詳細資訊和範例，請參閱[調試 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCObjectSample#19](../../mfc/codesnippet/cpp/diagnostic-services_5.cpp)]

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="debug_new"></a>  DEBUG_NEW

協助找出記憶體流失。

```
#define  new DEBUG_NEW
```

### <a name="remarks"></a>備註

您可以在程式中使用 DEBUG_NEW 的任何位置，通常會使用**NEW**運算子來配置堆積儲存區。

在 [偵錯工具] 模式中（定義 **_DEBUG**符號時），DEBUG_NEW 會追蹤所配置之每個物件的檔案名和行號。 然後，當您使用[CMemoryState：:D umpallobjectssince](cmemorystate-structure.md#dumpallobjectssince)成員函式時，以 DEBUG_NEW 配置的每個物件都會顯示其配置所在的檔案名和行號。

若要使用 DEBUG_NEW，請將下列指示詞插入至原始程式檔：

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

一旦您插入這個指示詞，預處理器就會在您使用**NEW**的位置插入 DEBUG_NEW，而 MFC 則會執行其餘工作。 當您編譯器的發行版本時，DEBUG_NEW 會解析為簡單的**新**作業，而且不會產生檔案名和行號資訊。

> [!NOTE]
>  在舊版 MFC （4.1 和更早版本）中，您需要將 `#define` 語句放在所有呼叫 IMPLEMENT_DYNCREATE 或 IMPLEMENT_SERIAL 宏的語句之後。 現已不再需要這麼做。

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="debug_only"></a>  DEBUG_ONLY

在 [調試] 模式中（定義 **_DEBUG**符號時），DEBUG_ONLY 會評估其引數。

```
DEBUG_ONLY(expression)
```

### <a name="remarks"></a>備註

在發行組建中，DEBUG_ONLY 不會評估其引數。 當您的程式碼應該只在 debug 組建中執行時，這會很有用。

DEBUG_ONLY 宏相當於具有 `#ifdef _DEBUG` 和 `#endif`的周圍*運算式*。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#32](../../mfc/codesnippet/cpp/diagnostic-services_6.cpp)]

### <a name="requirements"></a>需求

**標頭：** afx.h

### <a name="ensure"></a>確定並 ENSURE_VALID

使用來驗證資料正確性。

### <a name="syntax"></a>語法

```
ENSURE(  booleanExpression )
ENSURE_VALID( booleanExpression  )
```

### <a name="parameters"></a>參數

*booleanExpression*<br/>
指定要測試的布林運算式。

### <a name="remarks"></a>備註

這些宏的目的是要改善參數的驗證。 宏會防止在您的程式碼中進一步處理不正確的參數。 與 ASSERT 宏不同的是，除了產生判斷提示之外，確保宏還會擲回例外狀況。

宏的運作方式有兩種，視專案設定而定。 宏會呼叫 ASSERT，然後在判斷提示失敗時擲回例外狀況。 因此，在 Debug 設定（也就是定義 _DEBUG 的位置）中，宏會產生判斷提示和例外狀況，而在發行設定中，宏只會產生例外狀況（ASSERT 不會評估發行設定中的運算式）。

宏 ENSURE_ARG 的作用就像確保宏一樣。

ENSURE_VALID 會呼叫 ASSERT_VALID 宏（其只有在 Debug 組建中才會生效）。 此外，如果指標為 Null，ENSURE_VALID 會擲回例外狀況。 Null 測試會同時在 [調試] 和 [發行] 設定中執行。

如果其中任何一項測試失敗，則會以與 ASSERT 相同的方式來顯示警示訊息。 如有需要，宏會擲回不正確引數例外狀況。
### <a name="requirements"></a>需求

**標頭：** afx.h

## <a name="this_file"></a>THIS_FILE

展開為要編譯的檔案名。

### <a name="syntax"></a>語法

```
THIS_FILE
```

### <a name="remarks"></a>備註

判斷提示會使用此資訊，並驗證宏。 應用程式精靈和程式碼嚮導會將宏放在它們所建立的原始程式碼檔中。

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

**標頭：** afx.h

##  <a name="trace"></a>  TRACE

將指定的字串傳送至目前應用程式的偵錯工具。

```
TRACE(exp)
TRACE(DWORD  category,  UINT  level, LPCSTR lpszFormat, ...)
```

### <a name="remarks"></a>備註

如需追蹤的說明，請參閱[ATLTRACE2](../../atl/reference/debugging-and-error-reporting-macros.md#atltrace2) 。 TRACE 和 ATLTRACE2 具有相同的行為。

在 MFC 的 debug 版本中，這個宏會將指定的字串傳送至目前應用程式的偵錯工具。 在發行組建中，此宏會編譯為沒有任何程式碼（完全不會產生任何程式碼）。

如需詳細資訊，請參閱[調試 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="verify"></a>  VERIFY

在 MFC 的 Debug 版本中，會評估其引數。

```
VERIFY(booleanExpression)
```

### <a name="parameters"></a>參數

*booleanExpression*<br/>
指定評估為非零或0的運算式（包括指標值）。

### <a name="remarks"></a>備註

如果結果為0，宏會列印診斷訊息，並中止程式。 如果條件為非零，則不會執行任何操作。

診斷資訊格式如下

`assertion failed in file <name> in line <num>`

其中*name*是原始程式檔的名稱，而*num*是在原始程式檔中失敗之判斷提示的行號。

在 MFC 的發行版本中，VERIFY 會評估運算式，但不會列印或中斷程式。 例如，如果運算式是函式呼叫，則會進行呼叫。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#198](../../mfc/codesnippet/cpp/diagnostic-services_7.cpp)]

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="cdumpcontext_in_mfc"></a>afxDump （MFC 中的 CDumpCoNtext）

在您的應用程式中提供基本的物件傾印功能。

```
CDumpContext  afxDump;
```

### <a name="remarks"></a>備註

`afxDump` 是預先定義的[CDumpCoNtext](../../mfc/reference/cdumpcontext-class.md)物件，可讓您將 `CDumpContext` 資訊傳送至偵錯工具的 [輸出] 視窗或 [debug] 終端機。 一般來說，您會提供 `afxDump` 做為 `CObject::Dump`的參數。

在 Windows NT 和所有版本的 Windows 中，當您在偵錯工具時，`afxDump` 輸出會傳送C++到視覺效果的 [輸出-debug] 視窗。

這個變數只會在 MFC 的 Debug 版本中定義。 如需 `afxDump`的詳細資訊，請參閱[偵錯工具 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#23](../../mfc/codesnippet/cpp/diagnostic-services_8.cpp)]

### <a name="requirements"></a>需求

**標頭：** afx.h

## <a name="afxdump"></a>AfxDump （內部）

MFC 在進行偵錯工具時用來傾印物件狀態的內建函式。

### <a name="syntax"></a>語法

```
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>參數

*pOb*<br/>
衍生自 `CObject`之類別的物件指標。

### <a name="remarks"></a>備註

`AfxDump` 會呼叫物件的 `Dump` 成員函式，並將資訊傳送至 `afxDump` 變數所指定的位置。 `AfxDump` 只能在 MFC 的 Debug 版本中使用。

您的程式碼不應呼叫 `AfxDump`，但應改為呼叫適當物件的 `Dump` 成員函式。

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="afxmemdf"></a>  afxMemDF

此變數可從偵錯工具或您的程式存取，並可讓您微調配置診斷。

```
int  afxMemDF;
```

### <a name="remarks"></a>備註

`afxMemDF` 可以具有列舉 `afxMemDF`所指定的下列值：

- `allocMemDF` 開啟調試配置器（Debug 程式庫中的預設值）。

- `delayFreeMemDF` 會延遲釋放記憶體。 當您的程式釋放記憶體區塊時，配置器不會將該記憶體傳回給基礎作業系統。 這會將最大記憶體壓力放在您的程式上。

- 每次配置或釋放記憶體時，`checkAlwaysMemDF` 都會呼叫 `AfxCheckMemory`。 這會大幅降低記憶體配置和取消配置。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#30](../../mfc/codesnippet/cpp/diagnostic-services_9.cpp)]

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="afxcheckerror"></a>  AfxCheckError

這個函式會測試傳遞的 SCODE，以查看其是否為錯誤。

```
void AFXAPI AfxCheckError(SCODE sc);
throw CMemoryException*
throw COleException*
```

### <a name="remarks"></a>備註

如果是錯誤，函式會擲回例外狀況。 如果傳遞的 SCODE 是 E_OUTOFMEMORY，則函式會藉由呼叫[AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception)來擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md) 。 否則，函數會藉由呼叫[AfxThrowOleException](exception-processing.md#afxthrowoleexception)來擲回[COleException](../../mfc/reference/coleexception-class.md) 。

這個函式可用來檢查對應用程式中 OLE 函式呼叫的傳回值。 藉由在應用程式中以此函式測試傳回值，您可以用最少的程式碼因應錯誤狀況。

> [!NOTE]
>  這個函式在偵錯和非偵錯組建中具有相同的效果。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#33](../../mfc/codesnippet/cpp/diagnostic-services_10.cpp)]

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="afxcheckmemory"></a>  AfxCheckMemory

此函式會驗證可用的記憶體集區，並視需要列印錯誤訊息。

```
BOOL  AfxCheckMemory();
```

### <a name="return-value"></a>傳回值

如果沒有記憶體錯誤，則為非零;否則為0。

### <a name="remarks"></a>備註

如果函式偵測不到記憶體損毀，就不會列印任何內容。

系統會檢查堆積上目前配置的所有記憶體區塊，包括由**新**配置，但不是由直接呼叫基礎記憶體配置器（例如**malloc**函數或 `GlobalAlloc` Windows 函數）所配置的區塊。 如果發現任何區塊損毀，則會將訊息列印至偵錯工具輸出。

如果您包含這一行

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

在程式模組中，後續的 `AfxCheckMemory` 呼叫會顯示配置給記憶體的檔案名和行號。

> [!NOTE]
>  如果您的模組包含一或多個可序列化類別的執行，則您必須將 `#define` 行放在最後一個 IMPLEMENT_SERIAL 宏呼叫之後。

此函式只適用于 MFC 的調試版本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCObjectSample#26](../../mfc/codesnippet/cpp/diagnostic-services_11.cpp)]

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="afxdump"></a>AfxDump （MFC）

請在偵錯工具中呼叫此函式，以在偵測時傾印物件的狀態。

```
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>參數

*pOb*<br/>
衍生自 `CObject`之類別的物件指標。

### <a name="remarks"></a>備註

`AfxDump` 會呼叫物件的 `Dump` 成員函式，並將資訊傳送至 `afxDump` 變數所指定的位置。 `AfxDump` 只能在 MFC 的 Debug 版本中使用。

您的程式碼不應呼叫 `AfxDump`，但應改為呼叫適當物件的 `Dump` 成員函式。

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="afxdumpstack"></a>  AfxDumpStack

這個全域函式可以用來產生目前堆疊的影像。

```
void AFXAPI AfxDumpStack(DWORD dwTarget = AFX_STACK_DUMP_TARGET_DEFAULT);
```

### <a name="parameters"></a>參數

*dwTarget*<br/>
表示傾印輸出的目標。 可能的值（可以使用位 OR （ **&#124;** ）運算子結合）如下所示：

- AFX_STACK_DUMP_TARGET_TRACE 使用[TRACE](#trace)宏來傳送輸出。 TRACE 宏只會在 debug build 中產生輸出;它在發行組建中不會產生任何輸出。 此外，追蹤也可以重新導向至偵錯工具以外的其他目標。

- AFX_STACK_DUMP_TARGET_DEFAULT 會將傾印輸出傳送至預設目標。 若為 debug 組建，輸出會移至 TRACE 宏。 在發行組建中，輸出會移至剪貼簿。

- AFX_STACK_DUMP_TARGET_CLIPBOARD 只會將輸出傳送至剪貼簿。 資料會使用 CF_TEXT 的剪貼簿格式，以純文字的形式放在剪貼簿上。

- AFX_STACK_DUMP_TARGET_BOTH 會同時將輸出傳送至剪貼簿和追蹤宏。

- AFX_STACK_DUMP_TARGET_ODS 藉由 `OutputDebugString()`的 Win32 函數，直接將輸出傳送至偵錯工具。 當偵錯工具附加至進程時，這個選項會在 debug 和 release 組建中產生偵錯工具輸出。 AFX_STACK_DUMP_TARGET_ODS 一律會到達偵錯工具（如果已附加），而且無法重新導向。

### <a name="remarks"></a>備註

下列範例反映從 MFC 對話應用程式中的按鈕處理常式呼叫 `AfxDumpStack` 所產生的單一輸出行：

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

上述輸出中的每一行都會指出最後一個函式呼叫的位址、包含函式呼叫之模組的完整路徑名稱，以及名為的函式原型。 如果堆疊上的函式呼叫不會發生在函式的確切位址，則會顯示位元組位移。

例如，下表說明上述輸出的第一行：

|輸出|描述|
|------------|-----------------|
|`00427D55:`|最後函式呼叫的傳回位址。|
|`DUMP2\DEBUG\DUMP2.EXE!`|包含函式呼叫之模組的完整路徑名稱。|
|`void AfxDumpStack(unsigned long)`|函式原型呼叫。|
|`+ 181 bytes`|從函式原型的位址（在此案例中為 `void AfxDumpStack(unsigned long)`）到傳回位址的位移（以位元組為單位）（在此案例中為，`00427D55`）。|

`AfxDumpStack` 適用于 MFC 程式庫的 debug 和 nondebug 版本;不過，即使您的可執行檔在共用 DLL 中使用 MFC，函數一律會以靜態方式連結。 在共用程式庫的部署中，函式會在 MFCS42 中找到。LIB 程式庫（及其變體）。

若要成功使用此功能：

- 檔案 IMAGEHLP.DLL。DLL 必須位於您的路徑上。 如果您沒有此 DLL，函式會顯示錯誤訊息。 如需 IMAGEHLP.DLL 所提供之函數集的詳細資訊，請參閱[Image Help Library](/windows/win32/Debug/image-help-library) 。

- 堆疊上具有框架的模組必須包含偵錯工具資訊。 如果它們不包含調試資訊，函數仍然會產生堆疊追蹤，但是追蹤將會較不詳細。

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="afxenablememoryleakdump"></a>AfxEnableMemoryLeakDump

啟用和停用 AFX_DEBUG_STATE 析構函式中的記憶體流失傾印。

```
BOOL AFXAPI AfxEnableMemoryLeakDump(BOOL bDump);
```

### <a name="parameters"></a>參數

*bDump*<br/>
在TRUE 表示已啟用記憶體流失傾印;FALSE 表示已停用記憶體流失傾印。

### <a name="return-value"></a>傳回值

此旗標先前的值。

### <a name="remarks"></a>備註

當應用程式卸載 MFC 程式庫時，MFC 程式庫會檢查記憶體流失。 此時，系統會透過 Visual Studio 的 [ **Debug** ] 視窗，將任何記憶體流失回報給使用者。

如果您的應用程式在 MFC 程式庫之前先載入另一個程式庫，系統會將該程式庫中的一些記憶體配置誤報為記憶體流失。 因為 MFC 程式庫發生記憶體流失誤報的情況，這些誤報可能會導致您的應用程式關閉速度很慢。 在這種情況下，請使用 `AfxEnableMemoryLeakDump` 以停用記憶體流失傾印。

> [!NOTE]
>  如果您使用這個方法來關閉記憶體流失傾印，就不會收到應用程式中有效的記憶體流失報告。 因此，僅有當您確信記憶體流失報告包含誤報的記憶體流失，才建議使用這個方法。

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="afxenablememorytracking"></a>  AfxEnableMemoryTracking

通常會在 MFC 的偵錯工具版本中啟用診斷記憶體追蹤。

```
BOOL AfxEnableMemoryTracking(BOOL bTrack);
```

### <a name="parameters"></a>參數

*bTrack*<br/>
將此值設定為 TRUE 會開啟記憶體追蹤;FALSE 會將它關閉。

### <a name="return-value"></a>傳回值

追蹤-啟用旗標的先前設定。

### <a name="remarks"></a>備註

使用此函式可停用您的程式碼區段上，您知道要正確配置區塊的追蹤。

如需 `AfxEnableMemoryTracking`的詳細資訊，請參閱[偵錯工具 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。

> [!NOTE]
>  此函式只適用于 MFC 的調試版本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#24](../../mfc/codesnippet/cpp/diagnostic-services_12.cpp)]

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="afxismemoryblock"></a>  AfxIsMemoryBlock

測試記憶體位址，以確定它代表目前作用中的記憶體區塊，而此檔案是由**新**的診斷版本所配置。

```
BOOL AfxIsMemoryBlock(
    const void* p,
    UINT nBytes,
    LONG* plRequestNumber = NULL);
```

### <a name="parameters"></a>參數

*p*<br/>
指向要測試的記憶體區塊。

*nBytes*<br/>
包含記憶體區塊的長度（以位元組為單位）。

*plRequestNumber*<br/>
指向將填入記憶體區塊配置序號的**長**整數，如果不代表目前作用中的記憶體區塊，則為零。

### <a name="return-value"></a>傳回值

如果目前配置記憶體區塊且長度正確，則為非零。否則為0。

### <a name="remarks"></a>備註

它也會根據原始配置的大小來檢查指定的大小。 如果函式傳回非零值，則會在*plRequestNumber*中傳回配置序號。 此數位代表已配置區塊的相對於所有其他**新**配置的順序。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#27](../../mfc/codesnippet/cpp/diagnostic-services_13.cpp)]

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="afxisvalidaddress"></a>  AfxIsValidAddress

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

*nBytes*<br/>
包含要測試之記憶體的位元組數目。

*bReadWrite*<br/>
指定記憶體是否可用於讀取和寫入（TRUE），或只是讀取（FALSE）。

### <a name="return-value"></a>傳回值

在 debug 組建中，如果指定的記憶體區塊完全包含在程式的記憶體空間中，則為非零;否則為0。

在非 debug 組建中，如果*lp*不是 Null，則為非零;否則為0。

### <a name="remarks"></a>備註

此位址不限於**new**所配置的區塊。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#28](../../mfc/codesnippet/cpp/diagnostic-services_14.cpp)]

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="afxisvalidstring"></a>  AfxIsValidString

使用此函數來判斷字串的指標是否有效。

```
BOOL  AfxIsValidString(
    LPCSTR lpsz,
    int nLength = -1);
```

### <a name="parameters"></a>參數

*lpsz*<br/>
要測試的指標。

*nLength*<br/>
指定要測試之字串的長度（以位元組為單位）。 -1 的值表示字串將會以 null 結束。

### <a name="return-value"></a>傳回值

在 debug 組建中，如果指定的指標指向指定大小的字串，則為非零。否則為0。

在非 debug 組建中，如果*lpsz*不是 Null，則為非零;否則為0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#29](../../mfc/codesnippet/cpp/diagnostic-services_15.cpp)]

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="afxsetallochook"></a>  AfxSetAllocHook

設定在配置每個記憶體區塊之前，允許呼叫指定函式的勾點。

```
AFX_ALLOC_HOOK AfxSetAllocHook(AFX_ALLOC_HOOK pfnAllocHook);
```

### <a name="parameters"></a>參數

*pfnAllocHook*<br/>
指定要呼叫之函數的名稱。 請參閱配置函數原型的備註。

### <a name="return-value"></a>傳回值

如果您想要允許配置，則為非零值。否則為0。

### <a name="remarks"></a>備註

MFC 程式庫的「調試記憶體」配置器可以呼叫使用者定義的攔截函式，讓使用者監視記憶體配置，並控制是否允許配置。 配置攔截函式的原型如下：

**BOOL AFXAPI AllocHook （size_t** `nSize` **，Bool** `bObject` **，LONG** `lRequestNumber` **）;**

*nSize*<br/>
建議的記憶體配置大小。

*bObject*<br/>
如果配置適用于 `CObject`衍生的物件，則為 TRUE;否則為 FALSE。

*lRequestNumber*<br/>
記憶體配置的序號。

請注意，AFXAPI 呼叫慣例表示被呼叫端必須從堆疊移除參數。

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="afxdoforallclasses"></a>  AfxDoForAllClasses

在應用程式的記憶體空間中，針對所有可序列化的 `CObject`衍生類別呼叫指定的反復專案函式。

```
void
AFXAPI AfxDoForAllClasses(
    void (* pfn)(const CRuntimeClass* pClass, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>參數

*pfn*<br/>
指向要針對每個類別呼叫的反復專案函式。 函式引數是指向 `CRuntimeClass` 物件的指標，以及呼叫端提供給函式之額外資料的 void 指標。

*pContext*<br/>
指向呼叫者可以提供給反復專案函數的選擇性資料。 這個指標可以是 Null。

### <a name="remarks"></a>備註

可序列化的 `CObject`衍生類別是使用 DECLARE_SERIAL 宏衍生的類別。 傳遞至*pCoNtext*中 `AfxDoForAllClasses` 的指標，會在每次呼叫時傳遞至指定的反復專案函式。

> [!NOTE]
>  此函式只適用于 MFC 的調試版本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#113](../../mfc/codesnippet/cpp/diagnostic-services_16.cpp)]

[!code-cpp[NVC_MFCCollections#114](../../mfc/codesnippet/cpp/diagnostic-services_17.cpp)]

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="afxdoforallobjects"></a>  AfxDoForAllObjects

針對所有衍生自使用**new**所配置 `CObject` 的物件，執行指定的反復專案函式。

```
void AfxDoForAllObjects(
    void (* pfn)(CObject* pObject, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>參數

*pfn*<br/>
指向要針對每個物件執行的反復專案函式。 函式引數是指向 `CObject` 的指標，以及呼叫端提供給函式之額外資料的 void 指標。

*pContext*<br/>
指向呼叫者可以提供給反復專案函數的選擇性資料。 這個指標可以是 Null。

### <a name="remarks"></a>備註

不列舉 Stack、全域或内嵌物件。 傳遞至*pCoNtext*中 `AfxDoForAllObjects` 的指標，會在每次呼叫時傳遞至指定的反復專案函式。

> [!NOTE]
>  此函式只適用于 MFC 的調試版本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#115](../../mfc/codesnippet/cpp/diagnostic-services_18.cpp)]

[!code-cpp[NVC_MFCCollections#116](../../mfc/codesnippet/cpp/diagnostic-services_19.cpp)]

## <a name="see-also"></a>另請參閱

[宏和全域](mfc-macros-and-globals.md)<br/>
[CObject：:D ump](cobject-class.md#dump)
