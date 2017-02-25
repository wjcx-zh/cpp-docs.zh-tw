---
title: "Purpose of Attributes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "attributes [C++], about attributes"
ms.assetid: 3aff8bfa-a2a3-4fcb-a2c6-1d96a2b4c68d
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Purpose of Attributes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

屬性目前無法做到的方向擴充 C\+\+，而不會中斷該語言的傳統的結構。  屬性可讓提供者 \(個別的 Dll\) 來動態擴充語言功能。  屬性的主要目標是簡化 COM 元件，除了增加元件開發人員的產能層級的製作權限。  屬性可以套用到幾乎任何 C\+\+ 建構函式，例如類別、 資料成員或成員函式。  這項新技術所提供的益處的反白顯示如下：  
  
-   顯露常見及簡潔的呼叫慣例。  
  
-   使用插入的程式碼一樣，不像巨集可辨識的偵錯工具。  
  
-   允許簡單衍生自基底類別不包括繁瑣的實作詳細資料。  
  
-   取代大量的所需的幾個簡單的屬性與 COM 元件的 IDL 程式碼。  
  
 比方說，若要執行簡單的事件接收器為泛型的 ATL 類別，您無法套用 [event\_receiver](../windows/event-receiver.md) 如屬性設定為特定的類別`CMyReceiver`。  **Event\_receiver** 屬性由 Visual C\+\+ 編譯器，目的檔中插入適當的程式碼編譯。  
  
```  
[event_receiver(com)]  
class CMyReceiver   
{  
   void handler1(int i) { ... }  
   void handler2(int i, float j) { ... }  
}  
```  
  
 您接著可以設定 **CMyReceiver** 方法`handler1`和`handler2`來處理事件 \(使用內建的函式 [\_\_hook](../cpp/hook.md)\) 從事件來源，您可以建立使用 [event\_source](../windows/event-source.md)。  
  
## 請參閱  
 [Concepts](../windows/attributed-programming-concepts.md)