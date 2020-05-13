---
title: 除錯和錯誤報告巨集
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
ms.openlocfilehash: 69ab6e17bfb1ec85ddb5b8c19c18010a9b4f3df6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330192"
---
# <a name="debugging-and-error-reporting-macros"></a>除錯和錯誤報告巨集

這些宏提供有用的調試和跟蹤工具。

|||
|-|-|
|[_ATL_DEBUG_INTERFACES](#_atl_debug_interfaces)|寫入輸出視窗時檢測到`_Module.Term`的任何介面洩漏。|
|[_ATL_DEBUG_QI](#_atl_debug_qi)|將所有調用寫入`QueryInterface`輸出視窗。|
|[ATLASSERT](#atlassert)|執行與 C 運行時[庫中_ASSERTE宏](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)相同的功能。|
|[ATLENSURE](#atlensure)|執行參數驗證。 如果需要`AtlThrow`,請致電|
|[ATLTRACENOTIMPL](#atltracenotimpl)|向轉儲設備發送消息,指出未實現指定的功能。|
|[ATLTRACE](#atltrace)|根據指示的標誌和級別向輸出設備(如調試器視窗)報告警告。 包括用於向後相容性。|
|[ATLTRACE2](#atltrace2)|根據指示的標誌和級別向輸出設備(如調試器視窗)報告警告。|

## <a name="_atl_debug_interfaces"></a><a name="_atl_debug_interfaces"></a>_ATL_DEBUG_INTERFACES

在包含任何 ATL 標頭檔以追蹤元件`AddRef`介面`Release`上 的所有和調用到輸出視窗之前,請定義此巨集。

```
#define _ATL_DEBUG_INTERFACES
```

### <a name="remarks"></a>備註

追蹤輸出將顯示如下:

`ATL: QIThunk - 2008         AddRef  :   Object = 0x00d81ba0   Refcount = 1   CBug - IBug`

每個追蹤的第一部份將始終為`ATL: QIThunk`。 接下來是標識正在使用的特定*介面 thunk*的值。 介面 thunk 是用於維護引用計數並提供此處使用的跟蹤功能的物件。 `QueryInterface`除了`IUnknown`對介面的請求(在這種情況下,每次返回相同的 thunk 以遵守 COM 的標識規則),每次調用 時都會創建一個新的介面 thunk。

接下來,您將看到`AddRef``Release`或指示調用了哪種方法。 之後,您將看到一個值,用於標識其介面引用計數已更改的物件。 跟蹤的值是物件的**此**指標。

跟蹤的引用計數是調用或`AddRef``Release`調用後該 thunk 上的引用計數。 請注意,此引用計數可能與物件的引用計數不匹配。 每個 thunk 都維護自己的引用計數,以説明您完全遵守 COM 的引用計數規則。

跟蹤的最後一條資訊是對象的名稱和`AddRef`受`Release`或調用影響的介面。

伺服器關閉並`_Module.Term`呼叫時偵測到的任何介面洩漏都將記錄如下:

`ATL: QIThunk - 2005         LEAK    :   Object = 0x00d81ca0   Refcount = 1   MaxRefCount = 1   CBug - IBug`

此處提供的資訊直接映射到前面的跟蹤語句中提供的資訊,因此您可以檢查介面 thunk 的整個生存期內的引用計數。 此外,您還可以顯示該介面 thunk 上的最大引用計數。

> [!NOTE]
> _ATL_DEBUG_INTERFACES可用於零售版本。

## <a name="_atl_debug_qi"></a><a name="_atl_debug_qi"></a>_ATL_DEBUG_QI

將所有調用寫入`QueryInterface`輸出視窗。

```
#define _ATL_DEBUG_QI
```

### <a name="remarks"></a>備註

如果對`QueryInterface`撥號失敗,輸出視窗會顯示:

*介面名稱* - `failed`

## <a name="atlassert"></a><a name="atlassert"></a>ATLASSERT

ATLASSERT 宏執行的功能與 C 運行時庫中的[_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)宏相同。

```
ATLASSERT(booleanExpression);
```

### <a name="parameters"></a>參數

*布林運算式*<br/>
計算為非零或 0 的運算式(包括指標)。

### <a name="remarks"></a>備註

在調試生成中,ATLASSERT 會評估*布爾運算式*,並在結果為 false 時生成調試報告。

## <a name="requirements"></a>需求

**標題:** atldef.h

## <a name="atlensure"></a><a name="atlensure"></a>ATLENSURE

此宏用於驗證傳遞給函數的參數。

```
ATLENSURE(booleanExpression);
ATLENSURE_THROW(booleanExpression, hr);
```

### <a name="parameters"></a>參數

*布林運算式*<br/>
指定要測試的布爾表達式。

*人力資源*<br/>
指定要返回的錯誤代碼。

### <a name="remarks"></a>備註

這些宏提供了一種機制來檢測和通知使用者不正確的參數使用。

巨集呼叫 ATLASSERT,如果條件失敗`AtlThrow`呼叫 。

在 ATLENSURE`AtlThrow`的情況下 ,用E_FAIL調用。

在ATLENSURE_THROW情況下,`AtlThrow`使用指定的 HRESULT 調用。

ATLENSURE 和 ATLASSERT 之間的區別在於 ATLENSURE 在發佈版本和調試版本中引發異常。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#108](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_1.cpp)]

## <a name="requirements"></a>需求

**標題:** afx.h

## <a name="atltracenotimpl"></a><a name="atltracenotimpl"></a>ATLTRACENOTIMPL

在 ATL 的調試版本中,將字串"未實現*funcname"* 發送到轉儲設備並返回E_NOTIMPL。

```
ATLTRACENOTIMPL(funcname);
```

### <a name="parameters"></a>參數

*樂趣名稱*<br/>
[在]包含未實現的函數的名稱的字串。

### <a name="remarks"></a>備註

在版本生成中,只需返回E_NOTIMPL。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#127](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_2.cpp)]

## <a name="requirements"></a>需求

**標題:** atltrace.h

## <a name="atltrace"></a><a name="atltrace"></a>ATLTRACE

根據指示的標誌和級別向輸出設備(如調試器視窗)報告警告。 包括用於向後相容性。

```
ATLTRACE(exp);

ATLTRACE(
    DWORD category,
    UINT  level,
    LPCSTR lpszFormat, ...);
```

### <a name="parameters"></a>參數

*exp*<br/>
[在]要發送到輸出視窗或任何陷印這些消息的應用程式的字串和變數。

*類別*<br/>
[在]要報告的事件或方法的類型。 有關類別清單,請參閱備註。

*水平*<br/>
[在]要報告的跟蹤級別。 有關詳細資訊,請參閱備註。

*lpsz格式*<br/>
[在]要送出到轉儲裝置的格式化字串。

### <a name="remarks"></a>備註

有關 ATLTRACE 的說明,請參閱[ATLTRACE2。](#atltrace2) ATLTRACE 和 ATLTRACE2 具有相同的行為,ATLTRACE 包含在向後相容性中。

## <a name="atltrace2"></a><a name="atltrace2"></a>ATLTRACE2

根據指示的標誌和級別向輸出設備(如調試器視窗)報告警告。

```
ATLTRACE2(exp);

ATLTRACE2(
    DWORD category,
    UINT level,
    LPCSTR lpszFormat,  ...);
```

### <a name="parameters"></a>參數

*exp*<br/>
[在]要發送到輸出視窗或任何陷印這些消息的應用程式的字串。

*類別*<br/>
[在]要報告的事件或方法的類型。 有關類別清單,請參閱備註。

*水平*<br/>
[在]要報告的跟蹤級別。 有關詳細資訊,請參閱備註。

*lpsz格式*<br/>
[在]用於`printf`建立要送出到轉印裝置的字串的 -style 格式字串。

### <a name="remarks"></a>備註

ATLTRACE2 的短形式將字串寫入調試器的輸出視窗。 ATLTRACE2 的第二種形式還會將輸出寫入調試器的輸出視窗,但受 ATL/MFC 跟蹤工具的設置的約束(請參閱[ATLTraceTool 示例](../../overview/visual-cpp-samples.md))。 例如,如果將*級別*設置為 4,將 ATL/MFC 跟蹤工具設置為級別 0,則看不到消息。 *級別*可以是 0、1、2、3 或 4。 默認值 0 僅報告最嚴重的問題。

*類別*參數列出要設置的跟蹤標誌。 這些標誌對應於要為其報告的方法類型。 下表列出了可用於*類別*參數的有效跟蹤標誌。

### <a name="atl-trace-flags"></a>ATL 追蹤標誌

|ATL 類別|描述|
|------------------|-----------------|
|`atlTraceGeneral`|所有 ATL 應用程式的報告。 預設值。|
|`atlTraceCOM`|有關 COM 方法的報告。|
|`atlTraceQI`|有關查詢介面調用的報告。|
|`atlTraceRegistrar`|關於物件註冊的報告。|
|`atlTraceRefcount`|關於更改引用計數的報告。|
|`atlTraceWindowing`|關於視窗方法的報告;例如,報告無效的消息映射 ID。|
|`atlTraceControls`|關於控制的報告;例如,當控件或其視窗被銷毀時,報告。|
|`atlTraceHosting`|報告託管消息;例如,當容器中的用戶端被啟動時,將報告。|
|`atlTraceDBClient`|有關 OLE DB 消費者範本的報告;例如,當對 GetData 的調用失敗時,輸出可以包含 HRESULT。|
|`atlTraceDBProvider`|有關 OLE DB 提供程式範本的報告;例如,如果創建列失敗,則報告。|
|`atlTraceSnapin`|MMC SnapIn 應用程式的報告。|
|`atlTraceNotImpl`|報告未實現指示的功能。|
|`atlTraceAllocation`|報告由 atldbgmem.h 中的記憶體除錯工具列印的消息。|

### <a name="mfc-trace-flags"></a>MFC 追蹤標誌

|MFC 類別|描述|
|------------------|-----------------|
|`traceAppMsg`|一般用途,MFC 消息。 始終推薦。|
|`traceDumpContext`|從[CDumpContext 的訊息](../../mfc/reference/cdumpcontext-class.md)。|
|`traceWinMsg`|來自 MFC 消息處理代碼的消息。|
|`traceMemory`|來自 MFC 記憶體管理代碼的消息。|
|`traceCmdRouting`|來自 MFC 的 Windows 命令路由代碼的消息。|
|`traceHtml`|來自 MFC 的 DHTML 對話方塊支援的消息。|
|`traceSocket`|來自 MFC 的套接字支援的消息。|
|`traceOle`|來自 MFC OLE 支援的消息。|
|`traceDatabase`|來自 MFC 資料庫支援的消息。|
|`traceInternet`|來自 MFC 互聯網支援的消息。|

要聲明自定義追蹤類別,可以聲明類的全域實例,`CTraceCategory`如下所示:

[!code-cpp[NVC_ATL_Utilities#109](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_3.cpp)]

在本範例中MY_CATEGORY類別名稱是您為*類別*參數指定的名稱。 第一個參數是將出現在 ATL/MFC 跟蹤工具中的類別名稱。 第二個參數是默認跟蹤級別。 此參數是可選的,默認跟蹤級別為 0。

要使用使用者定義的類別:

[!code-cpp[NVC_ATL_Utilities#110](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_4.cpp)]

若要指定要篩選追蹤訊息,請在敘述之前將這些巨集的定義插入到 Stdafx.h 中`#include <atlbase.h>`。

或者,您可以在 **「屬性頁**」對話框中的預處理器指令中設置篩選器。 按下 **「預處理器**」選項卡,然後將全域插入到 **「預處理器定義**」編輯框中。

Atlbase.h 包含 ATLTRACE2 宏的預設定義,如果您在處理 atlbase.h 之前未定義這些符號,將使用這些定義。

在版本版本中,ATLTRACE2 編譯`(void) 0`到 。

ATLTRACE2 將要發送到轉儲設備的字串的內容限制在格式化後不超過 1023 個字元。

ATLTRACE 和 ATLTRACE2 具有相同的行為,ATLTRACE 包含在向後相容性中。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#111](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_5.cpp)]

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)<br/>
[除錯及錯誤報告全域函數](../../atl/reference/debugging-and-error-reporting-global-functions.md)
