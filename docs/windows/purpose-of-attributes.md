---
title: 屬性用途 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], about attributes
ms.assetid: 3aff8bfa-a2a3-4fcb-a2c6-1d96a2b4c68d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4f44d6e4db7e09033e9c3f05d94cbf5294b306a3
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018278"
---
# <a name="purpose-of-attributes"></a>屬性用途
屬性指示目前無法在延伸 c + +，而不會中斷語言的傳統結構。 屬性可讓提供者 (另一個 Dll) 來動態擴充的語言功能。 屬性的主要目標是簡化 COM 元件，以及增加元件開發人員的產能層級的撰寫。 屬性可以套用至幾乎任何 c + + 建構，例如類別、 資料成員或成員函式。 以下是提供這項新技術的優勢的反白顯示：  
  
-   會公開熟悉且簡單的呼叫慣例。  
  
-   使用插入程式碼，這不同於巨集，辨識偵錯工具。  
  
-   可讓您輕鬆衍生自基底類別，而不麻煩的實作詳細資料。  
  
-   取代了大量的所需的幾個簡要的屬性與 COM 元件的 IDL 程式碼。  
  
 例如，若要實作一般的 ATL 類別的簡單事件接收器，您可以套用[event_receiver](../windows/event-receiver.md)屬性，是特定的類別例如`CMyReceiver`。 `event_receiver`屬性就會編譯 Visual c + + compiler 物件檔案中插入適當的程式碼。  
  
```cpp  
[event_receiver(com)]  
class CMyReceiver   
{  
   void handler1(int i) { ... }  
   void handler2(int i, float j) { ... }  
}  
```  
  
 您接著可以設定`CMyReceiver`方法`handler1`並`handler2`來處理事件 (使用內建函式[__hook](../cpp/hook.md)) 從事件來源，您可以建立使用[event_source](../windows/event-source.md).  
  
## <a name="see-also"></a>另請參閱  
 [概念](../windows/attributed-programming-concepts.md)