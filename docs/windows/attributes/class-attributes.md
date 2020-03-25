---
title: 類別屬性（C++ COM）
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], class attributes
ms.assetid: fad04ea1-d8ff-46d4-bb42-2b4500a6ab60
ms.openlocfilehash: 5e10b7831e59211b73ce947ac21e43bc1a8af1c9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167312"
---
# <a name="class-attributes"></a>類別屬性

下列屬性適用于[class](../../cpp/class-cpp.md) C++關鍵字。

|屬性|描述|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|表示類別支援匯總。|
|[aggregates](aggregates.md)|表示控制項會匯總目標類別。|
|[appobject](appobject.md)|將 coclass 識別為與完整 .exe 應用程式相關聯的應用程式物件，並指出 coclass 的函式和屬性在此類型程式庫中可全域使用。|
|[case](case-cpp.md)|與聯集內的[switch_type](switch-type.md)屬性搭配使用。|
|[coclass](coclass.md)|建立 ActiveX 控制項。|
|[com_interface_entry](com-interface-entry-cpp.md)|將介面專案加入至 COM 對應。|
|[control](control.md)|指定使用者定義型別為控制項。|
|[custom](custom-cpp.md)|可讓您定義自己的屬性。|
|[db_command](db-command.md)|建立 OLE DB 命令。|
|[db_param](db-param.md)|將指定的成員變數與輸入或輸出參數產生關聯，並分隔變數。|
|[db_source](db-source.md)|建立與資料來源的連接。|
|[db_table](db-table.md)|開啟 OLE DB 資料表。|
|[預設值](default-cpp.md)|表示 coclass 內定義的自訂或 dispinterface，用以代表預設可程式性介面。|
|[defaultvtable](defaultvtable.md)|將介面定義為控制項的預設 vtable 介面。|
|[event_receiver](event-receiver.md)|建立事件接收器。|
|[event_source](event-source.md)|建立事件來源。|
|[helpcontext](helpcontext.md)|指定內容識別碼，讓使用者可在說明檔中查看此**元素的相關**資訊。|
|[helpfile](helpfile.md)|設定類型程式庫的說明檔名稱。|
|[helpstringcontext](helpstringcontext.md)|在 .hlp 或 .chm 檔案中指定說明主題的識別碼。|
|[helpstring](helpstring.md)|指定用來描述所套用之項目的字元字串。|
|[hidden](hidden.md)|表示專案存在，但不應該顯示在使用者導向的瀏覽器中。|
|[implements](implements-cpp.md)|指定強制成為 IDL coclass 成員的分派介面。|
|[implements_category](implements-category.md)|指定類別的實作為元件類別。|
|[name](module-cpp.md)|在 .idl 檔案中定義程式庫區塊。|
|[noncreatable](noncreatable.md)|定義無法自行具現化的物件。|
|[progid](progid.md)|定義控制項的 ProgID。|
|[registration_script](registration-script.md)|執行指定的註冊腳本。|
|[requestedit](requestedit.md)|表示屬性支援 `OnRequestEdit` 通知。|
|[來源](source-cpp.md)|為類別上的連接點指定控制項的來源介面。 在屬性或方法上，`source` 屬性會指出該成員會傳回屬於事件來源的物件或 `VARIANT`。|
|[support_error_info](support-error-info.md)|支援目標物件的錯誤報表。|
|[threading](threading-cpp.md)|指定控制項的執行緒模型。|
|[uuid](uuid-cpp-attributes.md)|指定類別或介面的唯一識別碼。|
|[version](version-cpp.md)|識別類別的多個版本之間的特定版本。|
|[vi_progid](vi-progid.md)|指定與版本無關的 ProgID 形式。|

## <a name="see-also"></a>另請參閱

[依使用方式分類的屬性](attributes-by-usage.md)
