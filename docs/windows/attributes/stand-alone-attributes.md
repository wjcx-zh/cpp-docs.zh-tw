---
title: 獨立屬性 (c + + COM)
ms.date: 10/02/2018
helpviewer_keywords:
- standalone attributes
- attributes [C++/CLI], standalone
ms.assetid: 0d72e84e-236c-43b3-ac9a-d9b91fcd6794
ms.openlocfilehash: 7dd1f35add3b23dbd81e32a1600481eec79fe7d7
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033053"
---
# <a name="stand-alone-attributes"></a>獨立屬性

獨立屬性不能進行 c + + 關鍵字，但更像是程式碼行。 獨立屬性陳述式需要行尾的分號。

## <a name="stand-alone-attribute-list"></a>獨立的屬性清單

|屬性|描述|
|---------------|-----------------|
|[cpp_quote](cpp-quote.md)|指定的字串，不能包含單引號字元，發出到產生的標頭檔。|
|[自訂](custom-cpp.md)|可讓您定義您自己的屬性。|
|[db_command](db-command.md)|建立 OLE DB 命令。|
|[emitidl](emitidl.md)|決定是否將處理並放在所產生的.idl 檔案中所有後續的 IDL 屬性。|
|[idl_module](idl-module.md)|指定進入點 DLL 中。|
|[idl_quote](idl-quote.md)|可讓您使用目前版本的 Visual c + + 中不支援的 IDL 建構，並將它們傳遞至所產生的.idl 檔案。|
|[import](import.md)|指定另一個.idl、.odl 或.h 檔案包含您想要從主要的.idl 檔案中參考的定義。|
|[importidl](importidl.md)|指定的.idl 檔插入所產生的.idl 檔案|
|[importlib](importlib.md)|讓已編譯成其他類型程式庫的類型可供正在建立的類型程式庫使用。|
|[include](include-cpp.md)|指定要包含在產生的.idl 檔案中的一或多個標頭檔。|
|[includelib](includelib-cpp.md)|會導致的.idl 或.h 檔案要包含在產生的.idl 檔案中。|
|[library_block](library-block.md)|會建構的.idl 檔案的程式庫區塊內。|
|[name](module-cpp.md)|在 .idl 檔案中定義程式庫區塊。|
|[no_injected_text](no-injected-text.md)|防止編譯器將程式碼，因為屬性使用。|
|[pragma](pragma.md)|指定的字串，不能包含單引號字元，發出到產生的.idl 檔案。|

## <a name="see-also"></a>另請參閱

[依使用方式分類的屬性](attributes-by-usage.md)