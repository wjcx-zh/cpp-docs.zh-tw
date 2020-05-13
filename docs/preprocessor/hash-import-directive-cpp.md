---
title: '#import 指示詞 (C++)'
ms.date: 08/29/2019
f1_keywords:
- '#import'
helpviewer_keywords:
- .tlh files
- '#import directive'
- import directive (#import)
- tlh files
- tlbid switch
- preprocessor, directives
- COM, type library header file
ms.assetid: 787d1112-e543-40d7-ab15-a63d43f4030a
ms.openlocfilehash: 9cdfef091b659151f427c381e386f0e83396e741
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332060"
---
# <a name="import-directive-c"></a>#import指令 (C++)

**C++ 專有的**

用來加入類型程式庫中的資訊。 類型程式庫的內容會轉換成 C++ 類別，多半是在描述 COM 介面。

## <a name="syntax"></a>語法

> **#import**「*檔案名稱*」\[*屬性*:
> **#import**\<*filename*> 檔案\[名稱*屬性*|

### <a name="parameters"></a>參數

*檔案名稱*\
指定要匯入的類型程式庫。 *檔案名稱*可以是以下類型之一:

- 包含類型程式庫之檔案的名稱，例如 .olb、.tlb 或 .dll 檔。 關鍵字`file:`可以位於每個檔名之前。

- 類型程式庫中的控制項 ProgID。 關鍵字`progid:`, 可以先於每個上位。 例如：

    ```cpp
    #import "progid:my.prog.id.1.5"
    ```

   有關 progid 的更多,請參閱[指定本地化 ID 和版本號](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber)。

   在 64 位元作業系統上使用 32 位元交叉編譯器時,編譯器只能讀取 32 位元註冊表配置單元。 您可能會想要使用原生 64 位元編譯器，建置並註冊 64 位元類型程式庫。

- 類型程式庫的程式庫 ID。 關鍵字`libid:`可以位於每個庫 ID 之前。 例如：

    ```cpp
    #import "libid:12341234-1234-1234-1234-123412341234" version("4.0") lcid("9")
    ```

   沒有`version``lcid`指定或 ,則套用`progid:``libid:`於[的規則](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber)也會套用 。

- 可執行檔 (.exe)。

- 包含類型庫資源(如 .ocx)的庫 (.dll) 檔。

- 包含類型程式庫的複合文件。

- **LoadTypeLib** API 可以理解的任何其他檔案格式。

*屬性*\
一個或多個[#import属性](#_predir_the_23import_directive_import_attributes)。 使用空格或逗號分隔屬性。 例如：

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace, raw_interfaces_only
```

\-或-

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace raw_interfaces_only
```

## <a name="remarks"></a>備註

### <a name="search-order-for-filename"></a><a name="_predir_the_23import_directive_searchorderforfilename"></a>搜尋檔案名的順序

*檔名*在目錄規範之前是可選的。 檔案名稱必須指定現有的檔案名稱。 兩個語法形式之間的差異在於未完整指定路徑時，前置處理器搜尋類型程式庫檔案的順序。

|語法形式|動作|
|-----------------|------------|
|有引號的形式|指示預處理器首先在包含 **#import**語句的檔案目錄中查找類型庫檔,然後在包含`#include`該檔的任何檔的目錄中尋找類型庫檔。 然後，前置處理器會沿著如下所示的路徑搜尋。|
|角括弧形式|指示前置處理器依照下列路徑搜尋類型程式庫檔案：<br /><br /> 1.`PATH`環境變數路徑清單<br />2.`LIB`環境變數路徑清單<br />3. [/I](../build/reference/i-additional-include-directories.md)編譯器選項指定的路徑,除了編譯器正在搜索從具有[no_registry](../preprocessor/no-registry.md)屬性的另一個類型庫中引用的類型庫。|

### <a name="specify-the-localization-id-and-version-number"></a><a name="_predir_the_23import_directive_specifyingthelocalizationidandversionnumber"></a>指定本地化識別碼與版本號

當您指定 ProgID 時，也可以指定 ProgID 的當地語系化 ID 和版本號碼。 例如：

```cpp
#import "progid:my.prog.id" lcid("0") version("4.0)
```

沒有指定本地化代碼,則根據以下規則選擇 progid:

- 如果只有一個本地化 ID,則使用該 ID。

- 如果有多個本地化 ID,則使用版本號為 0、9 或 409 的第一個 ID。

- 如果有多個當地語系化 ID,並且它們都不是 0、9 或 409,則使用最後一個 ID。

- 如果不指定版本號,將使用最新版本。

### <a name="header-files-created-by-import"></a><a name="_predir_the_23import_directive_header_files_created_by_import"></a>匯入建立的標頭檔

**#import**創建兩個標頭檔,用於在C++原始程式碼中重建類型庫內容。 主標頭檔類似於 Microsoft 介面定義語言 (MIDL) 編譯器生成的檔,但具有其他編譯器生成的代碼和數據。 [主標頭檔](#_predir_the_primary_type_library_header_file)具有與類型庫相同的基本名稱,外加一個 。TLH擴展。 次要標頭檔具有和類型程式庫相同的基底名稱，再加上 .TLI 副檔名。 它包含編譯器產生的成員函式的實作，而且已在主要標頭檔中包含 (`#include`)。

如果導入使用`byref`參數的 dispinterface 屬性 **,#import**不會為函數生成[__declspec(屬性)](../cpp/property-cpp.md)語句。

兩個標頭檔都放置在[/Fo(名稱物件檔)](../build/reference/fo-object-file-name.md)選項指定的輸出目錄中。 然後,編譯器讀取和編譯它們,就像主標頭檔由指令命名一樣`#include`。

#import**指令附帶**了以下編譯器優化:

- 標頭檔在建立時會獲得與類型程式庫相同的時間戳記。

- 處理 **#import**時,編譯器首先檢查標頭是否存在並且是最新的。 如果是,則無需重新創建。

**#import**指令還參與最少的重建,可以放置在預編譯的標頭檔中。  關於詳細資訊,請參閱[建立預寫編譯的標頭檔](../build/creating-precompiled-header-files.md)。

### <a name="primary-type-library-header-file"></a><a name="_predir_the_primary_type_library_header_file"></a>主型別庫標頭檔

主要類型程式庫標頭檔包含七個區段：

- 標題重複使用區段：包含註解、COMDEF.H 的 `#include` 陳述式 (會定義標題中使用的一些標準巨集)，以及其他設定資訊。

- 向前參考和 typedef：包含結構宣告，例如 `struct IMyInterface` 和 Typedef。

- 智慧指標聲明:範本類`_com_ptr_t`是智慧指標。 它封裝介面指標,並不需要調用`AddRef`和`Release``QueryInterface`函數。 在創建新的`CoCreateInstance`COM 物件時,它還隱藏呼叫。 本節使用宏語句`_COM_SMARTPTR_TYPEDEF`將 COM 介面的類型defs作為[_com_ptr_t](../cpp/com-ptr-t-class.md)範本類的範本專門化。 例如,對於介面`IMyInterface`, .TLH 檔將包含:

    ```TLH
    _COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
    ```

   編譯器將展開為：

    ```cpp
    typedef _com_ptr_t<_com_IIID<IMyInterface, __uuidof(IMyInterface)> > IMyInterfacePtr;
    ```

   然後就可以將類型 `IMyInterfacePtr` 用來取代原始介面指標 `IMyInterface*`。 因此,無需呼叫各個`IUnknown`成員函數

- 類型資訊聲明:主要由類定義和其他項組成,公開返回的`ITypeLib:GetTypeInfo`單個類型資訊項。 在本節中，類型程式庫中的每個 typeinfo 會反映在相依於 `TYPEKIND` 資訊之表單的標頭中。

- 選擇性舊樣式 GUID 定義：包含具名 GUID 常數的初始化。 這些名稱具有窗體`CLSID_CoClass``IID_Interface`和 ,類似於 MIDL 編譯器生成的名稱。

- 次要類型程式庫標頭的 `#include` 陳述式。

- 頁尾重複使用區段：目前包含 `#pragma pack(pop)`。

除標題樣板和註腳樣板部分外,所有部分都包含在命名空間中,其名稱由原始 IDL`library`檔中的語句指定。 可以使用命名空間名稱透過顯式限定使用類型庫標頭中的名稱。 或者,您可以包括以下語句:

```cpp
using namespace MyLib;
```

在原始碼中 **#import**語句之後。

可以使用 **#import**指令的[no_namespace](no-namespace.md)) 屬性來抑制命名空間。 不過，隱藏命名空間可能導致名稱衝突。 命名空間也可以由[rename_namespace](rename-namespace.md)屬性重新命名。

編譯器提供當前處理的類型庫所需的任何類型的庫依賴項的完整路徑。 路徑會以註解的形式寫入類型程式庫標頭 (.TLH)，編譯器為每個處理過的類型程式庫產生此標頭。

如果類型程式庫包含定義於其他類型程式庫之類型的參考，則 .TLH 檔案會包含下列排序的註解：

```TLH
//
// Cross-referenced type libraries:
//
//  #import "c:\path\typelib0.tlb"
//
```

**#import**註釋中的實際檔名是存儲在註冊表中的交叉引用類型庫的完整路徑。 如果遇到由於缺少類型定義而導致的錯誤,請檢查的註解在 。TLH 以查看可能需要首先導入哪些從屬類型庫。 編譯 .TLI 檔案時，可能發生的錯誤為語法錯誤 (例如，C2143、C2146、C2321)、C2501 (遺漏 decl 指定名稱) 或 C2433 (資料宣告不允許「內嵌」)。

要解決依賴項錯誤,請確定系統標頭未以其他方式提供哪些依賴項註釋,然後在依賴類型庫**的#import**指令之前的某個時間點提供 **#import**指令。

### <a name="import-attributes"></a><a name="_predir_the_23import_directive_import_attributes"></a>#import属性

**#import**可以選擇包含一個或多個屬性。 這些屬性會指示編譯器修改類型程式庫標頭的內容。 反斜杠**\\**( ) 符號可用於在單個 **#import**語句中包含其他行。 例如：

```cpp
#import "test.lib" no_namespace \
   rename("OldName", "NewName")
```

有關詳細資訊,請參閱[#import属性](../preprocessor/hash-import-attributes-cpp.md)。

**END C++ 特定的**

## <a name="see-also"></a>另請參閱

[預處理器指令](../preprocessor/preprocessor-directives.md)\
[編譯器 COM 支援](../cpp/compiler-com-support.md)
