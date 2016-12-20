---
title: "編譯器錯誤 CS0281 | Microsoft Docs"
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
  - "CS0281"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0281"
ms.assetid: 3b886510-6e4d-45bc-b885-3ab7f6b6b2c6
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0281
Friend 存取權限是授與 'AssemblyName1'，但是輸出組件名為 'AssemblyName2'。 請嘗試將參考加入 'AssemblyName1' 中，或變更輸出組件名稱使其相符。  
  
 Friend 存取權限是新的 Common Language Runtime \(CLR\) 功能，可讓組件查看另一個組件的非公用類型。 授與 Friend 存取權限的組件指定錯誤的被授與者組件名稱時，會發生這個錯誤。 如需詳細資訊，請參閱[Friend 組件](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)。  
  
## 範例  
 下列一系列的程式碼範例會產生 CS0281。  
  
 用來建立強式名稱組件的檔案產生如下：  
  
-   sn \-d CS0281.snk  
  
-   sn \-k CS0281.snk  
  
-   sn \-i CS0281.snk CS0281.snk  
  
-   sn \-pc CS0281.snk key.publickey  
  
-   sn \-tp key.publickey  
  
```  
// CS0281.cs // compile with: /target:library /keyfile:CS0281.snk public class A {}  
```  
  
## 範例  
  
```  
// CS0281_b.cs // compile with: /target:library /keyfile:CS0281.snk /reference:CS0281.dll [assembly:System.Runtime.CompilerServices.InternalsVisibleTo("CS0281 , PublicKey=00240000048000009400000006020000002400005253413100040000010001004b2d4d56af7c50be2fcbbf97cb880b9e73ad84467a587191fef63aadc118a96cecf9d508cd679c907b6e20f71684300bdc2c0a851019af0c96b29bf8f1339753276041aefd67db46139e6348b3a12f29537b4dc6c2c19829df2c9ed6803f3c63c3b84cfa2728849386aea575c543a5f70fa85793d2946f15f7fe1ccb0c5e8fe0")] class B : A {}  
```  
  
## 範例  
 下列範例會產生 CS0281。  
  
 請注意，這個範例所建立的輸出檔會與第一個範例中的輸出檔同名。 若要解決，請不要變更元件的組件屬性，並加入類別 C。  
  
```  
// CS0281_c.cs // compile with: /target:library /out:CS0281.dll /keyfile:CS0281.snk /reference:CS0281_b.dll // CS0281 expected [assembly:System.Reflection.AssemblyVersion("3")] [assembly:System.Reflection.AssemblyCulture("en-us")] class C : B {} public class A {}  
```