---
title: "&#39;Optional&#39; 不能套用至擴充方法的第一個參數 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36553"
  - "vbc36553"
helpviewer_keywords: 
  - "BC36553"
ms.assetid: 8ea0b90c-f155-47a9-988b-5b8009b510af
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Optional&#39; 不能套用至擴充方法的第一個參數
'Optional' 不能套用至擴充方法的第一個參數。 第一個參數會指定要擴充的類型。  
  
 擴充方法的第一個參數會指定方法可擴充的資料類型。 執行方法時，第一個參數會繫結至叫用方法的資料類型執行個體。 因此，第一個參數是必要項目，不得為選用項目。  
  
 只有第一個參數有此限制。 其他參數可以是選擇性或必要，取決於任何其他方法中的相同規則。 如需詳細資訊，請參閱[Parameter List](../Topic/Parameter%20List%20\(Visual%20Basic\).md)。  
  
 **錯誤 ID︰**BC36553  
  
### 更正這個錯誤  
  
-   如果您想要讓目前的第一個參數指定要擴充的資料類型，請移除 `Optional` 關鍵字。  
  
-   如果目前的第一個參數是方法的標準參數，而且您不想要讓它來表示要擴充的資料類型，請新增第一個參數。  
  
## 範例  
 下列範例中的第一個參數是指定 `Print` 方法可擴充 `String` 資料類型的唯一指示， 因此不可為選擇性參數。  
  
```  
<Extension()> Public Sub Print (ByVal str As String) Console.WriteLine(str) End Sub  
```  
  
 如下所示呼叫擴充方法時，`str` 方法中的參數會繫結至 `greeting`，也就是呼叫 `Print` 的 `String` 執行個體。 編譯器會使用 `greeting` 作為擴充方法 `Print` 的引數。  
  
```  
Dim greeting As String = "Hello" greeting.Print()  
```  
  
## 請參閱  
 [擴充方法](../Topic/Extension%20Methods%20\(Visual%20Basic\).md)   
 [如何：為程序定義選擇性參數 \(Visual Basic\)](http://msdn.microsoft.com/zh-tw/0b32b312-0da0-489b-96ad-7dcb1f1f8f88)   
 [Optional Parameters](../Topic/Optional%20Parameters%20\(Visual%20Basic\).md)