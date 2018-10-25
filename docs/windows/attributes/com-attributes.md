---
title: COM 屬性 |Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- attributes [COM]
- COM, attributes
ms.assetid: 52a5dd70-e8be-4bba-afd6-daf90fe689a0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2aa88f88fe26b96202f2a917bddf5c8bb07c0d3c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071124"
---
# <a name="com-attributes"></a>COM 屬性

COM 屬性插入程式碼，以支援 COM 開發和.NET Framework 通用語言執行階段開發的多個區域。 這些區域範圍從自訂的介面實作和支援的現有介面來支援內建屬性、 方法和事件。 此外，可在支援複合和 ActiveX 控制項的實作。

|屬性|描述|
|---------------|-----------------|
|[aggregatable](aggregatable.md)|表示控制項，可以彙總的另一個控制項。|
|[aggregates](aggregates.md)|表示控制項彙總的目標類別。|
|[coclass](coclass.md)|建立 COM 物件，可實作 COM 介面。|
|[com_interface_entry](com-interface-entry-cpp.md)|將 COM 對應中的介面項目。|
|[implements_category](implements-category.md)|指定類別的實作的元件類別。|
|[progid](progid.md)|定義控制項 ProgID。|
|[rdx](rdx.md)|建立或修改登錄機碼。|
|[registration_script](registration-script.md)|執行指定的註冊指令碼。|
|[requires_category](requires-category.md)|指定所需的元件類別的類別。|
|[support_error_info](support-error-info.md)|支援目標物件的錯誤報告功能。|
|[synchronize](synchronize.md)|同步處理方法的存取。|
|[threading](threading-cpp.md)|指定 COM 物件的執行緒模型。|
|[vi_progid](vi-progid.md)|定義控制項與版本無關的 ProgID。|

## <a name="see-also"></a>另請參閱

[依群組分類的屬性](attributes-by-group.md)