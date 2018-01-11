---
title: "介面屬性 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- attributes [C++], reference topics
- interface attributes
ms.assetid: 27fcdfee-abce-4585-8b53-ee31635356e8
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5ff84939b3211633e199066e1a38da2e91efb1c8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="interface-attributes"></a>介面屬性
下列屬性套用至[介面 （或 __interface）](../cpp/interface.md) c + + 關鍵字。  
  
|屬性|描述|  
|---------------|-----------------|  
|[async_uuid](../windows/async-uuid.md)|指定指示 MIDL 編譯器定義 COM 介面的同步和非同步版本的 UUID。|  
|[自訂](../windows/custom-cpp.md)|可讓您定義您自己的屬性。|  
|[dispinterface](../windows/dispinterface.md)|將介面放入 .idl 檔案中作為分派介面。|  
|[dual](../windows/dual.md)|雙重介面置於.idl 檔案介面。|  
|[export](../windows/export.md)|會導致資料結構，以便放入.idl 檔案。|  
|[helpcontext](../windows/helpcontext.md)|指定的內容識別碼，可讓使用者檢視的說明檔中此項目有關的資訊。|  
|[helpfile](../windows/helpfile.md)|設定型別程式庫的說明檔的名稱。|  
|[helpstring](../windows/helpstring.md)|指定的字元字串，用來描述它所套用的項目。|  
|[helpstringcontext](../windows/helpstringcontext.md)|指定.hlp 或.chm 檔案中的說明主題的識別碼。|  
|[helpstringdll](../windows/helpstringdll.md)|指定用來執行文件字串查閱 （當地語系化） 的 dll 名稱。|  
|[hidden](../windows/hidden.md)|表示項目存在，但不是會顯示在使用者導向的瀏覽器中。|  
|[library_block](../windows/library-block.md)|將.idl 檔案的程式庫區塊內的建構。|  
|[本機](../windows/local-cpp.md)|可讓您使用 MIDL 編譯器為標頭產生器時用於介面標頭。 個別的函式中使用時，會指定產生的任何虛設常式區域的程序。|  
|[nonextensible](../windows/nonextensible.md)|指定`IDispatch`實作只會包含屬性和方法的介面描述中所列，並且無法在執行階段擴充與其他成員。 這個屬性只適用於在[雙重](../windows/dual.md)介面。|  
|[odl](../windows/odl.md)|識別為物件描述語言 (ODL) 介面的介面。|  
|[object](../windows/object-cpp.md)|識別的自訂介面。|  
|[oleautomation](../windows/oleautomation.md)|表示與 Automation 相容介面。|  
|[pointer_default](../windows/pointer-default.md)|指定的預設指標屬性出現的最上層指標除外的所有指標的參數清單。|  
|[ptr](../windows/ptr.md)|將指標指定為完整的指標。|  
|[restricted](../windows/restricted.md)|指定無法任意呼叫的程式庫的哪些成員。|  
|[uuid](../windows/uuid-cpp-attributes.md)|提供程式庫的唯一識別碼|  
  
 您必須遵守下列規則來定義介面：  
  
-   預設呼叫慣例是[__stdcall](../cpp/stdcall.md)。  
  
-   如果沒有提供為您提供的 GUID。  
  
-   不允許任何多載的方法。  
  
 當未指定[uuid](../windows/uuid-cpp-attributes.md)屬性，並在不同的屬性專案中使用相同的介面名稱，會產生相同的 GUID。  
  
## <a name="see-also"></a>請參閱  
 [依使用方式分類的屬性](../windows/attributes-by-usage.md)