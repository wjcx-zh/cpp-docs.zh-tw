---
title: "Method Attributes | Microsoft Docs"
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
  - "method attributes"
  - "attributes [C++], reference topics"
ms.assetid: b2313352-480d-488b-8c35-6242ffd3a549
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Method Attributes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列的屬性套用至類別、 coclass 或介面中的方法。  
  
|屬性|描述|  
|--------|--------|  
|[bindable](../windows/bindable.md)|指示屬性支援資料繫結。|  
|[call\_as](../windows/call-as.md)|啟用 nonremotable 函式，以對應至遠端函式。|  
|[custom](../windows/custom-cpp.md)|讓您定義您自己的屬性。|  
|[db\_column](../windows/db-column.md)|將指定的資料行繫結至資料列集。|  
|[db\_command](../windows/db-command.md)|建立 OLE DB 命令一樣。|  
|[db\_param](../windows/db-param.md)|將指定的成員變數以輸入或輸出參數相關聯，用來分隔的變數。|  
|[db\_source](../windows/db-source.md)|建立資料來源的連接。|  
|[db\_table](../windows/db-table.md)|OLE DB 表格會跚|  
|[defaultbind](../windows/defaultbind.md)|表示可最佳表示物件的單一、 可繫結屬性。|  
|[defaultcollelem](../windows/defaultcollelem.md)|用於 Visual Basic 程式碼引發事件。|  
|[displaybind](../windows/displaybind.md)|表示應該顯示給使用者，可繫結之屬性。|  
|[helpcontext](../windows/helpcontext.md)|指定的主題代碼，可讓使用者檢視此說明檔中的項目相關的資訊。|  
|[說明檔案](../windows/helpfile.md)|設定型別程式庫的 \[說明\] 檔案名稱。|  
|[helpstring](../windows/helpstring.md)|指定用來描述所套用之項目的字元字串，|  
|[helpstringcontext](../windows/helpstringcontext.md)|指定.hlp 或.chm 檔中的 \[說明\] 主題的識別碼。|  
|[helpstringdll](../windows/helpstringdll.md)|指定要用來執行文件字串查閱 \(當地語系化\) 之 DLL 的名稱。|  
|[hidden](../windows/hidden.md)|表示該項目存在，但不是會顯示在使用者導向的瀏覽器中。|  
|[id](../windows/id.md)|指定的成員函式 \(屬性或方法，在介面或分配介面\) 的 DISPID。|  
|[immediatebind](../windows/immediatebind.md)|指示資料庫將立即被告知資料繫結物件的屬性的所有變更。|  
|[in](../windows/in-cpp.md)|表示參數從呼叫的程序傳遞至被呼叫的程序。|  
|[local](../windows/local-cpp.md)|可讓您使用 MIDL 編譯器，做一個標頭的產生器介面的標頭中使用時。  個別函式中使用時，會指定產生的任何虛設常式區域的程序。|  
|[nonbrowsable](../windows/nonbrowsable.md)|指示介面成員不會顯示在屬性瀏覽器。|  
|[propget 而言](../windows/propget.md)|指定的屬性存取子函式。|  
|[propput](../windows/propput.md)|指定函式屬性設定值。|  
|[propputref](../windows/propputref.md)|指定的值，而不是使用參考的屬性設定值函式。|  
|[ptr](../windows/ptr.md)|指定變數的指標做為完整的指標。|  
|[範圍](../windows/range-cpp.md)|指定引數，或是在 run time 設定其值的欄位的允許值的範圍。|  
|[requestedit](../windows/requestedit.md)|指示屬性支援 **OnRequestEdit** 通知。|  
|[restricted](../windows/restricted.md)|指定的模組、 介面或分配介面成員無法被任意呼叫。|  
|[satype](../windows/satype.md)|指定的資料型別**安全陣列時發生**結構。|  
|[source](../windows/source-cpp.md)|在類別上指定的連接點的控制項的來源介面。  在 \[屬性或方法， **來源**屬性表示成員傳回一個物件或 VARIANT 是一個事件的來源。|  
|[同步處理](../windows/synchronize.md)|同步處理對目標方法的存取。|  
|[vararg](../windows/vararg.md)|指定函式接受不同數目引數。|  
  
## 請參閱  
 [Attributes by Usage](../windows/attributes-by-usage.md)