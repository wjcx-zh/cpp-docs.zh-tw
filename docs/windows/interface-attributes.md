---
title: "Interface Attributes | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "attributes [C++], reference topics"
  - "interface attributes"
ms.assetid: 27fcdfee-abce-4585-8b53-ee31635356e8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Interface Attributes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列屬性套用於[介面 \(或 \_\_interface\)](../cpp/interface.md) C\+\+ 關鍵字。  
  
|屬性|描述|  
|--------|--------|  
|[async\_uuid](../windows/async-uuid.md)|指定指示 MIDL 編譯器，將定義 COM 介面的同步和非同步版本的 UUID。|  
|[custom](../windows/custom-cpp.md)|讓您定義您自己的屬性。|  
|[dispinterface](../windows/dispinterface.md)|表示該工期為介面的分派介面為.idl 檔內的位置。|  
|[dual](../windows/dual.md)|將.idl 檔內的介面以雙重介面。|  
|[export](../windows/export.md)|會造成.idl 檔內放置的資料結構。|  
|[helpcontext](../windows/helpcontext.md)|指定的主題代碼，可讓使用者檢視此說明檔中的項目相關的資訊。|  
|[說明檔案](../windows/helpfile.md)|設定型別程式庫的 \[說明\] 檔案名稱。|  
|[helpstring](../windows/helpstring.md)|指定用來描述所套用之項目的字元字串，|  
|[helpstringcontext](../windows/helpstringcontext.md)|指定.hlp 或.chm 檔中的 \[說明\] 主題的識別碼。|  
|[helpstringdll](../windows/helpstringdll.md)|指定要用來執行文件字串查閱 \(當地語系化\) 之 DLL 的名稱。|  
|[hidden](../windows/hidden.md)|表示該項目存在，但不是會顯示在使用者導向的瀏覽器中。|  
|[library\_block](../windows/library-block.md)|將.idl 檔案的媒體櫃區塊內的建構函式。|  
|[local](../windows/local-cpp.md)|可讓您使用 MIDL 編譯器，做一個標頭的產生器介面的標頭中使用時。  個別函式中使用時，會指定產生的任何虛設常式區域的程序。|  
|[nonextensible](../windows/nonextensible.md)|指定的`IDispatch`實作包括僅屬性以及方法介面描述中所列，並不能與其他成員在執行階段擴充。  這個屬性才有效，在[雙](../windows/dual.md)介面。|  
|[odl](../windows/odl.md)|識別為物件描述語言 \(ODL\) 介面的介面。|  
|[object](../windows/object-cpp.md)|識別自訂介面。|  
|[oleautomation](../windows/oleautomation.md)|指示介面適用於自動化。|  
|[pointer\_default](../windows/pointer-default.md)|指定的預設指標屬性，除了顯示的最上層指標的所有指標參數清單中。|  
|[ptr](../windows/ptr.md)|指定變數的指標做為完整的指標。|  
|[restricted](../windows/restricted.md)|將指定的文件庫的哪些成員不能被隨意呼叫。|  
|[uuid](../windows/uuid-cpp-attributes.md)|提供程式庫的專一識別碼|  
  
 您必須遵守這些規則來定義介面：  
  
-   呼叫慣例的預設值是 [\_\_stdcall](../cpp/stdcall.md)。  
  
-   如果沒有提供，會為您提供 GUID。  
  
-   允許沒有多載的方法。  
  
 未指定時 [uuid](../windows/uuid-cpp-attributes.md) 屬性，並使用相同的介面名稱，在專案中不同的屬性，就會產生相同的 GUID。  
  
## 請參閱  
 [Attributes by Usage](../windows/attributes-by-usage.md)