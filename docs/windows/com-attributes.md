---
title: COM 屬性 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], reference topics
- attributes [COM]
- COM, attributes
ms.assetid: 52a5dd70-e8be-4bba-afd6-daf90fe689a0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9d37ba5c690b61840ad261e6ab966d0cc74c07c1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="com-attributes"></a>COM 屬性
COM 屬性會插入程式碼以支援 COM 開發和.NET Framework 通用語言執行階段開發的多個區域。 這些區域範圍自訂介面實作和支援的現有的介面來支援內建屬性、 方法和事件。 此外，可以找到支援複合和 ActiveX 控制項的實作。  
  
|屬性|描述|  
|---------------|-----------------|  
|[aggregatable](../windows/aggregatable.md)|表示控制項，可以由另一個控制彙總。|  
|[aggregates](../windows/aggregates.md)|表示控制項彙總的目標類別。|  
|[coclass](../windows/coclass.md)|建立 COM 物件，可以實作 COM 介面。|  
|[com_interface_entry](../windows/com-interface-entry-cpp.md)|將介面項目加入至 COM 對應。|  
|[implements_category](../windows/implements-category.md)|指定此類別實作的元件類別。|  
|[progid](../windows/progid.md)|定義控制項 ProgID。|  
|[rdx](../windows/rdx.md)|建立或修改登錄機碼。|  
|[registration_script](../windows/registration-script.md)|執行指定的註冊指令碼。|  
|[requires_category](../windows/requires-category.md)|指定所需的元件類別目錄類別。|  
|[support_error_info](../windows/support-error-info.md)|支援的錯誤報告目標物件。|  
|[synchronize](../windows/synchronize.md)|同步處理方法的存取。|  
|[執行緒處理](../windows/threading-cpp.md)|指定 COM 物件的執行緒模型。|  
|[vi_progid](../windows/vi-progid.md)|定義控制項與版本無關的 ProgID。|  
  
## <a name="see-also"></a>另請參閱  
 [依群組分類的屬性](../windows/attributes-by-group.md)