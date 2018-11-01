---
title: IDL 屬性 (c + + COM)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- IDL attributes
- .idl files [C++], attributes
- IDL files [C++], attributes
- .idl files [C++]
ms.assetid: 04c596f4-c97b-4952-8053-316678b1d0b6
ms.openlocfilehash: 6e88edf114e180a118d0467d5425d16e50d7c216
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593488"
---
# <a name="idl-attributes"></a>IDL 屬性

傳統上，維護.idl 檔，表示您必須：

- 要熟悉的結構和語法的.idl 檔能夠修改它。

- 依賴的精靈，可讓您修改的.idl 檔案的某些層面。

現在，您可以修改從.idl 檔中使用 Visual c + + IDL 屬性的原始程式碼檔。 在許多情況下，Visual c + + IDL 屬性會有 MIDL 屬性相同的名稱。 名稱的 Visual c + + IDL 屬性，以及 MIDL 屬性相同時，這表示，置於您的原始程式碼檔中的 Visual c + + 屬性將導致.idl 檔，其中包含其 namesake MIDL 屬性。 不過，Visual c + + IDL 屬性可能不會提供 MIDL 屬性的所有功能。

不搭配使用時[COM 屬性](com-attributes.md)，IDL 屬性可讓您定義介面。 當編譯的原始程式碼時，屬性用來定義所產生的.idl 檔案。 ATL 專案中的 COM 屬性搭配使用時，某些 IDL 屬性，例如`coclass`，導致插入至專案的程式碼。

請注意， [idl_quote](idl-quote.md)可讓您使用目前版本的 Visual c + + 中不支援的 MIDL 建構。 這和其他屬性，例如[importlib](importlib.md)並[includelib](includelib-cpp.md)幫助您使用您目前的 Visual c + + 專案中現有的.idl 檔案。

|屬性|描述|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|表示控制項，可以彙總的另一個控制項。|
|[appobject](appobject.md)|識別做為應用程式物件，這是完整的 EXE 應用程式相關聯，並指出函數和屬性的 coclass 全域使用這個類型程式庫中的 coclass。|
|[async_uuid](async-uuid.md)|指定會指示 MIDL 編譯器定義 COM 介面的同步和非同步版本的 UUID。|
|[bindable](bindable.md)|表示支援資料繫結的屬性。|
|[call_as](call-as.md)|讓不可遠端處理函式對應至遠端函式。|
|[case](case-cpp.md)|搭配[switch_type](switch-type.md)等位中的屬性。|
|[coclass](coclass.md)|位置的類別到.idl 檔為 coclass 的定義。|
|[control](control.md)|指定使用者定義型別為控制項。|
|[cpp_quote](cpp-quote.md)|指定的字串，不能包含單引號字元，發出到產生的標頭檔。|
|[defaultbind](defaultbind.md)|表示最能代表物件的單一、 可繫結屬性。|
|[defaultcollelem](defaultcollelem.md)|使用 Visual Basic 程式碼最佳化。|
|[defaultvalue](defaultvalue.md)|允許指定的具類型的選擇性參數的預設值。|
|[default](default-cpp.md)|表示 coclass 內定義的自訂或 dispinterface，用以代表預設可程式性介面。|
|[defaultvtable](defaultvtable.md)|為控制項的預設 vtable 介面中定義的介面。|
|[dispinterface](dispinterface.md)|將介面放入 .idl 檔案中作為分派介面。|
|[displaybind](displaybind.md)|指出應該顯示給使用者，作為可繫結的屬性。|
|[dual](dual.md)|將介面放在.idl 檔案中，為雙重介面。|
|[entry](entry.md)|指定匯出的函式或常數 」 模組中，找出 DLL 的進入點。|
|[first_is](first-is.md)|指定要傳送的第一個陣列元素的索引。|
|[helpcontext](helpcontext.md)|指定的內容識別碼，可讓使用者檢視說明檔中這個項目相關的資訊。|
|[helpfile](helpfile.md)|設定型別程式庫的說明檔的名稱。|
|[helpstringcontext](helpstringcontext.md)|指定.hlp 或.chm 檔案中的說明主題的識別碼。|
|[helpstringdll](helpstringdll.md)|指定要用來執行文件字串查閱 （當地語系化） DLL 的名稱。|
|[helpstring](helpstring.md)|指定用來描述所套用之項目的字元字串。|
|[hidden](hidden.md)|表示項目存在，但不是會顯示在使用者導向的瀏覽器中。|
|[idl_module](idl-module.md)|指定進入點 DLL 中。|
|[idl_quote](idl-quote.md)|可讓您使用屬性或 IDL 建構不支援在目前版本的 Visual c + + 中。|
|[id](id.md)|指定成員函式 （屬性或方法，在介面或 dispinterface） 的 DISPID。|
|[iid_is](iid-is.md)|指定的介面指標所指向的 COM 介面的 IID。|
|[immediatebind](immediatebind.md)|表示資料庫將會立即被告知資料繫結物件的屬性的所有變更。|
|[importlib](importlib.md)|讓已編譯成其他類型程式庫的類型可供正在建立的類型程式庫使用。|
|[import](import.md)|指定另一個.idl、.odl 或標頭檔包含您想要從主要的.idl 檔案中參考的定義。|
|[include](include-cpp.md)|指定要包含在產生的.idl 檔案中的一或多個標頭檔。|
|[includelib](includelib-cpp.md)|會導致的.idl 或.h 檔案要包含在產生的.idl 檔案中。|
|[in](in-cpp.md)|指出參數是要呼叫的程序從傳遞至呼叫的程序。|
|[last_is](last-is.md)|指定要傳送的最後一個陣列元素的索引。|
|[lcid](lcid.md)|可讓您將地區設定識別碼傳遞給函式。|
|[length_is](length-is.md)|指定要傳送的陣列元素數目。|
|[licensed](licensed.md)|表示所套用的 coclass 係授權使用，而且必須具現化使用`IClassFactory2`。|
|[local](local-cpp.md)|可讓您使用 MIDL 編譯器為標頭的產生器時用於介面標頭。 中的個別函式使用時，會指定任何虛設常式所產生的本機程序。|
|[max_is](max-is.md)|指定有效的陣列索引的最大值。|
|[module](module-cpp.md)|在 .idl 檔案中定義程式庫區塊。|
|[ms_union](ms-union.md)|控制 nonencapsulated 等位的網路資料表示法對齊方式。|
|[no_injected_text](no-injected-text.md)|防止編譯器將程式碼，因為屬性使用。|
|[nonbrowsable](nonbrowsable.md)|指出介面成員不會顯示在屬性瀏覽器。|
|[noncreatable](noncreatable.md)|定義本身無法具現化的物件。|
|[nonextensible](nonextensible.md)|指定`IDispatch`實作只包括屬性和方法介面描述中所列，而且無法在執行階段延伸與其他成員。|
|[object](object-cpp.md)|識別自訂的介面;自訂屬性的同義詞。|
|[odl](odl.md)|識別物件描述語言 (ODL) 介面的介面。|
|[oleautomation](oleautomation.md)|表示與 Automation 相容介面。|
|[optional](optional-cpp.md)|指定的成員函式的選擇性參數。|
|[out](out-cpp.md)|識別從被呼叫程序傳回至呼叫程序的指標參數 (從伺服器至用戶端)。|
|[pointer_default](pointer-default.md)|指定的預設指標屬性的最上層出現的指標除外的所有指標的參數清單。|
|[pragma](pragma.md)|指定的字串，不能包含單引號字元，發出到產生的.idl 檔案。|
|[progid](progid.md)|指定 COM 物件的 ProgID。|
|[propget](propget.md)|指定屬性存取子 (get) 函式。|
|[propputref](propputref.md)|指定使用參考而非值的屬性設定函式。|
|[propput](propput.md)|指定屬性設定函式。|
|[ptr](ptr.md)|指定指標做為完整的指標。|
|[public](public-cpp-attributes.md)|可確保 typedef 會移至類型程式庫，即使它不從參考的.idl 檔案中。|
|[range](range-cpp.md)|指定引數或在執行階段設定其值的欄位的允許值的範圍。|
|[readonly](readonly-cpp.md)|禁止指派給變數。|
|[ref](ref-cpp.md)|識別參考指標。|
|[requestedit](requestedit.md)|表示屬性支援`OnRequestEdit`通知。|
|[restricted](restricted.md)|指定的程式庫或模組、 介面或 dispinterface 的成員不能任意呼叫。|
|[retval](retval.md)|指定接收成員的傳回值的參數。|
|[size_is](size-is.md)|指定記憶體的大小配置大小的指標，且大小來調整大小的指標，以及單一或多維陣列的指標。|
|[source](source-cpp.md)|表示的類別、 屬性或方法成員是一個事件的來源。|
|[string](string-cpp.md)|表示一維**char**， **wchar_t**， `byte`，或對等陣列或這類陣列的指標必須被視為字串。|
|[switch_is](switch-is.md)|指定的運算式或做為選取的等位成員的聯集判別的識別項。|
|[switch_type](switch-type.md)|識別做為等位的判別變數的型別。|
|[transmit_as](transmit-as.md)|指示編譯器將呈現的型別，用戶端和伺服器應用程式管理，相關聯的傳輸類型。|
|[uidefault](uidefault.md)|表示型別資訊成員是在使用者介面中顯示的預設成員。|
|[unique](unique-cpp.md)|指定唯一的指標。|
|[usesgetlasterror](usesgetlasterror.md)|會告知呼叫端是否有錯誤時呼叫該函式，呼叫端可以再呼叫`GetLastError`擷取錯誤碼。|
|[uuid](uuid-cpp-attributes.md)|指定類別或介面的唯一識別碼。|
|[v1_enum](v1-enum.md)|指示指定的列舉型別會傳輸為 32 位元的實體，而不是 16 位元的預設值。|
|[vararg](vararg.md)|指定的函式接受可變數目的引數。|
|[vi_progid](vi-progid.md)|指定與版本無關的 ProgID 表單。|
|[wire_marshal](wire-marshal.md)|指定將用於傳輸，而不是應用程式特定資料類型的資料類型。|

## <a name="see-also"></a>另請參閱

[依群組分類的屬性](attributes-by-group.md)
