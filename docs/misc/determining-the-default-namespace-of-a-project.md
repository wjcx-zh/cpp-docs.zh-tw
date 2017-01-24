---
title: "判斷專案的預設命名空間 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "自訂工具, 計算預設命名空間"
ms.assetid: 6d890676-7016-458c-8a6a-95cc0a068612
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# 判斷專案的預設命名空間
對於[!INCLUDE[vbprvb](../Token/vbprvb_md.md)]，如果`CustomToolNamespace`屬性設定將輸入檔的值`CustomToolNamespace`會變成預設的命名空間參數傳遞至值<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A>方法。  否則， `wszDefaultNamespace`參數傳遞至`Generate` \= 根命名空間。  如需有關命名空間的詳細資訊，請參閱[命名空間關鍵字](../Topic/Namespace%20Keywords%20\(C%23%20Reference\).md)。  
  
 [!INCLUDE[csprcs](../ide/includes/csprcs_md.md)]使用資料夾為基礎的命名空間。  也就是說，命名空間所組成的根命名空間，以及包含自訂工具的任何資料夾的名稱。  每個資料夾名稱會轉換成有效的識別項和句點來分隔所有的名稱。  比方說，如果輸入的檔案是 FolderA\\FolderB\\FolderC\\MyInput.txt，而根命名空間是 CL9，則計算的預設的命名空間會是**CL9.FolderA.FolderB.FolderC**。  
  
 當階層鏈結包含 Web 參考資料夾時，就會發生這項規則的例外狀況。  例如，當  
  
-   FolderC 是一個 Web 參考資料夾、 命名空間會是**CL9.FolderC**。  
  
-   FolderB 是一個 Web 參考資料夾、 命名空間會是**CL9.FolderB.FolderC**。  
  
 亦即，命名空間會使用下列格式：  
  
```  
rootNamespace.webReferenceFolder.containedFolder.containedFolder ...  
```  
  
## 請參閱  
 [實作單一檔案產生器](../Topic/Implementing%20Single-File%20Generators.md)   
 [註冊單一檔案產生器](../Topic/Registering%20Single%20File%20Generators.md)   
 [公開型別，以視覺化設計工具](../Topic/Exposing%20Types%20to%20Visual%20Designers.md)