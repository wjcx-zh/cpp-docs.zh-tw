---
title: "#import 屬性 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#import 指示詞, 屬性"
ms.assetid: 2a5085e3-82ee-4f83-892b-0aa6cc13863b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# #import 屬性 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

提供搭配 \#import 指示詞使用之屬性的連結。  
  
 **Microsoft 特定的**  
  
 下列屬性可供 \#import 指示詞使用。  
  
|屬性|說明|  
|--------|--------|  
|[auto\_rename](../preprocessor/auto-rename.md)|藉由對變數名稱附加兩個底線 \(\_\_\) 來重新命名 C\+\+ 保留字，以解決可能發生的名稱衝突。|  
|[auto\_search](../preprocessor/auto-search.md)|指定時，當類型程式庫是使用 \#import 加以參考，而且其本身參考又另一個類型程式庫，則編譯器可以對另一個類型程式庫執行隱含的 \#import。|  
|[embedded\_idl](../preprocessor/embedded-idl.md)|指定類型程式庫將寫入 .tlh 檔，並保留屬性產生的程式碼。|  
|[exclude](../preprocessor/exclude-hash-import.md)|排除從類型程式庫標頭檔產生的項目。|  
|[high\_method\_prefix](../preprocessor/high-method-prefix.md)|指定用來命名高階屬性和方法的前置詞。|  
|[high\_property\_prefixes](../preprocessor/high-property-prefixes.md)|為三個屬性方法指定替代的前置詞。|  
|[implementation\_only](../preprocessor/implementation-only.md)|不產生 .tlh 標頭檔 \(主要標頭檔\)。|  
|[include\(\)](../preprocessor/include-parens.md)|停用自動排除。|  
|[inject\_statement](../preprocessor/inject-statement.md)|將其做為來源文字的引數插入至類型程式庫標題。|  
|[named\_guids](../preprocessor/named-guids.md)|告知編譯器以 **LIBID\_MyLib**、**CLSID\_MyCoClass**、**IID\_MyInterface** 和 **DIID\_MyDispInterface** 形式的舊樣式定義和初始化 GUID 變數。|  
|[no\_auto\_exclude](../preprocessor/no-auto-exclude.md)|停用自動排除。|  
|[no\_dual\_interfaces](../preprocessor/no-dual-interfaces.md)|變更編譯器產生雙重介面方法之包裝函式的方式。|  
|[no\_implementation](../preprocessor/no-implementation.md)|不產生 .tli 標頭，其中包含包裝函式成員函式的實作。|  
|[no\_namespace](../preprocessor/no-namespace.md)|指定命名空間名稱不是由編譯器產生。|  
|[no\_registry](../preprocessor/no-registry.md)|告知編譯器不要搜尋類型程式庫的登錄。|  
|[no\_search\_namespace](../preprocessor/no-search-namespace.md)|與 [no\_namespace](../preprocessor/no-namespace.md) 屬性具有相同功能，但是會在您使用 \#import 指示詞搭配 [auto\_search](../preprocessor/auto-search.md) 屬性的類型程式庫上使用。|  
|[no\_smart\_pointers](../preprocessor/no-smart-pointers.md)|不為類型程式庫中的所有介面建立智慧型指標。|  
|[raw\_dispinterfaces](../preprocessor/raw-dispinterfaces.md)|告知編譯器為呼叫 **IDispatch::Invoke** 並傳回 `HRESULT` 錯誤碼的分配介面 \(Dispinterface\) 方法和屬性產生低階包裝函式。|  
|[raw\_interfaces\_only](../preprocessor/raw-interfaces-only.md)|不產生錯誤處理包裝函式以及使用這些包裝函式的 [property](../cpp/property-cpp.md) 宣告。|  
|[raw\_method\_prefix](../preprocessor/raw-method-prefix.md)|指定不同的前置詞，避免發生名稱衝突。|  
|[raw\_native\_types](../preprocessor/raw-native-types.md)|停用在高階包裝函式中使用 COM 支援類別，並強制改用低階資料類型。|  
|[raw\_property\_prefixes](../preprocessor/raw-property-prefixes.md)|為三個屬性方法指定替代的前置詞。|  
|[重新命名](../preprocessor/rename-hash-import.md)|解決名稱衝突問題。|  
|[rename\_namespace](../preprocessor/rename-namespace.md)|將包含類型程式庫內容的命名空間重新命名。|  
|[rename\_search\_namespace](../preprocessor/rename-search-namespace.md)|與 [rename\_namespace](../preprocessor/rename-namespace.md) 屬性具有相同功能，但是會在您使用 \#import 指示詞搭配 [auto\_search](../preprocessor/auto-search.md) 屬性的類型程式庫上使用。|  
|[tlbid](../preprocessor/tlbid.md)|允許載入主要類型程式庫以外的程式庫。|  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\#import 指示詞](../preprocessor/hash-import-directive-cpp.md)