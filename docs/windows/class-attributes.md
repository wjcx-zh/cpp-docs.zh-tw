---
title: "Class Attributes | Microsoft Docs"
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
  - "attributes [C++], class attributes"
  - "class attributes"
ms.assetid: fad04ea1-d8ff-46d4-bb42-2b4500a6ab60
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Class Attributes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列屬性套用於[類別](../cpp/class-cpp.md) C\+\+ 關鍵字。  
  
|屬性|描述|  
|--------|--------|  
|[可彙總](../windows/aggregatable.md)|指示此類別支援彙總。|  
|[彙總](../windows/aggregates.md)|表示控制項彙總的目標類別。|  
|[appobject](../windows/appobject.md)|識別做為應用程式物件，這是完整的.exe 應用程式相關聯，表示這個型別程式庫中的函式和 coclass 的屬性可使用全域 coclass。|  
|[case](../windows/case-cpp.md)|搭配 [switch\_type](../windows/switch-type.md) 等位中的屬性。|  
|[coclass](../windows/coclass.md)|會建立 ActiveX 控制項。|  
|[com\_interface\_entry](../windows/com-interface-entry-cpp.md)|將介面項目加入至 COM 對應。|  
|[控制項](../windows/control.md)|指定的使用者定義型別是一種控制項。|  
|[custom](../windows/custom-cpp.md)|讓您定義您自己的屬性。|  
|[db\_command](../windows/db-command.md)|建立 OLE DB 命令一樣。|  
|[db\_param](../windows/db-param.md)|將指定的成員變數以輸入或輸出參數相關聯，用來分隔的變數。|  
|[db\_source](../windows/db-source.md)|建立資料來源的連接。|  
|[db\_table](../windows/db-table.md)|OLE DB 表格會跚|  
|[default](../windows/default-cpp.md)|指示自訂或分配介面所定義的 coclass 代表預設的可程式化介面。|  
|[defaultvtable](../windows/defaultvtable.md)|控制項的預設 vtable 介面中定義的介面。|  
|[event\_receiver](../windows/event-receiver.md)|建立事件接收器。|  
|[event\_source](../windows/event-source.md)|建立事件來源。|  
|[helpcontext](../windows/helpcontext.md)|指定的主題代碼，可讓使用者檢視此說明檔中的項目相關的資訊。|  
|[說明檔案](../windows/helpfile.md)|設定型別程式庫的 \[說明\] 檔案名稱。|  
|[helpstringcontext](../windows/helpstringcontext.md)|指定.hlp 或.chm 檔中的 \[說明\] 主題的識別碼。|  
|[helpstring](../windows/helpstring.md)|指定用來描述所套用之項目的字元字串，|  
|[hidden](../windows/hidden.md)|表示該項目存在，但不是會顯示在使用者導向的瀏覽器中。|  
|[implements](../windows/implements-cpp.md)|指定強制為 IDL coclass 的成員的分派介面。|  
|[implements\_category](../windows/implements-category.md)|指定實作的元件類別的類別目錄。|  
|[Module \- 模組](../windows/module-cpp.md)|定義文件庫區塊.idl 檔中。|  
|[變成無法建立](../windows/noncreatable.md)|定義無法單獨執行個體化的物件。|  
|[progid](../windows/progid.md)|定義控制項的 ProgID。|  
|[registration\_script](../windows/registration-script.md)|執行指定的登錄指令碼。|  
|[requestedit](../windows/requestedit.md)|指示屬性支援 **OnRequestEdit** 通知。|  
|[source](../windows/source-cpp.md)|在類別上指定的連接點的控制項的來源介面。  在 \[屬性或方法， **來源**屬性表示成員傳回一個物件或 VARIANT 是一個事件的來源。|  
|[support\_error\_info](../windows/support-error-info.md)|支援的目標物件的錯誤報告功能。|  
|[執行緒處理](../windows/threading-cpp.md)|指定控制項的執行緒模型。|  
|[uuid](../windows/uuid-cpp-attributes.md)|指定類別或介面的專一識別碼。|  
|[version](../windows/version-cpp.md)|識別類別的多個版本之間的特定版本。|  
|[vi\_progid](../windows/vi-progid.md)|指定版本無關的形式的 ProgID。|  
  
## 請參閱  
 [Attributes by Usage](../windows/attributes-by-usage.md)