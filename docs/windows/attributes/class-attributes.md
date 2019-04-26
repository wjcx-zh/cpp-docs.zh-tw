---
title: 類別屬性 (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], class attributes
ms.assetid: fad04ea1-d8ff-46d4-bb42-2b4500a6ab60
ms.openlocfilehash: d0913d09c51734f5255271c0d06e639810e0cb58
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148415"
---
# <a name="class-attributes"></a>類別屬性

下列屬性套用至[類別](../../cpp/class-cpp.md)C++關鍵字。

|屬性|描述|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|表示類別，支援彙總。|
|[aggregates](aggregates.md)|表示控制項彙總的目標類別。|
|[appobject](appobject.md)|識別做為應用程式物件，這是完整的.exe 應用程式相關聯，並指出函數和屬性的 coclass 全域使用這個類型程式庫中的 coclass。|
|[case](case-cpp.md)|搭配[switch_type](switch-type.md)等位中的屬性。|
|[coclass](coclass.md)|建立 ActiveX 控制項。|
|[com_interface_entry](com-interface-entry-cpp.md)|將 COM 對應中的介面項目。|
|[control](control.md)|指定使用者定義型別為控制項。|
|[custom](custom-cpp.md)|可讓您定義您自己的屬性。|
|[db_command](db-command.md)|建立 OLE DB 命令。|
|[db_param](db-param.md)|關聯的輸入或輸出參數中指定的成員變數，並分隔的變數。|
|[db_source](db-source.md)|建立資料來源的連接。|
|[db_table](db-table.md)|開啟 OLE DB 資料表。|
|[default](default-cpp.md)|表示 coclass 內定義的自訂或 dispinterface，用以代表預設可程式性介面。|
|[defaultvtable](defaultvtable.md)|為控制項的預設 vtable 介面中定義的介面。|
|[event_receiver](event-receiver.md)|建立事件接收器。|
|[event_source](event-source.md)|建立事件來源。|
|[helpcontext](helpcontext.md)|指定的內容識別碼，可讓使用者檢視中此項目相關的資訊**協助**檔案。|
|[helpfile](helpfile.md)|設定型別程式庫的說明檔的名稱。|
|[helpstringcontext](helpstringcontext.md)|指定.hlp 或.chm 檔案中的說明主題的識別碼。|
|[helpstring](helpstring.md)|指定用來描述所套用之項目的字元字串。|
|[hidden](hidden.md)|表示項目存在，但不是會顯示在使用者導向的瀏覽器中。|
|[implements](implements-cpp.md)|指定分派介面，強制讓 IDL coclass 的成員。|
|[implements_category](implements-category.md)|指定類別的實作的元件類別。|
|[module](module-cpp.md)|在 .idl 檔案中定義程式庫區塊。|
|[noncreatable](noncreatable.md)|定義本身無法具現化的物件。|
|[progid](progid.md)|定義控制項 ProgID。|
|[registration_script](registration-script.md)|執行指定的註冊指令碼。|
|[requestedit](requestedit.md)|表示屬性支援 `OnRequestEdit` 通知。|
|[source](source-cpp.md)|指定控制項的連接點的來源介面的類別上。 在屬性或方法，`source`屬性會指出成員傳回的物件或`VARIANT`也就是事件來源。|
|[support_error_info](support-error-info.md)|支援目標物件的錯誤報告功能。|
|[threading](threading-cpp.md)|指定控制項的執行緒模型。|
|[uuid](uuid-cpp-attributes.md)|指定類別或介面的唯一識別碼。|
|[version](version-cpp.md)|識別類別的多個版本之間的特定版本。|
|[vi_progid](vi-progid.md)|指定與版本無關的 ProgID 表單。|

## <a name="see-also"></a>另請參閱

[依使用方式分類的屬性](attributes-by-usage.md)