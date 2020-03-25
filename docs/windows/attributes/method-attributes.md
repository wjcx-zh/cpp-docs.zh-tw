---
title: 方法屬性（C++ COM）
ms.date: 10/02/2018
helpviewer_keywords:
- method attributes
- attributes [C++/CLI], reference topics
ms.assetid: b2313352-480d-488b-8c35-6242ffd3a549
ms.openlocfilehash: c9823869be96f53a3c4fbc36c7b56e1bea0a1303
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166766"
---
# <a name="method-attributes"></a>方法屬性

下列屬性適用于類別、coclass 或介面中的方法。

|屬性|描述|
|---------------|-----------------|
|[bindable](bindable.md)|表示支援資料繫結的屬性。|
|[call_as](call-as.md)|讓不可遠端處理函數能夠對應至遠端函式。|
|[custom](custom-cpp.md)|可讓您定義自己的屬性。|
|[db_column](db-column.md)|將指定的資料行系結至資料列集。|
|[db_command](db-command.md)|建立 OLE DB 命令。|
|[db_param](db-param.md)|將指定的成員變數與輸入或輸出參數產生關聯，並分隔變數。|
|[db_source](db-source.md)|建立與資料來源的連接。|
|[db_table](db-table.md)|開啟 OLE DB 資料表。|
|[defaultbind](defaultbind.md)|表示最能代表物件的單一可系結屬性。|
|[defaultcollelem](defaultcollelem.md)|用於 Visual Basic 程式碼優化。|
|[displaybind](displaybind.md)|表示應該向使用者顯示為可系結的屬性。|
|[helpcontext](helpcontext.md)|指定內容識別碼，讓使用者可在說明檔中查看此**元素的相關**資訊。|
|[helpfile](helpfile.md)|設定類型連結**庫的說明**檔名稱。|
|[helpstring](helpstring.md)|指定用來描述所套用之項目的字元字串。|
|[helpstringcontext](helpstringcontext.md)|在 .hlp 或 .chm 檔案中指定說明主題的識別碼。|
|[helpstringdll](helpstringdll.md)|指定要用來執行檔字串查閱（當地語系化）之 DLL 的名稱。|
|[hidden](hidden.md)|表示專案存在，但不應該顯示在使用者導向的瀏覽器中。|
|[id](id.md)|指定成員函式的 DISPID （屬性或方法，在介面或分配介面中）。|
|[immediatebind](immediatebind.md)|表示資料庫將會在資料系結物件之屬性的所有變更時立即收到通知。|
|[in](in-cpp.md)|表示參數會從呼叫程式傳遞至被呼叫的進程。|
|[local](local-cpp.md)|當用於介面標頭時，可讓您使用 MIDL 編譯器做為標頭產生器。 在個別函式中使用時，會指定不會產生任何存根的本機程式。|
|[nonbrowsable](nonbrowsable.md)|表示介面成員不應顯示在屬性瀏覽器中。|
|[propget](propget.md)|指定屬性存取子函數。|
|[propput](propput.md)|指定屬性設定函數。|
|[propputref](propputref.md)|指定使用參考而非值的屬性設定函數。|
|[ptr](ptr.md)|將指標指定為完整指標。|
|[range](range-cpp.md)|針對在執行時間設定其值的引數或欄位，指定允許的值範圍。|
|[requestedit](requestedit.md)|表示屬性支援 `OnRequestEdit` 通知。|
|[restricted](restricted.md)|指定不能任意呼叫模組、介面或分配介面的成員。|
|[satype](satype.md)|指定 `SAFEARRAY` 結構的資料類型。|
|[來源](source-cpp.md)|為類別上的連接點指定控制項的來源介面。 在屬性或方法上，`source` 屬性會指出該成員會傳回屬於事件來源的物件或 VARIANT。|
|[synchronize](synchronize.md)|同步處理對目標方法的存取。|
|[vararg](vararg.md)|指定函式接受可變數目的引數。|

## <a name="see-also"></a>另請參閱

[依使用方式分類的屬性](attributes-by-usage.md)
