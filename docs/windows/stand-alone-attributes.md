---
title: 獨立屬性 |Microsoft 文件
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
ms.openlocfilehash: 59846b1ca031cc02c85cb6ace23f96e8c5cc9f37
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="stand-alone-attributes"></a>獨立屬性
獨立屬性不能進行 c + + 關鍵字，但更像一行程式碼。 獨立屬性陳述式需要在行尾的分號。  
  
|屬性|描述|  
|---------------|-----------------|  
|[cpp_quote](../windows/cpp-quote.md)|指定的字串，不能包含引號字元，發出至產生的標頭檔。|  
|[custom](../windows/custom-cpp.md)|可讓您定義您自己的屬性。|  
|[db_command](../windows/db-command.md)|建立 OLE DB 命令。|  
|[emitidl](../windows/emitidl.md)|判斷是否會處理並放在產生的.idl 檔中所有後續的 IDL 屬性。|  
|[idl_module](../windows/idl-module.md)|指定的進入點 DLL 中。|  
|[idl_quote](../windows/idl-quote.md)|可讓您使用目前版本的 Visual c + + 中不支援的 IDL 建構函式，並將它們傳遞至產生的.idl 檔案。|  
|[import](../windows/import.md)|指定包含的定義您想要從主要的.idl 檔案參考的另一個.idl、.odl 或.h 檔案。|  
|[importidl](../windows/importidl.md)|指定的.idl 檔案插入產生的.idl 檔案|  
|[importlib](../windows/importlib.md)|讓已編譯成其他類型程式庫的類型可供正在建立的類型程式庫使用。|  
|[include](../windows/include-cpp.md)|指定要包含在產生的.idl 檔中的一個或多個標頭檔。|  
|[includelib](../windows/includelib-cpp.md)|會導致的.idl 或.h 檔案包含在產生的.idl 檔案。|  
|[library_block](../windows/library-block.md)|將.idl 檔案的程式庫區塊內的建構。|  
|[模組](../windows/module-cpp.md)|在 .idl 檔案中定義程式庫區塊。|  
|[no_injected_text](../windows/no-injected-text.md)|防止編譯器插入程式碼，因為屬性使用。|  
|[pragma](../windows/pragma.md)|指定的字串，不能包含引號字元，發出至產生的.idl 檔案。|  
  
## <a name="see-also"></a>另請參閱  
 [依使用方式分類的屬性](../windows/attributes-by-usage.md)