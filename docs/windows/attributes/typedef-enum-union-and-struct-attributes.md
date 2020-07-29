---
title: Typedef、Enum、Union 和 Struct 屬性（c + + COM）
ms.date: 10/02/2018
helpviewer_keywords:
- union attributes
- attributes [C++/CLI], reference topics
ms.assetid: f8a4fe94-dc02-4aed-bc31-3e500d42f4c7
ms.openlocfilehash: 5e9eccd5e4464e92757d6dd78dd0f5187372ea3e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222104"
---
# <a name="typedef-enum-union-and-struct-attributes"></a>Typedef、Enum、Union 和 Struct 屬性

下列屬性適用于[typedef](../../cpp/aliases-and-typedefs-cpp.md)、 [struct](../../cpp/struct-cpp.md)和[enum](../../cpp/enumerations-cpp.md) c + + 關鍵字。

### <a name="typedef"></a>typedef

|屬性|說明|
|---------------|-----------------|
|[例圖](case-cpp.md)|與中的[switch_type](switch-type.md)屬性搭配使用 **`union`** 。|
|[客戶](custom-cpp.md)|可讓您定義自己的屬性。|
|[進出口](export.md)|導致將資料結構放在 .idl 檔案中。|
|[first_is](first-is.md)|指定要傳送之第一個陣列元素的索引。|
|[helpcontext](helpcontext.md)|指定內容識別碼，讓使用者可在說明檔中查看此元素的相關資訊。|
|[helpfile](helpfile.md)|設定類型程式庫的說明檔名稱。|
|[helpstring](helpstring.md)|指定用來描述所套用之項目的字元字串。|
|[library_block](library-block.md)|將結構放在 .idl 檔案的程式庫區塊內。|
|[ptr](ptr.md)|將指標指定為完整指標。|
|[public](public-cpp-attributes.md)|確保 typedef 會進入型別程式庫，即使它不是從 .idl 檔案中參考也一樣。|
|[ref](ref-cpp.md)|識別參考指標。|
|[switch_is](switch-is.md)|指定作為 union 判別的運算式或識別碼，以選取聯集成員。|
|[switch_type](switch-type.md)|識別用來做為聯集判別之變數的類型。|
|[unique](unique-cpp.md)|指定唯一的指標。|
|[wire_marshal](wire-marshal.md)|指定將用於傳輸的資料類型，而不是應用程式特定的資料類型。|

### <a name="enum"></a>列舉

|屬性|說明|
|---------------|-----------------|
|[客戶](custom-cpp.md)|可讓您定義自己的屬性。|
|[進出口](export.md)|導致將資料結構放在 .idl 檔案中。|
|[uuid](uuid-cpp-attributes.md)|指定類別或介面的唯一識別碼。|
|[v1_enum](v1-enum.md)|指示指定的列舉型別會以32位實體的形式傳送，而不是16位的預設值。|

### <a name="union"></a>union

|屬性|說明|
|---------------|-----------------|
|[客戶](custom-cpp.md)|可讓您定義自己的屬性。|
|[進出口](export.md)|導致將資料結構放在 .idl 檔案中。|
|[first_is](first-is.md)|指定要傳送之第一個陣列元素的索引。|
|[last_is](last-is.md)|指定要傳送之最後一個陣列元素的索引。|
|[length_is](length-is.md)|指定要傳送的陣列元素數目。|
|[max_is](max-is.md)|指定有效陣列索引的最大值。|
|[size_is](size-is.md)|指定配置給大小指標的記憶體大小、大小指標的大小指標，以及單一或多維陣列。|
|[unique](unique-cpp.md)|指定唯一的指標。|
|[uuid](uuid-cpp-attributes.md)|指定類別或介面的唯一識別碼。|

### <a name="nonencapsulated-union"></a>Nonencapsulated 聯集

|屬性|說明|
|---------------|-----------------|
|[ms_union](ms-union.md)|控制 nonencapsulated 等位的網路資料標記法對齊。|
|[no_injected_text](no-injected-text.md)|防止編譯器插入程式碼做為屬性使用的結果。|

### <a name="struct"></a>struct

|屬性|說明|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|表示類別支援匯總。|
|[總計](aggregates.md)|表示控制項會匯總目標類別。|
|[appobject](appobject.md)|將 coclass 識別為與完整 .exe 應用程式相關聯的應用程式物件，並指出 coclass 的函式和屬性在此類型程式庫中可全域使用。|
|[coclass](coclass.md)|建立 ActiveX 控制項。|
|[com_interface_entry](com-interface-entry-cpp.md)|將介面專案加入至 COM 對應。|
|[control](control.md)|指定使用者定義型別為控制項。|
|[客戶](custom-cpp.md)|可讓您定義自己的屬性。|
|[db_column](db-column.md)|將指定的資料行系結至資料列集。|
|[db_command](db-command.md)|建立 OLE DB 命令。|
|[db_param](db-param.md)|將指定的成員變數與輸入或輸出參數產生關聯，並分隔變數。|
|[db_source](db-source.md)|建立與資料來源的連接。|
|[db_table](db-table.md)|開啟 OLE DB 資料表。|
|[預設值](default-cpp.md)|表示 coclass 內定義的自訂或 dispinterface，用以代表預設可程式性介面。|
|[defaultvtable](defaultvtable.md)|將介面定義為控制項的預設 vtable 介面。|
|[event_receiver](event-receiver.md)|建立事件接收器。|
|[event_source](event-source.md)|建立事件來源。|
|[進出口](export.md)|導致將資料結構放在 .idl 檔案中。|
|[first_is](first-is.md)|指定要傳送之第一個陣列元素的索引。|
|[隱含](hidden.md)|表示專案存在，但不應該顯示在使用者導向的瀏覽器中。|
|[implements_category](implements-category.md)|指定類別的實作為元件類別。|
|[last_is](last-is.md)|指定要傳送之最後一個陣列元素的索引。|
|[length_is](length-is.md)|指定要傳送的陣列元素數目。|
|[max_is](max-is.md)|指定有效陣列索引的最大值。|
|[requires_category](requires-category.md)|指定目標類別所需的元件類別。|
|[size_is](size-is.md)|指定配置給大小指標的記憶體大小、大小指標的大小指標，以及單一或多維陣列。|
|[source](source-cpp.md)|在類別上，為連接點指定 COM 物件的來源介面。 在屬性或方法上，表示成員會傳回屬於事件來源的物件或 VARIANT。|
|[處理](threading-cpp.md)|指定 COM 物件的執行緒模型。|
|[unique](unique-cpp.md)|指定唯一的指標。|
|[uuid](uuid-cpp-attributes.md)|指定類別或介面的唯一識別碼。|
|[version](version-cpp.md)|識別類別的多個版本之間的特定版本。|
|[vi_progid](vi-progid.md)|指定與版本無關的 ProgID 形式。|

## <a name="see-also"></a>另請參閱

[依使用量的屬性](attributes-by-usage.md)
