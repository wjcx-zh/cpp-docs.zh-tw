---
title: COM 屬性
ms.date: 10/03/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- attributes [COM]
- COM, attributes
ms.assetid: 52a5dd70-e8be-4bba-afd6-daf90fe689a0
ms.openlocfilehash: 15225d23abb66b8aadd5f82b8429334356bdaa8d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168313"
---
# <a name="com-attributes"></a>COM 屬性

COM 屬性會插入程式碼，以支援 COM 開發的多個區域，並 .NET Framework common language runtime 開發。 這些領域的範圍包括自訂介面的執行，以及支援現有介面以支援內建屬性、方法和事件。 此外，也可以在複合和 ActiveX 控制項執行中找到支援。

|屬性|描述|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|表示控制項可以由另一個控制項匯總。|
|[aggregates](aggregates.md)|表示控制項會匯總目標類別。|
|[coclass](coclass.md)|建立可執行 COM 介面的 COM 物件。|
|[com_interface_entry](com-interface-entry-cpp.md)|將介面專案加入至 COM 對應。|
|[implements_category](implements-category.md)|指定類別的實作為元件類別。|
|[progid](progid.md)|定義控制項的 ProgID。|
|[rdx](rdx.md)|建立或修改登錄機碼。|
|[registration_script](registration-script.md)|執行指定的註冊腳本。|
|[requires_category](requires-category.md)|指定類別所需的元件類別。|
|[support_error_info](support-error-info.md)|支援目標物件的錯誤報表。|
|[synchronize](synchronize.md)|同步處理方法的存取。|
|[threading](threading-cpp.md)|指定 COM 物件的執行緒模型。|
|[vi_progid](vi-progid.md)|定義與版本無關的控制項 ProgID。|

## <a name="see-also"></a>另請參閱

[依群組分類的屬性](attributes-by-group.md)
