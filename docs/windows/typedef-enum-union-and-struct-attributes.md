---
title: "Typedef, Enum, Union, and Struct Attributes | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "union attributes"
  - "attributes [C++], reference topics"
  - "struct attributes"
  - "typedef attributes"
  - "enum attributes"
ms.assetid: f8a4fe94-dc02-4aed-bc31-3e500d42f4c7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Typedef, Enum, Union, and Struct Attributes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列屬性套用於 [typedef](http://msdn.microsoft.com/zh-tw/cc96cf26-ba93-4179-951e-695d1f5fdcf1)， [結構](../cpp/struct-cpp.md)，以及 [列舉](../cpp/enumerations-cpp.md) C\+\+ 關鍵字。  
  
### typedef  
  
|屬性|描述|  
|--------|--------|  
|[case](../windows/case-cpp.md)|搭配 [switch\_type](../windows/switch-type.md) 屬性上**等位**。|  
|[custom](../windows/custom-cpp.md)|讓您定義您自己的屬性。|  
|[export](../windows/export.md)|會造成.idl 檔內放置的資料結構。|  
|[first\_is](../windows/first-is.md)|指定要傳送的第一個陣列元素的索引。|  
|[helpcontext](../windows/helpcontext.md)|指定的主題代碼，可讓使用者檢視此說明檔中的項目相關的資訊。|  
|[說明檔案](../windows/helpfile.md)|設定型別程式庫的 \[說明\] 檔案名稱。|  
|[helpstring](../windows/helpstring.md)|指定用來描述所套用之項目的字元字串，|  
|[library\_block](../windows/library-block.md)|將.idl 檔案的媒體櫃區塊內的建構函式。|  
|[ptr](../windows/ptr.md)|指定變數的指標做為完整的指標。|  
|[public](../windows/public-cpp-attributes.md)|可確保 typedef 就會變為型別程式庫，即使它未被參考的.idl 檔內。|  
|[ref](../windows/ref-cpp.md)|識別的參考指標。|  
|[switch\_is](../windows/switch-is.md)|指定做為選取的聯集的成員聯集判別識別碼的運算式。|  
|[switch\_type](../windows/switch-type.md)|識別做為聯合判別變數的型別。|  
|[唯一](../windows/unique-cpp.md)|指定唯一的指標。|  
|[wire\_marshal](../windows/wire-marshal.md)|指定將用於傳輸，而不是應用程式特定資料型別的資料型別。|  
  
### enum  
  
|屬性|描述|  
|--------|--------|  
|[custom](../windows/custom-cpp.md)|讓您定義您自己的屬性。|  
|[export](../windows/export.md)|會造成.idl 檔內放置的資料結構。|  
|[uuid](../windows/uuid-cpp-attributes.md)|指定類別或介面的專一識別碼。|  
|[v1\_enum](../windows/v1-enum.md)|指示指定的列舉型別來傳輸為 32 位元實體，而不是 16 位元的預設值。|  
  
### union  
  
|屬性|描述|  
|--------|--------|  
|[custom](../windows/custom-cpp.md)|讓您定義您自己的屬性。|  
|[export](../windows/export.md)|會造成.idl 檔內放置的資料結構。|  
|[first\_is](../windows/first-is.md)|指定要傳送的第一個陣列元素的索引。|  
|[last\_is](../windows/last-is.md)|指定要傳送的最後一個陣列元素的索引。|  
|[length\_is](../windows/length-is.md)|指定要傳送的陣列元素數目。|  
|[max\_is](../windows/max-is.md)|請指定有效的陣列索引的最大值。|  
|[size\_is](../windows/size-is.md)|指定的記憶體大小配置大小的指標、 調整大小來調整大小的指標，以及單或多維陣列的指標。|  
|[唯一](../windows/unique-cpp.md)|指定唯一的指標。|  
|[uuid](../windows/uuid-cpp-attributes.md)|指定類別或介面的專一識別碼。|  
  
### Nonencapsulated 的聯集  
  
|屬性|描述|  
|--------|--------|  
|[ms\_union](../windows/ms-union.md)|控制網路資料表示對齊，nonencapsulated 的聯集。|  
|[no\_injected\_text](../windows/no-injected-text.md)|可以防止編譯器插入的屬性使用的程式碼。|  
  
### struct  
  
|屬性|描述|  
|--------|--------|  
|[可彙總](../windows/aggregatable.md)|指示此類別支援彙總。|  
|[彙總](../windows/aggregates.md)|表示控制項彙總的目標類別。|  
|[appobject](../windows/appobject.md)|識別做為應用程式物件，這是完整的.exe 應用程式相關聯，表示這個型別程式庫中的函式和 coclass 的屬性可使用全域 coclass。|  
|[coclass](../windows/coclass.md)|會建立 ActiveX 控制項。|  
|[com\_interface\_entry](../windows/com-interface-entry-cpp.md)|將介面項目加入至 COM 對應。|  
|[控制項](../windows/control.md)|指定的使用者定義型別是一種控制項。|  
|[custom](../windows/custom-cpp.md)|讓您定義您自己的屬性。|  
|[db\_column](../windows/db-column.md)|將指定的資料行繫結至資料列集。|  
|[db\_command](../windows/db-command.md)|建立 OLE DB 命令一樣。|  
|[db\_param](../windows/db-param.md)|將指定的成員變數以輸入或輸出參數相關聯，用來分隔的變數。|  
|[db\_source](../windows/db-source.md)|建立資料來源的連接。|  
|[db\_table](../windows/db-table.md)|OLE DB 表格會跚|  
|[default](../windows/default-cpp.md)|指示自訂或分配介面所定義的 coclass 代表預設的可程式化介面。|  
|[defaultvtable](../windows/defaultvtable.md)|控制項的預設 vtable 介面中定義的介面。|  
|[event\_receiver](../windows/event-receiver.md)|建立事件接收器。|  
|[event\_source](../windows/event-source.md)|建立事件來源。|  
|[export](../windows/export.md)|會造成.idl 檔內放置的資料結構。|  
|[first\_is](../windows/first-is.md)|指定要傳送的第一個陣列元素的索引。|  
|[hidden](../windows/hidden.md)|表示該項目存在，但不是會顯示在使用者導向的瀏覽器中。|  
|[implements\_category](../windows/implements-category.md)|指定實作的元件類別的類別目錄。|  
|[last\_is](../windows/last-is.md)|指定要傳送的最後一個陣列元素的索引。|  
|[length\_is](../windows/length-is.md)|指定要傳送的陣列元素數目。|  
|[max\_is](../windows/max-is.md)|請指定有效的陣列索引的最大值。|  
|[requires\_category](../windows/requires-category.md)|指定目標類別所需的元件類別的目錄。|  
|[size\_is](../windows/size-is.md)|指定的記憶體大小配置大小的指標、 調整大小來調整大小的指標，以及單或多維陣列的指標。|  
|[source](../windows/source-cpp.md)|在類別上指定的連接點的 COM 物件的來源介面。  在屬性或方法中，指出成員傳回一個物件或 VARIANT 是一個事件的來源。|  
|[執行緒處理](../windows/threading-cpp.md)|指定 COM 物件的執行緒模型。|  
|[唯一](../windows/unique-cpp.md)|指定唯一的指標。|  
|[uuid](../windows/uuid-cpp-attributes.md)|指定類別或介面的專一識別碼。|  
|[version](../windows/version-cpp.md)|識別類別的多個版本之間的特定版本。|  
|[vi\_progid](../windows/vi-progid.md)|指定版本無關的形式的 ProgID。|  
  
## 請參閱  
 [Attributes by Usage](../windows/attributes-by-usage.md)