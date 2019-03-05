---
title: 編譯器選項巨集
ms.date: 11/04/2016
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
helpviewer_keywords:
- compiler options, macros
ms.assetid: a869adc6-b3de-4299-b040-9ae20b45f82c
ms.openlocfilehash: 79b1cabc0304e905012db5f6dd73ed71073c0c1e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57258472"
---
# <a name="compiler-options-macros"></a>編譯器選項巨集

這些巨集來控制特定的編譯器功能。

|||
|-|-|
|[_ATL_ALL_WARNINGS](#_atl_all_warnings)|從舊版的 ATL 轉換的符號可在專案中的錯誤|
|[_ATL_APARTMENT_THREADED](#_atl_apartment_threaded)|定義一或多個物件使用 apartment 執行緒。|
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](#_atl_cstring_explicit_constructors)|確保`CString`明確，防止任何非預期的轉換建構函式。|
|[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)|若要使用 c + + 標準相容語法時，會產生 C4867 編譯器錯誤時的非標準的語法用來初始化成員函式的指標，定義此巨集。|
|[_ATL_FREE_THREADED](#_atl_free_threaded)|如果一或多個物件使用免費或中性執行緒，定義。|
|[_ATL_MULTI_THREADED](#_atl_multi_threaded)|表示專案的符號必須標示為兩者，免費 」 或 「 中性的物件。 巨集會[_ATL_FREE_THREADED](#_atl_free_threaded)應改為使用。|
|[_ATL_NO_AUTOMATIC_NAMESPACE](#_atl_no_automatic_namespace)|這是為了避免預設使用的命名空間作為 ATL 符號|
|[_ATL_NO_COM_SUPPORT](#_atl_no_com_support)|這樣可防止 COM 相關的程式碼正在您的專案編譯的符號。|
|[ATL_NO_VTABLE](#atl_no_vtable)|在類別的建構函式和解構函式中初始化時，防止 vtable 指標的符號。|
|[ATL_NOINLINE](#atl_noinline)|一個符號，指出函式不能內嵌。|
|[_ATL_SINGLE_THREADED](#_atl_single_threaded)|如果所有物件都使用單一執行緒模型，定義。|

##  <a name="_atl_all_warnings"></a>  _ATL_ALL_WARNINGS

從舊版的 ATL 轉換的符號可在專案中的錯誤

```
#define _ATL_ALL_WARNINGS
```

### <a name="remarks"></a>備註

Visual c + +.NET 2002，ATL 停用警告大量前後離開停用，讓它們永遠不會顯示使用者程式碼中。 尤其是：

- C4127 條件運算式是常數

- C4786 'identifier': 識別項被截斷成 'number' 個字元，在偵錯資訊

- C4201 使用非標準擴充： 沒有名稱的結構/等位

- C4103 'filename': 對齊方式變更時，用以 #pragma 組件

- C4291 'declaration': 沒有相符的 delete 運算子，如果初始設定擲回例外狀況，將不會釋放記憶體

- C4268 'identifier': 'const' 編譯器產生預設建構函式初始化的靜態/全域資料填滿零的物件

- C4702 無法連線到程式碼

在專案從舊版轉換中，這些警告會仍然停用的程式庫標頭。

加入 stdafx.h 檔案的下面這一行加入程式庫標頭之前，您可以變更此行為。

[!code-cpp[NVC_ATL_Utilities#97](../../atl/codesnippet/cpp/compiler-options-macros_1.h)]

如果這個`#define`加入，ATL 標頭會謹慎地保留這些警告的狀態，使它們不會停用全域 （或如果使用者明確停用個別的警告，不會，讓它們）。

新的專案具有這`#define`stdafx.h 中預設設定。

##  <a name="_atl_apartment_threaded"></a>  _ATL_APARTMENT_THREADED

定義一或多個物件使用 apartment 執行緒。

```
_ATL_APARTMENT_THREADED
```

### <a name="remarks"></a>備註

指定 apartment 執行緒。 請參閱[指定專案的執行緒模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)其他執行緒的選項，並[選項，ATL 簡單物件精靈](../../atl/reference/options-atl-simple-object-wizard.md)的執行緒說明模型 ATL 物件可用的。

##  <a name="_atl_cstring_explicit_constructors"></a>  _ATL_CSTRING_EXPLICIT_CONSTRUCTORS

確保`CString`明確，防止任何非預期的轉換建構函式。

```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```

### <a name="remarks"></a>備註

這定義時，所有 CString 建構函式會採用單一參數，會都編譯使用 explicit 關鍵字，它會禁止隱含轉換的輸入引數。 這表示，例如當已定義 _UNICODE，如果您嘗試使用 char * 字串做為 CString 建構函式引數，將會產生編譯器錯誤。 在您要防止窄和寬字串類型之間的隱含轉換的情況下使用這個巨集。

藉由使用所有的建構函式的字串引數的 _T 巨集，您可以定義 _ATL_CSTRING_EXPLICIT_CONSTRUCTORS，並避免編譯錯誤，不論是否已定義 _UNICODE。

##  <a name="_atl_enable_ptm_warning"></a>  _ATL_ENABLE_PTM_WARNING

定義此巨集，以便強制將 ANSI c + + 標準相容的語法用於成員函式的指標。 使用這個巨集，將導致 C4867 編譯器錯誤，會產生非標準的語法用來初始化的成員函式指標時。

```
#define _ATL_ENABLE_PTM_WARNING
```

### <a name="remarks"></a>備註

ATL 和 MFC 程式庫已變更為符合 Visual c + + 編譯器的改進標準 c + + 相容性。 類別成員函式指標的語法應該是根據 ANSI c + + 標準， `&CMyClass::MyFunc`。

當[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)未定義 （預設情況），ATL/MFC 會停用 C4867 中的錯誤訊息 （值得注意的是訊息對應） 的巨集對應，讓較早版本中所建立的程式碼可以繼續建置和以前一樣。 如果您定義 **_ATL_ENABLE_PTM_WARNING**，您的程式碼應該是符合規範的 c + + 標準。

不過，非標準格式已被取代，因此您需要將現有的程式碼移至 c + + 標準相容的語法。 例如，下列步驟：

[!code-cpp[NVC_MFCListView#14](../../atl/reference/codesnippet/cpp/compiler-options-macros_2.cpp)]

應變更為：

[!code-cpp[NVC_MFCListView#11](../../atl/reference/codesnippet/cpp/compiler-options-macros_3.cpp)]

請注意，加上 '&' 字元的對應巨集，您應該再次新增您的程式碼中。

##  <a name="_atl_free_threaded"></a>  _ATL_FREE_THREADED

如果一或多個物件使用免費或中性執行緒，定義。

```
_ATL_FREE_THREADED
```

### <a name="remarks"></a>備註

指定無限制執行緒。 無限制執行緒相當於多執行緒 apartment 模型。 請參閱[指定專案的執行緒模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)其他執行緒的選項，並[選項，ATL 簡單物件精靈](../../atl/reference/options-atl-simple-object-wizard.md)的執行緒說明模型 ATL 物件可用的。

##  <a name="_atl_multi_threaded"></a>  _ATL_MULTI_THREADED

表示專案的符號必須標示為兩者，免費 」 或 「 中性的物件。

```
_ATL_MULTI_THREADED
```

### <a name="remarks"></a>備註

如果定義這個符號，則會正確地同步處理對全域資料的存取權的程式碼會提取 ATL。 新的程式碼應該使用對等的巨集[_ATL_FREE_THREADED](#_atl_free_threaded)改。

##  <a name="_atl_no_automatic_namespace"></a>  _ATL_NO_AUTOMATIC_NAMESPACE

這是為了避免預設使用的命名空間作為 ATL 符號

```
_ATL_NO_AUTOMATIC_NAMESPACE
```

### <a name="remarks"></a>備註

如果未定義這個符號，將會執行包括 atlbase.h**使用 ATL 的命名空間**根據預設，這可能會導致命名衝突。 若要避免這個問題，定義這個符號。

##  <a name="_atl_no_com_support"></a>  _ATL_NO_COM_SUPPORT

這樣可防止 COM 相關的程式碼正在您的專案編譯的符號。

```
_ATL_NO_COM_SUPPORT
```

##  <a name="atl_no_vtable"></a>  ATL_NO_VTABLE

在類別的建構函式和解構函式中初始化時，防止 vtable 指標的符號。

```
ATL_NO_VTABLE
```

### <a name="remarks"></a>備註

如果 vtable 指標會防止在類別的建構函式和解構函式中初始化，連結器可以消除 vtable 和所有它所指向的函式。 若要展開 **__declspec （novtable)**。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#53](../../atl/codesnippet/cpp/compiler-options-macros_4.h)]

##  <a name="atl_noinline"></a>  ATL_NOINLINE

一個符號，指出函式不能內嵌。

```
    ATL_NOINLINE inline
    myfunction()
    {
    ...
    }
```

### <a name="parameters"></a>參數

*myfunction*<br/>
不應該由內嵌的函式。

### <a name="remarks"></a>備註

如果您想要確保函式並不會內嵌在編譯器中，即使它必須宣告為內嵌，讓它可以放在標頭檔，請使用這個符號。 若要展開 **__declspec （noinline)**。

##  <a name="_atl_single_threaded"></a>  _ATL_SINGLE_THREADED

如果所有物件都使用單一執行緒模型，定義

```
_ATL_SINGLE_THREADED
```

### <a name="remarks"></a>備註

指定的物件一律在主要 COM 執行緒執行。 請參閱[指定專案的執行緒模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)其他執行緒的選項，並[選項，ATL 簡單物件精靈](../../atl/reference/options-atl-simple-object-wizard.md)的執行緒說明模型 ATL 物件可用的。

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
