---
title: 獨立屬性 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- standalone attributes
- attributes [C++], standalone
ms.assetid: 0d72e84e-236c-43b3-ac9a-d9b91fcd6794
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6562a1de8baa9a5805f044233b97bf8dd8840638
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42613754"
---
# <a name="stand-alone-attributes"></a>獨立屬性
獨立屬性不能進行 c + + 關鍵字，但更像是程式碼行。 獨立屬性陳述式需要行尾的分號。
  
|屬性|描述|
|---------------|-----------------|
|[cpp_quote](../windows/cpp-quote.md)|指定的字串，不能包含單引號字元，發出到產生的標頭檔。|
|[custom](../windows/custom-cpp.md)|可讓您定義您自己的屬性。|
|[db_command](../windows/db-command.md)|建立 OLE DB 命令。|
|[emitidl](../windows/emitidl.md)|決定是否將處理並放在所產生的.idl 檔案中所有後續的 IDL 屬性。|
|[idl_module](../windows/idl-module.md)|指定進入點 DLL 中。|
|[idl_quote](../windows/idl-quote.md)|可讓您使用目前版本的 Visual c + + 中不支援的 IDL 建構，並將它們傳遞至所產生的.idl 檔案。|
|[import](../windows/import.md)|指定另一個.idl、.odl 或.h 檔案包含您想要從主要的.idl 檔案中參考的定義。|
|[importidl](../windows/importidl.md)|指定的.idl 檔插入所產生的.idl 檔案|
|[importlib](../windows/importlib.md)|讓已編譯成其他類型程式庫的類型可供正在建立的類型程式庫使用。|
|[include](../windows/include-cpp.md)|指定要包含在產生的.idl 檔案中的一或多個標頭檔。|
|[includelib](../windows/includelib-cpp.md)|會導致的.idl 或.h 檔案要包含在產生的.idl 檔案中。|
|[library_block](../windows/library-block.md)|會建構的.idl 檔案的程式庫區塊內。|
|[模組](../windows/module-cpp.md)|在 .idl 檔案中定義程式庫區塊。|
|[no_injected_text](../windows/no-injected-text.md)|防止編譯器將程式碼，因為屬性使用。|
|[pragma](../windows/pragma.md)|指定的字串，不能包含單引號字元，發出到產生的.idl 檔案。|
  
## <a name="see-also"></a>另請參閱
 [依使用方式分類的屬性](../windows/attributes-by-usage.md)