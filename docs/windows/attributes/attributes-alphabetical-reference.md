---
title: 依字母順序排列的屬性參考
ms.custom: index-page
ms.date: 10/02/2018
ms.topic: conceptual
f1_keywords:
- vc.attributes
helpviewer_keywords:
- attributes [C++/CLI]
ms.assetid: fb2216ef-9fbd-44f4-afed-732aa99450e2
ms.openlocfilehash: ad9ecd1e3b3d4620b1f862fd1d5d70ef050da48d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215331"
---
# <a name="attributes-alphabetical-reference"></a>依字母順序排列的屬性參考

下列屬性可用於 Microsoft c + + 編譯器：

|屬性|說明|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|表示控制項可以由另一個控制項匯總。|
|[總計](aggregates.md)|表示控制項會匯總目標類別。|
|[appobject](appobject.md)|將 coclass 識別為與完整 EXE 應用程式相關聯的應用程式物件，並指出 coclass 的函式和屬性在此類型程式庫中可全域使用。|
|[async_uuid](async-uuid.md)|指定 UUID，以指示 MIDL 編譯器定義 COM 介面的同步和非同步版本。|
|[特性](attribute.md)|可讓您建立自訂屬性。|
|[bindable](bindable.md)|表示支援資料繫結的屬性。|
|[call_as](call-as.md)|讓不可遠端處理函數能夠對應至遠端函式。|
|[例圖](case-cpp.md)|與聯集內的[switch_type](switch-type.md)屬性搭配使用。|
|[coclass](coclass.md)|建立可執行 COM 介面的 COM 物件。|
|[com_interface_entry](com-interface-entry-cpp.md)|將介面專案加入至 COM 對應。|
|[control](control.md)|指定使用者定義型別為控制項。|
|[cpp_quote](cpp-quote.md)|將指定的字串（不含引號字元）發出到產生的標頭檔中。|
|[客戶](custom-cpp.md)|可讓您定義自己的屬性。|
|[db_accessor](db-accessor.md)|系結資料列集中的資料行，並將其系結至對應的存取子對應。|
|[db_column](db-column.md)|將指定的資料行系結至資料列集。|
|[db_command](db-command.md)|執行 OLE DB 命令。|
|[db_param](db-param.md)|使指定的成員變數與輸入或輸出參數產生關聯。|
|[db_source](db-source.md)|透過提供者建立和封裝連接至資料來源。|
|[db_table](db-table.md)|開啟 OLE DB 資料表。|
|[預設值](default-cpp.md)|表示 coclass 內定義的自訂或 dispinterface，用以代表預設可程式性介面。|
|[defaultbind](defaultbind.md)|表示最能代表物件的單一可系結屬性。|
|[defaultcollelem](defaultcollelem.md)|用於 Visual Basic 程式碼優化。|
|[defaultvalue](defaultvalue.md)|允許指定具類型的選擇性參數的預設值。|
|[defaultvtable](defaultvtable.md)|將介面定義為控制項的預設 vtable 介面。|
|[dispinterface](dispinterface.md)|將介面放入 .idl 檔案中作為分派介面。|
|[displaybind](displaybind.md)|表示應該向使用者顯示為可系結的屬性。|
|[dual](dual.md)|將介面放在 .idl 檔案中，做為雙重介面。|
|[emitidl](emitidl.md)|判斷是否要處理所有後續的 IDL 屬性，並將其放在產生的 .idl 檔案中。|
|[上場](entry.md)|藉由識別 DLL 中的進入點，指定模組中匯出的函數或常數。|
|[event_receiver](event-receiver.md)|建立事件接收器。|
|[event_source](event-source.md)|建立事件來源。|
|[進出口](export.md)|導致將資料結構放在 .idl 檔案中。|
|[first_is](first-is.md)|指定要傳送之第一個陣列元素的索引。|
|[helpcontext](helpcontext.md)|指定內容識別碼，讓使用者可在說明檔中查看此元素的相關資訊。|
|[helpfile](helpfile.md)|設定類型程式庫的說明檔名稱。|
|[helpstring](helpstring.md)|在 .hlp 或 .chm 檔案中指定說明主題的識別碼。|
|[helpstringdll](helpstringdll.md)|指定要用來執行檔字串查閱（當地語系化）之 DLL 的名稱。|
|[隱含](hidden.md)|表示專案存在，但不應該顯示在使用者導向的瀏覽器中。|
|[id](id.md)|指定成員函式的 DISPID （屬性或方法，在介面或分配介面中）。|
|[idl_module](idl-module.md)|指定 DLL 中的進入點。|
|[idl_quote](idl-quote.md)|可讓您使用目前版本的 Visual C++ 中不支援的屬性或 IDL 結構。|
|[iid_is](iid-is.md)|指定介面指標所指向之 COM 介面的 IID。|
|[immediatebind](immediatebind.md)|表示資料庫將會在資料系結物件之屬性的所有變更時立即收到通知。|
|[實作](implements-cpp.md)|指定強制成為 IDL coclass 成員的分派介面。|
|[implements_category](implements-category.md)|指定類別的實作為元件類別。|
|[import](import.md)|指定另一個 .idl、. odl 或標頭檔，其中包含您想要從主要 .idl 檔案參考的定義。|
|[importidl](importidl.md)|將指定的 .idl 檔案插入產生的 .idl 檔案。|
|[importlib](importlib.md)|讓已編譯成其他類型程式庫的類型可供正在建立的類型程式庫使用。|
|[in](in-cpp.md)|表示參數會從呼叫程式傳遞至被呼叫的進程。|
|[涉及](include-cpp.md)|指定要包含在產生的 .idl 檔案中的一或多個標頭檔。|
|[includelib](includelib-cpp.md)|導致 .idl 或 .h 檔案包含在產生的 .idl 檔案中。|
|[last_is](last-is.md)|指定要傳送之最後一個陣列元素的索引。|
|[lcid](lcid.md)|可讓您將地區設定識別碼傳遞給函式。|
|[length_is](length-is.md)|指定要傳送的陣列元素數目。|
|[library_block](library-block.md)|將結構放在 .idl 檔案的程式庫區塊內。|
|[licensed](licensed.md)|表示它所套用的 coclass 已獲得授權，而且必須使用來具現化 `IClassFactory2` 。|
|[本機](local-cpp.md)|當用於介面標頭時，可讓您使用 MIDL 編譯器做為標頭產生器。 在個別函式中使用時，會指定不會產生任何存根的本機程式。|
|[max_is](max-is.md)|指定有效陣列索引的最大值。|
|[module](module-cpp.md)|在 .idl 檔案中定義程式庫區塊。|
|[ms_union](ms-union.md)|控制 nonencapsulated 等位的網路資料標記法對齊。|
|[no_injected_text](no-injected-text.md)|防止編譯器插入程式碼做為屬性使用的結果。|
|[nonbrowsable](nonbrowsable.md)|表示介面成員不應顯示在屬性瀏覽器中。|
|[noncreatable](noncreatable.md)|定義無法自行具現化的物件。|
|[nonextensible](nonextensible.md)|指定 `IDispatch` 執行只包含介面描述中所列的屬性和方法，而且無法在執行時間以其他成員擴充。|
|[object](object-cpp.md)|識別自訂介面;與自訂屬性同義。|
|[odl](odl.md)|將介面識別為物件描述語言（ODL）介面。|
|[oleautomation](oleautomation.md)|指出介面與 Automation 相容。|
|[選擇性](optional-cpp.md)|指定成員函式的選擇性參數。|
|[脫銷](out-cpp.md)|識別從被呼叫程序傳回至呼叫程序的指標參數 (從伺服器至用戶端)。|
|[pointer_default](pointer-default.md)|除了出現在參數清單中的最上層指標以外，指定所有指標的預設指標屬性。|
|[pragma](pragma.md)|將指定的字串（不含引號字元）發出到產生的 .idl 檔案。|
|[進程](progid.md)|指定 COM 物件的 ProgID。|
|[propget](propget.md)|指定屬性存取子（get）函數。|
|[propput](propput.md)|指定屬性設定函式。|
|[propputref](propputref.md)|指定使用參考而非值的屬性設定函數。|
|[ptr](ptr.md)|將指標指定為完整指標。|
|[public](public-cpp-attributes.md)|確保 typedef 會進入型別程式庫，即使它不是從 .idl 檔案中參考也一樣。|
|[range](range-cpp.md)|針對在執行時間設定其值的引數或欄位，指定允許的值範圍。|
|[rdx](rdx.md)|建立或修改登錄機碼。|
|[唯讀](readonly-cpp.md)|禁止指派給變數。|
|[ref](ref-cpp.md)|識別參考指標。|
|[registration_script](registration-script.md)|執行指定的註冊腳本。|
|[requestedit](requestedit.md)|表示屬性支援 `OnRequestEdit` 通知。|
|[requires_category](requires-category.md)|指定類別所需的元件類別。|
|[約束](restricted.md)|指定無法任意呼叫程式庫或模組、介面或分配介面的成員。|
|[retval](retval.md)|指定接收成員之傳回值的參數。|
|[satype](satype.md)|指定的資料類型 `SAFEARRAY` 。|
|[size_is](size-is.md)|指定配置給大小指標的記憶體大小、大小指標的大小指標，以及單一或多維陣列。|
|[source](source-cpp.md)|表示類別、屬性或方法的成員是事件的來源。|
|[string](string-cpp.md)|表示一維 **`char`** 、 **`wchar_t`** 、 `byte` 或對等陣列，或這類陣列的指標必須被視為字串。|
|[support_error_info](support-error-info.md)|支援目標物件的錯誤報表。|
|[switch_is](switch-is.md)|指定作為 union 判別的運算式或識別碼，以選取聯集成員。|
|[switch_type](switch-type.md)|識別用來做為聯集判別之變數的類型。|
|[同步處理](synchronize.md)|同步處理方法的存取。|
|[處理](threading-cpp.md)|指定 COM 物件的執行緒模型。|
|[transmit_as](transmit-as.md)|指示編譯器將呈現的型別（用戶端和伺服器應用程式操作）與傳輸的型別產生關聯。|
|[uidefault](uidefault.md)|表示類型資訊成員是要在使用者介面中顯示的預設成員。|
|[unique](unique-cpp.md)|指定唯一的指標。|
|[usesgetlasterror](usesgetlasterror.md)|告訴呼叫者，如果呼叫該函式時發生錯誤，呼叫端可以呼叫 `GetLastError` 來抓取錯誤碼。|
|[uuid](uuid-cpp-attributes.md)|指定類別或介面的唯一識別碼。|
|[v1_enum](v1-enum.md)|指示指定的列舉型別會以32位實體的形式傳送，而不是16位的預設值。|
|[vararg](vararg.md)|指定函式接受可變數目的引數。|
|[version](version-cpp.md)|識別介面或類別的多個版本之間的特定版本。|
|[vi_progid](vi-progid.md)|指定與版本無關的 ProgID 形式。|
|[wire_marshal](wire-marshal.md)|指定將用於傳輸的資料類型，而不是應用程式特定的資料類型。|

## <a name="see-also"></a>另請參閱

[適用於 COM 和 .NET 的 C++ 屬性](cpp-attributes-com-net.md)<br/>
[依群組的屬性](attributes-by-group.md)<br/>
[依使用量的屬性](attributes-by-usage.md)
