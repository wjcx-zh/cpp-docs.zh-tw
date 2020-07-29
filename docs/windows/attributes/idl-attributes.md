---
title: IDL 屬性（c + + COM）
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- IDL attributes
- .idl files [C++], attributes
- IDL files [C++], attributes
- .idl files [C++]
ms.assetid: 04c596f4-c97b-4952-8053-316678b1d0b6
ms.openlocfilehash: 8cceae2f1c4880b72f1ffc30070d6aa6bf8e3a51
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211966"
---
# <a name="idl-attributes"></a>IDL 屬性

傳統上，維護 .idl 檔案的目的，就是您必須：

- 請熟悉 .idl 檔案的結構和語法，以便能夠修改它。

- 依賴 wizard，這可讓您修改 .idl 檔案的某些層面。

現在，您可以使用 Visual C++ IDL 屬性，從原始程式碼檔內修改 .idl 檔案。 在許多情況下，Visual C++ IDL 屬性的名稱與 MIDL 屬性相同。 當 Visual C++ IDL 屬性和 MIDL 屬性的名稱相同時，就表示將 Visual C++ 屬性放在原始程式碼檔中，會產生一個包含其同名 MIDL 屬性的 .idl 檔案。 不過，Visual C++ IDL 屬性可能不會提供 MIDL 屬性的所有功能。

當不搭配[COM 屬性](com-attributes.md)使用時，IDL 屬性可讓您定義介面。 編譯原始程式碼時，會使用屬性來定義產生的 .idl 檔案。 與 ATL 專案中的 COM 屬性搭配使用時，某些 IDL 屬性（例如 `coclass` ）會導致程式碼插入專案中。

請注意， [idl_quote](idl-quote.md)可讓您使用目前版本的 Visual C++ 不支援的 MIDL 結構。 這個和其他屬性（例如[importlib](importlib.md)和[includelib](includelib-cpp.md) ）可協助您在目前的 Visual Studio c + + 專案中使用現有的 .idl 檔案。

|屬性|說明|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|表示控制項可以由另一個控制項匯總。|
|[appobject](appobject.md)|將 coclass 識別為與完整 EXE 應用程式相關聯的應用程式物件，並指出 coclass 的函式和屬性在此類型程式庫中可全域使用。|
|[async_uuid](async-uuid.md)|指定 UUID，以指示 MIDL 編譯器定義 COM 介面的同步和非同步版本。|
|[bindable](bindable.md)|表示支援資料繫結的屬性。|
|[call_as](call-as.md)|讓不可遠端處理函數能夠對應至遠端函式。|
|[例圖](case-cpp.md)|與聯集內的[switch_type](switch-type.md)屬性搭配使用。|
|[coclass](coclass.md)|將類別定義放入 .idl 檔案中作為 coclass。|
|[control](control.md)|指定使用者定義型別為控制項。|
|[cpp_quote](cpp-quote.md)|將指定的字串（不含引號字元）發出到產生的標頭檔中。|
|[defaultbind](defaultbind.md)|表示最能代表物件的單一可系結屬性。|
|[defaultcollelem](defaultcollelem.md)|用於 Visual Basic 程式碼優化。|
|[defaultvalue](defaultvalue.md)|允許指定具類型的選擇性參數的預設值。|
|[預設值](default-cpp.md)|表示 coclass 內定義的自訂或 dispinterface，用以代表預設可程式性介面。|
|[defaultvtable](defaultvtable.md)|將介面定義為控制項的預設 vtable 介面。|
|[dispinterface](dispinterface.md)|將介面放入 .idl 檔案中作為分派介面。|
|[displaybind](displaybind.md)|表示應該向使用者顯示為可系結的屬性。|
|[dual](dual.md)|將介面放在 .idl 檔案中，做為雙重介面。|
|[上場](entry.md)|藉由識別 DLL 中的進入點，指定模組中匯出的函數或常數。|
|[first_is](first-is.md)|指定要傳送之第一個陣列元素的索引。|
|[helpcontext](helpcontext.md)|指定內容識別碼，讓使用者可在說明檔中查看此元素的相關資訊。|
|[helpfile](helpfile.md)|設定類型程式庫的說明檔名稱。|
|[helpstringcontext](helpstringcontext.md)|在 .hlp 或 .chm 檔案中指定說明主題的識別碼。|
|[helpstringdll](helpstringdll.md)|指定要用來執行檔字串查閱（當地語系化）之 DLL 的名稱。|
|[helpstring](helpstring.md)|指定用來描述所套用之項目的字元字串。|
|[隱含](hidden.md)|表示專案存在，但不應該顯示在使用者導向的瀏覽器中。|
|[idl_module](idl-module.md)|指定 DLL 中的進入點。|
|[idl_quote](idl-quote.md)|可讓您使用目前版本的 Visual C++ 中不支援的屬性或 IDL 結構。|
|[id](id.md)|指定成員函式的 DISPID （屬性或方法，在介面或分配介面中）。|
|[iid_is](iid-is.md)|指定介面指標所指向之 COM 介面的 IID。|
|[immediatebind](immediatebind.md)|表示資料庫將會在資料系結物件之屬性的所有變更時立即收到通知。|
|[importlib](importlib.md)|讓已編譯成其他類型程式庫的類型可供正在建立的類型程式庫使用。|
|[import](import.md)|指定另一個 .idl、. odl 或標頭檔，其中包含您想要從主要 .idl 檔案參考的定義。|
|[涉及](include-cpp.md)|指定要包含在產生的 .idl 檔案中的一或多個標頭檔。|
|[includelib](includelib-cpp.md)|導致 .idl 或 .h 檔案包含在產生的 .idl 檔案中。|
|[in](in-cpp.md)|表示參數會從呼叫程式傳遞至被呼叫的進程。|
|[last_is](last-is.md)|指定要傳送之最後一個陣列元素的索引。|
|[lcid](lcid.md)|可讓您將地區設定識別碼傳遞給函式。|
|[length_is](length-is.md)|指定要傳送的陣列元素數目。|
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
|[propputref](propputref.md)|指定使用參考而非值的屬性設定函數。|
|[propput](propput.md)|指定屬性設定函式。|
|[ptr](ptr.md)|將指標指定為完整指標。|
|[public](public-cpp-attributes.md)|確保 typedef 會進入型別程式庫，即使它不是從 .idl 檔案中參考也一樣。|
|[range](range-cpp.md)|針對在執行時間設定其值的引數或欄位，指定允許的值範圍。|
|[唯讀](readonly-cpp.md)|禁止指派給變數。|
|[ref](ref-cpp.md)|識別參考指標。|
|[requestedit](requestedit.md)|表示屬性支援 `OnRequestEdit` 通知。|
|[約束](restricted.md)|指定無法任意呼叫程式庫或模組、介面或分配介面的成員。|
|[retval](retval.md)|指定接收成員之傳回值的參數。|
|[size_is](size-is.md)|指定配置給大小指標的記憶體大小、大小指標的大小指標，以及單一或多維陣列。|
|[source](source-cpp.md)|表示類別、屬性或方法的成員是事件的來源。|
|[string](string-cpp.md)|表示一維 **`char`** 、 **`wchar_t`** 、 `byte` 或對等陣列，或這類陣列的指標必須被視為字串。|
|[switch_is](switch-is.md)|指定作為 union 判別的運算式或識別碼，以選取聯集成員。|
|[switch_type](switch-type.md)|識別用來做為聯集判別之變數的類型。|
|[transmit_as](transmit-as.md)|指示編譯器將呈現的型別（用戶端和伺服器應用程式操作）與傳輸的型別產生關聯。|
|[uidefault](uidefault.md)|表示類型資訊成員是要在使用者介面中顯示的預設成員。|
|[unique](unique-cpp.md)|指定唯一的指標。|
|[usesgetlasterror](usesgetlasterror.md)|告訴呼叫者，如果呼叫該函式時發生錯誤，呼叫端可以呼叫 `GetLastError` 來抓取錯誤碼。|
|[uuid](uuid-cpp-attributes.md)|指定類別或介面的唯一識別碼。|
|[v1_enum](v1-enum.md)|指示指定的列舉型別會以32位實體的形式傳送，而不是16位的預設值。|
|[vararg](vararg.md)|指定函式接受可變數目的引數。|
|[vi_progid](vi-progid.md)|指定與版本無關的 ProgID 形式。|
|[wire_marshal](wire-marshal.md)|指定將用於傳輸的資料類型，而不是應用程式特定的資料類型。|

## <a name="see-also"></a>另請參閱

[依群組的屬性](attributes-by-group.md)
