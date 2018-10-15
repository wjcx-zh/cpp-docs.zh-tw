---
title: 屬性的用法 |Microsoft Docs
ms.custom: index-page
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI]
ms.assetid: 8be2de10-b1ff-4ca4-a114-75318408593c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 49e298af793655bb3ea3854909a16dd4db03c6a3
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2018
ms.locfileid: "49328177"
---
# <a name="attributes-by-usage"></a>依使用方式分類的屬性

本主題列出根據它們所套用的 c + + 語言項目屬性。

如果屬性在前面的項目不是屬性的範圍中，屬性區塊會被視為註解中。

|屬性|描述|
|---------------|-----------------|
|[模組屬性](module-attributes.md)|適用於[模組](module-cpp.md)屬性。|
|[介面屬性](interface-attributes.md)|適用於[__interface](../../cpp/interface.md) c + + 關鍵字。|
|[類別屬性](class-attributes.md)|適用於 c + + 關鍵字。|
|[方法屬性](method-attributes.md)|套用至類別、 coclass 或介面中方法。|
|[參數屬性](parameter-attributes.md)|適用於類別或介面中方法的參數。|
|[資料成員屬性](data-member-attributes.md)|套用至類別、 coclass 或介面中的資料成員。|
|[Typedef、Enum、Union 和 Struct 屬性](typedef-enum-union-and-struct-attributes.md)|適用於 c + + 關鍵字。|
|[陣列屬性](array-attributes.md)|套用至陣列或`SAFEARRAY`s。|
|[獨立屬性](stand-alone-attributes.md)|操作起來更像是程式碼行，但不是能進行 c + + 關鍵字。 獨立屬性陳述式需要行尾的分號。|
|[自訂屬性](custom-attributes-cpp.md)|可讓使用者擴充中繼資料。|

## <a name="module-attributes"></a>模組屬性
下列屬性只能套用至[模組](module-cpp.md)屬性。
  
|屬性|描述|
|---------------|-----------------|
|[helpstringdll](helpstringdll.md)|指定要用來執行文件字串查閱 （當地語系化） DLL 的名稱。|

## <a name="interface-attributes"></a>介面屬性

下列屬性套用至[介面 （或 __interface）](../../cpp/interface.md) c + + 關鍵字。

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

[適用於 COM 與 .NET 的 C++ 屬性](cpp-attributes-com-net.md)<br/>
[依群組分類的屬性](attributes-by-group.md)<br/>
[依字母順序排列的屬性參考](attributes-alphabetical-reference.md)