---
title: "編譯器選項巨集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
f1_keywords:
- _ATL_ALL_WARNINGS
- _ATL_APARTMENT_THREADED
- '_ATL_CSTRING_EXPLICIT_CONSTRUCTORS '
- _ATL_ENABLE_PTM_WARNING
- _ATL_FREE_THREADED
- _ATL_MULTI_THREADED
- _ATL_NO_AUTOMATIC_NAMESPACE
- _ATL_NO_COM_SUPPORT
- ATL_NO_VTABLE
- ATL_NOINLINE
- _ATL_SINGLE_THREADED
helpviewer_keywords: compiler options, macros
ms.assetid: a869adc6-b3de-4299-b040-9ae20b45f82c
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f48abc864133849353aeccf82ea3eb9aab1edb5a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-options-macros"></a>編譯器選項巨集
這些巨集來控制特定的編譯器功能。  
  
|||  
|-|-|  
|[_ATL_ALL_WARNINGS](#_atl_all_warnings)|從舊版的 ATL 轉換可讓專案發生錯誤的符號|  
|[_ATL_APARTMENT_THREADED](#_atl_apartment_threaded)|如果一或多個物件使用 apartment 執行緒，定義。|  
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](#_atl_cstring_explicit_constructors)|讓特定`CString`明確，防止任何意外的轉換建構函式。|  
|[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)|若要使用 c + + 標準相容語法時，會在非標準的語法用來初始化的成員函式指標時，產生 C4867 編譯器錯誤定義此巨集。|  
|[_ATL_FREE_THREADED](#_atl_free_threaded)|如果一或多個物件會使用執行緒可用或中性，定義。|  
|[_ATL_MULTI_THREADED](#_atl_multi_threaded)|一個符號，指出專案將會有標示為兩者，免費或中性的物件。 巨集[_ATL_FREE_THREADED](#_atl_free_threaded)應該改用。|  
|[_ATL_NO_AUTOMATIC_NAMESPACE](#_atl_no_automatic_namespace)|如此可防止預設使用的命名空間做 ATL 符號|  
|[_ATL_NO_COM_SUPPORT](#_atl_no_com_support)|符號以防止 COM 相關的程式碼要編譯您的專案。|  
|[ATL_NO_VTABLE](#atl_no_vtable)|在類別的建構函式和解構函式中初始化時，防止 vtable 指標符號。|  
|[ATL_NOINLINE](#atl_noinline)|一個符號，指出函式不應內嵌。|  
|[_ATL_SINGLE_THREADED](#_atl_single_threaded)|如果所有物件都使用單一執行緒模型，定義。|  
  
##  <a name="_atl_all_warnings"></a>_ATL_ALL_WARNINGS  
 從舊版的 ATL 轉換可讓專案發生錯誤的符號  
  
```
#define _ATL_ALL_WARNINGS
```  
  
### <a name="remarks"></a>備註  
 Visual c + +.NET 2002，ATL 停用警告大量前後保留停用，讓它們永遠不會顯示使用者程式碼中。 尤其是：  
  
-   C4127 條件運算式是常數  
  
-   C4786 'identifier': 識別項被截斷成 'number' 個字元，在偵錯資訊  
  
-   C4201 使用非標準擴充： 沒有名稱的結構/等位  
  
-   C4103 'filename': 用來變更對齊方式的 #pragma 組件  
  
-   C4291 'declaration': 沒有相符的 delete 運算子找到。如果初始設定擲回例外狀況，將不會釋放記憶體  
  
-   C4268 'identifier': 'const' 編譯器產生預設建構函式初始化的靜態/全域資料填滿零的物件  
  
-   C4702 無法連線到程式碼  
  
 在專案從舊版轉換中，這些警告仍然會由程式庫標頭停用。  
  
 Stdafx.h 檔案下列行加入包含程式庫標頭之前，您可以變更此行為。  
  
 [!code-cpp[NVC_ATL_Utilities#97](../../atl/codesnippet/cpp/compiler-options-macros_1.h)]  
  
 如果這個`#define`加入，ATL 標頭會保留這些警告的狀態，使它們不會停用全域 （或使用者明確地停用個別的警告，不是，讓它們），請小心。  
  
 新的專案具有這`#define`stdafx.h 中預設設定。  
  
##  <a name="_atl_apartment_threaded"></a>_ATL_APARTMENT_THREADED  
 如果一或多個物件使用 apartment 執行緒，定義。  
  
```
_ATL_APARTMENT_THREADED
```  
  
### <a name="remarks"></a>備註  
 指定 apartment 執行緒。 請參閱[指定專案的執行緒模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)其他執行緒的選項，和[選項，ATL 簡單物件精靈](../../atl/reference/options-atl-simple-object-wizard.md)的描述就會忽略執行緒模型 ATL 物件可用的。  
  
##  <a name="_atl_cstring_explicit_constructors"></a>_ATL_CSTRING_EXPLICIT_CONSTRUCTORS  
 讓特定`CString`明確，防止任何意外的轉換建構函式。  
  
```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```  
  
### <a name="remarks"></a>備註  
 這定義時，所有 CString 建構函式會接受一個參數會都編譯以明確的關鍵字，可防止輸入引數的隱含轉換。 這表示，例如，定義 _UNICODE 時，如果您嘗試使用 char * 字串做為 CString 建構函式引數，將會產生編譯器錯誤。 您要防止窄和寬字串類型之間的隱含轉換的情況下使用這個巨集。  
  
 藉由使用所有的建構函式的字串引數的 _T 巨集，您可以定義 _ATL_CSTRING_EXPLICIT_CONSTRUCTORS，及避免編譯錯誤，不論是否 _UNICODE 已定義。  
  
##  <a name="_atl_enable_ptm_warning"></a>_ATL_ENABLE_PTM_WARNING  
 定義此巨集，以便強制將 ANSI c + + 符合標準的語法用於成員函式的指標。 使用這個巨集，將導致 C4867 編譯器錯誤，以初始化成員函式的指標使用非標準語法時產生。  
  
```
#define _ATL_ENABLE_PTM_WARNING
```  
  
### <a name="remarks"></a>備註  
 要比對 Visual c + + 編譯器的改進標準 c + + 相容性已變更的 ATL 和 MFC 程式庫。 類別成員函式指標的語法應該是根據 ANSI c + + 標準， `&CMyClass::MyFunc`。  
  
 當[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)未定義 （預設情況），ATL/MFC 會停用 C4867 中的錯誤 （值得注意的是訊息對應） 的巨集對應，讓較早版本中所建立的程式碼可以繼續如常建置。 如果您定義**_ATL_ENABLE_PTM_WARNING**，您的程式碼應該是 c + + 標準相容。  
  
 不過，非標準的表單已被取代，所以您要將現有的程式碼移至 c + + 標準相容的語法。 例如，下列步驟：  
  
 [!code-cpp[NVC_MFCListView#14](../../atl/reference/codesnippet/cpp/compiler-options-macros_2.cpp)]  
  
 應該變更為：  
  
 [!code-cpp[NVC_MFCListView#11](../../atl/reference/codesnippet/cpp/compiler-options-macros_3.cpp)]  
  
 請注意，加入 '&' 字元的對應巨集，您應該不將它加入一次程式碼中。  
  
##  <a name="_atl_free_threaded"></a>_ATL_FREE_THREADED  
 如果一或多個物件會使用執行緒可用或中性，定義。  
  
```
_ATL_FREE_THREADED
```  
  
### <a name="remarks"></a>備註  
 指定無限制執行緒。 無限制執行緒相當於多執行緒 apartment 模型。 請參閱[指定專案的執行緒模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)其他執行緒的選項，和[選項，ATL 簡單物件精靈](../../atl/reference/options-atl-simple-object-wizard.md)的描述就會忽略執行緒模型 ATL 物件可用的。  
  
##  <a name="_atl_multi_threaded"></a>_ATL_MULTI_THREADED  
 一個符號，指出專案將會有標示為兩者，免費或中性的物件。  
  
```
_ATL_MULTI_THREADED
```  
  
### <a name="remarks"></a>備註  
 如果已定義這個符號，ATL 會提取將會正確地同步處理存取具備全域資料的程式碼中。 新的程式碼應該使用對等的巨集[_ATL_FREE_THREADED](#_atl_free_threaded)改為。  
  
##  <a name="_atl_no_automatic_namespace"></a>_ATL_NO_AUTOMATIC_NAMESPACE  
 如此可防止預設使用的命名空間做 ATL 符號  
  
```
_ATL_NO_AUTOMATIC_NAMESPACE
```  
  
### <a name="remarks"></a>備註  
 如果未定義這個符號，將會執行包括 atlbase.h**使用命名空間 ATL**根據預設，這可能導致名稱衝突。 若要防止這個情況，定義這個符號。  
  
##  <a name="_atl_no_com_support"></a>_ATL_NO_COM_SUPPORT  
 符號以防止 COM 相關的程式碼要編譯您的專案。  
  
```
_ATL_NO_COM_SUPPORT```  
  
##  <a name="atl_no_vtable"></a>  ATL_NO_VTABLE  
 A symbol that prevents the vtable pointer from being initialized in the class's constructor and destructor.  
  
```
ATL_NO_VTABLE
```  
  
### Remarks  
 If the vtable pointer is prevented from being initialized in the class's constructor and destructor, the linker can eliminate the vtable and all of the functions to which it points. Expands to **__declspec(novtable)**.  
  
### Example  
 [!code-cpp[NVC_ATL_COM#53](../../atl/codesnippet/cpp/compiler-options-macros_4.h)]  
  
##  <a name="atl_noinline"></a>  ATL_NOINLINE  
 A symbol that indicates a function should not be inlined.  
  
```
    ATL_NOINLINE inline
    myfunction
 { ... }
```  
  
### Parameters  
 *myfunction*  
 The function that should not be inlined.  
  
### Remarks  
 Use this symbol if you want to ensure a function does not get inlined by the compiler, even though it must be declared as inline so that it can be placed in a header file. Expands to **__declspec(noinline)**.  
  
##  <a name="_atl_single_threaded"></a>  _ATL_SINGLE_THREADED  
 Define if all of your objects use the single threading model  
  
```
_ATL_SINGLE_THREADED
```  
  
### Remarks  
 Specifies that the object always runs in the primary COM thread. See [Specifying the Project's Threading Model](../../atl/specifying-the-threading-model-for-a-project-atl.md) for other threading options, and [Options, ATL Simple Object Wizard](../../atl/reference/options-atl-simple-object-wizard.md) for a description of the threading models available for an ATL object.  
  
## See Also  
 [Macros](../../atl/reference/atl-macros.md)
