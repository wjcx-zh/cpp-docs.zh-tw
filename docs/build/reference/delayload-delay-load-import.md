---
title: "/DELAYLOAD (延遲載入匯入) | Microsoft Docs"
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
  - "/delayload"
  - "VC.Project.VCLinkerTool.DelayLoadDLLS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DELAYLOAD 連結器選項"
  - "DLL 的延遲載入, /DELAYLOAD 選項"
  - "DELAYLOAD 連結器選項"
  - "-DELAYLOAD 連結器選項"
ms.assetid: 39ea0f1e-5c01-450f-9c75-2d9761ff9b28
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /DELAYLOAD (延遲載入匯入)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/DELAYLOAD:dllname  
  
```  
  
## 參數  
 `dllname`  
 您想要延遲載入的 DLL 名稱。  
  
## 備註  
 \/DELAYLOAD 選項會使 `dllname` 指定的 DLL 只在程式第一次呼叫該 DLL 中的函式時載入。  如需詳細資訊，請參閱[延遲載入 DLL 的連結器支援](../../build/reference/linker-support-for-delay-loaded-dlls.md)。  您可以視需要多次使用此選項，指定您所選擇數目的 DLL。  當您連結您的程式，必須使用 Delayimp.lib，或者實作自己的延遲載入 helper 函式。  
  
 [\/DELAY](../../build/reference/delay-delay-load-import-settings.md) 選項指定每一個延遲載入 DLL 的繫結和載入選項。  
  
### 在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  在 \[**連結器**\] 資料夾，選取 \[**輸入**\] 屬性頁。  
  
3.  修改 \[延遲載入 DLL\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)