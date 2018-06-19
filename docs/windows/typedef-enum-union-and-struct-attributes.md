---
title: Typedef、 Enum、 Union 和 Struct 屬性 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- union attributes
- attributes [C++], reference topics
- struct attributes
- typedef attributes
- enum attributes
ms.assetid: f8a4fe94-dc02-4aed-bc31-3e500d42f4c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c14881afd000dc5fb4223a2ecfa9dcdc67e7b541
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891827"
---
# <a name="typedef-enum-union-and-struct-attributes"></a>Typedef、Enum、Union 和 Struct 屬性
下列屬性套用至[typedef](http://msdn.microsoft.com/en-us/cc96cf26-ba93-4179-951e-695d1f5fdcf1)，[結構](../cpp/struct-cpp.md)，和[列舉](../cpp/enumerations-cpp.md)c + + 關鍵字。  
  
### <a name="typedef"></a>typedef  
  
|屬性|描述|  
|---------------|-----------------|  
|[case](../windows/case-cpp.md)|搭配[switch_type](../windows/switch-type.md)屬性**union**。|  
|[custom](../windows/custom-cpp.md)|可讓您定義您自己的屬性。|  
|[export](../windows/export.md)|會導致資料結構，以便放入.idl 檔案。|  
|[first_is](../windows/first-is.md)|指定要傳送的第一個陣列元素的索引。|  
|[helpcontext](../windows/helpcontext.md)|指定的內容識別碼，可讓使用者檢視的說明檔中此項目有關的資訊。|  
|[helpfile](../windows/helpfile.md)|設定型別程式庫的說明檔的名稱。|  
|[helpstring](../windows/helpstring.md)|指定的字元字串，用來描述它所套用的項目。|  
|[library_block](../windows/library-block.md)|將.idl 檔案的程式庫區塊內的建構。|  
|[ptr](../windows/ptr.md)|將指標指定為完整的指標。|  
|[public](../windows/public-cpp-attributes.md)|可確保 typedef 將移到型別程式庫，即使它並未參考從.idl 檔中。|  
|[ref](../windows/ref-cpp.md)|識別參考指標。|  
|[switch_is](../windows/switch-is.md)|指定的運算式或做為選取的等位成員的聯集判別識別項。|  
|[switch_type](../windows/switch-type.md)|識別做為等位的判別變數的類型。|  
|[unique](../windows/unique-cpp.md)|指定唯一的指標。|  
|[wire_marshal](../windows/wire-marshal.md)|指定用於傳輸，而不是應用程式特定資料類型的資料類型。|  
  
### <a name="enum"></a>enum  
  
|屬性|描述|  
|---------------|-----------------|  
|[custom](../windows/custom-cpp.md)|可讓您定義您自己的屬性。|  
|[export](../windows/export.md)|會導致資料結構，以便放入.idl 檔案。|  
|[uuid](../windows/uuid-cpp-attributes.md)|指定類別或介面的唯一識別碼。|  
|[v1_enum](../windows/v1-enum.md)|指示指定的列舉的類型傳輸為 32 位元的實體，而不是 16 位元的預設值。|  
  
### <a name="union"></a>union  
  
|屬性|描述|  
|---------------|-----------------|  
|[custom](../windows/custom-cpp.md)|可讓您定義您自己的屬性。|  
|[export](../windows/export.md)|會導致資料結構，以便放入.idl 檔案。|  
|[first_is](../windows/first-is.md)|指定要傳送的第一個陣列元素的索引。|  
|[last_is](../windows/last-is.md)|指定要傳送的最後一個陣列元素的索引。|  
|[length_is](../windows/length-is.md)|指定要傳送的陣列元素數目。|  
|[max_is](../windows/max-is.md)|指定有效的陣列索引的最大值。|  
|[size_is](../windows/size-is.md)|指定的記憶體大小配置大小的指標，調整大小的指標和單一或多維度陣列的指標。|  
|[unique](../windows/unique-cpp.md)|指定唯一的指標。|  
|[uuid](../windows/uuid-cpp-attributes.md)|指定類別或介面的唯一識別碼。|  
  
### <a name="nonencapsulated-union"></a>Nonencapsulated 等位  
  
|屬性|描述|  
|---------------|-----------------|  
|[ms_union](../windows/ms-union.md)|控制 nonencapsulated 等位的網路資料表示對齊方式。|  
|[no_injected_text](../windows/no-injected-text.md)|防止編譯器插入程式碼，因為屬性使用。|  
  
### <a name="struct"></a>struct  
  
|屬性|描述|  
|---------------|-----------------|  
|[aggregatable](../windows/aggregatable.md)|表示此類別支援彙總。|  
|[aggregates](../windows/aggregates.md)|表示控制項彙總的目標類別。|  
|[appobject](../windows/appobject.md)|識別為的應用程式物件，其完整的.exe 應用程式相關聯，並指出函式和 coclass 的屬性都是全域使用這個類型程式庫的 coclass。|  
|[coclass](../windows/coclass.md)|建立 ActiveX 控制項。|  
|[com_interface_entry](../windows/com-interface-entry-cpp.md)|將介面項目加入至 COM 對應。|  
|[control](../windows/control.md)|指定使用者定義型別是控制項。|  
|[custom](../windows/custom-cpp.md)|可讓您定義您自己的屬性。|  
|[db_column](../windows/db-column.md)|將指定之資料行繫結至資料列集。|  
|[db_command](../windows/db-command.md)|建立 OLE DB 命令。|  
|[db_param](../windows/db-param.md)|關聯的輸入或輸出參數中指定的成員變數，分隔的變數。|  
|[db_source](../windows/db-source.md)|建立資料來源的連接。|  
|[db_table](../windows/db-table.md)|開啟 OLE DB 資料表。|  
|[default](../windows/default-cpp.md)|表示 coclass 內定義的自訂或 dispinterface，用以代表預設可程式性介面。|  
|[defaultvtable](../windows/defaultvtable.md)|為控制項的預設 vtable 介面定義的介面。|  
|[event_receiver](../windows/event-receiver.md)|建立事件接收器。|  
|[event_source](../windows/event-source.md)|建立事件來源。|  
|[export](../windows/export.md)|會導致資料結構，以便放入.idl 檔案。|  
|[first_is](../windows/first-is.md)|指定要傳送的第一個陣列元素的索引。|  
|[hidden](../windows/hidden.md)|表示項目存在，但不是會顯示在使用者導向的瀏覽器中。|  
|[implements_category](../windows/implements-category.md)|指定此類別實作的元件類別。|  
|[last_is](../windows/last-is.md)|指定要傳送的最後一個陣列元素的索引。|  
|[length_is](../windows/length-is.md)|指定要傳送的陣列元素數目。|  
|[max_is](../windows/max-is.md)|指定有效的陣列索引的最大值。|  
|[requires_category](../windows/requires-category.md)|指定目標類別的必要的元件類別目錄。|  
|[size_is](../windows/size-is.md)|指定的記憶體大小配置大小的指標，調整大小的指標和單一或多維度陣列的指標。|  
|[來源](../windows/source-cpp.md)|在類別上指定的連接點的 COM 物件的來源介面。 在屬性或方法中，會指出成員傳回的物件或為資料來源的事件的 VARIANT。|  
|[執行緒處理](../windows/threading-cpp.md)|指定 COM 物件的執行緒模型。|  
|[unique](../windows/unique-cpp.md)|指定唯一的指標。|  
|[uuid](../windows/uuid-cpp-attributes.md)|指定類別或介面的唯一識別碼。|  
|[version](../windows/version-cpp.md)|識別類別的多個版本之間的特定版本。|  
|[vi_progid](../windows/vi-progid.md)|指定版本無關的 ProgID 的表單。|  
  
## <a name="see-also"></a>另請參閱  
 [依使用方式分類的屬性](../windows/attributes-by-usage.md)