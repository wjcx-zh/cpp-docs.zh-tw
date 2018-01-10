---
title: "類別屬性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- attributes [C++], class attributes
- class attributes
ms.assetid: fad04ea1-d8ff-46d4-bb42-2b4500a6ab60
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: afc3f277170dbbdf92f280d341bffb042ab70af2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="class-attributes"></a>類別屬性
下列屬性套用至[類別](../cpp/class-cpp.md)c + + 關鍵字。  
  
|屬性|描述|  
|---------------|-----------------|  
|[aggregatable](../windows/aggregatable.md)|表示此類別支援彙總。|  
|[aggregates](../windows/aggregates.md)|表示控制項彙總的目標類別。|  
|[appobject](../windows/appobject.md)|識別為的應用程式物件，其完整的.exe 應用程式相關聯，並指出函式和 coclass 的屬性都是全域使用這個類型程式庫的 coclass。|  
|[case](../windows/case-cpp.md)|搭配[switch_type](../windows/switch-type.md)等位中的屬性。|  
|[coclass](../windows/coclass.md)|建立 ActiveX 控制項。|  
|[com_interface_entry](../windows/com-interface-entry-cpp.md)|將介面項目加入至 COM 對應。|  
|[control](../windows/control.md)|指定使用者定義型別是控制項。|  
|[自訂](../windows/custom-cpp.md)|可讓您定義您自己的屬性。|  
|[db_command](../windows/db-command.md)|建立 OLE DB 命令。|  
|[db_param](../windows/db-param.md)|關聯的輸入或輸出參數中指定的成員變數，分隔的變數。|  
|[db_source](../windows/db-source.md)|建立資料來源的連接。|  
|[db_table](../windows/db-table.md)|開啟 OLE DB 資料表。|  
|[default](../windows/default-cpp.md)|表示 coclass 內定義的自訂或 dispinterface，用以代表預設可程式性介面。|  
|[defaultvtable](../windows/defaultvtable.md)|為控制項的預設 vtable 介面定義的介面。|  
|[event_receiver](../windows/event-receiver.md)|建立事件接收器。|  
|[event_source](../windows/event-source.md)|建立事件來源。|  
|[helpcontext](../windows/helpcontext.md)|指定的內容識別碼，可讓使用者檢視的說明檔中此項目有關的資訊。|  
|[helpfile](../windows/helpfile.md)|設定型別程式庫的說明檔的名稱。|  
|[helpstringcontext](../windows/helpstringcontext.md)|指定.hlp 或.chm 檔案中的說明主題的識別碼。|  
|[helpstring](../windows/helpstring.md)|指定的字元字串，用來描述它所套用的項目。|  
|[hidden](../windows/hidden.md)|表示項目存在，但不是會顯示在使用者導向的瀏覽器中。|  
|[實作](../windows/implements-cpp.md)|指定強制為成員的 IDL coclass 的分派介面。|  
|[implements_category](../windows/implements-category.md)|指定此類別實作的元件類別。|  
|[模組](../windows/module-cpp.md)|在 .idl 檔案中定義程式庫區塊。|  
|[noncreatable](../windows/noncreatable.md)|定義本身無法具現化的物件。|  
|[progid](../windows/progid.md)|定義控制項 ProgID。|  
|[registration_script](../windows/registration-script.md)|執行指定的註冊指令碼。|  
|[requestedit](../windows/requestedit.md)|表示屬性支援**OnRequestEdit**通知。|  
|[來源](../windows/source-cpp.md)|在類別上指定控制項的連接點的來源介面。 在屬性或方法，**來源**屬性會指出成員傳回的物件或為資料來源的事件的 VARIANT。|  
|[support_error_info](../windows/support-error-info.md)|支援的錯誤報告目標物件。|  
|[執行緒處理](../windows/threading-cpp.md)|指定控制項的執行緒模型。|  
|[uuid](../windows/uuid-cpp-attributes.md)|指定類別或介面的唯一識別碼。|  
|[version](../windows/version-cpp.md)|識別類別的多個版本之間的特定版本。|  
|[vi_progid](../windows/vi-progid.md)|指定版本無關的 ProgID 的表單。|  
  
## <a name="see-also"></a>請參閱  
 [依使用方式分類的屬性](../windows/attributes-by-usage.md)