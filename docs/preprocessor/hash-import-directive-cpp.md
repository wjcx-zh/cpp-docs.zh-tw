---
title: '#import 指示詞 (C++)'
ms.date: 03/27/2019
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
ms.openlocfilehash: 98a0f9f66fb209bb41215fc1e86a9682a4fed023
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407675"
---
# <a name="import-directive-c"></a>#import 指示詞 (C++)

**C++特定**

用來加入類型程式庫中的資訊。 類型程式庫的內容會轉換成 C++ 類別，多半是在描述 COM 介面。

## <a name="syntax"></a>語法

```
#import "filename" [attributes]
#import <filename> [attributes]
```

### <a name="parameters"></a>參數

*filename*<br/>
指定要匯入的類型程式庫。 *檔名*可以是下列其中之一：

- 包含類型程式庫之檔案的名稱，例如 .olb、.tlb 或 .dll 檔。 關鍵字**檔案：**，可以在每個檔案名稱。

- 類型程式庫中的控制項 ProgID。 關鍵字**progid:**，可以在每個 progid。 例如: 

    ```cpp
    #import "progid:my.prog.id.1.5"
    ```

   如需 progid 的詳細資訊，請參閱 <<c0> [ 指定當地語系化 ID 和版本號碼](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber)。

   請注意，在 64 位元作業系統上使用跨平台編譯器進行編譯時，編譯器只能讀取 32 位元登錄區。 您可能會想要使用原生 64 位元編譯器，建置並註冊 64 位元類型程式庫。

- 類型程式庫的程式庫 ID。 關鍵字**libid:**，可以在每個程式庫識別碼。 例如：

    ```cpp
    #import "libid:12341234-1234-1234-1234-123412341234" version("4.0") lcid("9")
    ```

   如果您未指定版本或 lcid，[規則](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber)，會套用至**progid:** 也會套用至**libid:**。

- 可執行檔 (.exe)。

- 包含類型程式庫資源 (例如 .ocx) 的程式庫 (.dll) 檔案。

- 包含類型程式庫的複合文件。

- 可以理解的任何其他檔案格式**LoadTypeLib** API。

*屬性*<br/>
一或多個[#import 屬性](#_predir_the_23import_directive_import_attributes)。 使用空格或逗號分隔屬性。 例如：

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace, raw_interfaces_only
```

\-或-

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace raw_interfaces_only
```

## <a name="remarks"></a>備註

## <a name="_predir_the_23import_directive_searchorderforfilename"></a> 檔案名稱的搜尋順序

*檔名*可以選擇性加上目錄規格。 檔案名稱必須指定現有的檔案名稱。 兩個語法形式之間的差異在於未完整指定路徑時，前置處理器搜尋類型程式庫檔案的順序。

|語法形式|動作|
|-----------------|------------|
|有引號的形式|指示前置處理器先在包含的檔案的目錄中的類型程式庫檔案看起來 **#import**陳述式，然後在包含任何檔案的目錄 (`#include`) 該檔案。 然後，前置處理器會沿著如下所示的路徑搜尋。|
|角括弧形式|指示前置處理器依照下列路徑搜尋類型程式庫檔案：<br /><br /> 1.`PATH`環境變數路徑清單<br />2.`LIB`環境變數路徑清單<br />3./I 指定的路徑 (其他 include 目錄) 編譯器選項，但是它，編譯器會搜尋已從另一個型別程式庫，與參考型別程式庫[no_registry](../preprocessor/no-registry.md)屬性。|

##  <a name="_predir_the_23import_directive_specifyingthelocalizationidandversionnumber"></a> 指定當地語系化 ID 和版本號碼

當您指定 ProgID 時，也可以指定 ProgID 的當地語系化 ID 和版本號碼。 例如: 

```cpp
#import "progid:my.prog.id" lcid("0") version("4.0)
```

如果您未指定當地語系化 ID，則會根據下列規則選擇 ProgID：

- 如果只有一個當地語系化 ID，則使用該 ID。

- 如果有多個當地語系化 ID，則會使用版本號碼為 0、9 或 409 的第一個 ID。

- 如果有多個當地語系化 ID，但沒有一個是 0、9 或 409，則會使用最後一個。

- 如果沒有指定版本號碼，就會使用最新版本。

##  <a name="_predir_the_23import_directive_header_files_created_by_import"></a> 匯入所建立的標頭檔

**#import**會建立兩個標頭檔，以重新建構的類型程式庫內容C++原始碼。 主要標頭檔類似於由 Microsoft 介面定義語言 (MIDL) 編譯器產生的檔案，但是另有編譯器產生的其他程式碼和資料。 [主要標頭檔](#_predir_the_primary_type_library_header_file)為型別程式庫中，具有相同的基底名稱加上。TLH 延伸模組。 次要標頭檔具有和類型程式庫相同的基底名稱，再加上 .TLI 副檔名。 它包含編譯器產生的成員函式的實作，而且已在主要標頭檔中包含 (`#include`)。

如果匯入使用 byref 參數的 dispinterface 屬性，#import 將不會產生 __declspec ([屬性](../cpp/property-cpp.md)) 函式的陳述式。

這兩個標頭檔會放置在 /Fo (為目的檔命名) 選項指定的輸出目錄中。 編譯器接著會讀取並編譯這些檔案，就如同主要標頭檔是以 `#include` 指示詞所命名。

下列編譯器最佳化可搭配 **#import**指示詞：

- 標頭檔在建立時會獲得與類型程式庫相同的時間戳記。

- 當 **#import**是處理，編譯器會先檢查標頭是否存在，且是最新狀態。 如果是，就不需要重新建立。

**#Import**指示詞也參與最少重建，並可以放置在先行編譯標頭檔。 請參閱[建立先行編譯標頭檔](../build/creating-precompiled-header-files.md)如需詳細資訊。

###  <a name="_predir_the_primary_type_library_header_file"></a> 主要類型程式庫標頭檔
主要類型程式庫標頭檔包含七個區段：

- 標題重複使用區段：包含註解、 `#include` COMDEF 陳述式。H （會定義使用一些標準巨集的標頭中），和其他設定資訊。

- 向前參考和 typedef:例如，包含結構宣告`struct IMyInterface`和 typedef。

- 智慧型指標宣告：此範本類別`_com_ptr_t`是一個智慧型指標實作，封裝介面指標，而且不需要呼叫`AddRef`， `Release`，`QueryInterface`函式。 此外，還會在建立新的 COM 物件時隱藏 `CoCreateInstance` 呼叫。 本節使用巨集陳述式`_COM_SMARTPTR_TYPEDEF`以建立要的樣板特製化的 COM 介面的 typedef [_com_ptr_t](../cpp/com-ptr-t-class.md)範本類別。 例如，對於介面`IMyInterface`、。TLH 檔案會包含：

    ```TLH
    _COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
    ```

   編譯器將展開為：

    ```cpp
    typedef _com_ptr_t<_com_IIID<IMyInterface, __uuidof(IMyInterface)> > IMyInterfacePtr;
    ```

   然後就可以將類型 `IMyInterfacePtr` 用來取代原始介面指標 `IMyInterface*`。 因此，就不需要呼叫各種`IUnknown`成員函式

- Typeinfo 宣告：主要包含的類別定義和其他項目公開所傳回之個別 typeinfo 項`ITypeLib:GetTypeInfo`。 在本節中，類型程式庫中的每個 typeinfo 會反映在相依於 `TYPEKIND` 資訊之表單的標頭中。

- 選擇性舊樣式 GUID 定義：包含具名 GUID 常數的初始化。 這些是名稱格式`CLSID_CoClass`和`IID_Interface`，類似於 MIDL 編譯器所產生。

- 次要類型程式庫標頭的 `#include` 陳述式。

- 頁尾重複使用區段：目前包含`#pragma pack(pop)`。

所有的區段，除了標題重複使用和頁尾重複使用區段上，會以所指定的名稱括住命名空間`library`原始 IDL 檔案中的陳述式。 您可以明確限定命名空間或包含下列陳述式，來使用類型程式庫標頭中的名稱：

```cpp
using namespace MyLib;
```

之後立即 **#import**原始程式碼中的陳述式。

命名空間可以使用隱藏[no_namespace](no-namespace.md)) 屬性 **#import**指示詞。 不過，隱藏命名空間可能導致名稱衝突。 命名空間也可以藉由重新命名[rename_namespace](rename-namespace.md)屬性。

編譯器會提供其目前處理中類型程式庫所需之任何類型程式庫相依性的完整路徑。 路徑會以註解的形式寫入類型程式庫標頭 (.TLH)，編譯器為每個處理過的類型程式庫產生此標頭。

如果類型程式庫包含定義於其他類型程式庫之類型的參考，則 .TLH 檔案會包含下列排序的註解：

```TLH
//
// Cross-referenced type libraries:
//
//  #import "c:\path\typelib0.tlb"
//
```

在實際的檔名 **#import**註解是交互參考的類型程式庫的完整路徑，儲存在登錄中。 如果因為遺漏類型定義而發生錯誤，請檢查 .TLH 頂端的註解，以查看哪個相依類型程式庫可能需要先匯入。 編譯 .TLI 檔案時，可能發生的錯誤為語法錯誤 (例如，C2143、C2146、C2321)、C2501 (遺漏 decl 指定名稱) 或 C2433 (資料宣告不允許「內嵌」)。

您必須判斷哪些相依性的註解都不提供的系統標頭，然後提供 **#import**指示詞之前的某個位置 **#import**相依的指示詞若要解決錯誤的型別程式庫。

## <a name="_predir_the_23import_directive_import_attributes"></a> #import 屬性

**#import**可以選擇性地包含一個或多個屬性。 這些屬性會指示編譯器修改類型程式庫標頭的內容。 反斜線 (**\\**) 符號可用來包含其他行，在單一 **#import**陳述式。 例如：

```cpp
#import "test.lib" no_namespace \
   rename("OldName", "NewName")
```

如需詳細資訊，請參閱 < [#import 屬性](../preprocessor/hash-import-attributes-cpp.md)。

**結束C++特定**

## <a name="see-also"></a>另請參閱

[前置處理器指示詞](../preprocessor/preprocessor-directives.md)<br/>
[編譯器 COM 支援](../cpp/compiler-com-support.md)