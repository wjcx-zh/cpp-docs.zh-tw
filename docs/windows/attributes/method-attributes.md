---
title: 方法屬性 (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- method attributes
- attributes [C++/CLI], reference topics
ms.assetid: b2313352-480d-488b-8c35-6242ffd3a549
ms.openlocfilehash: aa67d45dfc0fadd300caeaaeb8a7c25bb1c38bcb
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59023564"
---
# <a name="method-attributes"></a>方法屬性

下列屬性套用至類別、 coclass 或介面中的方法。

|屬性|描述|
|---------------|-----------------|
|[bindable](bindable.md)|表示支援資料繫結的屬性。|
|[call_as](call-as.md)|讓不可遠端處理函式對應至遠端函式。|
|[custom](custom-cpp.md)|可讓您定義您自己的屬性。|
|[db_column](db-column.md)|將指定的資料行的資料列集繫結。|
|[db_command](db-command.md)|建立 OLE DB 命令。|
|[db_param](db-param.md)|關聯的輸入或輸出參數中指定的成員變數，並分隔的變數。|
|[db_source](db-source.md)|建立資料來源的連接。|
|[db_table](db-table.md)|開啟 OLE DB 資料表。|
|[defaultbind](defaultbind.md)|表示最能代表物件的單一、 可繫結屬性。|
|[defaultcollelem](defaultcollelem.md)|使用 Visual Basic 程式碼最佳化。|
|[displaybind](displaybind.md)|指出應該顯示給使用者，作為可繫結的屬性。|
|[helpcontext](helpcontext.md)|指定的內容識別碼，可讓使用者檢視中此項目相關的資訊**協助**檔案。|
|[helpfile](helpfile.md)|設定的名稱**協助**型別程式庫的檔案。|
|[helpstring](helpstring.md)|指定用來描述所套用之項目的字元字串。|
|[helpstringcontext](helpstringcontext.md)|指定.hlp 或.chm 檔案中的說明主題的識別碼。|
|[helpstringdll](helpstringdll.md)|指定要用來執行文件字串查閱 （當地語系化） DLL 的名稱。|
|[hidden](hidden.md)|表示項目存在，但不是會顯示在使用者導向的瀏覽器中。|
|[id](id.md)|指定成員函式 （屬性或方法，在介面或 dispinterface） 的 DISPID。|
|[immediatebind](immediatebind.md)|表示資料庫將會立即被告知資料繫結物件的屬性的所有變更。|
|[in](in-cpp.md)|指出參數是要呼叫的程序從傳遞至呼叫的程序。|
|[local](local-cpp.md)|可讓您使用 MIDL 編譯器為標頭的產生器時用於介面標頭。 中的個別函式使用時，會指定任何虛設常式所產生的本機程序。|
|[nonbrowsable](nonbrowsable.md)|指出介面成員不會顯示在屬性瀏覽器。|
|[propget](propget.md)|指定屬性存取子函式。|
|[propput](propput.md)|指定的屬性設定函式。|
|[propputref](propputref.md)|指定使用參考而非值屬性設定函式。|
|[ptr](ptr.md)|指定指標做為完整的指標。|
|[range](range-cpp.md)|指定引數或在執行階段設定其值的欄位的允許值的範圍。|
|[requestedit](requestedit.md)|表示屬性支援 `OnRequestEdit` 通知。|
|[restricted](restricted.md)|指定的模組、 介面或 dispinterface 成員不能任意呼叫。|
|[satype](satype.md)|指定的資料型別`SAFEARRAY`結構。|
|[source](source-cpp.md)|指定控制項的連接點的來源介面的類別上。 在屬性或方法，`source`屬性會指出成員傳回的物件或變數，是事件來源。|
|[synchronize](synchronize.md)|同步處理至目標方法的存取。|
|[vararg](vararg.md)|指定的函式接受可變數目的引數。|

## <a name="see-also"></a>另請參閱

[依使用方式分類的屬性](attributes-by-usage.md)