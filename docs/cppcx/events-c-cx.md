---
title: "事件 (C + + /CX) |Microsoft 文件"
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 31c8e08a-00ad-40f9-8f7e-124864aaad58
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ef32e8310454005fa01a3e23dcd8739dcdbaa647
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="events-ccx"></a>事件 (C++/CX)
Windows 執行階段類型可以宣告 （也就，發行） 事件，以及用戶端程式碼中的相同元件或其他元件可以訂閱這些事件產生關聯的方法呼叫*事件處理常式*與事件。 多個事件處理常式可以與單一事件相關聯。 當發行物件引發事件時，會導致所有事件處理常式被叫用。 如此一來，訂閱類別可以在發行者引發事件時，執行任何適當的自訂動作。 事件有委派類型，可指定所有事件處理常式必須具有的簽章，才能訂閱事件。  
  
## <a name="consuming-events-in-windows-components"></a>在 Windows 元件中使用事件  
 Windows 執行階段中的許多元件中公開事件。 例如，當感應器報告有新的光源值，LightSensor 物件就會引發 ReadingChanged 事件。 當您在程式中使用 LightSensor 物件時，可以定義要在 ReadingChanged 事件引發時呼叫的方法。 方法可以執行您所要的任何動作;唯一的需求是其簽章必須符合如需有關如何建立委派事件處理常式及訂閱事件，請參閱作為委派的簽章[委派](../cppcx/delegates-c-cx.md)。  
  
## <a name="creating-custom-events"></a>建立自訂事件  
  
### <a name="declaration"></a>宣告  
 您可以在 ref 類別或介面中宣告事件，事件可以有公用、內部 (公用/私用)、公用受保護的、受保護的、私用受保護的或私用存取範圍。 當您宣告事件時，編譯器會在內部建立可公開兩個存取子方法的物件：add 和 remove。 當訂閱物件註冊事件處理常式時，事件物件會將事件處理常式儲存在集合中。 當引發事件時，事件物件於是會叫用其清單中的所有處理常式。 Trivial 事件 (如下列範例所示) 具有隱含的備份存放區以及隱含的 `add` 和 `remove` 存取子方法。 如同在屬性上指定自訂 `get` 和 `set` 存取子，您也可以指定您自己的存取子。  實作的類別無法手動循環 trivial 事件中的事件訂閱者清單。  
  
 下列範例顯示如何宣告和引發事件。 請注意，事件有委派類型，並使用 "^" 符號來宣告。  
  
 [!code-cpp[cx_events#01](../cppcx/codesnippet/CPP/cx_events/class1.h#01)]  
  
### <a name="usage"></a>使用量  
 下列範例示範訂閱類別如何使用 `+=` 運算子訂閱事件，以及如何提供事件處理常式，以便在事件引發時叫用。 請注意，提供的函式符合在 `EventTest` 命名空間中發行者端定義之委派的簽章。  
  
 [!code-cpp[cx_events#02](../cppcx/codesnippet/CPP/eventsupportinvs/eventclientclass.h#02)]  
  
> [!WARNING]
>  一般來說，除非您十分小心避免循環參考，否則事件處理常式最好使用具名函式，而不是 Lambda。 具名函式會依弱式參考擷取 "this" 指標，而 Lambda 則是依強式參考來擷取，並且會建立循環參考。 如需詳細資訊，請參閱 [強式參考和中斷循環 (C++/CX)](../cppcx/weak-references-and-breaking-cycles-c-cx.md)。  
  
### <a name="custom-add-and-remove-methods"></a>自訂 add 和 remove 方法  
 就內部而言，事件具有加入方法、移除方法及引發方法。 當用戶端程式碼訂閱事件時，會呼叫加入方法，然後將傳遞的委派加入至事件的引動過程清單。 發行類別叫用事件之後，會呼叫引發方法，然後依序叫用清單中的每個委派。 訂閱者可以將其本身從委派清單中移除，這會呼叫事件的移除方法。 如果您在程式碼中未進行定義，編譯器會提供這些方法的預設版本，稱為 trivial 事件。 在許多情況下，只需要 trivial 事件。  
  
 如果您必須執行自訂邏輯以回應訂閱者的加入或移除，則可以指定事件的自訂 add、remove 和 raise 方法。 例如，假設您有一個只有事件報告需要用到的高度耗費資源物件，那麼您可以延遲此物件的建立，直到有用戶端實際訂閱此事件。  
  
 下一個範例說明如何將自訂 add、remove 和 raise 方法加入至事件：  
  
 [!code-cpp[cx_events#03](../cppcx/codesnippet/CPP/cx_events/class1.h#03)]  
  
## <a name="removing-an-event-handler-from-the-subscriber-side"></a>從訂閱者端移除事件處理常式  
 在某些較罕見的情況下，您可能要移除先前訂閱之事件的事件處理常式。 例如，您可能想以另一個事件處理常式取代舊的，或者您要刪除由它所持有的某些資源。 若要移除處理常式，您必須儲存由 `+=` 運算傳回的 EventRegistrationToken。 接著對這個語彙基元使用 `-=` 運算子，移除事件處理常式。  不過，就算移除之後，原始處理常式仍然可以被叫用。 因此，如果您想要移除事件處理常式，請先建立成員旗標，並在移除事件時設定它，然後在事件處理常式中檢查旗標，如果有設定就立即返回。 下一個範例顯示基本模式。  
  
 [!code-cpp[cx_events#04](../cppcx/codesnippet/CPP/eventsupportinvs/eventclientclass.h#04)]  
  
### <a name="remarks"></a>備註  
 多個處理常式可能與相同的事件相關聯。 事件來源會循序呼叫相同執行緒的所有事件處理常式。 如果事件處理常式方法中的事件接收器封鎖了，它會阻止事件來源叫用此事件的其他事件處理常式。  
  
 事件來源叫用事件接收器上之事件處理常式的順序並不一定，每個呼叫可能都不一樣。  
  
## <a name="see-also"></a>請參閱  
 [類型系統](../cppcx/type-system-c-cx.md)   
 [委派](../cppcx/delegates-c-cx.md)   
 [Visual c + + 語言參考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空間參考](../cppcx/namespaces-reference-c-cx.md)