---
title: 偵錯和錯誤報告巨集
ms.date: 05/06/2019
f1_keywords:
- atldef/ATL::_ATL_DEBUG_INTERFACES
- atldef/ATL::_ATL_DEBUG_QI
- atldef/ATL::ATLASSERT
- afx/ATL::ATLENSURE
- atltrace/ATL::ATLTRACENOTIMPL
- atltrace/ATL::ATLTRACE
helpviewer_keywords:
- macros, error reporting
ms.assetid: 4da9b87f-ec5c-4a32-ab93-637780909b9d
ms.openlocfilehash: a243351ff337cb517f8a8231c18c495c8d2ca302
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221085"
---
# <a name="debugging-and-error-reporting-macros"></a>偵錯和錯誤報告巨集

這些巨集提供有用的偵錯和追蹤功能。

|||
|-|-|
|[_ATL_DEBUG_INTERFACES](#_atl_debug_interfaces)|寫入，[輸出] 視窗中，任何介面流失，當偵測到`_Module.Term`呼叫。|
|[_ATL_DEBUG_QI](#_atl_debug_qi)|寫入的所有呼叫`QueryInterface`到輸出視窗。|
|[ATLASSERT](#atlassert)|執行相同的功能[_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) C 執行階段程式庫中找到的巨集。|
|[ATLENSURE](#atlensure)|執行參數驗證。 呼叫`AtlThrow`視|
|[ATLTRACENOTIMPL](#atltracenotimpl)|將訊息傳送到傾印裝置未指定的函式。|
|[ATLTRACE](#atltrace)|報告輸出裝置，例如 [偵錯工具] 視窗中，根據指定的旗標和層級的警告。 包含為了與舊版相容。|
|[ATLTRACE2](#atltrace2)|報告輸出裝置，例如 [偵錯工具] 視窗中，根據指定的旗標和層級的警告。|

##  <a name="_atl_debug_interfaces"></a>  _ATL_DEBUG_INTERFACES

定義此巨集包含任何要追蹤所有的 ATL 標頭檔前先`AddRef`和`Release`呼叫您的元件介面，以 [輸出] 視窗上。

```
#define _ATL_DEBUG_INTERFACES
```

### <a name="remarks"></a>備註

追蹤輸出會出現，如下所示：

`ATL: QIThunk - 2008         AddRef  :   Object = 0x00d81ba0   Refcount = 1   CBug - IBug`

每個追蹤的第一個部分一律為`ATL: QIThunk`。 接下來是值，識別特定*介面 thunk*正在使用。 介面 thunk 是用來維護參考計數，並提供此處所使用的追蹤功能的物件。 每次呼叫建立新的介面 thunk`QueryInterface`除了要求`IUnknown`介面 （在此情況下，相同的 thunk 會將每次傳回遵守 COM 的身分識別的規則）。

接下來，您會看到`AddRef`或`Release`指出所呼叫的方法。 接下來，您會看到值，識別已變更其介面的參考計數的物件。 追蹤的值是**這**物件的指標。

會進行追蹤的參考計數是參考計數上之後，thunk`AddRef`或`Release`呼叫。 請注意，此參考計數可能不會符合物件的參考計數。 每個 thunk 會維護其本身的參考計數可協助您完全符合 COM 的參考計數的規則。

追蹤資訊的最後一步是物件以及受影響的介面名稱`AddRef`或`Release`呼叫。

任何介面伺服器關閉時偵測到的遺漏和`_Module.Term`呼叫將會記錄如下：

`ATL: QIThunk - 2005         LEAK    :   Object = 0x00d81ca0   Refcount = 1   MaxRefCount = 1   CBug - IBug`

這裡提供一個都會直接對應到先前的追蹤陳述式中提供的資訊的資訊，因此您可以檢查的參考計數介面 thunk 的整個存留期間。 此外，您取得該介面 thunk 的最大值的參考計數的指示。

> [!NOTE]
> _ATL_DEBUG_INTERFACES 可用在零售組建中。

##  <a name="_atl_debug_qi"></a>  _ATL_DEBUG_QI

寫入的所有呼叫`QueryInterface`到輸出視窗。

```
#define _ATL_DEBUG_QI
```

### <a name="remarks"></a>備註

如果呼叫`QueryInterface`失敗，[輸出] 視窗會顯示：

*介面名稱* - `failed`

##  <a name="atlassert"></a>  ATLASSERT

ATLASSERT 巨集執行相同的功能[_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) C 執行階段程式庫中找到的巨集。

```
ATLASSERT(booleanExpression);
```

### <a name="parameters"></a>參數

*booleanExpression*<br/>
（包括指標） 的運算式，評估為非零值則為 0。

### <a name="remarks"></a>備註

在偵錯組建中，評估 ATLASSERT *booleanExpression*結果為 false 時，產生偵錯報表。

## <a name="requirements"></a>需求

**標頭：** atldef.h

##  <a name="atlensure"></a>  ATLENSURE

這個巨集用來驗證傳遞至函式的參數。

```
ATLENSURE(booleanExpression);
ATLENSURE_THROW(booleanExpression, hr);
```

### <a name="parameters"></a>參數

*booleanExpression*<br/>
指定要測試的布林運算式。

*hr*<br/>
指定要傳回的錯誤碼。

### <a name="remarks"></a>備註

這些巨集提供一個機制來偵測並通知使用者不正確的參數使用方式。

巨集會呼叫 ATLASSERT 和條件如果失敗呼叫`AtlThrow`。

ATLENSURE 萬一`AtlThrow`E_FAIL 呼叫。

ATLENSURE_THROW 萬一`AtlThrow`呼叫指定的 hresult。

ATLENSURE 和 ATLASSERT 之間的差異是 ATLENSURE 在發行組建也如同偵錯組建中，要擲回例外狀況。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#108](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_1.cpp)]

## <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="atltracenotimpl"></a>  ATLTRACENOTIMPL

在偵錯組建中的 ATL，會傳送字串" *funcname*未實作 」 的傾印裝置，然後傳回 E_NOTIMPL。

```
ATLTRACENOTIMPL(funcname);
```

### <a name="parameters"></a>參數

*funcname*<br/>
[in]字串，包含未實作的函式的名稱。

### <a name="remarks"></a>備註

在發行組建中，只會傳回 E_NOTIMPL。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#127](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_2.cpp)]

## <a name="requirements"></a>需求

**標頭：** atltrace.h

##  <a name="atltrace"></a>  ATLTRACE

報告輸出裝置，例如 [偵錯工具] 視窗中，根據指定的旗標和層級的警告。 包含為了與舊版相容。

```
ATLTRACE(exp);

ATLTRACE(
    DWORD category,
    UINT  level,
    LPCSTR lpszFormat, ...);
```

### <a name="parameters"></a>參數

*exp*<br/>
[in]字串和要傳送給 [輸出] 視窗或捕捉這些訊息的任何應用程式的變數。

*category*<br/>
[in]事件或在其上的方法來報告的類型。 請參閱的 < 備註 > 一份分類。

*level*<br/>
[in]報表的追蹤層級。 請參閱 「 備註 」，如需詳細資訊。

*lpszFormat*<br/>
[in]傳送至傾印裝置格式化的字串。

### <a name="remarks"></a>備註

請參閱[ATLTRACE2](#atltrace2) ATLTRACE 的說明。 ATLTRACE 而且 ATLTRACE2 有相同的行為，ATLTRACE 是為了回溯相容性。

##  <a name="atltrace2"></a>  ATLTRACE2

報告輸出裝置，例如 [偵錯工具] 視窗中，根據指定的旗標和層級的警告。

```
ATLTRACE2(exp);

ATLTRACE2(
    DWORD category,
    UINT level,
    LPCSTRlpszFormat,  ...);
```

### <a name="parameters"></a>參數

*exp*<br/>
[in]要傳送給 [輸出] 視窗或捕捉這些訊息的任何應用程式的字串。

*category*<br/>
[in]事件或在其上的方法來報告的類型。 請參閱的 < 備註 > 一份分類。

*level*<br/>
[in]報表的追蹤層級。 請參閱 「 備註 」，如需詳細資訊。

*lpszFormat*<br/>
[in]`printf`-樣式格式字串，用來建立傳送至傾印裝置的字串。

### <a name="remarks"></a>備註

ATLTRACE2 的簡短形式會將字串寫入至偵錯工具的 [輸出] 視窗。 ATLTRACE2 第二個表單也將輸出寫入至偵錯工具的 [輸出] 視窗，但受限於 ATL/MFC 追蹤工具的設定 (請參閱[ATLTraceTool 範例](../../overview/visual-cpp-samples.md))。 例如，如果您設定*層級*4 以及層級 0 的 ATL/MFC 追蹤工具，您不會看到訊息。 *層級*可以是 0、 1、 2、 3 或 4。 預設值，0，會報告最嚴重的問題。

*分類*參數會列出要設定追蹤旗標。 這些旗標會對應至您想要報告的方法的型別。 下表列出您可以使用有效的追蹤旗標*分類*參數。

### <a name="atl-trace-flags"></a>ATL 追蹤旗標

|ATL 類別|描述|
|------------------|-----------------|
|`atlTraceGeneral`|報告所有的 ATL 應用程式。 預設值。|
|`atlTraceCOM`|在 COM 方法上的報表。|
|`atlTraceQI`|QueryInterface 呼叫上的報表。|
|`atlTraceRegistrar`|在註冊的物件上的報表。|
|`atlTraceRefcount`|變更參考計數的報告。|
|`atlTraceWindowing`|在 windows 的方法; 上的報表例如，回報不正確的訊息對應識別碼。|
|`atlTraceControls`|在控制項; 上的報表例如，回報時終結控制項或它的視窗。|
|`atlTraceHosting`|裝載的訊息; 的報表比方說，會在容器中的用戶端啟動時報告。|
|`atlTraceDBClient`|OLE DB 消費者範本; 上的報表例如，當呼叫 GetData 失敗時，輸出可以包含 HRESULT。|
|`atlTraceDBProvider`|OLE DB 提供者範本; 上的報表比方說，會報告失敗時建立的資料行。|
|`atlTraceSnapin`|MMC 嵌入式管理單元的應用程式的報表。|
|`atlTraceNotImpl`|未指定的函式的報表。|
|`atlTraceAllocation`|偵錯工具中 atldbgmem.h 記憶體所列印的報表訊息。|

### <a name="mfc-trace-flags"></a>MFC 的追蹤旗標

|MFC 類別|描述|
|------------------|-----------------|
|`traceAppMsg`|一般用途，MFC 訊息。 一律建議使用。|
|`traceDumpContext`|從訊息[CDumpContext](../../mfc/reference/cdumpcontext-class.md)。|
|`traceWinMsg`|從 MFC 訊息處理程式碼的訊息。|
|`traceMemory`|從 MFC 的記憶體管理程式碼的訊息。|
|`traceCmdRouting`|從 MFC 的 Windows 訊息的命令路由的程式碼。|
|`traceHtml`|從 MFC DHTML 對話方塊支援的訊息。|
|`traceSocket`|從 MFC 通訊端支援的訊息。|
|`traceOle`|從 MFC 的 OLE 支援的訊息。|
|`traceDatabase`|從 MFC 資料庫支援的訊息。|
|`traceInternet`|MFC 網際網路支援訊息。|

若要宣告的自訂追蹤類別，宣告的全域執行個體`CTraceCategory`類別，如下所示：

[!code-cpp[NVC_ATL_Utilities#109](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_3.cpp)]

類別目錄名稱，而在此範例中，MY_CATEGORY 是您指定的名稱*分類*參數。 第一個參數是類別目錄名稱會出現在 ATL/MFC 追蹤工具。 第二個參數是預設追蹤層級。 這個參數是選擇性的而預設追蹤層級是 0。

若要使用使用者定義的類別：

[!code-cpp[NVC_ATL_Utilities#110](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_4.cpp)]

若要指定您想要篩選追蹤訊息，插入定義這些巨集之前的 Stdafx.h`#include <atlbase.h>`陳述式。

或者，您可以設定篩選條件中的前置處理器指示詞中**屬性頁** 對話方塊。 按一下 **前置處理器**索引標籤，然後再插入到全域**前置處理器定義**編輯方塊。

Atlbase.h 包含 ATLTRACE2 巨集的預設定義，如果您未定義這些符號，然後再處理 atlbase.h，就會使用這些定義。

ATLTRACE2 編譯成發行組建中`(void) 0`。

ATLTRACE2 限制的字串在格式化之後傳送給不能超過 1023年個字元，傾印裝置的內容。

ATLTRACE 而且 ATLTRACE2 有相同的行為，ATLTRACE 是為了回溯相容性。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#111](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_5.cpp)]

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)<br/>
[偵錯和錯誤報告全域函式](../../atl/reference/debugging-and-error-reporting-global-functions.md)
