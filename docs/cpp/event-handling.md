---
title: 事件處理
ms.date: 05/07/2019
helpviewer_keywords:
- event handling [C++]
ms.assetid: 82de3f9a-2d88-470c-9527-8a5b54c8ced4
ms.openlocfilehash: 4ed2dd2140176fe302d2b6800a3aa7768d17eedd
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91498897"
---
# <a name="event-handling"></a>事件處理

 (c + + 類別（通常會使用 ATL 類別或 [coclass](../windows/attributes/coclass.md) 屬性) ）來處理 com 類別，則主要支援事件處理。 如需詳細資訊，請參閱 [COM 中的事件處理](../cpp/event-handling-in-com.md)。

事件處理也支援原生 C++ 類別 (不實作 COM 物件的 C++ 類別)，不過該項支援已被取代，將在未來版本中移除。  如需詳細資訊，請參閱 [原生 c + + 中的事件處理](../cpp/event-handling-in-native-cpp.md)。

事件處理支援單一和多執行緒的使用方式，並在同時由多個執行緒存取時保護資料。 它也可讓您從事件來源或接收器類別衍生子類別，並在衍生類別中支援擴充的事件來源或接收。

Microsoft c + + 編譯器包含用來宣告事件和事件處理常式的屬性和關鍵字。 事件屬性和關鍵字可以在 CLR 程式與原生 C++ 程式中使用。

|主題|描述|
|-----------|-----------------|
|[event_source](../windows/attributes/event-source.md)|建立事件來源。|
|[event_receiver](../windows/attributes/event-receiver.md)|建立事件接收器 (接收)。|
|[__event](../cpp/event.md)|宣告事件。|
|[__raise](../cpp/raise.md)|強調事件的呼叫位置。|
|[__hook](../cpp/hook.md)|建立處理常式方法與事件的關聯。|
|[__unhook](../cpp/unhook.md)|解除處理常式方法與事件的關聯。|

## <a name="see-also"></a>另請參閱

[C + + 語言參考](../cpp/cpp-language-reference.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
