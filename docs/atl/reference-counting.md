---
title: "Reference Counting | Microsoft Docs"
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
  - "AddRef method [C++]"
  - "AddRef method [C++], reference counting"
  - "reference counting"
  - "reference counts"
  - "參考, 計算"
ms.assetid: b1fd4514-6de6-429f-9e60-2777c0d07a3d
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Reference Counting
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

COM 不會自動嘗試從記憶體移除物件，將它視為時不再使用的物件。  相反地，物件程式設計人員必須移除未使用的物件。  這個程式設計人員判斷是否可以移除物件根據參考計數。  
  
 使用 COM **IUnknown** 方法， [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) 和 [版本](http://msdn.microsoft.com/library/windows/desktop/ms682317)，處理參考計數此物件的介面。  呼叫這些方法一般規則如下:  
  
-   每當用戶端接收介面指標，必須呼叫 `AddRef` 介面。  
  
-   使用介面指標，當用戶端完成，它必須呼叫 **版本**。  
  
 在簡單的實作，每個 `AddRef` 呼叫將和每 **版本** 稱為遞減物件中的計數器變數。  當計數為零，介面就再也沒有任何使用者也能從記憶體移除本身。  
  
 參考次數 \(Reference Count\) 上實作，以便為物件的每個參考 \(而非個別介面\) 計數。  在這種情況下，，其參考計數到達零時，每 `AddRef` 和 **版本** 呼叫委派集中實作的物件和 **版本** 釋放整個物件。  
  
> [!NOTE]
>  當 `CComObject`\-使用 **new** 運算子，衍生的建構物件時，參考計數為 0。  因此，必須在成功建立 `CComObject`之後對 `AddRef` 上一次呼叫衍生物件。  
  
## 請參閱  
 [COM 簡介](../atl/introduction-to-com.md)   
 [Managing Object Lifetimes through Reference Counting](http://msdn.microsoft.com/library/windows/desktop/ms687260)