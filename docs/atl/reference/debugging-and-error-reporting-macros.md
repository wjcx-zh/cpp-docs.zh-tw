---
title: "偵錯和錯誤報告巨集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- macros, error reporting
ms.assetid: 4da9b87f-ec5c-4a32-ab93-637780909b9d
caps.latest.revision: 18
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 112b43c325d4b73d2cc15ba41d9aac255c74da8a
ms.lasthandoff: 02/24/2017

---
# <a name="debugging-and-error-reporting-macros"></a>偵錯和錯誤報告巨集
這些巨集提供有用的偵錯和追蹤功能。  
  
|||  
|-|-|  
|[_ATL_DEBUG_INTERFACES](#_atl_debug_interfaces)|將任何介面會遺漏，寫入 [輸出] 視窗中，當偵測到`_Module.Term`呼叫。|  
|[_ATL_DEBUG_QI](#_atl_debug_qi)|寫入的所有呼叫`QueryInterface`至輸出視窗。|  
|[ATLASSERT](#atlassert)|執行相同的功能[_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) C 執行階段程式庫中找到的巨集。|  
|[ATLENSURE](#atlensure)|執行參數驗證。 呼叫`AtlThrow`視|  
|[ATLTRACENOTIMPL](#atltracenotimpl)|傳送訊息至傾印裝置尚未指定的函式。|  
|[ATLTRACE](http://msdn.microsoft.com/library/c796baa5-e2b9-4814-a27d-d800590b102e)|報告輸出裝置，例如偵錯工具視窗中，根據指定的旗標和層級的警告。 包含的回溯相容性。|  
|[ATLTRACE2](#atltrace2)|報告輸出裝置，例如偵錯工具視窗中，根據指定的旗標和層級的警告。|  
  
##  <a name="a-nameatldebuginterfacesa--atldebuginterfaces"></a><a name="_atl_debug_interfaces"></a>_ATL_DEBUG_INTERFACES  
 定義這個巨集之前包含 ATL 標頭檔來追蹤所有`AddRef`和**版本**呼叫介面上，您的元件以 [輸出] 視窗。  
  
```
#define _ATL_DEBUG_INTERFACES
```  
  
### <a name="remarks"></a>備註  
 追蹤輸出會出現，如下所示︰  
  
 `ATL: QIThunk - 2008         AddRef  :   Object = 0x00d81ba0   Refcount = 1   CBug - IBug`  
  
 每個追蹤的第一個部分一定會`ATL: QIThunk`。 接下來是值，識別特定*介面 thunk*正在使用。 介面 thunk 是用來維護參考計數，並提供此處所使用的追蹤功能的物件。 在每次呼叫建立新的介面 thunk`QueryInterface`除了要求**IUnknown**介面 （在此情況下，相同的 thunk 會將每次傳回遵守 COM 的身分識別的規則）。  
  
 接下來您會看到`AddRef`或**版本**表示所呼叫的方法。 接下來，您會看到值，識別已變更其介面的參考計數的物件。 追蹤的值是**這**物件的指標。  
  
 追蹤參考計數會在之後的 thunk 上的參考計數`AddRef`或**版本**呼叫。 請注意，此參考計數可能不符合物件的參考計數。 每個 thunk 維護它自己的參考計數來幫助您完全符合 COM 的參考計數的規則。  
  
 追蹤資訊的最後一步是物件和受影響的介面名稱`AddRef`或**版本**呼叫。  
  
 伺服器關閉時偵測到遺漏的任何介面和`_Module.Term`呼叫將會記錄如下︰  
  
 `ATL: QIThunk - 2005         LEAK    :   Object = 0x00d81ca0   Refcount = 1   MaxRefCount = 1   CBug - IBug`  
  
 這裡提供都會直接對應到先前的追蹤陳述式中提供的資訊的資訊，因此您可以檢查的參考計數介面 thunk 的整個存留。 此外，取得最大的參考計數的指示該介面 thunk。  
  
> [!NOTE]
> `_ATL_DEBUG_INTERFACES`可在零售組建中。  
  
##  <a name="a-nameatldebugqia--atldebugqi"></a><a name="_atl_debug_qi"></a>_ATL_DEBUG_QI  
 寫入的所有呼叫`QueryInterface`至輸出視窗。  
  
```
#define _ATL_DEBUG_QI
```  
  
### <a name="remarks"></a>備註  
 如果呼叫`QueryInterface`失敗，[輸出] 視窗會顯示︰  
  
 *介面名稱* - `failed`  
  
##  <a name="a-nameatlasserta--atlassert"></a><a name="atlassert"></a>ATLASSERT  
 `ATLASSERT`巨集執行相同的功能[_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) C 執行階段程式庫中找到的巨集。  
  
```
ATLASSERT(booleanExpression);
```  
  
### <a name="parameters"></a>參數  
 `booleanExpression`  
 運算式 （包括指標） 會評估為非零值則為 0。  
  
### <a name="remarks"></a>備註  
 在偵錯組建`ATLASSERT`評估`booleanExpression`結果為 false 時，產生偵錯報表。  

## <a name="requirements"></a>需求  
 **標頭︰** atldef.h  
    
##  <a name="a-nameatlensurea--atlensure"></a><a name="atlensure"></a>ATLENSURE  
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
 這些巨集提供機制來偵測並通知使用者不正確的參數使用。  
  
 巨集呼叫`ATLASSERT`如果條件無法呼叫`AtlThrow`。  
  
 在**ATLENSURE**的情況下，`AtlThrow`稱為 E_FAIL。  
  
 在**ATLENSURE_THROW**的情況下，`AtlThrow`呼叫指定之 HRESULT。  
  
 之間的差異**ATLENSURE**和`ATLASSERT`是**ATLENSURE**版本中的例外狀況以及建置與偵錯組建中擲回。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&108;](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_1.cpp)]  

## <a name="requirements"></a>需求  
 **標頭：** afx.h  

##  <a name="a-nameatltracenotimpla--atltracenotimpl"></a><a name="atltracenotimpl"></a>ATLTRACENOTIMPL  
 在偵錯組建中的 ATL，會將字串"`funcname`未實作 」 至傾印裝置，然後傳回**E_NOTIMPL**。  
  
```
ATLTRACENOTIMPL(funcname);
```  
  
### <a name="parameters"></a>參數  
 `funcname`  
 [in]包含未實作的函式名稱的字串。  
  
### <a name="remarks"></a>備註  
 在發行組建，只會傳回**E_NOTIMPL**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&127;](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_2.cpp)]  
  
## <a name="requirements"></a>需求  
 **標頭︰** atltrace.h 

##  <a name="a-nameatla--atltrace"></a><a name="atl_"></a>ATLTRACE
 報告輸出裝置，例如偵錯工具視窗中，根據指定的旗標和層級的警告。 包含的回溯相容性。  
  
```
ATLTRACE(exp);

ATLTRACE(  
    DWORD category,
    UINT  level,
    LPCSTR lpszFormat, ...);
```  
  
### <a name="parameters"></a>參數  
 `exp`  
 [in]字串和要傳送至 Visual c + + 的 [輸出] 視窗或捕捉這些訊息的任何應用程式變數中。  
  
 `category`  
 [in]事件或在其上的方法來報告的類型。 請參閱備註的分類清單。  
  
 `level`  
 [in]報表的追蹤層級。 請參閱 < 備註 > 以取得詳細資料。  
  
 `lpszFormat`  
 [in]傳送至傾印裝置格式化的字串。  
  
### <a name="remarks"></a>備註  
 請參閱[ATLTRACE2](#atltrace2)的說明**ATLTRACE**。 **ATLTRACE**和`ATLTRACE2`有相同的行為， **ATLTRACE**是為了回溯相容性。  
  
##  <a name="a-nameatltrace2a--atltrace2"></a><a name="atltrace2"></a>ATLTRACE2  
 報告輸出裝置，例如偵錯工具視窗中，根據指定的旗標和層級的警告。  
  
```
ATLTRACE2(exp);

ATLTRACE2(
    DWORD category,
    UINT level,
    LPCSTRlpszFormat,  ...);
```  
  
### <a name="parameters"></a>參數  
 `exp`  
 [in]要傳送至 Visual c + + 的 [輸出] 視窗或應用程式的這些訊息的字串。  
  
 `category`  
 [in]事件或在其上的方法來報告的類型。 請參閱備註的分類清單。  
  
 `level`  
 [in]報表的追蹤層級。 請參閱 < 備註 > 以取得詳細資料。  
  
 `lpszFormat`  
 [in]`printf`-樣式格式字串，用來建立傳送至傾印裝置的字串。  
  
### <a name="remarks"></a>備註  
 簡短形式`ATLTRACE2`寫入 [輸出] 視窗中偵錯工具的字串。 第二種`ATLTRACE2`也會將輸出寫入偵錯工具的 [輸出] 視窗中，但受限於 ATL/MFC 追蹤工具的設定 (請參閱[ATLTraceTool 範例](../../visual-cpp-samples.md))。 例如，如果您設定`level`4 以及層級 0 ATL/MFC 追蹤工具，您將不會看到訊息。 *層級*可以是 0、 1、 2、 3 或 4。 預設值，0，會報告最嚴重的問題。  
  
 `category`參數會列出要設定追蹤旗標。 這些旗標對應到您想要報告的方法的類型。 下表列出您可以使用有效的追蹤旗標`category`參數。  
  
### <a name="atl-trace-flags"></a>ATL 追蹤旗標  
  
|ATL 類別|說明|  
|------------------|-----------------|  
|`atlTraceGeneral`|報告所有 ATL 應用程式。 預設值。|  
|`atlTraceCOM`|報告 COM 方法。|  
|`atlTraceQI`|QueryInterface 呼叫上的報表。|  
|`atlTraceRegistrar`|報告的物件註冊。|  
|`atlTraceRefcount`|變更參考計數的報告。|  
|`atlTraceWindowing`|報告 windows 方法。例如，報告是無效的訊息對應識別碼。|  
|`atlTraceControls`|報表上的控制項。例如，報表的控制項或其視窗終結時。|  
|`atlTraceHosting`|報表裝載訊息。例如，報告將容器中的用戶端啟動時。|  
|`atlTraceDBClient`|OLE DB 消費者樣板; 上的報表例如，當 GetData 失敗的呼叫的輸出可以包含 HRESULT。|  
|`atlTraceDBProvider`|OLE DB 提供者範本; 上的報表例如，報告失敗時建立的資料行。|  
|`atlTraceSnapin`|MMC 嵌入式管理單元的應用程式的報表。|  
|`atlTraceNotImpl`|報告尚未指定函式。|  
|**atlTraceAllocation**|偵錯工具中 atldbgmem.h 的記憶體來列印報表訊息。|  
  
### <a name="mfc-trace-flags"></a>MFC 追蹤旗標  
  
|MFC 類別|描述|  
|------------------|-----------------|  
|**traceAppMsg**|一般用途，MFC 訊息。 一律建議。|  
|**traceDumpContext**|從訊息[CDumpContext](../../mfc/reference/cdumpcontext-class.md)。|  
|**traceWinMsg**|從 MFC 訊息處理程式碼的訊息。|  
|**traceMemory**|從 MFC 的記憶體管理程式碼的訊息。|  
|**traceCmdRouting**|從 MFC 的 Windows 訊息的命令路由的程式碼。|  
|**traceHtml**|從 MFC DHTML 對話方塊支援的訊息。|  
|**traceSocket**|從 MFC 通訊端支援的訊息。|  
|**traceOle**|從 MFC 的 OLE 支援的訊息。|  
|**traceDatabase**|從 MFC 資料庫支援的訊息。|  
|**traceInternet**|從 MFC 的網際網路訊息支援。|  
  
 若要宣告自訂追蹤類別，宣告的全域執行個體`CTraceCategory`類別，如下所示︰  
  
 [!code-cpp[NVC_ATL_Utilities #&109;](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_3.cpp)]  
  
 分類名稱`MY_CATEGORY`在此範例中，是您指定的名稱`category`參數。 第一個參數是類別名稱將會出現在 ATL/MFC 追蹤工具。 第二個參數是預設的追蹤層級。 這個參數是選擇性的並預設追蹤層級為 0。  
  
 若要使用使用者定義的類別︰  
  
 [!code-cpp[NVC_ATL_Utilities #&110;](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_4.cpp)]  
  
 若要指定您想要篩選追蹤訊息，請插入這些巨集的定義之前 Stdafx.h`#include <atlbase.h>`陳述式。  
  
 或者，您可以設定篩選器中的前置處理器指示詞中**屬性頁**對話方塊。 按一下 **前置處理器**索引標籤，然後插入到全域**前置處理器定義**編輯方塊。  
  
 Atlbase.h 包含預設定義`ATLTRACE2`巨集和這些定義將使用 atlbase.h 處理之前，沒有定義這些符號。  
  
 在發行組建`ATLTRACE2`會編譯成`(void) 0`。  
  
 `ATLTRACE2`限制的內容傳送到傾印裝置，不能超過 1023年個字元，以完成格式化後的字串。  
  
 **ATLTRACE**和`ATLTRACE2`有相同的行為， **ATLTRACE**是為了回溯相容性。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Utilities #&111;](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_5.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [巨集](../../atl/reference/atl-macros.md)   
 [偵錯和錯誤報告全域函式](../../atl/reference/debugging-and-error-reporting-global-functions.md)

