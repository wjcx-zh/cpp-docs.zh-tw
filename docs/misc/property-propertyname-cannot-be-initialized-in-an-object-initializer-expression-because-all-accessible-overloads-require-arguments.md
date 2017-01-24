---
title: "屬性 &#39;&lt;屬性名稱&gt;&#39; 不能在物件初始設定式運算式中初始化，因為所有可存取的多載必須有引數 | Microsoft Docs"
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
  - "bc30993"
  - "vbc30993"
helpviewer_keywords: 
  - "BC30993"
ms.assetid: d4476065-2ca2-4c9e-a571-c08917a6387f
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 屬性 &#39;&lt;屬性名稱&gt;&#39; 不能在物件初始設定式運算式中初始化，因為所有可存取的多載必須有引數
物件初始設定式清單中所初始化的成員必須是欄位或屬性。 此外，初始設定式清單中的屬性不能有參數。 造成多載這個錯誤的屬性，而且它的每個版本都需要引數。 因此，無法初始化物件初始設定式清單中的屬性。  
  
 **錯誤 ID︰**BC30993  
  
### 更正這個錯誤  
  
-   請從初始設定式清單中移除需要引數的屬性。  
  
## 範例  
 下列類別包含三種屬性定義：一個用於 `TotalItems`，兩個用於 `Item` \(已多載\)。  
  
```  
Class CollectionOfItems Property TotalItems() As Integer Get End Get Set(ByVal value As Integer) End Set End Property Property Item(ByVal Key As String) As Object Get End Get Set(ByVal value As Object) End Set End Property Property Item(ByVal Index As Integer) As Object Get End Get Set(ByVal value As Object) End Set End Property End Class  
```  
  
 `TotalItems` 屬性不需要引數，而且可以在物件初始設定清單中進行初始化 \(如下列宣告所示\)。  
  
```  
Dim coinCollection As New CollectionOfItems With { .TotalItems = 0 }  
```  
  
 `Item` 屬性已多載 ，而且每個多載都需要引數。 因此，`Item` 不能出現在物件初始設定式清單中。  
  
```  
' The following declaration is not valid. ' Dim coinCollection As New CollectionOfItems With { .TotalItems = 0, _ '    .Item = aCoinObject }  
```  
  
 若要避免這個錯誤，請在物件初始設定式外部初始化 `Item` 屬性。  
  
```  
Dim coinCollection As New CollectionOfItems With { .TotalItems = 0 } coinCollection.Item(1) = aCoinObject  
```  
  
## 請參閱  
 [不在組建中：屬性和屬性程序](http://msdn.microsoft.com/zh-tw/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [How to: Call a Property Procedure](../Topic/How%20to:%20Call%20a%20Property%20Procedure%20\(Visual%20Basic\).md)   
 [不在組建中：預設屬性](http://msdn.microsoft.com/zh-tw/a70f2a27-8176-4858-935e-f25afdd43ab5)   
 [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md)   
 [Procedure Overloading](../Topic/Procedure%20Overloading%20\(Visual%20Basic\).md)