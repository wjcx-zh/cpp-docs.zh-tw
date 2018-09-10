---
title: 屬性依字母順序排列參考 |Microsoft Docs
ms.custom: index-page
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.attributes
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI]
ms.assetid: fb2216ef-9fbd-44f4-afed-732aa99450e2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e2353b952964ffe6b8078f688b4ac8e129d891d7
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314676"
---
# <a name="attributes-alphabetical-reference"></a>依字母順序排列的屬性參考

下列屬性可用於 Visual c + +。

|屬性|描述|
|---------------|-----------------|
|[aggregatable](../windows/aggregatable.md)|表示控制項，可以彙總的另一個控制項。|
|[aggregates](../windows/aggregates.md)|表示控制項彙總的目標類別。|
|[appobject](../windows/appobject.md)|識別做為應用程式物件，這是完整的 EXE 應用程式相關聯，並指出函數和屬性的 coclass 全域使用這個類型程式庫中的 coclass。|
|[async_uuid](../windows/async-uuid.md)|指定會指示 MIDL 編譯器定義 COM 介面的同步和非同步版本的 UUID。|
|[attribute](../windows/attribute.md)|可讓您建立自訂屬性。|
|[bindable](../windows/bindable.md)|表示支援資料繫結的屬性。|
|[call_as](../windows/call-as.md)|讓不可遠端處理函式對應至遠端函式。|
|[case](../windows/case-cpp.md)|搭配[switch_type](../windows/switch-type.md)等位中的屬性。|
|[coclass](../windows/coclass.md)|建立 COM 物件，可實作 COM 介面。|
|[com_interface_entry](../windows/com-interface-entry-cpp.md)|將 COM 對應中的介面項目。|
|[control](../windows/control.md)|指定使用者定義型別為控制項。|
|[cpp_quote](../windows/cpp-quote.md)|指定的字串，不能包含單引號字元，發出到產生的標頭檔。|
|[custom](../windows/custom-cpp.md)|可讓您定義您自己的屬性。|
|[db_accessor](../windows/db-accessor.md)|繫結的資料列集資料行，並將它們繫結至對應的存取子對應。|
|[db_column](../windows/db-column.md)|將指定的資料行的資料列集繫結。|
|[db_command](../windows/db-command.md)|執行 OLE DB 命令。|
|[db_param](../windows/db-param.md)|關聯的輸入或輸出參數中指定的成員變數。|
|[db_source](../windows/db-source.md)|建立並封裝的連接，透過提供者，資料來源。|
|[db_table](../windows/db-table.md)|開啟 OLE DB 資料表。|
|[default](../windows/default-cpp.md)|表示 coclass 內定義的自訂或 dispinterface，用以代表預設可程式性介面。|
|[defaultbind](../windows/defaultbind.md)|表示最能代表物件的單一、 可繫結屬性。|
|[defaultcollelem](../windows/defaultcollelem.md)|使用 Visual Basic 程式碼最佳化。|
|[defaultvalue](../windows/defaultvalue.md)|允許指定的具類型的選擇性參數的預設值。|
|[defaultvtable](../windows/defaultvtable.md)|為控制項的預設 vtable 介面中定義的介面。|
|[dispinterface](../windows/dispinterface.md)|將介面放入 .idl 檔案中作為分派介面。|
|[displaybind](../windows/displaybind.md)|指出應該顯示給使用者，作為可繫結的屬性。|
|[dual](../windows/dual.md)|將介面放在.idl 檔案中，為雙重介面。|
|[emitidl](../windows/emitidl.md)|決定是否將處理並放在所產生的.idl 檔案中所有後續的 IDL 屬性。|
|[entry](../windows/entry.md)|指定匯出的函式或常數 」 模組中，找出 DLL 的進入點。|
|[event_receiver](../windows/event-receiver.md)|建立事件接收器。|
|[event_source](../windows/event-source.md)|建立事件來源。|
|[export](../windows/export.md)|會導致資料結構，以放入.idl 檔案。|
|[first_is](../windows/first-is.md)|指定要傳送的第一個陣列元素的索引。|
|[helpcontext](../windows/helpcontext.md)|指定的內容識別碼，可讓使用者檢視說明檔中這個項目相關的資訊。|
|[helpfile](../windows/helpfile.md)|設定型別程式庫的說明檔的名稱。|
|[helpstring](../windows/helpstring.md)|指定.hlp 或.chm 檔案中的說明主題的識別碼。|
|[helpstringdll](../windows/helpstringdll.md)|指定要用來執行文件字串查閱 （當地語系化） DLL 的名稱。|
|[hidden](../windows/hidden.md)|表示項目存在，但不是會顯示在使用者導向的瀏覽器中。|
|[id](../windows/id.md)|指定成員函式 （屬性或方法，在介面或 dispinterface） 的 DISPID。|
|[idl_module](../windows/idl-module.md)|指定進入點 DLL 中。|
|[idl_quote](../windows/idl-quote.md)|可讓您使用屬性或 IDL 建構不支援在目前版本的 Visual c + + 中。|
|[iid_is](../windows/iid-is.md)|指定的介面指標所指向的 COM 介面的 IID。|
|[immediatebind](../windows/immediatebind.md)|表示資料庫將會立即被告知資料繫結物件的屬性的所有變更。|
|[實作](../windows/implements-cpp.md)|指定分派介面，強制讓 IDL coclass 的成員。|
|[implements_category](../windows/implements-category.md)|指定類別的實作的元件類別。|
|[import](../windows/import.md)|指定另一個.idl、.odl 或標頭檔包含您想要從主要的.idl 檔案中參考的定義。|
|[importidl](../windows/importidl.md)|指定的.idl 檔插入所產生的.idl 檔案。|
|[importlib](../windows/importlib.md)|讓已編譯成其他類型程式庫的類型可供正在建立的類型程式庫使用。|
|[in](../windows/in-cpp.md)|指出參數是要呼叫的程序從傳遞至呼叫的程序。|
|[include](../windows/include-cpp.md)|指定要包含在產生的.idl 檔案中的一或多個標頭檔。|
|[includelib](../windows/includelib-cpp.md)|會導致的.idl 或.h 檔案要包含在產生的.idl 檔案中。|
|[last_is](../windows/last-is.md)|指定要傳送的最後一個陣列元素的索引。|
|[lcid](../windows/lcid.md)|可讓您將地區設定識別碼傳遞給函式。|
|[length_is](../windows/length-is.md)|指定要傳送的陣列元素數目。|
|[library_block](../windows/library-block.md)|會建構的.idl 檔案的程式庫區塊內。|
|[licensed](../windows/licensed.md)|表示所套用的 coclass 係授權使用，而且必須具現化使用`IClassFactory2`。|
|[local](../windows/local-cpp.md)|可讓您使用 MIDL 編譯器為標頭的產生器時用於介面標頭。 中的個別函式使用時，會指定任何虛設常式所產生的本機程序。|
|[max_is](../windows/max-is.md)|指定有效的陣列索引的最大值。|
|[模組](../windows/module-cpp.md)|在 .idl 檔案中定義程式庫區塊。|
|[ms_union](../windows/ms-union.md)|控制 nonencapsulated 等位的網路資料表示法對齊方式。|
|[no_injected_text](../windows/no-injected-text.md)|防止編譯器將程式碼，因為屬性使用。|
|[nonbrowsable](../windows/nonbrowsable.md)|指出介面成員不會顯示在屬性瀏覽器。|
|[noncreatable](../windows/noncreatable.md)|定義本身無法具現化的物件。|
|[nonextensible](../windows/nonextensible.md)|指定`IDispatch`實作只包括屬性和方法介面描述中所列，而且無法在執行階段延伸與其他成員。|
|[object](../windows/object-cpp.md)|識別自訂的介面;自訂屬性的同義詞。|
|[odl](../windows/odl.md)|識別物件描述語言 (ODL) 介面的介面。|
|[oleautomation](../windows/oleautomation.md)|表示與 Automation 相容介面。|
|[選擇性](../windows/optional-cpp.md)|指定的成員函式的選擇性參數。|
|[out](../windows/out-cpp.md)|識別從被呼叫程序傳回至呼叫程序的指標參數 (從伺服器至用戶端)。|
|[pointer_default](../windows/pointer-default.md)|指定的預設指標屬性的最上層出現的指標除外的所有指標的參數清單。|
|[pragma](../windows/pragma.md)|指定的字串，不能包含單引號字元，發出到產生的.idl 檔案。|
|[progid](../windows/progid.md)|指定 COM 物件的 ProgID。|
|[propget](../windows/propget.md)|指定屬性存取子 (get) 函式。|
|[propput](../windows/propput.md)|指定屬性設定函式。|
|[propputref](../windows/propputref.md)|指定使用參考而非值的屬性設定函式。|
|[ptr](../windows/ptr.md)|指定指標做為完整的指標。|
|[public](../windows/public-cpp-attributes.md)|可確保 typedef 會移至類型程式庫，即使它不從參考的.idl 檔案中。|
|[範圍](../windows/range-cpp.md)|指定引數或在執行階段設定其值的欄位的允許值的範圍。|
|[rdx](../windows/rdx.md)|建立或修改登錄機碼。|
|[readonly](../windows/readonly-cpp.md)|禁止指派給變數。|
|[ref](../windows/ref-cpp.md)|識別參考指標。|
|[registration_script](../windows/registration-script.md)|執行指定的註冊指令碼。|
|[requestedit](../windows/requestedit.md)|表示屬性支援`OnRequestEdit`通知。|
|[requires_category](../windows/requires-category.md)|指定所需的元件類別的類別。|
|[restricted](../windows/restricted.md)|指定的程式庫或模組、 介面或 dispinterface 的成員不能任意呼叫。|
|[retval](../windows/retval.md)|指定接收成員的傳回值的參數。|
|[satype](../windows/satype.md)|指定的資料型別`SAFEARRAY`。|
|[size_is](../windows/size-is.md)|指定記憶體的大小配置大小的指標，且大小來調整大小的指標，以及單一或多維陣列的指標。|
|[source](../windows/source-cpp.md)|表示的類別、 屬性或方法成員是一個事件的來源。|
|[string](../windows/string-cpp.md)|表示一維**char**， **wchar_t**， `byte`，或對等陣列或這類陣列的指標必須被視為字串。|
|[support_error_info](../windows/support-error-info.md)|支援目標物件的錯誤報告功能。|
|[switch_is](../windows/switch-is.md)|指定的運算式或做為選取的等位成員的聯集判別的識別項。|
|[switch_type](../windows/switch-type.md)|識別做為等位的判別變數的型別。|
|[synchronize](../windows/synchronize.md)|同步處理方法的存取。|
|[執行緒處理](../windows/threading-cpp.md)|指定 COM 物件的執行緒模型。|
|[transmit_as](../windows/transmit-as.md)|指示編譯器將呈現的型別，用戶端和伺服器應用程式管理，相關聯的傳輸類型。|
|[uidefault](../windows/uidefault.md)|表示型別資訊成員是在使用者介面中顯示的預設成員。|
|[unique](../windows/unique-cpp.md)|指定唯一的指標。|
|[usesgetlasterror](../windows/usesgetlasterror.md)|會告知呼叫端是否有錯誤時呼叫該函式，呼叫端可以再呼叫`GetLastError`擷取錯誤碼。|
|[uuid](../windows/uuid-cpp-attributes.md)|指定類別或介面的唯一識別碼。|
|[v1_enum](../windows/v1-enum.md)|指示指定的列舉型別會傳輸為 32 位元的實體，而不是 16 位元的預設值。|
|[vararg](../windows/vararg.md)|指定的函式接受可變數目的引數。|
|[version](../windows/version-cpp.md)|識別多個版本之間的介面或類別的特定版本。|
|[vi_progid](../windows/vi-progid.md)|指定與版本無關的 ProgID 表單。|
|[wire_marshal](../windows/wire-marshal.md)|指定將用於傳輸，而不是應用程式特定資料類型的資料類型。|

## <a name="see-also"></a>另請參閱

[C++ 屬性參考](../windows/cpp-attributes-reference.md)  
[概念](../windows/attributed-programming-concepts.md)  
[依群組分類的屬性](../windows/attributes-by-group.md)  
[依使用方式分類的屬性](../windows/attributes-by-usage.md)