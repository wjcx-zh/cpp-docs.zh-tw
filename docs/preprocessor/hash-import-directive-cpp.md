---
title: "#import 指示詞 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "#import"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#import 指示詞"
  - ".tlh 檔案"
  - "COM, 類型程式庫標頭檔"
  - "import 指示詞 (#import)"
  - "前置處理器, 指示詞"
  - "tlbid 參數"
  - "tlh 檔案"
ms.assetid: 787d1112-e543-40d7-ab15-a63d43f4030a
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# #import 指示詞 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 專有的**  
  
 用來加入類型程式庫中的資訊。  類型程式庫的內容會轉換成 C\+\+ 類別，多半是在描述 COM 介面。  
  
## 語法  
  
```  
#import "filename" [attributes]  
#import <filename> [attributes]  
```  
  
#### 參數  
 *filename*  
 指定要匯入的類型程式庫。  `filename` 可以是下列其中一項：  
  
-   包含類型程式庫之檔案的名稱，例如 .olb、.tlb 或 .dll 檔。  關鍵字 **file:** 可以加在每個檔案名稱之前。  
  
-   類型程式庫中的控制項 ProgID。  關鍵字 **progid:** 可以加在每個 ProgID 之前。  例如：  
  
    ```  
    #import "progid:my.prog.id.1.5"  
    ```  
  
     如需 ProgID 的詳細資訊，請參閱[指定當地語系化 ID 和版本號碼](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber)。  
  
     請注意，在 64 位元作業系統上使用跨平台編譯器進行編譯時，編譯器只能讀取 32 位元登錄區。  您可能會想要使用原生 64 位元編譯器，建置並註冊 64 位元類型程式庫。  
  
-   類型程式庫的程式庫 ID。  關鍵字 **libid:** 可以加在每個程式庫 ID 之前。  例如：  
  
    ```  
    #import "libid:12341234-1234-1234-1234-123412341234" version("4.0") lcid("9")  
    ```  
  
     如果您未指定版本或 lcid，套用至 **progid:** 的[規則](#_predir_the_23import_directive_specifyingthelocalizationidandversionnumber)也會套用至 **libid:**。  
  
-   可執行檔 \(.exe\)。  
  
-   包含類型程式庫資源 \(例如 .ocx\) 的程式庫 \(.dll\) 檔案。  
  
-   包含類型程式庫的複合文件。  
  
-   **LoadTypeLib** 應用程式開發介面可以辨識的其他檔案格式。  
  
 `attributes`  
 一個或多個 [\#import 屬性](#_predir_the_23import_directive_import_attributes)。  使用空格或逗號分隔屬性。  例如：  
  
```  
#import "..\drawctl\drawctl.tlb" no_namespace, raw_interfaces_only  
```  
  
 \-或\-  
  
```  
#import "..\drawctl\drawctl.tlb" no_namespace raw_interfaces_only  
```  
  
## 備註  
  
##  <a name="_predir_the_23import_directive_searchorderforfilename"></a> 檔案名稱的搜尋順序  
 *filename* 前面可以選擇性加上目錄規格。  檔案名稱必須指定現有的檔案名稱。  兩個語法形式之間的差異在於未完整指定路徑時，前置處理器搜尋類型程式庫檔案的順序。  
  
|語法形式|動作|  
|----------|--------|  
|有引號的形式|指示前置處理器先在包含 `#import` 陳述式檔案的目錄中，然後在包含 \(`#include`\) 該檔案之任何檔案目錄中，尋找目錄中的類型程式庫檔案。  然後，前置處理器會沿著如下所示的路徑搜尋。|  
|角括弧形式|指示前置處理器依照下列路徑搜尋類型程式庫檔案：<br /><br /> 1.  **PATH** 環境變數路徑清單<br />2.  **LIB** 環境變數路徑清單<br />3.  \/I \(其他 Include 目錄\) 編譯器選項指定的路徑，除此之外，編譯器會搜尋另一個類型程式庫，該類型程式庫是從 [no\_registry](../preprocessor/no-registry.md) 屬性參考的類型程式庫。|  
  
##  <a name="_predir_the_23import_directive_specifyingthelocalizationidandversionnumber"></a> 指定當地語系化 ID 和版本號碼  
 當您指定 ProgID 時，也可以指定 ProgID 的當地語系化 ID 和版本號碼。  例如：  
  
```  
#import "progid:my.prog.id" lcid("0") version("4.0)  
```  
  
 如果您未指定當地語系化 ID，則會根據下列規則選擇 ProgID：  
  
-   如果只有一個當地語系化 ID，則使用該 ID。  
  
-   如果有多個當地語系化 ID，則會使用版本號碼為 0、9 或 409 的第一個 ID。  
  
-   如果有多個當地語系化 ID，但沒有一個是 0、9 或 409，則會使用最後一個。  
  
-   如果沒有指定版本號碼，就會使用最新版本。  
  
##  <a name="_predir_the_23import_directive_header_files_created_by_import"></a> 藉由匯入建立的標頭檔  
 `#import` 會建立兩個標頭檔，以重新建構 C\+\+ 原始程式碼的類型程式庫內容。  主要標頭檔類似於由 Microsoft 介面定義語言 \(MIDL\) 編譯器產生的檔案，但是另有編譯器產生的其他程式碼和資料。  [主要標頭檔](#_predir_the_primary_type_library_header_file)具有和類型程式庫相同的基底名稱，再加上 .TLH 副檔名。  次要標頭檔具有和類型程式庫相同的基底名稱，再加上 .TLI 副檔名。  它包含編譯器產生的成員函式的實作，而且已在主要標頭檔中包含 \(`#include`\)。  
  
 如果匯入使用 byref 參數的 dispinterface 屬性，\#import 不會產生函式的 \_\_declspec\([property](../cpp/property-cpp.md)\) 陳述式。  
  
 這兩個標頭檔會放置在 \/Fo \(為目的檔命名\) 選項指定的輸出目錄中。  編譯器接著會讀取並編譯這些檔案，就如同主要標頭檔是以 `#include` 指示詞所命名。  
  
 下列編譯器最佳化可搭配 `#import` 指示詞進行：  
  
-   標頭檔在建立時會獲得與類型程式庫相同的時間戳記。  
  
-   當處理 `#import` 時，編譯器會先檢查標頭是否存在以及是否為最新狀態。  如果是，就不需要重新建立。  
  
 `#import` 指示詞也會參與最少的重建，而且可以放置在先行編譯標頭檔中。  如需詳細資訊，請參閱[建立先行編譯標頭檔](../build/reference/creating-precompiled-header-files.md)。  
  
###  <a name="_predir_the_primary_type_library_header_file"></a> 主要類型程式庫標頭檔  
 主要類型程式庫標頭檔包含七個區段：  
  
-   標題重複使用區段：包含註解、COMDEF.H 的 `#include` 陳述式 \(會定義標題中使用的一些標準巨集\)，以及其他設定資訊。  
  
-   向前參考和 typedef：包含結構宣告，例如 `struct IMyInterface` 和 Typedef。  
  
-   智慧型指標宣告：樣板類別 `_com_ptr_t` 是封裝介面指標的智慧型指標實作，不需要呼叫 `AddRef`、**Release**、`QueryInterface` 函式。  此外，還會在建立新的 COM 物件時隱藏 `CoCreateInstance` 呼叫。  本節使用巨集陳述式 **\_COM\_SMARTPTR\_TYPEDEF**，將 COM 介面的 typedef 建立成為 [\_com\_ptr\_t](../cpp/com-ptr-t-class.md) 樣板類別的樣板特製化。  例如，對於介面 **IMyInterface**，.TLH 檔案會包含：  
  
    ```  
    _COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));  
    ```  
  
     編譯器將展開為：  
  
    ```  
    typedef _com_ptr_t<_com_IIID<IMyInterface, __uuidof(IMyInterface)> > IMyInterfacePtr;  
    ```  
  
     然後就可以將類型 `IMyInterfacePtr` 用來取代原始介面指標 `IMyInterface*`。  因此，不需要呼叫各種 **IUnknown** 成員函式  
  
-   Typeinfo 宣告：主要包含會公開 **ITypeLib:GetTypeInfo** 所傳回之個別 typeinfo 項目的類別定義及其他項目。  在本節中，類型程式庫中的每個 typeinfo 會反映在相依於 `TYPEKIND` 資訊之表單的標頭中。  
  
-   選擇性舊樣式 GUID 定義：包含具名 GUID 常數的初始化。  名稱的形式分為 **CLSID\_CoClass** 和 **IID\_Interface**，類似於 MIDL 編譯器產生的那些名稱。  
  
-   次要類型程式庫標頭的 `#include` 陳述式。  
  
-   頁尾重複使用區段：目前包含 `#pragma pack(pop)`。  
  
 除了標題重複使用和頁尾重複使用區段之外，所有其他區段部分都會放在命名空間中，由原始 IDL 檔案中的 **library** 陳述式指定命名空間名稱。  您可以明確限定命名空間或包含下列陳述式，來使用類型程式庫標頭中的名稱：  
  
```  
using namespace MyLib;  
```  
  
 緊接在原始程式碼的 `#import` 陳述式之後。  
  
 命名空間可以使用 `#import` 指示詞的 [no\_namespace](#_predir_no_namespace) 屬性來隱藏。  不過，隱藏命名空間可能導致名稱衝突。  命名空間也可以透過 [rename\_namespace](#_predir_rename_namespace) 屬性重新命名。  
  
 編譯器會提供其目前處理中類型程式庫所需之任何類型程式庫相依性的完整路徑。  路徑會以註解的形式寫入類型程式庫標頭 \(.TLH\)，編譯器為每個處理過的類型程式庫產生此標頭。  
  
 如果類型程式庫包含定義於其他類型程式庫之類型的參考，則 .TLH 檔案會包含下列排序的註解：  
  
```  
//  
// Cross-referenced type libraries:  
//  
//  #import "c:\path\typelib0.tlb"  
//  
```  
  
 `#import` 註解中的實際檔名是交互參考類型程式庫的完整路徑，存放在登錄中。  如果因為遺漏類型定義而發生錯誤，請檢查 .TLH 頂端的註解，以查看哪個相依類型程式庫可能需要先匯入。  編譯 .TLI 檔案時，可能發生的錯誤為語法錯誤 \(例如，C2143、C2146、C2321\)、C2501 \(遺漏 decl 指定名稱\) 或 C2433 \(資料宣告不允許「內嵌」\)。  
  
 您必須判斷哪些相依性註解是系統標頭沒有提供的，然後在相依類型程式庫的 `#import` 指示詞之前的某個位置提供 `#import` 指示詞以解決錯誤。  
  
 如需詳細資訊，請參閱知識庫文件＜\#import 包裝函式方法可能造成存取違規＞\(Q242527\) 或＜當您使用 XML 與 \#import 時發生編譯器錯誤＞\(Q269194\)。  您可以在 MSDN Library 媒體或是在 [http:\/\/support.microsoft.com\/support\/](http://support.microsoft.com/support/) 找到知識庫文件。  
  
##  <a name="_predir_the_23import_directive_import_attributes"></a> \#import 屬性  
 `#import` 可以選擇性地包含一個或多個屬性。  這些屬性會指示編譯器修改類型程式庫標頭的內容。  反斜線 \(**\\**\) 符號可用來在單一 `#import` 陳述式包含其他行。  例如：  
  
```  
#import "test.lib" no_namespace \  
   rename("OldName", "NewName")  
```  
  
 如需詳細資訊，請參閱 [\#import 屬性](../preprocessor/hash-import-attributes-cpp.md)。  
  
 **END C\+\+ 特定的**  
  
## 請參閱  
 [前置處理器指示詞](../preprocessor/preprocessor-directives.md)   
 [編譯器 COM 支援](../cpp/compiler-com-support.md)