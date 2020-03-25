---
title: 介面屬性（C++ COM）
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- interface attributes
ms.assetid: 27fcdfee-abce-4585-8b53-ee31635356e8
ms.openlocfilehash: 81a88ddfd74f20fa57ef615c988ba9786f41c1ad
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214821"
---
# <a name="interface-attributes"></a>介面屬性

下列屬性適用于[介面（或 __interface）](../../cpp/interface.md) C++關鍵字。

|屬性|描述|
|---------------|-----------------|
|[async_uuid](async-uuid.md)|指定 UUID，以指示 MIDL 編譯器定義 COM 介面的同步和非同步版本。|
|[custom](custom-cpp.md)|可讓您定義自己的屬性。|
|[dispinterface](dispinterface.md)|將介面放入 .idl 檔案中作為分派介面。|
|[dual](dual.md)|將介面放在 .idl 檔案中，做為雙重介面。|
|[export](export.md)|導致將資料結構放在 .idl 檔案中。|
|[helpcontext](helpcontext.md)|指定內容識別碼，讓使用者可在說明檔中查看此元素的相關資訊。|
|[helpfile](helpfile.md)|設定類型程式庫的說明檔名稱。|
|[helpstring](helpstring.md)|指定用來描述所套用之項目的字元字串。|
|[helpstringcontext](helpstringcontext.md)|在 .hlp 或 .chm 檔案中指定說明主題的識別碼。|
|[helpstringdll](helpstringdll.md)|指定要用來執行檔字串查閱（當地語系化）之 DLL 的名稱。|
|[hidden](hidden.md)|表示專案存在，但不應該顯示在使用者導向的瀏覽器中。|
|[library_block](library-block.md)|將結構放在 .idl 檔案的程式庫區塊內。|
|[local](local-cpp.md)|當用於介面標頭時，可讓您使用 MIDL 編譯器做為標頭產生器。 在個別函式中使用時，會指定不會產生任何存根的本機程式。|
|[nonextensible](nonextensible.md)|指定 `IDispatch` 的實作為僅包含介面描述中所列的屬性和方法，而且在執行時間不能與其他成員一起擴充。 這個屬性只有在[雙重](dual.md)介面上才有效。|
|[odl](odl.md)|將介面識別為物件描述語言（ODL）介面。|
|[object](object-cpp.md)|識別自訂介面。|
|[oleautomation](oleautomation.md)|指出介面與 Automation 相容。|
|[pointer_default](pointer-default.md)|除了出現在參數清單中的最上層指標以外，指定所有指標的預設指標屬性。|
|[ptr](ptr.md)|將指標指定為完整指標。|
|[restricted](restricted.md)|指定無法任意呼叫程式庫的成員。|
|[uuid](uuid-cpp-attributes.md)|提供程式庫的唯一識別碼|

您必須觀察下列定義介面的規則：

- 預設呼叫慣例為[__stdcall](../../cpp/stdcall.md)。

- 如果您未提供 GUID，則會提供給您。

- 不允許多載的方法。

當未指定[uuid](uuid-cpp-attributes.md)屬性並在不同的屬性專案中使用相同的介面名稱時，會產生相同的 GUID。

## <a name="see-also"></a>另請參閱

[依使用方式分類的屬性](attributes-by-usage.md)
