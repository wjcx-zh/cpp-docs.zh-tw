---
title: "編譯器錯誤 CS0313 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0313"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0313"
ms.assetid: a0b0f2fb-e742-4df8-98bd-3bc068f0c71c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0313
類型 'type1' 不能作為泛型類型或方法 'type2' 中的類型參數 'parameter name'。 可為 Null 的類型 'type1' 無法滿足 'type2' 的條件約束。 可為 Null 的類型無法滿足任何介面條件約束。  
  
 可為 Null 的類型不等於其不可為 Null 的對等項目。 在下列範例中，`ImplStruct` 滿足 `BaseInterface` 條件約束，但 `ImplStruct?` 不滿足，因為 `Nullable<ImplStruct>` 未實作 `BaseInterface`。  
  
### 更正這個錯誤  
  
1.  使用下面的程式碼作為範例，其中一種解決方案是指定一般 `ImplStruct` 作為 `TestMethod` 呼叫中的第一個類型引數。 然後，修改 `TestMethod`，以在其傳回陳述式中建立可為 Null 的 `Implstruct` 版本：  
  
    ```  
    return new Nullable<T>(t);  
    ```  
  
## 範例  
 下列程式碼會產生 CS0313：  
  
```  
// cs0313.cs public interface BaseInterface { } public struct ImplStruct : BaseInterface { } public class TestClass { public T? TestMethod<T, U>(T t) where T : struct, U { return t; } } public class NullableTest { public static void Run() { TestClass tc = new TestClass(); tc.TestMethod<ImplStruct?, BaseInterface>(new ImplStruct?()); // CS0313 } public static void Main() { } }  
```  
  
## 請參閱  
 [可為 Null 的類型](../Topic/Nullable%20Types%20\(C%23%20Programming%20Guide\).md)