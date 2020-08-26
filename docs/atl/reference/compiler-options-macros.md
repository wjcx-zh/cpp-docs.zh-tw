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
ms.openlocfilehash: 90b80aaa34456677f2d7c2dd5717ae6837f4523f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833565"
---
# <a name="compiler-options-macros"></a>編譯器選項宏

這些宏會控制特定的編譯器功能。

|巨集|描述|
|-|-|
|[_ATL_ALL_WARNINGS](#_atl_all_warnings)|在從舊版 ATL 轉換的專案中啟用錯誤的符號。|
|[_ATL_APARTMENT_THREADED](#_atl_apartment_threaded)|定義一個或多個物件是否使用單元執行緒。|
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](#_atl_cstring_explicit_constructors)|讓特定 `CString` 的函式明確，防止任何意外的轉換。|
|[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)|定義這個宏，以使用 c + + 標準相容的語法，這會在使用非標準語法來初始化成員函式的指標時，產生 C4867 編譯器錯誤。|
|[_ATL_FREE_THREADED](#_atl_free_threaded)|定義您的一或多個物件是否使用免費或中立的執行緒。|
|[_ATL_MULTI_THREADED](#_atl_multi_threaded)|符號，表示專案會有標示為 [免費] 或 [中性] 的物件。 應改為使用宏 [_ATL_FREE_THREADED](#_atl_free_threaded) 。|
|[_ATL_NO_AUTOMATIC_NAMESPACE](#_atl_no_automatic_namespace)|防止預設使用命名空間作為 ATL 的符號。|
|[_ATL_NO_COM_SUPPORT](#_atl_no_com_support)|防止 COM 相關程式碼與您的專案一起編譯的符號。|
|[ATL_NO_VTABLE](#atl_no_vtable)|防止 vtable 指標在類別的函式和函式中初始化的符號。|
|[ATL_NOINLINE](#atl_noinline)|表示不應該內嵌函式的符號。|
|[_ATL_SINGLE_THREADED](#_atl_single_threaded)|定義是否所有的物件都使用單一線程模型。|

## <a name="_atl_all_warnings"></a><a name="_atl_all_warnings"></a> _ATL_ALL_WARNINGS

在從舊版 ATL 轉換的專案中啟用錯誤的符號。

```
#define _ATL_ALL_WARNINGS
```

### <a name="remarks"></a>備註

在 Visual C++ .NET 2002 之前，ATL 已停用許多警告，並將其停用，使其不會顯示在使用者程式碼中。 具體來說：

- C4127 條件運算式是常數

- C4786 ' identifier '：偵測資訊中的識別碼已被截斷為 ' number ' 個字元

- 使用了 C4201 非標準的擴充：無的結構/等位

- C4103 ' filename '：已使用 #pragma 套件來變更對齊

- C4291 ' 宣告 '：找不到相符的運算子 delete;如果初始化擲回例外狀況，則不會釋放記憶體

- C4268 ' identifier '：使用編譯器產生的預設值函式初始化的 ' const ' 靜態/全域資料會將物件填入零

- C4702 無法連線的程式碼

在從舊版轉換的專案中，程式庫標頭仍會停用這些警告。

藉由將下列程式程式碼加入至 *pch. h* (*stdafx.h* ，在包含程式庫標頭之前 Visual Studio 2017 和先前的) 檔中，可以變更此行為。

[!code-cpp[NVC_ATL_Utilities#97](../../atl/codesnippet/cpp/compiler-options-macros_1.h)]

如果加入此專案 `#define` ，ATL 標頭會謹慎地保留這些警告的狀態，使它們不會全域停用 (或使用者明確停用個別警告，而不是) 啟用它們。

`#define`依預設，新的專案在*pch. h*中 (*stdafx.h* ，Visual Studio 2017 及更早的) 。

## <a name="_atl_apartment_threaded"></a><a name="_atl_apartment_threaded"></a> _ATL_APARTMENT_THREADED

定義一個或多個物件是否使用單元執行緒。

```
_ATL_APARTMENT_THREADED
```

### <a name="remarks"></a>備註

指定單元執行緒。 如需 ATL 物件可用之執行緒模型的描述，請參閱為其他執行緒選項 [指定專案的執行緒模型](../../atl/specifying-the-threading-model-for-a-project-atl.md) ，以及指定 Atl [Simple Object Wizard 的選項](../../atl/reference/options-atl-simple-object-wizard.md) 。

## <a name="_atl_cstring_explicit_constructors"></a><a name="_atl_cstring_explicit_constructors"></a> _ATL_CSTRING_EXPLICIT_CONSTRUCTORS

讓特定 `CString` 的函式明確，防止任何意外的轉換。

```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```

### <a name="remarks"></a>備註

定義此函式時，採用單一參數的所有 CString 函式都會使用明確關鍵字進行編譯，以防止輸入引數的隱含轉換。 這表示，當定義 _UNICODE 時，如果您嘗試使用 char * 字串作為 CString 的函式引數，則會產生編譯器錯誤。 在您需要防止在窄和寬字元串類型之間隱含轉換的情況下，請使用這個宏。

藉由在所有的函式字串引數上使用 _T 宏，您可以定義 _ATL_CSTRING_EXPLICIT_CONSTRUCTORS 並避免編譯錯誤，不論是否已定義 _UNICODE。

## <a name="_atl_enable_ptm_warning"></a><a name="_atl_enable_ptm_warning"></a> _ATL_ENABLE_PTM_WARNING

定義這個宏以強制將 ANSI c + + 標準相容的語法用於成員函式的指標。 使用這個宏會在使用非標準語法來初始化成員函式的指標時，產生 C4867 編譯器錯誤。

```
#define _ATL_ENABLE_PTM_WARNING
```

### <a name="remarks"></a>備註

ATL 和 MFC 程式庫已變更，以符合 Microsoft c + + 編譯器改善的標準 c + + 相容性。 根據 ANSI c + + 標準，類別成員函式指標的語法應該是 `&CMyClass::MyFunc` 。

當 [_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning) 未定義 (預設案例) 時，ATL/MFC 會在宏對應中停用 C4867 錯誤， (特別是訊息對應) 如此一來，在舊版中建立的程式碼仍可以繼續建立。 如果您定義 **_ATL_ENABLE_PTM_WARNING**，您的程式碼應該符合 c + + 標準。

不過，非標準的表單已被取代。 您必須將現有的程式碼移至符合 c + + 標準的語法。 例如，下列程式碼：

[!code-cpp[NVC_MFCListView#14](../../atl/reference/codesnippet/cpp/compiler-options-macros_2.cpp)]

應變更為：

[!code-cpp[NVC_MFCListView#11](../../atl/reference/codesnippet/cpp/compiler-options-macros_3.cpp)]

針對對應宏，加入 & 符號 ' & ' 字元。 您不應該在程式碼中再次新增該字元。

## <a name="_atl_free_threaded"></a><a name="_atl_free_threaded"></a> _ATL_FREE_THREADED

定義您的一或多個物件是否使用免費或中立的執行緒。

```
_ATL_FREE_THREADED
```

### <a name="remarks"></a>備註

指定自由執行緒。 自由執行緒相當於多執行緒的單元模型。 如需 ATL 物件可用之執行緒模型的描述，請參閱為其他執行緒選項 [指定專案的執行緒模型](../../atl/specifying-the-threading-model-for-a-project-atl.md) ，以及指定 Atl [Simple Object Wizard 的選項](../../atl/reference/options-atl-simple-object-wizard.md) 。

## <a name="_atl_multi_threaded"></a><a name="_atl_multi_threaded"></a> _ATL_MULTI_THREADED

符號，表示專案會有標示為 [免費] 或 [中性] 的物件。

```
_ATL_MULTI_THREADED
```

### <a name="remarks"></a>備註

如果已定義此符號，ATL 將會提取程式碼，以正確地同步處理全域資料的存取。 新的程式碼應該改用相等的宏 [_ATL_FREE_THREADED](#_atl_free_threaded) 。

## <a name="_atl_no_automatic_namespace"></a><a name="_atl_no_automatic_namespace"></a> _ATL_NO_AUTOMATIC_NAMESPACE

防止預設使用命名空間作為 ATL 的符號。

```
_ATL_NO_AUTOMATIC_NAMESPACE
```

### <a name="remarks"></a>備註

如果未定義此符號，包含 atlbase.h 預設會 **使用命名空間 ATL** 執行，這可能會導致命名衝突。 若要避免這種情況，請定義此符號。

## <a name="_atl_no_com_support"></a><a name="_atl_no_com_support"></a> _ATL_NO_COM_SUPPORT

防止 COM 相關程式碼與您的專案一起編譯的符號。

```
_ATL_NO_COM_SUPPORT
```

## <a name="atl_no_vtable"></a><a name="atl_no_vtable"></a> ATL_NO_VTABLE

防止 vtable 指標在類別的函式和函式中初始化的符號。

```
ATL_NO_VTABLE
```

### <a name="remarks"></a>備註

如果無法在類別的函式和函式中初始化 vtable 指標，連結器可以排除 vtable 以及它所指向的所有函式。 展開至 **`__declspec(novtable)`** 。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#53](../../atl/codesnippet/cpp/compiler-options-macros_4.h)]

## <a name="atl_noinline"></a><a name="atl_noinline"></a> ATL_NOINLINE

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
不應內嵌的函式。

### <a name="remarks"></a>備註

如果您想要確保編譯器不會內嵌函式，即使它必須宣告為內嵌，以便將它放在標頭檔中，也可以使用此符號。 展開至 **`__declspec(noinline)`** 。

## <a name="_atl_single_threaded"></a><a name="_atl_single_threaded"></a> _ATL_SINGLE_THREADED

定義是否所有物件都使用單一線程模型

```
_ATL_SINGLE_THREADED
```

### <a name="remarks"></a>備註

指定物件一律在主要 COM 執行緒中執行。 如需 ATL 物件可用之執行緒模型的描述，請參閱為其他執行緒選項 [指定專案的執行緒模型](../../atl/specifying-the-threading-model-for-a-project-atl.md) ，以及指定 Atl [Simple Object Wizard 的選項](../../atl/reference/options-atl-simple-object-wizard.md) 。

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
