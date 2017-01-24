---
title: "編譯器警告 (層級 2) CS1698 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1698"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1698"
ms.assetid: 65cac5d0-e045-40f9-911c-1bf50e710b18
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 2) CS1698
循環組件參考 'AssemblyName1' 與輸出組件名稱 'AssemblyName2' 不相符。 請嘗試將參考加入 'AssemblyName1' 中，或變更輸出組件名稱使其相符。  
  
 組件參考不正確時，就會發生 CS1698。 如果參考的組件受到重新編譯，也會發生此錯誤。 若要解決此問題，如果某個組件是您所參考之組件的相依項目，請勿將其取代。  
  
## 範例  
  
```  
// CS1698_a.cs // compile with: /target:library /keyfile:mykey.snk [assembly:System.Reflection.AssemblyVersion("2")] public class CS1698_a {}  
```  
  
## 範例  
  
```  
// CS1698_b.cs // compile with: /target:library /reference:CS1698_a.dll /keyfile:mykey.snk public class CS1698_b : CS1698_a {}  
```  
  
## 範例  
 下列範例會產生 CS1698：  
  
```  
// CS1698_c.cs // compile with: /target:library /out:cs1698_a.dll /reference:cs1698_b.dll /keyfile:mykey.snk // CS1698 expected [assembly:System.Reflection.AssemblyVersion("3")] public class CS1698_c : CS1698_b {} public class CS1698_a {}  
  
```