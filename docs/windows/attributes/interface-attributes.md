---
title: 介面屬性 (C++ COM)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- interface attributes
ms.assetid: 27fcdfee-abce-4585-8b53-ee31635356e8
ms.openlocfilehash: 8218ccb66c6be9edef5d7de751a73bf4753d069f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59027201"
---
# <a name="interface-attributes"></a>介面屬性

下列屬性套用至[介面 （或 __interface）](../../cpp/interface.md) C++關鍵字。

|屬性|描述|
|---------------|-----------------|
|[async_uuid](async-uuid.md)|指定會指示 MIDL 編譯器定義 COM 介面的同步和非同步版本的 UUID。|
|[custom](custom-cpp.md)|可讓您定義您自己的屬性。|
|[dispinterface](dispinterface.md)|將介面放入 .idl 檔案中作為分派介面。|
|[dual](dual.md)|將介面放在.idl 檔案中，為雙重介面。|
|[export](export.md)|會導致資料結構，以放入.idl 檔案。|
|[helpcontext](helpcontext.md)|指定的內容識別碼，可讓使用者檢視說明檔中這個項目相關的資訊。|
|[helpfile](helpfile.md)|設定型別程式庫的說明檔的名稱。|
|[helpstring](helpstring.md)|指定用來描述所套用之項目的字元字串。|
|[helpstringcontext](helpstringcontext.md)|指定.hlp 或.chm 檔案中的說明主題的識別碼。|
|[helpstringdll](helpstringdll.md)|指定要用來執行文件字串查閱 （當地語系化） DLL 的名稱。|
|[hidden](hidden.md)|表示項目存在，但不是會顯示在使用者導向的瀏覽器中。|
|[library_block](library-block.md)|會建構的.idl 檔案的程式庫區塊內。|
|[local](local-cpp.md)|可讓您使用 MIDL 編譯器為標頭的產生器時用於介面標頭。 中的個別函式使用時，會指定任何虛設常式所產生的本機程序。|
|[nonextensible](nonextensible.md)|指定`IDispatch`實作只包括屬性和方法介面描述中所列，而且無法在執行階段延伸與其他成員。 這個屬性只適[雙重](dual.md)介面。|
|[odl](odl.md)|識別物件描述語言 (ODL) 介面的介面。|
|[object](object-cpp.md)|識別自訂的介面。|
|[oleautomation](oleautomation.md)|表示與 Automation 相容介面。|
|[pointer_default](pointer-default.md)|指定的預設指標屬性的最上層出現的指標除外的所有指標的參數清單。|
|[ptr](ptr.md)|指定指標做為完整的指標。|
|[restricted](restricted.md)|指定無法被任意呼叫程式庫的哪些成員。|
|[uuid](uuid-cpp-attributes.md)|程式庫提供的唯一識別碼|

您必須遵守這些規則來定義介面：

- 預設呼叫慣例是[__stdcall](../../cpp/stdcall.md)。

- 若您未提供其中一個，則會為您提供 GUID。

- 不允許任何多載的方法。

當未指定[uuid](uuid-cpp-attributes.md)屬性，並在不同的屬性專案中使用相同的介面名稱，會產生相同的 GUID。

## <a name="see-also"></a>另請參閱

[依使用方式分類的屬性](attributes-by-usage.md)