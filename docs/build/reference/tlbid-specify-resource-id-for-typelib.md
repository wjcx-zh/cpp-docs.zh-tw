---
title: "/TLBID (指定 TypeLib 的資源 ID) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/tlbid"
  - "VC.Project.VCLinkerTool.TypeLibraryResourceID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".tlb 檔案, 指定資源 ID"
  - "/TLBID 連結器選項"
  - "tlb 檔案, 指定資源 ID"
  - "TLBID 連結器選項"
  - "-TLBID 連結器選項"
  - "類型程式庫, 指定資源 ID"
ms.assetid: 434b28a2-4656-4d52-ac82-8b18bf486fb2
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /TLBID (指定 TypeLib 的資源 ID)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/TLBID:id  
```  
  
## 備註  
 其中：  
  
 `id`  
 是使用者對連結器建立的型別程式庫指定的值。  它會覆寫值為 1 的預設資源 ID。  
  
## 備註  
 在編譯一個使用多項屬性的程式時，連結器將會建立型別程式庫。  連結器會指派值為 1 的資源 ID 給這個型別程式庫。  
  
 如果這個資源 ID 與您現有的資源衝突，您可以使用 \/TLBID 指定另一個 ID。  您可以傳遞給 `id` 的值範圍是從 1 到 65535。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[內嵌 IDL\] 屬性頁。  
  
4.  修改 \[TypeLib 資源 ID\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryResourceID%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)