---
title: "/FIXED (固定基底位址) | Microsoft Docs"
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
  - "/fixed"
  - "VC.Project.VCLinkerTool.FixedBaseAddress"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/FIXED 連結器選項"
  - "FIXED 連結器選項"
  - "-FIXED 連結器選項"
  - "載入程式的偏好基底位址"
ms.assetid: 929bba5e-b7d8-40ed-943e-056aa3710fc5
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /FIXED (固定基底位址)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/FIXED[:NO]  
```  
  
## 備註  
 告知作業系統只將程式載入其慣用的基底位址。  如果慣用的基底位址無法使用，作業系統就不會載入檔案。  如需詳細資訊，請參閱[\/BASE \(基底位址\)](../../build/reference/base-base-address.md)。  
  
 在建置 DLL 時 \/FIXED:NO 為預設值，而 \/FIXED 則是其他專案類型的預設值。  
  
 指定 \/FIXED 時，LINK 不會在程式中產生重新配置區段。  在執行階段時，如果作業系統無法將程式載入該位址，它便會發出錯誤訊息而且不會載入程式。  
  
 指定 \/FIXED:NO 會在程式中產生一個重新配置區段。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取 \[**連結器**\] 資料夾。  
  
3.  選取 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中輸入選項名稱和設定。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)