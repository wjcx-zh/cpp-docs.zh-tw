---
title: "擴充方法 &#39;&lt;方法名稱&gt;&#39; 有一直無法滿足的類型條件約束 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36561"
  - "vbc36561"
helpviewer_keywords: 
  - "BC36561"
ms.assetid: ff42d6e9-611b-407d-a269-f268b36ed277
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 擴充方法 &#39;&lt;方法名稱&gt;&#39; 有一直無法滿足的類型條件約束
這個方法之類型參數的互動方式，使得這些參數無法一直滿足。 下列擴充方法即為一例。  
  
```  
'' Not valid. '<Extension()> _ 'Sub extensionExample(Of T As U, U)(ByVal para1 As T, ByVal para2 As U) 'End Sub  
```  
  
 由於此方法是擴充方法，因此編譯器必須能夠只根據方法宣告中的第一個參數 `para1` 及針對該參數所傳入的引數，來決定方法所擴充的一或多個資料類型。 當第一個參數參考到泛型類型參數 `para1 as T` 時，泛型參數的條件約束會將類型集合限制為方法所套用的類型集合。  
  
 擴充方法的適用性取決於提供給第一個參數的引數，也就是下列程式碼中的 `arg1`。  
  
 `'' Not valid.`  
  
 `'arg1.extensionExample(arg2)`  
  
 您必須能夠藉由只查看第一個引數  `arg1`，來確認第一個參數 `para1` 所參考之所有泛用類型參數的條件約束。 在 `extensionExample` 中，無法單獨透過第一個參數來決定所要擴充的類型集合。 類型參數 `T` 受到類型參數 `U` 的條件約束，但後者不是由 `para1` 所參考，而且無法從 `arg1` 推斷。 因此，無法驗證任何可能類型之方法的適用性，而且永遠不會呼叫此方法。  
  
 **錯誤 ID︰**BC36561  
  
### 更正這個錯誤  
  
-   變更類型宣告，以移除類型之間的相依關係。  
  
## 請參閱  
 [擴充方法](../Topic/Extension%20Methods%20\(Visual%20Basic\).md)   
 [Visual Basic 中的泛型類型](../Topic/Generic%20Types%20in%20Visual%20Basic%20\(Visual%20Basic\).md)