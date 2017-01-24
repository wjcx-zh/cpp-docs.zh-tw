---
title: "/VERSION (版本資訊) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.Version"
  - "/version"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/VERSION 連結器選項"
  - "Version Information 連結器選項"
  - "VERSION 連結器選項"
  - "-VERSION 連結器選項"
  - "版本編號, 在 .exe 中指定"
ms.assetid: b86d0e86-dca6-4316-aee2-d863ccb9f223
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /VERSION (版本資訊)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/VERSION:major[.minor]  
```  
  
## 備註  
 其中：  
  
 *major* 和 *minor*  
 是您希望在 .exe 或 .dll 檔之標頭中的版本號碼。  
  
## 備註  
 \/VERSION 選項會告訴連結器將版本號碼放入 .exe 或 .dll 檔的標頭中。  請使用 DUMPBIN [\/HEADERS](../../build/reference/headers.md) 查看 OPTIONAL HEADER VALUES 的影像版本欄位，以檢視 \/VERSION 的效果。  
  
 *major* 和 *minor* 引數是 0 到 65,535 之間的十進位數字。  預設值為 0.0 版。  
  
 以 \/VERSION 指定的資訊不會影響您在檔案總管中檢視應用程式屬性時所顯示的版本資訊。  那個版本資訊是來自用來建置應用程式的資源檔。  如需詳細資訊，請參閱[版本資訊編輯器](../../mfc/version-information-editor.md)。  
  
 另一種插入版本號碼的方法是使用 [VERSION](../../build/reference/version-c-cpp.md) 模組定義陳述式。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱[設定 Visual C\+\+ 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下 \[連結器\] 資料夾。  
  
3.  按一下 \[**一般**\] 屬性頁。  
  
4.  修改 \[**版本**\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Version%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)