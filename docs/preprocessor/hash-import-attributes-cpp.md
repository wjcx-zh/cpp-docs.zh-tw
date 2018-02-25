---
title: "#匯入屬性 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- '#import directive, attributes'
ms.assetid: 2a5085e3-82ee-4f83-892b-0aa6cc13863b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 76507ef9d840b9d3544442af2881810d715bd4ca
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="import-attributes-c"></a>#import 屬性 (C++)
提供搭配 #import 指示詞使用之屬性的連結。  
  
 **Microsoft 特定的**  
  
 下列屬性可供 #import 指示詞使用。  
  
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
|[named_guids](../preprocessor/named-guids.md)|告知編譯器来定義和初始化 GUID 變數中表單的舊樣式**LIBID_MyLib**， **CLSID_MyCoClass**， **IID_MyInterface**，和**DIID_MyDispInterface**。|  
|[no_auto_exclude](../preprocessor/no-auto-exclude.md)|停用自動排除。|  
|[no_dual_interfaces](../preprocessor/no-dual-interfaces.md)|變更編譯器產生雙重介面方法之包裝函式的方式。|  
|[no_implementation](../preprocessor/no-implementation.md)|不產生 .tli 標頭，其中包含包裝函式成員函式的實作。|  
|[no_namespace](../preprocessor/no-namespace.md)|指定命名空間名稱不是由編譯器產生。|  
|[no_registry](../preprocessor/no-registry.md)|告知編譯器不要搜尋類型程式庫的登錄。|  
|[no_search_namespace](../preprocessor/no-search-namespace.md)|具有相同的功能為[no_namespace](../preprocessor/no-namespace.md)屬性，但適用於使用 #import 指示詞中的型別程式庫[auto_search](../preprocessor/auto-search.md)屬性。|  
|[no_smart_pointers](../preprocessor/no-smart-pointers.md)|不為類型程式庫中的所有介面建立智慧型指標。|  
|[raw_dispinterfaces](../preprocessor/raw-dispinterfaces.md)|告知編譯器產生低階包裝函式呼叫的分配介面方法和屬性**idispatch:: Invoke**並傳回`HRESULT`錯誤碼。|  
|[raw_interfaces_only](../preprocessor/raw-interfaces-only.md)|隱藏的錯誤處理的包裝函式產生和[屬性](../cpp/property-cpp.md)使用這些包裝函式的宣告。|  
|[raw_method_prefix](../preprocessor/raw-method-prefix.md)|指定不同的前置詞，避免發生名稱衝突。|  
|[raw_native_types](../preprocessor/raw-native-types.md)|停用在高階包裝函式中使用 COM 支援類別，並強制改用低階資料類型。|  
|[raw_property_prefixes](../preprocessor/raw-property-prefixes.md)|為三個屬性方法指定替代的前置詞。|  
|[rename](../preprocessor/rename-hash-import.md)|解決名稱衝突問題。|  
|[rename_namespace](../preprocessor/rename-namespace.md)|將包含類型程式庫內容的命名空間重新命名。|  
|[rename_search_namespace](../preprocessor/rename-search-namespace.md)|具有相同的功能為[rename_namespace](../preprocessor/rename-namespace.md)屬性，但適用於使用 #import 指示詞中的型別程式庫[auto_search](../preprocessor/auto-search.md)屬性。|  
|[tlbid](../preprocessor/tlbid.md)|允許載入主要類型程式庫以外的程式庫。|  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [#import 指示詞](../preprocessor/hash-import-directive-cpp.md)