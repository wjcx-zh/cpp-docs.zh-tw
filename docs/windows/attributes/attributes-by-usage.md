---
title: 依使用方式分類的屬性
ms.custom: index-page
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributes [C++/CLI]
ms.assetid: 8be2de10-b1ff-4ca4-a114-75318408593c
ms.openlocfilehash: dcbed019f8cd08ddbf4ab6b4756a59f7fcbabc4b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361328"
---
# <a name="attributes-by-usage"></a>依使用方式分類的屬性

本主題根據屬性應用C++語言元素列出屬性。

如果屬性位於不在屬性作用域中的元素前面,則屬性塊將被視為註釋。

|屬性|描述|
|---------------|-----------------|
|[模組屬性](module-attributes.md)|應用於[模組](module-cpp.md)屬性。|
|[介面屬性](interface-attributes.md)|適用於[__interfaceC++](../../cpp/interface.md)關鍵字。|
|[類別屬性](class-attributes.md)|應用於C++關鍵字。|
|[方法屬性](method-attributes.md)|應用於類、類或介面中的方法。|
|[參數屬性](parameter-attributes.md)|應用於類或介面中方法的參數。|
|[資料成員屬性](data-member-attributes.md)|應用於類、coclass 或介面中的數據成員。|
|[類型定義、枚舉、聯合和結構屬性](typedef-enum-union-and-struct-attributes.md)|適用於C++關鍵字。|
|[陣列屬性](array-attributes.md)|適用於陣列或`SAFEARRAY`s。|
|[獨立屬性](stand-alone-attributes.md)|操作方式更像一行代碼,但不對C++關鍵字進行操作。 獨立屬性語句需要在行尾使用分號。|
|[自訂屬性](custom-attributes-cpp.md)|允許用戶擴展元數據。|

## <a name="module-attributes"></a>模組屬性

以下屬性只能應用於[模塊](module-cpp.md)屬性。

|屬性|描述|
|---------------|-----------------|
|[helpstringdll](helpstringdll.md)|指定用於執行文件字串尋找(本地化)的 DLL 的名稱。|

## <a name="interface-attributes"></a>介面屬性

以下屬性適用於C++關鍵字的[介面(或__interface)。](../../cpp/interface.md)

|屬性|描述|
|---------------|-----------------|
|[async_uuid](async-uuid.md)|指定指示 MIDL 編譯器定義 COM 介面的同步和異步版本的 UUID。|
|[自訂](custom-cpp.md)|允許您定義自己的屬性。|
|[dispinterface](dispinterface.md)|將介面放入 .idl 檔案中作為分派介面。|
|[雙](dual.md)|將介面作為雙介面放在 .idl 檔中。|
|[出口](export.md)|導致資料結構放置在 .idl 檔中。|
|[helpcontext](helpcontext.md)|指定一個上下文 ID,允許使用者在幫助檔案中查看有關此元素的資訊。|
|[說明檔案](helpfile.md)|設定類型庫的幫助檔的名稱。|
|[helpstring](helpstring.md)|指定用來描述所套用之項目的字元字串。|
|[helpstringcontext](helpstringcontext.md)|指定 .hlp 或 .chm 檔中説明主題的 ID。|
|[helpstringdll](helpstringdll.md)|指定用於執行文件字串尋找(本地化)的 DLL 的名稱。|
|[隱藏](hidden.md)|指示該專案存在,但不應在面向用戶的瀏覽器中顯示。|
|[library_block](library-block.md)|將建構放在 .idl 檔案的庫塊中。|
|[local](local-cpp.md)|允許您在介面標頭中使用 MIDL 編譯器作為標頭生成器。 在單個函數中使用時,指定不為其生成存根的本地過程。|
|[nonextensible](nonextensible.md)|指定`IDispatch`實現僅包括介面描述中列出的屬性和方法,並且在運行時不能使用其他成員進行擴展。 此屬性僅在[雙](dual.md)介面上有效。|
|[奧德爾](odl.md)|將介面識別為物件描述語言 (ODL) 介面。|
|[物件](object-cpp.md)|標識自定義介面。|
|[oleautomation](oleautomation.md)|指示介面與自動化相容。|
|[pointer_default](pointer-default.md)|指定除參數清單中顯示的頂級指標之外的所有指標的預設指標屬性。|
|[Ptr](ptr.md)|將指標指定為完整指標。|
|[限制](restricted.md)|指定不能任意調用庫的成員。|
|[uuid](uuid-cpp-attributes.md)|提供函式庫的唯一 ID|

定義介面時必須遵守以下規則:

- 預設呼叫約定[__stdcall](../../cpp/stdcall.md)。

- 如果您不提供 GUID,則為您提供 GUID。

- 不允許使用重載方法。

如果不指定[uuid](uuid-cpp-attributes.md)屬性並在不同的屬性專案中使用相同的介面名稱時,將生成相同的 GUID。

## <a name="see-also"></a>另請參閱

[適用於 COM 和 .NET 的 C++ 屬性](cpp-attributes-com-net.md)<br/>
[依群組屬性](attributes-by-group.md)<br/>
[屬性字母引用](attributes-alphabetical-reference.md)
