---
title: 編譯器選項巨集
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
ms.openlocfilehash: 702324c3300ff23bb60113529a681e3b8fa99354
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331626"
---
# <a name="compiler-options-macros"></a>編譯器選項巨集

這些宏控制特定的編譯器功能。

|||
|-|-|
|[_ATL_ALL_WARNINGS](#_atl_all_warnings)|啟用從早期版本的 ATL 轉換的專案中的錯誤的符號。|
|[_ATL_APARTMENT_THREADED](#_atl_apartment_threaded)|定義一個或多個物件是否使用公寓線程。|
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](#_atl_cstring_explicit_constructors)|使某些`CString`構造函數成為顯式,防止任何無意轉換。|
|[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)|定義此宏以便使用C++標準相容的語法,當使用非標準語法初始化指向成員函數的指標時,該語法會生成C4867編譯器錯誤。|
|[_ATL_FREE_THREADED](#_atl_free_threaded)|定義一個或多個物件是否使用自由線程或中性線程。|
|[_ATL_MULTI_THREADED](#_atl_multi_threaded)|指示專案將具有標記為「兩者」 、「自由」 或「中性」的物件的符號。 應改為使用宏[_ATL_FREE_THREADED。](#_atl_free_threaded)|
|[_ATL_NO_AUTOMATIC_NAMESPACE](#_atl_no_automatic_namespace)|防止預設使用命名空間作為 ATL 的符號。|
|[_ATL_NO_COM_SUPPORT](#_atl_no_com_support)|阻止與 COM 相關的代碼與專案一起編譯的符號。|
|[ATL_NO_VTABLE](#atl_no_vtable)|阻止在類的構造函數和析構函數中初始化 vtable 指標的符號。|
|[ATL_NOINLINE](#atl_noinline)|指示函數的符號不應內聯。|
|[_ATL_SINGLE_THREADED](#_atl_single_threaded)|定義是否所有物件都使用單個線程模型。|

## <a name="_atl_all_warnings"></a><a name="_atl_all_warnings"></a>_ATL_ALL_WARNINGS

啟用從早期版本的 ATL 轉換的專案中的錯誤的符號。

```
#define _ATL_ALL_WARNINGS
```

### <a name="remarks"></a>備註

在 Visual C++ .NET 2002 之前,ATL 禁用了許多警告並將其禁用,以便它們永遠不會出現在用戶代碼中。 具體來說：

- C4127 條件表示式是常量運算式

- C4786「標識符」:標識符被截斷為調試資訊中的「數位」字元

- 使用 C4201 非標準擴充:無名結構/聯合

- C4103"檔案名":使用#pragma包更改對齊方式

- C4291"聲明":未找到匹配的運算符刪除;如果初始化引發異常,則不會釋放記憶體

- C4268"標識符":"使用編譯器生成的預設建構函數初始化的"const"靜態/全域數據用零填充物件

- C4702 無法存取的代碼

在從早期版本轉換的專案中,庫標頭仍禁用這些警告。

通過在包含庫標頭之前將以下行添加到*pch.h(Visual* Studio 2017 和更早版本中的*stdafx.h)* 檔中,可以更改此行為。

[!code-cpp[NVC_ATL_Utilities#97](../../atl/codesnippet/cpp/compiler-options-macros_1.h)]

如果添加了`#define`此選項,ATL 標頭將小心保留這些警告的狀態,以便它們不會全域禁用(或者如果使用者顯式禁用單個警告,而不是啟用它們)。

默認情況下,新專案在`#define` *pch.h(Visual* Studio 2017 和更早版本中的*stdafx.h)* 中設置了此集。

## <a name="_atl_apartment_threaded"></a><a name="_atl_apartment_threaded"></a>_ATL_APARTMENT_THREADED

定義一個或多個物件是否使用公寓線程。

```
_ATL_APARTMENT_THREADED
```

### <a name="remarks"></a>備註

指定公寓線程。 有關其他線程選項,請參閱[指定專案的線程模型](../../atl/specifying-the-threading-model-for-a-project-atl.md),以及[ATL 簡單物件精靈選項](../../atl/reference/options-atl-simple-object-wizard.md),瞭解可用於 ATL 物件的線程模型的說明。

## <a name="_atl_cstring_explicit_constructors"></a><a name="_atl_cstring_explicit_constructors"></a>_ATL_CSTRING_EXPLICIT_CONSTRUCTORS

使某些`CString`構造函數成為顯式,防止任何無意轉換。

```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```

### <a name="remarks"></a>備註

定義此建構函數時,使用顯式關鍵字編譯採用單個參數的所有 CString 構造函數,從而阻止輸入參數的隱式轉換。 例如,這意味著在定義_UNICODE時,如果嘗試使用 char* 字串作為 CString 構造函數參數,則會導致編譯器錯誤。 在需要防止窄字串類型和寬字串類型之間的隱式轉換的情況下使用此宏。

通過對所有構造函數位串參數使用_T宏,可以定義_ATL_CSTRING_EXPLICIT_CONSTRUCTORS並避免編譯錯誤,而不管是否定義了_UNICODE。

## <a name="_atl_enable_ptm_warning"></a><a name="_atl_enable_ptm_warning"></a>_ATL_ENABLE_PTM_WARNING

定義此宏以強制使用 ANSI C++標準相容的語法來指向成員函數的指標。 使用此宏將導致使用非標準語法初始化指向成員函數的指標時生成 C4867 編譯器錯誤。

```
#define _ATL_ENABLE_PTM_WARNING
```

### <a name="remarks"></a>備註

ATL 和 MFC 庫已更改,以匹配 Microsoft C++編譯器改進的標準C++合規性。 根據 ANSI C++標準,指向類別的函數的指標的語法應`&CMyClass::MyFunc`為 。

如果未定義[_ATL_ENABLE_PTM_WARNING(](#_atl_enable_ptm_warning)預設情況),ATL/MFC 會禁用宏映射中的 C4867 錯誤(尤其是消息映射),以便在早期版本中創建的代碼可以繼續像以前那樣生成。 如果定義 **_ATL_ENABLE_PTM_WARNING,** 則代碼應C++標準相容。

但是,非標準窗體已被棄用。 您需要將現有代碼移動到C++標準相容的語法。 例如，下列程式碼：

[!code-cpp[NVC_MFCListView#14](../../atl/reference/codesnippet/cpp/compiler-options-macros_2.cpp)]

應變更為：

[!code-cpp[NVC_MFCListView#11](../../atl/reference/codesnippet/cpp/compiler-options-macros_3.cpp)]

對於地圖宏,添加放大器和"&"字元。 不應在代碼中再次添加該字元。

## <a name="_atl_free_threaded"></a><a name="_atl_free_threaded"></a>_ATL_FREE_THREADED

定義一個或多個物件是否使用自由線程或中性線程。

```
_ATL_FREE_THREADED
```

### <a name="remarks"></a>備註

指定自由線程。 自由線程等效於多線程單元模型。 有關其他線程選項,請參閱[指定專案的線程模型](../../atl/specifying-the-threading-model-for-a-project-atl.md),以及[ATL 簡單物件精靈選項](../../atl/reference/options-atl-simple-object-wizard.md),瞭解可用於 ATL 物件的線程模型的說明。

## <a name="_atl_multi_threaded"></a><a name="_atl_multi_threaded"></a>_ATL_MULTI_THREADED

指示專案將具有標記為「兩者」 、「自由」 或「中性」的物件的符號。

```
_ATL_MULTI_THREADED
```

### <a name="remarks"></a>備註

如果定義了此符號,ATL 將提取正確同步對全域數據的訪問的代碼。 新代碼應使用等效的宏[_ATL_FREE_THREADED。](#_atl_free_threaded)

## <a name="_atl_no_automatic_namespace"></a><a name="_atl_no_automatic_namespace"></a>_ATL_NO_AUTOMATIC_NAMESPACE

防止預設使用命名空間作為 ATL 的符號。

```
_ATL_NO_AUTOMATIC_NAMESPACE
```

### <a name="remarks"></a>備註

如果未定義此符號,則包括 atlbase.h 預設**使用命名空間 ATL**執行,這可能導致命名衝突。 為了防止這種情況,請定義此符號。

## <a name="_atl_no_com_support"></a><a name="_atl_no_com_support"></a>_ATL_NO_COM_SUPPORT

阻止與 COM 相關的代碼與專案一起編譯的符號。

```
_ATL_NO_COM_SUPPORT
```

## <a name="atl_no_vtable"></a><a name="atl_no_vtable"></a>ATL_NO_VTABLE

阻止在類的構造函數和析構函數中初始化 vtable 指標的符號。

```
ATL_NO_VTABLE
```

### <a name="remarks"></a>備註

如果阻止在類的構造函數和析構函數中初始化 vtable 指標,則連結器可以消除 vtable 及其指向的所有函數。 延伸到 **__declspec(可更新的)**。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#53](../../atl/codesnippet/cpp/compiler-options-macros_4.h)]

## <a name="atl_noinline"></a><a name="atl_noinline"></a>ATL_NOINLINE

指示函數的符號不應內聯。

```
    ATL_NOINLINE inline
    myfunction()
    {
    ...
    }
```

### <a name="parameters"></a>參數

*我的功能*<br/>
不應內聯的函數。

### <a name="remarks"></a>備註

如果要確保函數不會由編譯器內聯,即使必須將其聲明為內聯,以便將其放置在標頭檔中,也可以使用此符號。 延伸到 **__declspec(名詞)**。

## <a name="_atl_single_threaded"></a><a name="_atl_single_threaded"></a>_ATL_SINGLE_THREADED

定義所有物件是否使用單一線程式程式

```
_ATL_SINGLE_THREADED
```

### <a name="remarks"></a>備註

指定物件始終在主 COM 線程中運行。 有關其他線程選項,請參閱[指定專案的線程模型](../../atl/specifying-the-threading-model-for-a-project-atl.md),以及[ATL 簡單物件精靈選項](../../atl/reference/options-atl-simple-object-wizard.md),瞭解可用於 ATL 物件的線程模型的說明。

## <a name="see-also"></a>另請參閱

[巨集](../../atl/reference/atl-macros.md)
