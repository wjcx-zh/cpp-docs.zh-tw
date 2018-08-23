---
title: 方法屬性 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- method attributes
- attributes [C++], reference topics
ms.assetid: b2313352-480d-488b-8c35-6242ffd3a549
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 67db478fbca64d56769ca9b57e7e72c41325925b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603562"
---
# <a name="method-attributes"></a>方法屬性

下列屬性套用至類別、 coclass 或介面中的方法。

|屬性|描述|
|---------------|-----------------|
|[bindable](../windows/bindable.md)|表示支援資料繫結的屬性。|
|[call_as](../windows/call-as.md)|讓不可遠端處理函式對應至遠端函式。|
|[custom](../windows/custom-cpp.md)|可讓您定義您自己的屬性。|
|[db_column](../windows/db-column.md)|將指定的資料行的資料列集繫結。|
|[db_command](../windows/db-command.md)|建立 OLE DB 命令。|
|[db_param](../windows/db-param.md)|關聯的輸入或輸出參數中指定的成員變數，並分隔的變數。|
|[db_source](../windows/db-source.md)|建立資料來源的連接。|
|[db_table](../windows/db-table.md)|開啟 OLE DB 資料表。|
|[defaultbind](../windows/defaultbind.md)|表示最能代表物件的單一、 可繫結屬性。|
|[defaultcollelem](../windows/defaultcollelem.md)|使用 Visual Basic 程式碼最佳化。|
|[displaybind](../windows/displaybind.md)|指出應該顯示給使用者，作為可繫結的屬性。|
|[helpcontext](../windows/helpcontext.md)|指定的內容識別碼，可讓使用者檢視中此項目相關的資訊**協助**檔案。|
|[helpfile](../windows/helpfile.md)|設定的名稱**協助**型別程式庫的檔案。|
|[helpstring](../windows/helpstring.md)|指定用來描述所套用之項目的字元字串。|
|[helpstringcontext](../windows/helpstringcontext.md)|指定.hlp 或.chm 檔案中的說明主題的識別碼。|
|[helpstringdll](../windows/helpstringdll.md)|指定要用來執行文件字串查閱 （當地語系化） DLL 的名稱。|
|[hidden](../windows/hidden.md)|表示項目存在，但不是會顯示在使用者導向的瀏覽器中。|
|[id](../windows/id.md)|指定成員函式 （屬性或方法，在介面或 dispinterface） 的 DISPID。|
|[immediatebind](../windows/immediatebind.md)|表示資料庫將會立即被告知資料繫結物件的屬性的所有變更。|
|[in](../windows/in-cpp.md)|指出參數是要呼叫的程序從傳遞至呼叫的程序。|
|[local](../windows/local-cpp.md)|可讓您使用 MIDL 編譯器為標頭的產生器時用於介面標頭。 中的個別函式使用時，會指定任何虛設常式所產生的本機程序。|
|[nonbrowsable](../windows/nonbrowsable.md)|指出介面成員不會顯示在屬性瀏覽器。|
|[propget](../windows/propget.md)|指定屬性存取子函式。|
|[propput](../windows/propput.md)|指定的屬性設定函式。|
|[propputref](../windows/propputref.md)|指定使用參考而非值屬性設定函式。|
|[ptr](../windows/ptr.md)|指定指標做為完整的指標。|
|[範圍](../windows/range-cpp.md)|指定引數或在執行階段設定其值的欄位的允許值的範圍。|
|[requestedit](../windows/requestedit.md)|表示屬性支援`OnRequestEdit`通知。|
|[restricted](../windows/restricted.md)|指定的模組、 介面或 dispinterface 成員不能任意呼叫。|
|[satype](../windows/satype.md)|指定的資料型別`SAFEARRAY`結構。|
|[source](../windows/source-cpp.md)|指定控制項的連接點的來源介面的類別上。 在屬性或方法，`source`屬性會指出成員傳回的物件或變數，是事件來源。|
|[synchronize](../windows/synchronize.md)|同步處理至目標方法的存取。|
|[vararg](../windows/vararg.md)|指定的函式接受可變數目的引數。|

## <a name="see-also"></a>另請參閱

[依使用方式分類的屬性](../windows/attributes-by-usage.md)