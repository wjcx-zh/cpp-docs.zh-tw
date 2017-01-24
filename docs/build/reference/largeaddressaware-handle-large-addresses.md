---
title: "/LARGEADDRESSAWARE (處理大型記憶體位址) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.LargeAddressAware"
  - "/largeaddressaware"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/LARGEADDRESSAWARE 連結器選項"
  - "LARGEADDRESSAWARE 連結器選項"
  - "-LARGEADDRESSAWARE 連結器選項"
ms.assetid: a29756c8-e893-47a9-9750-1f0d25359385
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /LARGEADDRESSAWARE (處理大型記憶體位址)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/LARGEADDRESSAWARE[:NO]  
```  
  
## 備註  
 \/LARGEADDRESSAWARE 選項會告訴連結器，應用程式能夠處理 2 GB 以上的記憶體。  在 64 位編譯器中，在預設情況下會啟用此選項。  在 32 位元編譯器中，如果連結器列未以其他方式指定 \/LARGEADDRESSAWARE，就會啟用 \/LARGEADDRESSAWARE:NO。  
  
 如果應用程式是以 \/LARGEADDRESSAWARE 連結的，DUMPBIN [\/HEADERS](../../build/reference/headers.md) 將會顯示此一效果的資訊。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[系統\] 屬性頁。  
  
4.  修改 \[啟用大型記憶體\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LargeAddressAware%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)