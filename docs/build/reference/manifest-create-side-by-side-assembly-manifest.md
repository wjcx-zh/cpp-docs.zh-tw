---
title: "/MANIFEST (建立並存組件資訊清單) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.GenerateManifest"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/MANIFEST 連結器選項"
  - "MANIFEST 連結器選項"
  - "-MANIFEST 連結器選項"
ms.assetid: 98c52e1e-712c-4f49-b149-4d0a3501b600
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /MANIFEST (建立並存組件資訊清單)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/MANIFEST[:{EMBED[,ID=#]|NO}]  
```  
  
## 備註  
 \/MANIFEST 會指定連結器應該要建立並存資訊清單檔。  如需資訊清單檔的詳細資訊，請參閱[資訊清單檔參考](http://msdn.microsoft.com/library/aa375632)。  
  
 預設值為 \/MANIFEST。  
  
 \/MANIFEST:EMBED 選項指定連結器在影像可以內嵌資訊清單檔為 RT\_MANIFEST 型別的資源。  選擇性 `ID` 參數所使用的資源 ID 為資訊清單。  可執行檔使用值 1。   DLL使用值 2 以使它可以指定私用依賴。  如果 `ID` 參數未指定，則如果 \/DLL 選項已設定，預設值為 2 ;否則，預設值為 1。  
  
 從 [!INCLUDE[vs_orcas_long](../../atl/reference/includes/vs_orcas_long_md.md)] 開始，可執行檔的資訊清單檔包含用於指定使用者帳戶控制 \(UAC\) 資訊的區段。  如果有指定 \/MANIFEST，但卻沒有指定 [\/MANIFESTUAC](../../build/reference/manifestuac-embeds-uac-information-in-manifest.md) 或 [\/DLL](../../build/reference/dll-build-a-dll.md)，就會在資訊清單中插入預設 UAC 片段，其 UAC 層級設為 *asInvoker*。  如需 UAC 層級的詳細資訊，請參閱 [\/MANIFESTUAC \(將 UAC 資訊內嵌在資訊清單中\)](../../build/reference/manifestuac-embeds-uac-information-in-manifest.md)。  
  
 若要變更 UAC 的預設行為，請執行其中一項：  
  
-   指定 \/MANIFESTUAC 選項並將 UAC 層級設成所要的值  
  
-   如果不想在資訊清單中產生 UAC 片段，則指定 \/MANIFESTUAC:NO 選項  
  
 如果沒有指定 \/MANIFEST 卻指定 [\/MANIFESTDEPENDENCY](../../build/reference/manifestdependency-specify-manifest-dependencies.md) 註解，就會建立資訊清單檔。  如果指定 \/MANIFEST 為 NO，就不會建立資訊清單檔。  
  
 如果您指定 \/MANIFEST，資訊清單檔的名稱將會與您的輸出檔名稱相同，但是 .manifest 會附加在檔案名稱之後。  例如，如果您的輸出檔名稱是 MyFile.exe，資訊清單檔名稱會是 MyFile.exe.manifest。如果您指定 \/MANIFESTFILE:*name*  ，資訊清單的名稱將會是 *name* 中所指定的名稱。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展開 \[**組態屬性**\] 節點。  
  
3.  展開 **\[連結器\]** 節點。  
  
4.  請選取 \[**資訊清單檔案**\] 屬性頁。  
  
5.  修改 \[**產生資訊清單**\] 屬性。  
  
### 若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateManifest%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)