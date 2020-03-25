---
title: 獨立屬性（C++ COM）
ms.date: 10/02/2018
helpviewer_keywords:
- standalone attributes
- attributes [C++/CLI], standalone
ms.assetid: 0d72e84e-236c-43b3-ac9a-d9b91fcd6794
ms.openlocfilehash: a7df91bbb1c6929b08d8cd867be9f13ce0c35b91
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166163"
---
# <a name="stand-alone-attributes"></a>獨立屬性

獨立屬性不會在C++關鍵字上運作，而是比較像一行程式碼。 獨立的屬性語句在行尾需要分號。

## <a name="stand-alone-attribute-list"></a>獨立屬性清單

|屬性|描述|
|---------------|-----------------|
|[cpp_quote](cpp-quote.md)|將指定的字串（不含引號字元）發出到產生的標頭檔中。|
|[custom](custom-cpp.md)|可讓您定義自己的屬性。|
|[db_command](db-command.md)|建立 OLE DB 命令。|
|[emitidl](emitidl.md)|判斷是否要處理所有後續的 IDL 屬性，並將其放在產生的 .idl 檔案中。|
|[idl_module](idl-module.md)|指定 DLL 中的進入點。|
|[idl_quote](idl-quote.md)|可讓您使用目前版本的 Visual C++中不支援的 IDL 結構，並將它們傳遞至產生的 .idl 檔案。|
|[import](import.md)|指定另一個 .idl、. odl 或 .h 檔案，其中包含您想要從主要 .idl 檔案參考的定義。|
|[importidl](importidl.md)|將指定的 .idl 檔案插入產生的 .idl 檔案中|
|[importlib](importlib.md)|讓已編譯成其他類型程式庫的類型可供正在建立的類型程式庫使用。|
|[include](include-cpp.md)|指定要包含在產生的 .idl 檔案中的一或多個標頭檔。|
|[includelib](includelib-cpp.md)|導致 .idl 或 .h 檔案包含在產生的 .idl 檔案中。|
|[library_block](library-block.md)|將結構放在 .idl 檔案的程式庫區塊內。|
|[name](module-cpp.md)|在 .idl 檔案中定義程式庫區塊。|
|[no_injected_text](no-injected-text.md)|防止編譯器插入程式碼做為屬性使用的結果。|
|[pragma](pragma.md)|將指定的字串（不含引號字元）發出到產生的 .idl 檔案。|

## <a name="see-also"></a>另請參閱

[依使用方式分類的屬性](attributes-by-usage.md)
