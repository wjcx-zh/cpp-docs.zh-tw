---
title: "IDL Attributes | Microsoft Docs"
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
  - "attributes [C++], reference topics"
  - "IDL attributes"
  - ".idl files, attributes"
  - "IDL files, attributes"
  - ".idl files"
ms.assetid: 04c596f4-c97b-4952-8053-316678b1d0b6
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDL Attributes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

傳統上，維持.idl 檔，代表您必須：  
  
-   先熟悉的結構和語法的.idl 檔，才能夠進行修改。  
  
-   只使用由精靈程式，就會讓您修改.idl 檔的某些方面指令碼。  
  
 現在，您可以修改從.idl 檔內的原始程式碼檔使用 Visual C\+\+ IDL 屬性。  在許多情況下，Visual C\+\+ IDL 屬性會有 MIDL 屬性相同的名稱。  Visual C\+\+ IDL 屬性和 MIDL 屬性的名稱相同時，就表示將 Visual C\+\+ 屬性放在您的原始程式檔中會造成.idl 檔，其中包含它的 namesake MIDL 屬性。  不過，Visual C\+\+ IDL 屬性可能不會提供 MIDL 屬性的所有功能。  
  
 不搭配使用時 [COM 屬性](../windows/com-attributes.md)，IDL 屬性可讓您定義介面。  當編譯的原始程式碼時，屬性用來定義產生的.idl 檔中。  與 COM 屬性的 ATL 專案中使用時，某些 IDL 屬性，例如 **coclass**，可全數插入專案的程式碼。  
  
 請注意，  [idl\_quote](../windows/idl-quote.md) 可讓您使用最新版的 Visual C\+\+ 中不支援的 MIDL 建構。  這和其他屬性，例如 [importlib](../windows/importlib.md) 和 [includelib](../windows/includelib-cpp.md) 幫助您使用目前的 Visual C\+\+ 專案中現有的.idl 檔。  
  
|屬性|描述|  
|--------|--------|  
|[可彙總](../windows/aggregatable.md)|表示控制項可以由另一個控制項彙總。|  
|[appobject](../windows/appobject.md)|識別做為應用程式物件，這是完整的 EXE 應用程式相關聯，表示這個型別程式庫中的函式和 coclass 的屬性可使用全域 coclass。|  
|[async\_uuid](../windows/async-uuid.md)|指定指示 MIDL 編譯器，將定義 COM 介面的同步和非同步版本的 UUID。|  
|[bindable](../windows/bindable.md)|指示屬性支援資料繫結。|  
|[call\_as](../windows/call-as.md)|啟用 nonremotable 函式，以對應至遠端函式。|  
|[case](../windows/case-cpp.md)|搭配 [switch\_type](../windows/switch-type.md) 等位中的屬性。|  
|[coclass](../windows/coclass.md)|放置類別為 coclass 至.idl 檔中定義。|  
|[控制項](../windows/control.md)|指定的使用者定義型別是一種控制項。|  
|[cpp\_quote](../windows/cpp-quote.md)|指定的字串，不能包含引號的字元，發出至產生的標頭檔。|  
|[defaultbind](../windows/defaultbind.md)|表示可最佳表示物件的單一、 可繫結屬性。|  
|[defaultcollelem](../windows/defaultcollelem.md)|用於 Visual Basic 程式碼引發事件。|  
|[預設值&#93;](../windows/defaultvalue.md)|容許指定型別的選擇性參數的預設值。|  
|[default](../windows/default-cpp.md)|指示自訂或分配介面所定義的 coclass 代表預設的可程式化介面。|  
|[defaultvtable](../windows/defaultvtable.md)|控制項的預設 vtable 介面中定義的介面。|  
|[dispinterface](../windows/dispinterface.md)|表示該工期為介面的分派介面為.idl 檔內的位置。|  
|[displaybind](../windows/displaybind.md)|表示應該顯示給使用者，可繫結之屬性。|  
|[dual](../windows/dual.md)|將.idl 檔內的介面以雙重介面。|  
|[項目](../windows/entry.md)|用來識別在 DLL 中的進入點在模組中指定的匯出函式或常數。|  
|[first\_is](../windows/first-is.md)|指定要傳送的第一個陣列元素的索引。|  
|[helpcontext](../windows/helpcontext.md)|指定的主題代碼，可讓使用者檢視此說明檔中的項目相關的資訊。|  
|[說明檔案](../windows/helpfile.md)|設定型別程式庫的 \[說明\] 檔案名稱。|  
|[helpstringcontext](../windows/helpstringcontext.md)|指定.hlp 或.chm 檔中的 \[說明\] 主題的識別碼。|  
|[helpstringdll](../windows/helpstringdll.md)|指定要用來執行文件字串查閱 \(當地語系化\) 之 DLL 的名稱。|  
|[helpstring](../windows/helpstring.md)|指定用來描述所套用之項目的字元字串，|  
|[hidden](../windows/hidden.md)|表示該項目存在，但不是會顯示在使用者導向的瀏覽器中。|  
|[idl\_module](../windows/idl-module.md)|指定在 DLL 的進入點。|  
|[idl\_quote](../windows/idl-quote.md)|可讓您使用屬性或 IDL 建構不在目前版本的 Visual C\+\+ 中支援。|  
|[id](../windows/id.md)|指定的成員函式 \(屬性或方法，在介面或分配介面\) 的 DISPID。|  
|[iid\_is](../windows/iid-is.md)|指定的介面指標所指向的 COM 介面的 IID。|  
|[immediatebind](../windows/immediatebind.md)|指示資料庫將立即被告知資料繫結物件的屬性的所有變更。|  
|[importlib](../windows/importlib.md)|讓已編譯成另一個型別程式庫所建立的型別程式庫，您可以使用的型別。|  
|[import](../windows/import.md)|指定包含您想要參考主要的.idl 檔中定義的另一個.idl、.odl 或標頭檔。|  
|[包含](../windows/include-cpp.md)|指定要包含在產生的.idl 檔中的一或多個標頭檔。|  
|[includelib](../windows/includelib-cpp.md)|會造成.idl 或.h 檔被包含在產生的.idl 檔。|  
|[in](../windows/in-cpp.md)|表示參數從呼叫的程序傳遞至被呼叫的程序。|  
|[last\_is](../windows/last-is.md)|指定要傳送的最後一個陣列元素的索引。|  
|[lcid](../windows/lcid.md)|可讓您傳遞至函式的地區設定識別項。|  
|[length\_is](../windows/length-is.md)|指定要傳送的陣列元素數目。|  
|[授權](../windows/licensed.md)|表示它所套用的 coclass 授權而，且必須使用執行個體化 **IClassFactory2**。|  
|[local](../windows/local-cpp.md)|可讓您使用 MIDL 編譯器，做一個標頭的產生器介面的標頭中使用時。  個別函式中使用時，會指定產生的任何虛設常式區域的程序。|  
|[max\_is](../windows/max-is.md)|請指定有效的陣列索引的最大值。|  
|[Module \- 模組](../windows/module-cpp.md)|定義文件庫區塊.idl 檔中。|  
|[ms\_union](../windows/ms-union.md)|控制網路資料表示對齊，nonencapsulated 的聯集。|  
|[no\_injected\_text](../windows/no-injected-text.md)|可以防止編譯器插入的屬性使用的程式碼。|  
|[nonbrowsable](../windows/nonbrowsable.md)|指示介面成員不會顯示在屬性瀏覽器。|  
|[變成無法建立](../windows/noncreatable.md)|定義無法單獨執行個體化的物件。|  
|[nonextensible](../windows/nonextensible.md)|指定的`IDispatch`實作包括僅屬性以及方法介面描述中所列，並不能與其他成員在執行階段擴充。|  
|[object](../windows/object-cpp.md)|識別自訂介面。 等於自訂屬性。|  
|[odl](../windows/odl.md)|識別為物件描述語言 \(ODL\) 介面的介面。|  
|[oleautomation](../windows/oleautomation.md)|指示介面適用於自動化。|  
|[選擇性](../windows/optional-cpp.md)|指定選擇性參數的成員函式。|  
|[out](../windows/out-cpp.md)|識別指標參數從被呼叫的程序傳回呼叫的程序 \(從伺服器到用戶端\)。|  
|[pointer\_default](../windows/pointer-default.md)|指定的預設指標屬性，除了顯示的最上層指標的所有指標參數清單中。|  
|[pragma](../windows/pragma.md)|指定的字串，不能包含引號的字元，發出至產生的.idl 檔。|  
|[progid](../windows/progid.md)|指定 COM 物件的 ProgID。|  
|[propget 而言](../windows/propget.md)|指定的屬性存取子 \(get\) 函式。|  
|[propputref](../windows/propputref.md)|指定的值，而不是使用參考的屬性設定函式。|  
|[propput](../windows/propput.md)|指定的屬性設定函式。|  
|[ptr](../windows/ptr.md)|指定變數的指標做為完整的指標。|  
|[public](../windows/public-cpp-attributes.md)|可確保 typedef 就會變為型別程式庫，即使它未被參考的.idl 檔內。|  
|[範圍](../windows/range-cpp.md)|指定引數，或是在 run time 設定其值的欄位的允許值的範圍。|  
|[readonly](../windows/readonly-cpp.md)|禁止指派給變數。|  
|[ref](../windows/ref-cpp.md)|識別的參考指標。|  
|[requestedit](../windows/requestedit.md)|指示屬性支援 **OnRequestEdit** 通知。|  
|[restricted](../windows/restricted.md)|指定的文件庫或模組、 介面或分配介面的成員不能被隨意呼叫。|  
|[retval](../windows/retval.md)|指定接收成員傳回值的參數。|  
|[size\_is](../windows/size-is.md)|指定的記憶體大小配置大小的指標、 調整大小來調整大小的指標，以及單或多維陣列的指標。|  
|[source](../windows/source-cpp.md)|表示類別、 屬性或方法的成員是一個事件的來源。|  
|[string](../windows/string-cpp.md)|表示一維`char`， `wchar_t`， **位元組**，或對等的陣列或這類陣列的指標必須被視為字串。|  
|[switch\_is](../windows/switch-is.md)|指定做為選取的聯集的成員聯集判別識別碼的運算式。|  
|[switch\_type](../windows/switch-type.md)|識別做為聯合判別變數的型別。|  
|[transmit\_as](../windows/transmit-as.md)|指示編譯器將呈現的類型，哪些用戶端和伺服器應用程式操作，與傳輸類型產生關聯。|  
|[uidefault](../windows/uidefault.md)|表示型別資訊成員是在使用者介面中顯示的預設成員。|  
|[唯一](../windows/unique-cpp.md)|指定唯一的指標。|  
|[usesgetlasterror](../windows/usesgetlasterror.md)|告知呼叫端呼叫該函式時，卻發生錯誤，是否呼叫端可以再呼叫`GetLastError`以取得錯誤的程式碼。|  
|[uuid](../windows/uuid-cpp-attributes.md)|指定類別或介面的專一識別碼。|  
|[v1\_enum](../windows/v1-enum.md)|指示指定的列舉型別來傳輸為 32 位元實體，而不是 16 位元的預設值。|  
|[vararg](../windows/vararg.md)|指定函式接受不同數目引數。|  
|[vi\_progid](../windows/vi-progid.md)|指定版本無關的形式的 ProgID。|  
|[wire\_marshal](../windows/wire-marshal.md)|指定將用於傳輸，而不是應用程式特定資料型別的資料型別。|  
  
## 請參閱  
 [Attributes by Group](../windows/attributes-by-group.md)   
 [Attribute Limitations](http://msdn.microsoft.com/zh-tw/6e6c4329-f667-4869-b991-cbe9cb7a8f61)