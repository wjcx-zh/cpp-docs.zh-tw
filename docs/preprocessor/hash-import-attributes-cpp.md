---
title: '#import 屬性 (C++)'
ms.date: 08/29/2019
helpviewer_keywords:
- '#import directive, attributes'
ms.assetid: 2a5085e3-82ee-4f83-892b-0aa6cc13863b
ms.openlocfilehash: fc2af69025d47a9ea6cea0e2c9e1423151b01606
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215289"
---
# <a name="import-attributes-c"></a>#import 屬性（C++）

提供與 `#import` 指示詞搭配使用之屬性的連結。

**Microsoft 專屬**

下列屬性可供 `#import` 指示詞使用。

|屬性|描述|
|---------------|-----------------|
|[auto_rename](../preprocessor/auto-rename.md)|藉由對變數名稱附加兩個底線 (__) 來重新命名 C++ 保留字，以解決可能發生的名稱衝突。|
|[auto_search](../preprocessor/auto-search.md)|指定時，當類型程式庫是使用 #import 加以參考，而且其本身參考又另一個類型程式庫，則編譯器可以對另一個類型程式庫執行隱含的 #import。|
|[embedded_idl](../preprocessor/embedded-idl.md)|指定類型程式庫將寫入 .tlh 檔，並保留屬性產生的程式碼。|
|[排除](../preprocessor/exclude-hash-import.md)|排除從類型程式庫標頭檔產生的項目。|
|[high_method_prefix](../preprocessor/high-method-prefix.md)|指定用來命名高階屬性和方法的前置詞。|
|[high_property_prefixes](../preprocessor/high-property-prefixes.md)|為三個屬性方法指定替代的前置詞。|
|[implementation_only](../preprocessor/implementation-only.md)|不產生 .tlh 標頭檔 (主要標頭檔)。|
|[include()](../preprocessor/include-parens.md)|停用自動排除。|
|[inject_statement](../preprocessor/inject-statement.md)|將其做為來源文字的引數插入至類型程式庫標題。|
|[named_guids](../preprocessor/named-guids.md)|告訴編譯器以舊樣式定義和初始化 GUID 變數，格式為 `LIBID_MyLib`、`CLSID_MyCoClass`、`IID_MyInterface`和 `DIID_MyDispInterface`。|
|[no_auto_exclude](../preprocessor/no-auto-exclude.md)|停用自動排除。|
|[no_dual_interfaces](../preprocessor/no-dual-interfaces.md)|變更編譯器產生雙重介面方法之包裝函式的方式。|
|[no_implementation](../preprocessor/no-implementation.md)|不產生 .tli 標頭，其中包含包裝函式成員函式的實作。|
|[no_namespace](../preprocessor/no-namespace.md)|指定命名空間名稱不是由編譯器產生。|
|[no_registry](../preprocessor/no-registry.md)|告知編譯器不要搜尋類型程式庫的登錄。|
|[no_search_namespace](../preprocessor/no-search-namespace.md)|具有與[no_namespace](../preprocessor/no-namespace.md)屬性相同的功能，但會在使用 #import 指示詞搭配[auto_search](../preprocessor/auto-search.md)屬性的類型程式庫上使用。|
|[no_smart_pointers](../preprocessor/no-smart-pointers.md)|不為類型程式庫中的所有介面建立智慧型指標。|
|[raw_dispinterfaces](../preprocessor/raw-dispinterfaces.md)|告知編譯器針對會呼叫 `IDispatch::Invoke` 並傳回 HRESULT 錯誤碼的分派介面方法和屬性，產生低層級的包裝函式。|
|[raw_interfaces_only](../preprocessor/raw-interfaces-only.md)|抑制產生錯誤處理包裝函式，以及使用這些包裝函數的[屬性](../cpp/property-cpp.md)宣告。|
|[raw_method_prefix](../preprocessor/raw-method-prefix.md)|指定不同的前置詞，避免發生名稱衝突。|
|[raw_native_types](../preprocessor/raw-native-types.md)|停用在高階包裝函式中使用 COM 支援類別，並強制改用低階資料類型。|
|[raw_property_prefixes](../preprocessor/raw-property-prefixes.md)|為三個屬性方法指定替代的前置詞。|
|[rename](../preprocessor/rename-hash-import.md)|解決名稱衝突問題。|
|[rename_namespace](../preprocessor/rename-namespace.md)|將包含類型程式庫內容的命名空間重新命名。|
|[rename_search_namespace](../preprocessor/rename-search-namespace.md)|具有與[rename_namespace](../preprocessor/rename-namespace.md)屬性相同的功能，但會在使用 #import 指示詞搭配[auto_search](../preprocessor/auto-search.md)屬性的類型程式庫上使用。|
|[tlbid](../preprocessor/tlbid.md)|允許載入主要類型程式庫以外的程式庫。|

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)
