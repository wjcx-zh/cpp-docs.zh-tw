---
title: "屬性 &#39;&lt;屬性名稱&gt;&#39; 不能在物件初始設定式運算式中初始化，因為它必須有引數 | Microsoft Docs"
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
  - "bc30992"
  - "vbc30992"
helpviewer_keywords: 
  - "BC30992"
ms.assetid: a4d050b2-7366-457a-a852-8eb490c97573
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 屬性 &#39;&lt;屬性名稱&gt;&#39; 不能在物件初始設定式運算式中初始化，因為它必須有引數
物件初始設定式清單中所初始化的成員必須是欄位或屬性，而且屬性成員不能有參數。 例如，預設屬性需要有引數，因此不能在物件初始設定式清單中進行初始化。 如需詳細資訊，請參閱[不在組建中：預設屬性](http://msdn.microsoft.com/zh-tw/a70f2a27-8176-4858-935e-f25afdd43ab5)。  
  
 **錯誤 ID︰**BC30992  
  
### 更正這個錯誤  
  
-   請從初始設定清單中移除具有引數的所有屬性。  
  
## 範例  
 下列類別包含需要整數引數的預設屬性 `defaultProp`。  
  
```  
Public Class SomeStrings Private myStrings() As String Sub New(ByVal size As Integer) ReDim myStrings(size) End Sub Default Property defaultProp(ByVal index As Integer) As String Get Return myStrings(index) End Get Set(ByVal Value As String) myStrings(index) = Value End Set End Property End Class  
```  
  
 因為預設屬性需要有引數，所以下列宣告會造成錯誤。  
  
```  
' Dim strs As New SomeStrings(2) With { .defaultProp = "One" }  
```  
  
## 請參閱  
 [不在組建中：預設屬性](http://msdn.microsoft.com/zh-tw/a70f2a27-8176-4858-935e-f25afdd43ab5)   
 [不在組建中：屬性和屬性程序](http://msdn.microsoft.com/zh-tw/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)