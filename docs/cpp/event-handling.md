---
title: "事件處理 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], event handling
- intrinsic functions [C++], event handling
- event handling [C++], Visual C++
ms.assetid: 82de3f9a-2d88-470c-9527-8a5b54c8ced4
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: a05886ade7ff9369dfae29accf7c47d1890998b8
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="event-handling"></a>事件處理
事件處理主要是支援 COM 類別 (c + + 類別可實作 COM 物件，通常會使用 ATL 類別或[coclass](../windows/coclass.md)屬性)。  如需詳細資訊，請參閱[COM 中的事件處理](../cpp/event-handling-in-com.md)。  
  
 事件處理也支援原生 C++ 類別 (不實作 COM 物件的 C++ 類別)，不過該項支援已被取代，將在未來版本中移除。  如需詳細資訊，請參閱[原生 c + + 中的事件處理](../cpp/event-handling-in-native-cpp.md)。  
  
 事件處理支援單一和多執行緒的使用方式，並在同時由多個執行緒存取時保護資料。 它也可讓您從事件來源或接收器類別衍生子類別，並在衍生類別中支援擴充的事件來源或接收。  
  
 Visual C++ 包含用於宣告事件和事件處理常式的屬性和關鍵字。 事件屬性和關鍵字可以在 CLR 程式與原生 C++ 程式中使用。  
  
|主題|說明|  
|-----------|-----------------|  
|[event_source](../windows/event-source.md)|建立事件來源。|  
|[event_receiver](../windows/event-receiver.md)|建立事件接收器 (接收)。|  
|[__event](../cpp/event.md)|宣告事件。|  
|[__raise](../cpp/raise.md)|強調事件的呼叫位置。|  
|[__hook](../cpp/hook.md)|建立處理常式方法與事件的關聯。|  
|[__unhook](../cpp/unhook.md)|解除處理常式方法與事件的關聯。|  
  
## <a name="see-also"></a>另請參閱  
 [C + + 語言參考](../cpp/cpp-language-reference.md)   
 [關鍵字](../cpp/keywords-cpp.md)   
 [事件處理範例](http://msdn.microsoft.com/en-us/cc0287d4-f92b-4da5-85fc-a0f186e16424)
