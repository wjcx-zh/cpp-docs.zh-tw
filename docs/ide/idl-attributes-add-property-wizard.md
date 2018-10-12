---
title: 新增屬性精靈、IDL 屬性 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.prop.idlattributes
dev_langs:
- C++
ms.assetid: 356ed666-79d0-4bd9-a5e7-cda679cbadbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ce3597f656d46da85faee3f6ec51b89257d25d05
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426350"
---
# <a name="idl-attributes-add-property-wizard"></a>加入屬性精靈、IDL 屬性

[新增屬性精靈] 的這個頁面可用來指定屬性的任何介面定義語言 (IDL) 設定。

- **id**

   設定識別屬性的數值識別碼。 此選項不適用於自訂介面的屬性。 請參閱＜MIDL 參考＞中的 [id](/windows/desktop/Midl/id)。

- **helpcontext**

   指定內容識別碼，讓使用者可在說明檔中檢視此屬性的相關資訊。 請參閱＜MIDL 參考＞中的 [helpcontext](/windows/desktop/Midl/helpcontext)。

- **helpstring**

   指定用來描述所套用之項目的字元字串。 根據預設，它會設定為 "property *Property name*"。 請參閱＜MIDL 參考＞中的 [helpstring](/windows/desktop/Midl/helpstring)。

## <a name="other-options"></a>其他選項

並非所有選項都適用於所有屬性類型。

|選項|描述|
|------------|-----------------|
|**bindable**|表示支援資料繫結的屬性。 請參閱＜MIDL 參考＞中的 [bindable](/windows/desktop/Midl/bindable)。 對於屬性的內建實作，預設會設定此選項，而且無法變更。|
|**defaultbind**|表示這個單一、可繫結屬性可最佳表示物件。 請參閱＜MIDL 參考＞中的 [defaultbind](/windows/desktop/Midl/defaultbind)。|
|**displaybind**|表示這個屬性應向使用者顯示為可繫結。 請參閱＜MIDL 參考＞中的 [displaybind](/windows/desktop/Midl/displaybind)。|
|**immediatebind**|表示該資料庫將立即被告知此資料繫結物件屬性的所有變更。 請參閱＜MIDL 參考＞中的 [immediatebind](/windows/desktop/Midl/immediatebind)。|
|**defaultcollelem**|表示屬性是預設集合項目的存取子函式。 請參閱＜MIDL 參考＞中的 [defaultcollelem](/windows/desktop/Midl/defaultcollelem)。|
|**nonbrowsable**|標記不應顯示在屬性瀏覽器中的介面或分配介面成員。 請參閱＜MIDL 參考＞中的 [nonbrowsable](/windows/desktop/Midl/nonbrowsable)。|
|**requestedit**|表示屬性支援 **OnRequestEdit** 通知。請參閱＜MIDL 參考＞中的 [requestedit](/windows/desktop/Midl/requestedit)。 對於屬性的內建實作，預設會設定此選項，而且無法變更。|
|**source**|表示屬性的成員是事件來源。 請參閱＜MIDL 參考＞中的 [source](/windows/desktop/Midl/source)。|
|**hidden**|表示屬性存在，但不應該在使用者導向的瀏覽器中顯示。 請參閱＜MIDL 參考＞中的 [hidden](/windows/desktop/Midl/hidden)。|
|**restricted**|指定無法任意呼叫屬性。 請參閱＜MIDL 參考＞中的 [restricted](/windows/desktop/Midl/restricted)。|
|`local`|向 MIDL 編譯器指定屬性不是遠端。 請參閱＜MIDL 參考＞中的 [local](/windows/desktop/Midl/local)。|

## <a name="see-also"></a>請參閱

[新增屬性](../ide/adding-a-property-visual-cpp.md)<br>
[新增屬性精靈、名稱](../ide/names-add-property-wizard.md)<br>
[實作介面](../ide/implementing-an-interface-visual-cpp.md)<br>
[內建屬性](../ide/stock-properties.md)