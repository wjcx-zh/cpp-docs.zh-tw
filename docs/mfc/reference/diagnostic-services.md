---
title: 診斷服務 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd420544f341159fa4281c4f837fa222d357e1b1
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50068693"
---
# <a name="diagnostic-services"></a>診斷服務

MFC 程式庫提供許多診斷服務，可讓您更輕鬆地對程式進行偵錯。 這些診斷服務包含巨集和全域函式，可讓您追蹤程式的記憶體配置、在執行階段傾印物件的內容，以及在執行階段列印偵錯訊息。 診斷服務的巨集和全域函式可分為下列分類：

- 一般診斷巨集

- 一般診斷函式和變數

- 物件診斷函式

這些巨集和函式都可以在 MFC 的偵錯和發行版本中，供所有衍生自 `CObject` 的類別使用。 不過，除了 DEBUG_NEW 及驗證所有項目會執行任何動作的發行版本中。

在偵錯程式庫中，所有配置的記憶體區塊都會以一系列「保護位元組」(Guard Byte) 來提供支援。 如果這些位元組受到錯誤記憶體寫入的干擾，則診斷常式可能會回報問題。 如果您在實作檔中包含此行：

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

則所有對 **new** 的呼叫都會儲存發生記憶體配置的檔案名稱和行號。 [CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince) 函式會顯示這項額外的資訊，讓您找出記憶體流失的問題。 如需診斷輸出的其他資訊，另請參閱 [CDumpContext](../../mfc/reference/cdumpcontext-class.md) 類別。

此外，C 執行階段程式庫也支援一組可用來偵錯應用程式的診斷函式。 如需詳細資訊，請參閱＜執行階段程式庫參考＞中的 [偵錯常式](../../c-runtime-library/debug-routines.md) 。

### <a name="mfc-general-diagnostic-macros"></a>MFC 一般診斷巨集

|||
|-|-|
|[ASSERT](#assert)|列印訊息，如果指定的運算式評估為 FALSE 的程式庫的偵錯版本中，再中止程式。|
|[ASSERT_KINDOF](#assert_kindof)|測試某物件是屬於指定類別，還是屬於該類別的衍生類別。|
|[ASSERT_VALID](#assert_valid)|藉由呼叫物件的 `AssertValid` 成員函式來測試其內部有效性，通常會覆寫自 `CObject`。|
|[DEBUG_NEW](#debug_new)|提供偵錯模式中所有物件配置的檔案名稱和行號，以協助找出記憶體流失的問題。|
|[DEBUG_ONLY](#debug_only)|判斷提示類似，但不會測試運算式; 的值適用於只在偵錯模式中執行的程式碼。|
|[請確定和 ENSURE_VALID](#ensure)|使用此選項，來驗證資料的正確性。|
|[THIS_FILE](#this_file)|展開要編譯之檔案的名稱。|
|[TRACE](#trace)|提供此程式庫之偵錯版本中類似 `printf`的功能。|
|[VERIFY](#verify)|判斷提示的類似但評估程式庫也如同偵錯版本的發行版本中的運算式。|

### <a name="mfc-general-diagnostic-variables-and-functions"></a>MFC 一般診斷變數和函式

|||
|-|-|
|[afxDump](#afxdump)|全域變數，可將 [CDumpContext](../../mfc/reference/cdumpcontext-class.md) 資訊傳送至偵錯工具輸出視窗或偵錯終端機。|
|[afxMemDF](#afxmemdf)|全域變數，可控制偵錯記憶體配置器的行為。|
|[AfxCheckError](#afxcheckerror)|全域變數，可用來測試以查看是否發生錯誤，若是如此，傳入的 SCODE 會擲回適當的錯誤。|
|[AfxCheckMemory](#afxcheckmemory)|檢查目前配置之所有記憶體的完整性。|
|[AfxDebugBreak](#afxdebugbreak)|在執行中，會導致中斷。|
|[AfxDump](#cdumpcontext_in_mfc)|如果在偵錯工具中呼叫，則會一面進行偵錯，一面傾印物件的狀態。|
|[AfxDump](#afxdump)|將物件狀態傾印偵錯時的內部函式。|
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

### <a name="mfc-compilation-macros"></a>MFC 編譯巨集

|||
|-|-|
|[_AFX_SECURE_NO_WARNINGS](#afx_secure_no_warnings)|隱藏關於使用被取代 MFC 的功能的編譯器警告。|

## <a name="afx_secure_no_warnings"></a> _AFX_SECURE_NO_WARNINGS

隱藏關於使用被取代 MFC 的功能的編譯器警告。

### <a name="syntax"></a>語法

```
_AFX_SECURE_NO_WARNINGS
```

### <a name="example"></a>範例

如果沒有定義 _AFX_SECURE_NO_WARNINGS，則此程式碼範例會產生編譯器警告。

```cpp
// define this before including any afx files in stdafx.h
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

呼叫此函式可導致中斷 (在呼叫位置`AfxDebugBreak`) 的 MFC 應用程式的偵錯版本執行。

### <a name="syntax"></a>語法

```
void AfxDebugBreak( );
```

### <a name="remarks"></a>備註

`AfxDebugBreak` 沒有任何作用中的 MFC 應用程式的發行版本，應該移除。 此函式應該只用在 MFC 應用程式。 使用 Win32 API 版本， `DebugBreak`、 非 MFC 應用程式中造成中斷。

### <a name="requirements"></a>需求

**標頭：** afxver_.h

##  <a name="assert"></a>  ASSERT

會評估其引數。

```
ASSERT(booleanExpression)
```

### <a name="parameters"></a>參數

*booleanExpression*<br/>
指定評估為非零值則為 0 的運算式 （包括指標值）。

### <a name="remarks"></a>備註

如果結果為 0，巨集會列印診斷訊息，並中止程式。 如果條件為非零值，它會執行任何動作。

診斷資訊格式如下

`assertion failed in file <name> in line <num>`

何處*名稱*是來源檔案的名稱並*num*是在原始程式檔中失敗的判斷提示的行號。

在 MFC 發行版本中，判斷提示不會評估運算式，而且因此不會中斷程式。 如果運算式必須評估環境無關，請使用 VERIFY 巨集，來判斷提示取代。

> [!NOTE]
>  此函式是只能在 MFC 的偵錯版本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#44](../../mfc/codesnippet/cpp/diagnostic-services_2.cpp)]

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="assert_kindof"></a>  ASSERT_KINDOF

指向的物件是指定類別的物件，或類別的物件衍生自指定的類別，這個巨集判斷提示。

```
ASSERT_KINDOF(classname, pobject)
```

### <a name="parameters"></a>參數

*classname*<br/>
名稱`CObject`-衍生的類別。

*pobject*<br/>
類別物件的指標。

### <a name="remarks"></a>備註

*Pobject*參數應該是物件的指標，而且可以是**const**。 指向的物件，且必須支援類別`CObject`執行階段類別資訊。 做為範例，以確保`pDocument`是物件的指標`CMyDoc`類別，或任何其衍生項目，您可以撰寫程式碼：

[!code-cpp[NVC_MFCDocView#194](../../mfc/codesnippet/cpp/diagnostic-services_3.cpp)]

使用`ASSERT_KINDOF`巨集正是與撰寫程式碼相同：

[!code-cpp[NVC_MFCDocView#195](../../mfc/codesnippet/cpp/diagnostic-services_4.cpp)]

此函式僅適用於以宣告的類別 [DECLARE_DYNAMIC] (執行-時間-物件-模型-services.md #declare_dynamic 或[DECLARE_SERIAL](run-time-object-model-services.md#declare_serial)巨集。

> [!NOTE]
>  此函式是只能在 MFC 的偵錯版本。

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="assert_valid"></a>  ASSERT_VALID

使用此選項，若要測試有效性的物件的內部狀態的相關假設。

```
ASSERT_VALID(pObject)
```

### <a name="parameters"></a>參數

*pObject*<br/>
指定的物件衍生自類別`CObject`具有覆寫的新版`AssertValid`成員函式。

### <a name="remarks"></a>備註

ASSERT_VALID 呼叫`AssertValid`之物件的成員函式傳遞做為其引數。

在 MFC 發行版本中，ASSERT_VALID 沒有任何作用。 在偵錯版本中，它會驗證指標、 檢查針對 null 值，並呼叫物件的自己`AssertValid`成員函式。 如果其中任何一項測試失敗，警示訊息會顯示在相同的方式[ASSERT](#assert)。

> [!NOTE]
>  此函式是只能在 MFC 的偵錯版本。

如需詳細資訊和範例，請參閱 <<c0> [ 偵錯 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。

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

您通常會使用您計劃在各處使用 DEBUG_NEW**新**運算子來配置堆積的儲存體。

在偵錯模式中 (當 **_DEBUG**已定義符號)，DEBUG_NEW 會持續追蹤的每個物件所配置的名稱和行號。 然後，當您使用[cmemorystate:: Dumpallobjectssince](cmemorystate-structure.md#dumpallobjectssince)成員函式，以 DEBUG_NEW 配置每個物件顯示的檔名和行號配置位置。

若要使用 DEBUG_NEW，插入原始程式檔中的下列指示詞：

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

無論在何處使用當您插入此指示詞時，前置處理器會插入 DEBUG_NEW**新**，而 MFC 會。 當您編譯程式的發行版本時，DEBUG_NEW 解析成簡單**新**不會產生作業和檔名和行號資訊。

> [!NOTE]
>  在舊版的 MFC （4.1 及更早版本），就不必放`#define`呼叫 IMPLEMENT_DYNCREATE 或 IMPLEMENT_SERIAL 巨集的所有陳述式之後的陳述式。 這不再是必要的。

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="debug_only"></a>  DEBUG_ONLY

在偵錯模式中 (當 **_DEBUG**已定義符號)，DEBUG_ONLY 評估其引數。

```
DEBUG_ONLY(expression)
```

### <a name="remarks"></a>備註

在發行組建，DEBUG_ONLY 不會評估其引數。 當您有應該只在偵錯組建中執行的程式碼時，這非常有用。

DEBUG_ONLY 巨集就相當於周圍*運算式*具有`#ifdef _DEBUG`和`#endif`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#32](../../mfc/codesnippet/cpp/diagnostic-services_6.cpp)]

### <a name="requirements"></a>需求

**標頭：** afx.h

### <a name="ensure"></a>  請確定和 ENSURE_VALID

使用此選項，來驗證資料的正確性。

### <a name="syntax"></a>語法

```
ENSURE(  booleanExpression )
ENSURE_VALID( booleanExpression  )
```

### <a name="parameters"></a>參數

*booleanExpression*<br/>
指定要測試的布林運算式。

### <a name="remarks"></a>備註

這些巨集的目的是要提升驗證的參數。 巨集會阻止進一步處理的程式碼中的參數不正確。 不同於 ASSERT 巨集，請確定巨集擲回除了產生判斷提示例外狀況。

巨集的行為有兩種會根據專案組態。 巨集呼叫判斷提示，並再擲回例外狀況，如果判斷提示失敗。 因此，在偵錯組態 （也就是其中定義 _DEBUG） 巨集產生判斷提示和發行組態，巨集產生時發生的例外狀況 （判斷提示不會評估發行組態中的運算式） 的例外狀況。

巨集 ENSURE_ARG 像是請確定巨集。

ENSURE_VALID 呼叫 ASSERT_VALID 巨集 （這只在偵錯組建中沒有作用）。 颾魤 ㄛ ENSURE_VALID 指標為 NULL 時擲回例外狀況。 NULL 測試會在偵錯和發行組態。

如果任何一種測試失敗時，警示訊息會顯示在相同的方式來判斷提示。 如有需要巨集，則會擲回例外狀況的引數無效。
### <a name="requirements"></a>需求

**標頭：** afx.h

### <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)<br/>
[VERIFY](#verify)<br/>
[ATLENSURE](#altensure)

## <a name="this_file"></a> THIS_FILE

展開要編譯之檔案的名稱。

### <a name="syntax"></a>語法

```
THIS_FILE
```

### <a name="remarks"></a>備註

判斷提示及驗證巨集使用資訊。 應用程式精靈和程式碼精靈會將巨集放在他們建立原始程式碼檔。

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

### <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)<br/>
[ASSERT](#assert)<br/>
[VERIFY](#verify)

##  <a name="trace"></a>  TRACE

將指定的字串傳送至目前的應用程式的偵錯工具中。

```
TRACE(exp)
TRACE(DWORD  category,  UINT  level, LPCSTR lpszFormat, ...)
```

### <a name="remarks"></a>備註

請參閱[ATLTRACE2](../../atl/reference/debugging-and-error-reporting-macros.md#atltrace2)如需追蹤的描述。 追蹤和 ATLTRACE2 有相同的行為。

在 MFC 的偵錯版本，這個巨集會將指定的字串傳送至目前的應用程式的偵錯工具。 在發行組建，這個巨集會編譯為 nothing （沒有程式碼產生的話）。

如需詳細資訊，請參閱 <<c0> [ 偵錯 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="verify"></a>  VERIFY

在 MFC 的偵錯版本，會評估其引數。

```
VERIFY(booleanExpression)
```

### <a name="parameters"></a>參數

*booleanExpression*<br/>
指定評估為非零值則為 0 的運算式 （包括指標值）。

### <a name="remarks"></a>備註

如果結果是 0，巨集會列印診斷訊息，並中止程式。 如果條件為非零值，它會執行任何動作。

診斷資訊格式如下

`assertion failed in file <name> in line <num>`

何處*名稱*是原始程式檔的名稱並*num*是在原始程式檔中失敗的判斷提示的行號。

在 MFC 發行版本中，確認會評估運算式，但不會列印或中斷程式。 例如，如果運算式是函式呼叫，將會進行呼叫。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#198](../../mfc/codesnippet/cpp/diagnostic-services_7.cpp)]

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="cdumpcontext_in_mfc"></a>  afxDump (MFC 中的 CDumpContext)

提供物件傾印的基本功能，在您的應用程式。

```
CDumpContext  afxDump;
```

### <a name="remarks"></a>備註

`afxDump` 是預先定義[CDumpContext](../../mfc/reference/cdumpcontext-class.md)物件，可讓您傳送`CDumpContext`偵錯工具的 [輸出] 視窗或偵錯終端機的資訊。 一般而言，您提供`afxDump`做為參數`CObject::Dump`。

在 Windows NT 和所有版本的 Windows，`afxDump`輸出會傳送至輸出偵錯視窗的 Visual c + +，當您偵錯您的應用程式。

只在 MFC 的偵錯版本中定義此變數。 如需詳細資訊`afxDump`，請參閱 <<c2> [ 偵錯 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#23](../../mfc/codesnippet/cpp/diagnostic-services_8.cpp)]

### <a name="requirements"></a>需求

**標頭：** afx.h

## <a name="afxdump"></a> AfxDump （內部）

MFC 使用傾印偵錯時的物件狀態的內部函式。

### <a name="syntax"></a>語法

```
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>參數

*pOb*<br/>
從衍生類別的物件指標`CObject`。

### <a name="remarks"></a>備註

`AfxDump` 呼叫物件的`Dump`成員函式，並將所指定的位置資訊`afxDump`變數。 `AfxDump` 只有使用 MFC 的偵錯版本。

您的程式碼不應該呼叫`AfxDump`，但應該改為呼叫`Dump`成員函式的適當的物件。

### <a name="requirements"></a>需求

**標頭：** afx.h

### <a name="see-also"></a>另請參閱

[CObject::Dump](cobject-class.md#dump)

##  <a name="afxmemdf"></a>  afxMemDF

此變數可從 偵錯工具或程式存取，並可讓您調整配置診斷。

```
int  afxMemDF;
```

### <a name="remarks"></a>備註

`afxMemDF` 可以是下列值所指定的列舉型別`afxMemDF`:

- `allocMemDF` 開啟偵錯的配置器 （偵錯文件庫中的預設設定）。

- `delayFreeMemDF` 延遲釋放記憶體。 雖然您的程式釋放記憶體區塊，配置器不會傳回該記憶體基礎作業系統。 這會將最大記憶體壓力放在您的程式。

- `checkAlwaysMemDF` 呼叫`AfxCheckMemory`每次配置或釋放記憶體。 這會將大幅降低記憶體配置和解除配置。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#30](../../mfc/codesnippet/cpp/diagnostic-services_9.cpp)]

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="afxcheckerror"></a>  AfxCheckError

此函式會測試傳遞的 SCODE 發生錯誤。

```
void AFXAPI AfxCheckError(SCODE sc);
throw CMemoryException*
throw COleException*
```

### <a name="remarks"></a>備註

如果是錯誤，函式會擲回例外狀況。 如果傳遞的 SCODE E_OUTOFMEMORY，函式會擲回[CMemoryException](../../mfc/reference/cmemoryexception-class.md)藉由呼叫[AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception)。 否則，函式會擲回[COleException](../../mfc/reference/coleexception-class.md)藉由呼叫[AfxThrowOleException](exception-processing.md#afxthrowoleexception)。

這個函式可用來檢查對應用程式中 OLE 函式呼叫的傳回值。 藉由在應用程式中以此函式測試傳回值，您可以用最少的程式碼因應錯誤狀況。

> [!NOTE]
>  這個函式在偵錯和非偵錯組建中具有相同的效果。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCOleContainer#33](../../mfc/codesnippet/cpp/diagnostic-services_10.cpp)]

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="afxcheckmemory"></a>  AfxCheckMemory

此函式會驗證可用記憶體集區，並列印所需的錯誤訊息。

```
BOOL  AfxCheckMemory();
```

### <a name="return-value"></a>傳回值

非零值，如果沒有記憶體錯誤;否則為 0。

### <a name="remarks"></a>備註

如果函式偵測不到任何記憶體損毀，它會列印任何動作。

所有在堆積上目前配置的記憶體區塊會檢查，包括所配置**新**但無法直接呼叫基礎的記憶體配置器所配置的這類**malloc**函式或`GlobalAlloc` Windows 函式。 如果發現任何區塊已損毀，會將訊息列印至偵錯工具的輸出。

如果您包含線條

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

在程式模組中，則後續呼叫`AfxCheckMemory`顯示的檔名和行號配置的記憶體位置。

> [!NOTE]
>  如果模組包含的一或多個類別實作之可序列化，則必須將`#define`最後一次的 IMPLEMENT_SERIAL 巨集呼叫的一行。

此功能僅適用於 MFC 的偵錯版本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCObjectSample#26](../../mfc/codesnippet/cpp/diagnostic-services_11.cpp)]

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="afxdump"></a>  AfxDump (MFC)

呼叫此函式在偵錯工具傾印偵錯時的物件狀態中。

```
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>參數

*pOb*<br/>
從衍生類別的物件指標`CObject`。

### <a name="remarks"></a>備註

`AfxDump` 呼叫物件的`Dump`成員函式，並將所指定的位置資訊`afxDump`變數。 `AfxDump` 只有使用 MFC 的偵錯版本。

您的程式碼不應該呼叫`AfxDump`，但應該改為呼叫`Dump`成員函式的適當的物件。

### <a name="requirements"></a>需求

**標頭：** afx.h

### <a name="see-also"></a>另請參閱

[CObject::Dump](cobject-class.md#dump)

##  <a name="afxdumpstack"></a>  AfxDumpStack

此全域函式可用來產生目前堆疊的映像。

```
void AFXAPI AfxDumpStack(DWORD dwTarget = AFX_STACK_DUMP_TARGET_DEFAULT);
```

### <a name="parameters"></a>參數

*dwTarget*<br/>
表示傾印的輸出目標。 可能的值，可以使用位元 OR 結合 ( **&#124;**) 運算子，如下所示：

- 藉由 AFX_STACK_DUMP_TARGET_TRACE 傳送的輸出[追蹤](#trace)巨集。 TRACE 巨集; 偵錯組建中產生輸出它會在發行的組建產生任何輸出。 此外，追蹤可以重新導向至其他偵錯工具以外的目標。

- AFX_STACK_DUMP_TARGET_DEFAULT 傳送傾印的預設目標的輸出。 偵錯組建中，會輸出至追蹤巨集。 在發行組建，輸出會移至剪貼簿。

- AFX_STACK_DUMP_TARGET_CLIPBOARD 傳送輸出到只在剪貼簿。 資料會放在剪貼簿，以使用 CF_TEXT 剪貼簿格式的純文字。

- AFX_STACK_DUMP_TARGET_BOTH，傳送同時輸出到剪貼簿和 TRACE 巨集。

- AFX_STACK_DUMP_TARGET_ODS 傳送輸出直接透過 Win32 函式偵錯工具`OutputDebugString()`。 這個選項會在這兩個偵錯中產生偵錯工具輸出，並在偵錯工具附加至處理程序時，發行組建。 AFX_STACK_DUMP_TARGET_ODS 永遠會到達偵錯工具 （如果它已連結），而且無法重新導向。

### <a name="remarks"></a>備註

下列範例會反映程式的呼叫所產生的輸出`AfxDumpStack`從 MFC 對話方塊應用程式中的按鈕處理常式：

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

上述輸出中的每一行指出最後一次的函式呼叫的函式呼叫時，並呼叫的函式原型所包含的模組的完整路徑名稱的位址。 如果堆疊上的函式呼叫不會發生在函式的實際位址，則會顯示位元組位移。

比方說下, 表說明上述的輸出結果的第一行：

|輸出|描述|
|------------|-----------------|
|`00427D55:`|最後一個函式呼叫的傳回位址。|
|`DUMP2\DEBUG\DUMP2.EXE!`|包含函式呼叫的模組完整路徑名稱。|
|`void AfxDumpStack(unsigned long)`|呼叫函式原型。|
|`+ 181 bytes`|以位元組為單位從函式原型的位址位移 (在此情況下， `void AfxDumpStack(unsigned long)`) 傳回的位址 (在此情況下， `00427D55`)。|

`AfxDumpStack` 可在偵錯和非偵錯版本的 MFC 程式庫;不過，此函式是一律以靜態方式連結，即使可執行檔使用 MFC 的共用 dll。 在共用程式庫實作中，此函式位於 MFCS42 中。LIB 程式庫 （及變體）。

若要成功使用此函式：

- IMAGEHLP 檔案。DLL 必須位於您的路徑。 如果您沒有此 DLL，此函式會顯示錯誤訊息。 請參閱[映像 Help Library](/windows/desktop/Debug/image-help-library) IMAGEHLP 所提供的函式集上的資訊。

- 具有堆疊框架的模組必須包含偵錯資訊。 如果它們不包含偵錯資訊，此函式仍會產生堆疊追蹤，但會較不詳細追蹤。
### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="afxenablememoryleakdump"></a>  AfxEnableMemoryLeakDump

啟用和停用記憶體流失傾印，AFX_DEBUG_STATE 解構函式中。

```
BOOL AFXAPI AfxEnableMemoryLeakDump(BOOL bDump);
```

### <a name="parameters"></a>參數

*bDump*<br/>
[in]TRUE 表示已啟用記憶體流失傾印;FALSE 表示已停用記憶體流失傾印。

### <a name="return-value"></a>傳回值

此旗標先前的值。

### <a name="remarks"></a>備註

當應用程式卸載 MFC 程式庫時，MFC 程式庫會檢查記憶體流失。 此時，任何記憶體流失情況回報給使用者**偵錯**Visual Studio 的視窗。

如果您的應用程式在 MFC 程式庫之前先載入另一個程式庫，系統會將該程式庫中的一些記憶體配置誤報為記憶體流失。 因為 MFC 程式庫發生記憶體流失誤報的情況，這些誤報可能會導致您的應用程式關閉速度很慢。 在這種情況下，請使用 `AfxEnableMemoryLeakDump` 以停用記憶體流失傾印。

> [!NOTE]
>  如果您使用這個方法來關閉記憶體流失傾印，就不會收到應用程式中有效的記憶體流失報告。 因此，僅有當您確信記憶體流失報告包含誤報的記憶體流失，才建議使用這個方法。

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="afxenablememorytracking"></a>  AfxEnableMemoryTracking

在 MFC 的偵錯版本中，通常會啟用診斷追蹤的記憶體。

```
BOOL AfxEnableMemoryTracking(BOOL bTrack);
```

### <a name="parameters"></a>參數

*bTrack*<br/>
將此值為 TRUE 會設定追蹤; 的記憶體FALSE 予以關閉。

### <a name="return-value"></a>傳回值

追蹤啟用旗標先前的設定。

### <a name="remarks"></a>備註

若要停用您知道正確配置區塊程式碼區段上的 追蹤使用此函數。

如需詳細資訊`AfxEnableMemoryTracking`，請參閱 <<c2> [ 偵錯 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。

> [!NOTE]
>  此功能僅適用於 MFC 的偵錯版本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#24](../../mfc/codesnippet/cpp/diagnostic-services_12.cpp)]

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="afxismemoryblock"></a>  AfxIsMemoryBlock

測試以確定它代表目前作用中的記憶體區塊的診斷版本所配置的記憶體位址**新**。

```
BOOL AfxIsMemoryBlock(
    const void* p,
    UINT nBytes,
    LONG* plRequestNumber = NULL);
```

### <a name="parameters"></a>參數

*p*<br/>
要測試的記憶體區塊指向。

*nBytes*<br/>
包含以位元組為單位的記憶體區塊的長度。

*plRequestNumber*<br/>
指向**長**時會被填入記憶體區塊的配置順序編號，或如果它不代表目前作用中的記憶體區塊則為零的整數。

### <a name="return-value"></a>傳回值

非零值，如果目前已配置的記憶體區塊，且長度為正確;否則為 0。

### <a name="remarks"></a>備註

它也會檢查指定的大小，針對原始配置的大小。 如果函式傳回非零值，就會傳回的配置順序編號*plRequestNumber*。 這個數字代表相對於所有其他已配置區塊的順序**新**配置。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#27](../../mfc/codesnippet/cpp/diagnostic-services_13.cpp)]

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="afxisvalidaddress"></a>  AfxIsValidAddress

測試以確保它完全在程式的記憶體空間內包含的任何記憶體位址。

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
包含要測試的記憶體位元組數目。

*bReadWrite*<br/>
指定的記憶體是同時用於讀取和寫入 (TRUE) 或只讀取 (FALSE)。

### <a name="return-value"></a>傳回值

在偵錯組建中，非零值，如果指定的記憶體區塊包含完全在程式的記憶體空間;否則為 0。

在非偵錯組建中，非零*lp*不是 NULL，否則為 0。

### <a name="remarks"></a>備註

位址不是限制為所配置的區塊**新**。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#28](../../mfc/codesnippet/cpp/diagnostic-services_14.cpp)]

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="afxisvalidstring"></a>  AfxIsValidString

使用此函數來判斷字串指標是否有效。

```
BOOL  AfxIsValidString(
    LPCSTR lpsz,
    int nLength = -1);
```

### <a name="parameters"></a>參數

*lpsz*<br/>
要測試的指標。

*nLength*<br/>
指定要測試，以位元組為單位的字串長度。 -1 值表示此字串會以 null 結束。

### <a name="return-value"></a>傳回值

在偵錯組建中，如果指定的指標指向指定大小; 的字串，非零值。否則為 0。

在非偵錯組建中，非零*lpsz*不是 NULL，否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#29](../../mfc/codesnippet/cpp/diagnostic-services_15.cpp)]

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="afxsetallochook"></a>  AfxSetAllocHook

設定每個記憶體區塊會配置之前，可讓指定的函式呼叫的勾點。

```
AFX_ALLOC_HOOK AfxSetAllocHook(AFX_ALLOC_HOOK pfnAllocHook);
```

### <a name="parameters"></a>參數

*pfnAllocHook*<br/>
指定要呼叫的函式的名稱。 請參閱的 < 備註 > 的配置函式的原型。

### <a name="return-value"></a>傳回值

非零值，如果您想要允許配置;否則為 0。

### <a name="remarks"></a>備註

Microsoft Foundation 類別庫偵錯記憶體配置器可以呼叫以允許使用者監視記憶體配置，並控制是否允許配置的使用者定義的攔截函式。 配置攔截函式原型如下所示：

**BOOL AFXAPI AllocHook (size_t** `nSize` **，BOOL** `bObject`**完整** `lRequestNumber` **);**

*nSize*<br/>
建議的記憶體配置的大小。

*bObject*<br/>
如果配置，則為 TRUE `CObject`-衍生的物件，否則為 FALSE。

*lRequestNumber*<br/>
記憶體配置順序編號。

請注意，呼叫慣例 AFXAPI 意味著被呼叫端必須從堆疊移除參數。

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="afxdoforallclasses"></a>  AfxDoForAllClasses

呼叫指定的反覆項目函式的所有可序列化`CObject`-衍生的應用程式的記憶體空間中的類別。

```
void
AFXAPI AfxDoForAllClasses(
    void (* pfn)(const CRuntimeClass* pClass, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>參數

*pfn*<br/>
指向的反覆項目函式，呼叫每個類別。 函式引數是一個指向`CRuntimeClass`物件和 void 指標至函式的呼叫端提供的額外資料。

*pContext*<br/>
呼叫端可以提供給反覆項目函式的選擇性資料點。 此指標可以是 NULL。

### <a name="remarks"></a>備註

可序列化`CObject`-衍生的類別是使用 DECLARE_SERIAL 巨集衍生的類別。 將指標傳遞給`AfxDoForAllClasses`中*pContext*會傳遞至指定的反覆項目函式每次呼叫時。

> [!NOTE]
>  此功能僅適用於 MFC 的偵錯版本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#113](../../mfc/codesnippet/cpp/diagnostic-services_16.cpp)]

[!code-cpp[NVC_MFCCollections#114](../../mfc/codesnippet/cpp/diagnostic-services_17.cpp)]

### <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="afxdoforallobjects"></a>  AfxDoForAllObjects

執行指定的反覆項目函式的所有物件衍生自`CObject`與已配置**新**。

```
void AfxDoForAllObjects(
    void (* pfn)(CObject* pObject, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>參數

*pfn*<br/>
指向要針對每個物件執行反覆項目函式。 函式引數是一個指向`CObject`和 void 指標至函式的呼叫端提供的額外資料。

*pContext*<br/>
呼叫端可以提供給反覆項目函式的選擇性資料點。 此指標可以是 NULL。

### <a name="remarks"></a>備註

不會列舉堆疊，全域或內嵌的物件。 將指標傳遞給`AfxDoForAllObjects`中*pContext*會傳遞至指定的反覆項目函式每次呼叫時。

> [!NOTE]
>  此功能僅適用於 MFC 的偵錯版本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCCollections#115](../../mfc/codesnippet/cpp/diagnostic-services_18.cpp)]

[!code-cpp[NVC_MFCCollections#116](../../mfc/codesnippet/cpp/diagnostic-services_19.cpp)]

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)