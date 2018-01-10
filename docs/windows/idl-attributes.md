---
title: "IDL 屬性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- attributes [C++], reference topics
- IDL attributes
- .idl files, attributes
- IDL files, attributes
- .idl files
ms.assetid: 04c596f4-c97b-4952-8053-316678b1d0b6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 447c4369d7a80348dfb6c5eee54c49d76c1e8a4c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="idl-attributes"></a>IDL 屬性
傳統上，維持.idl 檔案，表示您必須以：  
  
-   要熟悉之結構和語法的.idl 檔案能夠修改它。  
  
-   依賴精靈，可讓您修改.idl 檔的某些層面。  
  
 現在，您可以修改從.idl 檔中的原始程式碼檔使用的 Visual c + + IDL 屬性。 在許多情況下，Visual c + + IDL 屬性有 MIDL 屬性相同的名稱。 Visual c + + IDL 屬性和 MIDL 屬性的名稱相同時，這表示，置於您的原始程式碼檔中的 Visual c + + 屬性時會產生.idl 檔包含其 namesake MIDL 屬性中。 不過，Visual c + + IDL 屬性可能不會提供 MIDL 屬性的所有功能。  
  
 不搭配使用時[COM 屬性](../windows/com-attributes.md)，IDL 屬性可讓您定義介面。 當編譯原始程式碼時，屬性用來定義產生的.idl 檔案。 ATL 專案中的 COM 屬性搭配使用時，某些 IDL 屬性，例如**coclass**，使程式碼插入至專案。  
  
 請注意， [idl_quote](../windows/idl-quote.md)可讓您使用目前版本的 Visual c + + 中不支援的 MIDL 建構。 這和其他屬性，例如[importlib](../windows/importlib.md)和[includelib](../windows/includelib-cpp.md)幫助您使用目前的 Visual c + + 專案中現有的.idl 檔案。  
  
|屬性|描述|  
|---------------|-----------------|  
|[aggregatable](../windows/aggregatable.md)|表示控制項，可以由另一個控制彙總。|  
|[appobject](../windows/appobject.md)|識別為的應用程式物件，其完整的 EXE 應用程式相關聯，並指出函式和 coclass 的屬性都是全域使用這個類型程式庫的 coclass。|  
|[async_uuid](../windows/async-uuid.md)|指定指示 MIDL 編譯器定義 COM 介面的同步和非同步版本的 UUID。|  
|[bindable](../windows/bindable.md)|表示屬性支援資料繫結。|  
|[call_as](../windows/call-as.md)|讓分為函式對應至遠端函式。|  
|[case](../windows/case-cpp.md)|搭配[switch_type](../windows/switch-type.md)等位中的屬性。|  
|[coclass](../windows/coclass.md)|上的芳鄰類別至.idl 檔案為 coclass 的定義。|  
|[control](../windows/control.md)|指定使用者定義型別是控制項。|  
|[cpp_quote](../windows/cpp-quote.md)|指定的字串，不能包含引號字元，發出至產生的標頭檔。|  
|[defaultbind](../windows/defaultbind.md)|表示最能代表物件的單一、 可繫結屬性。|  
|[defaultcollelem](../windows/defaultcollelem.md)|使用 Visual Basic 程式碼最佳化。|  
|[defaultvalue](../windows/defaultvalue.md)|允許指定具類型的選擇性參數的預設值。|  
|[default](../windows/default-cpp.md)|表示 coclass 內定義的自訂或 dispinterface，用以代表預設可程式性介面。|  
|[defaultvtable](../windows/defaultvtable.md)|為控制項的預設 vtable 介面定義的介面。|  
|[dispinterface](../windows/dispinterface.md)|將介面放入 .idl 檔案中作為分派介面。|  
|[displaybind](../windows/displaybind.md)|指出應該顯示給使用者，作為可繫結的屬性。|  
|[dual](../windows/dual.md)|雙重介面置於.idl 檔案介面。|  
|[entry](../windows/entry.md)|識別 DLL 中的進入點在模組中指定的匯出函式或常數。|  
|[first_is](../windows/first-is.md)|指定要傳送的第一個陣列元素的索引。|  
|[helpcontext](../windows/helpcontext.md)|指定的內容識別碼，可讓使用者檢視的說明檔中此項目有關的資訊。|  
|[helpfile](../windows/helpfile.md)|設定型別程式庫的說明檔的名稱。|  
|[helpstringcontext](../windows/helpstringcontext.md)|指定.hlp 或.chm 檔案中的說明主題的識別碼。|  
|[helpstringdll](../windows/helpstringdll.md)|指定用來執行文件字串查閱 （當地語系化） 的 dll 名稱。|  
|[helpstring](../windows/helpstring.md)|指定的字元字串，用來描述它所套用的項目。|  
|[hidden](../windows/hidden.md)|表示項目存在，但不是會顯示在使用者導向的瀏覽器中。|  
|[idl_module](../windows/idl-module.md)|指定的進入點 DLL 中。|  
|[idl_quote](../windows/idl-quote.md)|可讓您使用屬性或 IDL 建構的目前版本的 Visual c + + 中不支援。|  
|[id](../windows/id.md)|指定 DISPID 成員函式 （屬性或方法，在介面或 dispinterface）。|  
|[iid_is](../windows/iid-is.md)|指定的介面指標所指向的 COM 介面的 IID。|  
|[immediatebind](../windows/immediatebind.md)|指示資料庫將會立即被告知資料繫結物件的屬性的所有變更。|  
|[importlib](../windows/importlib.md)|讓已編譯成其他類型程式庫的類型可供正在建立的類型程式庫使用。|  
|[import](../windows/import.md)|指定包含的定義您想要從主要的.idl 檔案參考的另一個.idl、.odl 或標頭檔。|  
|[include](../windows/include-cpp.md)|指定要包含在產生的.idl 檔中的一個或多個標頭檔。|  
|[includelib](../windows/includelib-cpp.md)|會導致的.idl 或.h 檔案包含在產生的.idl 檔案。|  
|[in](../windows/in-cpp.md)|指出參數是要呼叫的程序從傳遞給呼叫的程序。|  
|[last_is](../windows/last-is.md)|指定要傳送的最後一個陣列元素的索引。|  
|[lcid](../windows/lcid.md)|可讓您將地區設定識別碼傳遞給函式。|  
|[length_is](../windows/length-is.md)|指定要傳送的陣列元素數目。|  
|[licensed](../windows/licensed.md)|表示要套用的 coclass 係授權使用，而且必須使用具現化**IClassFactory2**。|  
|[本機](../windows/local-cpp.md)|可讓您使用 MIDL 編譯器為標頭產生器時用於介面標頭。 個別的函式中使用時，會指定產生的任何虛設常式區域的程序。|  
|[max_is](../windows/max-is.md)|指定有效的陣列索引的最大值。|  
|[模組](../windows/module-cpp.md)|在 .idl 檔案中定義程式庫區塊。|  
|[ms_union](../windows/ms-union.md)|控制 nonencapsulated 等位的網路資料表示對齊方式。|  
|[no_injected_text](../windows/no-injected-text.md)|防止編譯器插入程式碼，因為屬性使用。|  
|[nonbrowsable](../windows/nonbrowsable.md)|表示某個介面成員不會顯示在屬性瀏覽器。|  
|[noncreatable](../windows/noncreatable.md)|定義本身無法具現化的物件。|  
|[nonextensible](../windows/nonextensible.md)|指定`IDispatch`實作只會包含屬性和方法的介面描述中所列，並且無法在執行階段擴充與其他成員。|  
|[object](../windows/object-cpp.md)|識別自訂的介面。自訂屬性的同義詞。|  
|[odl](../windows/odl.md)|識別為物件描述語言 (ODL) 介面的介面。|  
|[oleautomation](../windows/oleautomation.md)|表示與 Automation 相容介面。|  
|[選擇性](../windows/optional-cpp.md)|指定的成員函式的選擇性參數。|  
|[out](../windows/out-cpp.md)|識別從被呼叫程序傳回至呼叫程序的指標參數 (從伺服器至用戶端)。|  
|[pointer_default](../windows/pointer-default.md)|指定的預設指標屬性出現的最上層指標除外的所有指標的參數清單。|  
|[pragma](../windows/pragma.md)|指定的字串，不能包含引號字元，發出至產生的.idl 檔案。|  
|[progid](../windows/progid.md)|指定 COM 物件的 ProgID。|  
|[propget](../windows/propget.md)|指定屬性存取子 (get) 函式。|  
|[propputref](../windows/propputref.md)|指定使用參考而非值屬性設定函式。|  
|[propput](../windows/propput.md)|指定屬性設定函式。|  
|[ptr](../windows/ptr.md)|將指標指定為完整的指標。|  
|[public](../windows/public-cpp-attributes.md)|可確保 typedef 將移到型別程式庫，即使它並未參考從.idl 檔中。|  
|[範圍](../windows/range-cpp.md)|指定引數或在執行階段設定其值的欄位的允許值的範圍。|  
|[readonly](../windows/readonly-cpp.md)|禁止指派給變數。|  
|[ref](../windows/ref-cpp.md)|識別參考指標。|  
|[requestedit](../windows/requestedit.md)|表示屬性支援**OnRequestEdit**通知。|  
|[restricted](../windows/restricted.md)|指定的程式庫或模組、 介面或 dispinterface，用以的成員無法任意呼叫。|  
|[retval](../windows/retval.md)|指定接收成員的傳回值的參數。|  
|[size_is](../windows/size-is.md)|指定的記憶體大小配置大小的指標，調整大小的指標和單一或多維度陣列的指標。|  
|[來源](../windows/source-cpp.md)|表示類別、 屬性或方法的成員是事件來源。|  
|[string](../windows/string-cpp.md)|表示一維`char`， `wchar_t`，**位元組**，或對等陣列或這類陣列的指標必須視為字串。|  
|[switch_is](../windows/switch-is.md)|指定的運算式或做為選取的等位成員的聯集判別識別項。|  
|[switch_type](../windows/switch-type.md)|識別做為等位的判別變數的類型。|  
|[transmit_as](../windows/transmit-as.md)|指示編譯器將呈現的型別，用戶端和伺服器應用程式管理，與傳輸類型產生關聯。|  
|[uidefault](../windows/uidefault.md)|表示型別資訊成員的使用者介面中顯示的預設成員。|  
|[unique](../windows/unique-cpp.md)|指定唯一的指標。|  
|[usesgetlasterror](../windows/usesgetlasterror.md)|會告知呼叫端是否有錯誤時呼叫該函式，呼叫端可以接著呼叫`GetLastError`擷取錯誤碼。|  
|[uuid](../windows/uuid-cpp-attributes.md)|指定類別或介面的唯一識別碼。|  
|[v1_enum](../windows/v1-enum.md)|指示指定的列舉的類型傳輸為 32 位元的實體，而不是 16 位元的預設值。|  
|[vararg](../windows/vararg.md)|指定的函式接受可變數目的引數。|  
|[vi_progid](../windows/vi-progid.md)|指定版本無關的 ProgID 的表單。|  
|[wire_marshal](../windows/wire-marshal.md)|指定用於傳輸，而不是應用程式特定資料類型的資料類型。|  
  
## <a name="see-also"></a>請參閱  
 [依群組分類的屬性](../windows/attributes-by-group.md)   
 [屬性的限制](http://msdn.microsoft.com/en-us/6e6c4329-f667-4869-b991-cbe9cb7a8f61)