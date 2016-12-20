---
title: "MSBuild 錯誤 MSB3180 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateManifest.DuplicateComDefinition"
helpviewer_keywords: 
  - "MSB3180"
ms.assetid: 98d8cb76-6176-4121-82ee-8a297d9deebc
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 錯誤 MSB3180
**MSB3180: COM 元件 '\<assembly\>' 同時定義於 '\<file\>' 和 '\<file\>' 中，而 clsid\/tlbid\="'\<assembly\>'"。**  
  
 如果在檔案參考或相依資訊清單中找到重複的 COM 參考 \(類別或型別程式庫的參考\)，則在應用程式資訊清單產生過程中就會產生這個錯誤訊息。  
  
 例如，如果您以外部資訊清單加入對 COM 物件的參考，又以內部資訊清單加入對相同 COM 物件的參考，就有可能會收到這個錯誤。  
  
### 若要更正這個錯誤  
  
-   移除其中一個重複的 COM 參考。  
  
## 請參閱  
 [\<PackageFiles\> 項目](../Topic/%3CPackageFiles%3E%20Element%20\(Bootstrapper\).md)