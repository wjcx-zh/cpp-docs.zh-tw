---
title: 編譯器選項宏
ms.date: 08/19/2019
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
ms.openlocfilehash: 84083c696ee7bdcbb9538bf587c4aaded7a3932e
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630635"
---
# <a name="compiler-options-macros"></a>編譯器選項宏

這些宏會控制特定編譯器功能。

|||
|-|-|
|[_ATL_ALL_WARNINGS](#_atl_all_warnings)|在從舊版 ATL 轉換的專案中啟用錯誤的符號。|
|[_ATL_APARTMENT_THREADED](#_atl_apartment_threaded)|定義您的一或多個物件是否使用單元執行緒。|
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](#_atl_cstring_explicit_constructors)|讓特定`CString`的函式成為明確的, 以防止任何意外的轉換。|
|[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)|定義此宏以使用C++標準相容語法, 這會在使用非標準語法來初始化成員函式的指標時, 產生 C4867 編譯器錯誤。|
|[_ATL_FREE_THREADED](#_atl_free_threaded)|定義您的一或多個物件是否使用免費或中性的執行緒。|
|[_ATL_MULTI_THREADED](#_atl_multi_threaded)|表示專案將會有標示為「免費」或「中性」之物件的符號。 應該改為使用宏[_ATL_FREE_THREADED](#_atl_free_threaded) 。|
|[_ATL_NO_AUTOMATIC_NAMESPACE](#_atl_no_automatic_namespace)|防止預設使用命名空間做為 ATL 的符號。|
|[_ATL_NO_COM_SUPPORT](#_atl_no_com_support)|防止 COM 相關程式碼使用您的專案進行編譯的符號。|
|[ATL_NO_VTABLE](#atl_no_vtable)|防止 vtable 指標在類別的函式和析構函數中初始化的符號。|
|[ATL_NOINLINE](#atl_noinline)|表示不應內嵌函數的符號。|
|[_ATL_SINGLE_THREADED](#_atl_single_threaded)|定義您的所有物件是否使用單一線程模型。|

##  <a name="_atl_all_warnings"></a>  _ATL_ALL_WARNINGS

在從舊版 ATL 轉換的專案中啟用錯誤的符號。

```
#define _ATL_ALL_WARNINGS
```

### <a name="remarks"></a>備註

在 Visual C++ .net 2002 之前, ATL 已停用許多警告, 並將其停用, 使它們永遠不會顯示在使用者程式碼中。 尤其是：

- C4127 條件運算式是常數

- C4786 ' identifier ': 識別碼已被截斷為偵錯工具資訊中的 ' number ' 個字元

- 使用的 C4201 非標準擴充: 不帶結構/聯集

- C4103 ' filename ': 已使用 #pragma 套件來變更對齊

- C4291 ' 宣告 ': 找不到相符的運算子 delete;如果初始化擲回例外狀況, 則不會釋放記憶體

- C4268 ' identifier ': 使用編譯器產生的預設函式初始化的 ' const ' 靜態/全域資料會以零填滿物件

- C4702 無法連線的程式碼

在先前版本中轉換的專案中, 這些警告仍然會由程式庫標頭停用。

藉由在包含程式庫標頭之前, 將下面這一行新增至*pch* (Visual Studio 2017 和更早版本) 檔案中的*stdafx.h* , 即可變更此行為。

[!code-cpp[NVC_ATL_Utilities#97](../../atl/codesnippet/cpp/compiler-options-macros_1.h)]

如果加入`#define`這項功能, ATL 標頭會小心保留這些警告的狀態, 讓它們不會全域停用 (或者, 如果使用者明確停用個別的警告, 則不會加以啟用)。

根據預設, 新`#define`的專案在*pch*中會有此設定 (Visual Studio 2017 和更早版本中的*stdafx.h* )。

##  <a name="_atl_apartment_threaded"></a>_ATL_APARTMENT_THREADED

定義您的一或多個物件是否使用單元執行緒。

```
_ATL_APARTMENT_THREADED
```

### <a name="remarks"></a>備註

指定單元執行緒。 如需 ATL 物件可用之執行緒模型的描述, 請參閱為其他執行緒選項[指定專案的執行緒模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)和[選項, 以及 Atl 簡單物件 Wizard](../../atl/reference/options-atl-simple-object-wizard.md)

##  <a name="_atl_cstring_explicit_constructors"></a>_ATL_CSTRING_EXPLICIT_CONSTRUCTORS

讓特定`CString`的函式成為明確的, 以防止任何意外的轉換。

```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```

### <a name="remarks"></a>備註

定義此函式時, 採用單一參數的所有 CString 函式都會以明確的關鍵字進行編譯, 這可防止輸入引數的隱含轉換。 例如, 這表示當定義 _UNICODE 時, 如果您嘗試使用 char * 字串做為 CString 函式引數, 則會產生編譯器錯誤。 當您需要防止在窄和寬字元串類型之間進行隱含轉換時, 請使用此宏。

藉由在所有的「函數位符串」引數上使用 _T 宏, 您可以定義 _ATL_CSTRING_EXPLICIT_CONSTRUCTORS 並避免編譯錯誤, 不論是否已定義 _UNICODE。

##  <a name="_atl_enable_ptm_warning"></a>  _ATL_ENABLE_PTM_WARNING

定義此宏, 以強制將 ANSI C++標準相容語法用於成員函式的指標。 使用此宏會導致在使用非標準語法來初始化成員函式的指標時, 產生 C4867 編譯器錯誤。

```
#define _ATL_ENABLE_PTM_WARNING
```

### <a name="remarks"></a>備註

ATL 和 MFC 程式庫已變更, 以符合 Microsoft C++編譯器改良的標準C++合規性。 根據 ANSI C++標準, 類別成員函式的指標語法應該是`&CMyClass::MyFunc`。

未定義[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)時 (預設案例), ATL/MFC 會停用宏對應中的 C4867 錯誤 (特別是訊息對應), 因此在舊版中建立的程式碼可以繼續如之前一樣建立。 如果您定義 **_ATL_ENABLE_PTM_WARNING**, 您的程式碼C++應該符合標準。

不過, 非標準格式已被取代。 您必須將現有的程式碼C++移至標準相容語法。 例如，下列程式碼：

[!code-cpp[NVC_MFCListView#14](../../atl/reference/codesnippet/cpp/compiler-options-macros_2.cpp)]

應變更為:

[!code-cpp[NVC_MFCListView#11](../../atl/reference/codesnippet/cpp/compiler-options-macros_3.cpp)]

針對 [對應宏], 新增 & ' & ' 字元。 您不應該在程式碼中再次新增該字元。

##  <a name="_atl_free_threaded"></a>_ATL_FREE_THREADED

定義您的一或多個物件是否使用免費或中性的執行緒。

```
_ATL_FREE_THREADED
```

### <a name="remarks"></a>備註

指定自由執行緒。 自由執行緒相當於多執行緒單元模型。 如需 ATL 物件可用之執行緒模型的描述, 請參閱為其他執行緒選項[指定專案的執行緒模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)和[選項, 以及 Atl 簡單物件 Wizard](../../atl/reference/options-atl-simple-object-wizard.md)

##  <a name="_atl_multi_threaded"></a>_ATL_MULTI_THREADED

表示專案將會有標示為「免費」或「中性」之物件的符號。

```
_ATL_MULTI_THREADED
```

### <a name="remarks"></a>備註

如果定義了這個符號, ATL 將會提取程式碼, 以正確同步處理全域資料的存取。 新的程式碼應該改用對等的宏[_ATL_FREE_THREADED](#_atl_free_threaded) 。

##  <a name="_atl_no_automatic_namespace"></a>_ATL_NO_AUTOMATIC_NAMESPACE

防止預設使用命名空間做為 ATL 的符號。

```
_ATL_NO_AUTOMATIC_NAMESPACE
```

### <a name="remarks"></a>備註

如果未定義此符號, 包括 atlbase.h 預設會**使用命名空間 ATL**來執行, 這可能會導致命名衝突。 若要避免這個情況, 請定義這個符號。

##  <a name="_atl_no_com_support"></a>_ATL_NO_COM_SUPPORT

防止 COM 相關程式碼使用您的專案進行編譯的符號。

```
_ATL_NO_COM_SUPPORT
```

##  <a name="atl_no_vtable"></a>  ATL_NO_VTABLE

防止 vtable 指標在類別的函式和析構函數中初始化的符號。

```
ATL_NO_VTABLE
```

### <a name="remarks"></a>備註

如果無法在類別的「函式」和「析構函數」中初始化 vtable 指標, 則連結器可以排除 vtable 及其指向的所有函數。 展開至 **__declspec (novtable)** 。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#53](../../atl/codesnippet/cpp/compiler-options-macros_4.h)]

##  <a name="atl_noinline"></a>  ATL_NOINLINE

表示不應內嵌函式的符號。

```
    ATL_NOINLINE inline
    myfunction()
    {
    ...
    }
```

### <a name="parameters"></a>參數

*myfunction*<br/>
不應該內嵌的函式。

### <a name="remarks"></a>備註

如果您想要確保編譯器不會內嵌函式, 則請使用這個符號, 即使它必須宣告為內嵌, 使其可以放在標頭檔中也一樣。 展開至 **__declspec (noinline)** 。

##  <a name="_atl_single_threaded"></a>_ATL_SINGLE_THREADED

定義您的所有物件是否使用單一線程模型

```
_ATL_SINGLE_THREADED
```

### <a name="remarks"></a>備註

指定物件一律在主要 COM 執行緒中執行。 如需 ATL 物件可用之執行緒模型的描述, 請參閱為其他執行緒選項[指定專案的執行緒模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)和[選項, 以及 Atl 簡單物件 Wizard](../../atl/reference/options-atl-simple-object-wizard.md)

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
