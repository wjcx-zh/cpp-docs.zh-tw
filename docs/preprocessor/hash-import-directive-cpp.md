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
ms.openlocfilehash: afd05e7380ec3838fe9763be23ccfae338adb4fb
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220272"
---
# <a name="import-directive-c"></a>#import 指示詞C++（）

**C++特殊**

用來加入類型程式庫中的資訊。 類型程式庫的內容會轉換成 C++ 類別，多半是在描述 COM 介面。

## <a name="syntax"></a>語法

> **#import**"*filename*" \[*屬性*] \
> **#import**\< *filename*屬性]>  \[

### <a name="parameters"></a>參數

*名稱*\
指定要匯入的類型程式庫。 *檔案名*可以是下列其中一種類型：

- 包含類型程式庫之檔案的名稱，例如 .olb、.tlb 或 .dll 檔。 關鍵字`file:`可以放在每個檔案名的前面。

- 類型程式庫中的控制項 ProgID。 關鍵字`progid:`可以放在每個 progid 的前面。 例如：

    ```cpp
    #import "progid:my.prog.id.1.5"
    ```

   如需 progid 的詳細資訊，請參閱[指定當地語系化 ID 和版本號碼](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber)。

   當您在64位的作業系統上使用32位的跨平臺編譯器時，編譯器只能讀取32位的登錄 hive。 您可能會想要使用原生 64 位元編譯器，建置並註冊 64 位元類型程式庫。

- 類型程式庫的程式庫 ID。 關鍵字（ `libid:`）可以在每個程式庫識別碼之前。 例如：

    ```cpp
    #import "libid:12341234-1234-1234-1234-123412341234" version("4.0") lcid("9")
    ```

   如果您未指定`version`或`lcid`，套用至`progid:`的[規則](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber)也會套用至`libid:`。

- 可執行檔 (.exe)。

- 包含類型程式庫資源（例如 .ocx）的程式庫（.dll）檔案。

- 包含類型程式庫的複合文件。

- **LoadTypeLib** API 可以理解的任何其他檔案格式。

*特性*\
一或多個[#import 屬性](#_predir_the_23import_directive_import_attributes)。 使用空格或逗號分隔屬性。 例如：

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace, raw_interfaces_only
```

\-或-

```cpp
#import "..\drawctl\drawctl.tlb" no_namespace raw_interfaces_only
```

## <a name="remarks"></a>備註

### <a name="_predir_the_23import_directive_searchorderforfilename"></a>檔案名的搜尋順序

*filename*前面會選擇性地加上目錄規格。 檔案名稱必須指定現有的檔案名稱。 兩個語法形式之間的差異在於未完整指定路徑時，前置處理器搜尋類型程式庫檔案的順序。

|語法形式|動作|
|-----------------|------------|
|有引號的形式|指示預處理器在包含 **#import**語句的檔案目錄中，先尋找類型程式庫檔案，然後在任何檔案的目錄中包含該檔案（`#include`）。 然後，前置處理器會沿著如下所示的路徑搜尋。|
|角括弧形式|指示前置處理器依照下列路徑搜尋類型程式庫檔案：<br /><br /> 1.`PATH`環境變數路徑清單<br />2.`LIB`環境變數路徑清單<br />3.[/I](../build/reference/i-additional-include-directories.md)編譯器選項所指定的路徑，不同之處在于編譯器會搜尋從另一個具有[no_registry](../preprocessor/no-registry.md)屬性之類型程式庫所參考的類型程式庫。|

### <a name="_predir_the_23import_directive_specifyingthelocalizationidandversionnumber"></a>指定當地語系化識別碼和版本號碼

當您指定 ProgID 時，也可以指定 ProgID 的當地語系化 ID 和版本號碼。 例如：

```cpp
#import "progid:my.prog.id" lcid("0") version("4.0)
```

如果您未指定當地語系化識別碼，則會根據下列規則來選擇 progid：

- 如果只有一個當地語系化 ID，則會使用該識別碼。

- 如果有一個以上的當地語系化識別碼，則會使用版本號碼為0、9或409的第一個。

- 如果有一個以上的當地語系化識別碼，而且它們都不是0、9或409，則會使用最後一個。

- 如果您未指定版本號碼，則會使用最新版本。

###  <a name="_predir_the_23import_directive_header_files_created_by_import"></a>匯入所建立的標頭檔

**#import**會建立兩個標頭檔，以在原始程式碼中C++重建類型程式庫內容。 主要標頭檔類似于 Microsoft 介面定義語言（MIDL）編譯器所產生的檔案，但具有其他編譯器產生的程式碼和資料。 [主要標頭檔](#_predir_the_primary_type_library_header_file)具有與類型程式庫相同的基底名稱，加上。TLH 擴充功能。 次要標頭檔具有和類型程式庫相同的基底名稱，再加上 .TLI 副檔名。 它包含編譯器產生的成員函式的實作，而且已在主要標頭檔中包含 (`#include`)。

如果匯入使用`byref`參數的分配介面屬性， **#import**不會產生函數的[__declspec （property）](../cpp/property-cpp.md)語句。

這兩個標頭檔會放在 [ [/fo （名稱物件檔案）](../build/reference/fo-object-file-name.md) ] 選項所指定的輸出目錄中。 然後編譯器會讀取和編譯它們，如同主要標頭檔是由`#include`指示詞所命名。

下列編譯器優化會隨附 **#import**指示詞：

- 標頭檔在建立時會獲得與類型程式庫相同的時間戳記。

- 處理 **#import**時，編譯器會先檢查標頭是否存在且為最新狀態。 如果是，則不需要重新建立。

**#Import**指示詞也會參與最少的重建，而且可以放置在先行編譯標頭檔中。  如需詳細資訊，請參閱[建立先行編譯標頭檔](../build/creating-precompiled-header-files.md)。

### <a name="_predir_the_primary_type_library_header_file"></a>主要類型程式庫標頭檔

主要類型程式庫標頭檔包含七個區段：

- 標題樣板：包含 comdef.h 的批註`#include` 、語句。H （定義標頭中使用的一些標準宏），以及其他的安裝資訊。

- 向前參考和 typedef：包含結構宣告`struct IMyInterface` ，例如和 typedef。

- 智慧型指標宣告：範本類別`_com_ptr_t`是智慧型指標。 它會封裝介面指標，並免除呼叫`AddRef`、 `Release`和`QueryInterface`函式的需求。 它也會在`CoCreateInstance`建立新的 COM 物件時隱藏呼叫。 本節使用巨集式`_COM_SMARTPTR_TYPEDEF`來建立 COM 介面的 typedef，做為[_com_ptr_t](../cpp/com-ptr-t-class.md)樣板類別的範本特製化。 例如，如果是介面`IMyInterface`，則為。TLH 檔案將包含：

    ```TLH
    _COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
    ```

   編譯器將展開為：

    ```cpp
    typedef _com_ptr_t<_com_IIID<IMyInterface, __uuidof(IMyInterface)> > IMyInterfacePtr;
    ```

   然後就可以將類型 `IMyInterfacePtr` 用來取代原始介面指標 `IMyInterface*`。 因此，不需要呼叫各種`IUnknown`成員函式

- Typeinfo 宣告：主要是由類別定義以及公開所傳回`ITypeLib:GetTypeInfo`之個別 typeinfo 專案的其他專案所組成。 在本節中，類型程式庫中的每個 typeinfo 會反映在相依於 `TYPEKIND` 資訊之表單的標頭中。

- 選擇性的舊樣式 GUID 定義：包含已命名 GUID 常數的初始化。 這些名稱的格式`CLSID_CoClass`和`IID_Interface`（類似 MIDL 編譯器所產生的）。

- 次要類型程式庫標頭的 `#include` 陳述式。

- 頁尾樣板化：目前包含`#pragma pack(pop)`。

所有區段（標題為「未使用」和「頁尾」的樣板區段除外）都會包含在命名空間`library`中，其名稱是由原始 IDL 檔案中的語句所指定。 您可以使用類型程式庫標頭中的名稱，方法是使用命名空間名稱進行明確限定。 或者，您可以包含下列語句：

```cpp
using namespace MyLib;
```

緊接在原始程式碼中的 **#import**語句之後。

您可以使用 **#import**指示詞的[no_namespace](no-namespace.md)）屬性來隱藏命名空間。 不過，隱藏命名空間可能導致名稱衝突。 命名空間也可以由[rename_namespace](rename-namespace.md)屬性重新命名。

編譯器會提供其目前正在處理之類型程式庫所需之任何類型程式庫相依性的完整路徑。 路徑會以註解的形式寫入類型程式庫標頭 (.TLH)，編譯器為每個處理過的類型程式庫產生此標頭。

如果類型程式庫包含定義於其他類型程式庫之類型的參考，則 .TLH 檔案會包含下列排序的註解：

```TLH
//
// Cross-referenced type libraries:
//
//  #import "c:\path\typelib0.tlb"
//
```

**#Import**批註中的實際檔案名是交互參照類型程式庫的完整路徑，儲存在登錄中。 如果您遇到因遺漏類型定義所造成的錯誤，請檢查的開頭的批註。TLH，查看可能需要先匯入哪些相依類型程式庫。 編譯 .TLI 檔案時，可能發生的錯誤為語法錯誤 (例如，C2143、C2146、C2321)、C2501 (遺漏 decl 指定名稱) 或 C2433 (資料宣告不允許「內嵌」)。

若要解決相依性錯誤，請決定不是由系統標頭提供的相依性批註，然後在相依類型程式庫的 **#import**指示詞之前的某個時間點提供 **#import**指示詞。

### <a name="_predir_the_23import_directive_import_attributes"></a>#import 屬性

**#import**可以選擇性地包含一個或多個屬性。 這些屬性會指示編譯器修改類型程式庫標頭的內容。 您可以使用 **\\** 反斜線（）符號，在單一 **#import**語句中包含額外的行。 例如：

```cpp
#import "test.lib" no_namespace \
   rename("OldName", "NewName")
```

如需詳細資訊，請參閱[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)。

**結束C++特定**

## <a name="see-also"></a>另請參閱

[預處理器指示詞](../preprocessor/preprocessor-directives.md)\
[編譯器 COM 支援](../cpp/compiler-com-support.md)
