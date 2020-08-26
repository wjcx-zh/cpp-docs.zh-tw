---
title: 調試和錯誤報表宏
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
ms.openlocfilehash: 2bcdfb474ee852e55bd54f1b125716e7785f28be
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833474"
---
# <a name="debugging-and-error-reporting-macros"></a>調試和錯誤報表宏

這些宏提供實用的調試和追蹤功能。

|名稱|描述|
|-|-|
|[_ATL_DEBUG_INTERFACES](#_atl_debug_interfaces)|寫入至 [輸出] 視窗，呼叫時偵測到的任何介面流失 `_Module.Term` 。|
|[_ATL_DEBUG_QI](#_atl_debug_qi)|將所有的呼叫寫入至 `QueryInterface` [輸出] 視窗。|
|[ATLASSERT](#atlassert)|執行的功能與 C 執行時間程式庫中找到的 [_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 宏相同。|
|[ATLENSURE](#atlensure)|執行參數驗證。 視 `AtlThrow` 需要呼叫|
|[ATLTRACENOTIMPL](#atltracenotimpl)|將訊息傳送給傾印裝置，指出未執行指定的函式。|
|[ATLTRACE](#atltrace)|根據指定的旗標和層級，將警告報告至輸出裝置，例如偵錯工具視窗。 為了與舊版相容而納入。|
|[ATLTRACE2](#atltrace2)|根據指定的旗標和層級，將警告報告至輸出裝置，例如偵錯工具視窗。|

## <a name="_atl_debug_interfaces"></a><a name="_atl_debug_interfaces"></a> _ATL_DEBUG_INTERFACES

在包含任何 ATL 標頭檔之前定義這個宏，以 `AddRef` 追蹤 `Release` 元件介面上的所有和呼叫至輸出視窗。

```
#define _ATL_DEBUG_INTERFACES
```

### <a name="remarks"></a>備註

追蹤輸出將會出現，如下所示：

`ATL: QIThunk - 2008         AddRef  :   Object = 0x00d81ba0   Refcount = 1   CBug - IBug`

每個追蹤的第一個部分一律會是 `ATL: QIThunk` 。 Next 是一個值，用來識別使用中的特定 *介面 Thunk* 。 介面 Thunk 是用來維護參考計數的物件，並提供此處所使用的追蹤功能。 在每次呼叫時都會建立新的介面 Thunk `QueryInterface` `IUnknown` ，但 (在此情況下，每次都會傳回相同的 Thunk，以符合 COM 的身分識別規則) 。

接下來，您將會看到 `AddRef` 或 `Release` 指出所呼叫的方法。 之後，您將會看到一個值，可識別其介面參考計數已變更的物件。 追蹤的值是 **`this`** 物件的指標。

所追蹤的參考計數是在呼叫或之後，該 Thunk 上的參考計數 `AddRef` `Release` 。 請注意，此參考計數可能不符合物件的參考計數。 每個 Thunk 都會維護它自己的參考計數，以協助您完全符合 COM 的參考計數規則。

追蹤的最後一項資訊是物件的名稱，以及受到或呼叫影響的介面 `AddRef` `Release` 。

當伺服器關機且被呼叫時所偵測到的任何介面流失 `_Module.Term` 都會記錄如下：

`ATL: QIThunk - 2005         LEAK    :   Object = 0x00d81ca0   Refcount = 1   MaxRefCount = 1   CBug - IBug`

此處提供的資訊會直接對應到先前追蹤語句中提供的資訊，因此您可以在介面 Thunk 的整個存留期內檢查參考計數。 此外，您也會看到該介面 Thunk 上的最大參考計數。

> [!NOTE]
> _ATL_DEBUG_INTERFACES 可以在零售組建中使用。

## <a name="_atl_debug_qi"></a><a name="_atl_debug_qi"></a> _ATL_DEBUG_QI

將所有的呼叫寫入至 `QueryInterface` [輸出] 視窗。

```
#define _ATL_DEBUG_QI
```

### <a name="remarks"></a>備註

如果呼叫 `QueryInterface` 失敗，將會顯示輸出視窗：

*介面名稱* - `failed`

## <a name="atlassert"></a><a name="atlassert"></a> ATLASSERT

ATLASSERT 宏執行的功能與 C 執行時間程式庫中找到的 [_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 宏相同。

```
ATLASSERT(booleanExpression);
```

### <a name="parameters"></a>參數

*booleanExpression*<br/>
運算式 (包含評估為非零或0的指標) 。

### <a name="remarks"></a>備註

在 debug 組建中，ATLASSERT 會評估 *booleanExpression* ，並在結果為 false 時產生 debug 報表。

## <a name="requirements"></a>規格需求

**標頭：** atldef。h

## <a name="atlensure"></a><a name="atlensure"></a> ATLENSURE

這個宏是用來驗證傳遞給函式的參數。

```
ATLENSURE(booleanExpression);
ATLENSURE_THROW(booleanExpression, hr);
```

### <a name="parameters"></a>參數

*booleanExpression*<br/>
指定要測試的布林運算式。

*小時*<br/>
指定要傳回的錯誤碼。

### <a name="remarks"></a>備註

這些宏會提供一種機制來偵測並通知使用者不正確的參數使用方式。

宏會呼叫 ATLASSERT，如果條件失敗，則會呼叫 `AtlThrow` 。

在 ATLENSURE 案例中， `AtlThrow` 會使用 E_FAIL 來呼叫。

在 ATLENSURE_THROW 案例中， `AtlThrow` 會使用指定的 HRESULT 來呼叫。

ATLENSURE 和 ATLASSERT 之間的差異在於 ATLENSURE 會在發行組建中以及在 Debug 組建中擲回例外狀況。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#108](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_1.cpp)]

## <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="atltracenotimpl"></a><a name="atltracenotimpl"></a> ATLTRACENOTIMPL

在 ATL 的 debug 組建中，會傳送字串 " *funcname* 未實作為傾印裝置，並傳回 E_NOTIMPL。

```
ATLTRACENOTIMPL(funcname);
```

### <a name="parameters"></a>參數

*funcname*<br/>
在字串，其中包含未實作為函式的名稱。

### <a name="remarks"></a>備註

在發行組建中，只會傳回 E_NOTIMPL。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#127](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_2.cpp)]

## <a name="requirements"></a>規格需求

**標頭：** atltrace。h

## <a name="atltrace"></a><a name="atltrace"></a> ATLTRACE

根據指定的旗標和層級，將警告報告至輸出裝置，例如偵錯工具視窗。 為了與舊版相容而納入。

```
ATLTRACE(exp);

ATLTRACE(
    DWORD category,
    UINT  level,
    LPCSTR lpszFormat, ...);
```

### <a name="parameters"></a>參數

*exp*<br/>
在要傳送至輸出視窗的字串和變數，或任何會將這些訊息陷阱的應用程式。

*類別*<br/>
在要報告的事件或方法的類型。 如需類別清單，請參閱備註。

*等級*<br/>
在要報告的追蹤層級。 如需詳細資訊，請參閱備註。

*lpszFormat*<br/>
在要傳送給傾印裝置的格式化字串。

### <a name="remarks"></a>備註

如需 ATLTRACE 的說明，請參閱 [ATLTRACE2](#atltrace2) 。 ATLTRACE 和 ATLTRACE2 具有相同的行為，而 ATLTRACE 則是為了與舊版相容。

## <a name="atltrace2"></a><a name="atltrace2"></a> ATLTRACE2

根據指定的旗標和層級，將警告報告至輸出裝置，例如偵錯工具視窗。

```
ATLTRACE2(exp);

ATLTRACE2(
    DWORD category,
    UINT level,
    LPCSTR lpszFormat,  ...);
```

### <a name="parameters"></a>參數

*exp*<br/>
在要傳送至輸出視窗的字串，或任何會將這些訊息陷阱的應用程式。

*類別*<br/>
在要報告的事件或方法的類型。 如需類別清單，請參閱備註。

*等級*<br/>
在要報告的追蹤層級。 如需詳細資訊，請參閱備註。

*lpszFormat*<br/>
在 `printf`用來建立要傳送給傾印裝置之字串的樣式格式字串。

### <a name="remarks"></a>備註

ATLTRACE2 的簡短形式會將字串寫入偵錯工具的輸出視窗。 第二種形式的 ATLTRACE2 也會將輸出寫入偵錯工具的輸出視窗，但受限於 ATL/MFC 追蹤工具的設定 (參閱 [ATLTraceTool 範例](../../overview/visual-cpp-samples.md)) 。 例如，如果您將 *層級* 設定為4，而 ATL/MFC 追蹤工具的層級為0，則不會看到訊息。 *層級* 可以是0、1、2、3或4。 預設值為0，只會報告最嚴重的問題。

*Category*參數會列出要設定的追蹤旗標。 這些旗標會對應至您想要報告的方法類型。 下表列出可用於 *category* 參數的有效追蹤旗標。

### <a name="atl-trace-flags"></a>ATL 追蹤旗標

|ATL 類別|描述|
|------------------|-----------------|
|`atlTraceGeneral`|所有 ATL 應用程式的報告。 預設值。|
|`atlTraceCOM`|COM 方法的報告。|
|`atlTraceQI`|QueryInterface 呼叫的報告。|
|`atlTraceRegistrar`|有關註冊物件的報告。|
|`atlTraceRefcount`|變更參考計數的報告。|
|`atlTraceWindowing`|Windows 方法的報告;例如，報告不正確訊息對應識別碼。|
|`atlTraceControls`|控制項的報表;例如，當控制項或其視窗損毀時，就會報告。|
|`atlTraceHosting`|報表裝載訊息;例如，當容器中的用戶端啟動時，就會報告。|
|`atlTraceDBClient`|報表 OLE DB 取用者範本;例如，當對操作程式的呼叫失敗時，輸出可以包含 HRESULT。|
|`atlTraceDBProvider`|報表 OLE DB 提供者範本;例如，報表建立資料行失敗。|
|`atlTraceSnapin`|MMC 嵌入式管理單元應用程式的報告。|
|`atlTraceNotImpl`|報告指出的函式不是實作為。|
|`atlTraceAllocation`|報告 atldbgmem 中的記憶體偵錯工具所列印的訊息。|

### <a name="mfc-trace-flags"></a>MFC 追蹤旗標

|MFC 類別|描述|
|------------------|-----------------|
|`traceAppMsg`|一般用途的 MFC 訊息。 一律建議。|
|`traceDumpContext`|來自 [CDumpCoNtext](../../mfc/reference/cdumpcontext-class.md)的訊息。|
|`traceWinMsg`|MFC 訊息處理常式代碼中的訊息。|
|`traceMemory`|來自 MFC 記憶體管理程式碼的訊息。|
|`traceCmdRouting`|來自 MFC Windows 命令路由程式碼的訊息。|
|`traceHtml`|來自 MFC 之 DHTML 對話方塊支援的訊息。|
|`traceSocket`|來自 MFC 通訊端支援的訊息。|
|`traceOle`|來自 MFC 的 OLE 支援的訊息。|
|`traceDatabase`|來自 MFC 資料庫支援的訊息。|
|`traceInternet`|來自 MFC 網際網路支援的訊息。|

若要宣告自訂追蹤分類，請宣告類別的全域實例，如下所示 `CTraceCategory` ：

[!code-cpp[NVC_ATL_Utilities#109](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_3.cpp)]

此範例中的分類名稱（MY_CATEGORY）是您指定給 *category* 參數的名稱。 第一個參數是將出現在 ATL/MFC 追蹤工具中的分類名稱。 第二個參數是預設的追蹤層級。 這個參數是選擇性的，預設追蹤層級是0。

若要使用使用者定義的類別：

[!code-cpp[NVC_ATL_Utilities#110](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_4.cpp)]

若要指定您要篩選追蹤訊息，請在語句之前，將這些宏的定義插入 Stdafx.h 中。 `#include <atlbase.h>`

或者，您也可以在 [ **屬性頁** ] 對話方塊的預處理器指示詞中設定篩選。 按一下 [ **預處理器** ] 索引標籤，然後將全域插入 [ **預處理器定義** ] 編輯方塊中。

Atlbase.h 包含 ATLTRACE2 宏的預設定義，如果您未在處理 atlbase.h 之前定義這些符號，則會使用這些定義。

在發行組建中，ATLTRACE2 會編譯為 `(void) 0` 。

ATLTRACE2 會在格式化之後，將傳送給傾印裝置的字串內容限制為不超過1023個字元。

ATLTRACE 和 ATLTRACE2 具有相同的行為，而 ATLTRACE 則是為了與舊版相容。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#111](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_5.cpp)]

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)<br/>
[調試和錯誤報表全域函式](../../atl/reference/debugging-and-error-reporting-global-functions.md)
