---
title: "屬性用途 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], about attributes
ms.assetid: 3aff8bfa-a2a3-4fcb-a2c6-1d96a2b4c68d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ed20c29d017527d5c2ce0b0c5ab8053fc75dc6ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="purpose-of-attributes"></a>屬性用途
屬性會指示目前無法在 c + + 擴充而不需要傳統的語言結構。 屬性可讓提供者 (個別 Dll)，以動態方式擴充語言功能。 屬性的主要目標是簡化 COM 元件，除了增加元件開發人員的產能等級的撰寫。 屬性可以套用到幾乎可在任何 c + + 建構，例如類別、 資料成員或成員函式。 以下是提供這項新技術的優勢的反白顯示：  
  
-   公開親切又簡單的呼叫慣例。  
  
-   使用插入程式碼，其與不同的巨集，是可辨識偵錯工具。  
  
-   可讓您輕鬆沒有相當惱人實作詳細資料的基底類別衍生。  
  
-   取代了大量的所需的幾個簡單的屬性與 COM 元件的 IDL 程式碼。  
  
 例如，若要實作泛型的 ATL 類別的簡單事件接收，您可以套用[event_receiver](../windows/event-receiver.md)屬性特定的類別例如`CMyReceiver`。 **Event_receiver**屬性然後編譯的 Visual c + + 編譯器中，將適當的程式碼插入至目的檔。  
  
```  
[event_receiver(com)]  
class CMyReceiver   
{  
   void handler1(int i) { ... }  
   void handler2(int i, float j) { ... }  
}  
```  
  
 您可以再設定**CMyReceiver**方法`handler1`和`handler2`來處理事件 (使用內建函式[__hook](../cpp/hook.md)) 從事件來源，您可以建立使用[event_source](../windows/event-source.md)。  
  
## <a name="see-also"></a>請參閱  
 [概念](../windows/attributed-programming-concepts.md)