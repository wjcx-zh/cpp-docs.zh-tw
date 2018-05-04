---
title: 偵錯和錯誤報告巨集 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atldef/ATL::_ATL_DEBUG_INTERFACES
- atldef/ATL::_ATL_DEBUG_QI
- atldef/ATL::ATLASSERT
- afx/ATL::ATLENSURE
- atltrace/ATL::ATLTRACENOTIMPL
- atltrace/ATL::ATLTRACE
dev_langs:
- C++
helpviewer_keywords:
- macros, error reporting
ms.assetid: 4da9b87f-ec5c-4a32-ab93-637780909b9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b99147c9eb9a331d7cc0f9064b858979d00e2804
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="debugging-and-error-reporting-macros"></a>偵錯和錯誤報告巨集
這些巨集提供有用的偵錯和追蹤功能。  
  
|||  
|-|-|  
|[_ATL_DEBUG_INTERFACES](#_atl_debug_interfaces)|寫入，[輸出] 視窗中，任何介面流失的問題，當偵測到`_Module.Term`呼叫。|  
|[_ATL_DEBUG_QI](#_atl_debug_qi)|寫入的所有呼叫`QueryInterface`到輸出視窗。|  
|[ATLASSERT](#atlassert)|執行相同的功能[_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) C 執行階段程式庫中找到的巨集。|  
|[ATLENSURE](#atlensure)|執行參數驗證。 呼叫`AtlThrow`視|  
|[ATLTRACENOTIMPL](#atltracenotimpl)|傳送訊息至傾印裝置未實作指定的函式。|  
|[ATLTRACE](#alttrace)|輸出裝置，例如偵錯工具視窗中，根據指定的旗標和層級的報告警告。 包含為了回溯相容性。|  
|[ATLTRACE2](#atltrace2)|輸出裝置，例如偵錯工具視窗中，根據指定的旗標和層級的報告警告。|  
  
##  <a name="_atl_debug_interfaces"></a>  _ATL_DEBUG_INTERFACES  
 定義此巨集包含任何 ATL 標頭檔，以追蹤所有之前`AddRef`和**發行**呼叫您的元件介面，以 [輸出] 視窗上。  
  
```
#define _ATL_DEBUG_INTERFACES
```  
  
### <a name="remarks"></a>備註  
 追蹤輸出會出現如下所示：  
  
 `ATL: QIThunk - 2008         AddRef  :   Object = 0x00d81ba0   Refcount = 1   CBug - IBug`  
  
 每個追蹤的第一個部分一定會`ATL: QIThunk`。 接下來是值，識別特定*介面 thunk*正在使用。 介面 thunk 是用來維護參考計數，並提供在這裡使用的追蹤功能的物件。 在每次呼叫建立新的介面 thunk`QueryInterface`除了要求**IUnknown**介面 （在此情況下，為相同的 thunk 都會將每次傳回符合 COM 的身分識別的規則）。  
  
 接下來，您會看到`AddRef`或**發行**表示所呼叫的方法。 接下來，您會看到值，識別已變更其介面的參考計數的物件。 追蹤的值是**這**物件的指標。  
  
 追蹤參考計數會在之後的 thunk 上的參考計數`AddRef`或**發行**呼叫。 請注意，此參考計數可能不符合物件的參考計數。 每個 thunk 會維護其本身參考計數可協助您完全符合 COM 的參考計數的規則。  
  
 追蹤資訊的最後一段是物件，而且會影響的介面名稱`AddRef`或**發行**呼叫。  
  
 任何介面伺服器關閉時偵測到遺漏和`_Module.Term`呼叫將會記錄如下：  
  
 `ATL: QIThunk - 2005         LEAK    :   Object = 0x00d81ca0   Refcount = 1   MaxRefCount = 1   CBug - IBug`  
  
 這裡的資訊提供，都會直接對應到上一個追蹤陳述式中提供的資訊，因此您可以檢查的參考計數的整個介面 thunk 的整個存留期。 此外，取得最大的參考計數的指示該介面 thunk。  
  
> [!NOTE]
> `_ATL_DEBUG_INTERFACES` 可以在零售組建中使用。  
  
##  <a name="_atl_debug_qi"></a>  _ATL_DEBUG_QI  
 寫入的所有呼叫`QueryInterface`到輸出視窗。  
  
```
#define _ATL_DEBUG_QI
```  
  
### <a name="remarks"></a>備註  
 如果呼叫`QueryInterface`失敗，[輸出] 視窗會顯示：  
  
 *介面名稱* - `failed`  
  
##  <a name="atlassert"></a>  ATLASSERT  
 `ATLASSERT`巨集執行相同的功能[_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) C 執行階段程式庫中找到的巨集。  
  
```
ATLASSERT(booleanExpression);
```  
  
### <a name="parameters"></a>參數  
 `booleanExpression`  
 （包括指標） 的運算式，評估為非零，則為 0。  
  
### <a name="remarks"></a>備註  
 在偵錯組建`ATLASSERT`評估`booleanExpression`結果為 false 時，產生偵錯報表。  

## <a name="requirements"></a>需求  
 **標頭：** atldef.h  
    
##  <a name="atlensure"></a>  ATLENSURE  
 這個巨集用來驗證傳遞至函式的參數。  
  
```
ATLENSURE(booleanExpression);
ATLENSURE_THROW(booleanExpression, hr);
```  
  
### <a name="parameters"></a>參數  
 `booleanExpression`  
 指定要測試的布林運算式。  
  
 `hr`  
 指定要傳回的錯誤碼。  
  
### <a name="remarks"></a>備註  
 這些巨集提供機制來偵測並通知使用者的不正確的參數使用方式。  
  
 巨集呼叫`ATLASSERT`如果條件未通過呼叫`AtlThrow`。  
  
 在**ATLENSURE**的情況下，`AtlThrow`稱為 E_FAIL。  
  
 在**ATLENSURE_THROW**的情況下，`AtlThrow`呼叫以指定的 HRESULT。  
  
 之間的差異**ATLENSURE**和`ATLASSERT`在於**ATLENSURE**會擲回版本中的例外狀況以及建置與偵錯組建。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#108](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_1.cpp)]  

## <a name="requirements"></a>需求  
 **標頭：** afx.h  

##  <a name="atltracenotimpl"></a>  ATLTRACENOTIMPL  
 在偵錯組建的 ATL，會將字串"`funcname`未實作 」 傾印裝置和傳回**E_NOTIMPL**。  
  
```
ATLTRACENOTIMPL(funcname);
```  
  
### <a name="parameters"></a>參數  
 `funcname`  
 [in]包含未實作的函式名稱的字串。  
  
### <a name="remarks"></a>備註  
 在發行組建中只會傳回**E_NOTIMPL**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#127](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_2.cpp)]  
  
## <a name="requirements"></a>需求  
 **標頭：** atltrace.h 

##  <a name="atltrace"></a>  ATLTRACE
 輸出裝置，例如偵錯工具視窗中，根據指定的旗標和層級的報告警告。 包含為了回溯相容性。  
  
```
ATLTRACE(exp);

ATLTRACE(  
    DWORD category,
    UINT  level,
    LPCSTR lpszFormat, ...);
```  
  
### <a name="parameters"></a>參數  
 `exp`  
 [in]字串和要傳送給 Visual c + + 的 [輸出] 視窗或任何應用程式，這些訊息的變數。  
  
 `category`  
 [in]事件或在其上的方法來報告的類型。 請參閱類別目錄的清單中的 < 備註 >。  
  
 `level`  
 [in]報表的追蹤層級。 請參閱 < 備註 > 以取得詳細資料。  
  
 `lpszFormat`  
 [in]格式化的字串傳送至傾印裝置。  
  
### <a name="remarks"></a>備註  
 請參閱[ATLTRACE2](#atltrace2)的說明**ATLTRACE**。 **ATLTRACE**和`ATLTRACE2`有相同的行為， **ATLTRACE**是為了與舊版相容。  
  
##  <a name="atltrace2"></a>  ATLTRACE2  
 輸出裝置，例如偵錯工具視窗中，根據指定的旗標和層級的報告警告。  
  
```
ATLTRACE2(exp);

ATLTRACE2(
    DWORD category,
    UINT level,
    LPCSTRlpszFormat,  ...);
```  
  
### <a name="parameters"></a>參數  
 `exp`  
 [in]要傳送給 Visual c + + 的 [輸出] 視窗或任何應用程式，這些訊息的字串。  
  
 `category`  
 [in]事件或在其上的方法來報告的類型。 請參閱類別目錄的清單中的 < 備註 >。  
  
 `level`  
 [in]報表的追蹤層級。 請參閱 < 備註 > 以取得詳細資料。  
  
 `lpszFormat`  
 [in]`printf`-樣式格式字串，用來建立傳送至傾印裝置的字串。  
  
### <a name="remarks"></a>備註  
 簡短形式`ATLTRACE2`寫入字串，以偵錯工具的輸出視窗。 第二種`ATLTRACE2`也將輸出寫入到偵錯工具的 [輸出] 視窗，但受限於 ATL/MFC 追蹤工具的設定 (請參閱[ATLTraceTool 範例](../../visual-cpp-samples.md))。 例如，如果您設定`level`4 以及 ATL/MFC 追蹤工具，為層級 0，不會看到訊息。 *層級*可以是 0、 1、 2、 3 或 4。 預設值，0，會報告最嚴重的問題。  
  
 `category`參數列出要設定追蹤旗標。 這些旗標會對應至您想要報告的方法的型別。 下表列出您可以使用有效的追蹤旗標`category`參數。  
  
### <a name="atl-trace-flags"></a>ATL 追蹤旗標  
  
|ATL 類別|描述|  
|------------------|-----------------|  
|`atlTraceGeneral`|報告所有的 ATL 應用程式。 預設值。|  
|`atlTraceCOM`|報告 COM 方法。|  
|`atlTraceQI`|報告的 QueryInterface 呼叫。|  
|`atlTraceRegistrar`|物件的登錄來報告。|  
|`atlTraceRefcount`|變更參考計數的報告。|  
|`atlTraceWindowing`|Windows 方法; 上的報表例如，報告無效的訊息對應識別碼。|  
|`atlTraceControls`|報表上的控制項。例如，報表的控制項或其視窗終結時。|  
|`atlTraceHosting`|報表裝載訊息。例如，報告容器中的用戶端啟動時。|  
|`atlTraceDBClient`|OLE DB 消費者範本; 上的報表例如，當 GetData 而失敗的呼叫，輸出可以包含 HRESULT。|  
|`atlTraceDBProvider`|OLE DB 提供者範本; 上的報表例如，報告失敗時建立的資料行。|  
|`atlTraceSnapin`|MMC 嵌入式管理單元的應用程式的報表。|  
|`atlTraceNotImpl`|報告指定的函式未實作。|  
|**atlTraceAllocation**|偵錯工具中 atldbgmem.h 的記憶體來列印報表訊息。|  
  
### <a name="mfc-trace-flags"></a>MFC 追蹤旗標  
  
|MFC 類別|描述|  
|------------------|-----------------|  
|**traceAppMsg**|一般用途，MFC 訊息。 一律建議。|  
|**traceDumpContext**|從訊息[CDumpContext](../../mfc/reference/cdumpcontext-class.md)。|  
|**traceWinMsg**|從 MFC 的郵件處理程式碼的訊息。|  
|**traceMemory**|從 MFC 的記憶體管理程式碼的訊息。|  
|**traceCmdRouting**|從 MFC 的 Windows 訊息的命令路由的程式碼。|  
|**traceHtml**|從 MFC 的 DHTML 對話方塊支援的訊息。|  
|**traceSocket**|從 MFC 的通訊端支援的訊息。|  
|**traceOle**|從 MFC 的 OLE 支援的訊息。|  
|**traceDatabase**|從 MFC 資料庫支援的訊息。|  
|**traceInternet**|從 MFC 的網際網路支援的訊息。|  
  
 若要宣告自訂追蹤類別，宣告的全域執行個體`CTraceCategory`類別，如下所示：  
  
 [!code-cpp[NVC_ATL_Utilities#109](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_3.cpp)]  
  
 分類名稱`MY_CATEGORY`在此範例中，是您指定的名稱`category`參數。 第一個參數是類別目錄名稱會出現在 ATL/MFC 追蹤工具。 第二個參數是預設的追蹤層級。 這個參數是選擇性，而且預設追蹤層級為 0。  
  
 若要使用的使用者定義類別目錄：  
  
 [!code-cpp[NVC_ATL_Utilities#110](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_4.cpp)]  
  
 若要指定您想要篩選追蹤訊息，插入這些巨集的定義之前 Stdafx.h`#include <atlbase.h>`陳述式。  
  
 或者，您可以設定篩選器中的前置處理器指示詞中**屬性頁** 對話方塊。 按一下**前置處理器**索引標籤，然後插入 全域到**前置處理器定義**編輯方塊。  
  
 Atlbase.h 包含 default 定義的`ATLTRACE2`巨集和這些定義將用於如果 atlbase.h 處理之前，未定義這些符號。  
  
 在發行組建中`ATLTRACE2`會編譯成`(void) 0`。  
  
 `ATLTRACE2` 限制的內容傳送至不超過 1023 個字元，傾印裝置完成格式化後的字串。  
  
 **ATLTRACE**和`ATLTRACE2`有相同的行為， **ATLTRACE**是為了與舊版相容。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities#111](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_5.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [巨集](../../atl/reference/atl-macros.md)   
 [偵錯和錯誤報告全域函式](../../atl/reference/debugging-and-error-reporting-global-functions.md)
