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
ms.openlocfilehash: 386afe5362f876cd1489a35839f4f8cfc2381e91
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038209"
---
# <a name="attributes-alphabetical-reference"></a>依字母順序排列的屬性參考

下列屬性可在 Microsoft c + + 編譯器：

|屬性|描述|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|表示控制項，可以彙總的另一個控制項。|
|[彙總](aggregates.md)|表示控制項彙總的目標類別。|
|[appobject](appobject.md)|識別做為應用程式物件，這是完整的 EXE 應用程式相關聯，並指出函數和屬性的 coclass 全域使用這個類型程式庫中的 coclass。|
|[async_uuid](async-uuid.md)|指定會指示 MIDL 編譯器定義 COM 介面的同步和非同步版本的 UUID。|
|[屬性](attribute.md)|可讓您建立自訂屬性。|
|[bindable](bindable.md)|表示支援資料繫結的屬性。|
|[call_as](call-as.md)|讓不可遠端處理函式對應至遠端函式。|
|[case](case-cpp.md)|搭配[switch_type](switch-type.md)等位中的屬性。|
|[coclass](coclass.md)|建立 COM 物件，可實作 COM 介面。|
|[com_interface_entry](com-interface-entry-cpp.md)|將 COM 對應中的介面項目。|
|[控制項](control.md)|指定使用者定義型別為控制項。|
|[cpp_quote](cpp-quote.md)|指定的字串，不能包含單引號字元，發出到產生的標頭檔。|
|[自訂](custom-cpp.md)|可讓您定義您自己的屬性。|
|[db_accessor](db-accessor.md)|繫結的資料列集資料行，並將它們繫結至對應的存取子對應。|
|[db_column](db-column.md)|將指定的資料行的資料列集繫結。|
|[db_command](db-command.md)|執行 OLE DB 命令。|
|[db_param](db-param.md)|關聯的輸入或輸出參數中指定的成員變數。|
|[db_source](db-source.md)|建立並封裝的連接，透過提供者，資料來源。|
|[db_table](db-table.md)|開啟 OLE DB 資料表。|
|[default](default-cpp.md)|表示 coclass 內定義的自訂或 dispinterface，用以代表預設可程式性介面。|
|[defaultbind](defaultbind.md)|表示最能代表物件的單一、 可繫結屬性。|
|[defaultcollelem](defaultcollelem.md)|使用 Visual Basic 程式碼最佳化。|
|[defaultvalue](defaultvalue.md)|允許指定的具類型的選擇性參數的預設值。|
|[defaultvtable](defaultvtable.md)|為控制項的預設 vtable 介面中定義的介面。|
|[dispinterface](dispinterface.md)|將介面放入 .idl 檔案中作為分派介面。|
|[displaybind](displaybind.md)|指出應該顯示給使用者，作為可繫結的屬性。|
|[dual](dual.md)|將介面放在.idl 檔案中，為雙重介面。|
|[emitidl](emitidl.md)|決定是否將處理並放在所產生的.idl 檔案中所有後續的 IDL 屬性。|
|[entry](entry.md)|指定匯出的函式或常數 」 模組中，找出 DLL 的進入點。|
|[event_receiver](event-receiver.md)|建立事件接收器。|
|[event_source](event-source.md)|建立事件來源。|
|[匯出](export.md)|會導致資料結構，以放入.idl 檔案。|
|[first_is](first-is.md)|指定要傳送的第一個陣列元素的索引。|
|[helpcontext](helpcontext.md)|指定的內容識別碼，可讓使用者檢視說明檔中這個項目相關的資訊。|
|[helpfile](helpfile.md)|設定型別程式庫的說明檔的名稱。|
|[helpstring](helpstring.md)|指定.hlp 或.chm 檔案中的說明主題的識別碼。|
|[helpstringdll](helpstringdll.md)|指定要用來執行文件字串查閱 （當地語系化） DLL 的名稱。|
|[隱藏](hidden.md)|表示項目存在，但不是會顯示在使用者導向的瀏覽器中。|
|[id](id.md)|指定成員函式 （屬性或方法，在介面或 dispinterface） 的 DISPID。|
|[idl_module](idl-module.md)|指定進入點 DLL 中。|
|[idl_quote](idl-quote.md)|可讓您使用屬性或 IDL 建構不支援在目前版本的 Visual c + + 中。|
|[iid_is](iid-is.md)|指定的介面指標所指向的 COM 介面的 IID。|
|[immediatebind](immediatebind.md)|表示資料庫將會立即被告知資料繫結物件的屬性的所有變更。|
|[實作](implements-cpp.md)|指定分派介面，強制讓 IDL coclass 的成員。|
|[implements_category](implements-category.md)|指定類別的實作的元件類別。|
|[import](import.md)|指定另一個.idl、.odl 或標頭檔包含您想要從主要的.idl 檔案中參考的定義。|
|[importidl](importidl.md)|指定的.idl 檔插入所產生的.idl 檔案。|
|[importlib](importlib.md)|讓已編譯成其他類型程式庫的類型可供正在建立的類型程式庫使用。|
|[中的](in-cpp.md)|指出參數是要呼叫的程序從傳遞至呼叫的程序。|
|[include](include-cpp.md)|指定要包含在產生的.idl 檔案中的一或多個標頭檔。|
|[includelib](includelib-cpp.md)|會導致的.idl 或.h 檔案要包含在產生的.idl 檔案中。|
|[last_is](last-is.md)|指定要傳送的最後一個陣列元素的索引。|
|[lcid](lcid.md)|可讓您將地區設定識別碼傳遞給函式。|
|[length_is](length-is.md)|指定要傳送的陣列元素數目。|
|[library_block](library-block.md)|會建構的.idl 檔案的程式庫區塊內。|
|[licensed](licensed.md)|表示所套用的 coclass 係授權使用，而且必須具現化使用`IClassFactory2`。|
|[本機](local-cpp.md)|可讓您使用 MIDL 編譯器為標頭的產生器時用於介面標頭。 中的個別函式使用時，會指定任何虛設常式所產生的本機程序。|
|[max_is](max-is.md)|指定有效的陣列索引的最大值。|
|[name](module-cpp.md)|在 .idl 檔案中定義程式庫區塊。|
|[ms_union](ms-union.md)|控制 nonencapsulated 等位的網路資料表示法對齊方式。|
|[no_injected_text](no-injected-text.md)|防止編譯器將程式碼，因為屬性使用。|
|[nonbrowsable](nonbrowsable.md)|指出介面成員不會顯示在屬性瀏覽器。|
|[noncreatable](noncreatable.md)|定義本身無法具現化的物件。|
|[nonextensible](nonextensible.md)|指定`IDispatch`實作只包括屬性和方法介面描述中所列，而且無法在執行階段延伸與其他成員。|
|[object](object-cpp.md)|識別自訂的介面;自訂屬性的同義詞。|
|[odl](odl.md)|識別物件描述語言 (ODL) 介面的介面。|
|[oleautomation](oleautomation.md)|表示與 Automation 相容介面。|
|[選擇性](optional-cpp.md)|指定的成員函式的選擇性參數。|
|[out](out-cpp.md)|識別從被呼叫程序傳回至呼叫程序的指標參數 (從伺服器至用戶端)。|
|[pointer_default](pointer-default.md)|指定的預設指標屬性的最上層出現的指標除外的所有指標的參數清單。|
|[pragma](pragma.md)|指定的字串，不能包含單引號字元，發出到產生的.idl 檔案。|
|[progid](progid.md)|指定 COM 物件的 ProgID。|
|[propget](propget.md)|指定屬性存取子 (get) 函式。|
|[propput](propput.md)|指定屬性設定函式。|
|[propputref](propputref.md)|指定使用參考而非值的屬性設定函式。|
|[ptr](ptr.md)|指定指標做為完整的指標。|
|[public](public-cpp-attributes.md)|可確保 typedef 會移至類型程式庫，即使它不從參考的.idl 檔案中。|
|[range](range-cpp.md)|指定引數或在執行階段設定其值的欄位的允許值的範圍。|
|[rdx](rdx.md)|建立或修改登錄機碼。|
|[readonly](readonly-cpp.md)|禁止指派給變數。|
|[ref](ref-cpp.md)|識別參考指標。|
|[registration_script](registration-script.md)|執行指定的註冊指令碼。|
|[requestedit](requestedit.md)|表示屬性支援 `OnRequestEdit` 通知。|
|[requires_category](requires-category.md)|指定所需的元件類別的類別。|
|[restricted](restricted.md)|指定的程式庫或模組、 介面或 dispinterface 的成員不能任意呼叫。|
|[retval](retval.md)|指定接收成員的傳回值的參數。|
|[satype](satype.md)|指定的資料型別`SAFEARRAY`。|
|[size_is](size-is.md)|指定記憶體的大小配置大小的指標，且大小來調整大小的指標，以及單一或多維陣列的指標。|
|[來源](source-cpp.md)|表示的類別、 屬性或方法成員是一個事件的來源。|
|[字串](string-cpp.md)|表示一維**char**， **wchar_t**， `byte`，或對等陣列或這類陣列的指標必須被視為字串。|
|[support_error_info](support-error-info.md)|支援目標物件的錯誤報告功能。|
|[switch_is](switch-is.md)|指定的運算式或做為選取的等位成員的聯集判別的識別項。|
|[switch_type](switch-type.md)|識別做為等位的判別變數的型別。|
|[synchronize](synchronize.md)|同步處理方法的存取。|
|[執行緒處理](threading-cpp.md)|指定 COM 物件的執行緒模型。|
|[transmit_as](transmit-as.md)|指示編譯器將呈現的型別，用戶端和伺服器應用程式管理，相關聯的傳輸類型。|
|[uidefault](uidefault.md)|表示型別資訊成員是在使用者介面中顯示的預設成員。|
|[unique](unique-cpp.md)|指定唯一的指標。|
|[usesgetlasterror](usesgetlasterror.md)|會告知呼叫端是否有錯誤時呼叫該函式，呼叫端可以再呼叫`GetLastError`擷取錯誤碼。|
|[uuid](uuid-cpp-attributes.md)|指定類別或介面的唯一識別碼。|
|[v1_enum](v1-enum.md)|指示指定的列舉型別會傳輸為 32 位元的實體，而不是 16 位元的預設值。|
|[vararg](vararg.md)|指定的函式接受可變數目的引數。|
|[版本](version-cpp.md)|識別多個版本之間的介面或類別的特定版本。|
|[vi_progid](vi-progid.md)|指定與版本無關的 ProgID 表單。|
|[wire_marshal](wire-marshal.md)|指定將用於傳輸，而不是應用程式特定資料類型的資料類型。|

## <a name="see-also"></a>另請參閱

[適用於 COM 和.NET 的 c + + 屬性](cpp-attributes-com-net.md)<br/>
[依群組分類的屬性](attributes-by-group.md)<br/>
[依使用方式分類的屬性](attributes-by-usage.md)